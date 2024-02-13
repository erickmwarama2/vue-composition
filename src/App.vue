<template>
  <section class="container">
    <h2>{{ computedUserName }}</h2>
    <h2>{{ userName }}</h2>
    <h2>{{ age }}</h2>
    <p>
      {{ user.name }}
      {{ user.age }}
    </p>
    <button @click="changeAge"> Change Age </button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName"/>
      <input type="text" placeholder="Last Name" v-model="lastName"/>
    </div>
  </section>
</template>

<script>
import { ref, reactive, toRefs, computed } from 'vue';
export default {
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
  setup() {
    // const userName = ref('Erick');
    const firstName = ref('');
    const lastName = ref('');
    // const age = ref(32);
    const user = reactive({
      name: 'Erick',
      age: 31
    });

    const computedUserName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    setTimeout(() => {
      // userName.value = 'Mutwiri';
      user.name = 'Mr. Mutwiri';
      user.age = 32;
    }, 2000);

    const changeAge = () => {
      user.age = 35;
    };

    const setFirstName = (evt) => {
      firstName.value = evt.target.value;
    }

    const setLastName = (evt) => {
      lastName.value = evt.target.value;
    }

    const userRefs = toRefs(user);

    return {
      userName: userRefs.name,
      age: userRefs.age,
      user,
      changeAge,
      firstName,
      lastName,
      setFirstName,
      setLastName,
      computedUserName,
    }
  }
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