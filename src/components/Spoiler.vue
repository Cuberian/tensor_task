<template>
  <div class="spoiler">
      <div class="spoiler-container">
        <div class="spoiler-button">
            <div :class="['spoiler-button__title', titleStyle]">
              {{ title }}
            </div>
            <div :class="['spoiler-button__toggler','size-' + togglerSize, togglerStyle]" @click="openContent()">
                <font-awesome-icon :icon="arrow" :size="iconSize" />
            </div>
        </div>
        <div :class="['spoiler__content', contentStyle]" v-show="isOpen">
          {{ content }}
        </div>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      required: true,
      type: String
    },
    content: {
      required: true,
      type: String
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
    },
    titleStyle: {
      required: false,
      type: String,
      default: ''
    },
    contentStyle: {
      required: false,
      type: String,
      default: ''
    },
    togglerState: {
      required: false,
      type: String,
      default: 'close'
    },
    orderNumber: {
      required: false,
      type: Number,
    }
  },
  name: "Spoiler",
  mounted() {
    if(this.orderNumber !== null)
    {
      this.$parent.$on('closeContent', this.stateHandler)
    }
  },
  data() {
    return {
      isOpen: false,
    };
  },
  created() {
    this.isOpen = this.togglerState === 'open'
  },
  computed: {
    arrow() {
      return this.isOpen ? 'angle-down' : 'angle-up';
    },
    iconSize() {
      let sizes = {
        'small': 'lg',
        'normal': '2x',
        'big': '3x'
      }
      return sizes[this.togglerSize];
    }
  },
  methods: {
    stateHandler(value) {
      if(value === this.orderNumber)
      {
        this.isOpen = false;
      }
    },
    openContent() {
      this.isOpen = !this.isOpen;
      this.$emit('stateChanged', this.isOpen)
    }
  }
}
</script>

<style scoped>

</style>