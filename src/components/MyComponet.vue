<template>
  <div class="card-container">
    <header class="card-header">
      <span class="badge">Vue 3 Demo</span>
      <h1 v-if="isVisible" :class="{ 'highlight-text': isHighlighted }">
        {{ message }}
      </h1>
      <h1 v-else class="placeholder-text">
        <em>(Mensaje oculto)</em>
      </h1>
    </header>

    <section class="controls-section">
      <div class="button-group">
        <button class="btn btn-secondary" @click="toggleVisibility">
          {{ isVisible ? 'Ocultar' : 'Mostrar' }}
        </button>
        <button class="btn btn-accent" @click="toggleHighlight">
          Cambiar Color
        </button>
      </div>

      <div class="input-group">
        <label>Edita el título en tiempo real (v-model):</label>
        <input v-model="message" type="text" placeholder="Escribe un mensaje..." />
      </div>

      <div class="computed-box">
        <span>En mayúsculas:</span>
        <strong>{{ mensajeEnMayusculas }}</strong>
      </div>
    </section>

    <hr class="divider" />

    <section class="list-section">
      <h3>Lista dinámica (v-for)</h3>
      <ul class="styled-list">
        <li v-for="item in itemsList" :key="item.id">
          <span class="dot"></span>
          {{ item.text }}
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: 'MyComponent',
  data() {
    return {
      message: 'Hello World with Vue',
      isVisible: true,
      isHighlighted: false,
      itemsList: [
        { id: 1, text: 'Fundamentos de reactividad' },
        { id: 2, text: 'Directivas v-if, v-for y v-model' },
        { id: 3, text: 'Componentes y eventos' }
      ]
    }
  },
  computed: {
    mensajeEnMayusculas() {
      return this.message.toUpperCase()
    }
  },
  methods: {
    toggleVisibility() {
      this.isVisible = !this.isVisible
    },
    toggleHighlight() {
      this.isHighlighted = !this.isHighlighted
    }
  }
}
</script>

<style scoped>
.card-container {
  max-width: 520px;
  margin: 40px auto;
  background: #ffffff;
  padding: 32px;
  border-radius: 16px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  color: #2c3e50;
}

.card-header {
  text-align: center;
  margin-bottom: 24px;
}

.badge {
  display: inline-block;
  background: #42b88320;
  color: #42b883;
  font-size: 12px;
  font-weight: 700;
  padding: 4px 10px;
  border-radius: 20px;
  text-transform: uppercase;
  letter-spacing: 0.8px;
  margin-bottom: 10px;
}

h1 {
  font-size: 26px;
  font-weight: 700;
  margin: 0;
  transition: color 0.3s ease;
}

.highlight-text {
  color: #42b883;
}

.placeholder-text {
  color: #a0aec0;
  font-size: 22px;
}

.button-group {
  display: flex;
  gap: 12px;
  justify-content: center;
  margin-bottom: 20px;
}

.btn {
  border: none;
  padding: 10px 18px;
  font-size: 14px;
  font-weight: 600;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-secondary {
  background-color: #edf2f7;
  color: #4a5568;
}

.btn-secondary:hover {
  background-color: #e2e8f0;
}

.btn-accent {
  background-color: #42b883;
  color: #ffffff;
}

.btn-accent:hover {
  background-color: #33a06f;
  transform: translateY(-1px);
}

.input-group {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin-bottom: 14px;
}

.input-group label {
  font-size: 12px;
  font-weight: 600;
  color: #718096;
}

input {
  padding: 12px 14px;
  font-size: 15px;
  border: 1.5px solid #e2e8f0;
  border-radius: 8px;
  outline: none;
  transition: border-color 0.2s ease;
}

input:focus {
  border-color: #42b883;
}

.computed-box {
  background-color: #f7fafc;
  border-left: 4px solid #42b883;
  padding: 10px 14px;
  border-radius: 0 8px 8px 0;
  font-size: 13px;
  color: #4a5568;
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.computed-box strong {
  color: #2d3748;
}

.divider {
  border: 0;
  height: 1px;
  background-color: #edf2f7;
  margin: 24px 0;
}

.list-section h3 {
  font-size: 16px;
  margin-bottom: 12px;
  color: #4a5568;
}

.styled-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.styled-list li {
  display: flex;
  align-items: center;
  gap: 10px;
  background-color: #f8fafc;
  padding: 10px 14px;
  border-radius: 8px;
  font-size: 14px;
  border: 1px solid #edf2f7;
}

.dot {
  width: 8px;
  height: 8px;
  background-color: #42b883;
  border-radius: 50%;
}
</style>