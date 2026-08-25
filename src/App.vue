<template>
  <div class="portfolio-container">
    <!-- SEÇÃO HERO (Apresentação e Foto) -->
    <header class="hero">
      <div class="hero-content">
        <p class="tagline">Olá, mundo! Eu sou um</p>
        <h1>Desenvolvedor & Entusiasta de Tecnologia</h1>
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
        <!-- O Vue usa v-for para criar os cards automaticamente com base nos seus dados -->
        <div class="card" v-for="(projeto, index) in meusProjetos" :key="index">
          <h3>{{ projeto.titulo }}</h3>
          <p>{{ projeto.descricao }}</p>
          <div class="tech-tags">
            <span v-for="tech in projeto.tecnologias" :key="tech" class="tag">
              {{ tech }}
            </span>
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
    descricao: 'Aplicação web para gerenciar, editar e acompanhar o progresso de atividades de forma intuitiva.',
    tecnologias: ['HTML', 'CSS', 'JavaScript', 'Bootstrap']
  },
  {
    titulo: 'Discretização e Análise de Dados',
    descricao: 'Script para processamento de arquivos CSV, realizando limpeza de dados e discretização de variáveis como idades.',
    tecnologias: ['Python', 'Data Analysis']
  },
  {
    titulo: 'Conformidade e Defesa de Redes',
    descricao: 'Investigação de requisitos e implementação de medidas de segurança (normas HIPAA) em laboratório de redes.',
    tecnologias: ['Cybersecurity', 'Infraestrutura']
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
  background-color: #1e293b; /* Fundo do card um pouco mais claro que o fundo da página */
  padding: 25px;
  border-radius: 12px;
  border: 1px solid #334155;
  transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
  border-color: #10b981; /* Destaque verde ao passar o mouse */
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