<template>
    <div>
    <ul>
        <li v-for="(framework, frameworkKey) in frameworks" :key="frameworkKey">
            {{ framework.name }}
            <button v-on:click="removeMe(frameworkKey)">Remove me</button>
        </li>
    </ul>
    <p v-if="!frameworks.length">No frameworks!</p>
    <button v-on:click="addNew()">Add another item</button>
        <input
                v-validate="'required|min:6'"
                type="text"
                name="newFramework"
                v-model="newFramework"
                placeholder="Write framework name"
        />
        <span>{{ errors.first('newFramework') }}</span>
    </div>
</template>

<script>
export default {
  name: 'FrameworkList',
  data() {
    return {
      newFramework: '',
      frameworks: [{
        name: 'Angular',
      }],
    };
  },
  methods: {
    removeMe(key) {
      this.frameworks.splice(key, 1);
    },
    addNew() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          const frameWorkName = this.newFramework.length > 0 ? this.newFramework : Math
            .random()
            .toString(36)
            .substring(7);
          this.frameworks.push({
            name: frameWorkName,
          });
          this.newFramework = '';
          this.$validator.reset();
        }
      });
    },
  },
};
</script>

<style scoped>

</style>
