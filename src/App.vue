<template>
  <div id="app">
    <Navbar></Navbar>
    <MiddleSection></MiddleSection>
    <Footer></Footer>
  </div>
</template>

<script>
import Navbar from './Navbar.vue';
import MiddleSection from './MiddleSection.vue';
import Footer from './Footer.vue';

export default {
  name: 'app',
  components:{
    Navbar: Navbar,
    MiddleSection: MiddleSection,
    Footer: Footer,
  },

  data () {
    return {
      
    }
  }
}
</script>