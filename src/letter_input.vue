<template>
  <span class="quote_digester--letter">
    <input
      type="text"
      rel="letter_input"
      v-model="userGuess"
      v-show="!solved"
      @keyup="tryToSolve()"
    />
    <article>
      <span class="solved_letter" v-show="solved">{{ character }}</span>
      <span>{{ tryCount }}</span>
    </article>
  </span>
</template>

<script>
export default {
  name: 'LetterInput',
  props: ['character'],
  data () {
    return {
      tryCount: 0,
      solved: false,
      userGuess: null
    }
  },
  methods: {
    tryToSolve () {
      let letterMatched = this.userGuess === this.character
      if (this.guessHasLength) {
        this.iterateTryCount()
      }
      if (letterMatched) {
        this.solved = true
      }
    },
    iterateTryCount () {
      this.tryCount ++
    },
    clearInput () {

    }
  },
  computed: {
    letterPassed () {
      return !!this.character
    },
    guessHasLength () {
      return this.userGuess && this.userGuess.length > 0
    }
  }
}
</script>

<style lang="scss" scoped>
.quote_digester--letter {
  display: flex;
  flex-direction: column;
}

input {
  padding: 1rem;
  width: 1rem;
  font-size: 1rem;
  border-top: none;
  border-right: none;
  border-left: none;
}

article {
  display: inline-block;
}

.solved_letter {
  font-size: 1rem;
}

</style>
