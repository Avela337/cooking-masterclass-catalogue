<script setup>

defineProps({
  count: {
    type: Number,
    required: true
  }
})
</script>

<template>
  <header class="main-header">
    <h1 class="logo">🍳 Cooking Masterclass</h1>
    <div class="wishlist-badge">
      Saved Sessions: <span class="badge-number">{{ count }}</span>
    </div>
  </header>
</template>

<style scoped>
.main-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 0;
  border-bottom: 2px solid #eaeaea;
}
.wishlist-badge {
  font-weight: bold;
  background-color: #f0f0f0;
  padding: 8px 15px;
  border-radius: 20px;
}
.badge-number {
  color: #ff4757;
}
</style>
