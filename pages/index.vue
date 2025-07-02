<template>
  <form @submit="onSubmit">
    <FormField v-slot="{ componentField }" name="firstname">
      <FormItem>
        <FormLabel>First Name</FormLabel>
        <FormControl>
          <Input placeholder="First Name" v-bind="componentField" />
        </FormControl>
        <FormDescription />
        <FormMessage />
      </FormItem>
    </FormField>
    <FormField v-slot="{ componentField }" name="lastname">
      <FormItem>
        <FormLabel>Last Name</FormLabel>
        <FormControl>
          <Input placeholder="Last Name" v-bind="componentField" />
        </FormControl>
        <FormDescription />
        <FormMessage />
      </FormItem>
    </FormField>
    <FormField v-slot="{ componentField }" name="email">
      <FormItem>
        <FormLabel>Email</FormLabel>
        <FormControl>
          <Input placeholder="Email" v-bind="componentField" />
        </FormControl>
        <FormDescription />
        <FormMessage />
      </FormItem>
    </FormField>
    <div class="flex gap-2">
      <Button type="submit" :disabled="submitting"> Submit </Button>
      <Button variant="outline" size="icon" @click="like" :disabled="liking">
        <HeartIcon class="w-4 h-4" />
      </Button>
    </div>

    <h3 class="mt-20">Toasts</h3>
    <div class="flex gap-2">
      <Button
        type="button"
        variant="outline"
        @click="showToast('success')"
        class="mt-4"
        >Success</Button
      >
      <Button
        type="button"
        variant="outline"
        @click="showToast('error')"
        class="mt-4"
        >Error</Button
      >
      <Button
        type="button"
        variant="outline"
        @click="showToast('warning')"
        class="mt-4"
        >Warning</Button
      >
      <Button
        type="button"
        variant="outline"
        @click="showToast('info')"
        class="mt-4"
        >Info</Button
      >
      <Button
        type="button"
        variant="outline"
        @click="showToast('loading')"
        class="mt-4"
        >Loading</Button
      >
    </div>

    <div class="mt-4">
      <AppDatePicker />
    </div>

    <div class="mt-4">(no time picker)</div>

    <pre class="mt-4">{{ JSON.stringify(form.values, null, 2) }}</pre>
  </form>
</template>

<script setup lang="ts">
import { useForm } from "vee-validate";
import { toTypedSchema } from "@vee-validate/zod";
import * as z from "zod";
import { Button } from "@/components/ui/button";
import {
  FormControl,
  FormDescription,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";
import { HeartIcon } from "lucide-vue-next";
import { toast } from "vue-sonner";

const formSchema = toTypedSchema(
  z.object({
    firstname: z.string().min(1, { message: "First name is required." }),
    lastname: z.string().min(1, { message: "Last name is required." }),
    email: z.string().email({ message: "Invalid email address." }),
  })
);

const form = useForm({
  validationSchema: formSchema,
});

const submitting = ref(false);
const liking = ref(false);

const onSubmit = form.handleSubmit(async (values) => {
  submitting.value = true;
  await new Promise((resolve) => setTimeout(resolve, 1000));
  submitting.value = false;
});

async function like() {
  liking.value = true;
  await new Promise((resolve) => setTimeout(resolve, 1000));
  liking.value = false;
}

async function showToast(
  type: "success" | "error" | "warning" | "info" | "loading"
) {
  switch (type) {
    case "success":
      toast.success("This is a success toast");
      break;
    case "error":
      toast.error("This is an error toast");
      break;
    case "warning":
      toast.warning("This is a warning toast");
      break;
    case "info":
      toast.info("This is an info toast");
      break;
    case "loading":
      toast.loading("This is a loading toast");
      break;
  }
}
</script>
