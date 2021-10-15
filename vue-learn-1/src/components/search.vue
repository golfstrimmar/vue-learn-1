<template>
<div class="search">
  <input
      type="text"
      v-model = "searchText"
  >
  <button
    type="button"
    @click="$emit('search', searchText )"
>Найти </button>
</div>
</template>

<script>
export default {
  name: "search",
  data(){
    return{
      searchText: ""
    }
  }
}
</script>

<style scoped>

</style>