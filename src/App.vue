<template>
  <div class="flex flex-col items-center justify-center h-screen bg-gradient-to-r from-pink-300 to-purple-400">
    <h1 class="text-4xl font-bold text-white mb-8 shadow-lg">Veux-tu sortir avec moi ? 💖 Abeg faut accepter </h1>

    <div class="relative w-64 h-32 flex justify-center items-center">
      <!-- Bouton "Oui" -->
      <button 
        class="yes-btn px-6 py-3 text-lg font-semibold text-white bg-green-500 rounded-lg shadow-md transition-transform hover:scale-110"
        @click="accept"
      >
        Oui
      </button>

      <!-- Bouton "Non" qui fuit -->
      <button 
        class="no-btn px-6 py-3 text-lg font-semibold text-white bg-red-500 rounded-lg shadow-md absolute"
        @mouseover="moveButton"
        :style="{ transform: `translate(${noButtonX}px, ${noButtonY}px) rotate(${noButtonRotation}deg)` }"
      >
        Non 😢
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      noButtonX: 0,
      noButtonY: 0,
      noButtonRotation: 0 // Ajout de la rotation
    };
  },
  methods: {
    accept() {
      alert('Bonne réponse ! ');
    },
    moveButton() {
      const maxX = window.innerWidth / 3; // Limite le déplacement horizontal
      const maxY = window.innerHeight / 3; // Limite le déplacement vertical

      // Déplacement du bouton
      this.noButtonX = (Math.random() * maxX * 2) - maxX;
      this.noButtonY = (Math.random() * maxY * 2) - maxY;

      // Rotation aléatoire
      this.noButtonRotation = Math.random() * 360;

      // Ajout d'un effet de rebond sur les bords de l'écran
      if (Math.abs(this.noButtonX) > maxX) {
        this.noButtonX = (Math.random() * maxX * 2) - maxX;
      }
      if (Math.abs(this.noButtonY) > maxY) {
        this.noButtonY = (Math.random() * maxY * 2) - maxY;
      }
    }
  }
};
</script>

<style scoped>
/* Fond avec dégradé pour une ambiance romantique */
body {
  overflow: hidden; /* Empêche le scroll si le bouton va trop loin */
}

/* Animation fluide du bouton "Non" */
.no-btn {
  transition: transform 0.3s ease-in-out;
}

/* Effet au survol du bouton "Oui" */
.yes-btn:hover {
  box-shadow: 0px 0px 20px rgba(255, 255, 255, 0.6);
}
</style>
