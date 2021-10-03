<template>
  <div>
       <div class="input-group mb-3" >
            <input @keyup="$emit('search', needle)"   v-model.trim='needle' type="text" class="form-control" placeholder="Che film stai cercando?" >
            <div class="input-group-prepend">
                <button class="btn btn-danger" @click="resetNeedle()" type="reset">Reset</button>
            </div>
        </div>
  </div>
</template>

<script>
export default {
  name: 'Header',

     data: function(){
        return{
            needle :'',   
        }
    },
    computed:{
       
    },
    methods:{
         resetNeedle: function(){
            this.needle = '';
        },
    
    }
    
}
</script>


<style>

</style>