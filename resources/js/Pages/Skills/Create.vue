<template>

    <Head title="New Skill" />
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">New Skill</h2>
        </template>

        <div class="py-12">
            <div class="max-w-md mx-auto sm:px-6 lg:px-8 bg-white">
                <form class="p-4" @submit.prevent="submit">
                    <div>
                        <InputLabel for="name" value="Name" />
                
                        <TextInput id="name" type="text" class="mt-1 block w-full" v-model="form.name" required autofocus
                            autocomplete="Skill" />
                
                        <InputError class="mt-2" :message="form.errors.name" />
                    </div>

                    <div class="m-2">
                        <InputLabel for="image" value="Image" />
                
                        <TextInput id="image" type="file" class="mt-1 block w-full" @input="form.image = $event.target.files[0]" />
                
                        <InputError class="mt-2" :message="form.errors.image" />
                    </div>
                
                    <div class="flex items-center justify-end mt-4">
                        <button class="px-2 py-1 bg-indigo-500 hover:bg-indigo-700 text-white rounded-md" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                            <font-awesome-icon icon="fa-solid fa-save" /> Save
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
<script setup>
import { Head, useForm } from '@inertiajs/inertia-vue3';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
/* import the fontawesome core */
import { library } from '@fortawesome/fontawesome-svg-core'

/* import specific icons */
import { faSave} from '@fortawesome/free-solid-svg-icons'

/* import font awesome icon component */
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

/* add icons to the library */
library.add(faSave)
const form = useForm({
    name: '',
    image: null,
});

const submit = () => {
    form.post(route('skills.store'));
};
</script>