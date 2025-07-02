<template>
  <v-container fluid class="contact-container" id="contact">
    <v-row class="justify-center">
      <v-col cols="12" class="text-center mb-10">
        <h2 class="section-title">CONTACTO</h2>
        <div class="title-divider"></div>
        <p class="section-subtitle">¿Listo para crear algo increíble juntos?</p>
      </v-col>
    </v-row>

    <v-row class="justify-center">
      <v-col cols="12" md="8" lg="6">
        <!-- Tarjeta de contacto principal -->
        <div class="contact-card">
          <div class="contact-header">
            <v-avatar size="80" class="contact-avatar">
              <v-img :src="me" alt="Alejandra Giannattasio"></v-img>
            </v-avatar>
            <h3 class="contact-name">Alejandra Giannattasio</h3>
            <p class="contact-title">Diseñadora UI/UX</p>
          </div>

          <!-- Canales de contacto -->
          <div class="contact-channels">
            <!-- WhatsApp -->
            <a href="https://wa.me/+584120137644" target="_blank" class="contact-item">
              <div class="contact-icon whatsapp">
                <v-icon color="white" aria-hidden="true">mdi-whatsapp</v-icon>
              </div>
              <div class="contact-info">
                <p class="contact-label">WhatsApp</p>
                <p class="contact-value">+58 412 013 7644</p>
              </div>
            </a>

            <!-- Email -->
            <a href="mailto:alegiannattasioxd@gmail.com" class="contact-item">
              <div class="contact-icon email">
                <v-icon color="white" aria-hidden="true">mdi-email</v-icon>
              </div>
              <div class="contact-info">
                <p class="contact-label">Correo electrónico</p>
                <p class="contact-value">alegiannattasioxd@gmail.com</p>
              </div>
            </a>

            <!-- LinkedIn -->
            <a href="https://www.linkedin.com/in/alegiannattasio/" target="_blank" class="contact-item">
              <div class="contact-icon linkedin">
                <v-icon color="white" aria-hidden="true">mdi-linkedin</v-icon>
              </div>
              <div class="contact-info">
                <p class="contact-label">LinkedIn</p>
                <p class="contact-value">alegiannattasio</p>
              </div>
            </a>

            <!-- GitHub -->
            <a href="https://github.com/alegiannattasio" target="_blank" class="contact-item">
              <div class="contact-icon github">
                <v-icon color="white" aria-hidden="true">mdi-github</v-icon>
              </div>
              <div class="contact-info">
                <p class="contact-label">GitHub</p>
                <p class="contact-value">alegiannattasio</p>
              </div>
            </a>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import me from '@/assets/me.webp';
import '@/styles/ContactSection.css';
</script>