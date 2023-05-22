<template>
	<div class="md:w-[20rem] min-h-[25rem] bg-white rounded-lg p-5 flex flex-col justify-between border shadow-lg">
		<div>
	      <p class="font-serif font-semibold text-xl text-black mb-4">Keranjang</p>
			<div v-if="datas.length != 0">
				<div v-for="product in datas" class="text-black flex justify-between mb-2" :key="product.id">
					<div class="flex gap-x-2 items-center">
						<span>1x</span>
						<p class="text-md">{{product.name}}</p>
					</div>
				</div>
				<p class="text-lg font-mono text-gray-700">Rp. {{product.price}}</p>
			</div>
			<div v-else>
				Gada data
			</div>
		</div>
		<div class="text-black flex justify-between mt-4">
			<p class="text-lg font-semibold">Total</p>
			<p class="text-xl font-mono text-gray-700">Rp. 80000</p>
		</div>
	</div>
</template>
<!-- 
<script setup>
	let datas = []
	onMounted(() => {
		setTimeout(() => {
			datas = JSON.parse(localStorage.getItem("data"))
		}, 100)
	})
</script> -->