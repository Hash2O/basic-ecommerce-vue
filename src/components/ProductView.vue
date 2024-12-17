<template>
  <div class="group relative">
    <div
      class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-md bg-gray-200 lg:aspect-none group-hover:opacity-75 lg:h-80"
    >
      <img
        v-bind:src="item.image"
        alt=""
        class="h-full w-full object-cover object-center lg:h-full lg:w-full"
      />
      <!-- https://cdn.dummyjson.com/products/images/beauty/Essence%20Mascara%20Lash%20Princess/1.png -->
    </div>
    <div class="mt-4 flex justify-between">
      <div>
        <h3 class="text-sm text-gray-700">
          <a @click.prevent="cart.add(item)" href="#">
            <span aria-hidden="true" class="absolute inset-0"></span>
            {{ item.name }}
          </a>
        </h3>
        <p class="mt-1 text-sm text-gray-500">{{ item.description }}</p>
      </div>
      <p class="text-sm font-medium text-gray-900">{{ item.price }}€</p>
    </div>
  </div>
</template>

<script setup>
import { useCartStore } from '@/utils/useCartStore.js'

const cart = useCartStore()

defineProps({
  item: [
    {
      id: Number,
      name: String,
      description: String,
      price: Number,
      image: String,
      qty: Number,
    },
  ],
})
</script>
