<template>
  <v-footer class="custom-footer">
    <v-container>
      <v-row class="align-center">
        <!-- Logo y nombre -->
        <v-col cols="12" md="4" class="text-center text-md-left">
          <div class="footer-brand">
            <v-avatar size="50" class="mr-3">
              <v-img :src="me" alt="Alejandra Giannattasio"></v-img>
            </v-avatar>
            <div>
              <h3 class="footer-name">Alejandra Giannattasio</h3>
              <p class="footer-title">Diseñadora UI/UX</p>
            </div>
          </div>
        </v-col>

        <!-- Derechos de autor -->
        <v-col cols="12" md="4" class="text-center">
          <p class="copyright">
            © {{ new Date().getFullYear() }} Alejandra Giannattasio
          </p>
        </v-col>

        <!-- Redes sociales -->
        <v-col cols="12" md="4" class="text-center text-md-right">
          <div class="social-icons">
            <a href="https://github.com/alegiannattasio" target="_blank" class="social-icon">
              <v-icon aria-hidden="true">mdi-github</v-icon>
            </a>
            <a href="https://www.linkedin.com/in/alegiannattasio/" target="_blank" class="social-icon">
              <v-icon aria-hidden="true">mdi-linkedin</v-icon>
            </a>
            <a href="mailto:alegiannattasioxd@gmail.com" class="social-icon">
              <v-icon aria-hidden="true">mdi-email</v-icon>
            </a>
          </div>
        </v-col>
      </v-row>

      <!-- Línea divisora elegante -->
      <v-divider class="footer-divider"></v-divider>

      <!-- Mensaje especial -->
      <v-row>
        <v-col cols="12" class="text-center">
          <p class="footer-message">
            Hecho con <v-icon small color="#ff4081" aria-hidden="true">mdi-heart</v-icon>
          </p>
        </v-col>
      </v-row>
    </v-container>
  </v-footer>
</template>

<script setup lang="ts">
import me from '@/assets/me.webp';
</script>

<style scoped>
.custom-footer {
  background: #2d2d2d;
  color: white;
  padding: 60px 0 30px;
}

.footer-brand {
  display: flex;
  align-items: center;
  justify-content: center;
  justify-content: flex-start;
}

.footer-name {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 4px;
  color: white;
}

.footer-title {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.7);
  margin: 0;
}

.copyright {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
  margin: 0;
}

.social-icons {
  display: flex;
  justify-content: center;
  justify-content: flex-end;
  gap: 20px;
}

.social-icon {
  color: rgba(255, 255, 255, 0.7);
  transition: all 0.3s ease;
  text-decoration: none;
}

.social-icon:hover {
  color: #8c52ff;
  transform: translateY(-3px);
}

.footer-divider {
  margin: 30px 0;
  background-color: rgba(255, 255, 255, 0.1);
}

.footer-message {
  color: rgba(255, 255, 255, 0.5);
  font-size: 0.85rem;
  margin: 0;
}

/* Responsive */
@media (max-width: 960px) {
  .footer-brand {
    justify-content: center;
    margin-bottom: 20px;
  }
  
  .social-icons {
    justify-content: center;
    margin-top: 20px;
  }
  
  .copyright {
    margin: 15px 0;
  }
  
  .custom-footer {
    padding: 40px 0 20px;
  }
}
</style>