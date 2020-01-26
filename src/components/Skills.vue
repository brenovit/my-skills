<template>
  <div class="container">
    <div class="holder">
      <ValidationObserver v-slot="{ handleSubmit }">
        <form @submit.prevent="handleSubmit(addSkill)">
          <ValidationProvider name="skill" rules="min:5|max:10" v-slot="{ errors }">
            <input type="text" v-model="skill" placeholder="Enter a skill you have" />
            <transition
              name="alert-in"
              enter-active-class="animated flipInX"
              leave-active-class="animated flipOutX"
            >
              <p class="alert" v-if="errors[0]">{{errors[0]}}</p>
            </transition>
          </ValidationProvider>
        </form>
      </ValidationObserver>
      <ul>
        <transition-group
          name="list"
          enter-active-class="animated bounceInUp"
          leave-active-class="animated bounceOutDown"
        >
          <li v-for="(data, index) in skills" :key="index">
            {{data.skill}}
            <font-awesome-icon icon="minus-circle" pull="right" v-on:click="remove(index)" />
          </li>
        </transition-group>
      </ul>
    </div>

    <p v-if="skills.length > 1">These are the skills that you possess.</p>
    <p v-else-if="skills.length == 1">You get your first skill.</p>
    <p v-else>You don't have any skill. :(</p>
  </div>
</template>

<script>
import { ValidationProvider, ValidationObserver } from "vee-validate";

export default {
  components: {
    ValidationProvider,
    ValidationObserver
  },
  name: "Skills",
  data() {
    return {
      skills: [],
      skill: ""
    };
  },
  props: {
    msg: String
  },
  methods: {
    addSkill() {
      this.skills.push({ skill: this.skill });
      this.skill = "";
    },
    remove(index) {
      this.skills.splice(index, 1);
    }
  }
};
</script>

<style scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.2/animate.min.css";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

.holder {
  background: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}

p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687f7f;
}

.alert {
  background: #fdf2ce;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin-top: -20px;
}

.alert-in-enter-active {
  animation: bounce-in 0.5s;
}

.alert-in-leave-active {
  animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
</style>
