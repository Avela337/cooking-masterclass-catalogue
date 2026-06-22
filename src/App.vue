<script setup>
import { ref, computed } from 'vue'
import AppHeader from './components/AppHeader.vue'
import CourseCard from './components/CourseCard.vue'


const courses = ref([
  { id: 1, title: 'Mastering French Pastries', chef: 'Jean-Luc Picard', price: 850, level: 'Advanced', isAvailable: true },
  { id: 2, title: 'Artisanal Sourdough Baking', chef: 'Sarah Jenkins', price: 450, level: 'Beginner', isAvailable: true },
  { id: 3, title: 'Sushi Roll Perfection', chef: 'Kenji Tanaka', price: 600, level: 'Intermediate', isAvailable: false },
  { id: 4, title: 'Thai Street Food Classics', chef: 'Noi Srisai', price: 500, level: 'Beginner', isAvailable: true }
])


const wishlist = ref([])


const wishlistCount = computed(() => wishlist.value.length)


const toggleWishlist = (courseId) => {
  if (wishlist.value.includes(courseId)) {
    
    wishlist.value = wishlist.value.filter(id => id !== courseId)
  } else {
    
    wishlist.value.push(courseId)
  }
}
</script>

<template>
  <div class="app-container">
    
    <AppHeader :count="wishlistCount" />
    
    <main class="catalogue-grid">
      
      <CourseCard 
        v-for="course in courses" 
        :key="course.id" 
        :course="course"
        :isSaved="wishlist.includes(course.id)"
        @toggle-save="toggleWishlist"
      />
    </main>
  </div>
</template>

<style scoped>
.app-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}
.catalogue-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 20px;
  margin-top: 30px;
}
</style>
