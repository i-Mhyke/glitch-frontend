<template>
  <div class="header">
    <div class="heading">
      <h1>{{ apiData.name }}</h1>
    </div>

    <div class="img-box">
      <img
        src="../assets/main-img.png"
        alt="Header Image"
        width="300"
        class="header-img"
      />
    </div>

    <div class="nav">
      <a href="#">Home</a>
      <a href="#">About</a>
      <img src="../assets/head-shot.jpg" class="img-headshot" />
      <a href="#">Gallery</a>
      <a href="#">Contact</a>
    </div>

    <div class="side-icons">
      <a :href="'http://www.instagram.com/' + apiData.social_media?.instagram">
        <span
          class="iconify"
          data-inline="false"
          data-icon="simple-icons:instagram"
          style="font-size: 35px;color: #ffffff"
        ></span>
      </a>
      <a :href="'http://www.twitter.com/' + apiData.social_media?.twitter">
        <span
          class="iconify"
          data-inline="false"
          data-icon="fa-brands:twitter-square"
          style="font-size: 35px;color: #ffffff"
        ></span>
      </a>
      <a
        :href="'http://www.snapchat.com/add/' + apiData.social_media?.snapchat"
      >
        <span
          class="iconify"
          data-inline="false"
          data-icon="fa:snapchat-square"
          style="font-size: 35px;color: #ffffff"
        ></span>
      </a>
      <a :href="'mailto:' + apiData.social_media?.email">
        <span
          class="iconify"
          data-inline="false"
          data-icon="fluent:mail-24-filled"
          style="font-size: 35px;color: #ffffff"
        ></span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      apiData: {},
      menuOpen: false,
    };
  },

  mounted() {
    this.getData();
  },

  methods: {
    getData() {
      fetch("https://hirng-x2021.glitch.me/api")
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          this.apiData = data;
          console.log(this.apiData);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.header {
  margin: 0;
  display: flex;
  align-content: center;
  flex-direction: column;

  .heading {
    padding-top: 2rem;
    h1 {
      color: white;
      margin: 0;
      padding-left: 4rem;
      letter-spacing: 7px;
    }
  }
  .img-box {
    width: 90%;
    max-width: 540px;
    margin: 2rem auto;
    border-radius: 0px;
    background: #ca2b65;
    box-shadow: -20px -20px 60px#8f0b3a, 20px 20px 60px #e83174;
    padding: 0;
  }

  .nav {
    display: flex;
    justify-content: center;
    margin-left: 4rem;

    .img-headshot {
      width: 100px;
      border-radius: 50%;
      border: 1px solid #c4c4c4;
      animation: FadeIn 1s linear;
      animation-fill-mode: both;
      animation-delay: 0.5s;
    }

    a {
      color: white;
      letter-spacing: 5px;
      padding-bottom: 5px;
      border: 1px solid transparent;
      text-decoration: none;
      margin: 0 3rem;
      font-size: 1rem;
      justify-self: center;
      align-self: center;
      text-transform: uppercase;
      font-family: "Noto Sans KR", sans-serif;
      animation: FadeIn 0.2s linear;
      animation-fill-mode: both;
      transition: 500ms all;

      &:hover {
        border-bottom: 1px solid white;
      }
    }
  }
  .side-icons {
    display: flex;
    flex-direction: column;
    justify-content: right;
    position: fixed;
    right: 0;
    top: 45%;
    transform: translate(-50%, -50%);

    a {
      margin: 0.5rem 0;
      transition: all 0.2s ease-in-out;

      svg {
        animation: FadeIn 0.7s linear;
        animation-fill-mode: both;
      }

      &:nth-child(1) svg {
        animation-delay: 0.5s;
      }
      &:nth-child(2) svg {
        animation-delay: 1s;
      }
      &:nth-child(3) svg {
        animation-delay: 1.5s;
      }
      &:nth-child(4) svg {
        animation-delay: 2s;
      }

      &:hover {
        transform: scale(1.2);
      }
    }
  }

  @keyframes FadeIn {
    0% {
      opacity: 0;
      transform: scale(0.1);
    }

    85% {
      opacity: 1;
      transform: scale(1.05);
    }
    100% {
      transform: scale(1);
    }
  }
}
@media (max-width: 992px) {
  .header {
    .heading {
      h1 {
        font-size: 1.1rem;
      }
    }
    .nav {
      a {
        font-size: 0.8rem;
        letter-spacing: 3px;
      }
    }
    .side-icons {
      a {
        svg {
          font-size: 25px !important;
        }
      }
    }
  }
}
@media (max-width: 779px) {
  .header {
    .heading {
      h1 {
        padding: 0;
      }
      .menu {
        display: block;
      }
    }
    .nav {
      overflow: hidden;
      overflow-x: scroll;
      margin: 0;
      padding: 2rem;
      -ms-overflow-style: none;
      scrollbar-width: none;

      &::-webkit-scrollbar {
        display: none;
      }
    }
  }
}

</style>
