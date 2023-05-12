<template>
  <div class="app">
      <p>{{ name }} - {{ age }}</p>
      <button @click="changeName('Zelda')">change name</button>
      <button @click="changeAge('30')">change age</button>
      
      <!-- <p>{{ jobs[0].location }}</p> -->
    </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue'

export default defineComponent({
    components:{},
    setup() {
      // const state = reactive({
      //   name: "Link",
      //   age : 25 as number | string
      // }); 

      const name = ref('Sam');
      const age = ref<string | number >(25);

      const changeName = (n:string) => {
          // state.name = name;
          name.value = n;
          return name;
        };
      const changeAge = (a: string | number) => {
          // state.age = age;
          age.value = a
          return age;
      }
      return {
        // ...toRefs(state), 
        name,
        age,
        changeName, 
        changeAge
      };
    }
})
</script>

<style scoped>

</style>
