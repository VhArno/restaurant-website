<script setup lang="ts">
import AppButton from '@/components/atoms/AppButton.vue'
import AppModal from '@/components/organisms/AppModal.vue'
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const pictures = [
  '../../public/fish-dish1.jpg',
  '../../public/fish-dish2.jpg',
  '../../public/fish-dish3.jpg',
  '../../public/fish-dish4.jpg',
]

const router = useRouter()

const selectedPic = ref(pictures[0])
const isModalOpen = ref<boolean>(false)

const prevPic = () => {
  selectedPic.value = ''
}

const nextPic = () => {
  selectedPic.value = ''
}

const navigateTo = (route: string) => {
  router.push(route)
}

const openModal = () => {
  isModalOpen.value = true
}
</script>

<template>
  <section class="container">
    <div class="title-container">
      <div class="title-text">
        <svg class="curved-title" viewBox="0 0 500 150" xmlns="http://www.w3.org/2000/svg">
          <path id="curve" d="M50,100 Q250,10 450,100" fill="transparent" />
          <text>
            <textPath href="#curve" startOffset="50%" text-anchor="middle">Le Forel</textPath>
          </text>
        </svg>
        <h2>Visbar</h2>

        <div class="button-container">
          <AppButton @click="navigateTo('/menu')" type="outlined">Bekijk menu</AppButton>
          <AppButton @click="openModal" type="outlined">Reserveren</AppButton>
        </div>
      </div>

      <div class="title-pictures">
        <img src="../../public/fish-display2.avif" alt="head picture 2" />
        <img src="../../public/fish-display1.avif" alt="head picture 1" />
      </div>
    </div>

    <div class="about-container">
      <div class="about">
        <h2>Over Le Forel</h2>

        <p>
          Le Forel is een restaurant gespecialiseerd in verse vis uit het seizoen. Onze
          gepassioneerde chef Hessel Blok, die jarenlang ervaring heeft in het ontwikkelen van de
          fijnste visgerechten, heeft een menukaart samengesteld waar elke visliefhebber zijn of
          haar hart kan ophalen. U kunt bij Le Forel terecht voor de traditionele visgerechten, maar
          op de menukaart is ook ruimte voor spannende combinaties waarbij u de vingers bij aflikt.
        </p>

        <p>
          Ook zal er dagelijks verse vis van de markt binnen komen die we voor u op onze
          houtskoolgrill bereiden. Uiteraard bent u ook welkom voor een oester proeverij met een
          glas bubbels of een cocktail.
        </p>

        <div class="button-container">
          <AppButton @click="navigateTo('/menu')">Bekijk menu</AppButton>

          <AppButton @click="navigateTo('/wijn-kaart')">Wijnkaart</AppButton>
        </div>
      </div>

      <img src="../../public/fish-display.jpg" alt="fish dish displayed" />
    </div>

    <div class="pics-container">
      <!--<AppButton class="prev" type="filled" @click="prevPic">prev</AppButton>-->

      <div class="pictures">
        <img src="../../public/fish-dish1.jpg" alt="fish dish 1" />
        <img src="../../public/fish-dish2.jpg" alt="fish dish 2" />
        <img src="../../public/fish-dish3.jpg" alt="fish dish 3" />
        <img src="../../public/fish-dish4.png" alt="fish dish 4" />
      </div>

      <!--<AppButton class="next" type="filled" @click="nextPic">next</AppButton>-->
    </div>

    <AppModal v-if="isModalOpen" v-model:isVisible="isModalOpen"></AppModal>
  </section>
</template>

<style lang="css" scoped>
.container {
  .title-container {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    height: 45rem;

    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.425);
      z-index: 1;
    }

    .title-text {
      position: absolute;
      display: flex;
      flex-flow: column;
      align-items: center;
      gap: 2rem;
      text-align: center;
      color: white;
      z-index: 2;

      .curved-title {
        width: 100%;
        margin: 0 auto;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
      }

      .curved-title path {
        stroke: transparent;
        display: none;
      }

      .curved-title textPath {
        position: absolute;
        top: 100px;
        fill: #a7daee; /* Light blue text color */
        font-family: 'Playfair Display', serif;
        font-size: 5rem;
        letter-spacing: 3px;
        font-weight: bold;
        -webkit-text-stroke: 2px #d38900; /* Add proper border */
        text-stroke: 2px #d38900; /* Cross-browser fallback */
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4); /* Adds depth */
      }

      h2 {
        font-size: 1.5rem;
        font-weight: 300;
      }

      .button-container {
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
        gap: 2rem;

        button {
          border: 2px solid white;
          padding: 1rem 3rem;

          &:hover {
            background-color: white;
            color: black;
          }
        }
      }
    }

    .title-pictures {
      display: flex;
      flex-flow: row;
      width: 100%;
      z-index: 0;

      img {
        width: 50%;
        height: 45rem;
        object-fit: cover;
      }
    }
  }

  .about-container {
    width: 65%;
    display: flex;
    flex-flow: row;
    justify-content: space-between;
    align-items: center;
    margin: 4rem auto;
    gap: 10rem;

    .about {
      display: flex;
      flex-flow: column;
      gap: 2rem;
      min-width: 15rem;
    }

    .button-container {
      display: flex;
      flex-flow: row;
      gap: 1rem;
    }

    img {
      width: 20rem;
    }
  }

  .pics-container {
    display: flex;
    align-items: center;
    position: relative;

    button {
      position: absolute;
      height: fit-content;

      &:hover {
        cursor: pointer;
      }
    }

    .prev {
      left: 10px;
    }

    .next {
      right: 10px;
    }

    .pictures {
      display: flex;
      flex-flow: row;
      gap: 2rem;
      overflow-x: scroll;

      img {
        width: 30rem;
        height: 35rem;
        object-fit: cover;
      }

      /* Scrollbar styles */
      &::-webkit-scrollbar {
        height: 12px;
        background-color: #f5f5f5;
      }

      &::-webkit-scrollbar-thumb {
        background-color: #888;
        border-radius: 6px;
        border: 3px solid #f5f5f5;
      }

      &::-webkit-scrollbar-thumb:hover {
        background-color: #555;
      }

      &::-webkit-scrollbar-corner {
        background-color: transparent;
      }
    }
  }
}

@media (max-width: 56rem) {
  .container {
    .title-container {
      height: auto;

      .title-pictures {
        display: flex;
        flex-flow: column;
        width: 100%;

        img {
          width: 100%;
          height: 20rem;
          object-fit: cover;
        }
      }
    }

    .about-container {
      width: 85%;
      display: flex;
      flex-flow: column;
      justify-content: space-between;
      align-items: center;
      margin: 4rem auto;
      gap: 2rem;

      .about {
        display: flex;
        flex-flow: column;
        gap: 2rem;
        min-width: 15rem;
      }

      .button-container {
        display: flex;
        flex-flow: column;
        gap: 1rem;
      }

      img {
        display: none;
        width: 20rem;
      }
    }
  }
}
</style>
