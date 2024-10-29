<template>
    <div>
        <h1 style="color:red">Tabla Multiplicar</h1>
        <label>Introduzca número</label>
        <input type="number" v-model="numero"/>
        <button @click="generarTabla()">
            Generar tabla
        </button>
        <table border="1">
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody v-html="html"></tbody>
        </table>
        <table v-if="numero != 0" style="background-color:lightblue">
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="contador in 10" :key="contador">
                    <td> {{ $filters.getOperacion(numero, contador)}} </td>
                    <td> {{ $filters.getMultiplicacion(numero, contador)}} </td>
                </tr>
            </tbody>
        </table>        
        <table v-if="numero != 0" style="background-color:lightgreen">
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="contador in 10" :key="contador">
                    <td>{{ numero + " * " + contador }}</td>
                    <td>{{ numero * contador }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        name: "TablaMultiplicar",
        data() {
            return {
                numero: 0,
                html: ""
            }
        }, 
        methods: {
            generarTabla() {
                let aux = "";
                for (var i = 1; i <= 10; i++){
                    var operacion = this.numero + " * " + i;
                    var resultado = this.numero * i;
                    aux += "<tr>";
                    aux += "<td>" + operacion + "</td>";
                    aux += "<td>" + resultado + "</td>";
                    aux += "</tr>";
                }
                this.html = aux;
            }
        }
    }
</script>