<script>
import { ref } from "vue";

export default {
  data() {
    return {
      email: ref(''),
      password: ref(''),
      role: ref(''),
      accept: ref(false),
      //aqours: ref([])
      tempSkill: ref(''),
      skills: ref([])
    }
  },
  methods: {
    addSkill(e) {
      //e is supplied automatically since it is tied to the @keyup event
      if(e.key === ',' && this.tempSkill)
      {
        //checks for possible dublicate skills and wont add it
        if(!this.skills.includes(this.tempSkill))
        {
          this.tempSkill = this.tempSkill.slice(0, -1);
          this.skills.push(this.tempSkill);

        }
        this.tempSkill = '';
      }
      //no need to use anything else to complicate things
    },

    deleteSkill(e){
      let deleteIndex = this.skills.indexOf(e);
      this.skills.splice(deleteIndex, 1);
    },
    handleSubmit() {
      console.log("Form Submitted");
    }
  }
}

</script>

<template>
  <form @submit.prevent="handleSubmit">
    <label>Email</label>
    <input type="email" required v-model="email">
    <label>Password</label>
    <input type="password" required v-model="password">
    <label>Role</label>
    <select v-model="role">
      <option>Web Developer</option>
      <option>Web Designer</option>
      <option>Project Manager</option>
      <option>Other</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill" @click="deleteSkill(skill)">
      {{skill}}
    </div>

    <div class="terms">
    <input type="checkbox" v-model="accept" required/>
    <label>Accept terms and conditions</label>
    </div>

    <div class="submit">
      <button>Create an account</button>
    </div>
<!--
    <p>Choose your favorite Aqours member:</p>
    <p>
    <input type="checkbox" value="Chika" v-model="aqours">
    <label>Chika</label>
    <input type="checkbox" value="Riko" v-model="aqours">
    <label>Riko</label>
    <input type="checkbox" value="Kanan" v-model="aqours">
    <label>Kanan</label>
    <input type="checkbox" value="Dia" v-model="aqours">
    <label>Dia</label>
    <input type="checkbox" value="You" v-model="aqours">
    <label>You</label>
    <input type="checkbox" value="Yoshiko" v-model="aqours">
    <label>Yoshiko</label>
    <input type="checkbox" value="Hanamaru" v-model="aqours">
    <label>Hanamaru</label>
    <input type="checkbox" value="Mari" v-model="aqours">
    <label>Mari</label>
    <input type="checkbox" value="Ruby" v-model="aqours">
    <label>Ruby</label>

    </p>
-->
  <p>Email: {{email}}</p>
  <p>Password: {{password}}</p>
  <p>Role: {{role}}</p>
  <p>Accept: {{accept}}</p>
    <p>Skills: {{skills}}</p>
    <p>TempSkill: {{tempSkill}}</p>

    <!--<p>Aqours: {{aqours}}</p> -->
  </form>
</template>

<style>

form{
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
  font-family: 'Roboto', sans-serif;

}
label{
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input, select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.pill{
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eeeeee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;}
button{
  background: #0b6dff;
  border: none;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}

.submit{
  text-align: center;
}

</style>