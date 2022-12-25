<script setup lang="ts">
    const route = useRoute()
    const { data: product, pending } = await useFetch(`https://www.itgenius.co.th/sandbox_api/mrta_flutter_api/public/api/news/${route.params.id}`)
  // console.log(products.value.Target)
    // console.log(route.params.id)
</script>

<template>
    
    <div class="mb-5">
        <div v-if="!pending">
            <div class="wrapper">
                <v-row justify="center">
                <v-col cols="12" sm="10" md="9" lg="7">
                    <div class="text-center">
                    <h2 class="ui-title font-weight-bold text-white mb-4 mt-5">{{ product.topic }}</h2>
                    </div>
                </v-col>
                </v-row>
            </div>

            <v-container>
                <img :src="product.imageurl" :alt="product.topic" class="w-100">
                <h3 class="my-4">{{ product.detail }}</h3>
                <p class="my-4">{{ product.created_at }}</p>
                <a :href="product.linkurl" target="_blank">อ่านเพิ่มเติม</a>
            </v-container>
        </div>
        <div class="text-center py-10" v-else>Loading...</div>
    </div>

</template>


<style scoped>
    .ui-title {
        font-size: 32px;
    }

    .font-18{
        font-size: 18px;
    }

    .wrapper {
        background: #2196F3;
        padding: 40px 0 20px;
        min-height: 250px;
        display: flex;
        align-items: center;
        margin-bottom: 20px;
    }

    .blog-card {
        transition: 0.2s ease-in;
    }

    .blog-card:hover {
        transform: translateY(-10px);
    }

    .blog-title {
        color: #263238 !important;
        line-height: 22px;
        font-weight: bold;
    }

    .blog-title:hover {
        color: #607df9 !important;
    }


</style>