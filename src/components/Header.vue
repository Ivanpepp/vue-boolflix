<template>
  <header >
      <nav class="navbar navbar-expand-xl navbar-light" >
        <div class="container-fluid">
            <a class="navbar-brand" href="#"><img class="b-logo" src="https://fontmeme.com/permalink/211004/c072857f28ffed69c9266a55183f4c20.png" alt="Boolflix logo"></a>
            <button class="navbar-toggler"  type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon " ></span>
            </button>
            <div class="collapse navbar-collapse " id="navbarSupportedContent">
            <ul class="navbar-nav me-auto mb-2 mb-md-0">
                <li class="nav-item"><a href="#">Home</a></li>
                <li><a href="#">Serie Tv</a></li>
                <li><a href="#">Film</a></li>
                <li><a href="#">Originale</a></li>
                <li><a href="#">Aggiunti di recente</a></li>
                <li><a href="#">La mia lista</a></li>
            </ul>
                <form class="d-flex">
                        <input id="input-search" @keyup="$emit('search', needle)"   v-model.trim='needle' type="text" class="form-control" placeholder="Che film stai cercando?" >   
                        <button class="rounded-1 btn btn-danger mx-2" @click="resetNeedle()" type="reset">Reset</button>
                        <span class="mx-2">BAMBINI</span>
                        <i class="far fs-3 fa-user mx-2"></i>
                        <i class="fas fs-4 fa-angle-down"></i>
                </form>
            </div>
        </div>
</nav>
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
            this.needle === "";
        },
    
    }
    
}
</script>


<style scoped lang='scss'>
header{
  .navbar-light .navbar-toggler{
      
      border-color: rgb(183, 183, 183);
  }
    .fas,
    .far,
    span{
        color: white;
        cursor: pointer;
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
                &:hover{
                    color: white;
                }
            }
            
        }
    }
    .b-logo{
        width : 120px
    }
    
}
    
</style>