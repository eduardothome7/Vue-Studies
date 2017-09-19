<template>
  <nav>
    <ul>
      <li v-for="rota in rotas">
        <router-link :to="rota.path ? rota.path : '/'">{{ rota.titulo }}</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  
  props: {
    rotas: {
      type: Array,
      required: true
        
    }
  }

}
</script>

<style scoped>

  nav {
    width: 100%;
    border-bottom: 1px solid #f2f2f2;
    background: #f5f5f5;
    height: 54px;
  } 

  nav ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  nav ul li {
    display: inline-block;
    float: left;
    margin-left: 1pc;     
    padding: 8px;   
  }

  nav li a {
    margin-top: 4pc;
  }

  nav li a:hover {
    background: #c3c3c3;
  }

  ul.ul-right {
    /*float: right !important;*/
  }
</style>
