<template>
  <div class="home">
    <!-- name.value and age.value will be automatically used in the template -->
    <p ref="refP">Name: {{ name }}, Age: {{ age }}</p>

    <button @click="handleClick">Click me!</button>
    <button @click="++age" style="margin-left: 4px;">Increase age</button>

    <!-- name in the input field will be updated in the DOM -->
    <input type="text" style="margin-left: 4px;" v-model="name">

  </div>
</template>

<script>
import { ref } from 'vue'

// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  
  // 1st order
  setup() {
    // values in setup are not reactive values
       
    // let name_in_setup = 'ta2lsm'
    // let age_in_setup = 39
    // return { name: name_in_setup, age: age_in_setup}
    
    // variables (not reactive. they can be changed but will not be updated in the DOM)
    // let name = 'ta2lsm'
    // let age = 39

    const name = ref('ta2lsm')
    const age = ref(39)

    // refs
    const refP = ref(null)
    //console.log(refP, refP.value)   // can't use refP before returns it below. refP will be null at this point...

    // functions
    const handleClick = () => {
      // // console.log('Button clicked')
      // console.log("refP: ", refP)
      // console.log("refP Value: ", refP.value)

      // refP.value.classList.add('test')                // add class named 'test' to paragraph
      // refP.value.textContent = 'NEW TEXT CONTENT'     // change paragraph's text content

      // name = 'John'         // this will change value of name but will not be updates in the DOM
      name.value = 'John'     // if "name" is defined as a ref, when we change its value it will be updated in the DOM also
      age.value = 18
    }

    return { name, age, handleClick, refP }
  },

  // 2nd order
  data() {
    return {
      // values in data are reactive values. Changes of them will be reflected in template
      score: 5
    }
  },

  // // 3rd order
  // created() {

  // },

  // // 4th order
  // mounted() {

  // }
}
</script>
