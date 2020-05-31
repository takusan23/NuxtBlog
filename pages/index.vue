<template>
  <div class="container">
    <div>
      <el-card class="box-card" v-for="item in blogItems" :key="item">
        <nuxt-link class="text item" :to="`posts/${item.fileName}`">{{ item.title }}</nuxt-link>
      </el-card>
    </div>
  </div>
</template>

<script lang="js">
import Vue from 'vue'
import { fileMap } from "../contents/posts/summary.json";

export default {
  data: () => {
    return {
      blogItems: []
    };
  },
  created() {
    // キーを取り出す
    Object.keys(fileMap).forEach(title => {
      // 記事一個ずつ取る
      const blog = fileMap[title];
      // 名前
      const name = blog.sourceBase.replace(".md", "");
      blog.fileName = name;
      this.blogItems.push(blog);
    });
  }
};
</script>
