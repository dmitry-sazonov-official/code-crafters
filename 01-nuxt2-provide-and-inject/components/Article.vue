<template lang="pug">
.article
  p.article__title {{ article.title }}
  p.article__username Author: {{ user.name }}

</template>

<script lang="ts">
import { defineComponent, PropType, inject } from 'vue';
import type { IArticle, IUser } from '~/types'

export default defineComponent({
  props: {
    article: {
      type: Object as PropType<IArticle>,
      required: true,
    },
  },

  setup() {
    const users = inject('users', []) as IUser[];

    return {
      users,
    };
  },

  computed: {
    user(): IUser | null {
      return this.users.find((user) => {
        return user.id === this.article.ownerId;
      }) ?? null;
    },
  },
});
</script>

<style lang="scss" scoped>
.article {
  background-color: #A8A8A8;
  border-radius: 16px;
  padding: 4px 16px;
  color: #FFFFFF;

  &__title {
    font-size: 24px;
  }
}
</style>