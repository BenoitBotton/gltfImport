<template>
    <TresGroup :rotation-z="cutter.theta * toRad" :key="cutter.spiral">
        <TresGroup :position-z="cutter.ztip">
            <TresGroup :position-x="cutter.radius">
                <TresGroup :rotation-y="cutter.yrot * toRad">
                    <TresGroup :rotation-z="-cutter.siderake * toRad">
                        <TresGroup :rotation-x="cutter.backrake * toRad">
                            <TresMesh :position="cutter.spiral < 500 ? [0, 0, -r] : [0, 0, 0]"
                                :rotation="[90 * toRad, 0, 0]">
                                <Suspense fallback={null}>
                                    <Cylinder_1013_base :color="color" :scale="[cutter.dia/10,cutter.dia/10,cutter.lgth/13.2]"/>
                                </Suspense>
                            </TresMesh>
                        </TresGroup>
                    </TresGroup>
                </TresGroup>
            </TresGroup>
        </TresGroup>
    </TresGroup>
</template>

<script setup lang="ts">
import Cylinder_1013_base from './components/Cylinder_1013_base.vue'

type Cutter = {
    spiral: number
    ctype: string
    shape: string
    dia: number
    lgth: number
    backrake: number
    siderake: number
    yrot: number
    ztip: number
    radius: number
    theta: number
    color: string
}

const props = defineProps<{
    cutter: Cutter
    color: string
}>()

const r = props.cutter.dia / 2
const toRad = Math.PI / 180
</script>

<style scoped></style>