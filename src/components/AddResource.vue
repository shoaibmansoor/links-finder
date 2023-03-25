<template>
    <TheDialogue
        v-if="invalidInput"
        title="Invalid Input!!!"
        @close="closeDialog"
    >
        <template #default>
            <p>Invalid inputs provided</p>
            <p>Consider providing some characters for each input fields</p>
        </template>
        <template #actions>
            <button @click="closeDialog">OK</button>
        </template>
    </TheDialogue>
    <div class="add-resrouce box-shadow">
        <label for="title">Title</label>
        <input
            type="text"
            name="title"
            id="title"
            v-model="form.title"
        >
        <label for="description">Description</label>
        <textarea
            name="description"
            id="description"
            cols="30"
            rows="10"
            v-model="form.description"
        ></textarea>
        <label for="link">Link</label>
        <input
            type="text"
            name="link"
            id="link"
            v-model="form.link"
        >
        <button @click="addResource">Add Resource</button>
    </div>
</template>

<script>
import TheDialogue from './TheDialogue.vue'
export default {
    components: {
        TheDialogue,
    },
    data() {
        return {
            form: {
                title: '',
                description: '',
                link: '',
            },
            invalidInput: false,
        };
    },
    methods: {
        addResource() {
            if (this.form.title.trim() === '' || this.form.description.trim() === '' || this.form.link.trim() === '') {
                this.invalidInput = true;
                return;
            }

            this.$emit('add-resource', Object.assign({}, this.form))
            this.form.title = '';
            this.form.description = '';
            this.form.link = '';
        },
        closeDialog() {
            this.invalidInput = false;
        },
    },
}

</script>

<style scoped>
.add-resrouce {
    display: flex;
    flex-direction: column;
    width: 100vh;
    height: 400px;
    margin: 20px auto 20px auto;
    border: 2px solid black;
    padding: 10px;
    /* align-items: space-around;
    justify-content: space-between; */
}

.add-resrouce label,
button {
    font-weight: bold;
    font-size: 24px;
    margin: 10px 0 10px 0;
}</style>