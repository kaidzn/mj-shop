<template>
  <div class="home">
    <HeaderSection/>
    <MenuSection/>
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderSection from '@/components/HeaderSection.vue';
import MenuSection from '@/components/MenuSection.vue';

export default {
  name: 'HomeView',
  components: {
    HeaderSection,
    MenuSection
  }
}
</script>
