<script>
  import * as d3 from "d3";
  import { onMount } from "svelte";

  onMount(() => {
    const script = document.createElement("script");
    script.src = "https://public.flourish.studio/resources/embed.js";
    script.async = true;
    document.body.appendChild(script);
  });

  let paises = [
  { nombre: "Estados Unidos", oro: 98, plata: 25 },
  { nombre: "China", oro: 92, plata: 28 },
  { nombre: "Rusia", oro: 87, plata: 32 },
  { nombre: "Francia", oro: 77, plata: 38 },
  { nombre: "Reino Unido", oro: 71, plata: 43 },
  { nombre: "Japón", oro: 63, plata: 50 },
  { nombre: "Alemania", oro: 54, plata: 56 },
  { nombre: "Corea del Sur", oro: 42, plata: 45 },
  { nombre: "Italia", oro: 33, plata: 35 },
  { nombre: "Brasil", oro: 24, plata: 23 }
];


  const escalaFactor = 4;
  const max = d3.max(paises, d => d.medallas / escalaFactor);
  let escalaColumnas = d3.scaleLinear().domain([0, max]).range([0, 500]);
</script>

<main>
  <div class="header-container">
    <img src="/images/logo.png" alt="Logo JJOO" class="logo-jjoo" />
    <h1>Juegos Olímpicos: París 2024</h1>
    <img src="/images/paris.png" alt="Logo París 2024" class="logo-paris" />
  </div>

  <p class="intro">Los Juegos Olímpicos de París 2024 marcaron un hito al reunir a más de 10.000 atletas de 204 países en 32 disciplinas
     deportivas, celebradas en escenarios emblemáticos de la capital francesa. Durante 10 días de intensa competencia, se
      vivieron momentos inolvidables que destacaron el espíritu deportivo y la excelencia atlética.</p>

  

  <h2>Medallero Olimpico </h2>
  <h6>(1 ícono = 4 medallas reales)</h6>

  {#each paises as pais}
  <div class="fila">
    <div class="etiqueta">
      <img src={`/images/${pais.nombre}.svg`} alt={pais.nombre} class="bandera" />
    </div>

    <div class="medallas-container">
      <!-- FILA ORO -->
      <div class="fila-medalla">
        <div class="medallas">
          {#each Array(Math.floor(pais.oro / escalaFactor)) as _, j}
            <img src="/images/medalla.svg" alt="medalla de oro" class="medalla" />
          {/each}
        </div>
        <div class="numero-derecha oro">{pais.oro}</div>
      </div>

      <!-- FILA PLATA -->
      <div class="fila-medalla">
        <div class="medallas">
          {#each Array(Math.floor(pais.plata / escalaFactor)) as _, j}
            <img src="/images/Medalla_plata.svg" alt="medalla de plata" class="medalla" />
          {/each}
        </div>
        <div class="numero-derecha plata">{pais.plata}</div>
      </div>
    </div>
  </div>
{/each}





<h2 class="graficos-header">Comparación de medallas de Paris 2024</h2>

<p class="texto-graficos-header">
</p>

<div class="graficos-wrapper">
  <section class="graficos-container">

    <!-- Gráfico 1: Liderazgo en Medallas (Flourish) -->
<div class="flourish-embed flourish-chart" data-src="visualisation/23327100">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/23327100/thumbnail" width="100%" alt="chart visualization" />
  </noscript>
</div>


    <!-- Gráfico 2: Comparación por País (Flourish) -->
<div class="flourish-embed flourish-chart" data-src="visualisation/23327751">
  <script src="https://public.flourish.studio/resources/embed.js"></script>
  <noscript>
    <img src="https://public.flourish.studio/visualisation/23327751/thumbnail" width="100%" alt="chart visualization" />
  </noscript>
</div>


  </section>
</div>


  <div class="video-container">
    <iframe 
      width="1000" 
      height="562" 
      src="https://www.youtube.com/embed/vy6FivZHRjQ" 
      title="YouTube video player" 
      frameborder="0" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>

  <footer class="footer">
    <p>© 2025 Juegos Olímpicos - Todos los derechos reservados</p>
    <div class="footer-social">
      <a href="https://www.linkedin.com/in/benja-sanchez-salas-4a8769360/" target="_blank" class="social-link">Benjamin Sanchez Salas</a>
      <a href="http://www.linkedin.com/in/mateo-tejera-089b89270" target="_blank" class="social-link">Mateo Tejera</a>
    </div>
  </footer>
</main>

<style>
  .header-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 3rem; 
  }

  .header-container h1 {
    flex: 1; 
    text-align: center;
    font-family: 'Avenir', sans-serif;
    font-weight: 500;
    color: #000000;
    margin: 0;
  }

  .logo-jjoo,
  .logo-paris {
    width: 100px; 
    height: auto;
  }

  .intro {
    font-family: "Avenir", sans-serif;
    font-weight: 200;
    text-align: justify;
    margin-left: 50px;
    margin-right: 50px;
  }


  .video-container {
    display: flex;
    justify-content: center;
    margin-top: 2rem;
    margin-bottom: 0rem;
    
  }

  .video-container iframe {
    width: 100%; 
    max-width: 1000px; 
    height: 562px; 
    border-radius: 12px; 
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1); 
    margin-top: 0px;

  }

  :global(body) {
    margin: 0;
    font-family: 'Avenir', sans-serif;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    color: #333;
  }
  
  main {
    position: relative;
    z-index: 1;
    backdrop-filter: blur(50px);
    background-color: rgba(255, 255, 255, 0.8);
    padding: 2rem;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    margin: 2rem auto;
    width: 1200px;
  }

  h2 {
    font-family: 'Avenir', sans-serif;
    font-weight: 300;
    margin-left: 50px;
    margin-bottom: 0rem;
    color: #000000;
  }

  h6{
    margin-left: 50px;
    margin-top: 0px;
  }

  .fila {
  display: flex;
  align-items: center;
  margin-bottom: 1.5rem;
  width: 100%;
  padding: 0;
}

.etiqueta {
  width: 160px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.bandera {
  width: 70px;
  height: auto;
}

.medallas-container {
  display: flex;
  flex-direction: column;
  gap: 5px;
  width: 100%;
}

.fila-medalla {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding-right: 50px; 
}

.medallas {
  display: flex;
  gap: 2px;
  flex-wrap: nowrap;
  flex: 1;
}

.medalla {
  width: 36px;
  height: 36px;
}

.numero-derecha {
  width: 60px;
  text-align: right;
  font-weight: bold;
  font-size: 1rem;
  font-family: 'Avenir', sans-serif;
}

.numero-derecha.oro {
  color: #DAA520;
}

.numero-derecha.plata {
  color: #C0C0C0;
}




  .graficos-header {
    margin-top: 5rem;
    font-family: 'Avenir', sans-serif;
    font-weight: 300;
    margin-left: 50px;
    margin-bottom: 0;
    color: #000000;
    
  }

  .texto-graficos-header{
    font-family: "Avenir", sans-serif;
    font-weight: 200;
    text-align: justify;
    margin-left: 50px;
    margin-right: 50px;
  }

  .graficos-wrapper {
  margin-left: 70px;
  margin-right: 70px;
  margin-bottom: 0px;
}

.datawrapper-embed {
  flex: 1;
  max-width: 48%;
  min-width: 300px;
  box-sizing: border-box;
  
}


  .graficos-container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 2rem;
    margin-top: 2rem;
    flex-wrap: wrap;
    margin-bottom: 0px;
  }
  .flourish-embed {
  width: 100%;
  aspect-ratio: 16/9; /* relación moderna que evita el corte */
  max-width: 100%;
  margin-bottom: 2rem;
  overflow: hidden;
}




  .footer {
    background-color: #003366;
    color: white;
    text-align: center;
    padding: 1rem;
    margin-top: 3rem;
    font-family: 'Avenir', sans-serif;
    font-size: 0.9rem;
    border-radius: 0 0 12px 12px;
    clear: both;
    margin-left: 70px;
    margin-right: 70px;
  }

  .footer-social {
    margin-top: 1rem;
  }

  .social-link {
    color: white;
    text-decoration: none;
    margin: 0 0.5rem;
    font-size: 0.9rem;
  }

  .social-link:hover {
    text-decoration: underline;
  }
</style>
