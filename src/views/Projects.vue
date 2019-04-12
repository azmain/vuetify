<template>
    <div class="projects">
        <h1 class="subheading grey--text">Projects</h1>

        <v-container class="my-5">

            <v-expansion-panel>
                <v-expansion-panel-content v-for="project in myProjects" :key="project.title">
                    <div slot="header">
                        {{ project.title }}
                    </div>
                    <v-card>
                        <v-card-text class="px-4 grey--text">
                            <div class="font-weight-bold">
                                {{ project.due }}
                            </div>
                            <div>{{ project.status }}</div>
                        </v-card-text>
                    </v-card>
                </v-expansion-panel-content>
            </v-expansion-panel>

        </v-container>
    </div>
</template>

<script>
export default {
    name: 'Projects',
    data(){
        return {
            projects: [
                {
                    title: "Read The Alchemist",
                    person: "Nishan",
                    due: "20 April 2019",
                    status: "ongoing"
                },
                {
                    title: "Menu Authentication & Authorization",
                    person: "Azmain",
                    due: "25 April 2019",
                    status: "overdue"
                },
                {
                    title: "Voucher Entry & Reporting",
                    person: "Nishan",
                    due: "15 March 2019",
                    status: "complete"
                }
            ]
        }
    },
    computed: {
        myProjects(){
            return this.projects.filter(project => {
                return project.person === 'Nishan';
            });
        }
    }
}
</script>

