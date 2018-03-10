<template>
  <span class="quote_digester--character">
    {{ character }}
  </span>
</template>

<script>
export default {
  name: 'CharacterDisplay',
  props: ['character'],
  computed: {
    characterPassed () {
      return !!this.character
    }
  }
}
</script>

<style lang="scss" scoped>
span {
  padding: 0 .25rem 0 1.5rem;
}
</style>
