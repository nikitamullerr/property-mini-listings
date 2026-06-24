<script>
import PropertyCard from './components/PropertyCard.vue'

export default {

  // Register reusable components
  components: {
    PropertyCard
  },

  data() {
    return {

      // Property listing data used to display cards
      properties: [
        {
          id: 1,
          title: 'Luxury Beach Apartment',
          location: 'Cape Town',
          price: 2500,
          type: 'Apartment',
          available: true,
          image: 'https://i.ibb.co/8Lj0BrFk/luxury-beach-apartment.jpg'
        },
        
{
  id: 2,
  title: "Ocean View Villa",
  location: "Camps Bay",
  price: 38000,
  type: "Villa",
  available: false,
  image: 'https://i.ibb.co/mrCTMvFK/luxury-villa.jpg'
},
{
  id: 3,
  title: "Modern Studio",
  location: "Woodstock",
  price: 8500,
  type: "Studio",
  available: true,
  image: "https://i.ibb.co/nqZCXwMG/modern-villa.jpg"
},
{
  id: 4,
  title: "Family Townhouse",
  location: "Claremont",
  price: 18500,
  type: "Townhouse",
  available: true,
  image: "https://i.ibb.co/zyyhTdY/townhouse.jpg"
},
{
  id: 5,
  title: "Waterfront Penthouse",
  location: "V&A Waterfront",
  price: 55000,
  type: "Penthouse",
  available: false,
  image: "https://i.ibb.co/mCZJPGM3/wtaerfront-pent.jpg"
},
{
  id: 6,
  title: "Garden Cottage",
  location: "Constantia",
  price: 12000,
  type: "Cottage",
  available: true,
  image: "https://i.ibb.co/4nrJDvpC/garden-cot.jpg"
},
{
  id: 7,
  title: "Student Apartment",
  location: "Rondebosch",
  price: 9500,
  type: "Apartment",
  available: true,
  image: "https://i.ibb.co/N2nBZ6z3/student-apartment.jpg"
},
{
  id: 8,
  title: "Executive Loft",
  location: "City Bowl",
  price: 22000,
  type: "Loft",
  available: true,
  image: "https://i.ibb.co/XkrMV2R3/executive-loft.jpg"
},
{
  id: 9,
  title: "Mountain View Home",
  location: "Newlands",
  price: 27500,
  type: "House",
  available: true,
  image: "https://i.ibb.co/HLTPNj1K/mount-view.jpg"
},
{
  id: 10,
  title: "Luxury Estate Villa",
  location: "Bishopscourt",
  price: 68000,
  type: "Villa",
  available: false,
  image: "https://i.ibb.co/0j14Yf7V/luxury-estate.jpg"
}
      ],

      // Stores text entered into the search box
      searchQuery: '',

      // Stores selected sort option
      sortOrder: 'low-high'
    }
  },

  computed: {

    // Automatically filters and sorts properties
    filteredProperties() {

      // Filter properties by title or location
      let filtered = this.properties.filter(property =>
        property.title.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
        property.location.toLowerCase().includes(this.searchQuery.toLowerCase())
      )

      // Sort prices from lowest to highest
      if (this.sortOrder === 'low-high') {
        filtered.sort((a, b) => a.price - b.price)
      }

      // Sort prices from highest to lowest
      if (this.sortOrder === 'high-low') {
        filtered.sort((a, b) => b.price - a.price)
      }

      return filtered
    }
  }
}
</script>

<template>

  <div class="container">

    <!-- Application Header -->
    <header>
  <h1> Homes & Beyond</h1>

  <p>
    Discover premium rental properties across Cape Town
  </p>

  <div class="count">
    {{ filteredProperties.length }} Properties Available
  </div>
</header>

    <!-- Search properties by title or location -->
    <input
      v-model="searchQuery"
      type="text"
      placeholder="Search by title or location..."
    >

    <!-- Sort properties by price -->
    <select v-model="sortOrder">
      <option value="low-high">Price: Low to High</option>
      <option value="high-low">Price: High to Low</option>
    </select>

    <!-- Display property cards -->
    <div class="property-grid">

      <!-- Loop through filtered properties -->
      <PropertyCard
        v-for="property in filteredProperties"
        :key="property.id"
        :property="property"
      />

    </div>

  </div>

</template>

<style>

/* Page background */
/* Page */
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f4f4;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: auto;
  padding: 20px;
}

/* Header */
header {
  background: linear-gradient(135deg, #1e3c72, #2a5298);
  color: white;
  text-align: center;
  padding: 40px 20px;
  border-radius: 16px;
  margin-bottom: 30px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
}

header h1 {
  margin: 0;
  font-size: 3rem;
}

header p {
  margin-top: 10px;
  font-size: 1.1rem;
}

.count {
  display: inline-block;
  margin-top: 15px;
  background: rgba(255,255,255,0.2);
  padding: 8px 16px;
  border-radius: 20px;
  font-weight: bold;
}

/* Search */
input {
  width: 100%;
  padding: 14px;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  margin-bottom: 15px;
  box-sizing: border-box;
}

/* Sort */
select {
  padding: 12px;
  border: none;
  border-radius: 10px;
  margin-bottom: 25px;
  cursor: pointer;
}

/* Property Grid */
.property-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 25px;
}
</style>