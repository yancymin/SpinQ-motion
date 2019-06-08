<template>
  <div class="hero">
    <div class="wrapper">
      <div class="container">
        <div class="sphere">
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
        </div>
        <div class="sphere">
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
          <div class="ring"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="scss">
body {
  background: #000;
  overflow: hidden;
}

.wrapper {
  perspective: 800px;
  display: flex;
  justify-content: center;
  filter: blur(1.5px);
}

.container {
  transform: rotateX(40deg) rotateY(40deg) rotateZ(90deg);
  transform-style: preserve-3d;
  position: relative;
  display: flex;
  height: 600px;
  width: 600px;
  margin: 100px 0;
}

.sphere,
.ring {
  position: absolute;
  height: 100%;
  width: 100%;
  transform-style: preserve-3d;
}

.sphere {
  animation: rotateSphere 10s linear infinite;
  &:nth-of-type(1) {
    @for $i from 1 through 10 {
      .ring:nth-of-type(#{$i}) {
        transform: rotateY($i * 18deg);
      }
    }
  }
  &:nth-of-type(2) {
    @for $i from 1 through 10 {
      .ring:nth-of-type(#{$i}) {
        transform: rotateX($i * 18deg);
      }
    }
  }
}

$colors: #40E0D0, #4AE2D2, #53E3D5, #5DE5D7, #66E6D9, #70E8DC, #79E9DE, #83EBE0,
  #8CECE3, #96EEE5;

.ring {
  border: 1px solid;
  box-sizing: border-box;
  border-radius: 50%;
  opacity: 0;
  animation: fadeIn 2000ms ease infinite;
  box-shadow: 0 0 80px rgba(#fff, 0.2), inset 0 0 80px rgba(#fff, 0.2);
  @for $i from 1 through 10 {
    &:nth-of-type(#{$i}) {
      border-color: nth($colors, $i);
      animation-delay: $i * 200ms;
    }
  }
}

@keyframes rotateSphere {
  to {
    transform: rotateX(360deg) rotateY(360deg);
  }
}

@keyframes fadeIn {
  from,
  to {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
}
</style>
