<template>
    <article>
        <h3>{{ dragonData.name }}</h3>
        <p class="skills">{{ dragonData.Skills }}</p>
        <img :src="dragonData.img_url" :alt="dragonData.name">
        <hr>
        <form @submit.prevent="handleSubmit">
            <label for="betterName">Rename to:</label>
            <input type="text" placeholder="Better name..." id="betterName" v-model="newName" required>
            <input type="submit" value="Update name" />
        </form>
        New name her {{ newName }}
        <!-- <button @click="handleClick">Emit stuff to parent</button> -->
    </article>
</template>

<script setup>

    import {ref} from "vue";

    // State

    const newName = ref("")

    // Modtag props
    const props = defineProps({ // Henter objektet fra app.vue (:dragonData="dragon")
        dragonData: Object
    })

    // Emit

    const emit = defineEmits(["updateName"])

    // const emit = defineEmits(["sillyEvent"])

    // Functions

    function handleSubmit(){
        emit("updateName", newName.value, props.dragonData.id)
    }

    // function handleClick(){
    //     emit("sillyEvent", "Hej med dig, jeg er en payload", 42);
    // }
</script>

<style scoped>
    article{
        border: 2px solid red;
        border-radius: 6px;
        padding: 1rem;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    img{
        width: 90%;
        margin: 5%;
    }
</style>