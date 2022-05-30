<template>
  <!-- Home  -->
  <main class="home">
    <!-- Landing section  -->
    <section class="landing">
      <!-- Top  -->
      <div class="top">
        <!-- Bar  -->
        <span class="bar"></span>
        <!-- Sub title  -->
        <h3 class="sub-title">the history of</h3>
        <!-- Bar  -->
        <span class="bar"></span>
      </div>
      <!-- Main title  -->
      <div class="landing-title animate__animated animate__fadeInDownBig">
        <!-- Image  -->
        <img :src="logoImg" alt="title" />
      </div>
      <!-- Main image  -->
      <div
        v-if="!showTimeLine"
        class="landing-img animate__animated animate__fadeInUpBig"
      >
        <img
          :src="pizzaImg"
          class="animate__rotateIn animate__animated first-half"
          alt="Pizza image"
          @click="toggleTimeLine"
        />
      </div>
      <Timeline class="animate__animated" v-if="showTimeLine" />
    </section>
  </main>
  <!-- Home  -->
</template>

<script>
// Importing media assets needed

// Images
import logoImg from "../assets/images/logo.png";
import pizzaImg from "../assets/images/pizza.png";
// Components
import Timeline from "../components/Timeline.vue";

export default {
  name: "Home",
  components: { Timeline },
  data() {
    // Returning data
    return {
      showTimeLine: false,
      logoImg,
      pizzaImg,
    };
  },
  methods: {
    // This function will toggle timeline
    toggleTimeLine() {
      // Changing showTimeLine value
      this.showTimeLine = true;
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 20px;
  min-height: 100vh;
  padding-top: 50px;
  background: linear-gradient(78.84deg, #e63c01 3%, #fd8c00 96.8%);
  position: relative;
  .landing {
    padding: 0px 10px;
    .top {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 20px;
      .bar {
        display: block;
        width: 70px;
        height: 2px;
        background: #fff;
      }
      .sub-title {
        font-size: 1.5rem;
        text-transform: uppercase;
        color: #fff;
      }
    }
    .landing-title {
      max-width: 550px;
      margin: auto;
      animation-duration: 2s;
      img {
        width: 100%;
      }
    }
    .landing-img {
      max-width: 550px;
      margin: auto;
      animation-duration: 2s;
      position: relative;

      img {
        animation-duration: 2s;
        width: 100%;
        cursor: pointer;
        border-radius: 50%;
        transition: 0.3s ease-in-out;

        &:hover {
          filter: drop-shadow(5px 5px 10px #333);
        }
      }
    }
  }
}

// Media queries
@media only screen and (max-width: 550px) {
  .home {
    .landing {
      .top {
        .bar {
          display: block;
          width: 50px;
          height: 2px;
          background: #fff;
        }
        .sub-title {
          font-size: 1rem;
        }
      }
    }
  }
}
</style>
