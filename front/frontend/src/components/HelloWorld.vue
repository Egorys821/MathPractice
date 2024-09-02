<script setup>
import { ref } from 'vue'


const page = ref(0)


function getImageUrl(page) {
console.log(page)
  return `/pages/scan_${page}.jpg`
}

function getRandomNumber() {


  page.value = Math.floor(Math.random() * 100 + 2);

  const mynew = document.getElementById("container");
  const myimg = document.getElementById("myimg");
  

mynew.addEventListener("mousemove",onZoom)
mynew.addEventListener("mouseover",onZoom)
mynew.addEventListener("mouseleave",offZoom)

function onZoom(e) {
 const x = e.clientX - e.target.offsetLeft;
 const y = e.clientY - e.target.offsetTop;
  myimg.style.transformOrigin = `${x}px ${y}px`;
myimg.style.transform = "scale(2)";
}


function offZoom(e) {
  myimg.style.transformOrigin = `center center`;
myimg.style.transform = "scale(1)";
}
}



</script>

<template>

  <div class="card">
    <button type="button" @click="getRandomNumber()">Get Random page</button>
    <div class="container" id="container">
    <img id="myimg" class="img" :src="getImageUrl(page)" alt="">
  </div>
  </div>
  
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
.button {
color: red;
border: 1px solid black;
}

img {
  height:100%;
  width: 100%;
  transform-origin: center center;
  object-fit: cover;
  transform: scale(1);
  cursor: pointer;
}
.container{
width: 900px;
border: 1px solid black;
overflow: hidden;

}
</style>
