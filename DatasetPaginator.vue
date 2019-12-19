<template>
    <div>
        <div class="row">
            <slot :items="itemsOnCurrentPage"> </slot>
        </div>
        <div class="row">
            <div class="col-md-12">
                <nav>
                    <ul class="pagination">
                        <li class="page-item"><a class="page-link" @click.prevent="previous" href="#">Previous</a></li>
                        <li class="page-item"><a class="page-link" @click.prevent="next" href="#">Next</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            dataset: Array,
            initialItemsPerPage: {
                type: Number,
                required: true,
            },
        },

        data() {
            return {
                currentPage: 0,
                itemsPerPage: this.initialItemsPerPage,
            }
        },

        computed: {
            itemsOnCurrentPage() {
                return this.pages[this.currentPage];
            },

            pages() {
                return _.chunk(this.dataset, this.itemsPerPage);
            },

            totalPages() {
                return this.pages.length - 1;
            }
        },

        methods: {
            previous() {
                if (this.currentPage > 0) {
                    this.currentPage--;
                }
            },

            next() {
                if (this.currentPage < this.totalPages) {
                    this.currentPage++;
                }
            },
        }
    };
</script>
