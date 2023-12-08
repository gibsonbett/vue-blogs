<!-- src/views/Home.vue -->
<template>
  <div>
    <Header />

    <div class="container">
      <div class="main-content">
        <h1>Blog Posts</h1>
        <div v-for="post in posts" :key="post.id">
          <BlogPost :post="post" />
          <CommentSection />
        </div>
        <Pagination />
      </div>

      <SideBar />
    </div>
  </div>
</template>

<script>
import Header from '@/components/HeaderComp.vue';
import BlogPost from '@/components/BlogPost.vue';
import CommentSection from '@/components/CommentSection.vue';
import Pagination from '@/components/PaginationComp.vue';
import SideBar from '@/components/SideBar.vue';

export default {
  components: {
    Header,
    BlogPost,
    CommentSection,
    Pagination,
    SideBar,
  },
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    // Fetch data from the mock API (replace with actual API call in a real project)
    fetch(`../mockData.json`)
      .then(response => response.json())
      .then(data => {
        console.log('Fetched data:', data); // Log the fetched data
        this.posts = data;
      })
      .catch(error => {
        console.error('Error fetching data:', error);
      });
  },
};
</script>

<style scoped>
/* Add view-specific styles here */
.container {
  display: flex;
}

.main-content {
  flex: 1;
  margin-right: 20px;
}
</style>
