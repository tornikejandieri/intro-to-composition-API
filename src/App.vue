<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ userAge }}</h3>
    <button @click="setAge">Change Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" v-model="lastName" />
    </div>
  </section>
</template>

<script>
import { ref, computed, watch } from 'vue';

export default {
  setup() {
    // const uName = ref('Maximilian');
    const firstName = ref('');
    const lastName = ref('');

    const uAge = ref(13);
    // const user = reactive({
    //   name: 'Maximilian',
    //   age: 31,
    // });

    const uName = computed(() => {
      return firstName.value + ' ' + lastName.value;
    });

    const setNewAge = () => {
      uAge.value = 32;
    };
    watch([uAge, uName], (newValues, oldValues) => {
      console.log('old age:' + oldValues[0]);
      console.log('new age:' + newValues[0]);
      console.log('old name:' + oldValues[1]);
      console.log('new name:' + newValues[1]);
    });
    return {
      userName: uName,
      userAge: uAge,
      setAge: setNewAge,
      firstName,
      lastName,
    };
  },

  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
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
