<template>
    <main class="row justify-content-around">

      <h1 class="col-12">Page spécifique pour eleve et prof</h1>

      <div class="col-5 border">
        <h2>Communauté</h2>
        <p>personne ou groupe suivi, musique et instrument suivi, prof suivi, artiste suivi</p>
        <p>mur actu dédié a la musique</p>
      </div>

      <div class="col-5 border">
        <h2>Tableau de bords</h2>
        <p>Renvoie a 2 pages différentes : </p>
        <p>si prof = gestion et construction de la plateforme de lecon, mes disponibilites </p>
        <p>si eleve = gestion, suivi des lecons dont je participe, mes disponibilites </p>
      </div>

      <div class="col-5 border">
        <h2>Music world</h2>
        <p>Acces global a toute la base de donnée :<br>
        recherche des concerts, groupe, festival pres de chez soi</p>
        <p>achat et echange de instrument musique</p>
        <p>Decouverte de nouveaux instruments, nouvelles musique</p>
      </div>
      
      <aside>
      
      <ul>PAGE SPECIAL musicien, groupe, festival
        <li>Tableau de bord : Mes publications: video, presse... pour se promouvoir \ recommandation, avis \ messagerie</li>
        <li>Mes dispo \ planning : possibilité de reservation</li>
        <li>Mes besoins : musicien(renvoie au prof/etudiant), groupe, salle, matos, recherche de bénévolat</li>
        <li>Mon site web dédié : presentation / tarif / merchandising, possibilite de personnaliser sa page et son domaine</li>
        <li>Music event : trouver des concerts, groupe, festival pres de chez soi</li>
      </ul>
      
      </aside>
    </main>
</template>

<script>
export default {
  layout: 'home'
}
</script>