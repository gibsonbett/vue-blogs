<!-- src/views/BlogPostDetail.vue -->
<template>
    <div>
      <Header />
  
      <div class="container">
        <div class="main-content">
          <BlogPost :post="selectedPost" />
          <CommentSection />
        </div>
  
        <Sidebar />
      </div>
    </div>
  </template>
  
  <script>
  import Header from '@/components/HeaderComp.vue';
  import BlogPost from '@/components/BlogPost.vue';
  import CommentSection from '@/components/CommentSection.vue';
  import Sidebar from '@/components/SideBar.vue';
  
  export default {
    components: {
      Header,
      BlogPost,
      CommentSection,
      Sidebar,
    },
    data() {
      return {
        selectedPost: {},
      };
    },
    mounted() {
      // Fetch data from the mock API for a specific post (replace with actual API call in a real project)
      const postId = this.$route.params.id;
      fetch(`../mockData.json?id=${postId}`)
        .then(response => response)
        .then(data => {
            console.log('post items', this.post)
          this.selectedPost = JSON.parse(data[0].posts.find(post => post.id === Number(postId)));
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
  