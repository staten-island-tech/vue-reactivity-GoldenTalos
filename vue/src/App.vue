<template>
  <div id="app">
    <section id="inputs">
      <h1>Characters:</h1>

      <div id="team">
        <div id="characters">
          <div
            class="wish"
            v-for="(characterList, index) in characterList"
            :key="index"
          >
            <button @click="updateCharacter(index)">
              {{ characterList.food }}
            </button>
            <img class="image" :src="characterList.characterImage" />
            <p>${{ characterList.price }}</p>
          </div>
        </div>

        <div id="weapons">
          <div
            class="wish"
            v-for="(weaponsList, index) in weaponsList"
            :key="index"
          >
            <button @click="updateWeapon(index)">
              {{ weaponsList.drink }}
            </button>
            <img class="image" :src="weaponsList.weaponImage" />
            <p>${{ weaponsList.price }}</p>
          </div>
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
          <li class="info" v-for="price in primogems" :key="price">
            ${{ price }}
          </li>
        </ul>
      </div>
      <h3>Total Primogems: ${{ totalPrimogems }}</h3>
      <button class="delete-btn" @click="removeLastItem()">
        Delete previous order.
      </button>
      <button class="delete-btn" @click="removeAllItems()">
        Delete all orders.
      </button>
    </section>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      totalPrimogems: 0,
      selectedCharacters: 0,
      selectedWeapons: 0,
      characterList: [
        {
          character: "HuTao",
          characterImage: "./assets/hutao.jpg",
          price: 14400,
        },
        {
          character: "Kazuha",
          characterImage: "./assets/Kazuha.jpg",
          price: 14400,
        },
        {
          character: "Ganyu",
          characterImage: "./assets/ganyu.jpg",
          price: 14400,
        },
        {
          character: "Raiden Shogun",
          characterImage: "./assets/ei.jpg",
          price: 14400,
        },
        {
          character: "Ayaka",
          characterImage: "./assets/Ayaka.jpg",
          price: 14400,
        },
        {
          character: "Eula",
          characterImage: "./assets/eula.jpg",
          price: 14400,
        },
        {
          character: "Venti",
          characterImage: "./assets/Venti.jpg",
          price: 14400,
        },
        {
          character: "Xiao",
          characterImage: "./assets/Xiao.jpg",
          price: 14400,
        },
        {
          character: "Yelan",
          characterImage: "./assets/Yelan.jpg",
          price: 14400,
        },
        {
          character: "Zhongli",
          characterImage: "./assets/Zhongli.jpg",
          price: 14400,
        },
        {
          character: "Bennett",
          characterImage: "./assets/Bennett.jpg",
          price: 6400,
        },
        {
          character: "Fischl",
          characterImage: "./assets/Fischl.jpg",
          price: 6400,
        },
        {
          character: "Xiangling",
          characterImage: "./assets/Xiangling.jpg",
          price: 6400,
        },
        {
          character: "Xingqiu",
          characterImage: "./assets/xingqiu.jpg",
          price: 6400,
        },
        {
          character: "Sucrose",
          characterImage: "./assets/Sucrose.jpg",
          price: 6400,
        },
        {
          character: "Shinobu",
          characterImage: "./assets/Shinobu.jpg",
          price: 6400,
        },
        {
          character: "Diona",
          characterImage: "./assets/Diona.jpg",
          price: 6400,
        },
        {
          character: "Heizou",
          characterImage: "./assets/Heizou.jpg",
          price: 6400,
        },
      ],
      weaponsList: [
        {
          weapon: "Mistsplitter Reforged",
          weaponImage: "./assets/Mistsplitter.jpg",
          price: 25600,
        },
        {
          weapon: "Primordial Jade Cutter",
          weaponImage: "./assets/Primordial Jade Cutter.jpg",
          price: 25600,
        },
        {
          weapon: "Freedom-Sworn",
          weaponImage: "./assets/Freedom.png",
          price: 25600,
        },
        {
          weapon: "Aqua Simulacra",
          weaponImage: "./assets/Aqua.jpg",
          price: 25600,
        },
        {
          weapon: "Thundering Pulse",
          weaponImage: "./assets/Thundering.jpg",
          price: 25600,
        },
        {
          weapon: "Polar Star",
          weaponImage: "./assets/Polar.jpg",
          price: 25600,
        },
        {
          weapon: "Staff Of Homa",
          weaponImage: "./assets/homa.jpg",
          price: 25600,
        },
        {
          weapon: "Englufing Lightning",
          weaponImage: "./assets/Lightning.png",
          price: 25600,
        },
        {
          weapon: "Primoridal Jade Winged-Spear",
          weaponImage: "./assets/Primoridal Jade Spear.jpg",
          price: 25600,
        },
        {
          weapon: "Skyward Atlas",
          weaponImage: "./assets/Skyward.jpg",
          price: 25600,
        },
        {
          weapon: "Kagura's Verity",
          weaponImage: "./assets/Kagura.jpg",
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
      this.totalPrimogems.push(this.characterList[index].price);
      this.subtotal = this.subtotal + this.characterList[index].price;
    },
    updateWeapon(index) {
      this.wishes.push(this.weaponsList[index].weapon);
      this.totalPrimogems.push(this.weaponsList[index].price);
      this.subtotal = this.subtotal + this.weaponsList[index].price;
    },
    removeAllItems() {
      this.wishes = [];
      this.primogems = [];
      this.totalPrimogems = 0;
    },
    removeLastCItem() {
      this.wishes.splice(this.wishes.indexOf(characterList), 1);
    },
    removeLastWItem() {
      this.wishes.splice(this.wishes.indexOf(weaponList), 1);
    },
  },
};
</script>

<style scoped></style>
