<template>
  <div class="fixed top-0 left-0 right-0 z-50 bg-background border-b px-4 py-2">
    <div class="flex items-center gap-2">
      <SidebarTrigger />
      <h1 class="text-2xl font-bold">ShadCN Prototype</h1>
      <div class="grow"></div>
      <Button @click="toggleTheme">
        <SunIcon class="size-4" />
      </Button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { SunIcon } from "lucide-vue-next";

const colorMode = useColorMode();

function toggleTheme() {
  colorMode.preference = colorMode.preference === "dark" ? "light" : "dark";
}
</script>
