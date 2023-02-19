<template>

    <Head title="Projects" />
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Projects</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="flex justify-end m-2 p-2">
                    <Link href="/projects/create" class="px-2 py-1 bg-indigo-500 hover:bg-indigo-700 text-white rounded-md">
                    <font-awesome-icon icon="fa-solid fa-plus" />New</Link>
                </div>
                <div class="overflow-x-auto relative">
                    <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
                        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                            <tr>
                                <th class="py-3 px-6" scope="col">S/N</th>
                                <th class="py-3 px-6" scope="col">Name</th>
                                <th class="py-3 px-6" scope="col">SKill</th>
                                <th class="py-3 px-6" scope="col">Created</th>
                                <th class="py-3 px-6" scope="col">Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="project in projects.data" :key="project.id" class="bg-white border-b dark:text-gray-400">
                                <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-gray-400">
                                    {{ project.id }}
                                </th>
                                <td class="py-4 px-6">{{ project.name }}</td>
                                <td class="py-4 px-6">
                                    <img :src="project.image" class="w-12 h-12 rounded-full" />
                                </td>
                                <td class="py-4 px-6">{{ project.created_at }}</td>
                                <td class="py-4 px-6">
                                    <Link :href="route('projects.edit', project.id)"
                                        class="bg-orange-500 text-white rounded-sm hover:bg-orange-700 mr-2 px-2 py-1">
                                    <font-awesome-icon icon="fa-solid fa-edit" />Edit
                                    </Link>
                                    <Link :href="route('projects.destroy', project.id)" method="delete" as="button" type="button"
                                        class="bg-red-500 text-white rounded-sm hover:bg-red-700 mr-2 py-1 px-2">
                                    <font-awesome-icon icon="fa-solid fa-trash-alt" /> Delete
                                    </Link>
                                </td>                                
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/inertia-vue3';
/* import the fontawesome core */
import { library } from '@fortawesome/fontawesome-svg-core'

/* import specific icons */
import { faPlus, faEdit, faTrashAlt } from '@fortawesome/free-solid-svg-icons'

/* import font awesome icon component */
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

/* add icons to the library */
library.add(faPlus, faEdit, faTrashAlt)

defineProps({
    projects: Object,
})
</script>