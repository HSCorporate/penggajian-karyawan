<template>
<Navbar/>
  <Home/>
  <Footer/>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Home from './components/Home.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Home, Navbar, Footer
  }
}
</script>