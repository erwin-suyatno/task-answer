<template>
  <div class="hello-world">
    <h2>{{ title }}</h2>
    <p>{{ message }}</p>
    
    <div class="counter-section">
      <button @click="increment" class="counter-btn">
        Clicked {{ count }} times
      </button>
      <button @click="reset" class="reset-btn" v-if="count > 0">
        Reset
      </button>
    </div>

    <div class="props-demo" v-if="showProps">
      <h3>Props Demo</h3>
      <p><strong>Received prop:</strong> {{ receivedProp }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Definisi props menggunakan defineProps (macro khusus untuk script setup)
const props = defineProps({
  title: {
    type: String,
    default: 'Hello World Component'
  },
  receivedProp: {
    type: String,
    default: 'No prop received'
  }
})

// Reactive state
const count = ref(0)
const message = ref('This is a reusable Vue 3 component using Composition API')

// Computed property
const showProps = computed(() => props.receivedProp !== 'No prop received')

// Methods
const increment = () => {
  count.value++
}

const reset = () => {
  count.value = 0
}
</script>

<style scoped>
.hello-world {
  padding: 2rem;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  border-radius: 12px;
  text-align: center;
  margin: 1rem 0;
}

.hello-world h2 {
  color: #2c3e50;
  margin-bottom: 1rem;
}

.hello-world p {
  color: #7f8c8d;
  margin-bottom: 1.5rem;
}

.counter-section {
  display: flex;
  gap: 1rem;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 1.5rem;
}

.counter-btn {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 6px;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.counter-btn:hover {
  background-color: #369870;
  transform: scale(1.05);
}

.reset-btn {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  font-size: 0.9rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.reset-btn:hover {
  background-color: #c0392b;
}

.props-demo {
  background: white;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.props-demo h3 {
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.props-demo p {
  color: #555;
  margin: 0;
}
</style>
