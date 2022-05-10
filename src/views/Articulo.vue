<template>
  <Titulo texto="Post"/>
  <b>Post {{$route.params.id}}</b>
  <br>
  <b>{{articulo.title}}</b>
  <p>{{articulo.body}}
  </p>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
    name: 'ArticuloView',
    components: {
        Titulo
    },
    data(){
        return{
            articulo:{}
        }
    },
    methods : { 
        async consumirArticulo(){
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const objeto = await data.json()
                this.articulo = objeto
            } catch (error) {
                console.log(error)
                
            }
        }
    },
    created(){
        this.consumirArticulo()
    }

}
</script>

<style>

</style>