<template>
    <v-app>
        <v-app-bar
            app
            color="primary"
            dark
        >
        <div class="d-flex align-center">
            <v-img
                alt="Vuetify Logo"
                class="shrink mr-2"
                contain
                src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
                transition="scale-transition"
                width="40"
            />

            <v-img
                alt="Vuetify Name"
                class="shrink mt-1 hidden-sm-and-down"
                contain
                min-width="100"
                src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
                width="100"
            />
        </div>

        <v-spacer></v-spacer>

        </v-app-bar>

        <v-main>
            <v-container>
                <v-card elevation="0">
                    <v-card-title>
                        <v-text-field
                            v-model="newTask"
                            label="Task Name"
                            prepend-icon="mdi-content-save"
                            clear-icon="mdi-close-circle"
                            clearable
                            filled
                            type="text"
                            @click:prepend="addNewTask"
                            @click:clear="clearNewTask"
                        ></v-text-field>
                    </v-card-title>
                    <v-card-text>
                        <v-timeline
                            v-if="tasks.length > 0"
                            dense
                            clipped
                        >
                            <v-timeline-item
                                v-for="(t, index) in tasks"
                                :key="index"
                            >
                                <v-row class="display-1 text-capitalize">
                                    <v-col cols="7">
                                        {{ t }}
                                    </v-col>
                                    <v-col
                                        class="text-right"
                                        cols="5"
                                    >
                                        <v-btn
                                            icon
                                            @click="removeTask(index)"
                                        >
                                            <v-icon color="red lighten-1" large>
                                                mdi-sticker-remove
                                            </v-icon>
                                        </v-btn>
                                    </v-col>
                                </v-row>
                            </v-timeline-item>
                        </v-timeline>
                    </v-card-text>
                </v-card>
            </v-container>
        </v-main>
    </v-app>
</template>

<script>

export default {
    name: 'App',

    data: () => ({
        tasks: ['task 1'],
        newTask: null
    }),
    methods: {
        addNewTask() {
            this.tasks.push(this.newTask);
            this.clearNewTask();
        },
        clearNewTask() {
            this.newTask = '';
        },
        removeTask(i) {
            this.tasks.splice(i, 1);
        }
    }
};
</script>
