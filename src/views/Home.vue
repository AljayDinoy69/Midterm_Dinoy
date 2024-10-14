<template>
  <div class="home">
    <div class="overlay">
      <h1>Welcome to the Product Manager</h1>
      <p>Aljay Dinoy - Midterm Exam</p>
    </div>
    <img src="/wall.jpg" alt="Background" />
  </div>
</template>

<script>
export default {
  name: 'Home',
};
</script>

<style>
.home {
  position: relative;
  text-align: center;
  color: white;
}

img {
  width: 100%;
  height: auto;
  filter: brightness(60%);
}

.overlay {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1;
}

h1 {
  font-size: 3rem;
  margin: 0;
  text-shadow: 2px 2px 4px rgb(255, 255, 255);
}

p {
  font-size: 1.5rem;
  margin-top: 1rem;
  text-shadow: 1px 1px 3px rgba(255, 255, 255, 0.7);
}

@media (max-width: 768px) {
  h1 {
    font-size: 2.5rem;
  }
  
  p {
    font-size: 1.2rem;
  }
}
</style>
