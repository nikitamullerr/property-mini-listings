<script setup>

// Receive property data from App.vue using props
defineProps({
  property: Object
})

</script>

<template>

  <!-- Individual property card -->
  <div class="property-card">

    <!-- Property image -->
    <img
      :src="property.image"
      :alt="property.title"
    >

    <!-- Show badge when property is unavailable -->
    <span
      v-if="!property.available"
      class="badge"
    >
      Not Available
    </span>

    <!-- Property information -->
    <div class="card-content">

      <h3>{{ property.title }}</h3>

      <p> {{ property.location }}</p>

      <p> {{ property.type }}</p>

      <p class="price">
        R{{ property.price }}
      </p>

    </div>

  </div>

</template>

<style scoped>

/* Individual property card */
.property-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0,0,0,.1);
  transition: 0.3s;
  position: relative;
}

/* Card hover animation */
.property-card:hover {
  transform: translateY(-5px);
}

/* Property image */
.property-card img {
  width: 100%;
  height: 220px;
  object-fit: cover;
  display: block;
}

/* Card content */
.card-content {
  padding: 15px;
}

.card-content h3 {
  margin-bottom: 10px;
}

.card-content p {
  margin: 8px 0;
}

/* Price styling */
.price {
  color: #2e7d32;
  font-weight: bold;
}

/* Not available badge */
.badge {
  position: absolute;
  top: 10px;
  right: 10px;
  background: crimson;
  color: white;
  padding: 6px 12px;
  border-radius: 20px;
}

</style>