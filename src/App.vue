<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <!-- <input type="text" placeholder="First Name" @input="setFirstName" /> -->
      <input type="text" placeholder="Last Name" v-model="lastName" />
      <!-- <input type="text" placeholder="Last Name" @input="setLastname" /> -->
    </div>
  </section>
</template>

<script>
import { ref, computed, watch } from 'vue';
/* import { ref } from 'vue'; */
// ref work with single data(.value)
// reactive work with group data

export default {
  setup() {
    // const uName = ref('Monday');
    const firstName = ref('');
    const lastName = ref('');
    const uAge = ref(31);
    // const user = reactive({
    //   name: 'Monday',
    //   age: 31,
    // });

    const uName = computed(function () {
      return firstName.value + ' ' + lastName.value;
    });

    watch([uAge, uName], function (newValues, olaValues) {
      console.log('Old Age: ', olaValues[0]);
      console.log('New Age: ', newValues[0]);
      console.log('Old Name: ', olaValues[1]);
      console.log('New Name: ', newValues[1]);
    });

    function setNewData() {
      uAge.value = uAge.value + 1;
    }

    // function setFirstName(event) {
    //   firstName.value = event.target.value;
    // }

    // function setLastname(event) {
    //   lastName.value = event.target.value;
    // }

    return {
      userName: uName,
      age: uAge,
      setAge: setNewData,
      // setFirstName,
      // setLastname,
      firstName,
      lastName,
    };
    /* attack object(user) to a name(userinfo) */
    /* attack an event(setNewData) to a name(setAge) */
  },
  // data() {
  //   return {
  //     userName: 'Mon',
  //     age: 31
  //   };
  // },
  // methods: {
  //   setNewAge() {
  //     this.age = 32;
  //   },
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
