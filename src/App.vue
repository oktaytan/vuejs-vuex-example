<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}

#app,
.home {
  height: 100%;
}
body {
  background-color: #f4f4f4;
  margin: 0;
  height: 100vh;
}

.title {
  color: #3d3d3d;
}

.rm {
  float: right;
  background: none;
  cursor: pointer;
  background-color: #f03d3d;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  color: #fff;
  transition: background-color 0.25s ease;
  outline: none;
}

.rm:hover {
  background-color: #ac2c2c;
}
</style>
