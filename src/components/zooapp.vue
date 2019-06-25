<template>
    <div>
        <h3>Lista Zivotinja</h3>
        <table>
            <tr v-for="(zivotinja, index) in spisak_zivotinja" :key="index" >
                <td>{{ zivotinja.vrsta }}</td>
                <td>{{ zivotinja.ime}}</td>
                <td>{{ zivotinja.datum_rodjenja || "NEPOZNATO" }}</td>
                <td><button @click="izbrisi_zivotinju(index)">Izbrisi</button></td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    data () {
        return {
            spisak_zivotinja: [
                {vrsta:'Zec' , ime:'Svetislav' , datum_rodjenja: '1.1.1990'},
                {vrsta:'Konj' , ime:'Cvetko' , datum_rodjenja: '4.10.2000'},
                {vrsta:'Koza' , ime:'Dragica' , datum_rodjenja: '5.5.2006'},
                {vrsta:'Glista' , ime:'Miroslav' , datum_rodjenja: ''},
                {vrsta:'Pcela' , ime:'Rajka' , datum_rodjenja: '8.1.1980'},
            ]
        }
    },

    methods : {
        izbrisi_zivotinju (index) {
            this.spisak_zivotinja.splice(index,1)
        }
    }
}
</script>

<style>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
