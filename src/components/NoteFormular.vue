<template>
    <form @submit.prevent="submitNote">
      <div>
        <label for="title">Titel:</label>
        <input type="text" id="title" placeholder="Titel" v-model="note.title" />
        <span v-if="errors.title" class="error-message">{{ errors.title }}</span>
      </div>
      <div>
        <label for="description">Beschreibung:</label>
        <textarea id="description" placeholder="Beschreibung" v-model="note.description"></textarea>
        <span v-if="errors.description" class="error-message">{{ errors.description }}</span>
      </div>
      <button type="submit">Notiz absenden</button>
    </form>
</template>
    
<script>
    export default {
        data() {
            return {
                note: {
                    title: '',
                    description: ''
                },
                errors: {
                    title: '',
                    description: ''
                },
            };
        },
        methods: {
            submitNote() {
                this.errors.title = '';
                this.errors.description = '';
                
                if (!this.note.title) {
                this.errors.title = 'Der Titel darf nicht leer sein.';
                }
                if (!this.note.description) {
                    this.errors.description = 'Die Beschreibung darf nicht leer sein.';
                }

                if (this.note.title && this.note.description) {
                    this.$emit('note-submitted', { ...this.note });

                    this.note.title = '';
                    this.note.description = '';
                }
            }
        }
    };
</script>

<style scoped>
    form {
        display: flex;
        flex-direction: column;
        gap: 20px;
        max-width: 400px;
        margin: 0 auto;
        padding: 20px;
        background-color: #1e1e1e;
        border-radius: 8px;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }

    label {
        font-size: 1rem;
        color: #f1f1f1;
        margin-bottom: 6px;
    }

    input, textarea {
        width: 100%;
        padding: 12px;
        background-color: #181818;
        border: 1px solid #f1f1f1;
        border-radius: 4px;
        color: #b7b7b7;
        font-size: 1rem;
        outline: none;
        transition: border-color 0.3s ease;
    }

    input:focus, textarea:focus {
        border-color: #1f7c53;
    }

    textarea {
        min-height: 100px;
        resize: vertical;
    }

    button {
        padding: 12px 16px;
        background-color: #40B883;
        color: #fff;
        border: none;
        border-radius: 4px;
        font-size: 1rem;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }

    button:hover {
        background-color: #34986d;
    }

    button:active {
        background-color: #1f7c53;
    }

    .error-message {
        color: #ff6b6b;
        font-size: 0.6rem;
    }
</style>