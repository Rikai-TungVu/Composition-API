<template>
  <section class="container">
    <user-data :first-name="firstName" :last-name="lastName"></user-data>
    <!-- call UserData(child) -->
    <!-- bind data -->
    <!-- (3)Working with Provide/ Inject -->
    <!-- :user-name="userName" -->
    <!-- :age="age" -->
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <!-- <input type="text" placeholder="First Name" @input="setFirstName" /> -->
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <!-- receive lastname.value from function setLastname-->
      <!-- <input type="text" placeholder="Last Name" @input="setLastname" /> -->
      <button @click="setLastName">Set Last Name</button>
    </div>
  </section>
</template>

<script>
import './components/graphic/setting.css';

import UserData from './components/Data/UserData.vue';
import { ref, computed, watch, provide } from 'vue';
/* import { ref } from 'vue'; */
// ref work with single data(.value)
// reactive work with group data

export default {
  components: {
    UserData,
    // Define componemt in App.vue(parent)
  },
  setup() {
    // const uName = ref('Monday');
    const firstName = ref('');
    const lastName = ref('');
    const lastNameInput = ref(null);
    const uAge = ref(31);
    // const user = reactive({
    //   name: 'Monday',
    //   age: 31,
    // });

    provide('userAge', uAge);
    // (3)Working with Provide/ Inject
    // define data to provide in App(parent), data store

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

    function setLastName() {
      // lastName.value = this.$refs.lastNameInput.value;
      lastName.value = lastNameInput.value.value;
    } /* transfer lastname.value from function setLastName to action lastNameInput(ref) */

    return {
      userName: uName,
      age: uAge,
      setAge: setNewData,
      // setFirstName,
      setLastName,
      firstName,
      lastName,
      lastNameInput,
    };
    /* attack object(user) to a name(userinfo) */
    /* attack an event(setNewData) to a name(setAge) */
  },
  // Options API
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
  // provide() {
  //   return { age: this.age };
  // }
};
</script>
