<template>
    <v-app>
        <app-layout>
            <template #header>
                <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                    Dashboard
                </h2>
            </template>
            <!-- <Main /> -->

            <div class="py-12">
                <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                    <div
                        class="bg-white overflow-hidden shadow-xl sm:rounded-lg"
                    >
                        <welcome />
                        <!-- <img
                        src="https://i.ytimg.com/vi/MQyjFLP-Krk/maxresdefault.jpg"
                    /> -->
                    </div>
                </div>
            </div>
        </app-layout>
    </v-app>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
import Welcome from "@/Jetstream/Welcome";
import Main from "@/Pages/Main.vue";

export default {
    components: {
        AppLayout,
        Welcome,
        Main,
    },
};
</script>
