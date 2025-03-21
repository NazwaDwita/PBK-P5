<script>
import { ref, computed, watch, onMounted } from 'vue';

export default {
  setup() {
    // LIST RENDERING
    const buah = ref(['Durian', 'PIsang', 'Nangka']);

    // COMPUTED PROPERTIES
    const firstName = ref('Nazwa');
    const lastName = ref('Dwita');
    const fullName = computed(() => `${firstName.value} ${lastName.value}`);

    // WATCHERS
    const name = ref('Nazwa');
    watch(name, (newValue, oldValue) => {
      console.log(`Nama berubah dari ${oldValue} ke ${newValue}`);
    });

    // TEMPLATE REF
    const inputRef = ref(null);
    const focusInput = () => {
      inputRef.value.focus();
    };

    // LIFECYCLE HOOKS
    const message = ref('');
    onMounted(() => {
      message.value = 'Komponen sudah dimuat!';
    });

    return { 
      buah, 
      fullName, 
      name, 
      inputRef, 
      focusInput, 
      message 
    };
  }
};
</script>

<template>
  <div>
    <!-- LIST RENDERING -->
    <h2>Daftar Buah</h2>
    <ul>
      <li v-for="(item, index) in buah" :key="index">
        {{ item }}
      </li>
    </ul>

    <!-- COMPUTED PROPERTIES -->
    <h2>Nama Lengkap</h2>
    <p>{{ fullName }}</p>

    <!-- WATCHERS -->
    <h2>Watcher Demo</h2>
    <p>Nama: {{ name }}</p>
    <input v-model="name" placeholder="Ubah nama..." />

    <!-- TEMPLATE REF -->
    <h2>Template Ref - Fokus ke Input</h2>
    <input ref="inputRef" type="text" placeholder="Ketik sesuatu..." />
    <button @click="focusInput">Fokus ke Input</button>

    <!-- LIFECYCLE HOOKS -->
    <h2>Lifecycle Hook - onMounted</h2>
    <p>{{ message }}</p>
  </div>
</template>

<style>
h2 {
  color: #ffffff;
  margin-top: 20px;
}
button {
  margin-top: 10px;
  padding: 5px 10px;
  cursor: pointer;
}
</style>

