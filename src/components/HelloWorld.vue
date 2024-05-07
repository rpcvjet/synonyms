<template>
  <div class="hello">
    <h2>Thesaurus demo</h2>
    <input type="text"  v-model="query" >
    <button @click="handleRequest">search</button>
    <div v-if="results.length > 0">
      <li v-for="item in results" :key="item"> 
        {{item}}
      </li>

    </div>

  </div>
</template>

<script setup lang="js">
import { onMounted, ref } from 'vue'
import thesaurus from '../util/convert-thesaurus.js';

const results = ref([])
const query = ref('')
const driver = window.thesaurus

const handleRequest =  () => {
  const synonyms = driver.find(query.value);
  console.log('synonyms', synonyms)
  results.value = synonyms
}

onMounted (() => {
})



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
