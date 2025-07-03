<template>
  <div>
    <v-app-bar flat v-if="isMobile" class="px-4">
      <!-- Foto a la izquierda -->
      <v-avatar size="30">
        <img
          :src="me"
          alt="Avatar de A. Giannattasio"
          style="object-fit: cover; width: 100%; height: 100%;"
        />
      </v-avatar>

      <!-- Espacio flexible -->
      <div class="flex-grow-1"></div>

      <!-- Ícono hamburguesa a la derecha -->
      <v-app-bar-nav-icon @click="menuMobileOpen = true" aria-label="Menú" />
    </v-app-bar>

    <v-dialog
      v-model="menuMobileOpen"
      fullscreen
      hide-overlay
      transition="dialog-bottom-transition"
      class="mobile-menu-dialog"
    >
      <v-card class="mobile-menu-card">
        <div class="menu-close-btn">
          <v-btn icon @click="menuMobileOpen = false" aria-label="Cerrar menú">
            <v-icon size="28" aria-hidden="true">mdi-close</v-icon>
          </v-btn>
        </div>

        <div class="mobile-menu-content">
          <div
            v-for="item in items"
            :key="item.value"
            class="menu-link"
            @click="handleMobileClick(item.value)"
          >
            <v-icon size="28" class="menu-link-icon" aria-hidden="true">{{ item.icon }}</v-icon>
            <span class="menu-link-text">{{ item.title }}</span>
          </div>
        </div>

        <div class="mobile-menu-footer">
          <v-btn
            v-for="item in itemsContact"
            :key="item.icon"
            icon
            @click="handleOpenUrl(item.url)"
            class="footer-icon-btn"
          >
            <v-icon size="26" aria-hidden="true">{{ item.icon }}</v-icon>
          </v-btn>
        </div>
      </v-card>
    </v-dialog>

    <v-navigation-drawer
      v-if="!isMobile"
      permanent
      :rail="rail"
      v-model="drawer"
      @click="rail = false"
      class="h-screen position-fixed custom-drawer"
      :color="rail ? 'transparent' : undefined"
    >
      <!-- Encabezado con efecto especial -->
      <div class="drawer-header" :class="{ 'rail-mode': rail }">
        <v-list>
          <v-list-item 
            :prepend-avatar="me"
            class="header-content"
            :class="{ 'px-4': !rail }"
          >
            <template v-slot:title>
              <p class="text-caption text-white font-weight-bold">A. Giannattasio</p>
            </template>
            <template v-slot:subtitle>
              <p class="text-caption text-white">Diseñadora UI/UX</p>
            </template>
            <template v-slot:append>
              <v-btn
                size="x-small"
                variant="text"
                :icon="rail ? 'mdi-menu' : 'mdi-chevron-left'"
                @click.stop="rail = !rail"
                class="toggle-btn"
              ></v-btn>
            </template>
          </v-list-item>
        </v-list>
      </div>
  
      <!-- Items del menú con scroll suave -->
      <v-list nav class="menu-items">
        <v-list-item 
          v-for="item in items" 
          :key="item?.value"
          :title="!rail ? item?.title : ''"
          :value="item?.value"
          :prepend-icon="item?.icon"
          class="menu-item"
          active-class="active-menu-item"
          @click="scrollToSection(item.value)"
        >
          <template v-slot:prepend>
            <v-icon :icon="item?.icon" class="menu-icon" aria-hidden="true"></v-icon>
          </template>
          
          <template v-if="!rail" v-slot:title>
            <span class="menu-text">{{ item?.title }}</span>
          </template>
        </v-list-item>
      </v-list>
  
      <!-- Redes sociales -->
      <template v-slot:append>
        <div class="social-container" :class="{ 'rail-social': rail }">
          <div 
            v-for="item in itemsContact" 
            :key="item?.icon"
            class="social-bubble"
            @click="handleOpenUrl(item?.url)"
          >
            <v-icon :icon="item?.icon" size="large" aria-hidden="true"></v-icon>
          </div>
        </div>
      </template>
    </v-navigation-drawer>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import '@/styles/NavigationDrawer.css';

// Interfaces
interface MenuItem {
  title: string;
  value: string;
  icon: string;
}

interface MenuContactItem {
  url: string;
  icon: string;
}

// Assets
import me from '@/assets/me.webp';

// Vue
const drawer = ref(true);
const rail = ref(true);
const isMobile = ref(false);
const menuMobileOpen = ref(false);

// Data
const items: MenuItem[] = [
  {
    title: 'Inicio',
    value: 'home',
    icon: 'mdi-home'
  },
  {
    title: 'Sobre mí',
    value: 'about',
    icon: 'mdi-meditation'
  },
  {
    title: 'Experiencia',
    value: 'experience',
    icon: 'mdi-briefcase'
  },
  {
    title: 'Proyectos',
    value: 'projects',
    icon: 'mdi-earth'
  },
  {
    title: 'Contacto',
    value: 'contact',
    icon: 'mdi-email'
  }
];

const itemsContact: MenuContactItem[] = [
  {
    url: 'https://github.com/alegiannattasio',
    icon: 'mdi-github'
  },
  {
    url: 'mailto:alegiannattasioxd@gmail.com',
    icon: 'mdi-gmail'
  },
  {
    url: 'https://www.linkedin.com/in/alegiannattasio/',
    icon: 'mdi-linkedin'
  }
];

// Métodos
const handleOpenUrl = (url: string) => window.open(url, '_blank');

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    });
  }
  
  // Cerrar el drawer en móvil si está abierto
  if (window.innerWidth < 960) {
    rail.value = false;
  }
};

const checkIsMobile = () => {
  isMobile.value = window.innerWidth < 960;
};

const handleMobileClick = (sectionId: string) => {
  menuMobileOpen.value = false;
  scrollToSection(sectionId);
};

onMounted(() => {
  checkIsMobile();
  window.addEventListener('resize', checkIsMobile);
});

onUnmounted(() => {
  window.removeEventListener('resize', checkIsMobile);
});
</script>

