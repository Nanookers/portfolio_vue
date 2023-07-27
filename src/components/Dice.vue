<template>
<!-- Set up divs for the dice each side will have  -->
    <div class="skillCheck">
        <div class="icosahedron">
            <div class="dieFace"></div>
            <div class="dieFace"></div>
            <div class="dieFace"></div>
            <div class="dieFace"></div>
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
  width: 100;
  height: 1000;
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
  transform: rotateY(0deg) rotateX(33deg) translateZ(85.56px) ;
  background-color: rgb(235, 232, 232);
}

.dieFace:nth-child(2) {
  transform:  rotateY(58deg) rotateX(35deg) rotateZ(90deg) translateZ(130.56px) translateX(-17px) translateY(106px);
}

.dieFace:nth-child(3) {
  transform: rotateY(299deg) rotateX(35.264deg) rotateZ(268deg) translateZ(76.56px) translateX(55px) translateY(3px);
}
.dieFace:nth-child(4) {
  transform: rotateY(0deg) rotateX(147deg) translateZ(85.56px)  translateY(-2px);
  background-color: rgb(235, 232, 232);
}
.dieFace:nth-child(5) {
  /* transform: rotateY(333deg) rotateX(339deg) rotateZ(246deg) translateZ(81.56px) translateX(24px) translateY(27px); */
  transform: rotateY(299deg) rotateX(35.264deg) rotateZ(87deg) translateZ(-59.44px) translateX(-48px) translateY(77px);
  
}
.dieFace:nth-child(6) {

    transform: rotateY(58deg) rotateX(35.264deg) rotateZ(270deg) translateZ(36.56px) translateX(-24px) translateY(-119px);
}
.dieFace:nth-child(7) {
  transform: rotateY(246deg) rotateX(358deg) rotateZ(91deg) translateZ(50.56px) translateY(348px) translateX(-43px);
}

.dieFace:nth-child(8) {
  transform: rotateY(74deg) rotateX(180deg) rotateZ(90deg) translateZ(50.56px) translateY(131px) translateX(47px);
}
</style>
