<template>
    <div class="row">
        <div class="col-xs-12">
    <ul class="list-group">
        <li
                class="list-group-item"
                v-for="(framework, frameworkKey) in frameworks"
                :key="frameworkKey">
            {{ framework.name }}
            <button
                    class=" badge btn btn-xs"
                    v-on:click="removeMe(frameworkKey)"
            >
                Remove me
            </button>
        </li>
    </ul>
    <p v-if="!frameworks.length">No frameworks!</p>
<FrameworkForm v-bind:frameworks="frameworks"></FrameworkForm>
        </div>
    </div>
</template>

<script>
import FrameworkForm from './FrameworkForm.vue';

export default {
  name: 'FrameworkList',
  components: { FrameworkForm },
  data() {
    return {
      frameworks: [{
        name: 'Angular',
      }],
    };
  },
  methods: {
    removeMe(key) {
      this.frameworks.splice(key, 1);
    },
  },
};
</script>

<style scoped>

</style>
