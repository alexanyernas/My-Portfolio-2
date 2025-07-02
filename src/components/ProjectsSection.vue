<template>
  <v-container fluid class="projects-container" id="projects">
    <v-row class="justify-center">
      <v-col cols="12" class="text-center">
        <div class="section-header">
          <h2 class="section-title">PROYECTOS</h2>
          <div class="title-divider"></div>
        </div>
      </v-col>
    </v-row>

    <v-row class="justify-center">
      <v-col cols="12" md="10" lg="8">
        <div class="projects-intro">
          <p class="intro-text">
            Una selección de mis trabajos más importantes. Cada proyecto representa un desafío único 
            donde he aplicado mis habilidades en <strong>diseño UI/UX</strong> para crear soluciones 
            intuitivas y visualmente impactantes.
          </p>
        </div>
      </v-col>
    </v-row>

    <v-row class="justify-center project-grid">
      <v-col
        v-for="project in projects"
        :key="project.id"
        cols="12"
        sm="6"
        md="4"
        lg="3"
      >
        <v-card
          class="project-card"
          @click="openProject(project)"
          flat
          hover
        >
          <div class="image-wrapper">
            <v-img
              :src="getProjectThumbnail(project)"
              :alt="project.name"
              cover
              class="project-image"
              gradient="to bottom, rgba(0,0,0,0.1), rgba(0,0,0,0.5)"
            >
              <template v-slot:placeholder>
                <v-row class="fill-height ma-0" align="center" justify="center">
                  <v-progress-circular indeterminate color="grey lighten-5" />
                </v-row>
              </template>
            </v-img>
          </div>
          
          <v-card-title class="project-title">
            {{ project.name }}
          </v-card-title>
          
          <v-card-subtitle class="project-subtitle">
            {{ project.imagesCount }} {{ project.imagesCount > 1 ? 'imágenes' : 'imagen' }}
          </v-card-subtitle>
        </v-card>
      </v-col>
    </v-row>

    <!-- Lightbox Dialog -->
    <v-dialog
      v-model="dialog"
      max-width="1200"
      scrollable
    >
      <v-card class="lightbox-card">
        <v-card-actions class="lightbox-header">
          <v-spacer></v-spacer>
          <v-btn
            icon
            @click="dialog = false"
            class="close-btn"
          >
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-card-actions>
        
        <v-card-title class="lightbox-title">
          {{ currentProject?.name }}
        </v-card-title>
        
        <v-carousel
          v-model="currentImageIndex"
          hide-delimiters
          height="600"
          touch
          class="lightbox-carousel"
          show-arrows="hover"
        >
          <v-carousel-item
            v-for="(n, i) in currentProject?.imagesCount"
            :key="i"
          >
            <div class="carousel-image-container">
              <v-img
                :src="`/projects/${currentProject?.folder}/${n}.webp`"
                contain
                class="carousel-image"
                :alt="currentProject?.folder"
              >
                <template v-slot:placeholder>
                  <v-row class="fill-height ma-0" align="center" justify="center">
                    <v-progress-circular indeterminate color="grey lighten-5" />
                  </v-row>
                </template>
              </v-img>
            </div>
          </v-carousel-item>
        </v-carousel>
        
        <div class="navigation-controls">
          <v-btn
            icon
            @click="prevImage"
            :disabled="currentImageIndex === 0"
            class="nav-btn"
            size="large"
          >
            <v-icon>mdi-chevron-left</v-icon>
          </v-btn>
          
          <div class="image-counter">
            {{ currentImageIndex + 1 }} / {{ currentProject?.imagesCount }}
          </div>
          
          <v-btn
            icon
            @click="nextImage"
            :disabled="currentImageIndex === (currentProject?.imagesCount - 1)"
            class="nav-btn"
            size="large"
          >
            <v-icon>mdi-chevron-right</v-icon>
          </v-btn>
        </div>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script setup>
import { ref } from 'vue';
import '@/styles/ProjectsSection.css';

const projects = [
  { id: 1, name: 'Buddy', folder: 'buddy', imagesCount: 3 },
  { id: 2, name: 'Chelo Desktop', folder: 'chelo_desktop', imagesCount: 3 },
  { id: 3, name: 'Chelo Mobile', folder: 'chelo_mobile', imagesCount: 3 },
  { id: 4, name: 'Contratando Personal', folder: 'contratando_personal', imagesCount: 2 },
  { id: 5, name: 'Educa2', folder: 'educa2', imagesCount: 3 },
  { id: 6, name: 'OJC', folder: 'ojc', imagesCount: 3 },
  { id: 7, name: 'Oxford App', folder: 'oxford_app', imagesCount: 3 },
  { id: 8, name: 'Oxford en Línea', folder: 'oxford_en_linea', imagesCount: 3 },
  { id: 9, name: 'Oxford SRE', folder: 'oxford_sre', imagesCount: 3 },
  { id: 10, name: 'Oxford SRE App', folder: 'oxford_sre_app', imagesCount: 3 },
  { id: 11, name: 'Punicorp', folder: 'punicorp', imagesCount: 3 },
  { id: 12, name: 'QRWoof App', folder: 'qrwoof_app', imagesCount: 2 },
  { id: 13, name: 'QRWoof Desktop', folder: 'qrwoof_desktop', imagesCount: 3 },
  { id: 14, name: 'Restaurante', folder: 'restaurante', imagesCount: 3 },
  { id: 15, name: 'Saon App 1', folder: 'saon_app_1', imagesCount: 3 },
  { id: 16, name: 'Saon App 2', folder: 'saon_app_2', imagesCount: 3 },
  { id: 17, name: 'Saon Web', folder: 'saon_web', imagesCount: 3 },
  { id: 18, name: 'Sermadre App', folder: 'sermadre_app', imagesCount: 3 },
];

const dialog = ref(false);
const currentProject = ref(null);
const currentImageIndex = ref(0);

const openProject = (project) => {
  currentProject.value = project;
  currentImageIndex.value = 0;
  dialog.value = true;
};

const nextImage = () => {
  if (currentImageIndex.value < currentProject.value.imagesCount - 1) {
    currentImageIndex.value++;
  }
};

const prevImage = () => {
  if (currentImageIndex.value > 0) {
    currentImageIndex.value--;
  }
};

const getProjectThumbnail = (project) => {
  return `/projects/${project.folder}/1.webp`;
};
</script>