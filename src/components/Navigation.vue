<template>
    <div>
        <b-navbar type="dark" variant="danger">
            <b-navbar-nav>
                <b-nav-item to="/">Home</b-nav-item>
                <b-nav-item to="/longitud">Longitud</b-nav-item>
                <b-nav-item to="/monedas">Monedas</b-nav-item>
                <b-nav-item to="/masa">Masa</b-nav-item>
                <b-nav-item to="/tiempo">Tiempo</b-nav-item>
                <b-nav-item to="/almacenamiento">Almacenamiento</b-nav-item>
            </b-navbar-nav>
        </b-navbar>
        <router-view/>
    </div>  
</template>
<script>
export default {
    name:'Navigation'
}
</script>