<template>
<div>
    <button @click="sort" class="btn btn-sm btn-block btn-default" type="button">Sort list</button>
</div>
</template>

<script>
export default {
  name: 'FrameworkSorter',
  props: {
    frameworks: Array,
  },
  methods: {
    sort() {
      this.frameworks.sort((a, b) => {
        if (a.name < b.name) return -1;
        if (a.name > b.name) return 1;
        return 0;
      });
    },
  },
};
</script>
<style scoped>
</style>
