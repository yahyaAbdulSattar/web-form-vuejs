<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email" />
    <label>Password:</label>
    <input type="password" required v-model="password" />
    <div v-if="passwordError" class="error">
        <p>{{ passwordError }}</p>
    </div>
    <label>Select role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill" @click="handleClick">
      {{ skill }}
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Accept terms and conditions</label>
    </div>

    <div class="submit">
      <button>Create an account</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      tempSkill: "",
      skills: [],
      passwordError: ""
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill)
        }

        this.tempSkill = ""
      }
    },
    handleClick() {
      this.skills.pop()
    },
    handleSubmit(){
        this.passwordError = this.password.length > 5 ? '' : 'Password needs to be longer than 5 characters'

        if(!this.passwordError){
            console.log(this.email)
            console.log(this.password)
            console.log(this.role)
            console.log(this.skills)
            console.log(this.terms)
        }
    }
  },
};
</script>

<style>
</style>