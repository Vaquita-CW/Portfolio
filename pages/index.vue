<template>
  <div>
    <h1>Welcome!</h1>
    <NLink to="/about">
      About Page
    </NLink>
  </div>
  <Renderer ref="renderer">
    <Camera :position="{ z: 10 }" />
    <Scene>
      <PointLight :position="{ y: 50, z: 50 }" />
      <Box ref="box" :rotation="{ y: Math.PI / 4, z: Math.PI / 4 }">
        <LambertMaterial />
      </Box>
    </Scene>
  </Renderer>
</template>

<script>
import { Box, Camera, LambertMaterial, PointLight, Renderer, Scene } from 'troisjs';
export default {
  head: {
    title: 'Home page'
  },
    components: { Box, Camera, LambertMaterial, PointLight, Renderer, Scene },
}
</script>
