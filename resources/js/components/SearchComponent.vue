<template>
    <div class="search-app">
        <div class="row">
            <div class="input-group">
            <input @keyup="searchdata" type="text" v-model="search" class="form-control" placeholder="Search user here" name="">
        </div>
        </div>
         <div v-if="search != ''">
           <class class="row">
               <div class="card md-4">
                   <div class="card-body">
                    <div class="card" style="width: 18rem;">
                          <img src="https://via.placeholder.com/150" class="card-img-top" alt="...">
                          <div class="card-body">
                            <h5 class="card-title"> {{  searchresult.name }}</h5>
                            <p class="card-text"> {{  searchresult.email }}</p>
                            <a href="#" class="btn btn-primary">{{ searchresult.created_at }}</a>
                          </div>
                        </div>
                   </div>
               </div>
           </class>
       </div>
       <div v-else>
           No found
       </div>
     </div>
    </div>
</template>
<script>
    import axios from 'axios'
    export default {
       
        data(){
            return {
                search:'',
                searchresult:{},
                result: [],
                searchtrue:false
            };
        },
        mounted() {
            //console.log(this.user)
        },
        methods:{
            searchdata() {
               axios.get('search?query='+this.search)
                    .then(({data}) => {
                        // TODO: store data
                        this.searchresult= data[0];
                        this.searchtrue=true;
                    })
                    .catch(({response}) => {
                        alert(response);
                    });
            }
        },
    }
</script>
