<template>
    <div>
        <div id="SubEdicion">

        <form @submit.prevent="editarNota(notaEditar)" v-if="editar">
        <h4 id="aaa">Editar nota</h4>
        <section class="form-register2">

        </section>
        <input type="text" class="control2" placeholder="Nombre Propietario" v-model="formularioEditar.NombreProp">
        <input type="text" class="control2" placeholder="Nombre Mascota" v-model="formularioEditar.NombreMasc">
        <input type="text" class="control2" placeholder="Edad Mascota" v-model="formularioEditar.NombreMasc">
        <input type="text" class="control2" placeholder="Direccion" v-model="formularioEditar.Direccion">
        <input type="text" class="control2" placeholder="Celular" v-model="formularioEditar.Celular">
        <br>
        <b-button class="btn-success my-2 mx-2" type="submit">Editar</b-button>
        <b-button class=" my-2" type="submit" @click="editar=false">Cancelar</b-button>

        </form>

        </div>
        
        <div id="SubFormulario">

        <table class="table">
        <thead>
            <tr>
                <th id="pruebacolumna" scope="col">Nombre Propietario</th>
                <th id="pruebacolumna" scope="col">Nombre Mascota</th>
                <th id="pruebacolumna" scope="col">Edad Mascota</th>
                <th id="pruebacolumna" scope="col">Direccion</th>
                <th id="pruebacolumna" scope="col">Celular</th>
                <th id="pruebacolumna" scope="col">Acciones</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item, index) in vistaformulario" :key="index">
                <th scope="row">{{item._id}}</th>
                <td>{{item.NombreProp}}</td>
                <td>{{item.NombreMasc}}</td>
                <td>{{item.EdadMasc}}</td>
                <td>{{item.Direccion}}</td>
                <td>{{item.Celular}}</td>
                <td>
                    <b-button class="btn-danger mx-2" @click="eliminarNota(item._id)">Eliminar</b-button>
                    <b-button class="btn-warning mx-2" @click="activarEdicion(item._id)">Editar</b-button>
                </td>
            </tr>

        </tbody>
        </table>

        </div>
            
        

    </div>

    
</template>

<script>
export default {
    
data() {
        return{
            vistaformulario:[],
            editar:true,
            formularioEditar:{}
        
    }


},

created() {

        this.listarNotas();

},

methods: {

        listarNotas() {

            this.axios.get('/nota')
                .then(res => {
                    console.log(res.data);
                    this.vistaformulario = res.data;

                })
                .catch(e => {

                    console.log(e.response);

                })

        },

        eliminarNota(id){

            this.axios.delete(`/nota/${id}`)
            .then(res=>{

                const index = this.vistaformulario.findIndex(item=> item._id===res.data._id);
                this.vistaformulario.splice(index, 1);
                this.mensaje.color="success";
                this.mensaje.texto="Nota Eliminada";
                this.showAlert();


            })
            .catch(e=>{

                  console.log(e.response);

            })
        },

        activarEdicion(id){

            this.editar=true;
            this.axios.get(`/nota/${id}`)
            .then(res=>{

                this.vistaformularioEditar=res.data;

            })
            .catch(e=>{

                 console.log(e.response);


            })


        },

        editarNota(item){
            
            this.axios.put(`/nota/${item._id}`, item)
            .then(res=>{
                const index= this.vistaformulario.findIndex(n=> n._id===res.data._id);
                this.vistaformulario[index].NombreProp=res.data.NombreProp;
                this.vistaformulario[index].NombreMasc=res.data.NombreMasc;
                this.vistaformulario[index].EdadMasc=res.data.EdadMasc;
                this.vistaformulario[index].Direccion=res.data.Direccion;
                this.vistaformulario[index].Celular=res.data.Celular;

                // this.mensaje.color="success";
                // this.mensaje.texto="Nota Editada";
                // this.showAlert();
                // this.editar=false;


            })
            .catch(e=>{

                console.log(e.response);

            })
        }

}
}
</script>

<style>
    #pruebacolumna{
        text-align: center;
    }

    
#SubEdicion{
    height: auto;
    width: 100%;
    text-align: center;
    float: left;
    
}

#SubFormulario{
    height: auto;
    width: 100%;
    float: left;
}

.form-register2{

            width: 50%;
            border-radius: 8px;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: rgb(64, 46, 127);
            
        
        }

        .control2{
            width:60%;
            padding: 10px;
            border-radius: 4px;
            border: 1px solid;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-size: 18px;
            color: rgb(64, 46, 127);
            margin-bottom: 10px;
            

        }

        #aaa{
            font-size:20px;
            padding-top: 10px;
            text-align: center;
            color: rgb(0, 0, 0);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-weight: bold;
        }
</style>