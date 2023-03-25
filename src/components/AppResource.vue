<template>
    <div class="resource box-shadow">
        <div class="resource-header">
            <p class="title">{{ title }}</p>
            <button @click="deleteReource(title)">Delete</button>
        </div>
        <p>{{ description }}</p>
        <a
            :href="link"
            target="_blank"
        >View Resource</a>
    </div>
</template>

<script>
export default {
    props: {
        id: Number,
        title: String,
        description: String,
        link: String
    },
    emits: [
        'delete-resource',
    ],
    data() {
        return {

        };
    },
    methods: {
        deleteReource() {
            this.$emit('delete-resource', { id: this.id, title: this.title });
        },
    }
}
</script>

<style scoped>
.resource {
    border-radius: 16px;
    display: flex;
    flex-direction: column;
    border: 2px solid black;
    margin: 20px 100px 20px 100px;
    padding: 3rem;
}

.resource-header p {
    margin: 0;
    margin-bottom: 1rem;
}

.resource-header {
    display: inline-flex;
    flex-direction: row;
    justify-content: space-between;
}

.resource-header button {
    background: none;
    color: inherit;
    border: none;
    padding: 0;
    font-size: 1.5rem;
    outline: inherit;
    cursor: pointer;
}

.title {
    font-size: 2rem;
    font-weight: bold;
}
</style>