<template>
  <div>
    <div v-for="(singlePost, index) in post" :key="index">
      <h2 class="mt-3 text-lg font-semibold leading-6 text-gray-900 group-hover:text-gray-600">{{ singlePost.title }}</h2>
      <p class="mt-5 line-clamp-3 text-sm leading-6 text-gray-600">{{ singlePost.body }}</p>
      <a :href="singlePost.tag" class="relative z-10 rounded-full bg-gray-50 px-3 py-1.5 font-medium text-gray-600 hover:bg-gray-100" v-for="tag in singlePost.tags" :key="tag">{{ tag }}</a>
      <!-- <div class="relative z-10 rounded-full bg-gray-50 px-3 py-1.5 font-medium text-gray-600 hover:bg-gray-100" v-for="tag in singlePost.tags" :key="tag">{{ tag }}</div> -->
      <div>Likes: {{ singlePost.reactions }}  </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['post'],
  mounted() {
  },
};
</script>



<style scoped>
/* Add component-specific styles here */
.blog-post {
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.blog-post h2 {
  color: #333;
}

.blog-post p {
  color: #666;
}

.tags {
  margin-top: 10px;
}

.tags span {
  display: inline-block;
  margin-right: 5px;
  padding: 5px;
  background-color: #007bff;
  color: #fff;
  border-radius: 3px;
}

.reactions {
  margin-top: 10px;
}

.reactions span {
  color: #888;
}
</style>
