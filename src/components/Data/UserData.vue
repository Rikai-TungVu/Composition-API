<template>
  <h2>{{ userName }}</h2>
  <h3>{{ age }}</h3>
</template>

<script>
import { computed } from 'vue';
// (2) Not necessary to import ref when use 'props' way

export default {
  props: ['firstName', 'lastName', 'age'],
  //Define props in UserData(child)

  //Composition API
  setup(props) {
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

    return {
      uName,
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
