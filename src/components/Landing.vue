<template>
  <div class="hero">
    <navbar />
    <ul class="slider">
      <li class="slider-item" v-for="(item, index) in sliderItems" :key="index">
        <img :src="require(`@/assets/images/${item.image}`)" class="slider-item-image" :alt="item.image">
        <div class="slider-item-des">
          <h2 class="title">{{ item.title }}</h2>
          <p class="des">
            {{ item.des }}
          </p>
          <button class="shop-now">
            SHOP NOW
            <svg width="40" height="12" xmlns="http://www.w3.org/2000/svg"><path d="M34.05 0l5.481 5.527h.008v.008L40 6l-.461.465v.063l-.062-.001L34.049 12l-.662-.668 4.765-4.805H0v-1h38.206l-4.82-4.86L34.05 0z" fill="#000" fill-rule="nonzero"/></svg>
          </button>
        </div>
        <div class="slider-navigation">
          <button class="slider-navigation-btn" @click="navigateLeft">
            <svg width="14" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M13 0L1 12l12 12" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>
          </button>
          <button class="slider-navigation-btn" @click="navigateRight">
            <svg width="14" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M1 0l12 12L1 24" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>
          </button>
        </div>
      </li>
    </ul>
    <div class="about">
      <div class="about-image">
        <img src="@/assets/images/image-about-dark.jpg" alt="image-about-dark">
      </div>
      <div class="about-des">
        <h3 class="title">ABOUT OUR FURNITURE</h3>
          <p class="des">
            Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.
          </p>
      </div>
      <div class="about-image">
        <img src="@/assets/images/image-about-light.jpg" alt="image-about-dark">
      </div>
    </div>
  </div>

</template>

<script>
import Navbar from './Navbar.vue';
export default {
  components: { Navbar },
  data: () => ({
    sliderItems: [
      {
        image: "desktop-image-hero-1.jpg",
        title: 'Discover innovative ways to decorate',
        des: `We provide unmatched quality, comfort, and style for property
          owners across the country. Our experts combine form and function
          in bringing your vision to life. Create a room in your own style
          with our collection and make your property a reflection of you
          and what you love.`
      },
      {
        image: "desktop-image-hero-2.jpg",
        title: 'Discover innovative ways to decorate',
        des: `We provide unmatched quality, comfort, and style for property
          owners across the country. Our experts combine form and function
          in bringing your vision to life. Create a room in your own style
          with our collection and make your property a reflection of you
          and what you love.`
      },
      {
        image: "desktop-image-hero-3.jpg",
        title: 'Discover innovative ways to decorate',
        des: `We provide unmatched quality, comfort, and style for property
          owners across the country. Our experts combine form and function
          in bringing your vision to life. Create a room in your own style
          with our collection and make your property a reflection of you
          and what you love.`
      },
    ],
    currentSlide: 0
  }),
  methods: {
    navigateRight() {
      let slides = document.querySelectorAll(".slider-item")
      this.currentSlide = (this.currentSlide + 1) % slides.length;
      let item = 0;
      Array.from(slides).forEach((slide) => {
        slide.style.transform = `translateX(-${this.currentSlide * 100}%)`;
      });
    },
    navigateLeft() {
      let slides = document.querySelectorAll(".slider-item")
      this.currentSlide = (this.currentSlide - 1 + slides.length) % slides.length;
      let item = 0;
      Array.from(slides).forEach((slide) => {
        slide.style.transform = `translateX(-${this.currentSlide * 100}%)`;
      });
    }
  },
  mounted() {
    setInterval(
      () => this.navigateRight(),
      3500
    )
  }
}
</script>

<style lang="scss" scoped>
.hero {
  display: flex;
  flex-wrap: wrap;
  overflow: hidden;
  max-height: 100vh;

  & .slider {
    display: flex;
    flex-direction: row;
    position: relative;

    & .slider-item {
      display: flex;
      flex: 1 0 100vw;
      width: 100vw;
      transform: translateX(0%);

      & .slider-item-image {
        width: 60vw;
        height: 66vh;
      }

      & .slider-item-des {
        padding: 4vw 5vw;
        width: 30vw;

        & .title {
          font-weight: 600;
          font-size: 1.6em;
        }

        & .des {
          color: $dark-gray;
          font-size: .7em;
          line-height: 160%;
        }

        & .shop-now {
          background: none;
          padding: 0;
          letter-spacing: 14px;
          font-size: .75em;
          margin-top: 30px;

          &:hover {
            color: $dark-gray;

            & path {
              fill: $dark-gray;
            }
          }
        }
      }
    }

    & .slider-navigation {
      position: absolute;
      left: 60vw;
      bottom: 0;

      & .slider-navigation-btn {
        background-color: black;
        padding: 20px 25px;

        &:hover {
          background-color: $very-dark-gray;
        }
      }
    }
  }

  & .about {
    display: flex;
    flex-wrap: wrap;

    & .about-image {
      width: 30%;

      & img {
        height: 100%;
        width: 100%;
        object-fit: cover;
      }
    }

    & .about-des {
      width: calc(40% - 8vw);
      padding: 3.8vw 4vw 0;

        & .title {
          font-weight: 700;
          font-size: .8em;
          letter-spacing: .4vw;
        }

        & .des {
          color: $dark-gray;
          font-size: .7em;
          line-height: 140%;
          text-align: justify;
        }
    }
  }
}
</style>