<template>
    <div>
        <form>
            <div class="form-first-group">
                <div :class="[errors.authorError ? 'input-group input-group-error' : 'input-group']">
                    <label>Autheur</label>
                    <input v-model="author" type="text">
                    <div class="error-msg" v-if="errors.authorError">
                        <p>{{ errors.authorError }}</p>
                    </div>
                </div>
                <div :class="[errors.titleError ? 'input-group input-group-error' : 'input-group']">
                    <label>Titre</label>
                    <input v-model="title" type="text">
                    <div class="error-msg" v-if="errors.titleError">
                        <p>{{ errors.titleError }}</p>
                    </div>
                </div>
            </div>
            <div :class="[errors.descriptionError ? 'input-group input-group-error' : 'input-group']">
                <label>Description</label>
                <input v-model="description" type="text">
                <div class="error-msg" v-if="errors.descriptionError">
                        <p>{{ errors.descriptionError }}</p>
                </div>
            </div>
            <div :class="[errors.contentError ? 'input-group input-group-error' : 'input-group']">
                <label>Content</label>
                <textarea v-model="content" type="text" rows="10" />
                <div class="error-msg" v-if="errors.contentError">
                        <p>{{ errors.contentError }}</p>
                </div>
            </div>
            <button @click="addNewComment">Ajouter</button>
        </form>
    </div>
</template>

<script>

export default {
    methods: {
        addNewComment(e) {
            e.preventDefault()
            
            // Check if inputs are corectly filled
            this.checkFormInputs()

            if (!this.errors.authorError && !this.errors.titleError &&
                !this.errors.descriptionError && !this.errors.contentError) {
                // Create the new comment
                this.createNewComment()
            }
        },
        checkFormInputs() {
            // Check all inputs and fill the errors array
            this.errors = {}

            if (this.author.length === 0) this.errors.authorError = 'Nom d\'autheur obligatoire'
            if (this.title.length === 0) this.errors.titleError = 'Titre obligatoire'
            if (this.description.length === 0) this.errors.descriptionError = 'Description obligatoire'
            if (this.content.length === 0) this.errors.contentError = 'Contenu obligatoire'
        },
        createNewComment() {
            // Create the new comment
            const newComment = {
                author: this.author,
                title: this.title,
                description: this.description,
                date: new Date(),
                content: this.content
            }
            // Pass the new comment to the parent element
            this.$emit('newComment', newComment)
        }
    },
    data() {
        return {
            errors: {},
            author: '',
            title: '',
            description: '',
            date: '',
            content:''
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        flex-direction: column;
    }
    .form-first-group {
        display: flex;
        justify-content: space-between;
    }
    .form-first-group .input-group {
        width: 48%;
    }
    .input-group {
        border: 2px solid grey;
        border-radius: 7px;
        margin: 20px 0;
        position: relative;
    }
    
    .input-group label {
        position: absolute;
        height: 15px;
        top: -13px;
        left: 10px;
        background-color: white;
        padding: 0 5px;
        color: black;
        font-weight: 500;
    }
    .input-group input {
        outline: none;
        border: none;
        width: 94%;
        margin: 5px;
        padding: 5px;
    }
    .input-group textarea {
        border: none;
        outline: none;
        width: 96%;
        margin: 5px;
        margin-bottom: 0;
        resize: vertical;
    }
    .form-first-group input {
        width: 88%;
    }
    .input-group-error {
        border-color: red;
    }
    .input-group-error label {
        color: red;
    }
    .error-msg {
        position: absolute;
        bottom: -24px;
    }
    .error-msg p {
        color: red;
        margin: 0;
        font-size: 14px;
    }
    button {
        margin: 10px 0;
        background-color: #42b983;
        border: none;
        border-radius: 7px;
        cursor: pointer;
        padding: 10px 15px;
        font-weight: 600;
        color: white;
        width: fit-content;
    }
</style>