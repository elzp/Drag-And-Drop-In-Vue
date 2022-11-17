<template>
  <div id="app">
    <div className="flex justify-center items-top">
      <ArticlesContainer
        :title="title[0]"
        :articlesData="articlesData.filter((it) => it.container === title[0])"
      />
      <ArticlesContainer
        :title="title[1]"
        :articlesData="articlesData.filter((it) => it.container === title[1])"
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
      articlesData: [
        {
          name: 'art1',
          date: '10.11.2022',
          content: 'art1',
          container: 'Drafts',
        },
        {
          name: 'art2',
          date: '11.11.2022',
          content: 'art2',
          container: 'Drafts',
        },
        {
          name: 'art3',
          date: '12.11.2022',
          content: 'art3',
          container: 'Drafts',
        },
        {
          name: 'art4',
          date: '14.11.2022',
          content: 'art4',
          container: 'Published',
        },
      ],
    };
  },
};
</script>

<style scope>
h1,
p {
  font-family: Lato;
}
</style>
