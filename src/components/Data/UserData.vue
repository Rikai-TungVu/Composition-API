<template>
  <h2>{{ userName }}</h2>
  <h3>{{ age }}</h3>
</template>

<script>
import { computed, ref } from 'vue';

export default {
  props: ['firstName', 'lastName', 'age'],
  //Define props in UserData(child)

  //Composition API
  setup() {
    const firstName = ref('');
    const lastName = ref('');

    const uName = computed(function () {
      return firstName.value + ' ' + lastName.value;
    }); //

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
