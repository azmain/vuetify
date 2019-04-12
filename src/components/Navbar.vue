<template>
    <div class="navbar">
        <nav>
            <v-snackbar v-model="snackbar" :timeout="3000" top>
                <span>Awesome.</span>
                <v-btn flat color="white" @click="snackbar = false">close</v-btn>
            </v-snackbar>


            <v-toolbar flat app>
                <!-- Toggle Button -->
                <v-toolbar-side-icon class="grey--text" @click="drawer = !drawer"></v-toolbar-side-icon>
                
                <!-- Left Side Logo/Title -->
                <v-toolbar-title class="text-uppercase grey--text">
                    <span class="font-weight-light">Thy </span>
                    <span>Self</span>
                </v-toolbar-title>

                <!-- Strech space between two parts -->
                <v-spacer></v-spacer>
                
                <!-- Dropdown menu -->
                <v-menu offset-y>
                    <v-btn flat slot="activator" color="grey">
                        <v-icon left>expand_more</v-icon>
                        <span>Menu</span>
                    </v-btn>
                    <v-list>
                        <v-list-tile v-for="link in links" :key="link.route" router :to="link.route">
                            <v-list-tile-title>
                                {{ link.text }}
                            </v-list-tile-title>
                        </v-list-tile>
                    </v-list>
                </v-menu>

                <!-- Right side things -->
                <v-btn flat color="grey">
                    <span>Sign Out</span>
                    <v-icon right>exit_to_app</v-icon>
                </v-btn>
            </v-toolbar>

            <!-- Left side navigation drawer -->
            <v-navigation-drawer
                v-model="drawer"
                app
                dark
                >

                <v-layout column align-center>
                    <v-flex class="mt-5">
                        <v-avatar size="100">
                            <img src="/avatar.jpg" alt="User">
                        </v-avatar>
                        <p class="white--text subheading mt-4">
                            Know Thyself
                        </p>
                    </v-flex>

                    <!-- Popup -->
                    <v-flex class="mt-3 mb-2">
                        <Popup @projectAdded="projectAdded"/>
                    </v-flex>
                </v-layout>

                <v-list>
                    <v-list-tile v-for="link in links" :key="link.text" router :to="link.route">
                        <v-list-tile-action>
                            <v-icon>{{ link.icon }}</v-icon>
                        </v-list-tile-action>
                        <v-list-tile-content>
                            {{ link.text }}
                        </v-list-tile-content>
                    </v-list-tile>
                </v-list>
                
            </v-navigation-drawer>

        </nav>
    </div>
</template>

<script>
import Popup from './Popup'
export default {
    name: "Navbar",
    components:{
        Popup
    },
    data (){
        return{
            drawer: false,
            links: [
                {
                    icon: 'dashboard',
                    text: 'Dashboard',
                    route: '/'
                },
                {
                    icon: 'folder',
                    text: 'Projects',
                    route: '/projects'
                },
                {
                    icon: 'person',
                    text: 'Team',
                    route: '/team'
                }
            ],
            snackbar: false,
        }
    },
    methods: {
        projectAdded(){
            this.snackbar = true;
            this.drawer = false;
        }
    }
}
</script>
