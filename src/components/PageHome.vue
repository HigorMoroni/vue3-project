<template>
  <div>Hello World</div>
  <div v-for="thread in threads" :key="thread.id">
    <h2>{{thread.title}}</h2>
    <div v-for="postId in thread.posts" :key="postId">
      <p>{{userById(postById(postId).userId).name}}</p>
      <p>{{postById(postId).text}}</p>
    </div>
  </div>
</template>

<script>
import sourceData from '@/data.json'
export default {
  data () {
    return {
      threads: sourceData.threads,
      posts: sourceData.posts,
      users: sourceData.users
    }
  },
  methods: {
    postById (postId) {
      return this.posts.find(post => post.id === postId)
    },
    userById (userId) {
      return this.users.find(user => user.id === userId)
    }
  }
}
</script>

<style>

</style>
