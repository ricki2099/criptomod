<template>
  <v-card class="mx-auto" max-width="1044" tile>
    <v-container>
        <center>
            <p class="title ml-3 mr-5">
                Aritmetica Modular
            </p>
        </center>
       
        <v-form  ref="form" v-model="valid">
        <v-container>
            <p class="title ml-3 mr-5">
                Ingrese las variables
            </p>
        <v-layout>
         <v-flex xs12 md4>
            <v-text-field
                v-model.number="variableA"
                :rules="validRules"
                label="A"
                required
                class="ma-10"
                type="number"
            ></v-text-field>
            </v-flex>
            <v-flex xs12 md4>
            <v-text-field
                v-model.number="variableB"
                :rules="validRules"
                label="B"
                required
                class="ma-10"
                type="number"
            ></v-text-field>
            </v-flex>

            <v-flex xs12 md4>
            <v-text-field
                v-model.number="variableC"
                :rules="validRules"
                label="Mod"
                required
                class="ma-10"
                type="number"
            ></v-text-field>
            </v-flex>
        </v-layout>
        <v-btn color="success" class="mr-4" @click="validate" >
            Calcular
        </v-btn>
        </v-container>
      </v-form>
    </v-container>
    <v-container v-if="resultadoTotal!=0">
        <p class="title ml-3 mr-5">
                Los resultados son:
        </p>
        <span class="title ml-10 mr-5" ><b>Suma: </b> {{resultadoSuma}}</span>
        <span class="title ml-10 mr-5" ><b>Resta: </b> {{resultadoResta}}</span>
        <span class="title ml-10 mr-5" ><b>Multiplicación: </b> {{resultadoMulti}}</span>
        <span class="title ml-10 mr-5" ><b>División: </b> {{resultadoDivision}}</span>
        
   </v-container>
  </v-card>
</template>

<script>
  export default {

    data: () => ({
      valid: false,
      variableA: null,
      variableB: null,
      variableC: null,
      resultadoSuma : 0, 
      resultadoResta: 0,
      resultadoMulti: 0,
      resultadoDivision: 0,
      resultadoTotal: 0,

      validRules: [
        v => !!v || 'La variable es requerida',
        // v => v.length <= 10 || 'Name must be less than 10 characters'
      ],
    
    }),
    methods: {
        validate () {
            if(this.$refs.form.validate()){
               console.log('');
               this.calcular();
            }
        },
        calcular(){
            // Calcular
            // Asignación de variables
            let variable1 = this.variableA;
            let variable2 = this.variableB;
            let mod       = this.variableC;
            let suma,resta,multiplicacion,division = 0;
            

            // Proceso de suma
            suma = (variable1) + (variable2);
            this.resultadoSuma = suma % mod;

            // Proceso de resta
            resta = (variable1) - (variable2);
            this.resultadoResta = (resta % mod);
            
            if (this.resultadoResta < 0) {
                this.resultadoResta =  mod + this.resultadoResta;
            }else{
                this.resultadoResta = (resta % mod);
            }

            // Proceso de multiplicacion
            multiplicacion = (variable1) * (variable2);
            this.resultadoMulti = multiplicacion % mod;

            // Proceso de division
            division = (variable1) / (variable2);
            this.resultadoDivision = division % mod;

            // Mostrar resultados            
            this.resultadoTotal=1;
        }
     


    

    },
  }
</script>

<style>
/* #keep .v-navigation-drawer__border {
  display: none
} */
</style>
