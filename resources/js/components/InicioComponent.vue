<template>
  <v-app id="keep">
    <v-app-bar app clipped-left color="green lighten-3">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <span class="title ml-3 mr-5">Criptología</span>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app clipped color="grey lighten-3" >
      <v-list dense class="grey lighten-4" >
        <template v-for="(item, i) in items">
          <v-list-item :key="i" link @click="Desplegar(i)" >
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="grey--text">
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>
    <v-content>
      <v-container fluid class="white" v-if="this.tipo==0">
        <div >
          <div>
            <h2><p class="font-weight-black text-center">Bienvenidos</p></h2><br>
            <p class="font-weight-black text-center">Presentado por:</p>
            <p class="font-weight-black text-center">Leidy Lorena Pulido Morales - 123456789</p>
            
          </div>
          <v-row justify="center" align="center" >
            <v-img src="images/cripto_inicio.gif" max-width="40pc" contain></v-img>
          </v-row>
        </div>

      </v-container>
      <div v-if="this.tipo==1">
        <calcularMod-component></calcularMod-component>
      </div>
     </v-content>
  </v-app>
</template>
<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
      items: [
        { icon: 'search', text: 'Calcular Mod' },
      ],
      tipo: 0,
    }),
    methods: {
        Desplegar(x){
            if(x==0){
              this.tipo=1;
            }
        },

    },
  }
</script>

<style>
/* #keep .v-navigation-drawer__border {
  display: none
} */
</style>
