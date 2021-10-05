<template >
    <div class="pt-5">
       <div class="container">
           <div class="row">
               <div v-if="this.needle.length > 0" class="text-center">
                    <h1 >FILM:</h1>
                    <ul class="d-flex flex-wrap pt-3 mx-2">
                        <li class=" mb-5 d-flex flex-wrap mx-auto" v-for="(element, index) in filterFilm" :key='index'>
                             <img id="banner-image"  class="image-fluid" :src="pathGenerator(element)" :alt="element.title">
                             <div class="content ">
                                 <h5>Titolo</h5> <span> {{element.title}}</span>
                                 <h5>Titolo originale:</h5> <span>{{element.original_title}} </span>
                                  <h5>Lingua: </h5> <span>{{element.original_language}}</span> 
                              
                                <img v-if="element.original_language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="United Kingdom flag" class="flag"> 
                                <img v-if="element.original_language === 'it'"  src="../assets/img/64px-Flag_of_Italy.svg.png" alt="Italy flag" class="flag">
                                <h5>Voto: </h5> {{element.vote_average}} <span><i v-for="(star,counter) in 5 " :key='counter' :class="starHighLighter(element,counter)" class="fas fa-star"></i></span>
                              
                             </div>
                            
                           
                            </li>
                        
                        
                    </ul>
                    <h1 >SERIE TV:</h1>
                    <ul class="d-flex flex-wrap pt-3 mx-2">
                        <li class=" mb-5 d-flex flex-wrap mx-auto" v-for="(element, index) in filterTVs" :key='index'>
                            <img id="banner-image"  class="image-fluid" :src="pathGenerator(element)" :alt="element.name">
                            <div class="content ">
                                 <h5>Titolo</h5> <span> {{element.name}}</span>
                                 <h5>Titolo originale:</h5> <span>{{element.original_name}} </span>
                                  <h5>Lingua: </h5> <span>{{element.original_language}}</span> 
                              
                                <img v-if="element.original_language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="United Kingdom flag" class="flag"> 
                                <img v-if="element.original_language === 'it'"  src="../assets/img/64px-Flag_of_Italy.svg.png" alt="Italy flag" class="flag">
                                <h5>Voto: </h5> <span><i v-for="(star,counter) in 5 " :key='counter' :class="starHighLighter(element,counter)" class="fas fa-star"></i></span>
                              
                             </div>
                           <!--  {{element.name }} - titolo originale: {{element.original_name}} 
                            - lingua: {{element.original_language}}
                            <img v-if="element.original_language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="United Kingdom flag"> 
                            <img v-if="element.original_language === 'it'"  src="../assets/img/64px-Flag_of_Italy.svg.png" alt="Italy flag">
                            
                            - voto :  <i v-for="(star,counter) in stars " :key='counter' :class="starHighLighter(element,counter)" class="fas fa-star">{{star}}</i>
                            - immagine: <img class="banner-image" :src="pathGenerator(element)" :alt="element.name"> -->
                        </li>
                            
                    </ul>
                    
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
            return  `https://image.tmdb.org/t/p/w342${element.poster_path}`;
        },
        starHighLighter: function(element,counter){         
            let k = Math.ceil(element.vote_average / 2);   
            console.log(k)  
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
    
    li {
        position: relative;
       
        .flag {
        width: 30px;
        }
         #banner-image{
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