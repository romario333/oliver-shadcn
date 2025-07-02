<script setup lang="ts">
import { Home, ShoppingBag } from "lucide-vue-next";

import {
  Sidebar,
  SidebarContent,
  SidebarFooter,
  SidebarGroup,
  SidebarHeader,
} from "@/components/ui/sidebar";

const isActive = (path: string) => {
  return useRoute().path === path;
};
</script>

<template>
  <Sidebar>
    <SidebarContent class="pt-16">
      <SidebarGroup>
        <SidebarMenu>
          <SidebarMenuItem>
            <SidebarMenuButton asChild :isActive="isActive('/')">
              <NuxtLink to="/">
                <Home />
                <span>Home</span>
              </NuxtLink>
            </SidebarMenuButton>
          </SidebarMenuItem>
          <SidebarMenuItem>
            <SidebarMenuButton asChild :isActive="isActive('/eshop')">
              <NuxtLink to="/eshop">
                <ShoppingBag />
                <span>Eshop</span>
              </NuxtLink>
            </SidebarMenuButton>
          </SidebarMenuItem>
        </SidebarMenu>
      </SidebarGroup>
    </SidebarContent>
  </Sidebar>
</template>
