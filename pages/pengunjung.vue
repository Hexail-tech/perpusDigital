<template>
  <div>
    <div class="text-center py-3">
      <h1>Catatan Pengunjung Perpustakaan</h1>
      <h4>SMKN 4 Tasikmalaya</h4>
    </div>
    <div class="table-responsive py-3">
      <NuxtLink to="/" class="btn btn-dark">Isi Buku Kunjungan</NuxtLink>
      <table class="table table-bordered table-striped my-3">
        <thead>
          <tr>
            <th>No</th>
            <th>tanggal</th>
            <th>nama</th>
            <th>keanggotaan</th>
            <th>kelas</th>
            <th>keperluan</th>
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
    .select();
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>
