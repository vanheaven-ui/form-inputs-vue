<template>
  <form>
    <label>Email:</label>
    <input type="email" v-model="email" />

    <label>Password:</label>
    <input type="password" v-model="password" />

    <label>Role:</label>
    <select v-model="role">
      <option value="Frontend developer">Frontend developer</option>
      <option value="Backend developer">Backend developer</option>
      <option value="Web designer">Web designer</option>
      <option value="Full-stack developer">Full-stack developer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <p class="pill" v-for="skill in skills" :key="skill">{{ skill }}</p>

    <input type="checkbox" v-model="terms" />
    <label>Accept terms and conditions</label>

    <div>
      <input type="checkbox" value="Ezekiel" v-model="names" />
      <label>Ezekiel</label>
    </div>

    <div>
      <input type="checkbox" value="Angel" v-model="names" />
      <label>Angel</label>
    </div>

    <div>
      <input type="checkbox" value="Cherubim" v-model="names" />
      <label>Cherubim</label>
    </div>
  </form>
  <div class="output">
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms &#38; conditions accepted: {{ terms }}</p>
    <p>Names: {{ names }}</p>
    <p>Skills: {{ skills }}</p>
  </div>
</template>

<script>
export default {
  name: "SignupForm",
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      names: [],
      tempSkill: "",
      skills: [],
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        this.skills.push(this.tempSkill);
      }
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background-color: #fff;
  text-align: center;
  padding: 40px;
  border-radius: 10px;
  text-align: left;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 25px auto 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input,
select {
  display: block;
  width: 100%;
  padding: 10px 6px;
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
</style>