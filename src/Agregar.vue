<template>
  <div class="center">
   <section class="form">
            <div class="field">
              <label class="label">Name</label>
              <div class="control">
                <input v-model="form.firstName" class="input" type="text" placeholder="Text input">
                <input v-model="form.lastName" class="input" type="text" placeholder="Text input2">
              </div>
            </div>
          </section>
            <button v-on:click="agregar(form)">Add 1</button>

          <div class="column">
                <section class="section" id="results">
                  <div class="box">
                    <ul>
                      <!-- loop through all the `form` properties and show their values -->
                      <li v-for="(item, k) in form">
                        <strong>{{ k }}:</strong> {{ item }}
                      </li>
                    </ul>
                  </div>
                </section>
              </div>




  </div>
</template><script>


   export default {
     data(){
       return{
         form : {
             //   actorId: 1,
               firstName: '',
               lastName: '',
            //    lastUpdate: 1139988873000,


             }
       }
     },
     methods:{
     agregar: function(form){
        this.$http.post('http://localhost:3000/actors/', [form]);fistNa

     }


     },


     }
           </script>

