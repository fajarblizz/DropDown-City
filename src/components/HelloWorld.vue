<template>
<div class="cascading-dropdown">
            <div class="dropdown">
                <span>Propinsi:</span>
                <select v-model="selectedPropinsi">
                    <option value="">Pilih Provinsi</option>
                    <option v-for="(propinsi_obj, propinsi) in tempat" :value="propinsi" v-bind:key="propinsi">{{propinsi}}</option>
                </select>
            </div><br>
             <div class="dropdown">
                <span>Kota:</span>
                <select :disabled="kota.length == 0" v-model="selectedKota">
                    <option value="">Pilih Kota</option>
                    <option v-for="(kota_obj, kota) in kota"  v-bind:key="kota">{{kota}}</option>
                </select>
            </div>
        </div>
</template>

<script>
export default {
  data: function () {
    return {
      tempat: {
        'Jawa Timur': {
          Surabaya: [],
          Malang: [],
          Gresik: [],
          Banyuwangi: [],
          Madiun: []
        },
        'Jawa Tengah': {
          Solo: [],
          Semarang: [],
          Magelang: [],
          Boyolali: [],
          Klaten: []
        }
      },
      kota: [],
      selectedPropinsi: '',
      selectedKota: ''
    }
  },
  watch: {
    selectedPropinsi: function () {
      // Clear previously selected values
      this.kota = []
      this.selectedKota = ''
      // Populate list of countries in the second dropdown
      if (this.selectedPropinsi.length > 0) {
        this.kota = this.tempat[this.selectedPropinsi]
      }
    },
    selectedKota: function () {
    }
  }
}
</script>

<style >
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center ;
  color: #2c3e50;
}
.cascading-dropdown{
   text-align: center;
    margin-left: 400px;
    margin-right: 400px;
    margin-top: 30px;
    background-color: rgb(188, 231, 31);
    border-style: solid;
    border-color: black;
    align-content: center;
}

</style>
