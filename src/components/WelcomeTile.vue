<script setup>
    defineProps({
        content: {
            type: String,
            required: true
        }
    })
</script>

<template>
    <div class="welcome">
        <h1 class="green">{{ content }}</h1>
        <h3>Wie funktioniert <strong>$emit()</strong>?</h3>
    </div>
</template>

<style scoped>
  h1.green {
    font-size: 2.6rem;
    font-weight: bold;
    color: #40B883;
    background: linear-gradient(90deg, #34986d 0%, #40B883 100%);
    background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 20px;
    text-align: center;
    letter-spacing: 2px;
  }

  h3 {
    font-size: 1.2rem;
    font-weight: 600;
    color: #f1f1f1;
    margin-bottom: 15px;
    text-align: left;
  }

  h3 strong {
    color: #40B883;
    font-weight: bold;
  }

  h3::before {
    content: "➤ ";
    color: #40B883;
  }

  .welcome h1,
  .welcome h3 {
    text-align: center;
  }

  strong {
      font-weight: bold;
  }

  @media (min-width: 1024px) {
    .welcome h1,
    .welcome h3 {
      text-align: left;
    }
  }
</style>

