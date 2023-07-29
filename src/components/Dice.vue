<template>
  <canvas id="bg"></canvas>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import * as THREE from 'three';

// Function to create the 3D scene
function createScene() {  

  const scene = new THREE.Scene()
  // wet to white so I can see the object. 
  scene.background = new THREE.Color('white')
  const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000)
  // Create a new renderer
  const renderer = new THREE.WebGLRenderer({
    canvas: document.querySelector('#bg'),
  })
  renderer.setPixelRatio( window.devicePixelRatio );
  renderer.setSize( window.innerWidth, window.innerHeight );
  camera.position.setZ(30);
  renderer.render( scene, camera ) 
  // Create an icosahedron
  const geometry = new THREE.IcosahedronGeometry( 8 );
  const material = new THREE.MeshStandardMaterial({ color: 'red'});
  const icosahedron = new THREE.Mesh(geometry, material);
  scene.add(icosahedron);

  // Light 
  const pointLight = new THREE.PointLight(0xffffff, 1, 100)
  pointLight.position.set(5,5, 5 )
  scene.add(pointLight)
  // Position the camera
  camera.position.z = 30;

  // Create a render loop
  function animate() {
    requestAnimationFrame(animate);
    icosahedron.rotation.x += 0.01;
    icosahedron.rotation.y += 0.01;
    icosahedron.rotation.z += 0.01;
    renderer.render(scene, camera);
  }

  animate();
}

// Call createScene on component mount
onMounted(() => {
  createScene();
});
</script>

<style>
/* #bg {
  display: block;
} */
</style>
