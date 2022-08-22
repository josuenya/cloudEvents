<script setup>
import { Head, Link } from '@inertiajs/inertia-vue3';
import VueCalendar from "@/Components/VueCalendar.vue";
import {onMounted, reactive} from "vue";
defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
    events: [],
});

const modal = reactive ({
    display: false
})

onMounted(() => {
    // console.log('events', events)
})
</script>

<template>
    <div class="">
        <Head title="Event-cloud" />
        <div class="bg-blue-600 flex justify-between items-center text-white font-bold px-5 py-2">
            <Link :href="'/'">Cloud-Event</Link>
            <div class="flex items-center space-x-2">
                <div v-if="canLogin">
                    <Link v-if="$page.props.user" :href="route('dashboard')" class="text-sm dark:text-gray-500">Dashboard</Link>
                    <template v-else>
                        <Link :href="route('login')" class="text-sm dark:text-gray-500">Log in</Link>

                        <Link v-if="canRegister" :href="route('register')" class="ml-4 text-sm dark:text-gray-500">Register</Link>
                    </template>
                </div>
            </div>
        </div>
        <div class="" style="min-height: calc(100vh - 40px) !important;">
            <vue-calendar :EventsData="events" />
        </div>
    </div>
</template>
