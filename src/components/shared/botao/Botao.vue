<template>
  <div>
  	<button @click="disparaAcao()" class="botao" :class="estiloDoBotao" :type="tipo">{{ rotulo }}</button>
  </div>	
</template>

<script>
export default {

	props: {
		tipo:{
			required: true,
			type: String
		},

		rotulo: {
			required: true,
			type: String
		},

		confirmacao: Boolean,
		estilo: String

	},
	methods: {
		disparaAcao(){
			if(this.confirmacao) {
				if(confirm('Confirma exclusão?')){
					this.$emit('botaoAtivado');
					
				} else {
					return;
				}				
			}
			this.$emit('botaoAtivado');
		}
	},
	computed: {
		estiloDoBotao(){
			if(this.estilo == "padrao" || !this.estilo) return 'botao-padrao';
			if(this.estilo == "perigo") return 'botao-perigo';
		}
	}

}
</script>

<style scoped>

	.botao {
		display: inline-block;
		padding: 12px;
		border-radius: 0;
		font-size: 1.2em;
		border: none;
		margin-top: 0.5pc;
		cursor: pointer;
	}

	.botao-perigo {
		background: firebrick;
		color: white;
	}

	.botao-padrao {
		background: darkcyan;
		color: white;
	}
  
</style>
