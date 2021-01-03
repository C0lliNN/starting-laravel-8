<template>
    <app-layout>
        <template #header>
            <div class="flex justify-between align-middle">
                <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                    Todos
                </h2>
                <jet-button @click.native="handleShowCreateModal">
                    New
                </jet-button>
            </div>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <ul class="p-5">
                        <todo-item
                            v-for="todo in todos"
                            :key="todo.id"
                            v-bind="todo"
                        />
                    </ul>
                </div>
            </div>
        </div>

        <jet-modal :show="showCreateModal" @close="handleCloseCreateModal">
            <div class="p-5">
                <h3 class="text-center text-lg">Create New Todo</h3>
                <form
                    :action="route('todos.store')"
                    method="POST"
                    @submit.prevent="handleAddTodo"
                >
                    <jet-label for="title">Title</jet-label>
                    <jet-input
                        class="mt-1 w-full"
                        v-model="form.title"
                        id="title"
                        name="title"
                    />
                    <jet-input-error :message="errors.title" />

                    <jet-label for="description" class="mt-3"
                        >Description</jet-label
                    >

                    <jet-textarea
                        class="mt-1 w-full"
                        v-model="form.description"
                        id="description"
                        name="description"
                    />
                    <jet-input-error :message="errors.description" />
                    <jet-button
                        :type="'submit'"
                        class="mt-3"
                        :disabled="form.processing"
                        >Create</jet-button
                    >
                </form>
            </div>
        </jet-modal>
    </app-layout>
</template>

<script>
import AppLayout from '@/Layouts/AppLayout';
import JetButton from '@/Jetstream/Button.vue';
import JetModal from '@/Jetstream/Modal.vue';
import JetLabel from '@/Jetstream/Label.vue';
import JetInput from '@/Jetstream/Input.vue';
import JetInputError from '@/Jetstream/InputError.vue';
import JetTextarea from '@/Jetstream/Textarea.vue';
import TodoItem from '@/Todos/TodoItem.vue';

export default {
    props: {
        todos: {
            required: true,
            type: Array,
        },
        errors: Object,
    },
    components: {
        AppLayout,
        JetButton,
        JetModal,
        JetLabel,
        JetInput,
        JetTextarea,
        JetInputError,
        TodoItem,
    },
    data() {
        return {
            showCreateModal: false,
            form: this.$inertia.form({
                title: '',
                description: '',
            }),
            todoList: this.todos,
        };
    },
    methods: {
        handleShowCreateModal() {
            this.showCreateModal = true;
        },
        handleCloseCreateModal() {
            this.showCreateModal = false;
        },
        handleAddTodo() {
            const that = this;
            this.form.post(route('todos.store'), {
                onFinish() {
                    if (!that.errors.title && !that.errors.description) {
                        that.showCreateModal = false;
                    }
                },
            });
        },
    },
};
</script>
