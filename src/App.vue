<template>
  <!-- Router view  -->
  <router-view />
  <!-- Router view  -->
</template>

<script>
export default {
  name: "App",
};
</script>

<style lang="scss">
* {
  // Normalize styling
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  // Importing google font
  @import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap");
  font-family: "Open Sans", sans-serif;
}
body{
    background: linear-gradient(78.84deg, #e63c01 3%, #fd8c00 96.8%);
}

::-webkit-scrollbar {
  width: 5px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: #2222;
  cursor: pointer;
}

::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>
