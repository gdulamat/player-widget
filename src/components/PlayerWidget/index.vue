<template>
  <div class="widget-wrapp">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  created() {
    fetch("https://cors-anywhere.herokuapp.com/http://18.185.121.3:5000/", {
      mode: "cors"
    })
      .then(res => res.json())
      .then(res => console.log(res));
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
a {
  color: #42b983;
}

.widget-wrapp {
  width: 360px;
  height: 480px;
  background-color: #f3f4f8;
  border-radius: 30px;
  box-shadow: 0px 33px 60px -25px rgba(0, 0, 0, 0.6);
}
</style>
