<script>
import HeaderSearch from './HeaderSearch.vue'

export default {
    components:{
        HeaderSearch,
    },
  data() {
    return {
      
    }
  }
}
</script>

<template>
    <header>
        <HeaderSearch />
    </header>

    
</template>

<style lang="scss" scoped>

    header {
        background-color: #0c0c0c;
        padding: 2rem;
    }

</style>