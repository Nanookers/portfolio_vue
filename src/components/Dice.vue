<template>
  <canvas id="bg"></canvas>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';
import * as THREE from 'three';
import { TTFLoader } from 'three/examples/jsm/loaders/TTFLoader'; 
import { FontLoader } from 'three/examples/jsm/loaders/FontLoader'; 
import { TextGeometry } from 'three/examples/jsm/geometries/TextGeometry'; 
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

  const fontLoader = new FontLoader();
  fontLoader.load(
    'node_modules/three/examples/fonts/helvetiker_bold.typeface.json',
    ( helvetiker: string ) => {
      const textGeometry = new TextGeometry('Skill Check', {
        height: 2, 
        size: 2,
        font: helvetiker
      });
      const textMaterial = new THREE.MeshNormalMaterial();
      const textMesh = new THREE.Mesh(textGeometry, textMaterial)
      textMesh.position.x = -36;
      textMesh.position.y = 5;
      scene.add(textMesh)
    }
  );



  // PointLight (color, intensity, dsitancy, decay)
  const light = new THREE.HemisphereLight( 0xffffbb, 0x080820, 2 );
  scene.add( light );
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
