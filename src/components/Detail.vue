<template>
  <h1>{{state.stories.title}}</h1>
  <h5>{{ state.stories.by }}</h5>
  <h6>{{ new Date(state.stories.time*1000).toLocaleDateString('en-US') }}</h6>
  <br><br>
  <h5>description</h5>
  <p>{{ state.stories.text }}</p>

</template>

<script>
import { onMounted, reactive } from 'vue';
import { useRoute } from 'vue-router';
import axios from '../plugins/axios';
export default {
  setup() {
    const route = useRoute();
    const id = route.params.id;
    const state = reactive({
      stories: {}
    });

    onMounted(async () => {
      const { data } = await axios.get(`/item/${id}.json`)
      state.stories = data;
    })
    return {
      state
    }
  }
}
</script>
