<template>
  <h2>{{ userName }}</h2>
  <h3>{{ age }}</h3>
</template>

<script>
export default {
  props: ['userName', 'age'],
  //Define props in UserData(child)
};
</script>
