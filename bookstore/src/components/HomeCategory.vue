<template>
  <div class="homeCategory">
    <h3>图书分类</h3>
    <div v-for="category in categories" key="category.id">
      <h5>{{ category.name }}</h5>
      <router-link
        v-for="child in category.children"
        :key="child.id"
        to="'/category/' + child.id"
        >child.name</router-link
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeCategory",
  data() {
    return {
      categories: [],
    };
  },
  created() {
    this.axios
      .get("/category")
      .then((response) => {
        if (response.status == 200) {
          this.categories = response.data;
        }
      })
      .catch((error) => alert(error));
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
