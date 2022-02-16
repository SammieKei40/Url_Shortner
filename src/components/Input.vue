<template>
<div class="">
  <div class="shadow-lg rounded-lg  bg-[#958f9d] p-10">
                  <input id="inputForm" v-model="inputLink" class="h-14 w-full mb-2 pl-8 focus:outline-none pr-3 text-base shadow-lg placeholder-gray-500  bg-white rounded-lg focus:shadow-outline text-black " type="text" name="name" placeholder="Shorten a link here... i.e https://google.com"/>
                  <span  class="text-red-500 grid italic" id="validate"></span>
                  <span class="text-green-500 grid italic" id="check"></span>
               
                <div class="items-center px-2 ">
                      <button @click.stop.prevent="getLink"  class="w-full rounded-lg py-4 px-6 bg-green-300 font-bold text-white focus:outline-none"> Shorten It!</button>
                </div>
    </div>

    <div  v-if="link.result_url" v-bind:link='link.result_url' class="bg-white p-5 m-6 lg:m-0 mt-20 grid lg:flex justify-around">
        
            <span>{{inputLink}}</span>
            <hr class="m-3"/>
            <a 
           ref="mylink"  
         class="text-green-500 " v-bind:key="link.result_url">{{link.result_url}}</a>
             <hr class="m-3"/>
            <button @click.stop.prevent="copyURL()" class=" rounded-lg  px-6 py-2 bg-green-300 font-bold text-white focus:outline-none">Copy</button>
        
    </div>
</div>
</template>

<script>

export default {
    data(){
        return{
            inputLink : "",
            api_key : "c06f8948a0msh1a868fae930d352p1e9c5cjsn3f10c1fd6372",
            link: [{}]
        }
    },
    methods: {
        getLink(){
            //Input Validation
              var status = false
                var name = document.getElementById('inputForm').value

            if(name === ""){
                 setTimeout(() => {
                     status =false
                    document.getElementById("validate").innerHTML ="Please add a URL!!!"
                }, 1000)
            }else{
                document.getElementById("validate").innerHTML = ""
                status = true; 
            }

            //fETCH LINK
            fetch("https://url-shortener-service.p.rapidapi.com/shorten", {
            "method": "POST",
            "headers": {
                "content-type": "application/json",
                "x-rapidapi-host": "url-shortener-service.p.rapidapi.com",
                "x-rapidapi-key": `${this.api_key}`
            },
            body: 
                JSON.stringify({url: `${this.inputLink}`})
            
        })
        .then(response => {
            return response.json()
        })
        .then(this.setLink)
        .catch(err => {
            alert(err.message)
        });
        },
        setLink(result){
            this.link = result;
            console.log(this.link)   
            console.log(result)
        },

        //Copy link
        copyURL(){
            try{
                navigator.clipboard.writeText(this.link.result_url)
                alert("Link Copied")
            }  catch(e){
                throw e
            }     
        }
    }
}
</script>

<style>

</style>