<script setup>
</script>

<template>
  <div>
    <header class="bg-slate-800 shadow-md">
      <nav class="p-5 max-w-screen-lg mx-auto flex items-center justify-between">
        <div class="space-x-6">
          <Link
            :href="route('home')" 
            :class="{ 'bg-slate-700' : $page.component === 'Home' }"
            class="text-slate-200 hover:bg-slate-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">Home
          </Link>
        </div>

        <div v-if="$page.props.auth.user" class="space-x-6">
          <Link :href="route('dashboard')" class="text-slate-200 hover:bg-slate-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">Dashboard</Link>
          <Link :href="route('logout')" method="post" as="button" type="button" class="text-slate-200 hover:bg-slate-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">Logout</Link>
        </div>

        <div v-else class="space-x-6">
          <Link :href="route('register')" class="text-slate-200 hover:bg-slate-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">Register</Link>
          <Link :href="route('login')" class="text-slate-200 hover:bg-slate-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium">Login</Link>
        </div>
      </nav>
    </header>
    <main class="p-4 max-w-screen-lg mx-auto">
      <slot />
    </main>
  </div>
</template>