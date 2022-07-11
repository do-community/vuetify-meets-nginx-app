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
            <v-card elevation="2">
                <v-card-title>
                    <v-text-field
                        v-model="newTask"
                        append-outer-icon="mdi-content-save"
                        clear-icon="mdi-close-circle"
                        clearable
                        filled
                        type="text"
                        @click:append-outer="addTask"
                        @click:clear="clearTask"
                    ></v-text-field>
                </v-card-title>
                <v-card-text>
                    {{ tasks }}
                </v-card-text>
            </v-card>
        </v-main>
    </v-app>
</template>

<script>

export default {
    name: 'App',

    data: () => ({
        tasks: [],
        newTask: null
    }),
    methods: {
        addTask() {
            this.tasks.push(this.newTask);
            this.clearTask();
        },
        clearTask() {
            this.newTask = '';
        }
    }
};
</script>
