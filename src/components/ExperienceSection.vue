<template>
  <v-container fluid class="minimalist-experience" id="experience">
    <v-row class="justify-center">
      <v-col cols="12" class="text-center mb-10">
        <h2 class="section-title">EXPERIENCIA PROFESIONAL</h2>
        <div class="title-divider"></div>
        <p class="section-subtitle">Una trayectoria dedicada al diseño y la innovación</p>
      </v-col>
    </v-row>

    <v-row class="justify-center">
      <v-col cols="12" md="10" lg="8">
        <!-- Experiencia 1 -->
        <div class="experience-item">
          <div class="experience-header">
            <h3 class="job-title">Líder de Marketing - Diseñador UI/UX</h3>
            <div class="company-period">
              <span class="company">PAiCore Technologies</span>
              <span class="period">2022 - Actualidad</span>
            </div>
          </div>
          <ul class="responsibilities">
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Mantenimiento de página web y redes sociales</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Creación de contenido gráfico comercial</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Diseños UI/UX para proyectos</li>
          </ul>
        </div>

        <!-- Experiencia 2 -->
        <div class="experience-item">
          <div class="experience-header">
            <h3 class="job-title">Cofundador - Diseñador UI/UX</h3>
            <div class="company-period">
              <span class="company">Punicorp</span>
              <span class="period">2021 - 2023</span>
            </div>
          </div>
          <ul class="responsibilities">
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Mantenimiento web y redes</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Creación de banners y contenido</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Diseño de interfaces</li>
          </ul>
        </div>

        <!-- Experiencia 3 -->
        <div class="experience-item">
          <div class="experience-header">
            <h3 class="job-title">Cofundador</h3>
            <div class="company-period">
              <span class="company">EDUCA2</span>
              <span class="period">2018 - 2021</span>
            </div>
          </div>
          <ul class="responsibilities">
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Diseño de contenido educativo</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Dictado de cursos</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Mantenimiento web</li>
          </ul>
        </div>

        <!-- Experiencia 4 -->
        <div class="experience-item">
          <div class="experience-header">
            <h3 class="job-title">Preparador Universitario</h3>
            <div class="company-period">
              <span class="company">Universidad Central de Venezuela</span>
              <span class="period">2019 - Actualidad</span>
            </div>
          </div>
          <ul class="responsibilities">
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Introducción a la Informática</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Interacción Humano-Computador</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Tópicos Avanzados de IHC</li>
          </ul>
        </div>

        <!-- Experiencia 5 -->
        <div class="experience-item">
          <div class="experience-header">
            <h3 class="job-title">Ventas</h3>
            <div class="company-period">
              <span class="company">Mipto Tech</span>
              <span class="period">2019</span>
            </div>
          </div>
          <ul class="responsibilities">
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Marketing digital</li>
            <li><v-icon small color="#8c52ff" aria-hidden="true">mdi-circle-small</v-icon> Gestión de plataformas tales como Workana, Fiverr y Freelancer</li>
          </ul>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import '@/styles/ExperienceSection.css';
</script>