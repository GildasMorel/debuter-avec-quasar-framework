<template>
    <q-page class="flex flex-center">
        <q-carousel
            swipeable
            animated
            arrows
                thumbnails
                infinite
            v-model="slide"
            :fullscreen.sync="fullscreen"
            :style="`width: ${fullscreen ? '100vw' : '60vw'}`"
        >
            <q-carousel-slide :name="1" img-src="https://cdn.quasar.dev/img/mountains.jpg" />
            <q-carousel-slide :name="2" img-src="https://cdn.quasar.dev/img/parallax1.jpg" />
            <q-carousel-slide :name="3" img-src="https://cdn.quasar.dev/img/parallax2.jpg" />
            <q-carousel-slide :name="4" img-src="https://cdn.quasar.dev/img/quasar.jpg" />

            <template v-slot:control>
                <q-carousel-control
                    position="bottom-right"
                    :offset="[18, 18]"
                >
                    <q-btn
                        push round dense color="white" text-color="primary"
                        :icon="fullscreen ? 'fullscreen_exit' : 'fullscreen'"
                        @click="fullscreen = !fullscreen"
                    />
                        </q-carousel-control>
                </template>
        </q-carousel>
    </q-page>
</template>

<script>
export default {
    data () {
        return {
            slide: 1,
            fullscreen: false
        }
    }
}
</script>
