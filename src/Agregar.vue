<template>
  <div class="center">
    <p v-if="add.length">
      <b>Se ha añadido a:</b>
      <ul>
        <li v-for="added in add">{{ added }}</li>
      </ul>
    </p>
    <p v-if="errors.length">
      <b>Por favor, corriga los siguientes errores: </b>
      <ul>
        <li v-for="error in errors">{{ error }}</li>
      </ul>
    </p>
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






  </div>
</template><script>


   export default {
     data(){
       return{
         errors:[],
         add: [],
         form : {
                actorId: 1,
               firstName: null,
               lastName: null,
              lastUpdate: 1139988873000,


             }
       }
     },
     methods:{
     agregar: function(form){
        if(this.validar()){
            this.$http.post('http://localhost:3000/actors/', this.form);
            console.log(this.form);
            this.add.push(this.form.firstName);

        }

     },
      validar:function(e) {
           if(this.form.firstName && this.form.lastName) return true;
           this.errors = [];
           if(!this.form.firstName) this.errors.push("Ingrese Nombre.");
           if(!this.form.lastName) this.errors.push("Ingrese Apellido.");
           e.preventDefault();
         }


     },


     }
           </script>

