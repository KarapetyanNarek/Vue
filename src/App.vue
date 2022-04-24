
<script>
  import PostForm from "@/components/PostForm";
  import PostList from "@/components/PostList";

  export default {
    components: {
      PostList, PostForm
    },
    data() {
      return {
        posts: [
          {id: 1, title: 'JavaScript', body: 'Description post'},
          {id: 2, title: 'JavaScript 2', body: 'Description post 2'},
          {id: 3, title: 'JavaScript 3', body: 'Description post 3'},
        ],
        dialogVisible: false,
      }
    },
    methods: {
      createPost(post) {
        this.posts.push(post);
        this.dialogVisible=false;
      },
      removePost(post) {
        this.posts = this.posts.filter(p => p.id !== post.id);
      },
      showDialog() {
        this.dialogVisible = true
      }
    }
  }
</script>

<template>
  <div class="app">
    <h1>Posts page</h1>
    <my-button @click="showDialog">Create post</my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </my-dialog>
    <post-list
        :posts="posts"
        @remove="removePost"
    />
  </div>
</template>

<style>
  * {
   margin: 0px;
   padding: 0;
   box-sizing: border-box;
  }

  .app {
    padding: 20px;
  }
</style>