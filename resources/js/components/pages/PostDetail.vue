<template>
  <div class="container">
    <h1>{{post.title}}</h1>
    <p>{{post.content}}</p>
  </div>
</template>

<script>
export default {
  name: 'PostDetail',
  data(){
    return {
      apriUrl: 'http://127.0.0.1:8000/api/posts/',
      post:{
        title: '',
        content: '',
        category: '',
        tags: []
      }
    }
  },
  methods: {
    getApi(){
      axios.get(this.apriUrl + this.$route.params.slug)
      .then(res => {
        this.post = res.data;
        console.log(this.post);
      })
    }
  },
  mounted(){
    this.getApi();
  }
}
</script>

<style>

</style>