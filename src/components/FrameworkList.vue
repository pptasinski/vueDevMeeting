<template>
    <div class="row">
        <h3 class="text-center">Framework List</h3>
        <div class="col-xs-12">
            <transition-group class="list-group" name="list" tag="ul">
                <FrameworkListItem
                        v-for="(framework, frameworkKey) in frameworks"
                        :key="frameworkKey"
                        :framework="framework.name"
                        :frameworkKey="frameworkKey"
                        @remove-me="removeMe"
                />
            </transition-group>
            <div v-if="!frameworks.length" class="alert alert-info text-center">
                No frameworks!
            </div>
            <FrameworkForm :frameworks="frameworks"></FrameworkForm>
            <FrameworkSorter @sort-me="sort"></FrameworkSorter>
        </div>
    </div>
</template>
<script>
import FrameworkForm from './FrameworkForm.vue';
import FrameworkListItem from './FrameworkListItem.vue';
import FrameworkSorter from './FrameworkSorter.vue';

export default {
  name: 'FrameworkList',
  components: { FrameworkSorter, FrameworkListItem, FrameworkForm },
  data() {
    return {
      frameworks: [
        {
          name: 'Angular',
        },
        {
          name: 'React',
        },
        {
          name: 'Vue',
        },
        {
          name: 'jQuery',
        },
      ],
    };
  },
  methods: {
    sort(){
      this.frameworks = this.frameworks.sort(function(a, b){
        if(a.name.toLowerCase() < b.name.toLowerCase()) return -1;
        if(a.name.toLowerCase() > b.name.toLowerCase()) return 1;
        return 0;
      });
    },
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
