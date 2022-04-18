<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue'
import { Box, Camera, BasicMaterial, PointLight, Renderer, Scene, Sphere, Texture } from 'troisjs';

export default defineComponent({
  name: 'Home',
  components: { Box, Camera, BasicMaterial, PointLight, Renderer, Scene, Sphere, Texture },
  setup() {
    const renderer = ref(null)
    const sphere = ref(null)

    onMounted(() => {
      renderer?.value?.onBeforeRender(() => {
        sphere.value.mesh.rotation.x += 0.001;
      });
    })


    return { renderer, sphere }
  }
})
</script>
<template>
  <div class="container">
    <Renderer resize="window" orbit-ctrl ref="renderer">
      <Camera :position="{ z: 10 }" />
      <Scene background="#2E97F2">
        <PointLight :position="{ y: 50, z: 50 }" />
        <Sphere ref="sphere" :rotation="{ y: Math.PI / 6, z: Math.PI / 4 }">
          <BasicMaterial>
            <Texture src="@/assets/texture-soleil.jpg" refraction :refraction-ratio="0.95" />
          </BasicMaterial>
        </Sphere>
      </Scene>
    </Renderer>
  </div>
</template>

<style>

</style>
