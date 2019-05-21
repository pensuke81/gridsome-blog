<template>
  <Layout>
    
    <h1>Gridsomeで作るブログ</h1>

    <h2>投稿一覧</h2>
    <div v-for="post in $page.posts.edges" :key="post.node.id">
      タイトル: <g-link :to="post.node.path">
        {{ post.node.title }}
      </g-link>
      <p>概要: {{ post.node.description }}</p>
      <p>タグ:</p>
      <ul v-if="post.node.tags">
        <li v-for="tag in post.node.tags" :key="tag.id">{{ tag.title }}</li>
      </ul>
    </div>
  </Layout>
</template>

<page-query>
{
  posts: allPost {
    edges {
      node {
        path
        title
        tags {
          id
          title
          path
        }
        description
        content
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>