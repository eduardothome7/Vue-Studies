<template>
  <div class="painel">
    <h2 class="painel-titulo" @dblclick="visivel = !visivel">{{ titulo }}</h2>
    <transition name="painel-fade">
      <div class="painel-conteudo" v-show="visivel"> 
        <slot></slot>
      </div>
    </transition>
  </div>   
</template>

<script>
export default {
  props: ['titulo'],
  data(){
    return {
      visivel: true
    }     
  }  
}
</script>

<style scoped>
  
  * {
    box-shadow: 1px 1px 14px 0px;
  }

  .painel-titulo {
    text-align: center;
  }

  .painel-fade-enter, .painel-fade-leave-active {
    opacity: 0;
  }

  .painel-fade-enter-active, .painel-fade-leave-active {
    transition: opacity 0.4s;
  }

</style>
