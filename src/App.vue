<template>
  <div id="app">
    <div className="flex justify-center items-top">
      <ArticlesContainer
        :title="title[0]"
        :articlesData="articlesData.filter((it) => it.container === title[0])"
        @moveArticle="chandleMoveArticle"
        @position="updatePosition"
      />
      <ArticlesContainer
        :title="title[1]"
        :articlesData="articlesData.filter((it) => it.container === title[1])"
        @moveArticle="chandleMoveArticle"
        @position="updatePosition"
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
          position: -1,
        },
        {
          name: 'art2',
          date: '11.11.2022',
          content: 'art2',
          container: 'Drafts',
          position: -2,
        },
        {
          name: 'art3',
          date: '12.11.2022',
          content: 'art3',
          container: 'Drafts',
          position: -3,
        },
        {
          name: 'art4',
          date: '14.11.2022',
          content: 'art4',
          container: 'Published',
          position: -1,
        },
      ],
    };
  },
  methods: {
    chandleMoveArticle(articleData) {
      this.articlesData = this.articlesData.filter((it) => {
        if (articleData.name === it.name) {
          it.container =
            it.container === articleData.container
              ? it.container
              : it.container === 'Drafts'
              ? 'Published'
              : 'Drafts';
        }
        return it;
      });
    },
    updatePosition(data) {
      this.articlesData = this.articlesData.map((it) => {
        if (data.name === it.name) {
          it.position = data.pos;
        }
        return it;
      });
    },
  },
};
</script>

<style scope>
h1,
p {
  font-family: Lato;
}
</style>
