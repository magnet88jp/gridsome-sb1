<template>
  <Layout>
    <h1>About us</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error doloremque omnis animi, eligendi magni a voluptatum, vitae, consequuntur rerum illum odit fugit assumenda rem dolores inventore iste reprehenderit maxime! Iusto.</p>
    <template slot="sidebar">
      This will be added to sidebar slot from the page
    </template>
    <Card />
  </Layout>
</template>

<script>
import Card from '~/components/Card.vue'

export default {
  metaInfo: {
    title: 'About us'
  },
  components: {
    Card
  }
}
</script>
