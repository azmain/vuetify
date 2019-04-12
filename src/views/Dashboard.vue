<template>
    <div class="dashboard">
        <h1 class="subheading grey--text">Dashboard</h1>

        <v-container class="my-5">

            <v-layout row class="mb-3">
                <v-tooltip top>
                    <v-btn flat small color="grey" @click="sortBy('title')" slot="activator">
                        <v-icon left small>folder</v-icon>
                        <span class="caption text-lowercase">
                            By Project Name
                        </span>
                    </v-btn>
                    <span>Sort Project By Project Name</span>
                </v-tooltip>
                
                <v-tooltip top>
                    <v-btn flat small color="grey" @click="sortBy('person')" slot="activator">
                        <v-icon left small>person</v-icon>
                        <span class="caption text-lowercase">
                            By Person
                        </span>
                    </v-btn>
                    <span>Sort Project By Person</span>
                </v-tooltip>
                
            </v-layout>

            <v-card flat v-for="project in projects" :key="project.title">
                <v-layout row wrap :class="`pa-3 project ${project.status}`">
                    <v-flex xs12 md6>
                        <div class="caption grey--text">
                            Project Title
                        </div>
                        <div>{{ project.title }}</div>
                    </v-flex>
                    <v-flex xs6 sm4 md2>
                        <div class="caption grey--text">
                            Person
                        </div>
                        <div>{{ project.person }}</div>
                    </v-flex>
                    <v-flex xs6 sm4 md2>
                        <div class="caption grey--text">
                            Due Date
                        </div>
                        <div>{{ project.due }}</div>
                    </v-flex>
                    <v-flex xs2 sm4 md2>
                        <div class="right">
                            <v-chip :class="`my-2 caption white--text ${project.status}`">
                                {{ project.status }}
                            </v-chip>
                        </div>
                    </v-flex>
                </v-layout>
                <v-divider></v-divider>
            </v-card>
        </v-container>
    </div>
</template>

<script>
export default {
    name: 'Dashboard',
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
                    person: "Islam",
                    due: "15 March 2019",
                    status: "complete"
                }
            ],
        }
    },
    methods: {
        sortBy(prop){
            this.projects.sort((a,b) => a[prop]<b[prop]?-1:1);
        }
    }
}
</script>

<style scoped>
.project.complete{
    border-left: 4px solid green;
}
.project.ongoing{
    border-left: 4px solid yellow;
}
.project.overdue{
    border-left: 4px solid red;
}
.v-chip.complete{
    background: green;
}
.v-chip.ongoing{
    background: yellow;
}
.v-chip.overdue{
    background: red;
}
</style>


