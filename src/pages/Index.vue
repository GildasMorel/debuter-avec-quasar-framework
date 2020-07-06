<template>
    <q-page class="flex flex-center">
        <q-infinite-scroll @load="infiniteScroll" :offset="nbItemsPerPage" class="q-mt-xl">
            <q-pull-to-refresh @refresh="pullToRefresh">
                <p v-for="block in blocks" :key="block.id">{{ block.message }}</p>
            </q-pull-to-refresh>
            <template v-slot:loading>
                <div class="row justify-center q-my-md">
                    <q-spinner-dots color="primary" size="40px" />
                </div>
            </template>
        </q-infinite-scroll>
    </q-page>
</template>

<script>
export default {
    data() {
        return {
            nbItemsPerPage: 50,
            blocks: []
        }
    },
    created() {
        this.blocks = this.getNewBlocks(0, this.nbItemsPerPage);
    },
    methods: {
        getNewBlocks(cursor, nb) {
            const newBlocks = [];

            for (let i = cursor + 1; i <= cursor + nb; i++) {
                newBlocks.push({ id: i, message: `Line ${i}` });
            }

            return newBlocks;
        },
        pullToRefresh(done) {
            setTimeout(() => {
                this.blocks = this.blocks.slice(0, this.nbItemsPerPage);
                done();
            }, 1500);
        },
        infiniteScroll(index, done) {
            setTimeout(() => {
                this.blocks = [
                    ...this.blocks,
                    ...this.getNewBlocks(this.blocks.length, this.nbItemsPerPage)
                ];
                done();
            }, 1500);
        }
    }
}
</script>
