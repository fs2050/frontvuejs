<template>
 
  <Header />
  <Content /> <h1 class="text-primary">Hello World</h1>
  <Footer />
</template>

<script>
import Header from "./components/Header";
import Content from "./components/Content";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Header,
    Content,
    Footer
  },
};
</script>

<style>
body {
  padding:0;
  margin: 0;

}

</style>
