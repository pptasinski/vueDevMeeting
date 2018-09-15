<template>
    <div class="row">
        <h3 class="text-center">Framework List</h3>
        <div class="col-xs-12">
        <transition-group class="list-group" name="list" tag="ul">
            <FrameworkListItem
                    :key="frameworkKey"
                    @remove-me="removeMe"
                    v-for="(framework, frameworkKey) in frameworks"
                    v-bind:framework="framework.name"
                    v-bind:frameworkKey="frameworkKey"
            />
        </transition-group>
    <p v-if="!frameworks.length">No frameworks!</p>
<FrameworkForm :frameworks="frameworks"></FrameworkForm>
        </div>
    </div>
</template>

<script>
import FrameworkForm from './FrameworkForm.vue';
import FrameworkListItem from './FrameworkListItem.vue';

export default {
  name: 'FrameworkList',
  components: { FrameworkListItem, FrameworkForm },
  data() {
    return {
      frameworks: [{
        name: 'Angular',
      }],
    };
  },
  methods: {
    removeMe(e) {
      this.frameworks.splice(e.key, 1);
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
