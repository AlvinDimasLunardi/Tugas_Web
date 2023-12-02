<template>
    <div>
        <Menu />
        <div class="container">
            <h1 class="m0">Product</h1>
            <div class="row">
                <div class="col">
                    <p class="mt5 mb20 tc-green">Manage your product details</p>
                </div>
                <div class="col flex">
                    <router-link to="/add-product">
                        <button class="bt-green">+ Add </button>
                    </router-link>
                </div>
            </div>
            <div class="row bg-blue mt10 p10">
                <div class="col">
                    <input class="search-field" type="text" id="deskripsi" placeholder="Tambah deskripsi..." />
                </div>
                <div class="col flex">
                    <button class="bt-blue">Filter</button>
                </div>
            </div>
            <div class="mt50">
                <table>
                    <thead>
                        <tr>
                            <th>PRODUCT CODE</th>
                            <th>PRODUCT NAME</th>
                            <th>PRICE</th>
                            <th>STATUS</th>
                            <th>PRODUCT<br>CATEGORY</th>
                            <th>UNIT</th>
                            <th>PRODUCT<br>STATUS</th>
                            <th>PRODUCT<br>IMAGE</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="item of list_product" :key="item.id">
                            <td class="center">{{ item.product_code }}</td>
                            <td class="center">{{ item.product_name }}</td>
                            <td class="center">{{ item.price }}</td>
                            <td class="center"><div v-if="item.status === true">
                                    <label class="label-green">Publish</label>
                                </div>
                                <div v-if="item.status === false">
                                    <label class="label-red">Not Publish</label>
                                </div></td>
                            <td class="center">{{ item.product_category }}</td>
                            <td class="center">{{ item.unit }}</td>
                            <td class="center"><div v-if="item.product_status === true">
                                    <label class="label-green">Availability</label>
                                </div>
                                <div v-if="item.product_status === false">
                                    <label class="label-red">Not Availability</label>
                                </div></td>
                            <td class="center">
                                <img :src="item.product_image" alt="Product Image" v-if="item.product_image">
                                <span v-else>No Image</span>
                            </td>
                            <!-- <td class="center">
                                <div v-if="item.role === 1">
                                    <label class="label-green">Super Admin</label>
                                </div>
                                <div v-if="item.role === 2">
                                    <label class="label-blue">Sales</label>
                                </div>
                                <div v-if="item.role === 3">
                                    <label class="label-yellow">Marketing</label>
                                </div>
                            </td> -->
                            <td class="center">
                                <div class="mt5">
                                    <router-link to="/edit-product">
                                        <img src="../../assets/icons/edit.svg">
                                    </router-link>
                                </div>
                                <div class="mt5">
                                    <router-link to="/detail-product">
                                        <img src="../../assets/icons/detail.svg">
                                    </router-link>
                                </div>
                                <div class="mt5">
                                    <img src="../../assets/icons/delete.svg">
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
import Menu from "../../components/menu.vue"

export default {
    name: 'list-product',
    components: {
        Menu
    },
    data() {
        return {
            list_product: [
                {
                    id: "1",
                    product_code: "dfgr848",
                    product_name: "Realme 11 Pro",
                    price: "5.000.000",
                    status: true,
                    product_category: "Electronic",
                    unit: "10",
                    product_status: true,
                    product_image:  "https://p-id.ipricegroup.com/uploaded_4a9679e8b58e1518e9fa83a2115522f2d4a9fde7.jpg",
                    role: 1
                },
                {
                    id: "2",
                    product_code: "bhwop87",
                    product_name: "IKEA Kleppstad Lemari",
                    price: "3.200.000",
                    status: false,
                    product_category: "Furniture",
                    unit: "0",
                    product_status: false,
                    product_image: "data:image/jpeg;base64,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",
                    role: 1
                },
                {
                    id: "3",
                    product_code: "nknej298",
                    product_name: "Stone Island Shadow Project",
                    price: "19.000.000",
                    status: true,
                    product_category: "Clothing and Apparel",
                    unit: "2",
                    product_status: true,
                    product_image: "https://encrypted-tbn2.gstatic.com/shopping?q=tbn:ANd9GcSPolL57QOQBX-I-f2XAKgQTBbzbGNDvd9l1HJ4iscGud_S9s9hEW-dV2u_bbjN_MezN_zWsNnzQNIUxebQd2Je0EOKmpHmIkGJ7ifbNTE8eGvHopNCfPTz&usqp=CAE",
                    role: 1
                },
            ]
        }
    }
}
</script>