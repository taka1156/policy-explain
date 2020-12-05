<template>
  <div>
    <div v-if="status" class="marked-view">
      <article-header :article="article" />
      <div class="marked-view__text markdown-body" v-html="parseMarked" />
    </div>
  </div>
</template>

<script>
import ArticleHeader from './ArticleHeader';
import { markedWrap } from '@/plugins/marked/index.js';
import axios from 'axios';
import 'github-markdown-css';

export default {
  name: 'MarkedView',
  components: {
    'article-header': ArticleHeader
  },
  props: {
    articleUrl: {
      type: String,
      default: '',
      required: true
    }
  },
  data() {
    return {
      article: {},
      status: false
    };
  },
  computed: {
    parseMarked() {
      if (!this.status) return '';
      return markedWrap(this.article.md);
    }
  },
  async created() {
    await this.getArticle();
    this.status = !this.status;
  },
  methods: {
    async getArticle() {
      // 記事のURL
      const OPTIONS = {
        fields: 'title,md,createdAt,updatedAt'
      };
      this.article = await axios
        .get(this.articleUrl, {
          params: { ...OPTIONS },
          headers: { 'X-API-KEY': process.env.VUE_APP_MICRO_CMS }
        })
        .then(({ data }) => {
          console.log(data);
          return data;
        });
    }
  }
};
</script>

<style scoped>
.marked-view {
  width: 95vw;
  text-align: left;
  margin: 0 auto;
}

@media screen and (min-width: 768px) {
  .marked-view {
    width: 80vw;
  }
}

.marked-view__text {
  margin: 20px;
}

a {
  color: #42b983;
}
</style>
