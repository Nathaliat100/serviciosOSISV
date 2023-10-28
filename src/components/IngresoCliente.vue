<template>
  <div class="contenedor">
        <h1>Clientes</h1>
        <form id="ingresar" @submit.prevent="ingresar">
            <div class="grupofor">
                <label for="tipo de documento">Tipo de Documento</label>
                <select id="doc">
                    <option value="seleccione">Seleccione</option>
                    <option value="Cedula">Cedula</option>
                    <option value="Tarjeta de identidad">Tarjeta de identidad</option>
                    <option value="Cedula de extranjeria">Cedula de extranjeria</option>
                    <option value="Otro">Otro</option>
            
                </select>
            </div> 
            <div class="grupofor">
                <label for="Numero de doc">Numero de documento</label>
                <input type="number" id="numdoc" name="numerdoc" required v-model="numerdoc">  
            </div>
            <div class="grupofor">
                <label for="contraseña">Contraseña</label>
                <input type="password" id="contraseña" name="contraseña" required v-model="contraseña">
            </div>
            <button type="button" id="ingresar" name="ingresar" @click="ingresar">Iniciar sesión</button>
        </form>
    </div>
</template>
<script>
</script>