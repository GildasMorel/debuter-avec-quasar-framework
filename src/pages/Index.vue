<template>
    <q-page class="flex flex-center">
        <q-uploader
            class="q-ma-lg"
            label="Photos / Vidéos / Audio"
            method="put"
            :factory="getSignedUrl"
            multiple send-raw
            hide-upload-btn
            flat bordered
            accept="image/*, video/*, audio/*"
        />
    </q-page>
</template>

<script>
export default {
    name: 'PageIndex',
    methods: {
        getSignedUrl() {
            return '';
        }
    }
}
</script>
