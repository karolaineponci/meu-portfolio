<template>
  <div class="portfolio-container">
    <!-- SEÇÃO HERO (Apresentação e Foto) -->
    <header class="hero">
      <div class="hero-content">
        <p class="tagline">Olá, mundo! Eu sou a</p>
        <h1>Karolaine <span class="highlight">Ponci</span></h1>
        <h2>Desenvolvedora & Entusiasta de Tecnologia</h2>
        <p class="resumo">
          Estudante de tecnologia com foco em criar soluções eficientes, desde o desenvolvimento web até a infraestrutura e segurança de sistemas. Sempre em busca de novos desafios e aprendizados práticos.
        </p>
        
        <!-- Ícones de Contato -->
        <div class="social-links">
          <a href="https://github.com/karolaineponci"target="_blank" class="icon"><i class="fa-brands fa-github"></i></a>
          <a href="https://www.linkedin.com/in/karolaine-ponci-84a94b2a0"target="_blank" class="icon"><i class="fa-brands fa-linkedin"></i></a>
          <a href="https://instagram.com/karolaineponci"target="_blank" class="icon"><i class="fa-brands fa-instagram"></i></a>
        </div>
      </div>
      
      <div class="hero-image">
        <!-- Substitua pelo caminho da sua foto -->
        <img src="./img/IMG_6322.jpg" alt="Minha Foto" />
      </div>
    </header>

    <!-- SEÇÃO DE PROJETOS (Os Cards) -->
    <section class="projetos">
      <h2>Trabalhos Recentes</h2>
      
      <div class="cards-grid">
        <div class="card" v-for="(projeto, index) in meusProjetos" :key="index">
          <!-- Imagem do Projeto -->
          <div class="card-image-wrapper">
            <img :src="projeto.imagem" :alt="projeto.titulo" class="card-img" />
          </div>

          <div class="card-body">
            <h3>{{ projeto.titulo }}</h3>
            <p>{{ projeto.descricao }}</p>
            
            <div class="tech-tags">
              <span v-for="tech in projeto.tecnologias" :key="tech" class="tag">
                {{ tech }}
              </span>
            </div>

            <div class="card-links">
              <a :href="projeto.github" target="_blank" title="Ver no GitHub"><i class="fa-brands fa-github"></i> Código</a>
              <a v-if="projeto.link && projeto.link !== '#'" :href="projeto.link" target="_blank" title="Ver Projeto"><i class="fa-solid fa-arrow-up-right-from-square"></i> Demo</a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Aqui ficam os dados dos seus 3 trabalhos da faculdade!
const meusProjetos = ref([
  {
    titulo: 'TaskFlow | Gerenciador de Tarefas',
    descricao: 'Aplicação web interativa para gerenciar, editar e acompanhar o progresso de atividades de forma intuitiva.',
    tecnologias: ['HTML', 'CSS', 'JavaScript', 'Bootstrap'],
    imagem: '/taskflow.png', // Substitua pelo caminho do print ex: '/assets/taskflow.png'
    github: 'https://github.com/karolaineponci/taskflow-atividadeDW',
    link: 'https://karolaineponci.github.io/taskflow-atividadeDW/index.html'
  },
  {
    titulo: 'Blog de Viagens',
    descricao: 'Website focado em experiência de uso para leitores, trazendo postagens, relatos de viagens e interface responsiva.',
    tecnologias: ['HTML5', 'CSS3', 'Web Design'],
    imagem: '/guiadeviagem.png', // Substitua pelo print do seu blog
    github: 'https://github.com/karolaineponci/blog-html-css-js',
    link: 'https://karolaineponci.github.io/blog-html-css-js/'
  },
  {
    titulo: 'Dashboard de Vendas com Streamlit',
    descricao: 'Painel interativo para análise visual e acompanhamento de dados de vendas utilizando Python e a biblioteca Streamlit.',
    tecnologias: ['Python', 'Streamlit', 'Data Viz'],
    imagem: '/dashboardSTREAM.png', // Substitua pelo print do dashboard
    github: 'https://github.com/karolaineponci/karolaine-ponci-streamlit', 
    link: 'https://karolaine-ponci.streamlit.app/'
  }
]);
</script>

<style scoped>
/* Estilos Dark Mode e Cyber Vibe */
.portfolio-container {
  background-color: #0f172a; /* Azul muito escuro */
  color: #e2e8f0; /* Texto claro */
  font-family: 'Inter', sans-serif;
  padding: 40px;
  min-height: 100vh;
}

.hero {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 60px;
}

.tagline {
  color: #10b981; /* Verde "terminal" */
  font-family: monospace;
}

h1 {
  font-size: 2.5rem;
  margin: 10px 0;
}

.highlight {
  color: #10b981;
}

h2 {
  font-size: 1.5rem;
  color: #94a3b8;
  margin-top: -5px;
  margin-bottom: 15px;
}

.resumo {
  max-width: 500px;
  color: #94a3b8;
  line-height: 1.6;
}

.hero-image img {
  width: 200px;
  height: 200px;
  border-radius: 20px;
  border: 2px solid #334155;
  object-fit: cover;
}

/* Grid para os Cards tipo "Bento Box" */
.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.card {
  background-color: #1e293b;
  border-radius: 12px;
  border: 1px solid #334155;
  overflow: hidden; /* Garante que a imagem respeite as bordas arredondadas */
  display: flex;
  flex-direction: column;
  transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
  border-color: #10b981; /* Destaque verde ao passar o mouse */
}

.card-image-wrapper {
  width: 100%;
  height: 180px;
  overflow: hidden;
  background-color: #0f172a;
}

.card-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.card:hover .card-img {
  transform: scale(1.05); /* Leve zoom na imagem ao passar o mouse */
}

.card-body {
  padding: 20px;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.card-links {
  display: flex;
  gap: 15px;
  margin-top: 20px;
  padding-top: 15px;
  border-top: 1px solid #334155;
}

.card-links a {
  color: #10b981;
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
  display: flex;
  align-items: center;
  gap: 5px;
  transition: color 0.2s;
}

.card-links a:hover {
  color: #ffffff;
}

.tech-tags {
  display: flex;
  gap: 10px;
  margin-top: 15px;
  flex-wrap: wrap;
}

.tag {
  background-color: #334155;
  font-size: 0.8rem;
  padding: 4px 8px;
  border-radius: 6px;
  font-family: monospace;
}

.social-links {
  display: flex;
  gap: 20px;
  margin-top: 15px;
}

.icon {
  color: #10b981; /* Verde tech combinando com a tag */
  font-size: 2rem; /* Aumenta o tamanho do ícone */
  text-decoration: none;
  transition: transform 0.3s, color 0.3s;
}

.icon:hover {
  color: #e2e8f0; /* Fica branco ao passar o mouse */
  transform: translateY(-5px); /* Dá um pulinho pra cima */
}

</style>