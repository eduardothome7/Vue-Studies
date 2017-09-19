<template>
<body>	
  
  <meu-menu :rotas="routes"/>	

  <div class="container">
  	<transition name="page">
    	<router-view></router-view>
    </transition>	
  </div>
</body>
</template>

<script>
import { routes } from './routes';
import Menu from './components/shared/menu/Menu.vue';

export default {
	components: {
		'meu-menu': Menu
	},
	data() {
		return  {
			routes 
		}
	}

}

</script>

<style>
	
  .container {
    padding: 1pc;
    font-family: Helvetica, sans-serif;
    margin: 0 auto; 
    max-width: 96%;
  }

  .page-enter, .page-leave-active {
    opacity: 0;
  }

  .page-enter-active, .page-leave-active {
    transition: opacity 0.4s;
  }
  
</style>
