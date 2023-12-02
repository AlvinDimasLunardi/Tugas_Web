<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="mr40 mt20">
                    <router-link to="/list-product">
                        <img src="../../assets/icons/back.svg">
                    </router-link>
                </div>
                <div>
                    <h1 class="m0">Add Product</h1>
                    <p class="mt5 mb20 tc-green">Make your product looking good for customer</p>
                </div>
            </div>
            <hr class="uline-grey">
            <div class="mt50 row">
                <div class="w20">
                    <label class="form-label">Product Image</label>
                </div>
                <div class="w80">
                    <div class="form-image">
                        <label for="img"><img src="../../assets/icons/image-solid.svg" style="width: 100px;"></label>
                        <input id="img" type="file" accept="image/*" style="display: none;">
                    </div>
                </div>
            </div>
            <div class="mt30 row">
                <div class="w20">
                    <label class="form-label">Product Code</label>
                </div>
                <div class="w80 p-relative">
                    <input v-model="product_code" @input="countProductCode" class="form-text" type="text"
                        placeholder="Product Code" maxlength="8">
                    <div class="character-count text-bold"> | {{ product_code_length }} / 8</div>
                </div>
            </div>
            <div class="mt30 row">
                <div class="w20">
                    <label class="form-label">Product Name</label>
                </div>
                <div class="w80 p-relative">
                    <input v-model="product_name" @input="countProductName" class="form-text" type="text" placeholder="Product Name" maxlength="20">
                    <div class="character-count text-bold"> | {{ product_name_length }} / 20</div>
                </div>
            </div>
            <div class="mt30 row">
                <div class="w20">
                    <label class="form-label">Product Description</label>
                </div>
                <div class="w80">
                    <textarea class="form-text-area" placeholder="Masukkan Deskripsi Produk" cols="30" rows="10"></textarea>
                </div>
            </div>
            <div class="mt30 row">
                <div class="w20">
                    <label class="form-label">Unit</label>
                </div>
                <div class="w80">
                    <input class="form-text" type="number" placeholder="Unit">
                </div>
            </div>
            <div class="mt30 row">
                <div class="w20">
                    <label class="form-label">Min Purchase</label>
                </div>
                <div class="w80">
                    <input class="form-text" type="number" placeholder="Masukkan Min Purchase">
                </div>
            </div>
            <div class="mt30 row">
                <div class="w20">
                    <label class="form-label">Max Purchase</label>
                </div>
                <div class="w80">
                    <input class="form-text" type="number" placeholder="Masukkan Max Purchase">
                </div>
            </div>
            <div class="mt30 row">
                <div class="w20">
                    <label class="form-label">Catergory</label>
                </div>
                <div class="w80">
                    <select class="form-select">
                        <option disabled selected>Pilih Catergory</option>
                        <option value="1">Electronic</option>
                        <option value="2">Furniture</option>
                        <option value="3">Clothing and Apparel</option>
                    </select>
                </div>
            </div>
            <div class="flex mt30">
                <router-link to="/list-product">
                    <button class="bt-submit-green">Add Product</button>
                </router-link>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'add-user',
    data() {
        return {
            product_code: '',
            product_code_length: 0,
            product_name: '',
            product_name_length: 0
        }
    },
    methods: {
        countProductCode() {
            this.product_code_length = this.product_code.length
        },
        countProductName() {
            this.product_name_length = this.product_name.length
        }
    }
}
</script>