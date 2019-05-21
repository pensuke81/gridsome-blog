<template>
  <Layout>
    <h1>{{ $page.post.title }}</h1>
    <p>タグ:</p>
    <ul v-if="$page.post.tags">
        <li v-for="tag in $page.post.tags" :key="tag.id">{{ tag.title }}</li>
    </ul>
    <div v-html="$page.post.content"/>
  </Layout>
</template>

<page-query>
query Post ($path: String!) {
  post: post (path: $path) {
    title
    path
    date (format: "YYYY/MM/DD")
    tags {
      id
      title
      path
    }
    description
    content
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
        title: this.$page.post.title
    }
  }
}
</script>