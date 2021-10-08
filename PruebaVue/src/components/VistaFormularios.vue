<template>
    <table class="table">
        <thead>
            <tr>
                <th id="pruebacolumna" scope="col">Nombre Propietario</th>
                <th id="pruebacolumna" scope="col">Nombre Mascota</th>
                <th id="pruebacolumna" scope="col">Edad Mascota</th>
                <th id="pruebacolumna" scope="col">Direccion</th>
                <th id="pruebacolumna" scope="col">Celular</th>
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
            </tr>

        </tbody>
    </table>
</template>

<script>
export default {
    
data() {
        return{
            vistaformulario:[]
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

        }

}
}
</script>

<style>
    #pruebacolumna{
        text-align: center;
    }

    .table{
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
</style>