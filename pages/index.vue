<template>
  <div>
    <h1>Welcome!</h1>
    <NLink to="/about">
      About Page
    </NLink>
    <client-only>
      <Background/>
    </client-only>
  </div>
</template>

<script>
import Background from '../components/Background.vue';

export default {
    head: {
        title: "Home page"
    },
    components: {
      Background
    }
}
</script>
