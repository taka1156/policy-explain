<template>
  <div>
    <div class="article-header">
      <article-date
        :created-at="article.createdAt"
        :updated-at="article.updatedAt"
      />
      <div class="line" />
      <h1 class="article-header__title">
        {{ article.title }}
      </h1>
    </div>
  </div>
</template>

<script>
import ArticleDate from '../molecules/ArticleDate';

export default {
  name: 'ArticleHeader',
  components: {
    'article-date': ArticleDate
  },
  props: {
    article: {
      type: Object,
      default: () => {},
      required: true
    }
  }
};
</script>

<style scoped>
.article-header {
  padding: 10px;
  background-color: whitesmoke;
  border: 1px solid lightgray;
}

.article-header__title {
  font-size: 1.75rem;
  text-align: left;
  word-break: break-word;
  overflow-wrap: break-word;
  color: dimgray;
}
</style>
