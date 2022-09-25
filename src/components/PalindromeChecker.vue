<template>
  <span>O termo </span>
  <strong>{{ text }}</strong>
  <span v-if="isPalindrome"> é um </span>
  <span v-else> não é um </span>
  <span>palíndromo</span>
</template>

<script>
const getValue = (parameter) => {
  const paramsList = window.location.href.split("?")[1]?.replace("?", "").split("&");
  if (paramsList) {
    const value = paramsList.filter(item => item.includes(parameter));
    return value[0].split("=")[1];
  }
  return null;
}

const checker = (value) => {
  return value.split("").reverse().join("") === value;
}

export default {
  name: 'PalindromeChecker',

  data() {
    return {
      text: "",
      isPalindrome: false
    }
  },

  mounted() {
    const value = getValue("text");
    this.isPalindrome = checker(value);
    this.text = value;
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
