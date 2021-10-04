<template>
  <header >
    <div class="container">
        <div class="row justify-content-between align-items-center pt-1">
            <div class="col-7 d-flex align-items-center ">

                <ul class="d-flex align-items-center lh-lg">
                    <li><img class="b-logo" src="https://fontmeme.com/permalink/211004/c072857f28ffed69c9266a55183f4c20.png" alt="Boolflix logo"></li>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Serie Tv</a></li>
                    <li><a href="#">Film</a></li>
                    <li><a href="#">Originale</a></li>
                    <li><a href="#">Aggiunti di recente</a></li>
                    <li><a href="#">La mia lista</a></li>
                    </ul>
            </div>
            <div class="col-4 d-flex ">
                <div class="input-group input-group-sm mb-3 d-flex align-items-center">
                    <input id="input-search" @keyup="$emit('search', needle)"   v-model.trim='needle' type="text" class="form-control" placeholder="Che film stai cercando?" >   
                    <button class="rounded-1 btn btn-danger mx-2" @click="resetNeedle()" type="reset">Reset</button>
                    <span class="mx-2">BAMBINI</span>
                    <i class="far fs-3 fa-user mx-2"></i>
                    <i class="fas fs-4 fa-angle-down"></i>
                </div>
            </div>
            
               
        </div>
    </div>
    
       
  </header>
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


<style scoped lang='scss'>
header{
    .fas,
    .far,
    span{
        color: white;
    }
    ul{
        
        list-style: none;
        li{
            padding: 0 10px;
            display: flex;
            align-items: center;
            a{
                text-decoration: none;
                color: lightgray;
                font-weight: bold;
            }
            
        }
    }
    .b-logo{
        width : 120px
    }
    
}
    
</style>