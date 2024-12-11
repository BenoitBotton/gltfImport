<template>
    <primitive :object="model" />
</template>

<script setup async lang="ts">
import { useGLTF } from '@tresjs/cientos'
import * as THREE from "three"
import { shallowRef } from 'vue';

const props = defineProps<{
    color: string
    scale: number[]
}>()

const { scene } = await useGLTF('src/assets/cylinder_1013-transformed.glb', { draco: true })
const model = shallowRef(scene.clone())
const material = new THREE.MeshLambertMaterial({ color: props.color })
// const model = new THREE.Mesh(nodes.round_1013.geometry, material).clone()
model.value.scale.fromArray(props.scale)
</script>