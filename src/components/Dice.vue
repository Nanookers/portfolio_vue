<template>
<!-- Set up divs for the dice each side will have  -->
    <div class="skillCheck">
        <div class="icosahedron">
            <div class="dieFace"></div>
            <div class="dieFace"></div>
            <div class="dieFace"></div>
            <div class="dieFace"></div>
        </div>
        <div id="roll" class="rollButton">
            <!-- <button>Check Skill!</button> -->
        </div>
    </div>
</template>

<script lang="ts">

</script>

<style scoped>
.icosahedron {
  width: 0;
  height: 0;
  position: relative;
  transform-style: preserve-3d;
}
.dieFace{
  position: absolute;
  width: 100px; /* Adjust the size of the triangles as needed */
  height: 100px;
  background-color: #ccc; /* Adjust the colors and styles as needed */
  clip-path: polygon(50% 0%, 100% 100%, 0% 100%); /* Create an equilateral triangle */
  transform-origin: 50% 100%;
}
.dieFace:nth-child(1) {
  transform: rotateY(0deg) rotateX(35.264deg) translateZ(85.56px);
}

.dieFace:nth-child(2) {
  transform:  rotateY(30deg) rotateX(35.264deg) rotateZ(76deg) translateZ(169.56px) translateX(-3px) translateY(52px);
}

.dieFace:nth-child(3) {
  transform: rotateY(-30deg) rotateX(35.264deg) rotateZ(284deg) translateZ(85.56px) translateX(47px) translateY(-19px);
}
.dieFace:nth-child(4) {
  transform: rotateY(0deg) rotateX(147deg) translateZ(85.56px)  translateY(52px);
}

</style>
