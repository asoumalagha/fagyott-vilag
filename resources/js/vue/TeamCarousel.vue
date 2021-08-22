<template>
    <div id="teamCarouselIndicators" class="carousel slide" data-ride="carousel">
        <ol class="carousel-indicators">
            <li v-for="(team, index) in teams" :key="index" v-bind:class="{ active: index == 0}" data-target="#teamCarouselIndicators" :data-slide-to="index"></li>
        </ol>
        <div class="carousel-inner">
            <div v-for="(team, index) in teams" :key="index" class="team carousel-item" v-bind:class="{ active: index == 0}">
                <img class="team-picture d-block" :src="getPicture(team.picture)" :alt="team.name">
                <div class="carousel-caption">
                    <h5 class="d-none d-md-block">{{team.name}}</h5>
                    <button @click="loadContent(team.name, team.description)" type="button" class="d-block d-md-none team-modal-button" data-toggle="modal" data-target="#teamDescriptionModal">
                        {{team.name}}
                    </button>
                    <div class="d-none d-md-block">
                        <p>{{team.description}}</p>
                    </div>
                </div>
            </div>
        </div>
        <!-- <ol class="carousel-indicators">
            <li data-target="#teamCarouselIndicators" data-slide-to="0" class="active"></li>
            <li data-target="#teamCarouselIndicators" data-slide-to="1"></li>
            <li data-target="#teamCarouselIndicators" data-slide-to="2"></li>
        </ol>
        <div class="carousel-inner">
            <div v-for="(team, index) in teams" :key="index" class="team carousel-item" v-bind:class="{ active: index == 0}">
                <team-item
                    :team="team"
                    :index="index"
                />
            </div>
        </div> -->

        <a class="carousel-control-prev" href="#teamCarouselIndicators" role="button" data-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="sr-only">Előző</span>
        </a>
        <a class="carousel-control-next" href="#teamCarouselIndicators" role="button" data-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="sr-only">Következő</span>
        </a>
        
        <div class="modal fade" id="teamDescriptionModal" tabindex="-1" role="dialog" aria-labelledby="teamDescriptionModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                <div class="modal-header">
                    <h5 ref="teamModalTitle" class="modal-title" id="teamDescriptionModalLabel">Modal title</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div ref="teamModalBody" class="modal-body">
                    ...
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-dismiss="modal">Bezár</button>
                </div>
                </div>
            </div>
        </div>



    </div>
    
</template>

<script>

import TeamItem from "./TeamItem";

export default {
    props : ['teams'],
    components: {
        TeamItem
    },
    methods: {
        getPicture(name)
        {
            return './img/' + name;
        },
        loadContent(name, description)
        {
            this.$refs.teamModalTitle.innerText = name;
            this.$refs.teamModalBody.innerText = description;

        }
    },
}
</script>
