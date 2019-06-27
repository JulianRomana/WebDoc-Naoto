<template>
  <div class="enfantMiracle__wrapper">
    <h1>{{arrayName}}</h1>
    <figure>
      <img :src="arrayImage" alt>
      <figcaption>
        <p>
          Ce petit garçon est le fils de l'homme le plus irradié du Japon.
          <br>Son destin est celui d’un moine guerrier. Naoto Matsumura vit en ermite, à moins de 12 kilomètres des réacteurs de la centrale de Fukushima Daiichi. Il se lève à l’aube pour allumer un poêle à mazout et se préparer un petit déjeuner frugal, constitué de natto – du soja fermenté – et de riz blanc. Du café soluble est son seul luxe.
          <br>
          <br>Mais il a rencontré Akiko et toute sa vie en a été transformée. C’était au cours d’une conférence à Tokyo, l’été 2012.« J’ai d’abord pensé que Naoto était un vieil homme, raconte Akiko, parce que ses cheveux étaient complètement blancs. Il évoquait sa vie quotidienne à Tomioka avec beaucoup d’humour. Je ne suis pas immédiatement tombée amoureuse, car je pensais qu’avec ses cheveux blancs il avait plus de 70 ans. Mais j’ai été fascinée par son récit. J’ai pensé que je pourrais l’aider. En septembre 2012, je suis allée pour la première fois dans sa ferme ; j’avais peur des radiations, bien sûr, mais aussi du désert humain et des villes en ruine. Mais j’ai découvert la première qualité de Naoto, sa générosité envers les animaux. » Akiko a une voix douce lorsqu’elle parle japonais, plus affirmée en anglais. Cette ancienne guide touristique est parfaitement bilingue.
          <br>
          <br>Pour le mariage, le 4 avril 2013 ,il a 53 ans ; Akiko, 41. Quelques mois plus tard, le 8 octobre 2013, Akiko met au monde un garçon.
          Peu sont prêts à parier sur la santé du fils d’un homme aussi exposé aux radiations !
          Aujourd’hui, il se prend à espérer une famille plus grande : « J’aimerais avoir encore un enfant, mais Akiko est âgée. » Dans la population de Fukushima, de nombreuses grossesses ont été interrompues.
          Mais pour Naoto Matsumura chaque vie est sacrée : « Toutes les vies sont égales, répète-t-il. Nous sommes tous liés les uns aux autres. Ce qui arrive à la vache arrive aussi à l’homme. » Alors que 1 million d’animaux sont morts ou ont été abattus dans la préfecture de Fukushima, il a aussi sauvé des chiens et des chats, partageant leurs croquettes quand il n’y avait plus la moindre nourriture dans un rayon de 30 kilomètres. Son bébé portera le nom de Naoaki, contraction des prénoms de ses deux parents, et il fait aujourd’hui le bonheur du père qui l’appelle son « bébé miracle », mais garde son humour : « Naoaki a une puissance atomique ! » dit-il, en le regardant dévorer ses repas.
        </p>
      </figcaption>
    </figure>
    <Menu></Menu>
  </div>
</template>


<style scoped lang="scss">
.enfantMiracle__wrapper {
  width: 100vw;
  height: 200vh;
  background-color: white;
  background-image: url("../../static/images/enfantBG.png");
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
figure {
  display: flex;
  justify-content: center;
  position: relative;
  height: 37.5%;
  img {
    height: 55%;
    position: relative;
  }
  figcaption {
    background-color: white;
    font-size: 17px;
    overflow: scroll;
    line-height: 23px;
    height: 820px;
    width: 700px;
    p {
      margin: 20px 20px 0px 20px;
      line-height: 1.7rem;
    }
    &::first-line {
      font-weight: bold;
    }
  }
}
h1 {
  text-align: left;
  padding: 80px 0px 50px 40px;
  font-size: 30px;
  transition: ease;
}
</style>
<script>
import Menu from "~/components/Menu.vue";
import axios from "axios";
export default {
  data() {
    return {
      arrayName: null,
      arrayContent: null,
      arrayImage: null
    };
  },
  components: {
    Menu
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.arrayName = response.data[2].name;
      this.arrayContent = response.data[2].content;
      this.arrayImage = response.data[2].img;
    });
  }
};
</script>