<template>
  <div id="app">
    <section id="inputs">
      <h1>Characters:</h1>

      <div id="team">
        <div id="characters">
          <card
            class="wish"
            v-for="(characterList, index) in characterList"
            @updateCharacter="updateCharacter(index)"
            :key="index"
            :image="characterList.characterImage"
            :name="characterList.character"
            :price="characterList.price"
          ></card>
        </div>
        <h1>Weapons:</h1>
        <div id="weapons">
          <card2
            class="wish"
            v-for="(weaponsList, index) in weaponsList"
            @updateWeapon="updateWeapon(index)"
            :key="index"
            :images="weaponsList.weaponImage"
            :wname="weaponsList.weapon"
            :wprice="weaponsList.price"
          ></card2>
        </div>
      </div>
    </section>

    <section id="list">
      <h2>Your Wishes:</h2>
      <div id="wishesInfo">
        <ul class="list2">
          <li class="info" v-for="wishes in wishes" :key="wishes">
            {{ wishes }}
          </li>
        </ul>
        <ul class="list">
          <h2>Prices:</h2>
          <li class="info" v-for="price in primogems" :key="price">
            ${{ price }}
          </li>
        </ul>
      </div>
      <h3>Total Primogems: {{ totalPrimogems }}</h3>
      <button class="delete-btn" @click="removeLastItem()">
        Delete previous wish.
      </button>
      <button class="delete-btn" @click="removeAllItems()">
        Delete all wishes.
      </button>
    </section>
  </div>
</template>

<script>
import Card from "./components/Card.vue";
import Card2 from "./components/Card2.vue";

import hutao from "./assets/hutao.jpg";
import kazuha from "./assets/Kazuha.jpg";
import ganyu from "./assets/ganyu.jpg";
import ei from "./assets/ei.jpg";
import ayaka from "./assets/Ayaka.jpg";
import eula from "./assets/eula.jpg";
import venti from "./assets/Venti.jpg";
import yelan from "./assets/Yelan.jpg";
import zhongli from "./assets/Zhongli.jpg";
import bennett from "./assets/Bennett.jpg";
import xiao from "./assets/Xiao.jpg";
import fischl from "./assets/Fischl.jpg";
import xiang from "./assets/Xiangling.jpg";
import xing from "./assets/xingqiu.jpg";
import rose from "./assets/Sucrose.jpg";
import shinobu from "./assets/Shinobu.jpg";
import cat from "./assets/Diona.jpg";
import heizou from "./assets/Heizou.jpg";
import mist from "./assets/Mistsplitter.jpg";
import cutter from "./assets/Primordial Jade Cutter.jpg";
import freedom from "./assets/Freedom.png";
import aqua from "./assets/Aqua.jpg";
import pulse from "./assets/Thundering.jpg";
import polar from "./assets/Polar.jpg";
import homa from "./assets/homa.jpg";
import lightning from "./assets/Lightning.png";
import jadespear from "./assets/Primoridal Jade Spear.jpg";
import skyward from "./assets/Skyward.jpg";
import kagura from "./assets/Kagura.jpg";

