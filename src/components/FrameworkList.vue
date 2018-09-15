<template>
    <div class="row">
        <div class="col-xs-12">
        <transition-group class="list-group" name="list" tag="ul">
        <li
                class="list-group-item"
                v-for="(framework, frameworkKey) in frameworks"
                :key="frameworkKey">
            {{ framework.name }}
            <button
                    class="btn btn-xs btn-danger"
                    v-on:click="removeMe(frameworkKey)"
            >
                Remove me
            </button>
        </li>
        </transition-group>
    <p v-if="!frameworks.length">No frameworks!</p>
<FrameworkForm :frameworks="frameworks"></FrameworkForm>
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
    .list-enter-active, .list-leave-active {
        transition: all 1s;
    }
    .list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
        opacity: 0;
        transform: translateY(30px);
    }
</style>
