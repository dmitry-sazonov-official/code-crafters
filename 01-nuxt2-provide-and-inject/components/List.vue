<template lang="pug">
.list
  Article(
    v-for="article in articles"
    :key="article.id"
    :article="article"
  )

</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Article from '~/components/Article.vue';
import type { IArticle } from '~/types';

export default defineComponent({
  props: {
    articles: {
      type: Array as PropType<IArticle[]>,
      default: () => [],
    },
  },

  components: {
    Article,
  },
});
</script>

<style lang="scss" scoped>
.list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
</style>