export default {
  name: "App",
  components: {
    Card2,
    Card,
  },
  data() {
    return {
      totalPrimogems: 0,
      selectedCharacters: 0,
      selectedWeapons: 0,
      characterList: [
        {
          character: "HuTao",
          characterImage: hutao,
          price: 14400,
        },
        {
          character: "Kazuha",
          characterImage: kazuha,
          price: 14400,
        },
        {
          character: "Ganyu",
          characterImage: ganyu,
          price: 14400,
        },
        {
          character: "Raiden Shogun",
          characterImage: ei,
          price: 14400,
        },
        {
          character: "Ayaka",
          characterImage: ayaka,
          price: 14400,
        },
        {
          character: "Eula",
          characterImage: eula,
          price: 14400,
        },
        {
          character: "Venti",
          characterImage: venti,
          price: 14400,
        },
        {
          character: "Xiao",
          characterImage: xiao,
          price: 14400,
        },
        {
          character: "Yelan",
          characterImage: yelan,
          price: 14400,
        },
        {
          character: "Zhongli",
          characterImage: zhongli,
          price: 14400,
        },
        {
          character: "Bennett",
          characterImage: bennett,
          price: 6400,
        },
        {
          character: "Fischl",
          characterImage: fischl,
          price: 6400,
        },
        {
          character: "Xiangling",
          characterImage: xiang,
          price: 6400,
        },
        {
          character: "Xingqiu",
          characterImage: xing,
          price: 6400,
        },
        {
          character: "Sucrose",
          characterImage: rose,
          price: 6400,
        },
        {
          character: "Shinobu",
          characterImage: shinobu,
          price: 6400,
        },
        {
          character: "Diona",
          characterImage: cat,
          price: 6400,
        },
        {
          character: "Heizou",
          characterImage: heizou,
          price: 6400,
        },
      ],
      weaponsList: [
        {
          weapon: "Mistsplitter Reforged",
          weaponImage: mist,
          price: 25600,
        },
        {
          weapon: "Primordial Jade Cutter",
          weaponImage: cutter,
          price: 25600,
        },
        {
          weapon: "Freedom-Sworn",
          weaponImage: freedom,
          price: 25600,
        },
        {
          weapon: "Aqua Simulacra",
          weaponImage: aqua,
          price: 25600,
        },
        {
          weapon: "Thundering Pulse",
          weaponImage: pulse,
          price: 25600,
        },
        {
          weapon: "Polar Star",
          weaponImage: polar,
          price: 25600,
        },
        {
          weapon: "Staff Of Homa",
          weaponImage: homa,
          price: 25600,
        },
        {
          weapon: "Englufing Lightning",
          weaponImage: lightning,
          price: 25600,
        },
        {
          weapon: "Primoridal Jade Winged-Spear",
          weaponImage: jadespear,
          price: 25600,
        },
        {
          weapon: "Skyward Atlas",
          weaponImage: skyward,
          price: 25600,
        },
        {
          weapon: "Kagura's Verity",
          weaponImage: kagura,
          price: 25600,
        },
      ],
      wishes: [],
      primogems: [],
    };
  },
  methods: {
    updateCharacter(index) {
      this.wishes.push(this.characterList[index].character);
      this.primogems.push(this.characterList[index].price);
      this.totalPrimogems =
        this.totalPrimogems + this.characterList[index].price;
    },
    updateWeapon(index) {
      this.wishes.push(this.weaponsList[index].weapon);
      this.primogems.push(this.weaponsList[index].price);
      this.totalPrimogems = this.totalPrimogems + this.weaponsList[index].price;
    },
    removeAllItems() {
      this.wishes = [];
      this.primogems = [];
      this.totalPrimogems = 0;
    },
    removeLastItem() {
      if (this.wishes.length !== 0) {
        this.totalPrimogems =
          this.totalPrimogems - this.primogems[this.primogems.length - 1];
        this.wishes.pop();
        this.primogems.pop();
      }
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  display: flex;
  flex-direction: row;
}
#inputs {
  margin-left: 2px;
}
.image {
  height: 29rem;
  width: 6rem;
  object-fit: cover;
}
#weapons,
#characters {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  margin: 2rem;
  justify-content: space-around;
  align-content: space-around;
  width: 57vw;
}
.wish {
  display: flex;
  flex-direction: column;
  margin-left: 20px;
  width: 13.7vw;
}
#characters,
#weapons {
  display: flex;
  flex-direction: row;
  margin: 2rem;
}
section {
  display: flex;
  align-items: center;
  flex-direction: column;
}
#list {
  margin: 1rem 5rem;
  height: auto;
  width: 39vw;
  margin-left: -96px;
  position: sticky;
  top: 0;
  list-style: none;
}
.delete-btn {
  margin-bottom: 10px;
}
</style>
