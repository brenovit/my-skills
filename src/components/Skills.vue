<template>
  <div class="hello">
    <div class="holder">
      <ul>
        <li v-for="(data, index) in skills" :key="index">
          {{index}}.{{data.skill}}
        </li>
      </ul>
    </div>

    <div v-bind:class="{ warning: showAlert, 'box-border': showBorder }"></div>
    <div v-bind:class="alertObject"></div>
    <div v-bind:style="{ 
      backgroundColor: bgColor, 
      width: bgWidth, 
      height: bgHeight }"
      class="box-border"></div>

    <p v-if="skills.length > 1">You have more than 1 skill</p>
    <p v-else-if="skills.length == 1">You get the first skill</p>
    <p v-else>You don't have skills</p>
    
  </div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      skills: [
        { "skill" : "VueJs" },
        { "skill" : "Java" }
      ],
      showAlert: true,
      showBorder: true,
      alertObject: {
        error: true,
        "box-border": true
      },
      bgColor: "blue",
      bgWidth: "100%",
      bgHeight: "30px"
    }
  },
  props: {
    msg: String
  },
  methods: {
    changeName(){
      this.name = "Breno Arantes";
    }
  }
}
</script>

<style scoped>
  .warning{
    background-color: yellow;
    width: 100%;
    height: 30px;
  }
  .error{
    background-color: red;
    width: 100%;
    height: 30px;
  }
  .box-border {
    border: 5px solid black;
  }

</style>
