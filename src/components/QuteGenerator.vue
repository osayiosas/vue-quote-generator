<template>
  <div class="quote-generator">
    <h1 class="app-title">Random Quote Generator</h1>
    <blockquote class="qute-container">
      <p class="quote-text">
        {{ currentQuote.text }}
      </p>
      <cite class="quote-author">
        {{ currentQuote.author }}
      </cite>
    </blockquote>
    <button class="quote-btn" @click="getRandomQuote">Generate Quote</button>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const quote = ref([
  {
    text: 'The greatest glory in living lies not in never falling, but in rising every time we fall.',
    author: 'Nelson Mandela'
  },
  {
    text: 'The way to get started is to quit talking and begin doing.',
    author: 'Walt Disney'
  },
  {
    text: "Your time is limited, so don't waste it living someone else's life.",
    author: 'Steve Jobs'
  },
  {
    text: 'If life were predictable it would cease to be life, and be without flavor.',
    author: 'Eleanor Roosevelt'
  },
  {
    text: "If you set your goals ridiculously high and it's a failure, you will fail above everyone else's success.",
    author: 'James Cameron'
  },
  {
    text: "Life is what happens when you're busy making other plans.",
    author: 'John Lennon'
  }
])

const currentQuote = ref({ text: '', author: '' })

const getRandomQuote = () => {
  const randomIndex = Math.floor(Math.random() * quote.value.length)
  currentQuote.value = quote.value[randomIndex]
}

onMounted(() => {
  getRandomQuote()
})
</script>

<style>
.quote-generator {
  max-width: 400px;
  margin: 200px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
 
}
.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  color: #5a5151;
}
.qute-container {
  max-width: 500px;
  padding: 1rem;
  border-left: 5px solid #333;
  border-radius: 8px;
  margin-bottom: 1rem;
}
p {
  font-size: 18px;
  margin-bottom: 10px;
}
cite {
    font-style: italic;
    color: #777;
}
.quote-text {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}
.quote-author {
  font-size: 1rem;
  text-align: right;
}
.quote-btn {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  background-color: #333;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.quote-btn:hover {
  background-color: #555;
}
</style>
