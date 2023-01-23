<template>
  <section class="container">
    <h2>{{ userinfo.name }}</h2>
    <h3>{{ userinfo.age }}</h3>
    <button @click="setAge">Change Age</button>
  </section>
</template>

<script>
import { reactive } from 'vue';
/* import { reactive } from 'vue'; */
// ref work with single data(.value)
// reactive work with group data

export default {
  setup() {
    //  const uName = ref('Monday');
    //  const uAge = ref(31);
    const user = reactive({
      name: 'Monday',
      age: 31,
    });

    function setNewData() {
      user.age = user.age + 1;
    }

    return { userinfo: user, setAge: setNewData };
    /* attack object(user) to a name(userinfo) */
    /* attack an event(setNewData) to a name(setAge) */
  },
  /* data() {
    return {
      userName: 'Mon',
      age: 31
    };
  }, */
  methods: {
    setNewAge() {
      this.age = 32;
    },
  },
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
