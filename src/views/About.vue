<template>
  <div class="about">
    <h1>This is an about page</h1>
    <message>This is a test message</message>
    <counter></counter>
    <cupon-code></cupon-code>

    <div class="posts">
      <div
       class="post"
       v-for="(post, index) in posts"
       :key="index"
       :class="'post' + post.id"
      >
        <div class="post_header" v-text="post.title"></div>
        <div class="post_body" v-text="post.body"></div>
        <div class="post_footer" v-text="post.userId"></div>
      </div>
    </div>

  </div>
</template>

<script>
import axios from "axios";
import Message from "@/components/Message.vue";
import Counter from "@/components/Counter.vue";
import CuponCode from "@/components/CuponCode.vue";

export default {
  name: 'about',
  components: {
    Message,
    Counter,
    CuponCode
  },
  data() {
    return {
      posts: []
    };
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(response => this.posts = response.data)
      .catch(function (error) {
        // handle error
        console.log(error);
      })
      .finally(function () {
        console.log('Done with Request execution');
      });
  },
  mounted() {

  }
}
</script>

<style lang="scss">
  .posts{
    max-width: 750px;
    width: 100%;
    padding: 0 15px;
    margin: 0 auto;
  }
</style>
