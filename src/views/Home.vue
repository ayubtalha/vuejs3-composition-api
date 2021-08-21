<template>
  <!-- 
    ------------------
    REFS VS REACTIVITY -->
  <div class="home">Home</div>

  <p>{{ ninjaOne.name }} -- {{ ninjaOne.age }}</p>
  <button @click="updateNinjaOne">Click Me</button>

  <p>{{ ninjaTwo.name }} -- {{ ninjaTwo.age }} -- {{ nameTwo }}</p>
  <button @click="updateNinjaTwo">Click Me</button>

  <!--
    ---------------- 
  REACTIVITY WITH REFS
  <div class="home">Home</div>
  <p>Name is {{ name }}</p>
  <p>Age is {{ age }}</p>
  <button @click="handleClick">Click Me</button>

  <input type="text" v-model="name" /> -->
</template>

<script>
// ----------------------------------
// REFS VS REACTIVITY

import { reactive, ref } from "@vue/reactivity";
export default {
  name: "Home",
  setup() {
    const ninjaOne = ref({ name: "Talha", age: 25 });
    const ninjaTwo = reactive({ name: "Khan", age: 30 });

    const nameOne = ref("iamtalha");
    const nameTwo = reactive("iamkhan"); //reactive doecnt work like this

    const updateNinjaOne = () => {
      ninjaOne.value.name = "Khan";
    };

    const updateNinjaTwo = () => {
      ninjaTwo.name = "Ayub";
      nameTwo("iam"); // wont update reactive as it doesnt has the 'value'
    };

    return { ninjaOne, ninjaTwo, nameTwo, updateNinjaOne, updateNinjaTwo };

    // ----------------------------------------
    // let name = "Talha";
    // let age = 25;

    // // Template REFs - ref shouldnt be used before returing value
    // const p = ref(null);

    // const handleClick = () => {
    //   console.log("You clicked me");
    //   console.log(p.value);
    //   p.value.classList.add("test");
    //   p.value.textContent = "hello, ninjas";
    // };

    // return { name, age, handleClick, p };
  },
};

// ----------------------------------
//  REACTIVITY WITH REFS
// import { ref } from "@vue/reactivity";
// export default {
//   name: "Home",
//   components: {},
//   setup() {
//     // REACTIVITY WITH REFS
//     const name = ref("Talha");
//     const age = ref(25);

//     const handleClick = () => {
//       // updating the ref value
//       console.log("You clicked me");
//       name.value = "Khan";
//       age.value = "30";
//     };

//     return { name, age, handleClick };

//     // ----------------------------------------
//     // let name = "Talha";
//     // let age = 25;

//     // // Template REFs - ref shouldnt be used before returing value
//     // const p = ref(null);

//     // const handleClick = () => {
//     //   console.log("You clicked me");
//     //   console.log(p.value);
//     //   p.value.classList.add("test");
//     //   p.value.textContent = "hello, ninjas";
//     // };

//     // return { name, age, handleClick, p };
//   },
// };
</script>
