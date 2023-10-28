<template>
    <div class="clientes">
        <div class="componentes">
        <FormularioClientes/>
        </div>
    </div>
</template>

<script>
import FormularioClientes from "@/components/FormularioClientes.vue";

export default {
name: 'ClienteView',

  components:{
    FormularioClientes,
  }
}
</script>
<style>
body{
 font-family: Arial, Helvetica, sans-serif;
 margin: 0%;
}
.formularioregis{
  background-color: rgb(54, 181, 190);
  margin: 5%;
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.20);
  margin-top: 0%;
}
h1{
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-weight: 900;
  margin: 0%;
  color: black;
}
#regis{
  justify-content: center;
  display: grid;  
}
.grupores{
  display: flex;
  padding: 1px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: black; 
}
input{
  width: 100%;
}
select{
  width: 100%;
}
button{
  color: rgb(0, 0, 0);
  border-color: rgb(149, 255, 255);
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
</style>


