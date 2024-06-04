<template>
    <div class="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="../pengunjung/tambah">
                    <div class="card bg-pengunjung rounded-5">
                        <div class="card-body">
                            <h2>pengunjung</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>           
            <div class="col-lg-6">
                <nuxt-link to="/buku/">
                    <div class="card bg-buku rounded-5">
                        <div class="card-body">
                            <h2>cari buku</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
        </div>
    </div>
    <h2><strong>STATISTIK</strong></h2>
<div class="Container-fluid">
    <div class="row justify-cotent-evenly rounded-3">
        <div class="col-6">
            <div class="cardi">
                <div class="Alisa">
                    <h2>3 pengunjung</h2>
                </div>
            </div>
        </div>
        <div class="col-6">
            <div class="Alisa1">
                <h2>180 Buku</h2>
            </div>
        </div>
    </div>
</div>
<div class="line">
    <statistik/>
</div>
</template>

<script setup>
const supabase = useSupabaseClient()
const jml_pengunjung = ref(0)
const jml_buku = ref(0)

async function getjml_pengunjung(params) {
  const{ error, data, count} = await supabase
  .from("pengunjung")
  .select('*', { count: 'exact'})
  if (count) jml_pengunjung.value = count
}
async function getjml_buku() {
  const{ error, data, count} = await supabase
  .from("Buku")
  .select('*', { count: 'exact'})
  if (count) jml_buku.value = count
}

onMounted(() => {
  getjml_pengunjung()
  getjml_buku()
})
</script>
  

<style scoped>
.v2{
    height: 3px;
    width: 98%;
    margin-left: 30px;
    border-left: 3px solid black;
    background-color: black;
}
.v1 {
    margin-top: 40px;
    margin-left: 30px;
    border-left: 3px solid black;
    height: 400px;
}
.card {
    height: 250px;
    box-shadow: 1px 1px 10px #424242;
}
.card.bg-pengunjung {
    background-image: url('../assets/img/kunjungan.png');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
.card.bg-buku {
    background: url('../assets/img/buku.png');
    background-size: cover;
}
.Alisa {
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #E4CA6B;
}
.Alisa1 {
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #1DDD81
}
</style>