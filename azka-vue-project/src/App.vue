<template>
  <div id="app">
    <div class="container">
      <h1 class="title">Azka Vue App</h1>

      <!-- Click Counter -->
      <section class="card">
        <h2>Click Counter</h2>
        <p class="counter-display">Clicked {{ counter }} times</p>
        <button class="btn" @click="incrementCounter">Click Me</button>
      </section>

      <!-- Box Color Changer -->
      <section class="card">
        <h2>Box Color Changer</h2>
        <div :style="boxStyle" class="color-box"></div>
        <button class="btn" @click="changeColor">Change Color</button>
      </section>

      <!-- Image Carousel -->
      <section class="card">
        <h2>Image Carousel</h2>
        <div class="carousel">
          <img :src="images[currentImage]" alt="Carousel Image" class="carousel-image" />
        </div>
        <div class="carousel-controls">
          <button class="btn" @click="prevImage">Previous</button>
          <button class="btn" @click="nextImage">Next</button>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Click counter state
      counter: 0,

      // Box color changer state
      colors: ["#FF6F61", "#6B5B95", "#88B04B", "#F7CAC9", "#92A8D1"],
      currentColorIndex: 0,

      // Image carousel state
      images: [
        "https://cdn.pixabay.com/photo/2023/09/12/04/46/bird-8247917_1280.jpg",
        "https://cdn.pixabay.com/photo/2016/06/30/20/39/horse-1489825_1280.jpg",
        "https://cdn.pixabay.com/photo/2023/07/21/16/23/cat-8141916_960_720.jpg"
      ],
      currentImage: 0,
    };
  },
  computed: {
    boxStyle() {
      return {
        backgroundColor: this.colors[this.currentColorIndex],
        width: "200px",
        height: "200px",
        borderRadius: "12px",
        margin: "20px auto",
        boxShadow: "0 4px 8px rgba(0, 0, 0, 0.1)"
      };
    }
  },
  methods: {
    // Click counter method
    incrementCounter() {
      this.counter++;
    },

    // Box color changer method
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },

    // Image carousel methods
    prevImage() {
      this.currentImage =
        this.currentImage === 0
          ? this.images.length - 1
          : this.currentImage - 1;
    },
    nextImage() {
      this.currentImage =
        this.currentImage === this.images.length - 1
          ? 0
          : this.currentImage + 1;
    }
  }
};
</script>

<style scoped>
#app {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f0f0f0;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  width: 90%;
  max-width: 800px;
  background-color: #fff;
  border-radius: 16px;
  padding: 30px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.title {
  text-align: center;
  color: #333;
  font-size: 2.5em;
  margin-bottom: 30px;
}

.card {
  margin-bottom: 40px;
  text-align: center;
}

.counter-display {
  font-size: 1.5em;
  color: #666;
  margin-bottom: 10px;
}

.color-box {
  transition: background-color 0.3s ease;
}

.carousel {
  width: 500px;
  height: 400px;
  margin: 20px auto;
  overflow: hidden;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.carousel-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 0.5s ease;
}

.carousel-controls {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

.btn {
  background-color: #FF6F61;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 8px;
  font-size: 1em;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #ff4a3d;
}
</style>
