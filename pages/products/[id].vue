<template>
  <div>
    <Button variant="outline" class="mb-4" @click="backToEshop">
      <ArrowLeft class="w-4 h-4 mr-2" /> Back to E-shop
    </Button>
    <h1>Product {{ id }}</h1>
  </div>
</template>

<script setup lang="ts">
import { ArrowLeft } from "lucide-vue-next";
import { Button } from "@/components/ui/button";
const router = useRouter();

definePageMeta({
  pageTransition: {
    mode: "out-in",
    name: "slide-right",
  },
});

const { id } = useRoute().params;

const backToEshop = () => {
  router.back();
};
</script>
