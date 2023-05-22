<template>
  <section class="min-h-screen flex md:p-20 max-md:px-5 max-md:py-20 flex-wrap">
    <div>
      <p class="font-semibold font-serif text-xl">Total Barang di Keranjang!</p>
      <div class="mt-5">
        <div v-for="product in products" class="md:w-[18rem] w-full flex justify-between" :key="product.id">
          <div class="flex gap-x-2 items-center">
              <span>1x</span>
              <p class="text-md">{{product.name}}</p>
          </div>
          <p class="text-lg font-mono text-gray-700">Rp. {{product.price}}</p>
        </div>
      </div>
      <div class="text-black flex justify-between mt-8">
        <p class="text-lg font-semibold">Total</p>
        <p class="text-xl font-mono text-gray-700">Rp. {{total}}</p>
      </div>
      <div v-if="diskon != 0 && totalDiskon != 0" class="text-black flex justify-between mt-2">
          <p class="text-grey-800">Discount {{diskon}}%</p>
          <p class="text-xl font-mono text-gray-700">Rp. {{total * diskon / 100}}</p>
      </div>
      <br>
      <hr>
      <br>
      <div v-if="diskon != 0 && totalDiskon != 0" class="text-black flex justify-between mt-2">
          <p class="text-grey-800">Total + Discount {{diskon}}%</p>
          <p class="text-xl font-mono text-gray-700">Rp. {{totalDiskon}}</p>
      </div>
      <div class="mt-14">
        <button class="py-2 px-4 hover:bg-orange-500 hover:text-white bg-transparent border border-orange-500 text-orange-500 transition-all ease" @click="hapusData()">Hapus Data Keranjang</button>
      </div>
    </div>
  </section>
</template>

<script setup>
  const products = JSON.parse(localStorage.getItem("data")) || []
  console.log(products)
  let total = 0;
  let diskon = 0
  let totalDiskon = 0
  total = products.map(item => item.price)
                    .reduce((total, price) => total + price, 0);
  if (total >= 100000) {
    diskon = 10
    totalDiskon = total - (total * diskon / 100)
  } else if (total >= 50000) {
    diskon = 5
    totalDiskon = total - (total * diskon / 100)
  } else {
    diskon = 0
  }

  function hapusData() {
    localStorage.removeItem("data")
    alert("Remove data success!")
    window.location.href = "/"
  }

</script>
