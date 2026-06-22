<script setup>

defineProps({
  course: Object,
  isSaved: Boolean
})


defineEmits(['toggle-save'])
</script>

<template>
  
  <div class="course-card" :class="{ 'sold-out-box': !course.isAvailable }">
    <div class="card-body">
      <span class="level-tag">{{ course.level }}</span>
      <h3>{{ course.title }}</h3>
      <p class="chef-name">Chef: {{ course.chef }}</p>
      <p class="price-tag">R{{ course.price.toFixed(2) }}</p>
    </div>
    
    <div class="card-footer">
      
      <span v-if="!course.isAvailable" class="status-alert">Sold Out</span>
      
      <button 
        v-else 
        @click="$emit('toggle-save', course.id)"
        class="save-btn"
        :class="{ 'saved-active': isSaved }"
      >
        {{ isSaved ? '❤️ Saved' : '🤍 Save to Wishlist' }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.course-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-color: white;
}
.sold-out-box {
  opacity: 0.6;
  background-color: #f9f9f9;
}
.level-tag {
  font-size: 0.75rem;
  background: #341f97;
  color: white;
  padding: 2px 8px;
  border-radius: 4px;
}
.status-alert {
  color: #ff4d4d;
  font-weight: bold;
}
.save-btn {
  width: 100%;
  padding: 8px;
  border: 1px solid #333;
  background: transparent;
  cursor: pointer;
  border-radius: 4px;
}
.saved-active {
  background-color: #ff4757;
  color: white;
  border-color: #ff4757;
}
</style>
