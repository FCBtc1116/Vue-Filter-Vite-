<script>
import { ref } from 'vue'
import SearchResult from './SearchResult.vue';

export default {

  components: {
    SearchResult,
  },

  setup() {
    const query = ref('');

    const reset = (evt) => {
      query.value = "";
    }

    return {
      query,
      reset
    }
  },
}
</script>

<template>
  <div>
    <h2>Filter LearnVue Articles</h2>
    <div>
      <input type="text" placeholder="Filter Search" v-model="query" />
    </div>
    <div>
      <button @click="reset">Reset</button>
    </div>
    <SearchResult :query="query" />
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
