<template>
    <div>
        <form @submit.prevent="dodajZivotinju">
            <select name="" id="klasa" class="form-control" v-model="novaZivotinja.klasa">
                <option value="Sisari">Sisari</option>
                <option value="Reptili">Reptili</option>
                <option value="Ribe">Ribe</option>
                <option value="Crvi">Crvi</option>
                <option value="Insekti">Insekti</option>
            </select>
            <div class="form-group">
                <label for="vrsta">Vrsta</label>
                <input type="text" class="form-control" id="vrsta" v-model="novaZivotinja.vrsta" required />
            </div>
            <div class="form-group">
                <label for="ime">Ime</label>
                <input type="text" class="form-control" id="ime" v-model="novaZivotinja.ime" required />
            </div>
            <div class="form-group">
                <label for="datum_rodjenja">Datum rodjenja</label>
                <input type="date" class="form-control" id="datum_rodjenja" v-model="novaZivotinja.datum_rodjenja" required />
            </div>
            <div class="form-group">
                <button class="btn btn-primary" type="submit">Dodaj Zivotinju</button>
            </div>
        </form>

        <h3>Lista Zivotinja</h3>
        <table>
            <tr v-for="(zivotinja, index) in spisak_zivotinja" :key="index" >
                <td>{{ zivotinja.klasa }}</td>
                <td>{{ zivotinja.vrsta }}</td>
                <td>{{ zivotinja.ime}}</td>
                <td>{{ zivotinja.datum_rodjenja || "NEPOZNATO" }}</td>
                <td>
                    <button @click="izbrisiZivotinju(index)">Izbrisi</button>
                    <button @click="prvaNaListi(index)">Na Vrh</button>
                    </td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    data () {
        return {
            novaZivotinja: {
                klasa: '',
                vrsta: '',
                ime: '',
                datum_rodjenja: ''
            },
            spisak_zivotinja: [
                {klasa:'Sisar', vrsta:'Zec' , ime:'Svetislav' , datum_rodjenja: '1.1.1990'},
                {klasa:'Sisar', vrsta:'Konj' , ime:'Cvetko' , datum_rodjenja: '4.10.2000'},
                {klasa:'Sisar', vrsta:'Koza' , ime:'Dragica' , datum_rodjenja: '5.5.2006'},
                {klasa:'Crvi', vrsta:'Glista' , ime:'Miroslav' , datum_rodjenja: ''},
                {klasa:'Insekti',vrsta:'Pcela' , ime:'Rajka' , datum_rodjenja: '8.1.1980'},
            ]
        }
    },

    methods : {
        izbrisiZivotinju (index) {
            this.spisak_zivotinja.splice(index,1)
        },
        prvaNaListi (index) {
           let zivotinja = this.spisak_zivotinja[index]
           this.spisak_zivotinja.splice(index,1)
           this.spisak_zivotinja.unshift(zivotinja)
        },
        dodajZivotinju () {
            this.spisak_zivotinja.push({...this.novaZivotinja})
            this.novaZivotinja = {
                klasa: '',
                vrsta: '',
                ime: '',
                datum_rodjenja: ''
            }
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
