<template>
<body>	
  <nav>
	<ul>
	  <li v-for="route in routes">
	   	<router-link :to="route.path ? route.path : '/'">{{ route.titulo }}</router-link>
	  </li>
	</ul>
  </nav>
  <div class="container">
  	<transition name="page">
    	<router-view></router-view>
    </transition>	
  </div>
</body>
</template>

<script>
import { routes } from './routes';

export default {
	data() {
		return  {
			routes 
		}
	}

}

</script>

<style>
	
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
