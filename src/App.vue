<template>
  <div id="app">
    <div className="flex justify-center items-top">
      <ArticlesContainer :title="title[0]" />
      <ArticlesContainer :title="title[1]" />
    </div>
  </div>
</template>

<script>
import ArticlesContainer from './components/ArticlesContainer.vue';

export default {
  name: 'App',
  components: {
    ArticlesContainer,
  },
  data() {
    return {
      title: ['Drafts', 'Published'],
    };
  },
};
</script>
