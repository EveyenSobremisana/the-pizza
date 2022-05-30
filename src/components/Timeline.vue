<template>
  <!-- Timeline  -->
  <section class="timeline">
    <!-- Pizza top half -->
    <div class="pizza-top">
      <img :src="pizzaUpHalfImg" rel="preload" alt="Pizza half" />
    </div>
    <!-- Timeline content  -->
    <div
      v-if="show"
      class="timeline-content animate__animated animate__slideInRight"
    >
      <h1 class="timeline-title">the origin story of pizza</h1>
      <!-- History wraper  -->
      <div class="history-wraper">
        <!-- Top  -->
        <div class="top">
          <!-- Box  -->
          <div
            v-for="(item, index) in topHistory"
            :key="index"
            :class="'box-' + Number(index + 1)"
          >
            <!-- Icon  -->
            <div class="icon"><img :src="item.icon" alt="icon" /></div>
            <!-- Text  -->
            <div class="text">
              <!-- Box title  -->
              <h4>{{ item.title }}</h4>
              <!-- Box text  -->
              <p>{{ item.text }}</p>
            </div>
          </div>
        </div>
        <!-- Hr  -->
        <hr class="hr" />
        <!-- Bottom  -->
        <div class="bottom">
          <!-- Box  -->
          <div
            v-for="(item, index) in bottomHistory"
            :key="index"
            :class="'box-' + Number(index + 1)"
          >
            <!-- Icons  -->
            <div class="icon"><img :src="item.icon" alt="icon" /></div>
            <!-- Text  -->
            <div class="text">
              <!-- Box title  -->
              <h4>{{ item.title }}</h4>
              <!-- Box text  -->
              <p>{{ item.text }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Pizza bottom half  -->
    <div class="pizza-bottom">
      <img
        :src="pizzaDownHalfImg"
        class="animate__animated animate__fadeOutDownBig"
        alt="Pizza half"
        rel="preload"
      />
    </div>
  </section>
  <!-- Timeline  -->
</template>

<script>
// Importing media assets needed

// Images
import pizzaUpHalfImg from "../assets/images/pizza-up-half.png";
import pizzaDownHalfImg from "../assets/images/pizza-down-half.png";
import icon1 from "../assets/images/Icon-1.svg";
import icon2 from "../assets/images/Icon-2.svg";
import icon3 from "../assets/images/Icon-3.svg";
import icon4 from "../assets/images/Icon-4.svg";
import icon5 from "../assets/images/Icon-5.svg";
import icon6 from "../assets/images/Icon-6.svg";
import icon7 from "../assets/images/Icon-7.svg";
import icon8 from "../assets/images/Icon-8.svg";

export default {
  name: "Timeline",
  data() {
    return {
      show: false,
      topHistory: [
        {
          title: "79 A.D",
          text: "MT. Vesuvius erupted in Pompeii. Excavation revealed evidence of flat breads being baked with tools that resemble modern pizza supplies",
          icon: icon1,
        },
        {
          title: "1880",
          text: "Pizza was invented by Thomas Alva Edison in Menlo Park",
          icon: icon7,
        },
        {
          title: "1905",
          text: "Gennaro Lombardi opened the first true U.S. pizzeria",
          icon: icon5,
        },
        {
          title: "1958",
          text: "Pizza Hut was founded and has since become the world’s largest pizza franchise",
          icon: icon3,
        },
      ],
      bottomHistory: [
        {
          title: "1522",
          text: "Tomatoes brought from the new world were thought to be poisonous. Later, Naples managed to combine them with flat bread to make the earliest form of pizza in Italy ",
          icon: icon8,
        },
        {
          title: "1889",
          text: "The first time cheese was used in pizza when a chef made a pizza for Queen Margarita using tomato, cheese and basil to show the colors of the Italian Flag",
          icon: icon6,
        },
        {
          title: "1943",
          text: "The invention of Chicago style deep-dish pizza",
          icon: icon4,
        },
        {
          title: "today",
          text: "Pizza is one of most popular foods worldwide, with 252 million pound of pizza consumed everyday",
          icon: icon2,
        },
      ],
      pizzaUpHalfImg,
      pizzaDownHalfImg,
      icon1,
      icon2,
      icon3,
      icon4,
      icon5,
      icon6,
      icon7,
      icon8,
    };
  },
  //   Life cycle hook
  mounted() {
    //   Creating timeout
    setTimeout(() => {
      // Changing show value
      this.show = true;
      // Removing class from bottom half of pizza
      document
        .querySelector(".pizza-bottom  > img")
        .classList.remove("animate__fadeOutDownBig");
    }, 1000);
  },
};
</script>

<style lang="scss" scoped>
.timeline {
  .pizza-top,
  .pizza-bottom {
    max-width: 550px;
    margin: auto;
    img {
      width: 100%;
      animation-duration: 4s;
      filter: drop-shadow(5px 5px 10px #333);
    }
  }
  .timeline-content {
    background: #fff;
    margin-top: -5px;
    animation-duration: 2s;
    border-radius: 5px;
    display: flex;
    align-items: center;
    .timeline-title {
      font-size: 2rem;
      text-transform: uppercase;
      color: red;
      writing-mode: vertical-rl; // to make writing orientation vertical
      padding-left: 2em;
      background: #fff;
      z-index: 2;
    }
    .history-wraper {
      background: #fff;
      display: flex;
      flex-direction: column;
      gap: 5px;
      overflow-x: auto;
      max-width: 1440px;
      margin: auto;
      padding: 70px;
      .top {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr; //fr means fractional unit
        grid-template-rows: 1fr 1fr;
        grid-gap: 10px;

        .box-1 {
          grid-column: 1 / 2;
          grid-row: 1 / 3;
          align-self: end;
          display: flex;
          gap: 10px;
          min-width: 300px;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::after {
              content: "";
              display: block;
              width: 2px;
              height: 100px;
              background: red;
            }
          }
          .text {
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
        .box-2 {
          grid-column: 2 / 3;
          grid-row: 1 / 3;
          align-self: start;
          display: flex;
          gap: 10px;
          min-width: 300px;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::after {
              content: "";
              display: block;
              width: 2px;
              height: 210px;
              background: red;
            }
          }
          .text {
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
        .box-3 {
          grid-column: 3 / 4;
          grid-row: 1 / 3;
          align-self: end;
          display: flex;
          gap: 10px;
          min-width: 300px;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::after {
              content: "";
              display: block;
              width: 2px;
              height: 100px;
              background: red;
            }
          }
          .text {
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
        .box-4 {
          grid-column: 4 / 5;
          grid-row: 1 / 3;
          align-self: start;
          display: flex;
          gap: 10px;
          min-width: 300px;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::after {
              content: "";
              display: block;
              width: 2px;
              height: 210px;
              background: red;
            }
          }
          .text {
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
      }
      .bottom {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr;
        grid-gap: 10px;
        margin-left: 100px;

        .box-1 {
          grid-column: 1 / 2;
          grid-row: 1 / 3;
          align-self: start;
          display: flex;
          gap: 10px;
          min-width: 300px;
          position: relative;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::before {
              content: "";
              display: block;
              width: 2px;
              height: 100px;
              background: red;
            }
          }
          .text {
            position: absolute;
            width: 80%;
            left: 70px;
            top: 65%;
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
        .box-2 {
          grid-column: 2 / 3;
          grid-row: 1 / 3;
          align-items: baseline;
          display: flex;
          gap: 10px;
          min-width: 300px;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::before {
              content: "";
              display: block;
              width: 2px;
              height: 210px;
              background: red;
            }
          }
          .text {
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
        .box-3 {
          grid-column: 3 / 4;
          grid-row: 1 / 3;
          align-self: start;
          display: flex;
          gap: 10px;
          min-width: 300px;
          position: relative;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::before {
              content: "";
              display: block;
              width: 2px;
              height: 100px;
              background: red;
            }
          }
          .text {
            position: absolute;
            width: 80%;
            left: 70px;
            top: 65%;
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
        .box-4 {
          grid-column: 4 / 5;
          grid-row: 1 / 3;
          align-items: baseline;
          display: flex;
          gap: 10px;
          min-width: 300px;
          .icon {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
              width: 50px;
            }
            &::before {
              content: "";
              display: block;
              width: 2px;
              height: 210px;
              background: red;
            }
          }
          .text {
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
      }
    }
  }
}
.hr {
  border-top: 2px solid red;
  width: 100%;
  max-width: 1440px;
  position: absolute;
  margin: auto;
  top: 332px;
  left: 0;
  right: 0;
}

// Media queries
@media only screen and (max-width: 550px) {
  .timeline {
    .timeline-content {
      display: block;
      .timeline-title {
        font-size: 1.5rem;
        text-transform: uppercase;
        color: red;
        writing-mode: horizontal-tb;
        text-align: center;
      }
      .history-wraper {
        padding: 40px 10px;
        gap: 0;
        .top {
          display: flex;
          flex-direction: column;
          gap: 0;
          .box-3,
          .box-1,
          .box-2,
          .box-4 {
            align-self: auto;
          }
          .icon {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            gap: 0;
            img {
              width: 50px;
            }
            &::after {
              content: "";
              display: block;
              width: 2px;
              height: 80px !important;
              background: red;
            }
          }
          .text {
            h4 {
              font-size: 1.2rem;
              text-transform: capitalize;
              padding: 10px 0px;
            }
            p {
              font-size: 0.9rem;
              color: #555;
              line-height: 1.4rem;
            }
          }
        }
        .bottom {
          display: flex;
          flex-direction: column;
          margin: 0;
          align-self: auto;
          gap: 0;
          .box-1,
          .box-2,
          .box-3,
          .box-4 {
            align-self: auto;
            display: flex;
            align-items: flex-start;
            position: relative;
            gap: 10px;
            .icon {
              display: flex;
              flex-direction: column;
              align-items: center;
              gap: 0;
              img {
                width: 50px;
              }
              &::after {
                content: "";
                display: block;
                width: 2px;
                height: 100px !important;
                background: red;
              }
              &::before {
                content: "";
                display: none;
              }
            }
            .text {
              position: relative;
              width: 100%;
              left: 0;
              top: 0;
              h4 {
                font-size: 1.2rem;
                text-transform: capitalize;
                padding: 10px 0px;
              }
              p {
                font-size: 0.9rem;
                color: #555;
                line-height: 1.4rem;
              }
            }
          }
        }
      }
    }
  }
  .hr {
    display: none;
  }
}
</style>
