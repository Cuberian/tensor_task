<template>
  <div class="accordion">
    <div class="accordion_container">
      <template v-for="(item, index) in accordionItems">
        <spoiler
            :title="item.title"
            :content="item.content"
            :toggler-state="isOpen(index)"
            :key="item.title"
            :toggler-size="togglerSize"
            :toggler-style="togglerStyle"
            :order-number="index"
            @stateChanged="stateHandler(index, $event)">

        </spoiler>
      </template>
    </div>
  </div>
</template>

<script>
import Spoiler from "@/components/Spoiler";
export default {
  props: {
    accordionItems: {
      required: true,
      type: Array
    },
    openMode: {
      required: false,
      type: String,
      default: 'many'
    },
    openElements: {
      required: false,
      type: Array,
      default: null
    },
    togglerSize: {
      required: false,
      type: String,
      default: 'normal'
    },
    togglerStyle: {
      required: false,
      type: String,
      default: ''
    }
  },
  name: "Accordion",
  components: {
    Spoiler
  },
  data() {
    return {
      getOpenElements: []
    }
  },
  created() {
    if(this.openMode === 'one' && this.openElements && this.openElements.length > 0) {
      this.getOpenElements = this.openElements.slice(0,1);
    }
    else if(this.openMode === 'many' && this.openElements && this.openElements.length > 0) {
      this.getOpenElements = this.openElements;
    }
  },
  methods: {
    isOpen(index) {
      if(this.getOpenElements.length > 0)
        return this.getOpenElements.includes(index) ? 'open' : 'close';
      else
        return 'close';
    },
    stateHandler(orderNumber, e) {
      if(this.openMode === 'one' && e)
      {
        this.accordionItems.forEach((item,index) => {
           if(orderNumber !== index)
           {
             this.$emit('closeContent', index)
           }
        })
      }
    }
  }
}
</script>

<style scoped>

</style>