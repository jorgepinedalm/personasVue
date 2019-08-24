<template>
  <div>
    <md-dialog :md-active.sync="showDialog">
        <md-dialog-title>Agregar persona</md-dialog-title>
      <form novalidate class="md-layout md-size-100" @submit.prevent="validateUser">
      <md-dialog-content>
        

                <md-field>
                    <label>Cédula</label>
                    <md-input v-model="number" type="number"></md-input>
                </md-field>
                <md-field>
                    <label>Nombre</label>
                    <md-input v-model="number"></md-input>
                </md-field>
                <md-field>
                    <label>Apellido</label>
                    <md-input v-model="number"></md-input>
                </md-field>
                <md-field>
                    <label for="sexo">Sexo</label>
                    <md-select v-model="movie" name="sexo" id="sexo">
                        <md-option value="fight-club" v-for="sexo in sexos" :value="sexo.id" :key="sexo.id">{{sexo.valor}}</md-option>
                    </md-select>
                </md-field>

        <md-progress-bar md-mode="indeterminate" v-if="sending" />
        <md-snackbar :md-active.sync="userSaved"></md-snackbar>

        <md-dialog-actions>
          
          <md-button type="button" class="md-primary" :disabled="sending" @click="showDialog=false">Cancelar</md-button>
          <md-button type="submit" class="md-primary" :disabled="sending">Guardar</md-button>
        </md-dialog-actions>
      </md-dialog-content>
    </form>
    

      
    </md-dialog>
  </div>
</template>

<script>
  export default {
    name: 'DialogCustom',
    data: () => ({
      showDialog: false,
      sexos:[
        {
          id: 1,
          valor: "Masculino",
        },
        {
          id: 2,
          valor: "Femenino",
        }
      ],
    }), mounted(){
        EventBus.$on("activar_ventana_agregar", data => {
           this.showDialog = true;
        })
    }
  }
</script>

<style lang="scss" scoped>
    .md-card{
        width: 100%;
    }

  .md-dialog {
    max-width: 768px;
  }
</style>