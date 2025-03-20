<script setup>
import { useForm } from '@inertiajs/vue3';
import TextInput from '@/Pages/Components/TextInput.vue';

const form = useForm({
  email: null,
  password: null,
  remember: null,
});

const submit = () => {
  form.post(route("login"), {
    onError: () => form.reset("password"),
  });
};
</script>

<template>
  <Head title="Login" />

  <h1 class="my-6 text-center text-3xl font-bold leading-9 text-slate-900">Login to your account</h1>

  <div class="w-2/4 mx-auto">
    <form @submit.prevent="submit">
      <TextInput 
        name='email' 
        type='email' 
        v-model='form.email' 
        :message="form.errors.email"
      />

      <TextInput 
        name='password' 
        type='password'
        v-model='form.password' 
        :message="form.errors.password"
      />

      <div class="flex items-center gap-2">
        <label>Remember me</label>
        <input type="checkbox" v-model="form.remember">
        <p class="text-slate-600 mb-2">
          Need an account? <a :href="route('register')" class="font-semibold text-blue-500 hover:text-blue-600">Register</a>
        </p>
      </div>

      <div>
        <button class="flex w-full justify-center rounded-md bg-blue-500 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-blue-600 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:bg-slate-400 disabled:cursor-wait" :disabled="form.processing">Login</button>
      </div>
    </form>
  </div>
</template>