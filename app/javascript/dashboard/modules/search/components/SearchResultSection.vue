<template>
  <section>
    <div class="label-container">
      <h3 class="text-block-title">{{ title }}</h3>
    </div>
    <slot />
    <div v-if="empty" class="empty">
      <fluent-icon icon="info" size="16px" class="icon" />
      <p class="empty-state__text">
        {{ $t('SEARCH.EMPTY_STATE', { item: titleCase, query }) }}
      </p>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: '',
    },
    empty: {
      type: Boolean,
      default: false,
    },
    query: {
      type: String,
      default: '',
    },
  },
  computed: {
    titleCase() {
      return this.title.toLowerCase();
    },
  },
};
</script>

<style scoped lang="scss">
.search-list {
  list-style: none;
  margin: 0;
  padding: var(--spacing-normal) 0;
}
.label-container {
  position: sticky;
  top: 0;
  padding: var(--space-small) 0;
  z-index: 50;
  background: var(--white);
}

.empty {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: var(--space-medium) var(--space-normal);
  background: var(--s-25);
  border-radius: var(--border-radius-medium);
  .icon {
    color: var(--s-500);
  }
  .empty-state__text {
    text-align: center;
    color: var(--s-500);
    margin: 0 var(--space-small);
  }
}
</style>
