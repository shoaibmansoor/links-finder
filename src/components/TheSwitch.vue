<template>
    <div class="navigator box-shadow">
        <div :class="{selected: showResourceSelected}">
            <button @click="showResources" >Stored Resources</button>
        </div>
        <div :class="{selected: !showResourceSelected}">
            <button @click="showAddResource">Add Resource</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            showResourceSelected: true,
        };
    },
    methods: {
        showResources() {
            this.showResourceSelected = true; 
            this.$emit('show-resource', true);
        },
        showAddResource() {
            this.showResourceSelected = false;
            this.$emit('add-resource', true);
        },
    }
}
</script>

<style>
.navigator {
    display: flex;
    flex-direction: row;
    border: 2px solid lightgrey;
    margin: 16px 100px 16px 100px;
    height: 200px;
    justify-content: space-around;
    align-items: center;
}

.navigator button {
    background: none;
	color: inherit;
	border: none;
	padding: 0;
	font: inherit;
	cursor: pointer;
	outline: inherit;
    font-weight: bold;
    font-size: 1.5rem;
}

.navigator div {
    display: inline-flex;
    flex-direction: row;
    justify-content: center;
    justify-items: center;
    border: 5px solid grey;
    width: 15rem;
    height: 5rem;
    
}

.selected {
    background-color: blueviolet;
    color: white;
    box-shadow: -2px 2px 8px 2px rgba(0, 0, 0, 0.5);
}
</style>