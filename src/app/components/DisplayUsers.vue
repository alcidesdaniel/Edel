<!--
    Template en que se visualizará el listado de los usuarios
    registrados en la base de datos crud_usuarios
-->
<template>
    <div>
        <h3 class="center-align">Listado de usuarios</h3>
        <table class="striped centered responsive-table">
            <thead>
                <tr>
                  
                    <th>Nombre</th>
                    <th>Apellido</th>
                    <th>Dirección</th>
                    <th>Ciudad</th>
                    <th>Estado</th>
                    <th>País</th>
                    <th>Teléfono</th>
                    <th>Código de área</th>
                    <th>Fecha de nacimiento</th>                    
                    <th>Acciones</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="usuario in usuarios" :key="usuario._id">
                    
                    <td>{{usuario.name}}</td>
                    <td>{{usuario.last_name}}</td>
                    <td>{{usuario.address}}</td>
                    <td>{{usuario.city}}</td>
                    <td>{{usuario.state}}</td>
                    <td>{{usuario.country}}</td>
                    <td>{{usuario.phone}}</td>
                    <td>{{usuario.area_code}}</td>
                    <td >{{fechaNacimiento(usuario.birthdate)}}</td>
                    <div class="row">
                        <router-link :to="{ name: 'EditUser', params:{id: usuario._id} }" class="btn waves-effect waves-light green accent-2 col l12 m12 s12">
                            Editar
                            <i class="small material-icons">edit</i>                            
                        </router-link>                                                
                    </div>
                    <div class="row">
                        <button class="btn waves-effect waves-light red accent-4 col l12 m12 s12" v-on:click="deleteUser(usuario._id)">
                            Eliminar
                            <i class="small material-icons">delete_forever</i>
                        </button>
                    </div>
                         <div class="row">
                        <button class="btn waves-effect waves-light blue accent-4 col l12 m12 s12" v-on:click="imprimirPdf(usuario._id)">
                           Generar PDF
                            <i class="small material-icons"></i>
                        </button>
                         
                    </div>
                    
                </tr>
            </tbody>
        </table>

    </div>
</template>

<script>

/**
 * importa libreria moment.js
 * para parsear y dar formato a las fechas
 */
import moment from 'moment';
import jsPDF from 'jspdf';
import "jspdf-autotable";

    export default {
        data() {
            return {
                usuarios: []
            }
        },
        created(){
            this.fetchUsers();
        },
        
        // métodos del componente DisplayUsers
        methods: {
            fechaNacimiento: function (date) {
                return moment(date, 'YYYY-MM-DD').format('DD/MM/YYYY');
            },
            
            fetchUsers() {
                this.axios.get('/user')
                    .then(res => {
                        this.usuarios = res.data;
                    })
                    .catch(err => console.log(err));                
            },
            deleteUser(id) {                
                const response = confirm('¿Estas seguro de eliminar este Usuario?')
                if(response){              
                    this.axios.delete('/user/' + id)
                    .then(res => {
                        this.fetchUsers();                                     
                    }) 
                    .catch (err => console.log(err));                   
                }
                return;                  
            },
            imprimirPdf(id) {
      this.axios
        .get(`User/${id}`)
        .then(result => {
          var doc = new jsPDF();
          var head = [
            { title: "Nombre", dataKey: "name" },
            { title: "Apellidos", dataKey: "last_name" },
            { title: "Domicilio", dataKey: "city" },
            { title: "Estado", dataKey: "state" },   
            { title: "pais", dataKey: "country" },
            { title: "Telefono", dataKey: "phone" },   
            { title: "Codigo Postal", dataKey: "area_code" },
            { title: "Fecha de Nacimiento", dataKey: "birthdate" }

          ];
          var per = [result.data];
          doc.autoTable(head, per);
          doc.save("reporte.pdf");
        })
        .catch(err => {
          console.log(err.response);
        });
    },

        }     
    }



</script>