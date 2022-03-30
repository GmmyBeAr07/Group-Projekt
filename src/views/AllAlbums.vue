<template>

<section class="muso">
   
<h1 class="section-head">
            <span class="heading">Explore</span>
            <span class="sub-heading">Our Beautiful Albums</span>
        </h1>

<div class="wrap" v-if="products">
    <div v-for="(product, index) of products" :key="index.id">
    <div class="card">
      <div class="card__inner">
        <div class="card___imagen"><img :src="product.img" alt="" width="250" height="250"></div>
        <div class="card__info">
          <h3>{{ product.title }}</h3>
          <p>{{ product.artist }}</p>
          <p>{{ product.category }}</p>
          <p>R {{ product.price }}</p>
          <a href="#" class="btn btn-gradient">ADD TO CART</a>
          <a href="#" class="btn btn-gradient">UPDATE</a>
        </div>
      </div>
    </div>
  </div>
</div>

          
</section>
</template>

<script>
export default {
    data(){
        return{
            products: null
        }
    },
     mounted() {
      fetch("https://full-proj.herokuapp.com/products", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        
   
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.products = json;
          console.log(json)
          
        })  
  },

}
</script>

<style >
.muso{
      background: url(https://wallpapercave.com/dwp1x/4c8xmGs.jpg) ;


}
:root{
  --dark-color: #2d2c2c;
  --purple-solid:#350a4f;
  --purple-transparent: rgba(53, 10, 79, .7);

  --purple-transparent-alt: rgba(53, 10, 79, .5);
  --purple-light: #8f50fb;
  --yellow-solid:#fa9e2c;
  --gradient-color: linear-gradient(to right, var(--yellow-solid), var(--purple-light));

  --gradient-color-alt: linear-gradient(to right, var(--purple-light, var(--yellow-solid)));
}
.hero::before{
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: inherit;
  height: inherit;
  background-color: var(--purple-transparent-alt);
  z-index: -1;
}


.wrap {
    width: 100%;
    display: flex;
    justify-content:revert;
    flex-wrap: wrap;
    }

.card {
  margin: 22px;
  box-shadow: 10px 5px 5px rgba(0, 0, 0, 0.418);
  border-bottom-right-radius: 44px;
  border-bottom-left-radius: 44px;
  border-top-right-radius: 44px;
  border-top-left-radius: 44px;
  position: relative;
  transition: 0.5s ease-in-out;
}

.card:hover{
    transform: translateY(15px);
}

.card:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    display: block;
    width: 100%;
    height: 244px;
    background: var(--color-navy);
    border-top-right-radius: 44px;
    border-top-left-radius: 44px;
    transition: 0.5s all;
    opacity: 0;

}

.card:hover::before {
    opacity: 1;
}


.card__imagen{
    width: 100%;
    height: 100px;
}

.card__imagen > img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.card__info {
    font-size: 0.8rem;
    font-family: var(--font-sans);
    padding: 1rem 3rem 0rem 3rem;
    width: 100%;
    height: 10rem;
    line-height: 1.5;
    background-color: var(--color-navy-opaque);
    color: var(--color-light);
    border-bottom-right-radius: 44px;
    border-bottom-left-radius: 44px;
}

.card__info p{
    font-weight: bold;
    margin-bottom: 1rem;
}

.button {
    font-style: var(--font-sans);
    text-decoration: none;
    color: var(--color-light);
    background-color: black;
    padding: 0.6em 4em;
    border-radius: 15px;
    font-weight: bold;
    margin-bottom: 1em;
}

</style>