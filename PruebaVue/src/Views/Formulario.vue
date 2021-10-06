<template>
    <div id="body">
        <Cabecera></Cabecera>
        <MenuNavegacion></MenuNavegacion>
        <!-- "Main Formulario " -->
            <div id="main">
            <section class="form-register">
                <h4>Formulario de Registro</h4>
                <input class="control" type="text" name="Nombres" id="nombres" placeholder="Ingrese sus nombres">
                <input class="control" type="text" name="Apellidos" id="Apellidos" placeholder="Ingrese sus apellidos">
                <input class="control" type="email" name="correo" id="Correo" placeholder="Ingrese su correo">
                <input class="control" type="text" name="direccion" id="direccion" placeholder="Ingrese su dirección">
                <input class="control" type="text" name="celular" id="celular" placeholder="Ingrese su celular">
                <input class="control" type="password" name="Contraseña" id="Contraseña" placeholder="Ingrese su contraseña">
                <p>Estoy de acuerdo con <a href="terminos_condiciones.pdf">Terminos y Condiciones</a></p>
                <input class="botons" type="button" value="Registrar">
                <p><a href="login.html">Ya tengo una cuenta</a></p>
            </section>
        </div>    
        <!-- a -->
        <Barra></Barra>
        <PiePagina></PiePagina>
    </div>
</template>

<script>
import Cabecera from '../components/Cabecera.vue'
import MenuNavegacion from '../components/MenuNavegacion.vue'
import Barra from '../components/Barra.vue'
import PiePagina from '../components/PiePagina.vue'

export default {
  components: { 
    Cabecera, 
    MenuNavegacion,
    Barra,
    PiePagina
    }
}
</script>

<style>
#body {
  height: 1440px;
  width: 100%;
  font-family: "Arial";
  border-color: blue;
  border-style: solid;
}

#main{
    height: 74%;
    width: 100%;
    background: red;
    float: left;
    text-align: center;
    
}

.form-register{

            width: 400px;
            /* background:; */
            padding: 30px;
            margin: auto;
            margin-top: 50px;
            margin-bottom: 50px;
            border-radius: 8px;
            font-family: 'Exo', sans-serif;
            color: rgb(64, 46, 127);
            
        
        }

        .form-register h4{
            font-size:20px;
            margin-bottom: 20px;
            text-align: center;
            color:blue;
            font-family: 'Exo', sans-serif;
        }

        .control{
            width:100%;
            
            padding: 10px;
            border-radius: 4px;
            margin-bottom: 16px;
            border: 1px solid;
            font-family: 'Exo', sans-serif;
            font-size: 18px;
            color: rgb(64, 46, 127);
            

        }

        .form-register p{
          height: 40px;
          text-align: center;
          font-family: 'Exo', sans-serif;
          font-size: 16px;
          line-height: 40px;
        }

        .form-register a{
            color:rgb(64, 46, 127);
            text-decoration: none;
        }

        .form-register a:hover{
            color:rgb(64, 46, 127);
            text-decoration: underline;
        }

        .form-register .botons{
            width: 100%;
            
            font-family: 'Exo', sans-serif;
            color: blue;
            border-radius: 2px solid black;
            padding: 12px;
            font-size: 16px;
            margin: 16px 0;
        }

        .form-register .botons:hover{
            color:rgb(64, 46, 127);
            text-decoration: underline;
        }

        .login input[type=button]:focus{
            outline: none;
            
        }

</style>
