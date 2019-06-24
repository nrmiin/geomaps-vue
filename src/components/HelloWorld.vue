<template>
  <div id="app">
    <div class="map-wrapper">
      <h2 v-if="province" class="province-title">{{ province.state }}</h2>
      <div v-if="currentProvince" class="province-info">
        <h3 class="text-center">{{ currentProvince.state }}</h3>
        <ul>
          <li>cartodb_id: {{ currentProvince.cartodb_id }}</li>
          <li>slug: {{ currentProvince.slug }}</li>
        </ul>
      </div>
      <svg></svg>
    </div>
    <div class="container">
      <p>Reference</p>
      <ul>
        <li>
          <a href="https://bl.ocks.org/john-guerra/43c7656821069d00dcbc"
            >https://bl.ocks.org/john-guerra/43c7656821069d00dcbc</a
          >
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
