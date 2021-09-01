<template>
  <form @submit.prevent="createAccount">
    <label>Email:</label>
    <input type="email" v-model="email" />

    <label>Password:</label>
    <input type="password" v-model="password" />
    <div>
      <p>{{ passwordError }}</p>
    </div>

    <label>Role:</label>
    <select v-model="role">
      <option value="Frontend developer">Frontend developer</option>
      <option value="Backend developer">Backend developer</option>
      <option value="Web designer">Web designer</option>
      <option value="Full-stack developer">Full-stack developer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div>
      <p
        class="pill"
        v-for="skill in skills"
        :key="skill"
        @click="rmSkill(skill)"
      >
        {{ skill }}
      </p>
    </div>

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
    <div class="submit">
      <button>Create an Account</button>
    </div>
  </form>
  <div class="backdrop" v-if="showResults" @click.self="closeBackdrop">
    <div class="output">
      <h2>Data collected from form(For DB or server or anything)</h2>
      <p>Email: {{ email }}</p>
      <p>Password: {{ password }}</p>
      <p>Role: {{ role }}</p>
      <p>Terms &#38; conditions accepted: {{ terms }}</p>
      <p>Names: {{ names }}</p>
      <p>Skills: {{ skills }}</p>
    </div>
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
      passwordError: "",
      showResults: false,
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = "";
      }
    },

    rmSkill(item) {
      this.skills = this.skills.filter((skill) => skill !== item);
    },
    createAccount() {
      this.showResults = true;
      if (this.password.length < 5) {
        this.passwordError = "⚠️ The password should be atleast 5 chars long!";
      }
    },
    closeBackdrop() {
      this.showResults = false;
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

.pill {
  padding: 6px 12px;
  background-color: #eee;
  border: none;
  display: inline-block;
  margin: 20px 10px 0 0;
  cursor: pointer;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
}

.pill:hover {
  opacity: 0.8;
}

.submit {
  text-align: center;
}

.submit button {
  background-color: blue;
  border-radius: 20px;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  color: #fff;
}

.submit button:hover {
  opacity: 0.7;
}

.backdrop {
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  width: 100%;
  height: 100%;
  cursor: pointer;
}

.backdrop:hover {
  background-color: rgba(0, 0, 0, 0.7);
}

.output {
  width: 500px;
  margin: 10px auto 0 20px;
  background: #fff;
  text-align: left;
  border-radius: 20px;
  padding: 10px;
  transition: all 0.3s ease-in-out;
}
</style>