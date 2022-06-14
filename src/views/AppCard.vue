<template>
  <div class="card mb-3 col-sm-12 col-md-6 col-lg-4">
    <div class="row g-0">
      <div class="col-md-4">
        <img :src="character.thumbnail" class="img-fluid rounded-start" :alt="character.name">
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{ character.name }}</h5>
          <!-- Button trigger modal -->
          <button type="button" class="btn btn-secondary" data-bs-toggle="modal" data-bs-target="#exampleModal">
            Подробнее
          </button>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppCard',
  props: ['character']

}
</script>

<style scoped>

</style>
