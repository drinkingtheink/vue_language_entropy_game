<template>
  <section class="quote_digester--display">
    <component 
      v-for="(char, index) in dissectedQuote" 
      :is="componentDecider(char)" 
      :character="char"
      :class="{ letter : isALetter(char) }"
    ></component>
  </section>
</template>

<script>
import LetterInput from './letter_input.vue'
import CharacterDisplay from './char_display.vue'
export default {
  name: 'QuoteDigester',
  props: ['quote'],
  components: {
    LetterInput,
    CharacterDisplay
  },
  methods: {
    isALetter (char) {
      return char.length === 1 && char.match(/[a-z]/i);
    },
    componentDecider (char) {
      let decidingFactor = this.isALetter(char)
      return decidingFactor ? 'LetterInput' : 'CharacterDisplay'
    }
  },
  computed: {
    quotePassed () {
      return !!this.quote
    },
    dissectedQuote () {
      return this.quotePassed ? this.quote.split('') : null
    }
  }
}
</script>

<style lang="scss" scoped>
.quote_digester--display {
  display: flex;
  padding: 0 2rem;
}
</style>
