<template>
<div>
    <button @click="sort" class="btn btn-sm btn-block btn-default" type="button">Sort list</button>
</div>
</template>

<script>
export default {
  name: 'FrameworkSorter',
  methods: {
    sort() {
      this.$emit('sort-me');
    },
  },
};
</script>
<style scoped>
</style>
