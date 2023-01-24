<script>
import { computed, onMounted, onBeforeUpdate } from "vue";
import titles from "../post-data.json";

export default {
    props: {
        query: String,
    },
    setup(props, context) {

        onBeforeUpdate(() => {
            console.log("before update");
        })

        onMounted(() => {
            console.log("here");
        })

        const filteredTitles = computed(() => {
            return titles.filter((s) => s.Name.toLowerCase().includes(props.query.toLowerCase()))
        })

        return {
            filteredTitles,
        }
    },
};

</script>

<template>
    <div class="root">
        <p>Showing {{filteredTitles.length}} results for "{{query}}"</p>
        <ul>
            <li v-for="title in filteredTitles" :key="title.page">
                {{ title.Name }}
            </li>
        </ul>
    </div>
</template>