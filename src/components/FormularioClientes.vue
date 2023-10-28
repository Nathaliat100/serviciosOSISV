<template>
   <div class="formularioregis">
    <h1>Registro Cliente</h1>
    <form id="regis" @submit.prevent="Guardar">
        <div class="grupores">
            <label for="Nombre">Nombre</label>
            <input type="text" id="nombre" name="nombre" required v-model="nombre">
        </div>
        <div class="grupores">
                <label for="Tipo_documento">Tipo de Documento</label>
                <select id="docre">
                    <option value="seleccione">Seleccione</option>
                    <option value="Cedula">Cedula</option>
                    <option value="Tarjeta de identidad">Tarjeta de identidad</option>
                    <option value="Cedula de extranjeria">Cedula de extranjeria</option>
                    <option value="Otro">Otro</option>
                </select>
        </div> 
        <div class="grupores">
            <label for="Numero_de_documento">Numero de documento</label>
            <input type="number" id="numerodocre" name="numerodocre" required v-model="numerodocre">
        </div>
        <div class="grupores">
            <label for="genero">Genero</label>
            <input type="text" id="genero" name="genero" required v-model="genero">
        </div>
        <div class="grupores">
            <label for="Telefono">Telefono</label>
            <input type="number" name="numerotelefono" id="numerotelefono" required v-model="numerotelefono">
        </div>
        <div class="grupores">
            <label for="Direccion">Direccion </label>
            <input type="text" name="direccion" id="direccion" required v-model="direccion">
        </div>
        <div class="grupores">
            <label for="Correo">Correo </label>
            <input type="email" name="correo" id="correo" required v-model="correo">
        </div>
        <div class="grupores">
            <label for="Estado_civil">Estado civil</label>
            <input type="text" name="estadocivil" id="estadocivil" required v-model="estadocivil">
        </div>
        <div class="grupores">
            <label for="Fecha_de_nacimiento">Fecha de nacimiento</label>
            <input type="date" name="nacimiento" id="nacimiento" required v-model="nacimiento">
        </div>
        <div class="grupores">
            <label for="EPS">EPS</label>
            <input type="text" name="EPS" id="EPS" required v-model="EPS">
        </div>
        <div class="grupores">
            <label for="Contraseña">Contraseña</label>
            <input type="password" name="contraseña" id="contraseña" required v-model="contraseña">
        </div>
        <button type="submit" id="Guardar" name="Guardar">Guardar</button> <br>
        <button type="button" id="Eliminar" name="Eliminar" @click="Eliminar">Eliminar</button> <br>
        <button type="button" id="Actualizar" name="Actualizar" @click="Actulizar">Actualizar</button> <br>
        <button type="button" id="Consultar" name="Consultar" @click="Consultar">Consultar</button> <br>
        
    </form>
   </div>
</template>
<script>
import axios from "axios";

export default{
    data(){
        return {
            Nombre:"",
            Tipo_documento:"",
            Numero_de_documento:"",
            Genero:"",
            Telefono:"",
            Direccion:"",
            Correo:"",
            Estado_civil:"",
            Fecha_de_nacimiento:"",
            EPS:"",
            Contraseña:"",
        };
    },
    methods:{
        Guardar(){
            axios
            .post("http://localhost:8080/api/clientes",{
                Nombre: this.Nombre,
                Tipo_documento:this.Tipo_documento,
                Numero_de_documento:this.Numero_de_documento,
                Genero:this.Genero,
                Telefono:this.Telefono,
                Direccion:this.Direccion,
                Correo:this.Correo,
                Estado_civil:this.Estado_civil,
                Fecha_de_nacimiento:this.Fecha_de_nacimiento,
                EPS:this.EPS,
                Contraseña:this.Contraseña,  
            })
            .then((Response) => {
                console.log("registro exitoso",Response.data);
                alert("exito");
            this.Nombre = '';
            this.Tipo_documento='';
            this.Numero_de_documento='';
            this.Genero='';
            this.Telefono='';
            this.Direccion='';
            this.Correo='';
            this.Estado_civil='';
            this.Fecha_de_nacimiento='';
            this.EPS='';
            this.Contraseña='';
            })
            .catch((error)=> {
                console.error("Error al registrar:",error);   
            });
        },
        Consultar(){
            axios
                .get("http://localhost:8080/api/clientes/" +this.documento)
                .then((response) => {
                  //actualizar los campos del formulario con los datos del estudiante consultado
                    this.Nombre = response.data.Nombre;
                    this.Tipo_documento =response.data.Tipo_documento;
                    this.Numero_de_documento = response.data.Numero_de_documento;
                    this.Genero = response.data.Genero;
                    this.Telefono = response.data.Telefono;
                    this.Direccion = response.data.Direccion;
                    this.Correo = response.data.Correo;
                    this.Estado_civil = response.data.Estado_civil;
                    this.Fecha_de_nacimiento = response.data.Fecha_de_nacimiento;
                    this.EPS = response.data.EPS;
                    this.Contraseña = response.data.Contraseña;
                })
                .catch((error) => {
                    console.error("error al consultar al cliente:",error);
                });
        },

        Actulizar(){
            axios
              .put("http://localhost:8080/api/clientes/actualizar/"+this.Numero_de_documento,{
                Nombre: this.Nombre,
                Tipo_documento:this.Tipo_documento,
                Numero_de_documento:this.Numero_de_documento,
                Genero:this.Genero,
                Telefono:this.Telefono,
                Direccion:this.Direccion,
                Correo:this.Correo,
                Estado_civil:this.Estado_civil,
                Fecha_de_nacimiento:this.Fecha_de_nacimiento,
                EPS:this.EPS,
                Contraseña:this.Contraseña,
              })
              .then((response) =>{
                console.log("Actualizacion exitosa:",response.data);
              })
              .catch((error) => {
                console.error("error en la actualización",error);
              });
        },
        Eliminar(){
            axios
            .delete("http://localhost:8080/api/clientes/"+this.Numero_de_documento)
            .then(() => {
                console.log("Cliente eliminado con exito");
                //limpiar los campos del formulario despues de eliminar
                this.Nombre ="";
                this.Tipo_documento ="";
                this.Numero_de_documento = "";
                this.Genero ="";
                this.Telefono = "";
                this.Direccion = "";
                this.Correo = "";
                this.Estado_civil = "";
                this.Fecha_de_nacimiento = "";
                this.EPS = "";
                this.Contraseña = "";

            })
            .catch((error) =>{
                console.error("error al eliminar al usuario:", error);
            });
        },
    },
};
</script>
