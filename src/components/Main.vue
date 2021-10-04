<template >
    <div class="pt-5">
       <div class="container">
           <div class="row">
               <div v-if="this.needle.length > 0" class="text-center">
                    <h1 >FILM:</h1>
                    <ul>
                        <li  v-for="(element, index) in filterFilm" :key='index'>
                            {{element.title}} - titolo originale: {{element.original_title}} 
                            - lingua: {{element.original_language}}
                            <img v-if="element.original_language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="United Kingdom flag"> 
                            <img v-if="element.original_language === 'it'"  src="../assets/img/64px-Flag_of_Italy.svg.png" alt="Italy flag">
                            
                            - voto :  <i v-for="(star,counter) in stars " :key='counter' :class="starHighLighter(element,counter)" class="fas fa-star">{{star}}</i>
                            - immagine: <img :src="pathGenerator(element)" :alt="element.title">
                            </li>
                        
                        
                    </ul>
                    <h1 >SERIE TV:</h1>
                    <ul>
                        <li  v-for="(element, index) in filterTVs" :key='index'>
                            {{element.name }} - titolo originale: {{element.original_name}} 
                            - lingua: {{element.original_language}}
                            <img v-if="element.original_language === 'en'" src="../assets/img/Flag_of_the_United_Kingdom_(3-5).svg.png" alt="United Kingdom flag"> 
                            <img v-if="element.original_language === 'it'"  src="../assets/img/64px-Flag_of_Italy.svg.png" alt="Italy flag">
                            
                            - voto :  <i v-for="(star,counter) in stars " :key='counter' :class="starHighLighter(element,counter)" class="fas fa-star">{{star}}</i>
                            - immagine: <img :src="pathGenerator(element)" :alt="element.name">
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
            stars:['','','','',''],
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
            let k = parseInt(element.vote_average / 2 -1 );     
            if (counter <= k){
                return 'active';
            }else{
                return 'inActive'
            }

        },
      

       
    }
 
}


</script>

<style lang='scss' scoped>
    li > img{
        width: 30px;
    }
    .active{
        color: yellow;
    };
    .inActive{
        color: lightgray;
    }
</style>