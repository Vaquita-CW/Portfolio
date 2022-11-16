<template>
  <div>
    <h1>Welcome!</h1>
    <NLink to="/about">
      About Page
    </NLink>
    <client-only>
      <canvas></canvas>
    </client-only>
  </div>
</template>

<script>
import * as THREE from 'three';
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';

export default {
    head: {
        title: "Home page",
    }
}
const renderer = new THREE.WebGLRenderer();
renderer.setSize( window.innerWidth, window.innerHeight );
document.body.appendChild( renderer.domElement );

const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera( 45, window.innerWidth / window.innerHeight, 1, 10000 );

var loader = new GLTFLoader();
loader.load( 'static/Orca.glb', function (gltf) {
mixer = new THREE.AnimationMixer(gltf.scene);
var action = mixer.clipAction( gltf.animations[0] );
action.play();
action.setEffectiveTimeScale(0.7);
gltf.scene.scale.set(gltf.scene.scale.x * 5,gltf.scene.scale.y * 5,gltf.scene.scale.z * 5);
gltf.scene.traverse( child => {
  if (child.material) {
    child.material.metalness = 0.0;
    child.material.roughness = 0.0;
  }
} );
scene.add(gltf.scene);
model = gltf.scene;
//model.rotation.set(0,Math.PI,0);
model.position.set(10,10,0);
model.rotation.y = Math.PI/2
});

const controls = new OrbitControls( camera, renderer.domElement );

//controls.update() must be called after any manual changes to the camera's transform
camera.position.set( 0, 20, 100 );
controls.update();

function animate() {

	requestAnimationFrame( animate );

	// required if controls.enableDamping or controls.autoRotate are set to true
	controls.update();

	renderer.render( scene, camera );

}

animate();
</script>
