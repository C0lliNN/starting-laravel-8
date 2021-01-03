<template>
    <app-layout>
        <template #header>
                <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                    Todos Details
                </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <div class="p-5">
                        <table class="w-full">
                          <tr class="border">
                            <th scope="row" class="text-left p-3">ID</th>
                            <td class="p-3">{{ id }}</td>
                          </tr>
                          <tr class="border bg-gray-200">
                            <th scope="row" class="text-left p-3">Title</th>
                            <td class="p-3">{{ title }}</td>
                          </tr>
                          <tr class="border">
                            <th scope="row" class="text-left p-3">Description</th>
                            <td class="p-3">{{ description }}</td>
                          </tr>
                          <tr class="border bg-gray-200">
                            <th scope="row" class="text-left p-3">Created At</th>
                            <td class="p-3">{{ created_at }}</td>
                          </tr>
                        </table>
                    </div>
                </div>
            </div>
        </div>

    </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";

export default {
    props: {
        id: {
            required: true,
            type: Number
        },
        title: {
          required: true,
          type: String
        },
        description: {
          required: true,
          type: String
        },
        created_at: {
          required: true,
          type: String
        }
    },
    components: {
        AppLayout,
    },
};
</script>
