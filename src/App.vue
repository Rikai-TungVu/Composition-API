<template>
  <section class="container">
    <h2>{{ userinfo.name }}</h2>
    <h3>{{ userinfo.age }}</h3>
  </section>
</template>

<script>
import { reactive } from 'vue';
/* import { reactive } from 'vue'; */
// ref work with single data
// reactive work with group data

export default {
  setup() {
    //  const uName = ref('Monday');
    //  const uAge = ref(31);
    const user = reactive({
      name: 'Monday',
      age: 31,
    });

    setTimeout(function () {
      // user.value.name = 'Mon'; (ref)
      // user.value.age = 32; (ref)
      user.name = 'Mon';
      user.age = 32;
    }, 2000);
    /* Sự dụng ref còn thêm .value để chỉ biến */

    return { userinfo: user };
    /* return result to 1 variable */
  },
  /* data() {
    return {
      userName: 'Mon',
    };
  }, */
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
