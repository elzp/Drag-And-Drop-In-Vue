<template>
  <div
    class="
      bg-white
      overflow-hidden
      rounded-md
      p-30
      max-w-xs
      flex-1 flex flex-col
      m-2
    "
    draggable="false"
  >
    <h2 class="text-4xl p-5 text-center" draggable="false">{{ title }}</h2>
    <!--     -->
    <main
      class="p-2 bg-gray-300 flex-1 min-h-max"
      @dragstart="dragStart($event, article)"
      @dragenter.prevent="dragEnter($event)"
      @dragover.prevent="dragOver"
      @dragleave="dragLeave($event)"
      @drop="drop($event)"
      @dragend="dragEnd"
      :class="{ 'drag-over': dragover }"
     
    >
      <Article
        v-for="article in articlesData" 
        :id="article.name"
        :key="article.name"
        :name="article.name"
        :date="article.date"
        :content="article.content"
        ref="articles"
      />
    </main>
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
  data() {
    return {
      dragover: false,
    };
  },
  mounted() {
    this.$refs.articles.forEach((it) =>
      this.$emit('position', {
        name: it.name,
        pos: it.$el.getBoundingClientRect().top,
      })
    );
  },
  methods: {
    dragStart(e, item) {
      //  e.preventDefault();
      // https://learnvue.co/tutorials/vue-drag-and-drop
      // get it from https://forum.vuejs.org/t/how-to-get-id-of-dragged-element/13002
      e.dataTransfer.setData('text', e.target.id);
    },
    dragEnter(e) {
      e.preventDefault();
    },
    dragOver() {},
    dragLeave(e) {
      e.preventDefault();
    },
    dragEnd() {},
    drop(e) {
      e.preventDefault();
      const nameOfDragged = e.dataTransfer.getData('text');
      this.$emit('moveArticle', {
        name: nameOfDragged,
        container: this.title,
        mousePosition: e.clientY,
      });
    },
  },
};
</script>
