<template>
  <form class="box" @submit.prevent="handleLogin">
    <div class="field">
      <label class="label">Email</label>
      <div class="control">
        <input 
          class="input" 
          type="email" 
          placeholder="Введите e-mail" 
          v-model="email"
        />
      </div>
    </div>

    <div class="field">
      <label class="label">Password</label>
      <div class="control">
        <input 
          class="input" 
          type="password" 
          placeholder="Введите пароль" 
          v-model="password"
        />
      </div>
    </div>

    <button 
      class="button is-primary"
      type="submit" 
      :disabled="loading"
    >Войти</button>
  </form>
</template>

<script setup>
const supabase = useSupabaseClient();

const loading = ref(false);
const email = ref("");
const password = ref("");

const handleLogin = async () => {
  try {
    loading.value = true;
    const { error } = await supabase.auth.signInWithPassword({ email: email.value, password: password.value });
    if (error) throw error;
  } catch (error) {
    alert(error.error_description || error.message);
  } finally {
    loading.value = false;
  }
};
</script>
