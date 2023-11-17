<template>
  <div class="form col-md-6 offset-md-3 mt-5">
    <h2 class="mt-5 text-center text-white">Isi buku kunjungan disini.</h2>
    <form @submit.prevent="tambahData()">
      <div class="mb-3">
        <label for="exampleFormControlInput1">Nama</label>
        <input v-model="nama" type="text" class="form-control" id="exampleFormControlInput1" />
      </div>
      <div class="form-group py-3">
        <label for="exampleFormControlSelect1">Keanggotaan</label>
        <select v-model="keanggotaan" class="form-control form-select" id="exampleFormControlSelect1">
          <option value="Guru">Guru</option>
          <option value="Staf">Staf</option>
          <option value="Siswa">Siswa</option>
          <option value="Umum">Umum</option>
        </select>
      </div>
      <div v-if="keanggotaan === 'Siswa'" class="form-group py-3">
        <label for="exampleFormControlSelect1">Kelas Lengkap</label>
        <select v-model="tingkatan" class="form-control form-select" id="exampleFormControlSelect1">
          <option disabled value="">Tingkatan</option>
          <option value="X">X </option>
          <option value="XI">XI </option>
          <option value="XII">XII </option>
        </select>
        <select v-model="jurusan" class="form-control form-select mt-3" id="exampleFormControlSelect1">
          <option disabled value="">Jurusan</option>
          <option value="PPLG">PPLG</option>
          <option value="TJKT">TJKT</option>
          <option value="TBSM">TBSM</option>
          <option value="DKV">DKV</option>
          <option value="TOI">TOI</option>
        </select>
        <select v-model="kelas" class="form-control form-select mt-3" id="exampleFormControlSelect1">
          <option disabled value="">Kelas</option>
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
        </select>
      </div>
      <div class="form-group py-3">
        <label for="exampleFormControlTextarea1">Keperluan</label>
        <textarea v-model="keperluan" class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
      </div>
      <button type="submit" class="btn btn-primary my-2">Kirim</button>
    </form>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const nama = ref("");
const keanggotaan = ref("");
const keperluan = ref("");
const tingkatan = ref("");
const jurusan = ref("");
const kelas = ref("");
const kelasLengkap = ref("");

async function tambahData() {
  kelasLengkap.value = `${tingkatan.value} ${jurusan.value} ${kelas.value}`
  const { error } = await supabase
    .from("dataPengunjung")
    .insert([
      {
        nama: nama.value,
        kategori: keanggotaan.value,
        kelas: kelasLengkap.value,
        keperluan: keperluan.value
      }]);
  if (error) throw error
  else navigateTo('/pengunjung')
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Libre+Baskerville:wght@700&family=Poppins:wght@400;500;900&display=swap');

label {
  color: white;
  font-family: 'Poppins', sans-serif;
}

h2 {
  font-family: 'Libre Baskerville', serif;
  font-family: 'Poppins', sans-serif;
}

.form {
  margin-bottom: 200px;
}

::placeholder {
  color: black;
}
</style>
