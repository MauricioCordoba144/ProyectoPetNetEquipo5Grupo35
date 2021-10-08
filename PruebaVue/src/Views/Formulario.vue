<template>
    <div id="body">
        <Cabecera></Cabecera>
        <MenuNavegacion></MenuNavegacion>
        <!-- "Main Formulario " -->
        <div id="main123">
            <section class="form-register" @submit.prevent="PublicarFormulario">
                <br> <br> <br> <br> <br> <h4>Formulario de inscripcion </h4>
                <input class="control" type="text" placeholder="Ingrese nombres del propietario" v-model="formulario.NombreProp">
                <input class="control" type="text" placeholder="Ingrese nombre de la mascota" v-model="formulario.NombreMasc">
                <input class="control" type="number" placeholder="Ingrese edad de la mascota" v-model="formulario.EdadMasc">
                <input class="control" type="text" placeholder="Ingrese direccion del propietario" v-model="formulario.direccion">
                <input class="control" type="email" placeholder="Ingrese correo del propietario" v-model="formulario.correo">
                <input class="control" type="text" placeholder="Ingrese celular del propietario" v-model="formulario.celular">
                <br> <br>
                <p id="aa">Estoy de acuerdo con: <a href="terminos_condiciones.pdf">Terminos y Condiciones</a></p>
                <!-- <input class="botons" type="button" value="Registrar"> -->
                <button class="botons" type="submit">Registrar formulario</button>
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
    },

    data() {
        return{
            formulario:{NombreProp:"", NombreMasc:"", EdadMasc:"", Direccion:"", Correo:"", Celular:""}
        }
    },

    methods: {

        PublicarFormulario(){
            this.axios.post('/nuevoformulario',this.formulario)
            .then(res=>{

                this.formulario.push(res.data)
                this.formulario.NombreProp="";
                this.formulario.NombreMasc="";
                this.formulario.EdadMasc="";
                this.formulario.Direccion="";
                this.formulario.Correo="";
                this.formulario.Celular="";

                this.mensaje.color="success";
                this.mensaje.texto="Nota Agregada";
                this.showAlert();

            })
            .catch(e=>{

                console.log(e.response);

            })
        }

    }



}
</script>

<style>
#body{
  height: 100%;
  width: 100%;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  border-color: blue;
  border-style: solid;
}

#aa{
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-weight: bold;
}

#main123{
    height: 74%;
    width: 100%;
    float: left;
    text-align: center;
    background-image: url(http://ginva.com/wp-content/uploads/2012/02/funny-animal-potrait-photography-16.jpg);
    background-size: 125%;
    background-repeat: no-repeat;
    background-position-x: 80%;
    background-position-y: 50%;
}

.form-register{

            width: 50%;
            /* background: ; */
            padding: 15px;
            margin: auto;
            margin-top: 10%;
            margin-bottom: 50px;
            border-radius: 8px;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: rgb(64, 46, 127);
            
        
        }

        .form-register h4{
            font-size:40px;
            margin-bottom: 20px;
            text-align: center;
            color: rgb(0, 0, 0);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-weight: bold;
        }

        .control{
            width:100%;
            
            padding: 10px;
            border-radius: 4px;
            margin-bottom: 16px;
            border: 1px solid;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-size: 18px;
            color: rgb(64, 46, 127);
            

        }

        .form-register p{
          height: 40px;
          text-align: center;
          font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
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
            
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
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
