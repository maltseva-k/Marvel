<template>
  <div id="app">
    <app-header :changeSearch="changeSearch"/>
    <div class="container">
      <h1>Персонажи Marvel</h1>
      <content-loader v-if="!characters.length"/>
      <div v-else class="row">
        <app-card :character="character" v-for="(character, idx) in filterCharacters" :key="character.id" @click="characterIndex = idx"/>
        <app-modal :character="filterCharacters[characterIndex]" />
      </div>
    </div>
  </div>
</template>

<script>
import AppHeader from '@/views/AppHeader'
import AppCard from '@/views/AppCard'
import AppModal from '@/views/AppModal'
import ContentLoader from '@/views/ContentLoader'
/* import AppModal from '@/views/AppModal' */
export default {
  name: 'App',
  components: { ContentLoader, AppModal, AppHeader, AppCard },
  data () {
    return {
      loading: true,
      characters: [],
      characterIndex: 0,
      search: ''
    }
  },
  methods: {
    fetchCharacters () {
      this.characters = fetch('https://netology-api-marvel.herokuapp.com/characters')
        .then(res => res.json())
        .then(data => {
          this.characters = data
        })
      return this.characters
    },
    changeSearch (value) {
      this.search = value
    }
  },
  computed: {
    filterCharacters () {
      return this.characters.filter(character => {
        return character.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  },
  mounted () {
    this.fetchCharacters()
  }
}

</script>

<style lang="scss">
</style>
