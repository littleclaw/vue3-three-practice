<template>
    <div id="canvas"></div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import * as THREE from 'three'
const scene = new THREE.Scene()
const geometry = new THREE.BoxGeometry(100, 100, 100)
const material = new THREE.MeshBasicMaterial({
    color: 0xff0000,
})
const mesh = new THREE.Mesh(geometry, material)
mesh.position.set(0, 10, 0)
scene.add(mesh)

const width = 800
const height = 500
// 30:视场角度, width / height:Canvas画布宽高比, 1:近裁截面, 3000：远裁截面
const camera = new THREE.PerspectiveCamera(30, width / height, 1, 3000)
camera.position.set(200, 200, 200)
camera.lookAt(mesh.position)
const renderer = new THREE.WebGLRenderer()
renderer.setSize(width, height)

onMounted(() => {
    document.querySelector('#canvas').appendChild(renderer.domElement)
    renderer.render(scene, camera)
})
</script>

<style scoped lang="scss">
#canvas {
    width: 100%;
    height: 100%;
}
</style>