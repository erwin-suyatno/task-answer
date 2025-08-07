<template>
  <div class="tab-system">
    <div class="tab-header">
      <button 
        v-for="(tab, index) in tabs" 
        :key="index"
        @click="activeTab = index"
        :class="['tab-button', { active: activeTab === index }]"
      >
        {{ tab.title }}
      </button>
    </div>
    <div class="tab-content">
      <slot :name="'tab-' + activeTab"></slot>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Define props untuk menerima array tabs dari parent component
const props = defineProps({
  tabs: {
    type: Array,
    required: true
  },
  initialTab: {
    type: Number,
    default: 0
  }
})

// State untuk tab yang aktif
const activeTab = ref(props.initialTab)
</script>

<style scoped>
.tab-system {
  width: 100%;
  margin: 2rem 0;
}

.tab-header {
  display: flex;
  border-bottom: 2px solid #e2e8f0;
  margin-bottom: 1rem;
}

.tab-button {
  padding: 0.75rem 1.5rem;
  background: none;
  border: none;
  font-size: 1rem;
  font-weight: 500;
  color: #64748b;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
}

.tab-button:hover {
  color: #334155;
}

.tab-button.active {
  color: #3b82f6;
  font-weight: 600;
}

.tab-button.active::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: #3b82f6;
}

.tab-content {
  padding: 1rem 0;
}
</style>
