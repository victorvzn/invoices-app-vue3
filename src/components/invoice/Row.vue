<script setup>
import { RouterLink } from 'vue-router'

defineProps({
  data: {
    type: Object,
    default: {}
  }
})
</script>

<template>
  <div
    class="flex duration-300 justify-between items-center px-6 py-4 rounded-lg bg-slate-800 text-slate-400 hover:bg-slate-400/20 dark:bg-white shadow-md">
    <div class="w-32 text-center">
      #<span class="text-white font-semibold dark:text-gray-900">{{ data.code }}</span>
    </div>
    <div class="w-44 text-center">{{data.invoice.date}}</div>
    <div class="w-44">{{data.bill.to.client.name}}</div>
    <div class="w-44 text-center text-2xl text-white font-semibold dark:text-gray-900">
      {{ data.invoice.currency.symbol }}{{ data.invoice.grandTotal }}
    </div>
    <div class="w-44 flex justify-center">
      <div v-if="data.status === 'paid'"
        class="backdrop-blur-xl bg-emerald-400/10 text-emerald-400 text-center w-32 py-3 rounded-md font-bold capitalize">
        ● {{ data.status }}
      </div>
      <div v-else-if="data.status === 'pending'"
        class="backdrop-blur-xl bg-orange-400/10 text-orange-400 text-center w-32 py-3 rounded-md font-bold capitalize">
        ● {{ data.status }}
      </div>
      <div v-else
        class="backdrop-blur-xl bg-slate-400/10 text-white text-center w-32 py-3 rounded-md font-bold capitalize dark:text-gray-900">
        ● {{ data.status }}
      </div>
    </div>
    <router-link :to="`/invoices/${data.id}`">
      <div class="text-violet-500 cursor-pointer p-2 hover:bg-slate-700 rounded-full">
        <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd"
            d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
            clip-rule="evenodd"></path>
        </svg>
      </div>
    </router-link>
  </div>
</template>