<template>
<!-- Kode Form Input -->
  <form class="container">
  <label>NIK:</label><br>
  <input type="text" placeholder="masukkan nik"><br>
  <label>Nama Karyawan</label><br>
  <input type="text" placeholder="tulis nama karyawan"><br>
  <label>Jabatan</label><br>
  <input type="text" placeholder="jabatan"><br>
  <label>Alamat</label><br>
  <input type="text" placeholder="alamat"><br>
  <label>Gaji Pokok</label><br>
  <input type="text" placeholder="gaji pokok"><br>
  <label>Tunjangan</label><br>
  <input type="text" placeholder="tunjangan"><br>
  <label>Jam Lembur</label><br>
  <input type="text" placeholder="jam lembur"><br>
  <label>Total Gaji</label><br>
  <input type="text" placeholder="total gaji"><br>
  <input type="submit" value="Submit">
</form> 

<!-- Kode tampilkan data -->
  <div class="flex-container" v-for="item in karyawan" :key="item.nik">
    <ul>
      <li>No. Induk Karyawan : {{item.nik}}</li>
      <li>Nama Karyawan : {{item.nama}}</li>
      <li>Jabatan : {{item.jabatan}}</li>
      <li>Alamat : {{item.alamat}}</li>
      <li>Gaji Pokok : {{item.gaji-pokok}}</li>
      <li>Tunjangan : {{item.tunjangan}}</li>
      <li>Jam Lembur : {{item.jam-lembur}}</li>
      <li>Total Gaji : {{item.total-gaji}}</li>
      <button @click.prevent="hapus(item.nik)">delete</button>
      </ul>
  </div>

</template>

<script>
import Axios from 'axios'

export default {
    name: "karyawan",

     data() {
    return {
      karyawan: {},
    };
  },
  mounted() {
    Axios.get("http://localhost:3000/karyawan")
      .then((res) => {
        this.karyawan = res.data;
        console.log(res.data);
      })
      .catch((err) => {
        console.log(err);
      });
  },
}
</script>

<style scoped>
.container{
  text-align: center;
  display: inline-block;
  margin: auto;
  padding: 40px;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

.flex-container{
  display: inline-flex;
  padding: 5px;
  margin: 10px;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

ul{
  display: flexbox;
}
</style>