<template>
  <section class="pt-24 md:px-20 px-4 min-h-screen" id="products">
    <div>
      <h2 class="text-2xl font-semibold">Kasir</h2>
      <p class="text-gray-700">
        Masukkan total harga dan hitung diskonnya!
      </p>
    </div>
    <div class="mt-10">
      <div class="mb-5">
        <p class="mb-1"><label for="barang">Total Harga</label></p>
        <input type="text" v-model="total" class="px-3 py-1 rounded outline-none border focus:border focus:border-blue-500 transition-all ease w-1/3 max-md:w-full" required>
      </div>
      <div>
        <button class="py-2 px-4 bg-blue-500 hover:text-blue-500 text-white hover:border hover:border-blue-500 hover:bg-transparent transition-all ease" @click="hitung()">Klik untuk hitung diskon</button>
      </div>
    </div>
    <div v-if="total > 0" class="mt-8">
      <div class="md:w-[18rem] w-full flex justify-between">
        <p class="text-xl font-semibold mb-2">Total</p>
        <p class="text-xl font-mono text-gray-700 font-semibold">Rp. {{total}}</p>
      </div>
      <div v-if="diskon > 0" class="md:w-[18rem] w-full flex justify-between">
        <p class="text-md mb-2">Diskon {{diskon}}%</p>
        <p class="text-lg font-mono text-gray-700">Rp. {{total * diskon / 100}}</p>
      </div>
      <br>
      <hr>
      <br>
      <div v-if="diskon > 0" class="md:w-[18rem] w-full flex justify-between items-center">
        <p class="text-md mb-2">Total - Diskon</p>
        <p class="text-2xl font-mono text-gray-700 font-semibold">Rp. {{jumlah}}</p>
      </div>
      <div v-if="diskon == 0" class="md:w-[18rem] w-full flex justify-between">
        <p class="text-md mb-2">Tidak ada diskon</p>
      </div>
    </div>
    <div v-if="total < 0" class="mt-8">
      <p>Masukkan data dengan benar!</p>
    </div>
  </section>
</template>



<script>
  export default {
    data () {
      return {
        total: 0,
        diskon: 0,
        jumlah: 0
      }
    },
    methods: {
      hitung() {
        this.total = this.total
        if (this.total >= 100000) {
          this.diskon = 10
          this.jumlah = this.total - (this.total * this.diskon / 100)
        } else if (this.total >= 50000 && this.total < 100000) {
          this.diskon = 10
          this.jumlah = this.total - (this.total * this.diskon / 100)
        } else {
          this.diskon = 0
          this.jumlah = this.total - (this.total * this.diskon / 100)
        }
      }
    }
  }
</script>








<!-- <script>
  export default {
    data () {
      return {
        barang: "",
        jumlah: 0,
        harga: 0,
        dataBarang: [],
        storage: JSON.parse(localStorage.getItem("barang")) || []
      }
    },
    methods: {
      // add() {
      //   const data = {nama: this.barang, jumlah: this.jumlah, harga: this.harga}
      //   this.storage.push(data)
      //   localStorage.setItem("barang", JSON.stringify(this.storage))
      //   console.log(this.storage)
      //   alert("Berhasil menambahkan data!")
      // },
      // remove() {
      //   localStorage.removeItem("barang")
      //   alert("Berhasil menghapus semua data!")
      // }
    }
  }
</script> -->