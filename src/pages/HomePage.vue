<script>
import AppSlider from '../components/AppSlider.vue';
import AppBanner from "../components/AppBanner.vue";
import AppCard from "../components/AppCard.vue";
import { store } from '../store';
import AppcardHover from '../components/AppcardHover.vue';
import AppBlog from '../components/AppBlog.vue';

export default {
    data() {
        return {
            activeIndex: 0,
            store
        };
    },
    methods: {
        goToSlide(index) {
            this.activeIndex = index;
        },
        getUrlPath(img) {
            return new URL(`../assets/${img}.jpg`, import.meta.url).href;
        }
    },
    components: { AppSlider, AppBanner, AppCard, AppcardHover, AppBlog }
};
</script>

<template>
    <section class="container-fluid p-0 ms_container">
        <AppSlider />
    </section>
    <section v-for="item in store.heroHomeTop">
        <AppBanner :bannerObj="item" />
    </section>
    <section v-for="item in store.heroHomeBottom">
        <AppBanner :bannerObj="item" />
    </section>
    <section class="ms_cardsHome">
        <h1 class="fw-bold fs-1">Services</h1>
        <span class="ms_line mt-5"><span class="ms_inner_ine"></span></span>
        <div class="container-fluid p-5">
            <div class="row row-cols-1 row-cols-md-3">
                <div class="col" v-for="item in store.cardsHome">
                    <!-- CARD -->
                    <AppCard :cardObj="item" />
                    <!-- /CARD -->
                </div>
            </div>
        </div>
    </section>
    <section class="ms_containerCardx4 py-5 our-yatch">
        <h1 class="fw-bold fs-1 text-white pt-3">Our Yachts</h1>
        <span class="ms_line mt-5"><span class="ms_inner_ine"></span></span>
        <div class="container-fluid p-5">
            <div class="row row-cols-1 row-cols-md-4">
                <div class="col" v-for="item in store.cardsHomeServices">
                    <!-- CARD -->
                    <AppcardHover :cardObj="item" />
                    <!-- /CARD -->
                </div>
            </div>
        </div>
        <button class="btn border text-white fs-4">Learn More</button>
    </section>
    <section v-for="item in store.NewBanner">
        <AppBanner :bannerObj="item" />
    </section>
    <section class="ms_containerSectionblog">
        <div class="ms_ContainerBolg" v-for="item in store.postArray">
            <AppBlog :cardObj="item" />
        </div>
    </section>
</template>


<style scoped lang="scss">
.our-yatch{
    .ms_line {
    width: 90%;
    border: 0px ;
    .ms_inner_ine {
        display: block;
        width: 5%;
        margin: 0 auto;
        border: .1px solid #f1f3f4;
    }
}
}

.ms_cardsHome {
    background-image: url("../assets/bg6.jpg");
    background-attachment: fixed;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.ms_container {
    width: 100%;
    height: 100%;
}

.ms_line {
    width: 90%;
    border: .1px solid rgba(0, 0, 0, 0.074);
    background-color: rgba(0, 0, 0, 0.03);

    .ms_inner_ine {
        display: block;
        width: 5%;
        margin: 0 auto;
        border: .1px solid #09c2dd;
    }
}

.ms_containerCardx4 {
    background-color: #09c2dd;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
</style>