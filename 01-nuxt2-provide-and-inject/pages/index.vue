<template lang="pug">
.index-page
  List(:articles="articles")

</template>

<script lang="ts">
import { defineComponent, computed, ComputedRef } from 'vue';
import List from '~/components/List.vue';
import type { IArticle, IUser } from '~/types';

interface Provide {
  users: ComputedRef<IUser[]>;
}

export default defineComponent({
  components: {
    List,
  },

  provide(): Provide {
    return {
      users: computed(() => this.users),
    };
  },

  computed: {
    articles(): IArticle[] {
      return [
        { id: 'id-01', ownerId: 'user-01', title: 'Article 01' },
        { id: 'id-02', ownerId: 'user-02', title: 'Article 02' },
        { id: 'id-03', ownerId: 'user-01', title: 'Article 03' },
      ];
    },

    users(): IUser[] {
      return [
        { id: 'user-01', name: 'John' },
        { id: 'user-02', name: 'Jack' },
      ];
    },
  },
});
</script>
