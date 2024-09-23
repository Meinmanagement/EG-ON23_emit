<script setup>
  import NoteFormular from './components/NoteFormular.vue';
  import WelcomeEmit from './components/WelcomeTile.vue';
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <welcome-emit content="Willkommen"/>
    </div>
  </header>

  <main>
    <div>
      <h1 class="green">Notizen App</h1>
      <note-formular @note-submitted="handleNoteSubmit"></note-formular>
      <div class="notes" v-if="notes.length > 0">
        <h2 class="green">Gespeicherte Notizen</h2>
        <ul>
          <li v-for="(note, index) in notes" :key="index">
            <div>
              <strong>{{ note.title }}</strong>: {{ note.description }}
            </div>
            <button @click="deleteNote(index)" class="delete-btn">
              <svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-trash-2"><path d="M3 6h18"/><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"/><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"/><line x1="10" x2="10" y1="11" y2="17"/><line x1="14" x2="14" y1="11" y2="17"/></svg>
            </button>
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
  export default {
    components: {
      NoteFormular
    },
    data() {
      return {
        notes: []
      };
    },
    methods: {
      handleNoteSubmit(note) {
        this.notes.push(note);
      },
      deleteNote(index) {
        this.notes.splice(index, 1);
      }
    }
  }
</script>


<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

h1.green {
    font-size: 2.6rem;
    font-weight: bold;
    color: #40B883;
    background: linear-gradient(90deg, #34986d 0%, #40B883 100%);
    background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 20px;
    text-align: center;
    text-transform: uppercase;
    letter-spacing: 2px;
  }

  h1.green::after {
    content: "";
    display: block;
    width: 100px;
    height: 3px;
    background-color: #34986d;
    margin: 10px auto 0;
    border-radius: 2px;
  }

  main {
    max-width: 800px;
    max-height: 95vh;
    overflow-y: scroll;
    margin: 0 auto;
    padding: 20px;
    background-color: #1e1e1e;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }

  .notes {
    display: flex;
    flex-direction: column;
    gap: 20px;
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #1e1e1e;
    border-radius: 8px;
  }

  h2.green {
    color: #40B883;
    background: linear-gradient(90deg, #34986d 0%, #40B883 100%);
    background-clip: text;
    font-size: 1.4rem;
    font-weight: 600;
    text-align: left;
    -webkit-text-fill-color: transparent;
    text-align: center;
    text-transform: uppercase;
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  li {
    padding: 12px;
    margin-bottom: 10px;
    background-color: #181818;
    border: 1px solid #f1f1f1;
    border-radius: 6px;
    display: flex;
    justify-content: space-between;
    transition: background-color 0.3s ease;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  li div {
    display: block;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  button.delete-btn {
    background-color: #40B883;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 4px 8px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button.delete-btn:hover {
    background-color: #34986d;
  }

  strong {
    color: #40B883;
    font-weight: bold;
  }


  @media (min-width: 1024px) {
    header {
      display: flex;
      place-items: center;
      padding-right: calc(var(--section-gap) / 2);
    }

    .logo {
      margin: 0 2rem 0 0;
    }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
