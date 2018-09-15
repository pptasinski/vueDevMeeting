<template>
    <li
            class="list-group-item"
            >
        {{ framework }}
        <button
                class="btn btn-xs btn-danger pull-right"
                v-on:click="removeMe()"
        >
            Remove me
        </button>
    </li>
</template>
<script>
export default {
  name: 'FrameworkListItem',
  props: {
    framework: String,
    frameworkKey: Number,
  },
  methods: {
    removeMe() {
      this.$emit('remove-me', { key: this.frameworkKey });
    },
  },
};
</script>
