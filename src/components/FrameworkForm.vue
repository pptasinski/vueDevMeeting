<template>
    <form @submit.prevent method="post" role="form">
        <div class="form-group">
            <label></label>
            <input
                    class="form-control"
                    v-validate="'required|min:6'"
                    type="text"
                    name="newFramework"
                    v-model="newFramework"
                    placeholder="Write framework name"
            />
        </div>
        <button type="submit" @click="addNew()" class="btn btn-primary btn-block">Add new</button>
        <div class="form-group">
        <span class="text-danger">{{ errors.first('newFramework') }}</span>
        </div>
    </form>
</template>

<script>
export default {
  name: 'FrameworkForm',
  props: {
    frameworks: Array,
  },
  data() {
    return {
      newFramework: '',
    };
  },
  methods: {
    addNew() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          const frameWorkName = this.newFramework.length > 0 ? this.newFramework : Math
            .random()
            .toString(36)
            .substring(7);
          this.$props.frameworks.push({
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
