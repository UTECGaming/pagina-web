<template>
    <div class="product">
        <div class="product-image">
            <img
                :src="require(
                    '../assets/' + data.images[slideIndex] + '.png'
                    )" alt="product"
            />
        </div>

        <div class="product-details">
            <div>
                <h1 class="product-name">
                    {{ data.names[slideIndex] }}
                </h1>

                <h1 class="price">
                    $<span class="product-price">
                        {{ data.prices[slideIndex] }}
                    </span>, <sup>99</sup>
                </h1>

                <div class="details">
                    <div class="options">
                        <b class="option-title">
                            {{ data.optionTitles[slideIndex] }}
                        </b>
                        <ul class="option-list">
                            <li
                                v-for="(option, index) in data.optionTitles[slideIndex]" :key="index"
                                class="option"
                            >
                                {{ option }}
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductDetails',
    props: {
        data: Object,
        slideIndex: Number,
        count: Number,
        active: Number,
    },
}
</script>

<style scoped>
.product {
    position: relative;
    z-index: 2;
    display: grid;
    grid-template-columns: 1fr 1fr;
    height: 100%;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: #103248;

    opacity: 1;
    transition: opacity 0.5s ease;
}

.product-details {
    display: flex;
    justify-content: flex-start;
    align-items: center;
}

.product-image {
    display: flex;
    justify-content: center;
    align-items: center;
}

.product-image img {
    width: 70%;
    filter: drop-shadow(0 0 3em rgba(0, 0, 0, 0.3));
}

.product h1 {
    font-size: 2.8em;
    margin: 0;
}

.product .price {
    font-weight: 300;
    margin: 0.2em 0;
}

.details {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin: 2em 0;
}

.product-option-title {
    margin-left: 0.5em;
}

.options {
    list-style: none;
    margin-left: 0.5em 0;
    padding: 0;
}

.options ul {
    list-style: none;
    margin: 0.5em 0;
    padding: 0;
}

.options ul li {
    display: inline-block;
    margin-right: 0.5em;
    padding: 0.5em;
    border-radius: 3em;
    cursor: pointer;
}

.option-active {
    border: 1px #12c141 solid;
}

@media screen and (max-width: 880px) {
    .product-details {
        justify-content: center;
    }
    .details {
        flex-direction: column;
    }
    .product {
        grid-template-columns: 1fr;
    }
    .product-image img {
        width: 50%;
    }
    .options {
        border-right: none;
        padding-right: 0;
    }
}
</style>