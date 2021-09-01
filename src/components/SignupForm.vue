<template>
  <form>
    <label>Email:</label>
    <input type="email" />
  </form>
</template>

<script>
export default {
  name: "SignupForm",
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

input {
  display: block;
  width: 100%;
  padding: 10px 6px;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
</style>