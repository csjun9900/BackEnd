<template>
    <div>
        <!-- component -->
        <div class="antialiased mx-auto max-w-screen-m p-3">
            <!-- <h3 class="mb-4 text-lg font-semibold text-gray-900">Comments</h3> -->
            <br />
            <div class="space-y-4">
                <div class="flex">
                    <div class="flex-shrink-0 mr-3">
                        <img
                            class="mt-2 rounded-full w-8 h-8 sm:w-10 sm:h-10"
                            src="https://static-cdn.jtvnw.net/jtv_user_pictures/27fdad08-a2c2-4e0b-8983-448c39519643-profile_image-70x70.png"
                            alt=""
                        />
                    </div>
                    <div
                        class="flex-1 border rounded-lg px-4 py-2 sm:px-6 sm:py-4 leading-relaxed"
                    >
                        <strong>{{ comment.user.name }}</strong>
                        <!-- <strong v-for="n in names" :key="n">{{ n }}</strong> -->
                        <!-- <span class="text-xs text-gray-400">3:34 PM</span> -->
                        <p class="text-sm">
                            {{ comment.comment }}
                        </p>
                        <div
                            class="flex justify-start items-center text-xs w-full"
                        >
                            <div
                                class="font-semibold text-gray-700 px-1 flex items-center justify-center space-x-1"
                            >
                                <a
                                    href="#"
                                    class="hover:underline"
                                    v-if="comment.user_id == login_user_id"
                                >
                                    <small>Update</small>
                                </a>
                                <small class="self-center">.</small>
                                <a
                                    href="#"
                                    class="hover:underline"
                                    v-if="comment.user_id == login_user_id"
                                >
                                    <small>Delete</small>
                                </a>
                                <small class="self-center">.</small>
                                <a href="#" class="hover:underline">
                                    <small>15 hour</small>
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["comment", "login_user_id"]
};
</script>
