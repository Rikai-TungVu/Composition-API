<template>
  <div>
    <h2>{{ uName }}</h2>
    <h3>{{ age }}</h3>
  </div>
</template>

<script>
import { computed, inject } from 'vue';
// (2) Not necessary to import ref when use 'props' way
// (3)Working with Provide/ Inject

export default {
  props: ['firstName', 'lastName'],
  //Define props in UserData(child)
  // (3)Working with Provide/ Inject
  // Delete , 'age'

  //Composition API
  setup(props, context) {
    // (2) use 'props' to transfer data

    // (1)Traditions Ways of Compositions API
    // const firstName = ref('');
    // const lastName = ref('');
    // define inside Compositons API

    // (1)Traditions Ways of Compositions API
    // const uName = computed(function () {
    //   return firstName.value + ' ' + lastName.value;
    // });

    const uName = computed(function () {
      return props.firstName + ' ' + props.lastName;
    }); // (2) Use 'props' ways

    console.log(context);

    const age = inject('userAge');
    // (3)Working with Provide/ Inject
    // define variable in UserData(Child)

    //context.emit('save-data', 1);
    // Work same ways like ...
    // this.$emit('save-data, 1');

    return {
      uName,
      age,
    };
  },

  // Options API
  // computed: {
  //   userName() {
  //     return this.firstName + ' ' + this.lastName;
  //   },
  // },
};
</script>
