<template>
    <div class="team carousel-item" v-bind:class="{ active: isActive }" >
        <img class="d-block w-100" src="https://helpx.adobe.com/content/dam/help/en/photoshop/using/convert-color-image-black-white/jcr_content/main-pars/before_and_after/image-before/Landscape-Color.jpg" :alt="team.name">
        <div class="carousel-caption d-none d-md-block">
            <h5>{{team.name}}</h5>
            <p>{{team.description}}</p>
        </div>
    </div>
</template>

<script>

import TeamItem from "./TeamItem"

export default {
    props: ['team', 'index'],
    data: function () {
        return {
            isActive : this.index == 0
        }
    },

}
</script>