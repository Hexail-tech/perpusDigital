<template>
  <div>
    <div class="kunjungan py-5">
      <div class="text-center">
        <h2>Isi buku kunjungan disini.</h2>
      </div>
      <form @submit.prevent="tambahData">
        <div class="form-group py-3">
          <label for="exampleFormControlInput1">Nama</label>
          <input v-model="nama" type="nama" class="form-control" id="exampleFormControlInput1" />
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
          <label for="exampleFormControlSelect1">Kelas</label>
          <select v-model="kelas" class="form-control form-select" id="exampleFormControlSelect1">
            <option value="X PPLG 1">X PPLG 1</option>
            <option value="X PPLG 2">X PPLG 2</option>
            <option value="X PPLG 3">X PPLG 3</option>
            <option value="X PPLG 4">X PPLG 4</option>
            <option value="X TJKT 1">X TJKT 1</option>
            <option value="X TJKT 2">X TJKT 2</option>
            <option value="X TJKT 3">X TJKT 3</option>
            <option value="X TJKT 4">X TJKT 4</option>
            <option value="X TBSM 1">X TBSM 1</option>
            <option value="X TBSM 2">X TBSM 2</option>
            <option value="X TBSM 3">X TBSM 3</option>
            <option value="X TBSM 4">X TBSM 4</option>
            <option value="X DKV 1">X DKV 1</option>
            <option value="X DKV 2">X DKV 2</option>
            <option value="X TOI 1">X DKV 1</option>
            <option value="XI PPLG 1">XI PPLG 1</option>
            <option value="XI PPLG 2">XI IPPLG 2</option>
            <option value="XI PPLG 3">XI PPLG 3</option>
            <option value="XI PPLG 4">XI PPLG 4</option>
            <option value="XI TJKT 1">XI TJKT 1</option>
            <option value="XI TJKT 2">XI TJKT 2</option>
            <option value="XI TJKT 3">XI TJKT 3</option>
            <option value="XI TJKT 4">XI TJKT 4</option>
            <option value="XI TBSM 1">XI TBSM 1</option>
            <option value="XI TBSM 2">XI TBSM 2</option>
            <option value="XI TBSM 3">XI TBSM 3</option>
            <option value="XI TBSM 4">XI TBSM 4</option>
            <option value="XI DKV 1">XI DKV 1</option>
            <option value="XI DKV 2">XI DKV 2</option>
            <option value="XI TOI 1">XI TOI 1</option>
            <option value="XII PPLG 1">XII PPLG 1</option>
            <option value="XII PPLG 2">XII PPLG 2</option>
            <option value="XII PPLG 3">XII PPLG 3</option>
            <option value="XII TJKT 1">XII TJKT 1</option>
            <option value="XII TJKT 2">XII TJKT 2</option>
            <option value="XII TJKT 3">XII TJKT 3</option>
            <option value="XII TBSM 1">XII TBSM 1</option>
            <option value="XII TBSM 2">XII TBSM 2</option>
            <option value="XII TBSM 3">XII TBSM 3</option>
          </select>
        </div>
        <div class="form-group py-3">
          <label for="exampleFormControlTextarea1">Keperluan</label>
          <textarea v-model="keperluan" class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
        </div>
        <button type="submit" class="btn btn-primary my-2">Kirim</button>
      </form>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const nama = ref("");
const keanggotaan = ref("");
const keperluan = ref("");
const kelas = ref("");

async function tambahData() {
  const { error } = await supabase
    .from("dataPengunjung")
    .insert([
      {
        nama: nama.value,
        kategori: keanggotaan.value,
        kelas: kelas.value,
        keperluan: keperluan.value
      }]);
  if (error) throw error
  else navigateTo('/pengunjung')
}
</script>
