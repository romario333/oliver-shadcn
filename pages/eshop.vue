<template>
  <div class="flex flex-col gap-4 w-xl">
    <div v-for="(product, index) in products" :key="product.id">
      <NuxtLink :to="`/products/${product.id}`">
        <div
          class="flex items-center gap-2 p-4 hover:bg-gray-100 transition-colors"
        >
          <Avatar>
            <AvatarImage
              :src="`https://picsum.photos/200/300?random=${product.id}`"
            />
            <AvatarFallback>{{ index + 1 }}</AvatarFallback>
          </Avatar>
          <div>{{ product.name }}</div>
        </div>
      </NuxtLink>
      <Separator v-if="index !== products.length - 1" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { useProducts, type Product } from "../composables/products";

definePageMeta({
  pageTransition: {
    mode: "out-in",
  },
});

const { fetchProducts } = useProducts();

const products = ref<Product[]>([]);

products.value = await fetchProducts();
</script>
