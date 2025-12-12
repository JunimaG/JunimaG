# 👋 ¡Hola! Soy Juan Gatica

Bienvenido a mi repositorio personal. Este espacio funciona como mi carta de presentación en GitHub, donde comparto quién soy, qué hago y en qué estoy trabajando.

---

## 🚀 Sobre mí
- 🎓 Estudiante de **Licenciatura en Ciencias Físicas** y **Ingeniería Eléctrica**.  
- 💻 Apasionado por la programación y el desarrollo de soluciones prácticas.  
- 🔍 Me interesa la intersección entre la física, la electrónica y el software.  
- 📚 Siempre aprendiendo y explorando nuevas tecnologías.

---

## 🛠️ Tecnologías y lenguajes que manejo
- **Python**  
- **C**  
- **C++**  
- **Arduino**  
- **Markdown**  
- **GitHub**
- **LinkedIn**

---

## ⚡ Áreas de interés
- Programación y automatización  
- Electrónica y microcontroladores  
- Física computacional  
- Simulaciones y análisis de datos  
- Desarrollo de proyectos interdisciplinarios
- Astrofísica

---

## 📌 Proyectos destacados
- 🔧 *Próximamente agregaré mis proyectos más importantes aquí.*  
- 🧪 Estoy construyendo mi portafolio combinando programación, física y electrónica.

---

## ⭐ Gracias por visitar mi perfil
Si te interesa lo que hago, ¡no dudes en seguirme o ver mis repositorios!


<!-- index.html (versión API) -->
<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Playlist dinámica</title>
  <style>
    body { font-family: system-ui, sans-serif; margin: 24px; }
    .grid { display: grid; grid-template-columns: repeat(auto-fill,minmax(240px,1fr)); gap: 16px; }
    .card { border: 1px solid #e5e7eb; border-radius: 8px; overflow: hidden; background: #fff; }
    .thumb { aspect-ratio: 16/9; width: 100%; object-fit: cover; display: block; }
    .meta { padding: 8px 12px; }
    .title { font-weight: 600; font-size: 0.95rem; margin: 0 0 4px; }
    .desc { color: #6b7280; font-size: 0.85rem; margin: 0; }
  </style>
</head>
<body>
  <h1>Playlist dinámica</h1>
  <div class="grid" id="grid"></div>
  <script type="module">
    const API_KEY = "TU_API_KEY";
    const PLAYLIST_ID = "PLXXXXXXXXXXXX";
    const URL = `https://www.googleapis.com/youtube/v3/playlistItems?part=snippet&maxResults=50&playlistId=${PLAYLIST_ID}&key=${API_KEY}`;

    const grid = document.getElementById('grid');

    async function load() {
      const res = await fetch(URL);
      const data = await res.json();
      const items = (data.items || []).map(i => {
        const s = i.snippet;
        const vid = s.resourceId.videoId;
        const title = s.title;
        const desc = s.description?.split('\n')[0] || '';
        const thumb = s.thumbnails?.medium?.url || `https://img.youtube.com/vi/${vid}/0.jpg`;
        return { vid, title, desc, thumb };
      });

      grid.innerHTML = items.map(v => `
        <a class="card" href="https://www.youtube.com/watch?v=${v.vid}" target="_blank" rel="noopener">
          <img class="thumb" src="${v.thumb}" alt="${v.title}">
          <div class="meta">
            <p class="title">${v.title}</p>
            <p class="desc">${v.desc}</p>
          </div>
        </a>
      `).join('');
    }
    load();
  </script>
</body>
</html>


