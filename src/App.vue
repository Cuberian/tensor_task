<template>
  <div id="app">
    <spoiler :title="spoilerTitle" :content="spoilerContent" toggler-style="custom-style"></spoiler>
    <hr>
    <accordion :accordion-items="accordionItems"
               toggler-style="custom-style"
               toggler-size="small"
               open-mode="many"
               :open-elements="openElements"></accordion>
  </div>
</template>

<script>
import Spoiler from './components/Spoiler.vue'
import Accordion from "@/components/Accordion";

export default {
  name: 'App',
  components: {
    Accordion,
    Spoiler
  },
  data() {
    return {
      spoilerTitle: 'Скрытая подсказка',
      spoilerContent: 'Здесь могла быть ваша реклама',
      accordionItems: [
        {
          title: 'Элемент 1',
          content: 'Содержание 1',
        },
        {
          title: 'Элемент 2',
          content: 'Содержание 2',
        },
        {
          title: 'Элемент 3',
          content: 'Содержание 3',
        },
      ],
      openElements: [0,2],
      openMode: 'one'
    }
  }
}
</script>

<style>

</style>
