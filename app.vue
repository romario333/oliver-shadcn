<script setup lang="ts">
import { SidebarProvider, SidebarTrigger } from "@/components/ui/sidebar";
import AppSidebar from "@/components/AppSidebar.vue";
import { Toaster } from "@/components/ui/sonner";
// TODO: wtf?
import "vue-sonner/style.css"; // vue-sonner v2 requires this import
</script>

<template>
  <SidebarProvider>
    <AppSidebar />
    <main class="min-h-screen">
      <AppTopBar />
      <Toaster />
      <div class="pt-16 px-4">
        <NuxtPage />
      </div>
    </main>
  </SidebarProvider>
</template>

<style>
/* Slide right transition (eshop → products) */
.slide-right-enter-active,
.slide-right-leave-active {
  transition: all 0.3s ease-in-out;
}

.slide-right-enter-from {
  opacity: 0;
  transform: translateX(100%);
}

.slide-right-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>
