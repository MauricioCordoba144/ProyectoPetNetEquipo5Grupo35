<template>
    <div id="menu_navegacion">
            <ul>
                <li id="prueblist"><router-link to="home">Home</router-link></li>
                <li id="prueblist">|</li>
                <li id="prueblist"><router-link to="pageadoptante">Adoptante</router-link></li>
                <li id="prueblist">|</li>
                <li id="prueblist"><router-link to="pagedonante">Donante</router-link></li>
                <li id="prueblist">|</li>
                <li id="prueblist"><router-link to="formulario">Formulario</router-link></li>
                <li id="prueblist">|</li>
                <li id="prueblist"><a href="login.html">Ingresar</a></li>
            </ul>
      
        </div>

</template>



<style>
#menu_navegacion{
    height: 5%;
    background-color: rgb(16, 221, 221);
    text-align: center;
}

ul{
    list-style: none;
    display: inline-block;
    padding:5px;
}

#prueblist{
    float:left;
    margin-top: 1.2%;
    text-decoration:dotted;
    padding: 5px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: larger;
}

a{
    text-decoration:dotted;
    padding: 35px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

</style>
