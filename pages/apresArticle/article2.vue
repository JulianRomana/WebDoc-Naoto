<template>
  <div>
    <section id="apresScreen" class="apresScreen">
      <h1>L’APRÈS</h1>
      <img class="firstMove" src="../../static/images/lapres/rectangle.png" />
      <img class="secondImg" src="../../static/images/lapres/rectangle-3.png" />
      <img class="thirdImg" src="../../static/images/lapres/rectangle-4.png" />
      <img class="fourthImg" src="../../static/images/lapres/rectangle-2.png" />
      <article class="txt">
        <p>Keigo Sakamoto, un agriculteur et ancien soignant pour handicapés mentaux, est une de ces personnes pouvant être considérée comme folle par certains et comme un héros par d'autres. Monsieur Sakamoto a refusé d’évacuer et est resté à l'intérieur de la zone irradiée où il a fait des animaux sa priorité. Il s'est aventuré dans les villes et villages abandonnés et a rassemblé tous les chiens, chats ainsi que les marmottes et les lapins abandonnés par leurs anciens propriétaires.</p>
      </article>
      <article class="txt2">
        <p>Sakamoto vit maintenant dans son ranch de montagne, près de la ville de Naraha avec plus de 500 animaux. Un théâtre bruyant causé par beaucoup de ses chiens devenus fous après avoir été seuls, avant que Sakamoto ne les sauve.</p>
      </article>
      <article class="txt3">
        <p>"Il n'y a pas de voisins" a déclaré Monsieur Sakamoto. "Je suis seul ici mais je suis là pour rester." Parmi ses vingt chiens, seuls deux sont amicaux avec l'homme. L’un d’eux s’appelle Atom, un petit chien blanc, né juste avant la catastrophe de Fukushima.</p>
      </article>
      <article class="txt4">
        <p>Le long de la rue principale de Tomioka, se trouve un couple de personnes âgées avec des masques sur le visage et des sacs en plastique sur les chaussures. Ils ont obtenu une des rares autorisations pour se rendre à leur domicile et à la confiserie familiale qu’ils dirigeaient. Ils sont inquiets quant à l’hygiène de leur boutique, ils ont installé des pièges à souris partout, et le couple passe son temps à sortir les souris mortes et à y mettre plus de poison.</p>
      </article>
      <article class="txt5">
        <p>Après la suppression des parasites, Zenjuro et sa femme ont commencé à nettoyer les congélateurs à l'intérieur de leur magasin. À leur grande surprise, tous les gâteaux étaient toujours là et en parfait état. Nagaoka, le propriétaire, a expliqué que le courant ne s'était jamais éteint depuis le jour de la catastrophe. Il n'a pas semblé trouver cela étrange ou particulièrement significatif.</p>
      </article>
      <nuxt-link class="return" to="videoArticle2">
        <Retour Retour="Vidéo" class="returnButton"></Retour>
      </nuxt-link>
    </section>
    <Menu></Menu>
  </div>
</template>
<style lang="scss" scoped>
.returnButton {
  position: fixed;
  top: 40%;
  left: 10px;
  z-index: 5;
}
.apresScreen::before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(255, 255, 255, 0.541);
  position: fixed;
  z-index: 0;
}
.apresScreen {
  background-image: url("../../static/images/apres.jpg");
  background-size: cover;
  background-position: center;
  height: 245vh;
  width: 100vw;
  font-family: league spartan;
  h1 {
    font-size: 25px;
    position: fixed;
    top: 50px;
    left: 50px;
  }
  article {
    background-color: rgb(255, 255, 255);
    box-shadow: 0px 0px 4px 0px #656565;
    border: none;
    position: fixed;
    bottom: 50px;
    right: 200px;
    width: 580px;
    height: 360px;
    font-size: 18px;
    font-family: oswald;
    z-index: 1;
    padding: 0px 40px 0px 40px;
    &::first-line {
      font-weight: bold;
      font-size: 19px;
    }
    p {
      margin: 20px 20px 0px 20px;
      line-height: 1.7rem;
    }
  }
  img {
    width: 403px;
    height: 402px;
    position: fixed;
    top: 150px;
    right: 750px;
  }
  .secondImg {
    display: none;
    position: fixed;
    top: 30px;
    left: 250px;
    z-index: 3;
  }
  .thirdImg {
    display: none;
    position: fixed;
    top: 100px;
    left: 1000px;
    z-index: 2;
  }
  .fourthImg {
    display: none;
    position: fixed;
    top: 240px;
    left: 580px;
    z-index: 2;
  }
  .txt {
    z-index: 1;
    background-color: white;
    width: 585px;
    height: 230px;
    position: fixed;
    top: 100px;
    right: 240px;
  }
  .txt2 {
    display: none;
    z-index: 3;
    background-color: white;
    width: 480px;
    height: 200px;
    position: fixed;
    top: 420px;
    right: 880px;
  }
  .txt3 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 420px;
    height: 200px;
    position: fixed;
    top: 460px;
    right: 370px;
  }
  .txt4 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 460px;
    height: 321px;
    position: fixed;
    top: 100px;
    left: 100px;
  }
  .txt5 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 420px;
    height: 321px;
    position: fixed;
    top: 100px;
    right: 40px;
  }
}
</style>
<script>
import Menu from "~/components/Menu.vue";
import Retour from "~/components/Retour";
import $ from "jquery";
export default {
  components: {
    Menu,
    Retour
  },
  mounted() {
    let first = document.querySelector(".firstMove");
    let txt = document.querySelector(".txt");
    let button = document.querySelector(".returnButton");
    let img2 = document.querySelector(".secondImg");
    let img3 = document.querySelector(".thirdImg");
    let img4 = document.querySelector(".fourthImg");
    let txt2 = document.querySelector(".txt2");
    let txt3 = document.querySelector(".txt3");
    let txt4 = document.querySelector(".txt4");
    let txt5 = document.querySelector(".txt5");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
      first.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      txt.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      if (scroll > 502) {
        scroll = scroll - 502;
        img2.style.display = "block";
        img3.style.display = "block";
        txt2.style.display = "block";
        txt3.style.display = "block";
        img2.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        img3.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt2.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt3.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        img2.style.display = "none";
        img3.style.display = "none";
        txt2.style.display = "none";
        txt3.style.display = "none";
      }
      if (scroll > 502) {
        scroll = scroll - 502;
        img4.style.display = "block";
        txt4.style.display = "block";
        txt5.style.display = "block";
        img4.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt4.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt5.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        img4.style.display = "none";
        txt4.style.display = "none";
        txt5.style.display = "none";
      }
    });
  }
};
</script>