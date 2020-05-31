<template>
  <div class="container">
    <div>
      <el-card class="box-card">
        <div>{{(new Date(created_at).toLocaleDateString())}} 投稿</div>
        <div v-html="bodyHtml"></div>
      </el-card>
    </div>
  </div>
</template>

<script>
import { sourceFileArray } from "../../contents/posts/summary.json";

export default {
  // 記事があるかどうか。JSONのsourceFileArrayの配列に含まれているか確認している。
  validate({ params }) {
    return sourceFileArray.includes(
      `contents/posts/markdown/${params.slug}.md`
    );
  },
  // 各記事のJSONファイルを読み込んでる。
  asyncData({ params }) {
    return Object.assign(
      {},
      require(`~/contents/posts/json/${params.slug}.json`),
      { params }
    );
  },
  mounted() {
    // DOM生成後
  },
  // さあ？
  head() {
    const title = `${this.title}`;
    const url = `posts/${this.params.slug}/`;
    return {
      title: title,
      meta: [
        { hid: "og:url", property: "og:url", content: url },
        { hid: "og:title", property: "og:title", content: title }
      ],
      link: [{ rel: "canonical", href: url }]
    };
  }
};
</script>