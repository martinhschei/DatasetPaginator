# DatasetPaginator
A paginator component for paginating a dataset

<dataset-paginator v-if="archiveReady" :initial-items-per-page="12" :dataset="media">
    <template v-slot="{ items }">
      <div v-for="item in items">
        <h1> {{ item.prop }} </div>
      </div>
    </template>
</dataset-paginator>
