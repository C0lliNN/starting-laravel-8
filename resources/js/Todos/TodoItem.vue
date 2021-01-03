<template>
    <li
        class="border-t border-l border-r flex items-center justify-between px-4 py-3 last:border-b"
    >
        <h4>{{ title }}</h4>
        <div>
            <inertia-link
                as="button"
                :href="route('todos.show', id)"
                class="rounded bg-blue-500 text-white hover:bg-blue-600 px-3 py-2 mx-1 transition duration-200 ease-in-out"
            >
                Details
            </inertia-link>
            <inertia-link
                as="button"
                :href="route('todos.destroy', id)"
                method="DELETE"
                class="rounded bg-red-500 text-white hover:bg-red-600 px-3 py-2 transition duration-200 ease-in-out"
            >
                Delete
            </inertia-link>
        </div>
    </li>
</template>

<script>
import Button from "../Jetstream/Button.vue";

export default {
    components: {
        JetButton: Button
    },
    props: {
        id: {
            type: Number,
            required: true
        },
        title: {
            required: true,
            type: String
        }
    }
};
</script>
