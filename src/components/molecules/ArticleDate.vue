<template>
  <div>
    <div class="article-date">
      <p>作成日:{{ dateFormat(createdAt) }} ~ 更新日:{{ dateFormat(updatedAt) }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ArticleDate',
  props: {
    createdAt: {
      type: String,
      defalut: '',
      required: true
    },
    updatedAt: {
      type: String,
      defalut: '',
      required: true
    }
  },
  methods: {
    dateFormat(date) {
      if (date === undefined) return '--/--/--';
      return new Date(date).toLocaleDateString();
    }
  }
};
</script>

<style scoped>
.article-date {
  display: flex;
  margin: 0;
}
</style>
