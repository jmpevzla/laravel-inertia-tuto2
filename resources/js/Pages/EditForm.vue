<template>
    <AppLayout>
        <div class="flex items-center h-screen w-full bg-teal-lighter">
            <div class="w-full bg-white rounded shadow-lg p-8 m-4">
                <h1
                    class="block w-full text-center text-grey-darkest text-xl mb-6"
                >
                    Editar Producto
                </h1>
                <form @submit.prevent="submit" class="mb-6">
                    <div class="flex flex-col mb-4">
                        <label
                            class="mb-2 uppercase font-bold text-lg text-grey-darkest"
                            for="name"
                            >Nombre:</label
                        >
                        <input
                            id="name"
                            v-model="form.name"
                            class="border py-2 px-3 text-grey-darkest"
                        />
                    </div>
                    <div class="flex flex-col mb-4">
                        <label
                            class="mb-2 uppercase font-bold text-lg text-grey-darkest"
                            for="price"
                            >Precio:</label
                        >
                        <input
                            id="price"
                            v-model="form.price"
                            class="border py-2 px-3 text-grey-darkest"
                        />
                    </div>
                    <button
                        type="submit"
                        class="block bg-blue-500 hover:bg-blue-800 text-white uppercase text-lg mx-auto p-4 rounded"
                    >
                        Editar
                    </button>
                </form>
            </div>
        </div>
    </AppLayout>
</template>

<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { reactive, defineProps, toRefs } from 'vue';
import { router } from '@inertiajs/vue3';

const props = defineProps({
    product: Object,
})

const { product } = toRefs(props);

const form = reactive({
    name: product.value.name,
    price: product.value.price,
});

const submit = () => {
    router.put(route('products.update', product.value.id),
        form
    );
};

</script>

