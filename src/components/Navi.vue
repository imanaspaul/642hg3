<template>
   <header class="">
  <div class="container-flex">
    <div class="nav-wrapper">
      <div class="nav-left">
        <g-link to="/" class="brand"><b>BlogPosts</b></g-link>
        <g-link class="about-link" to="/about">About</g-link>
        <g-link class="about-link" to="/contact">Contact</g-link>
      </div>
      <div class="nav-right">
          <span class="about-link"><ToggleTheme/></span>
         
      </div>
    </div>
  </div>
</header>
</template>
<script>
import ToggleTheme from '~/components/ToggleTheme.vue'
export default {
    name: "navi",
    components : {
        ToggleTheme,
    }
}
</script>
<style lang="css" scoped>
    header{
    padding: 1rem 0;
    display: block;
    background-color: var(--bg-content-color);
    top:0;
    z-index: 10;
    margin-bottom: 50px!important;
   
    }
    .fixed{
     position: fixed;
     width: 100%;
     padding: 0.7rem
    }
    .mt-3{
        margin-top: 20px;
    }
    .container-flex{
    max-width: 860px;
    padding: 0 .5rem;
    margin: auto;
    }
    .nav-wrapper {
    display: flex;
    justify-content: space-between;
    }
    .nav-left a {
    margin-right: 10px;
}
    .brand{
        font-size: 20px;
        font-weight: 600;
        margin-right: 30px!important;
    }
    .nav-right a {
        margin-left: 2rem;
    }
    .about-link {
        color: #3c3c3c;
    }
    .nav-right > a {
        color: var(--title-color);
        text-decoration: none;
    }
    .active--exact{
        color: var(--link-color)!important;
        font-weight: 600;
    }
    .nav-left > a {
        color: var(--link-color);
        text-decoration: none;
    }
    @media (min-width: 600px){
    .container-flex {
        padding: 0 1rem;
    }


    }
</style>