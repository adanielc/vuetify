<template>
    <nav>
        <v-toolbar flat>
            <!--navegation bar button-->
            <v-app-bar-nav-icon class="grey--text" @click="drawer=!drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-uppercase grey--text">
                <span class="font-weight-light">Todo</span>
                <span>Ninja</span>

            </v-toolbar-title>
            <v-spacer></v-spacer>

            <v-menu offset-y>
                <template v-slot:activator="{ on, attrs }">
                    <v-btn
                            text
                            v-bind="attrs"
                            v-on="on"
                            color="grey"
                    >
                        <v-icon left>mdi-chevron-down</v-icon>
                        <span>Menu</span>
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item
                            v-for="(link, index) in links"
                            :key="link.text" router :to="link.route"
                    >
                        <v-list-item-title>{{ link.text }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>


            <v-btn text color="grey">
                <span>Sing Out</span>
                <v-icon>mdi-exit-to-app</v-icon>
            </v-btn>
        </v-toolbar>
        <!--absolute temporary for close on click elsewhere-->
        <v-navigation-drawer v-model="drawer" app absolute temporary class="primary">
            <v-row >
                <v-col align="center" class="mt-5">
                    <avatar size="100">
                        <img src="/avatar-1.png" >
                    </avatar>
                    <p class="white--text subtitle-1 mt-1">The Net Ninja</p>

                </v-col>
            </v-row>
            <v-list>
                <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                    <v-list-item-action>
                        <v-icon class="white--text">{{link.icon}}</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                        <v-list-item-title class="white--text">{{link.text}}</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </nav>

</template>


<script>
    export default {
        data() {
            return {
                drawer: false,
                links: [
                    {icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/'},
                    {icon: 'mdi-folder', text: 'My Projects', route: '/projects'},
                    {icon: 'mdi-account', text: 'Team', route: '/team'}
                ]

            }
        }
    }
</script>