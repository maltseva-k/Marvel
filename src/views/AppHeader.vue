<template>
  <nav class="navbar navbar-dark bg-dark">
    <div class="container-fluid">
      <a class="navbar-brand">Marvel</a>
      <form class="d-flex">
        <input
          class="form-control me-2"
          type="search"
          placeholder="Поиск..."
          aria-label="Search"
          v-model="inputValue"
          @input="changeSearch(inputValue)"
          @keydown.enter.prevent>
        <button
          class="btn btn-outline-success"
          type="reset"
          @click="inputValue = ''; changeSearch(inputValue)">ВСЕ</button>
      </form>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'AppHeader',
  data () {
    return {
      inputValue: ''
    }
  },
  props: ['changeSearch']
}
</script>

<style scoped>

</style>
