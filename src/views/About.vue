<template>
  <div class="about">
    <h1>This is an about page</h1>
    <message>This is a test message</message>
    <counter></counter>
    <cupon-code></cupon-code>
    <br>
    <!-- <button @click="editPost">Add data to post object</button> -->
    <div class="posts">
      <div
       class="post"
       v-for="(post, index) in posts"
       :key="index"
       :class="'post_' + post.id"
      >
        <div class="post_header" v-text="post.title"></div>
        <div class="post_body" v-text="post.body"></div>
        <div class="post_footer" v-text="post.userId"></div>
        <span  class="edit">Edit</span>
        <form class="post_edit">
          <input type="text" v-model="post.title">
          <textarea v-model="post.body"></textarea>
          <button>Update</button>
        </form>
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
  // props: ['postData'],
  components: {
    Message,
    Counter,
    CuponCode
  },
  data() {
    return {
      // edit: false,
      posts: [],
      i: 0,
    };
  },
  methods: {
    // editPost: function(){
    //   for(this.i; this.i < this.posts.length - 1; this.i++) {
    //       this.posts[this.i].edit = false;
    //       // console.log(this.posts[this.i]);
    //   }
    // }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(response => this.posts = response.data.splice(0, 20))
      .catch(function (error) {
        // handle error
        console.log(error);
      })
      .finally(function () {
        console.log('Done with Request execution');
      });
      // (function(){
      //   for(this.i = 0; this.i < this.posts.length - 1; this.i++) {
      //       this.posts[this.i].edit = false;
      //       // console.log(this.posts[this.i]);
      //   }
      // }());
  },
  mounted() {
    // console.log(i);
  }
}
</script>

<style lang="scss">
  .posts {
    max-width: 750px;
    width: 100%;
    padding: 100px 15px;
    margin: 0 auto;
    .post{
      margin-bottom: 30px;
      padding: 15px;
      border: 1px solid green;
      &:last-child{
        margin-bottom: 0;
      }
      .edit{
        text-decoration: underline;
        cursor: pointer;
      }
      .post_edit{
        padding: 30px;
        border: 1px solid #ddd;
        input{
          width: 100%;
          margin-bottom: 10px;
        }
        textarea{
          width: 100%;
          margin-bottom: 10px;
        }
      }
    }
  }
</style>
