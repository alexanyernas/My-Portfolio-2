<template>
  <v-container fluid class="hero-container pa-0 ma-0" id="home">
    <v-row no-gutters class="fill-height align-center mb-12">
      <!-- Columna de texto -->
      <v-col cols="12" md="8" lg="8" class="px-4 px-sm-8 px-md-6 px-lg-16 text-center text-md-start order-2 order-md-1 z-index-2">
        <div class="d-flex flex-column">
          <h1 class="text-h4 text-sm-h3 text-md-h2 text-lg-h1 font-weight-bold mb-2 mb-sm-4 pb-3 gradient-text">
            Alejandra Giannattasio
          </h1>
          
          <h2 class="text-h6 text-sm-h5 text-md-h4 text-lg-h3 mb-3 mb-sm-6">
            <span class="typewriter"></span>
            <span class="blinking-cursor">|</span>
          </h2>
          
          <p class="text-body-2 text-sm-body-1 text-md-h6 mb-4 mb-sm-8 px-2 px-sm-0">
            Transformando ideas en experiencias digitales memorables con diseño centrado en el usuario.
          </p>
          
          <div class="d-flex justify-center justify-md-start ga-2 ga-sm-4 flex-wrap mb-8">
            <v-btn
              color="primary"
              size="large"
              rounded="lg"
              class="elevation-2 primary-btn text-capitalize mb-2 mb-sm-0"
              @click="scrollToSection('projects')"
            >
              Ver Proyectos
            </v-btn>
            
            <v-btn
              variant="outlined"
              color="#8c52ff"
              size="large"
              rounded="lg"
              class="elevation-2 text-capitalize"
              @click="scrollToSection('contact')"
            >
              Contacto
            </v-btn>
          </div>
        </div>
      </v-col>
      
      <!-- Columna de imagen -->
      <v-col cols="12" md="4" lg="4" class="d-flex align-center justify-center order-1 order-md-2 pt-8 pt-md-0 z-index-1">
        <div class="bubble-container" :style="{ maxWidth: $vuetify.display.smAndDown ? '220px' : '100%' }">
          <v-img
            :src="me"
            alt="Alejandra Giannattasio - UI/UX Designer"
            class="bubble-image"
            :width="$vuetify.display.smAndDown ? 220 : $vuetify.display.lgAndUp ? 400 : 320"
            cover
          ></v-img>
          <div class="bubble-glow"></div>
        </div>
      </v-col>
    </v-row>
    
    <!-- Flecha de scroll down -->
    <div class="scroll-down" @click="scrollToSection('about')">
      <v-icon icon="mdi-chevron-double-down" size="x-large" color="#8c52ff" aria-hidden="true"></v-icon>
    </div>
  </v-container>
</template>

<script setup lang="ts">
import me from '@/assets/me.webp';
import '@/styles/HeroSection.css';
import { onMounted } from 'vue';

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    });
  }
};

onMounted(() => {
  // Efecto de máquina de escribir
  const typewriterTexts = [
    "Diseñadora UI/UX",
    "Experiencia de Usuario",
    "Productos Digitales",
    "Especialista en Interacción"
  ];
  let currentTextIndex = 0;
  let charIndex = 0;
  let isDeleting = false;
  const typewriterElement = document.querySelector('.typewriter');
  
  function typeWriter() {
    const currentText = typewriterTexts[currentTextIndex];
    
    if (isDeleting) {
      typewriterElement!.textContent = currentText.substring(0, charIndex - 1);
      charIndex--;
    } else {
      typewriterElement!.textContent = currentText.substring(0, charIndex + 1);
      charIndex++;
    }
    
    if (!isDeleting && charIndex === currentText.length) {
      isDeleting = true;
      setTimeout(typeWriter, 2000);
    } else if (isDeleting && charIndex === 0) {
      isDeleting = false;
      currentTextIndex = (currentTextIndex + 1) % typewriterTexts.length;
      setTimeout(typeWriter, 500);
    } else {
      const speed = isDeleting ? 50 : 100;
      setTimeout(typeWriter, speed);
    }
  }
  
  setTimeout(typeWriter, 1000);
});
</script>