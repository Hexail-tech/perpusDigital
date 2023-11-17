<template>
  <div class="body pt-5">
    <div class="text-center py-3 text-light">
      <h3>Catatan Pengunjung Perpustakaan</h3>
      <h1>SMKN 4 Tasikmalaya</h1>
    </div>
    <div class="table-responsive py-3">
      <NuxtLink to="/" class="btn btn-primary">Isi Buku Kunjungan</NuxtLink>
      <table class="table table-bordered my-3 text-light">
        <thead>
          <tr>
            <th>No</th>
            <th>Tanggal</th>
            <th>Nama</th>
            <th>Keanggotaan</th>
            <th>Kelas</th>
            <th>Keperluan</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(dataPengunjung, index) in visitors" :key="dataPengunjung.id">
            <td>{{ index + 1 }}</td>
            <td>{{ dataPengunjung.tanggal }}</td>
            <td>{{ dataPengunjung.nama }}</td>
            <td>{{ dataPengunjung.kategori }}</td>
            <td>{{ dataPengunjung.kelas }}</td>
            <td>{{ dataPengunjung.keperluan }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
useHead({ title: "Pengunjung - Aplikasi Buku Kunjungan" })

const supabase = useSupabaseClient()
const visitors = ref([]);

async function getData() {
  const { data, error } = await supabase
    .from("dataPengunjung")
    .select()
    .order('id', { ascending: false })
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Libre+Baskerville:wght@700&family=Poppins:wght@400;500;900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Libre+Baskerville:wght@700&family=Poppins:wght@400;500;900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Libre+Baskerville:wght@700&family=Poppins:wght@300;400;500;900&display=swap');

h3 {
  font-family: 'Libre Baskerville', serif;
  font-family: 'Poppins', sans-serif;
}

h1 {
  font-family: 'Libre Baskerville', serif;
  font-family: 'Poppins', sans-serif;
}

th {
  font-family: 'Libre Baskerville', serif;
  font-family: 'Poppins', sans-serif;

}

td {
  font-family: 'Libre Baskerville', serif;
  font-family: 'Poppins', sans-serif;
}

.btn {
  font-family: 'Libre Baskerville', serif;
  font-family: 'Poppins', sans-serif;
}
</style>