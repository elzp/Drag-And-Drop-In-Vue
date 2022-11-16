<template>
  <div
    className="bg-white overflow-hidden rounded-md p-30 max-w-xs flex-1 flex flex-col m-2"
    draggable="false"
  >
    <h2 className="text-4xl p-5 text-center" draggable="false">{{ title }}</h2>
    <main
      className="p-10 bg-gray-300 flex-1"
      draggable="false"
      v-for="article in articlesData"
      @dragstart="dragStart($event, article)"
      @dragenter="dragEnter"
      @dragover="dragOver"
      @sragleave="dragLeave"
      @ondrop="drop"
    >
      <Article
        :name="article.name"
        :date="article.date"
        :content="article.content"
      />
    </main>
  </div>
</template>

<script>
import Article from './Article.vue';
export default {
  name: 'ArticlesContainer',
  components: { Article },
  props: {
    title: String,
    articlesData: Array,
  },
  methods: {
    dragStart(e, item) {
      // https://learnvue.co/tutorials/vue-drag-and-drop
      console.log('start', e.target.id, item.name);
      e.dataTransfer.setData('text', item.name);
    },
  },
};
</script>
