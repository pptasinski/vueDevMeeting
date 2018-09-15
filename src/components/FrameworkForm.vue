<template>
    <form @submit.prevent method="post" role="form">
        <div class="form-group form-group-sm">
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
        <button
                type="submit"
                @click="addNew()"
                class="btn btn-sm btn-primary btn-block"
        >
            Add new
        </button>
        <div class="form-group text-center" style="margin-top: 15px;">
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
          this.$props.frameworks.push({
            name: this.newFramework,
          });
          this.newFramework = '';
          this.$validator.reset();
        }
      });
    },
  },
};
</script>
