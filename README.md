# nuxtblog

![image](https://user-images.githubusercontent.com/32033405/83357553-fe53eb80-a3a7-11ea-894c-cd3e3df83627.png)

Nuxt.js + processmd を使ったブログ。  

# はじめて

```console
npm install
npm run dev
```

# 記事追加

`contents/posts/markdown`にMarkdownファイルを入れます。

ターミナルで以下の一行を叩きます。

```console
npm run md
```


# 静的サイト生成

```console
npm run generate
```

distフォルダが出来てると思います。

# ファイル構成
- contents/posts/markdown
    - Markdownファイルを入れる
    - 入れたら `npm run md` 叩いてね
- pages/posts/_slug.vue
    - 記事の画面
- pages/index.vue
    - 記事一覧
