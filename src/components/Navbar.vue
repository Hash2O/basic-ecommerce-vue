<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <header class="relative bg-white">
    <p
      class="flex h-10 items-center justify-center bg-emerald-600 px-4 text-sm font-medium text-white sm:px-6 lg:px-8"
    >
      Get free delivery on orders over $100
    </p>
    <nav aria-label="Top" class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="border-b border-gray-200">
        <div class="flex h-16 items-center">
          <!-- Mobile menu toggle, controls the 'mobileMenuOpen' state. -->
          <button type="button" class="relative rounded-md bg-white p-2 text-gray-400 lg:hidden">
            <span class="absolute -inset-0.5"></span>
            <span class="sr-only">Open menu</span>
            <svg
              class="h-6 w-6"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              aria-hidden="true"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
              />
            </svg>
          </button>

          <!-- Logo -->
          <div class="ml-4 flex lg:ml-0">
            <a href="#">
              <span class="sr-only">Your Company</span>
              <div class="h-8 w-auto">🍍</div>
            </a>
          </div>

          <!-- Flyout menus -->
          <div class="hidden lg:ml-8 lg:block lg:self-stretch">
            <div class="flex h-full space-x-8">
              <div class="flex">
                <div class="relative flex">
                  <!-- Item active: "border-emerald-600 text-emerald-600", Item inactive: "border-transparent text-gray-700 hover:text-gray-800" -->
                  <button
                    type="button"
                    class="relative z-10 -mb-px flex items-center border-b-2 pt-px text-sm font-medium"
                  >
                    Clothes
                  </button>
                </div>
              </div>
              <div class="flex">
                <div class="relative flex">
                  <!-- Item active: "", Item inactive: "border-transparent text-gray-700 hover:text-gray-800" -->
                  <button
                    type="button"
                    class="relative z-10 -mb-px flex items-center border-b-2 border-emerald-600 text-emerald-600 pt-px text-sm font-medium transition-colors duration-200 ease-out hover:text-gray-800"
                    aria-expanded="false"
                  >
                    Beauty
                  </button>
                </div>

                <!--
                                'Men' flyout menu, show/hide based on flyout menu state.
                                
                                Entering: "transition ease-out duration-200"
                                From: "opacity-0"
                                To: "opacity-100"
                                Leaving: "transition ease-in duration-150"
                                From: "opacity-100"
                                To: "opacity-0"
                                -->
                <div class="absolute inset-x-0 top-full text-sm text-gray-500">
                  <!-- Presentational element used to render the bottom shadow, if we put the shadow on the actual panel it pokes out the top, so we use this shorter element to hide the top of the shadow -->
                  <div class="absolute inset-0 top-1/2 bg-white shadow" aria-hidden="true"></div>

                  <div class="relative bg-white">
                    <div class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8">
                      <div
                        class="mt-6 grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8"
                      >
                        <template v-for="product in products" :key="product.id">
                          <ProductView :item="product" />
                        </template>

                        <!-- More products... -->
                      </div>
                      <!--  -->
                    </div>
                  </div>
                </div>
              </div>

              <a
                href="#"
                class="flex items-center text-sm font-medium text-gray-700 hover:text-gray-800"
                >Jewels</a
              >
              <a
                href="#"
                class="flex items-center text-sm font-medium text-gray-700 hover:text-gray-800"
                >Bags</a
              >
            </div>
          </div>

          <div class="ml-auto flex items-center">
            <div class="hidden lg:flex lg:flex-1 lg:items-center lg:justify-end lg:space-x-6">
              <a href="#" class="text-sm font-medium text-gray-700 hover:text-gray-800">Sign in</a>
              <span class="h-6 w-px bg-gray-200" aria-hidden="true"></span>
              <a href="#" class="text-sm font-medium text-gray-700 hover:text-gray-800"
                >Create account</a
              >
            </div>

            <div class="hidden lg:ml-8 lg:flex">
              <!-- <a href="#" class="flex items-center text-gray-700 hover:text-gray-800">
                                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Flag_of_Canada.svg/2560px-Flag_of_Canada.svg.png" alt="" class="block h-auto w-5 flex-shrink-0">
                                <span class="ml-3 block text-sm font-medium">CAD</span>
                                <span class="sr-only">, change currency</span>
                            </a> -->
              <form>
                <select v-model="langSelected" id="lang">
                  <option>😆 | CAD</option>
                  <option>😁 | US</option>
                  <option>😃 | EU</option>
                </select>
              </form>
            </div>

            <!-- Search -->
            <div class="flex lg:ml-6">
              <a href="#" class="p-2 text-gray-400 hover:text-gray-500">
                <span class="sr-only">Search</span>
                <svg
                  class="h-6 w-6"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  aria-hidden="true"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
                  />
                </svg>
              </a>
            </div>

            <!-- Cart -->
            <div @click="showCart = true" class="ml-4 flow-root lg:ml-6">
              <a href="#" class="group -m-2 flex items-center p-2">
                <svg
                  class="h-6 w-6 flex-shrink-0 text-gray-400 group-hover:text-gray-500"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  aria-hidden="true"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M15.75 10.5V6a3.75 3.75 0 10-7.5 0v4.5m11.356-1.993l1.263 12c.07.665-.45 1.243-1.119 1.243H4.25a1.125 1.125 0 01-1.12-1.243l1.264-12A1.125 1.125 0 015.513 7.5h12.974c.576 0 1.059.435 1.119 1.007zM8.625 10.5a.375.375 0 11-.75 0 .375.375 0 01.75 0zm7.5 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z"
                  />
                </svg>

                <span class="ml-2 text-sm font-medium text-gray-700 group-hover:text-gray-800">{{
                  cart.count
                }}</span>

                <span class="sr-only">items in cart, view bag</span>
              </a>
            </div>

            <CartList @close="showCart = false" :show="showCart" />
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import { useCartStore } from '@/utils/useCartStore'
import ProductView from './ProductView.vue'
import CartList from './CartList.vue'

