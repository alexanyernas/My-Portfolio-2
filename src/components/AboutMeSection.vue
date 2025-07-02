<template>
  <v-container fluid class="about-container" id="about">
    <v-row class="justify-center">
      <v-col cols="12" class="text-center">
        <div class="section-header">
          <h2 class="section-title">SOBRE MÍ</h2>
          <div class="title-divider"></div>
          <p class="section-subtitle">Transformando pixels en experiencias memorables</p>
        </div>
      </v-col>
    </v-row>

    <v-row class="justify-center">
      <v-col cols="12" md="10" lg="8">
        <!-- Sección de Pasión por el Diseño -->
        <div class="bio-section">
          <h3 class="bio-title">Mi Pasión por el Diseño</h3>
          <p class="bio-text">
            ¡Hola! Soy <strong>Alejandra Giannattasio</strong>, Diseñadora UI/UX con más de <strong>4 años de experiencia</strong> creando interfaces que no solo son visualmente atractivas, 
            sino también intuitivas y accesibles. Mi enfoque combina principios de psicología cognitiva con 
            las últimas tendencias en diseño digital.
          </p>
          
          <p class="bio-text">
            En la <strong>Universidad Central de Venezuela</strong>, tengo el privilegio de enseñar 
            <strong>Interacción Humano-Computador</strong> y <strong>Tópicos Avanzados de IHC</strong>, 
            materias donde fusiono teoría y práctica para formar a la próxima generación de diseñadores.
          </p>

          <div class="experience-badges">
            <div class="experience-badge">
              <v-icon color="white">mdi-star</v-icon>
              <span>4+ años de experiencia</span>
            </div>
            
            <div class="education-badge">
              <v-icon>mdi-human-male-board</v-icon>
              <span>Preparadora universitaria</span>
            </div>
          </div>
        </div>

        <!-- Habilidades técnicas -->
        <div class="skills-section">
          <h3 class="skills-title">Habilidades Técnicas</h3>
          <div class="skills-grid">
            <div v-for="(skill, index) in technicalSkills" :key="index" class="skill-item">
              <div class="skill-icon">
                <v-img :src="getSkillIcon(skill)" height="60" contain />
              </div>
              <span class="skill-name">{{ skill }}</span>
              <div class="skill-bar">
                <div class="skill-progress" :style="{ width: getSkillLevel(skill) }"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Habilidades blandas -->
        <div class="soft-skills-section">
          <h3 class="skills-title">Habilidades Blandas</h3>
          <div class="soft-skills-container">
            <div v-for="(skill, index) in softSkills" :key="index" class="soft-skill-item">
              <v-icon class="soft-skill-icon">mdi-check-circle</v-icon>
              <span>{{ skill }}</span>
            </div>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import '@/styles/AboutMe.css';

const technicalSkills = [
  'Figma', 'Adobe XD', 'Sketch', 
  'Illustrator', 'Photoshop', 'Canva', 'WordPress', 'Jira', 'Trello'
];

const softSkills = [
  'Creatividad', 'Liderazgo', 'Trabajo en equipo',
  'Resolución de problemas', 'Metodologías ágiles', 'Comunicación efectiva',
  'Redacción', 'Tolerancia al estrés'
];

const getSkillIcon = (skill: string) => {
  const icons: Record<string, string> = {
    'Figma': '/skills/figma.svg',
    'Adobe XD': '/skills/xd.svg',
    'Sketch': '/skills/sketch.svg',
    'Illustrator': '/skills/illustrator.svg',
    'Photoshop': '/skills/photoshop.svg',
    'Canva': '/skills/canva.svg',
    'WordPress': '/skills/wordpress.svg',
    'Jira': '/skills/jira.svg',
    'Trello': '/skills/trello.svg',
  };
  return icons[skill] || '';
};

const getSkillLevel = (skill: string) => {
  const levels: Record<string, string> = {
    'Figma': '95%',
    'Adobe XD': '100%',
    'Sketch': '75%',
    'Illustrator': '100%',
    'Photoshop': '75%',
    'Canva': '100%',
    'WordPress': '90%',
    'Jira': '100%',
    'Trello': '100%'
  };
  return levels[skill] || '80%';
};
</script>