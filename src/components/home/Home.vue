<template>
  <div>
    <h1>{{ titulo }}</h1>
    <input type="search" class="filtro" @input="filtro = $event.target.value" placeholder="filtre pelo título da foto">
    {{ filtro }}
    <ul class="picture_list"> 
      <li v-for="foto of fotosComFiltro">
        <meu-painel :titulo="foto.titulo">
          <imagem-responsiva v-meu-transform:scale.animate.reverse="1.2" :url="foto.url" :titulo="foto.titulo" />
          <meu-botao 
            tipo="button" 
            rotulo="Remover" 
            @botaoAtivado="remove(foto)" 
            :confirmacao="true"
            estilo="perigo"
          />
        </meu-painel>
      </li>
    </ul>
  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue';
import ImagemResponsiva from '../shared/imagem-responsiva/ImagemResponsiva.vue';
import Botao from '../shared/botao/Botao.vue';

export default {
  
  components: {
    'meu-painel': Painel,
    'imagem-responsiva': ImagemResponsiva,
    'meu-botao': Botao
  },
  
  data(){
    return {
      titulo: 'Alura Pic',
      fotos: [],
      filtro: ''
    }
  },
  
  computed: {
    
    fotosComFiltro(){
      if(this.filtro){
        //formata o termo de busca, removendo espaços e ignorando case
        let exp = new RegExp(this.filtro.trim(), 'i');
        return this.fotos.filter(foto => exp.test(foto.titulo));
      } else {
        return this.fotos;
      }
    }
  
  },
  
  methods: {

    remove(foto){
    
      alert('remove a foto' + foto.titulo );  
    }
  },
  
  created() {

    this.$http.get('http://localhost:3000/v1/fotos')
      .then(res   => res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err));

  }

}
</script>

<style>
  
  h1 {
    text-align: center;
  }

  .picture_list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .picture_list li {
    display: inline-block;
    margin-right: 1pc;
    margin-top: 1pc;  
  }

  .picture_list li img {
    max-width: 340px;
    width: 100%;
  }

  .filtro {
    display: block;
    padding: 0.8pc;
    border: none;
    background: #f5f5f5;
    font-size: 16px;
    width: 100%;

  }

</style>
