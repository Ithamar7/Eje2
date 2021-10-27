<template>
    <div class="container animate__animated animate__fadeIn">
        <h3>Gráficas</h3>
        <div class="row">
            <div id="chart_col" class="col-md-8"></div>
            <div id="chart_pie" class="col-md-4"></div>
        </div>
    </div>
</template>


<script>
export default{
    name:'Graficas',
    props: {
        datos: Object,
    },
    data(){

    },
    computed: {

    },
    methods:{
carga(){
    console.log(this.datos);
}
    }
}
</script>

<style scoped>

</style>