const cart = useCartStore()

const showCart = ref(false)

const products = [
  {
    id: 1,
    name: 'Essence Mascara Lash Princess',
    description:
      'The Essence Mascara Lash Princess is a popular mascara known for its volumizing and lengthening effects.',
    price: 9.99,
    image:
      'https://cdn.dummyjson.com/products/images/beauty/Essence%20Mascara%20Lash%20Princess/1.png',
    qty: 1,
  },
  {
    id: 2,
    name: 'Eyeshadow Palette with Mirror',
    description:
      'The Eyeshadow Palette with Mirror offers a versatile range of eyeshadow shades for creating stunning eye looks.',
    price: 19.99,
    image:
      'https://cdn.dummyjson.com/products/images/beauty/Eyeshadow%20Palette%20with%20Mirror/1.png',
    qty: 1,
  },
  {
    id: 3,
    name: 'Powder Canister',
    description:
      'The Powder Canister is a finely milled setting powder designed to set makeup and control shine.',
    price: 14.99,
    image: 'https://cdn.dummyjson.com/products/images/beauty/Powder%20Canister/1.png',
    qty: 1,
  },
  {
    id: 4,
    name: 'Red Lipstick',
    description:
      'The Red Lipstick is a classic and bold choice for adding a pop of color to your lips.',
    price: 12.99,
    image: 'https://cdn.dummyjson.com/products/images/beauty/Red%20Lipstick/1.png',
    qty: 1,
  },
  {
    id: 5,
    name: 'Red Nail Polish',
    description:
      'The Red Nail Polish offers a rich and glossy red hue for vibrant and polished nails.',
    price: 8.99,
    image: 'https://cdn.dummyjson.com/products/images/beauty/Red%20Nail%20Polish/1.png',
    qty: 1,
  },
  {
    id: 6,
    name: 'Calvin Klein CK One',
    description:
      'CK One by Calvin Klein is a classic unisex fragrance, known for its fresh and clean scent.',
    price: 49.99,
    image: 'https://cdn.dummyjson.com/products/images/fragrances/Calvin%20Klein%20CK%20One/1.png',
    qty: 1,
  },
  {
    id: 7,
    name: 'Chanel Coco Noir Eau De Parfum',
    description:
      'Coco Noir by Chanel is an elegant and mysterious fragrance, featuring notes of grapefruit, rose, and sandalwood.',
    price: 129.99,
    image:
      'https://cdn.dummyjson.com/products/images/fragrances/Chanel%20Coco%20Noir%20Eau%20De/1.png',
    qty: 1,
  },
  {
    id: 8,
    name: "Dior J'adore",
    description:
      "J'adore by Dior is a luxurious and floral fragrance, known for its blend of ylang-ylang, rose, and jasmine.",
    price: 89.99,
    image: "https://cdn.dummyjson.com/products/images/fragrances/Dior%20J'adore/1.png",
    qty: 1,
  },
]
</script>
