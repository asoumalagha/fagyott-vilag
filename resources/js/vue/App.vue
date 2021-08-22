<template>
    <div class="team-container">
        <app-navbar></app-navbar>
        <team-carousel :teams="teams"></team-carousel>
    </div>
</template>

<script>
import TeamCarousel from "./TeamCarousel";
import AppNavbar from "./AppNavbar.vue";

export default {
    components : {
        TeamCarousel,
        AppNavbar

    },
    data: function () {
        return {
            teams: []
        }
    },
    methods: {
        getTeams()
        {
            axios.get('api/teams')
            .then (response => {
                this.teams = response.data
            })
            .catch(error => {
                console.log(error)
            })
        }
    },
    created(){
        this.getTeams();
    }
}
</script>
