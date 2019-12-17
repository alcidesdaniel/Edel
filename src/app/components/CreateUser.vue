<!-- 
    Template para visualizar el formulario
    de creación de usuario
-->
<template>
    <div class="row">
        <div class="col s12 m12 l12">
            <div class="card">
                <!-- 
                    formulario que captura los datos ingresados 
                     y son eviados al método addUser 
                -->
                <form v-on:submit.prevent="addUser">
                <div class="card-content">
                    <h4 class="center-align">Creación de Usuario</h4>                
                
                    <div class="row">
                        <div class="input-field col s12 m6 l6">
                        <i class="material-icons prefix">account_circle</i>
                      <!--  <input id="icon_prefix" type="text" v-model="user.name" class="validate" pattern="[a-z] {1,20}" title="Agrega Nombre" required> 
                       --> <input id="icon_prefix" type="text" v-model="user.name" pattern="[a-zA-ZàáâäãåąčćęèéêëėįìíîïłńòóôöõøùúûüųūÿýżźñçčšžÀÁÂÄÃÅĄĆČĖĘÈÉÊËÌÍÎÏĮŁŃÒÓÔÖÕØÙÚÛÜŲŪŸÝŻŹÑßÇŒÆČŠŽ∂ð ,.'-]{2,48}" required/>

                        <label for="icon_prefix">Nombre</label>
                        </div>                        

                        <div class="input-field col s12 m6 l6">
                        <i class="material-icons prefix">account_circle</i>
                     <!--   <input id="icon_prefix" type="text" v-model="user.last_name" class="validate" pattern="[A-Z a-z] {1,20}" title="Agrega Apellidos" required >
                       --><input id="icon_prefix" type="text" v-model="user.last_name" pattern="[a-zA-ZàáâäãåąčćęèéêëėįìíîïłńòóôöõøùúûüųūÿýżźñçčšžÀÁÂÄÃÅĄĆČĖĘÈÉÊËÌÍÎÏĮŁŃÒÓÔÖÕØÙÚÛÜŲŪŸÝŻŹÑßÇŒÆČŠŽ∂ð ,.'-]{2,48}" required/>

                       
                        <label for="icon_prefix">Apellido</label>
                        </div>                        
                    </div>    
                    <div class="row">
                        <div class="input-field col s12 m6 l6">
                        <i class="material-icons prefix">directions</i>
                        <!--
                        <input id="icon_prefix" type="text" v-model="user.address" class="validate" pattern="[A-Z a-z] {1,20}" title="Agrega Direccion" required>
                        --><input id="icon_prefix" type="text" v-model="user.address" pattern="[a-zA-ZàáâäãåąčćęèéêëėįìíîïłńòóôöõøùúûüųūÿýżźñçčšžÀÁÂÄÃÅĄĆČĖĘÈÉÊËÌÍÎÏĮŁŃÒÓÔÖÕØÙÚÛÜŲŪŸÝŻŹÑßÇŒÆČŠŽ∂ð ,.'-]{2,48}" required/>

                        
                        <label for="icon_prefix">Dirección</label>
                        </div>                        

                        <div class="input-field col s12 m6 l6">
                        <i class="material-icons prefix">location_city</i>
                       <!-- <input id="icon_prefix" type="text" v-model="user.city" class="validate" pattern="[A-Z a-z] {1,20}" title="Agrega Ciudad" required>
                       --> <input id="icon_prefix" type="text" v-model="user.city" pattern="[a-zA-ZàáâäãåąčćęèéêëėįìíîïłńòóôöõøùúûüųūÿýżźñçčšžÀÁÂÄÃÅĄĆČĖĘÈÉÊËÌÍÎÏĮŁŃÒÓÔÖÕØÙÚÛÜŲŪŸÝŻŹÑßÇŒÆČŠŽ∂ð ,.'-]{2,48}" required/>

                        <label for="icon_prefix">Ciudad</label>
                        </div>                        
                    </div>
                    <div class="row">
                        <div class="input-field col s12 m6 l6">
                        <i class="material-icons prefix">place</i>
                     <!--   <input id="icon_prefix" type="text" v-model="user.state" class="validate" pattern="[A-Z a-z] {1,20}" title="Agrega Estado" required>
                      ---> <input id="icon_prefix" type="text" v-model="user.state" pattern="[a-zA-ZàáâäãåąčćęèéêëėįìíîïłńòóôöõøùúûüųūÿýżźñçčšžÀÁÂÄÃÅĄĆČĖĘÈÉÊËÌÍÎÏĮŁŃÒÓÔÖÕØÙÚÛÜŲŪŸÝŻŹÑßÇŒÆČŠŽ∂ð ,.'-]{2,48}" required/>

                       
                        <label for="icon_prefix">Estado</label>
                        </div>                        

                        <div class="input-field col s12 m6 l6">
                        <i class="material-icons prefix">public</i>
                        <!--<input id="icon_prefix" type="text" v-model="user.country" class="validate" pattern="[A-Za-z] {1,20}" title="Agrega Pais" required>
                        -->
                        <input id="icon_prefix" type="text" v-model="user.country" pattern="[a-zA-ZàáâäãåąčćęèéêëėįìíîïłńòóôöõøùúûüųūÿýżźñçčšžÀÁÂÄÃÅĄĆČĖĘÈÉÊËÌÍÎÏĮŁŃÒÓÔÖÕØÙÚÛÜŲŪŸÝŻŹÑßÇŒÆČŠŽ∂ð ,.'-]{2,48}" required/>

                        
                        <label for="icon_prefix">País</label>
                        </div>                        
                    </div>                                                                                                            
                    <div class="row">   
                        <div class="input-field col s12 m6 l4">
                        <i class="material-icons prefix">phone</i>
                        <!--<input id="icon_telephone" type="tel" v-model="user.phone" class="validate" pattern="[0-9] {10}" title="Agrega Numero de Telefono" required>
                        --><input id="icon_telephone" type="tel" v-model="user.phone" pattern="[0-9]{10}" requiered>

                        <label for="icon_telephone">Teléfono</label>
                        </div>
                        <div class="input-field col s12 m6 l4">
                        <i class="material-icons prefix">map</i>                        
                       <!-- <input id="icon_telephone" type="text" v-model="user.area_code" class="validate" pattern="[0=9] {6}" title="Agrega el codigo Postal" required>
                        --><input id="icon_telephone" type="text" v-model="user.area_code" pattern="[0-9]{5}">

                        <label for="icon_area_code">Código de área</label>
                        </div>
                        <div class="input-field col s12 m6 l4"> 
                        <i class="material-icons">cake</i>
                        <date-picker v-model="user.birthdate" format="dd/MM/yyyy" editable lang="es" placeholder="Fecha de nacimiento" class="validate" required></date-picker>                                             
                        </div>
                                                                                
                    </div>
                </div>
                <div class="card-action">
                    <div class="row">
                        <div class="col s12">
                        <button class="btn waves-effect waves-light  deep-purple darken-4" type="submit">Agregar Usuario
                            <i class="material-icons right">send</i>
                            </button>
                        </div>
                    </div>
                </div>
                </form>                              
            </div>
        </div>
    </div>    
</template>

<script>

/**
 * Importa componente Datapicker 
 * para el campo fecha de nacimiento
 */
import DatePicker from 'vue2-datepicker'

    export default {

        components: { DatePicker },

        data() {
            return {
                user: {},   
                shortcuts: [                    
                    {
                        start: new Date(),
                        end: new Date()
                    }
                ]                
            }
        },

        // Métodos del componente CreateUser
        methods: {
            /**
             * Método que envia los datos obtenidos en el formulario
             * después de recibir respuesta redirecciona
             * al componente DisplayUsers
             */ 
            addUser() {
                
                this.axios.post('/user', this.user)
                    .then(res => {
                        this.$router.replace({name: 'DisplayUsers'});
                    })
                    .catch(err => console.log(err));                
            }
        }    
    }

    
    
</script>