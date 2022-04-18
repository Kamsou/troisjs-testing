<script lang="ts">
import { defineComponent } from 'vue'
import {  Camera,  AmbientLight, Renderer, Scene, GltfModel } from 'troisjs';

export default defineComponent({
  name: 'Model',
  components: {  Camera,  AmbientLight, Renderer, Scene, GltfModel },
})
</script>
<template>
  <div class="container">
    <Renderer resize="window" orbit-ctrl ref="renderer">
      <Camera :position="{ z: 1 }" />
      <Scene background="#fff">
        <AmbientLight :intensity="4" />
        <GltfModel
          src="/models/horse/horse.gltf"
        />
      </Scene>
    </Renderer>
  </div>
</template>