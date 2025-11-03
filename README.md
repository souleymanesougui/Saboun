<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="google-site-verification" content="jlqlGzhp6tqTZ-sI6PCuMjZ7FtCsctml2RRX5JizTrM" />
  <meta name="description" content="Arbre généalogique de la famille Saboun, visualisez les membres et leurs descendants facilement.">
  <title>Famille Saboun</title>
  <style>
    :root {
      --primary: #2C3E50;
      --secondary: #34495E;
      --accent: #8E44AD;
      --light: #ECF0F1;
      --dark: #2C3E50;
      --background: linear-gradient(135deg, #F8F9FA, #E9ECEF, #F8F9FA);
      --card-bg: rgba(255, 255, 255, 0.95);
      --shadow: 0 8px 32px rgba(44, 62, 80, 0.15);
      --text-dark: #2C3E50;
      --text-light: #7F8C8D;
    }

    * {
      box-sizing: border-box;
      transition: all 0.3s ease;
    }

    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: var(--background);
      color: var(--text-dark);
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
      padding-bottom: 40px;
      position: relative;
    }

    header {
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      width: 100%;
      text-align: center;
      padding: 20px 15px;
      font-size: clamp(20px, 6vw, 32px);
      font-weight: 600;
      letter-spacing: 1px;
      color: var(--light);
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
      margin-bottom: 15px;
      position: relative;
    }

    .credit-dot {
      position: absolute;
      top: 15px;
      left: 15px;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      cursor: pointer;
      opacity: 0.8;
      transition: all 0.3s ease;
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      background: rgba(255, 255, 255, 0.2);
    }

    .credit-dot:hover {
      opacity: 1;
      transform: scale(1.1);
      background: rgba(255, 255, 255, 0.3);
    }

    .credit-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.5);
      z-index: 2000;
      align-items: center;
      justify-content: center;
      padding: 20px;
    }

    .credit-modal-content {
      background: white;
      padding: 25px;
      border-radius: 20px;
      box-shadow: var(--shadow);
      width: 100%;
      max-width: 500px;
      max-height: 80vh;
      position: relative;
      text-align: center;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
    }

    .credit-modal h3 {
      margin-top: 0;
      color: var(--primary);
      margin-bottom: 15px;
      font-size: clamp(18px, 5vw, 24px);
    }

    .credit-modal p {
      color: var(--text-dark);
      font-size: clamp(14px, 4vw, 16px);
      line-height: 1.6;
      margin: 10px 0;
      text-align: left;
    }

    .close-modal {
      position: absolute;
      top: 15px;
      right: 15px;
      background: none;
      border: none;
      font-size: 28px;
      cursor: pointer;
      color: var(--text-light);
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .breadcrumb {
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      width: 100%;
      padding: 15px 10px;
      font-size: clamp(14px, 4vw, 18px);
      color: var(--light);
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      margin-bottom: 15px;
      text-align: center;
      word-wrap: break-word;
    }

    .breadcrumb a {
      color: var(--light);
      text-decoration: none;
      cursor: pointer;
      padding: 5px 8px;
      border-radius: 5px;
      transition: background-color 0.3s;
      display: inline-block;
      margin: 2px;
    }

    .breadcrumb a:hover {
      background-color: rgba(255, 255, 255, 0.2);
    }

    .breadcrumb span {
      margin: 0 8px;
      color: var(--accent);
    }

    #searchBox {
      margin: 20px 15px;
      padding: 15px 20px 15px 50px;
      font-size: clamp(14px, 4vw, 16px);
      width: 90%;
      max-width: 500px;
      border: none;
      border-radius: 50px;
      outline: none;
      background-color: var(--card-bg);
      color: var(--text-dark);
      box-shadow: var(--shadow);
      border: 2px solid var(--accent);
      background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="%238E44AD" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>');
      background-repeat: no-repeat;
      background-size: 18px;
      background-position: 20px center;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    #searchBox:focus {
      box-shadow: 0 0 0 3px rgba(142, 68, 173, 0.3);
      transform: translateY(-2px);
    }

    #searchBox::placeholder {
      color: var(--text-light);
      font-size: clamp(14px, 4vw, 16px);
    }

    #tree {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      padding: 15px;
      max-width: 1400px;
      width: 100%;
    }

    .person {
      text-align: center;
      cursor: pointer;
      padding: 12px;
      border-radius: 15px;
      background: var(--card-bg);
      box-shadow: var(--shadow);
      transition: all 0.3s ease;
      width: calc(50% - 20px);
      min-width: 140px;
      max-width: 200px;
    }

    .person:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 30px rgba(44, 62, 80, 0.2);
    }

    .person img {
      width: 100%;
      height: auto;
      aspect-ratio: 1;
      max-width: 120px;
      border-radius: 50%;
      border: 4px solid var(--accent);
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
      transition: transform 0.3s;
      object-fit: cover;
    }

    .person:hover img {
      transform: scale(1.05);
      border-color: var(--secondary);
    }

    .person-name {
      margin-top: 12px;
      font-size: clamp(14px, 4vw, 16px);
      font-weight: 600;
      color: var(--text-dark);
      padding: 6px 10px;
      border-radius: 8px;
      background: linear-gradient(to right, rgba(142, 68, 173, 0.1), rgba(52, 73, 94, 0.1));
      word-wrap: break-word;
      line-height: 1.3;
    }

    #backBtn {
      margin: 15px;
      padding: 12px 25px;
      font-size: clamp(14px, 4vw, 16px);
      width: auto;
      min-width: 160px;
      border: none;
      border-radius: 50px;
      outline: none;
      background: linear-gradient(135deg, var(--secondary), var(--accent));
      color: white;
      box-shadow: var(--shadow);
      cursor: pointer;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      font-weight: 600;
      letter-spacing: 0.5px;
    }

    #backBtn:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(44, 62, 80, 0.3);
      background: linear-gradient(135deg, var(--primary), var(--accent));
    }

    #backBtn:active {
      transform: translateY(1px);
    }

    p {
      font-size: clamp(14px, 4vw, 16px);
      color: var(--text-light);
      text-align: center;
      max-width: 90%;
      line-height: 1.5;
      padding: 15px;
      background: var(--card-bg);
      border-radius: 12px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
      margin: 10px;
    }

    /* Améliorations pour mobile */
    @media (max-width: 480px) {
      .person {
        width: calc(50% - 10px);
        padding: 10px;
      }
      
      .person img {
        max-width: 100px;
      }
      
      #searchBox {
        width: 95%;
        margin: 15px 10px;
        padding: 12px 15px 12px 45px;
      }
      
      .credit-dot {
        top: 10px;
        left: 10px;
        width: 35px;
        height: 35px;
        font-size: 18px;
      }
      
      .credit-modal-content {
        padding: 20px 15px;
        margin: 10px;
      }
      
      header {
        padding: 15px 10px;
      }
      
      #tree {
        gap: 15px;
        padding: 10px;
      }
    }

    @media (max-width: 320px) {
      .person {
        width: 100%;
        max-width: 150px;
      }
    }

    /* Animation pour le modal */
    @keyframes modalFadeIn {
      from {
        opacity: 0;
        transform: scale(0.9);
      }
      to {
        opacity: 1;
        transform: scale(1);
      }
    }

    .credit-modal-content {
      animation: modalFadeIn 0.3s ease-out;
    }
  </style>
