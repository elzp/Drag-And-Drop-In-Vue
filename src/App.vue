<template>
  <div id="app">
    <div className="flex justify-center items-top">
      <ArticlesContainer
        :title="title[0]"
        :articlesData="articlesData.Drafts"
      />
      <ArticlesContainer
        :title="title[1]"
        :articlesData="articlesData.Published"
      />
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
      articlesData: {
        Drafts: [
          { name: 'art1', date: '10.11.2022', content: 'art1' },
          { name: 'art2', date: '11.11.2022', content: 'art2' },
          { name: 'art3', date: '12.11.2022', content: 'art3' },
        ],
        Published: [{ name: 'art4', date: '14.11.2022', content: 'art4' }],
      },
    };
  },
};
</script>

<style scope>
h1,
p {
  font-family: Lato;
}

.hide {
  display: none;
}

.drag-over {
  border: dashed 3px red;
}
</style>
