<script setup>
import { useForm } from '@inertiajs/vue3';

const form = useForm({
  name: null,
  email: null,
  password: null,
  password_confirmation: null,
});

const submit = () => {
  form.post(route("register"), {
    onError: () => form.reset("password", "password_confirmation"),
  });
};

</script>

<template>
  <Head :title="Register" />

  <h1 class="my-6 text-center text-3xl font-bold leading-9 text-slate-900">Register a new account</h1>

  <div class="w-2/4 mx-auto">
    <form @submit.prevent="submit">
      <div class="mb-6">
        <label class="block text-sm font-medium leading-6 text-slate-900 first-letter:capitalize">Name</label>
        <input type="text" v-model="form.name" class="block w-full rounded-md border-0 p-2 text-slate-900 shadow-sm ring-1 ring-inset ring-slate-300 placeholder:text-slate-500 focus:ring-2 focus:ring-inset focus:ring-blue-500 sm:text-sm bg-white"/>
        <small>{{ form.errors.name }}</small>
      </div>

      <div class="mb-6">
        <label class="block text-sm font-medium leading-6 text-slate-900 first-letter:capitalize">Email</label>
        <input type="text" v-model="form.email" class="block w-full rounded-md border-0 p-2 text-slate-900 shadow-sm ring-1 ring-inset ring-slate-300 placeholder:text-slate-500 focus:ring-2 focus:ring-inset focus:ring-blue-500 sm:text-sm bg-white"/>
        <small>{{ form.errors.email }}</small>
      </div>

      <div class="mb-6">
        <label class="block text-sm font-medium leading-6 text-slate-900 first-letter:capitalize">Password</label>
        <input type="password" v-model="form.password" class="block w-full rounded-md border-0 p-2 text-slate-900 shadow-sm ring-1 ring-inset ring-slate-300 placeholder:text-slate-500 focus:ring-2 focus:ring-inset focus:ring-blue-500 sm:text-sm bg-white"/>
        <small>{{ form.errors.password }}</small>
      </div>

      <div class="mb-6">
        <label class="block text-sm font-medium leading-6 text-slate-900 first-letter:capitalize">Confirm Password</label>
        <input type="password" v-model="form.password_confirmation" class="block w-full rounded-md border-0 p-2 text-slate-900 shadow-sm ring-1 ring-inset ring-slate-300 placeholder:text-slate-500 focus:ring-2 focus:ring-inset focus:ring-blue-500 sm:text-sm bg-white"/>
      </div>

      <div>
        <p class="text-slate-600 mb-2">
          Already a user? <a href="#" class="font-semibold text-blue-500 hover:text-blue-600">Login</a>
        </p>
        <button class="flex w-full justify-center rounded-md bg-blue-500 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-blue-600 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:bg-slate-400 disabled:cursor-wait" :disabled="form.processing">Register</button>
      </div>
    </form>
  </div>
</template>