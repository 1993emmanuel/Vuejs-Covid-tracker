<template>
    <div class="text-center bg-blue-800 text-white p-4 mb-10 footer">
        <footer>
            <p class="text-bold capitalize">
                &copy; Parte de practicas de Vuejs hecho por Emmanuel hernandez mejia - {{getActualYear()}}
            </p>
        </footer>
    </div>    
</template>

<script>

export default{
    methods:{
        getActualYear(){
            const fecha = new Date;
            return fecha.getFullYear();
        }
    }
}
</script>

<style scoped>
.footer{
    width: 95%;
    position:absolute;
    bottom: 0;
}
</style>