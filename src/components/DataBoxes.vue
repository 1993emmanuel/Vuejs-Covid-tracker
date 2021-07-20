<template>
<div class="grid md:grid-cols-2 gap-4">
    <!-- box-1 -->
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
        <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
        <div class="text-2xl mb-4">
            <span class="font-bold">New: </span>
            {{numberWithCommas(stats.NewConfirmed)}}
        </div>
        <div class="text-2xl mb-4">
            <span class="font-bold">Total: </span>
            {{numberWithCommas(stats.TotalConfirmed)}}
        </div>
    </div>

    <!-- box-2 -->
    <div class="shadow-md bg-blue-200 p-10 text-center rounded">
        <h3 class="text-3xl text-blue-900 font-bold mb-4">Death</h3>
        <div class="text-2xl mb-4">
            <span class="font-bold">New Deaths: </span>
            {{numberWithCommas(stats.NewDeaths)}}
        </div>
        <div class="text-2xl mb-4">
            <span class="font-bold">TotalDeaths: </span>
            {{numberWithCommas(stats.TotalDeaths)}}
        </div>
    </div>

</div>
</template>



<script>

export default {
    name : 'DataBoxes',
    props :{
        stats : Object,
    },
    methods:{
        numberWithCommas(number){
            return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
}

</script>
