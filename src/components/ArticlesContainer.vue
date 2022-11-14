<template>
  <div
    className="bg-white overflow-hidden rounded-md p-30 max-w-xs flex-1 flex flex-col"
    draggable="false"
  >
    <h2 className="text-4xl p-5 text-center" draggable="false">{{ title }}</h2>
    <main className="p-10 bg-gray-300 flex-1" draggable="false"></main>
  </div>
</template>

<script>
export default {
  name: 'ArticlesContainer',
  props: {
    title: String,
  },
};
</script>
