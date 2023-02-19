<template>

    <Head title="New Skill" />
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">New Project</h2>
        </template>

        <div class="py-12">
            <div class="max-w-md mx-auto sm:px-6 lg:px-8 bg-white">
                <form class="p-4" @submit.prevent="submit">
                    <div>
                        <InputLabel for="skill_id" value="Skill"></InputLabel>
                        <select v-model="form.skill_id" id="skill_id" name="skill_id"
                            class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md">
                            <option v-for="skill in skills" :key="skill.id" :value="skill.id">{{ skill.name }}</option>
                        </select>
                    </div>
                    <div>
                        <InputLabel for="name" value="Name" />

                        <TextInput id="name" type="text" class="mt-1 block w-full" v-model="form.name" autofocus autocomplete="name" />

                        <InputError class="mt-2" :message="$page.props.errors.name" />
                    </div>

                    <div>
                        <InputLabel for="project_url" value="URL" />

                        <TextInput id="project_url" type="text" class="mt-1 block w-full" v-model="form.project_url"
                            autocomplete="project_url" />

                        <InputError class="mt-2" :message="$page.props.errors.project_url" />
                    </div>

                    <div class="m-2">
                        <InputLabel for="image" value="Image" />

                        <TextInput id="image" type="file" class="mt-1 block w-full"
                            @input="form.image = $event.target.files[0]" />

                        <InputError class="mt-2" :message="$page.props.errors.image" />
                    </div>

                    <div class="flex items-center justify-end mt-4">
                        <button class="px-2 py-1 bg-indigo-500 hover:bg-indigo-700 text-white rounded-md"
                            :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            <font-awesome-icon icon="fa-solid fa-save" /> Update
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, useForm } from '@inertiajs/inertia-vue3';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Inertia } from '@inertiajs/inertia';

/* import the fontawesome core */
import { library } from '@fortawesome/fontawesome-svg-core'

/* import specific icons */
import { faSave } from '@fortawesome/free-solid-svg-icons'

/* import font awesome icon component */
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

/* add icons to the library */
library.add(faSave)

const form = useForm({
    name: props.project?.name,
    image: null,
    skill_id: props.project?.skill_id,
    project_url: props.project?.project_url
});

const submit = () => {
    Inertia.post(`/projects/${props.project.id}`, {
        _method: "put",
        name: form.name,
        image: form.image,
        skill_id: form.skill_id,
        project_url: form.project_url
    })
};

const props = defineProps({
    skills: Array,
    project: Object,
})

</script>