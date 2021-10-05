<template >
    <div v-if="needle.length > 0" class="pt-5">
       <div class="container">
           <div class="row  justify-content-center">
                <h1 class="col-12" >FILM:</h1>
                <div class="col-3 card-wrapper p-0 mb-4" v-for="(element, index) in filterFilm" :key='index'>
                    <img id="banner-image"  class="image-fluid" :src="pathGenerator(element)" :alt="element.title">
                    <div class="content ">
                        <h5>Titolo</h5> <span> {{element.title}}</span>
                        <h5>Titolo originale:</h5> <span>{{element.original_title}} </span>
                        <h5>Lingua: </h5> <span>{{element.original_language}}</span> 
                        <img v-if="element.original_language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="United Kingdom flag" class="flag"> 
                        <img v-if="element.original_language === 'it'"  src="../assets/img/64px-Flag_of_Italy.svg.png" alt="Italy flag" class="flag">
                        <h5>Voto: </h5>  <span><i v-for="(star,counter) in 5 " :key='counter' :class="starHighLighter(element,counter)" class="fas fa-star"></i></span>  
                    </div>
                </div>
           </div>
           <div class="row justify-content-center">
                <h1 class="col-12" >SERIE TV:</h1>
                <div class="col-3 card-wrapper p-0 mb-4" v-for="(element, index) in filterTVs" :key='index'>
                         <img id="banner-image"  class="image-fluid" :src="pathGenerator(element)" :alt="element.name">
                        <div class="content ">
                            <h5>Titolo</h5> <span> {{element.name}}</span>
                            <h5>Titolo originale:</h5> <span>{{element.original_name}} </span>
                            <h5>Lingua: </h5> <span>{{element.original_language}}</span> 
                            <img v-if="element.original_language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="United Kingdom flag" class="flag"> 
                            <img v-if="element.original_language === 'it'"  src="../assets/img/64px-Flag_of_Italy.svg.png" alt="Italy flag" class="flag">
                            <h5>Voto: </h5> <span><i v-for="(star,counter) in 5 " :key='counter' :class="starHighLighter(element,counter)" class="fas fa-star"></i></span>                             
                        </div>
                </div>
           </div>
            
                    


       </div>
                
    </div>
</template>

<script>


export default {
    name: 'Main',
   
    props:{
        filmGroup: Array,
        TVSeriesGroup:Array,
        needle: String
    },
    data: function(){
        return{
            imgNoPath : 'https://via.placeholder.com/330x495'
        }
    },
    computed:{
        filterFilm: function(){
            return this.filmGroup.filter((element)=>{  

               return element.title.toLowerCase().trim().match(this.needle.toLowerCase())
               
        })
        },
        filterTVs: function(){
            return this.TVSeriesGroup.filter((element)=>{
                return element.name.toLowerCase().trim().match(this.needle.toLowerCase())
            })
        },
       
       
    },
    methods:{
        
        pathGenerator: function(element){
                if (element.poster_path === null){
                    return this.imgNoPath;
                }
                return  `https://image.tmdb.org/t/p/w342${element.poster_path}`;
            
           
        },
        starHighLighter: function(element,counter){         
            let k = Math.ceil(element.vote_average / 2);   
           
            if (counter < k){
                return 'active';
            }else{
                return 'inActive'
            }

        },
      

       
    }
 
}


</script>

<style lang='scss' scoped>
    
    .card-wrapper {
        position: relative;
        
        .flag {
        width: 30px;
        }
         #banner-image{
             width: 100%;
             height: 100%;
             object-fit: cover;
             object-position: center;
            transition: .2s cubic-bezier(0.165, 0.84, 0.44, 1);
        }
        &:hover #banner-image{
            opacity: .1;
        }
        &:hover .content{
            display: block;
            opacity: 1;
        }
         .content{
             padding-top: 30px;
             width: 80%;
             height: 80%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            opacity: 0;
            transition: .2s cubic-bezier(0.165, 0.84, 0.44, 1);
            
        }
        
    } 
    
    .active{
        color: yellow;
    };
    .inActive{
        color: lightgray;
    }
  
</style>