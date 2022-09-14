<template>
  <div>
    <h4>Version 1.0.0</h4>
    <router-link class="btn-about" to="/">Go Back</router-link>
  </div>
</template>

<style scoped>
.btn-about {
  display: inline-block;
  background: red;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn-about:hover {
  opacity: 0.8;
}

.btn-about:focus {
  outline: none;
}

.btn-about:active {
  transform: scale(0.98);
}

.btn-about-block {
  display: block;
  width: 100%;
}
</style>
