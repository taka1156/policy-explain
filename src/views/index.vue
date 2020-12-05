<template>
  <div>
    <marked-view :article-url="articleUrl" />
  </div>
</template>

<script>
// @ is an alias to /src
import MarkedView from '@/components/organisms/MarkedView.vue';

export default {
  name: 'Home',
  components: {
    'marked-view': MarkedView
  },
  data() {
    return {
      articleUrl: 'https://profile-taka1156.microcms.io/api/v1/policy/volngidla'
    };
  }
};
</script>
