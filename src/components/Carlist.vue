<template>
    <div>
        <h1>Car Table</h1>
        <table>
            <tbody>
                <tr v-for="(car, index) in cars" v-bind:key="index">
                    <td>{{car.brand}}</td>
                    <td>{{car.model}}</td>
                    <td>{{car.color}}</td>
                    <td>{{car.fuel}}</td>
                    <td>{{car.year}}</td>
                    <td>{{car.price}}</td>
                </tr>
            </tbody>
        </table>
    </div>    
</template>

<script>
import axios from 'axios';

export default {
    name: 'Carlist',
    data(){
        return {
            cars: []
        }
    },
    mounted() {
        axios.get('https://carstockrest.herokuapp.com/cars')
        .then(response => (this.cars = response.data._embedded.cars))
    }
}
</script>

<style scoped>
    table {
        margin: auto;
    }
</style>