</head>
<body>
  <div class="credit-dot" onclick="openCreditModal()">🎲</div>
  
  <div id="creditModal" class="credit-modal">
    <div class="credit-modal-content">
      <button class="close-modal" onclick="closeCreditModal()">×</button>
      <h3>🌟 Réalisation</h3>
      <p>
        <strong>Message de présentation</strong>
        <br><br>
        Nous, <strong>Souleymane Sougui</strong> et <strong>Aht</strong>, avons créé ce site web dédié à notre <strong>arbre généalogique familial Saboun</strong>.
        <br>
        Notre objectif est de <strong>préserver la mémoire</strong> de notre grande famille et de <strong>rassembler toutes les générations</strong>.
        <br>
        Ce projet marque une étape importante pour <strong>honorer nos ancêtres</strong> et <strong>transmettre notre histoire</strong> aux plus jeunes.
        <br>
        Chaque nom, chaque photo, chaque lien représente <strong>une partie vivante de notre héritage</strong>.
        <br>
        Ce site montre notre <strong>fierté d'appartenir à la famille Saboun</strong>.
        <br>
        C'est aussi un moyen de <strong>renforcer les liens familiaux</strong>, peu importe la distance.
        <br>
        Nous espérons que chacun contribuera à <strong>enrichir cette histoire commune</strong>.
        <br>
        Ce projet a été <strong>réalisé avec passion et respect</strong>.
        <br>
        <strong>Date de création : 31 octobre 2025.</strong>
      </p>
    </div>
  </div>

  <header id="mainHeader">Famille Saboun</header>
  <div id="breadcrumb" class="breadcrumb" style="display: none;"></div>
  <input id="searchBox" type="text" placeholder="Rechercher un nom..." oninput="searchPerson()">
  <button id="backBtn" onclick="goBack()">⬅ Retour à l'accueil</button>
  <div id="tree"></div>
  <script>
    const family = {
      name: "SABOUN",
      children: [
        { name: "KISSEYA",
          children: [
            { name: "IBRAHIM HANGATA" },
            { name: "YOUSSOUF HANGATA" },
            { name: "BICHARA HANGATA" },
            { name: "TOMBO HANGATA" },
            { name: "SIMBIL HANGATA" },
            { name: "ZARA HANGATA" }
          ]
        },
        { name: "HALIME",
          children: [
            { name: "MARIAM DJOROK" },
            { name: "BACHÉ DJOROK" },
            { name: "SOUNISSI DJOROK" },
            { name: "HISSEN DJOROK" }
          ]
        },
        { name: "HATOU",
          children: [
            { name: "MARIAM DJOROK" }
          ]
        },
        { name: "MATTI",
          children: [
            { name: "HASSAN MATTI" },
            { name: "HISSEN MATTI" },
            { name: "KHADIJÉ MATTI" },
            { name: "DJECKIDO MATTI" },
            { name: "ZARA MATTI" }
          ]
        },
        { name: "NIMIR",
          children: [
            { name: "HOTTOUMA NIMIR" },
            { name: "HOURRO NIMIR" }
          ]
        },
        { name: "KORÊ",
          children: [
            { name: "NAGUITI KORÊ" },
            { name: "GOUKOUNNI KORÊ" },
            { name: "BILLA KORÊ" },
            { name: "JAGOUAR KORÊ" },
            { name: "HAGAR KORÊ" },
            { name: "SAFIA KORÊ" },
            { name: "GACHI KORÊ" }
          ]
        },
        { name: "AHMAT",
          children: [
            { name: "SALEH AHMAT" },
            { name: "MAHAMAT AHMAT" },
            { name: "MOUNNA AHMAT" },
            { name: "FATIMÉ AHMAT" },
            { name: "KHADIJÉ AHMAT" },
            { name: "ABDRAMAN AHMAT" }
          ]
        },
        { name: "DJIMET",
          children: [
            { name: "BOUDIN DJIMET" },
            { name: "ADOUM DJIMET" },
            { name: "KHADIDJA DJIMET" },
            { name: "ACHE DJIMET" }
          ]
        },
        { name: "MARADA",
          children: [
            { name: "HOURRO BOLI" },
            { name: "TORBOYO BOLI" },
            { name: "MOURRA BOLI" },
            { name: "BILLA BOLI" },
            { name: "KOREÏ BOLI" },
            { name: "BRAHIM BOLI" },
            { name: "ABDELGADIR BOLI" }
          ]
        }
      ]
    };

    let history = [];
    let currentPath = [];

    // Fonctions pour le modal de crédit
    function openCreditModal() {
      document.getElementById('creditModal').style.display = 'flex';
      document.body.style.overflow = 'hidden';
    }

    function closeCreditModal() {
      document.getElementById('creditModal').style.display = 'none';
      document.body.style.overflow = 'auto';
    }

    // Fermer le modal en cliquant à l'extérieur ou avec Échap
    document.getElementById('creditModal').addEventListener('click', function(e) {
      if (e.target === this) {
        closeCreditModal();
      }
    });

    document.addEventListener('keydown', function(e) {
      if (e.key === 'Escape' && document.getElementById('creditModal').style.display === 'flex') {
        closeCreditModal();
      }
    });

    // Fonctions de l'arbre généalogique
    function displayPerson(person) {
      const tree = document.getElementById("tree");
      const mainHeader = document.getElementById("mainHeader");
      const breadcrumb = document.getElementById("breadcrumb");
      
      tree.innerHTML = "";
      document.getElementById("backBtn").style.display = history.length ? "inline-block" : "none";

      // Mettre à jour le chemin actuel
      if (person !== currentPath[currentPath.length - 1]) {
        currentPath.push(person);
      }

      // Afficher le fil d'Ariane
      updateBreadcrumb();

      if (!person.children || person.children.length === 0) {
        const msg = document.createElement("p");
        msg.innerText = "La liste des enfants n'est pas encore complète, elle est en cours d'élaboration.";
        tree.appendChild(msg);
        return;
      }

      person.children.forEach(child => {
        const div = document.createElement("div");
        div.className = "person";
        div.onclick = () => {
          history.push(person);
          displayPerson(child);
        };

        const img = document.createElement("img");
        img.src = child.photo ? "photos/" + child.photo : "default.jpg";
        img.alt = `Photo de ${child.name}`;
        img.onerror = function() {
          this.src = 'data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="170" height="170" viewBox="0 0 170 170"><rect width="170" height="170" fill="%23ECF0F1" rx="85"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" font-family="Arial" font-size="60" fill="%238E44AD">' + child.name.charAt(0) + '</text></svg>';
        };

        const name = document.createElement("div");
        name.className = "person-name";
        name.textContent = child.name;

        div.appendChild(img);
        div.appendChild(name);
        tree.appendChild(div);
      });
    }

    function updateBreadcrumb() {
      const mainHeader = document.getElementById("mainHeader");
      const breadcrumb = document.getElementById("breadcrumb");
      
      if (currentPath.length <= 1) {
        mainHeader.style.display = "block";
        breadcrumb.style.display = "none";
        mainHeader.textContent = "Famille Saboun";
      } else {
        mainHeader.style.display = "none";
        breadcrumb.style.display = "block";
        
        let breadcrumbHTML = "Enfants de ";
        
        currentPath.forEach((person, index) => {
          if (index > 0) {
            if (index > 1) {
              breadcrumbHTML += '<span>›</span>';
            }
            if (index === currentPath.length - 1) {
              breadcrumbHTML += `<strong>${person.name}</strong>`;
            } else {
              breadcrumbHTML += `<a onclick="navigateToPath(${index})">${person.name}</a>`;
            }
          }
        });
        
        breadcrumb.innerHTML = breadcrumbHTML;
      }
    }

    function navigateToPath(index) {
      const targetPerson = currentPath[index];
      currentPath = currentPath.slice(0, index + 1);
      history = currentPath.slice(0, -1);
      displayPerson(targetPerson);
    }

    function displayRoot() {
      const tree = document.getElementById("tree");
      tree.innerHTML = "";
      history = [];
      currentPath = [family];

      const div = document.createElement("div");
      div.className = "person";
      div.onclick = () => {
        history.push(family);
        displayPerson(family);
      };

      const img = document.createElement("img");
      img.src = "default.jpg";
      img.alt = `Photo de ${family.name}`;
      img.onerror = function() {
        this.src = 'data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="170" height="170" viewBox="0 0 170 170"><rect width="170" height="170" fill="%23ECF0F1" rx="85"/><text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" font-family="Arial" font-size="60" fill="%238E44AD">' + family.name.charAt(0) + '</text></svg>';
      };

      const name = document.createElement("div");
      name.className = "person-name";
      name.textContent = family.name;

      div.appendChild(img);
      div.appendChild(name);
      tree.appendChild(div);

      document.getElementById("backBtn").style.display = "none";
      updateBreadcrumb();
    }

    function goBack() {
      if (history.length > 0) {
        const prev = history.pop();
        currentPath.pop();
        displayPerson(prev);
      } else {
        displayRoot();
      }
    }

    function searchPerson() {
      const query = document.getElementById("searchBox").value.trim().toLowerCase();
      if (!query) return displayRoot();

      const path = findPath(family, query);
      if (path) {
        history = path.slice(0, -1);
        currentPath = [...path];
        displayPerson(path[path.length - 1]);
      }
    }

    function findPath(node, target, path = []) {
      if (node.name.toLowerCase().includes(target)) return [...path, node];
      if (!node.children) return null;
      for (let child of node.children) {
        const result = findPath(child, target, [...path, node]);
        if (result) return result;
      }
      return null;
    }

    // Initialisation
    currentPath = [family];
    displayRoot();
  </script>
</body>
</html>
