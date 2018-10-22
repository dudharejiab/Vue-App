<template>
  <div class="hello">
    <div class="holder">

      <form @submit.prevent="addSkill">
        <input type="text" placeholder=" Enter a skill " v-model="skill" v-validate="'min:5'" name="skill">
        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">  
          <p class="alert" v-if="errors.has('skill')"> {{ errors.first('skill') }} </p>
          <!-- <input type="checkbox" id="checkbox" v-model="checked"> -->
        </transition>
      </form>

      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown" > 
          <li v-for="(data, index) in skills" :key='index'> 
            {{data.skills}} 
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
      </ul>
      <p>These are the skill sets that you have. &#128540; </p>
     </div>
  </div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      checked: false,
      skill: "",
      skills: [
        { skills: "Vue.js" },
        { skills: "Angular 2" },
        { skills: "React JS" },
        { skills: "Angular 4/5/6" }
      ],
     alertObject: {
        alert: true
      }
    }
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if(result){
          this.skills.push({skills: this.skill })
          this.skill = '';
        } else {
          console.log("Not valid");
        }
      })
    },
    remove(id){
      this.skills.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="./skills.css" scoped>
</style>
