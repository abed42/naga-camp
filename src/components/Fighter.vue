<script setup lang="ts">
import { TresCanvas, useLoader } from '@tresjs/core'
import { BasicShadowMap, SRGBColorSpace, NoToneMapping } from 'three'
import { OrbitControls, Stars} from '@tresjs/cientos'
// @ts-ignore
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';
import { useGLTF } from '@tresjs/cientos';

// @ts-ignore
// const { scene } = await useLoader(GLTFLoader, '/models/scene.glb')
// const { nodes, materials } = await useGLTF('/models/houston.glb', { draco: true })


// const { scene, nodes, animations, materials } = await useGLTF('./models/scene.glb')

// console.log(nodes)
const gl = {
  clearColor: '#181C3E',
  shadows: true,
  alpha: false,
  shadowMapType: BasicShadowMap,
  outputColorSpace: SRGBColorSpace,
  toneMapping: NoToneMapping,
}

// const loader = new GLTFLoader();

// const scene = new THREE.Scene();

// loader.load( './public/models/scene.gltf', function ( gltf ) {

// 	scene.add( gltf.scene );

// }, undefined, function ( error ) {

// 	console.error( error );

// } );

</script>

<template>
  <div class="tres-container">
    <TresCanvas v-bind="gl">
    <TresPerspectiveCamera :position="[5,5,5]" :look-at="[0,1,0]" />
    <OrbitControls />
    <Stars />
    <Suspense>
      <Houston />
    </Suspense>
    <TresAmbientLight :intensity="1" />
    <TresDirectionalLight
      :position="[-4, -2, 2]"
      :intensity="1"
      cast-shadow
      color="#fff"
    />
    <TresDirectionalLight
      :position="[4, 6, 4]"
      :intensity="2"
      cast-shadow
      color="white"
    />
  </TresCanvas>
  </div>

</template>

<style>
.tres-container {
  width: 100%;
  height: 300px;
}
canvas {
  width: 100%;
  height: 100%;
}
</style>