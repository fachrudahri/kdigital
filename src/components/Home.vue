<template>
  <h1>Top Stories</h1>
  <h4>My Favourite</h4>
  <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit.</p>
  <hr>
  <div class="items">
    <div v-for="item in state.stories" :key="item.id">
      <router-link :to="`/detail/${item}`">{{ item }}</router-link>
    </div>
  </div>
</template>

<script>
import { computed, onMounted, reactive } from 'vue';
import axios from '../plugins/axios';
export default {
  setup() {
    const state = reactive({
      stories: []
    });

    onMounted(async () => {
      const { data } = await axios.get('/topstories.json')
      state.stories = data;
      
    })
    return {
      state
    }
  }
}
</script>

