<template>
  <Layout :sidebar="true">
    
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image alt="Example image" src="~/favicon.png" width="135" />
    
    <h1>Hello, world!</h1>
   
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur excepturi labore tempore expedita, et iste tenetur suscipit explicabo! Dolores, aperiam non officia eos quod asperiores
    </p>

    <p class="home-links">
      <a href="https://gridsome.org/docs" target="_blank" rel="noopener">Gridsome Docs</a>
      <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
    </p>

    <template slot="sidebar">
      This will be added to sidebar slot from the page
    </template>

    <!-- List posts -->
    <div class="posts">
      <!--g-link v-for="edge in $page.posts.edges" :key="edge.node.path">{{ edge.node.title }}</g-link-->
      <h2>aa</h2>
      <div v-for="edge in $page.allPost.edges" :key="edge.node.path">{{ edge.node.title }}</div>
    </div>

  </Layout>
</template>

<page-query>
query posts {
  allPost{
    edges {
      node {
        path,
        title
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
