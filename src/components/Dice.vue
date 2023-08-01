<template>
  <canvas id="bg"></canvas>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import * as THREE from 'three';
import { RapierPhysics } from 'three/addons/physics/RapierPhysics.js';

// Function to create the 3D scene
async function createScene() {  
  const physics = await RapierPhysics();
  // physics.setGravity(0, -9.81, 0)

  const scene = new THREE.Scene()
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

  // Creating a floor
  const floor = new THREE.Mesh(
    new THREE.PlaneGeometry( 50, 50 ), //This functions as geometry
    new THREE.MeshBasicMaterial( {color: 'green', side: THREE.DoubleSide} ) //this functions as material
  );
  floor.position.y = -10.5;
  floor.rotation.x = THREE.MathUtils.degToRad(90);
  floor.receiveShadow = true;
  scene.add( floor );
  physics.addMesh( floor );

  // Create an icosahedron
  const geometry = new THREE.IcosahedronGeometry( 2 );
  const material = new THREE.MeshStandardMaterial({ color: 'red'});
  const icosahedron = new THREE.Mesh(geometry, material);
  icosahedron.position.y = +15
  scene.add(icosahedron);
  physics.addMesh( icosahedron );

  // PointLight (color, intensity, dsitancy, decay)
  const light = new THREE.HemisphereLight( 0xffffbb, 0x080820, 2 );
  scene.add( light );
  // Position the camera
  camera.position.z = 30;

  // Create a render loop
  function animate() {
    requestAnimationFrame(animate);
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