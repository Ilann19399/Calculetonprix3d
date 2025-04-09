<html lang="fr"><head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Test Calculateur</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 600px; margin: auto; padding: 20px; }
    label { display: block; margin-top: 10px; }
    input { width: 100%; padding: 5px; margin-top: 5px; }
    button { margin-top: 20px; padding: 10px 15px; font-size: 16px; }
    .resultat { margin-top: 20px; padding: 15px; border: 1px solid #ccc; border-radius: 5px; }
  </style>
</head>
<body>
  <h1>Test Calculateur Impression 3D</h1>

  <label>Coûts matière par gramme (€):
    <input type="number" id="matiere" value="0.05" step="0.01">
  </label>

  <label>Temps d'impression (heures):
    <input type="number" id="temps" value="3" step="0.1">
  </label>

  <label>Coûts main d'œuvre (€):
    <input type="number" id="main" value="5" step="0.1">
  </label>

  <label>Poids de la pièce (grammes):
    <input type="number" id="poids" value="50">
  </label>

  <label>Dépenses fixes mensuelles (€):
    <input type="number" id="depenses" value="50">
  </label>

  <label>Nombre d'impressions par mois:
    <input type="number" id="nbImpressions" value="10">
  </label>

  <label>Marge souhaitée (%):
    <input type="number" id="margeSouhaitee" value="30">
  </label>

  <button onclick="calculer()">Calculer</button>

  <div class="resultat" id="resultat"></div>

  <script>
    function calculer() {
      const matiere = parseFloat(document.getElementById("matiere").value) || 0;
      const temps = parseFloat(document.getElementById("temps").value) || 0;
      const main = parseFloat(document.getElementById("main").value) || 0;
      const poids = parseFloat(document.getElementById("poids").value) || 0;
      const depenses = parseFloat(document.getElementById("depenses").value) || 0;
      const nbImpressions = parseFloat(document.getElementById("nbImpressions").value) || 1;
      const margeSouhaitee = parseFloat(document.getElementById("margeSouhaitee").value) || 0;

      const fraisFixesMoyens = depenses / nbImpressions;
      const coutMatiere = matiere * poids;
      const coutMain = main;
      const coutTotal = coutMatiere + coutMain + fraisFixesMoyens;
      const prixVente = coutTotal * (1 + margeSouhaitee / 100);
      const margeReelle = prixVente - coutTotal;

      document.getElementById("resultat").innerHTML = `
        <strong>Détail du calcul :</strong><br>
        Coût matière : ${coutMatiere.toFixed(2)} €<br>
        Main d'œuvre : ${coutMain.toFixed(2)} €<br>
        Frais fixes moyens : ${fraisFixesMoyens.toFixed(2)} €<br>
        <strong>Coût total : ${coutTotal.toFixed(2)} €</strong><br>
        Prix de vente conseillé (avec ${margeSouhaitee}% de marge) : <strong>${prixVente.toFixed(2)} €</strong><br>
        Marge réalisée : ${margeReelle.toFixed(2)} €
      `;
    }
  </script>



</body></html>
