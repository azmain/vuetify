<template>
    <div class="team" background-color="red">
        <h1 class="subheading grey--text">Team</h1>

        <v-container class="my-5">
            <v-layout row wrap>
                <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
                    <v-card flat class="text-xs-center ma-3">
                        <v-responsive class="pt-4">
                            <v-avatar size="100" class="red lighten-2">
                                <img :src="person.avatar" alt="Avatar">
                            </v-avatar>
                        </v-responsive>
                        <v-card-text>
                            <div class="subheading">
                                {{ person.name }}
                            </div>
                            <div class="grey--text">
                                {{ person.role }}
                            </div>
                        </v-card-text>
                        <v-card-actions>
                            <v-btn flat color="grey">
                                <v-icon small left>message</v-icon>
                                <span>Message</span>
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </v-flex>
            </v-layout>
        </v-container>
    </div>
</template>

<script>
export default {
    name: 'Team',
    data(){
        return {
            team: [
                {
                    name: 'Nishan',
                    role: 'Programmer',
                    avatar: '/avatar.jpg'
                },
                {
                    name: 'Azmain',
                    role: 'Web Developer',
                    avatar: '/avatar.jpg'
                },
                {
                    name: 'Islam',
                    role: 'Software Engineer',
                    avatar: '/avatar.jpg'
                },
                {
                    name: 'A I N',
                    role: 'Dreamer',
                    avatar: '/avatar.jpg'
                },
            ]
        }
    }
}
</script>

