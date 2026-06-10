# philosti2d.github.io
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Philo STI2D — 7 notions du bac</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;700&family=IBM+Plex+Sans:ital,wght@0,400;0,600;1,400&family=IBM+Plex+Mono:wght@400;600&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#FAFBF7; --grid:rgba(27,42,74,.06); --ink:#1B2A4A; --ink-soft:#4A5878;
    --card:#FFFFFF; --line:#E3E6DD; --accent:#2F6FED;
    --radius:14px; --mono:'IBM Plex Mono',monospace;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth}
  body{
    font-family:'IBM Plex Sans',sans-serif; color:var(--ink); background:var(--paper);
    background-image:linear-gradient(var(--grid) 1px,transparent 1px),linear-gradient(90deg,var(--grid) 1px,transparent 1px);
    background-size:24px 24px; line-height:1.55;
  }
  /* ---------- En-tête ---------- */
  header{padding:46px 20px 18px; max-width:980px; margin:0 auto;}
  .kicker{font-family:var(--mono); font-size:.75rem; letter-spacing:.18em; text-transform:uppercase; color:var(--ink-soft);}
  h1{font-family:'Space Grotesk',sans-serif; font-size:clamp(1.9rem,5vw,3rem); line-height:1.05; margin:.35em 0 .3em;}
  h1 em{font-style:normal; color:var(--accent);}
  .sub{color:var(--ink-soft); max-width:560px; font-size:.97rem;}
  /* ---------- Nav notions ---------- */
  nav{position:sticky; top:0; z-index:50; background:rgba(250,251,247,.92); backdrop-filter:blur(6px); border-bottom:1px solid var(--line);}
  .tabs{display:flex; gap:8px; overflow-x:auto; padding:12px 20px; max-width:980px; margin:0 auto; scrollbar-width:none;}
  .tabs::-webkit-scrollbar{display:none}
  .tab{
    flex:0 0 auto; font-family:var(--mono); font-size:.8rem; font-weight:600;
    border:1.5px solid var(--line); background:var(--card); color:var(--ink-soft);
    border-radius:999px; padding:8px 15px; cursor:pointer; transition:all .15s; white-space:nowrap;
  }
  .tab:hover{border-color:var(--ink-soft)}
  .tab.active{background:var(--tc,var(--accent)); border-color:var(--tc,var(--accent)); color:#fff;}
  .tab:focus-visible{outline:3px solid var(--accent); outline-offset:2px;}
  /* ---------- Fiche ---------- */
  main{max-width:980px; margin:0 auto; padding:26px 20px 80px;}
  .fiche{display:none; animation:fadeUp .3s ease;}
  .fiche.show{display:block}
  @keyframes fadeUp{from{opacity:0; transform:translateY(10px)} to{opacity:1; transform:none}}
  @media (prefers-reduced-motion:reduce){.fiche{animation:none}}
  .fiche-head{display:flex; align-items:flex-end; justify-content:space-between; gap:16px; flex-wrap:wrap; margin-bottom:6px;}
  .ref{font-family:var(--mono); font-size:.78rem; color:var(--ink-soft); letter-spacing:.12em;}
  .fiche h2{font-family:'Space Grotesk',sans-serif; font-size:clamp(1.7rem,4.5vw,2.5rem); color:var(--c);}
  .one-liner{font-size:1.02rem; color:var(--ink-soft); border-left:3px solid var(--c); padding-left:14px; margin:10px 0 24px;}
  /* chrono */
  .timer{font-family:var(--mono); font-size:.85rem; border:1.5px solid var(--line); background:var(--card);
    border-radius:999px; padding:8px 16px; cursor:pointer; color:var(--ink);}
  .timer.on{border-color:var(--c); color:var(--c); font-weight:600;}
  /* blocs */
  .grid2{display:grid; grid-template-columns:1fr 1fr; gap:16px;}
  @media(max-width:760px){.grid2{grid-template-columns:1fr}}
  .bloc{background:var(--card); border:1px solid var(--line); border-radius:var(--radius); padding:18px 20px; margin-bottom:16px;}
  .bloc h3{font-family:var(--mono); font-size:.74rem; letter-spacing:.16em; text-transform:uppercase; color:var(--c); margin-bottom:10px;}
  .bloc ul{padding-left:18px;}
  .bloc li{margin-bottom:7px;}
  .bloc li::marker{color:var(--c)}
  .auteur{font-weight:600;}
  /* schéma */
  .schema{font-family:var(--mono); font-size:.78rem; line-height:1.45; background:var(--ink); color:#E9EDF7;
    border-radius:var(--radius); padding:18px; overflow-x:auto; white-space:pre; margin-bottom:16px;}
  .schema b{color:#9DC1FF; font-weight:600;}
  .schema .t{color:#7E8CB0; font-size:.7rem; letter-spacing:.16em; display:block; margin-bottom:8px;}
  /* citations */
  .cite{font-style:italic; background:color-mix(in srgb,var(--c) 7%,white); border:1px solid color-mix(in srgb,var(--c) 25%,white);
    border-radius:var(--radius); padding:13px 16px; margin-bottom:10px;}
  .cite span{display:block; font-style:normal; font-family:var(--mono); font-size:.74rem; color:var(--ink-soft); margin-top:5px;}
  /* vidéos */
  .videos{display:grid; grid-template-columns:repeat(auto-fit,minmax(240px,1fr)); gap:12px;}
  .vid{display:block; text-decoration:none; background:var(--card); border:1.5px solid var(--line);
    border-radius:var(--radius); padding:14px 16px; color:var(--ink); transition:all .15s;}
  .vid:hover{border-color:var(--c); transform:translateY(-2px); box-shadow:0 6px 18px rgba(27,42,74,.08);}
  .vid .chan{font-family:var(--mono); font-size:.72rem; text-transform:uppercase; letter-spacing:.12em; color:var(--c); display:flex; align-items:center; gap:6px;}
  .vid .chan::before{content:"▶"; font-size:.65rem;}
  .vid .vtitle{font-weight:600; margin:4px 0 2px; font-size:.95rem;}
  .vid .dur{font-size:.8rem; color:var(--ink-soft);}
  .vid.search .chan::before{content:"🔍";}
  /* bonus / footer */
  .method td,.method th{border:1px solid var(--line); padding:9px 12px; text-align:left; font-size:.92rem;}
  .method{border-collapse:collapse; width:100%; background:var(--card);}
  .method th{font-family:var(--mono); font-size:.74rem; text-transform:uppercase; letter-spacing:.1em; background:color-mix(in srgb,var(--c) 8%,white);}
  footer{text-align:center; padding:30px; font-family:var(--mono); font-size:.78rem; color:var(--ink-soft);}
</style>
</head>
<body>

<header>
  <div class="kicker">Bac techno · Terminale STI2D · Philosophie</div>
  <h1>Les 7 notions,<br><em>fiche par fiche.</em></h1>
  <p class="sub">Une notion = une fiche relisible en 5 minutes : définition, problématiques, auteurs, schéma, exemples, citations… et les vidéos qui vont avec. Lance le chrono et c'est parti.</p>
</header>

<nav><div class="tabs" id="tabs" role="tablist"></div></nav>

<main id="main"></main>

<footer>Bon courage pour le bac 💪 — relis une fiche par jour, regarde la vidéo le lendemain.</footer>

<script>
const DATA = [
{
id:"art", titre:"L'art", emoji:"🎨", couleur:"#C2452D",
oneliner:"Création visant le beau ou le sens — sans utilité pratique directe, contrairement à la technique.",
definition:[
 "<b>Étymologie</b> : latin <i>ars</i> = savoir-faire (au départ, art = artisanat !)",
 "Création d'œuvres visant le <b>beau</b> ou l'<b>expression</b>, sans but utilitaire direct."
],
problematiques:[
 "L'art imite-t-il la nature ou la transforme-t-il ?",
 "Le beau est-il objectif ou subjectif (« des goûts et des couleurs… ») ?",
 "L'art doit-il être utile ? Dire la vérité ?"
],
auteurs:[
 "<span class='auteur'>Platon</span> : l'art = imitation d'imitation (mimésis) → il éloigne de la vérité.",
 "<span class='auteur'>Aristote</span> : la tragédie purge nos passions (<b>catharsis</b>).",
 "<span class='auteur'>Kant</span> : le beau = « ce qui plaît universellement sans concept » — subjectif mais prétend à l'universel.",
 "<span class='auteur'>Hegel</span> : l'art rend une idée sensible, il exprime l'esprit d'une époque.",
 "<span class='auteur'>Bergson</span> : l'artiste nous fait voir ce que l'habitude nous cache."
],
schema:`<span class="t">ART / TECHNIQUE / NATURE</span>
<b>NATURE</b> (donné)       <b>TECHNIQUE</b> (utile)      <b>ART</b> (beau / sens)
l'arbre qui pousse → la chaise en bois  →  la sculpture en bois
sans intention       but : s'asseoir       but : émouvoir, faire penser`,
exemples:[
 "<b>La Fontaine de Duchamp (1917)</b> : un urinoir signé en musée → l'art est-il dans l'objet ou dans le regard ?",
 "<b>Guernica (Picasso)</b> : l'art dénonce la guerre mieux qu'un discours.",
 "<b>L'IA générative (Midjourney)</b> : une image sans artiste humain est-elle de l'art ? (lie art et technique — parfait en STI2D)"
],
citations:[
 ["Le génie est le talent de produire ce dont on ne saurait donner de règle.","Kant"],
 ["L'art est ce qui rend la vie plus intéressante que l'art.","Robert Filliou"]
],
videos:[
 {chan:"SchoolMouv", titre:"Révisions bac philo : L'art", dur:"~5 min", url:"https://www.youtube.com/watch?v=nnZWEzq9HvU"},
 {chan:"Cyrus North", titre:"« art » sur sa chaîne (Coup de Phil')", dur:"5–10 min", url:"https://www.youtube.com/results?search_query=cyrus+north+l%27art+philosophie", search:true},
 {chan:"Le Précepteur", titre:"« L'art » — explication de la notion", dur:"extraits dispo", url:"https://www.youtube.com/results?search_query=le+pr%C3%A9cepteur+l%27art", search:true}
]
},
{
id:"justice", titre:"La justice", emoji:"⚖️", couleur:"#7A3FA0",
oneliner:"Distinguer le LÉGAL (conforme à la loi) du LÉGITIME (moralement juste) : tout part de là.",
definition:[
 "<b>Institution</b> : tribunaux, lois, juges → le <b>légal</b>.",
 "<b>Valeur morale</b> : ce qui est juste, équitable → le <b>légitime</b>."
],
problematiques:[
 "Le légal et le juste coïncident-ils toujours ? (une loi peut être injuste)",
 "Justice = traiter tout le monde pareil (égalité) ou selon les besoins/mérites (équité) ?",
 "Peut-on se faire justice soi-même ? (la vengeance n'est pas la justice)"
],
auteurs:[
 "<span class='auteur'>Aristote</span> : justice <b>distributive</b> (répartir selon le mérite) vs <b>corrective</b> (réparer les torts).",
 "<span class='auteur'>Pascal</span> : « La justice sans la force est impuissante ; la force sans la justice est tyrannique. »",
 "<span class='auteur'>Rousseau</span> : la loi est juste si elle exprime la <b>volonté générale</b>.",
 "<span class='auteur'>Rawls</span> : justice = équité, pensée sous un « <b>voile d'ignorance</b> » (sans savoir quelle place on aura)."
],
schema:`<span class="t">LÉGAL vs LÉGITIME</span>
              <b>LÉGAL</b> (conforme à la loi)
             /                          \\
     ET LÉGITIME                  MAIS ILLÉGITIME
 punir un meurtrier            lois de l'apartheid
             \\                          /
          <b>ILLÉGAL MAIS LÉGITIME ?</b>
     désobéissance civile (Rosa Parks)

<span class="t">ÉGALITÉ vs ÉQUITÉ</span>
ÉGALITÉ : la même chose pour tous
ÉQUITÉ  : à chacun selon ses besoins (caisse + haute pour le + petit)`,
exemples:[
 "<b>Rosa Parks (1955)</b> : désobéir à une loi injuste → l'illégal peut être juste.",
 "<b>Antigone</b> : elle enterre son frère contre la loi du roi, au nom d'une justice supérieure.",
 "<b>L'impôt progressif</b> : les riches paient plus → équité plutôt qu'égalité stricte."
],
citations:[
 ["Summum jus, summa injuria — le droit poussé à l'extrême devient injustice.","Cicéron"],
 ["Là où il n'y a pas de loi, il n'y a pas de liberté.","Locke"]
],
videos:[
 {chan:"SchoolMouv", titre:"Révisions bac philo : La Justice", dur:"~5 min", url:"https://www.youtube.com/watch?v=7XcBIyaAPQc"},
 {chan:"Cyrus North", titre:"La justice (Rawls…) sur sa chaîne", dur:"5–10 min", url:"https://www.youtube.com/results?search_query=cyrus+north+justice+rawls", search:true},
 {chan:"Le Précepteur", titre:"« La justice » — la notion en profondeur", dur:"extraits dispo", url:"https://www.youtube.com/results?search_query=le+pr%C3%A9cepteur+la+justice", search:true}
]
},
{
id:"liberte", titre:"La liberté", emoji:"🕊️", couleur:"#2F6FED",
oneliner:"Être libre, ce n'est pas faire tout ce qu'on veut : c'est se donner soi-même sa règle (autonomie).",
definition:[
 "<b>Sens courant</b> : faire ce que je veux, sans obstacle.",
 "<b>Sens philosophique</b> : capacité à se déterminer soi-même (<b>autonomie</b>), choisir en connaissance de cause."
],
problematiques:[
 "Sommes-nous libres ou déterminés (éducation, gènes, société, désirs) ?",
 "La liberté est-elle l'absence de lois… ou rendue possible par les lois ?",
 "Faire tout ce qu'on désire, est-ce être libre ? (on peut être esclave de ses désirs)"
],
auteurs:[
 "<span class='auteur'>Descartes</span> : le <b>libre arbitre</b> = pouvoir de dire oui ou non.",
 "<span class='auteur'>Spinoza</span> : le libre arbitre est une <b>illusion</b> — « la pierre qui roule se croirait libre si elle pensait ».",
 "<span class='auteur'>Rousseau</span> : « L'obéissance à la loi qu'on s'est prescrite est liberté. »",
 "<span class='auteur'>Kant</span> : être libre = obéir à la raison morale, pas à ses penchants.",
 "<span class='auteur'>Sartre</span> : « L'homme est <b>condamné à être libre</b> » — pas d'excuse, nous sommes responsables."
],
schema:`<span class="t">PLAN TYPE : « Être libre, est-ce faire ce que l'on veut ? »</span>
I.   <b>THÈSE</b>      liberté = absence de contrainte (sens commun)
        ↓ MAIS
II.  <b>ANTITHÈSE</b>  suivre ses désirs = en être esclave (Spinoza)
        ↓ DONC        + nos "choix" sont déterminés
III. <b>SYNTHÈSE</b>   vraie liberté = AUTONOMIE, se donner
                  sa propre loi (Rousseau, Kant)`,
exemples:[
 "<b>L'addiction au smartphone</b> : je « choisis » de scroller… ou les algorithmes choisissent pour moi ?",
 "<b>Le code de la route</b> : la loi limite ET permet la liberté (rouler en sécurité).",
 "<b>Matrix</b> : la pilule rouge = préférer une liberté lucide à un confort illusoire."
],
citations:[
 ["L'homme est né libre, et partout il est dans les fers.","Rousseau"],
 ["L'homme est condamné à être libre.","Sartre"]
],
videos:[
 {chan:"SchoolMouv", titre:"Révisions bac philo : La Liberté", dur:"~5 min", url:"https://www.youtube.com/watch?v=uCfTe7mOyMs"},
 {chan:"Cyrus North", titre:"Sartre / l'existentialisme (Coup de Phil')", dur:"~8 min", url:"https://www.youtube.com/results?search_query=cyrus+north+sartre+existentialisme", search:true},
 {chan:"Le Précepteur", titre:"Spinoza et le libre arbitre", dur:"extraits dispo", url:"https://www.youtube.com/results?search_query=le+pr%C3%A9cepteur+spinoza+libre+arbitre", search:true}
]
},
{
id:"nature", titre:"La nature", emoji:"🌿", couleur:"#2E8B57",
oneliner:"Trois sens : le monde non transformé par l'homme, l'essence d'une chose, et l'inné (vs l'acquis).",
definition:[
 "<b>Le monde</b> non transformé par l'homme — opposé à la <b>culture</b> et à l'<b>artifice</b>.",
 "<b>L'essence</b> d'une chose (« la nature humaine »).",
 "<b>Le naturel</b> = inné, spontané — opposé à l'acquis."
],
problematiques:[
 "Existe-t-il une « nature humaine » ou sommes-nous façonnés par la culture ?",
 "Faut-il dominer la nature ou la protéger ?",
 "Le naturel est-il forcément bon ? (attention : virus et catastrophes sont naturels…)"
],
auteurs:[
 "<span class='auteur'>Descartes</span> : se rendre « <b>comme maître et possesseur de la nature</b> » par la science.",
 "<span class='auteur'>Rousseau</span> : l'homme est bon à l'état de nature, la société le corrompt.",
 "<span class='auteur'>Lévi-Strauss</span> : la frontière nature/culture passe par la règle (prohibition de l'inceste).",
 "<span class='auteur'>Hans Jonas</span> : « <b>principe responsabilité</b> » — devoir envers la nature et les générations futures."
],
schema:`<span class="t">NATURE ⟷ CULTURE</span>
<b>NATURE</b>                        <b>CULTURE</b>
inné, donné, universel    ⟷   acquis, transformé, variable
l'instinct                ⟷   éducation, règles, langage

→ chez l'HOMME les deux sont inséparables :
  même manger ou marcher sont façonnés par la culture`,
exemples:[
 "<b>Le réchauffement climatique</b> : la maîtrise technique se retourne contre nous → éthique de Jonas. Exemple en or pour STI2D.",
 "<b>Victor de l'Aveyron</b> (enfant sauvage) : sans culture, pas d'humanité « achevée ».",
 "<b>OGM / clonage</b> : jusqu'où artificialiser le vivant ?"
],
citations:[
 ["Comme maître et possesseur de la nature.","Descartes"],
 ["Tout est bien sortant des mains de l'Auteur des choses, tout dégénère entre les mains de l'homme.","Rousseau"]
],
videos:[
 {chan:"SchoolMouv", titre:"Révisions bac philo : La Nature", dur:"~5 min", url:"https://www.youtube.com/watch?v=fpUKEq17CtU"},
 {chan:"Les Bons Profs", titre:"La nature — fiche de révision", dur:"~5 min", url:"https://www.youtube.com/results?search_query=les+bons+profs+philosophie+la+nature", search:true},
 {chan:"Cyrus North", titre:"Rousseau / nature et culture", dur:"5–10 min", url:"https://www.youtube.com/results?search_query=cyrus+north+rousseau", search:true}
]
},
{
id:"religion", titre:"La religion", emoji:"🕯️", couleur:"#B8860B",
oneliner:"Croyances + rites reliant une communauté à du sacré. Le réflexe : distinguer CROIRE et SAVOIR.",
definition:[
 "<b>Étymologie</b> : <i>religare</i> = relier (les hommes entre eux et à Dieu) ; <i>relegere</i> = relire avec scrupule.",
 "Ensemble de <b>croyances</b> et de <b>rites</b> reliant une communauté à du <b>sacré</b>."
],
problematiques:[
 "La religion est-elle compatible avec la raison ? Croire, est-ce renoncer à penser ?",
 "Pourquoi croit-on ? (sens, peur de la mort, lien social…)",
 "Peut-on prouver l'existence de Dieu ? (croire ≠ savoir)"
],
auteurs:[
 "<span class='auteur'>Pascal</span> : « Le cœur a ses raisons que la raison ne connaît point » + le <b>pari</b>.",
 "<span class='auteur'>Kant</span> : on ne peut ni prouver ni réfuter Dieu → « limiter le savoir pour laisser place à la croyance ».",
 "<span class='auteur'>Marx</span> : la religion = « <b>l'opium du peuple</b> », consolation qui détourne des injustices.",
 "<span class='auteur'>Freud</span> : illusion née du désir infantile de protection.",
 "<span class='auteur'>Durkheim</span> : fonction <b>sociale</b> — la religion soude la communauté."
],
schema:`<span class="t">CROIRE vs SAVOIR</span>
<b>SAVOIR</b>                       <b>CROIRE (foi)</b>
preuves, démonstration   ⟷   confiance, adhésion sans preuve
universel, vérifiable    ⟷   personnel, engagement

→ la foi n'est pas un savoir raté :
  c'est un AUTRE rapport au monde (sens, espérance)`,
exemples:[
 "<b>La laïcité (loi 1905)</b> : séparer religion et État pour garantir la liberté de croire ET de ne pas croire.",
 "<b>Galilée (1633)</b> : conflit science/religion quand la religion prétend dire le vrai sur la nature.",
 "<b>Les rites laïcs</b> (minutes de silence) : le besoin de sacré survit-il à la religion ?"
],
citations:[
 ["Le cœur a ses raisons que la raison ne connaît point.","Pascal"],
 ["La religion est l'opium du peuple.","Marx"]
],
videos:[
 {chan:"SchoolMouv", titre:"Révisions bac philo : La religion", dur:"~5 min", url:"https://www.youtube.com/watch?v=ppx4E0JgVYc"},
 {chan:"Les Bons Profs", titre:"La religion (fiche de révisions)", dur:"~6 min", url:"https://www.youtube.com/watch?v=MMf4JKv9Pwg"},
 {chan:"Cyrus North", titre:"Le pari de Pascal", dur:"~8 min", url:"https://www.youtube.com/results?search_query=cyrus+north+pari+de+pascal", search:true}
]
},
{
id:"technique", titre:"La technique", emoji:"🔧", couleur:"#D2691E",
oneliner:"LA notion STI2D par excellence : la technique nous libère-t-elle ou nous asservit-elle ?",
definition:[
 "<b>Étymologie</b> : grec <i>technè</i> = savoir-faire, art de produire.",
 "Ensemble des procédés et outils par lesquels l'homme <b>transforme la nature</b> pour satisfaire ses besoins."
],
problematiques:[
 "La technique libère-t-elle l'homme ou l'asservit-elle ?",
 "Est-elle neutre (tout dépend de l'usage) ou porte-t-elle ses propres dangers ?",
 "Progrès technique = progrès humain ?"
],
auteurs:[
 "<span class='auteur'>Mythe de Prométhée</span> (Platon) : l'homme naît « nu » → la technique (le feu) compense ce manque. Elle est constitutive de l'humanité.",
 "<span class='auteur'>Aristote</span> : « La main est l'outil des outils. »",
 "<span class='auteur'>Bergson</span> : l'homme = « <b>Homo faber</b> » avant Homo sapiens.",
 "<span class='auteur'>Heidegger</span> : la technique moderne transforme tout (nature, homme) en <b>stock de ressources</b> ; elle devient une manière de penser.",
 "<span class='auteur'>Hans Jonas</span> : la puissance technique exige une éthique de la <b>responsabilité</b>."
],
schema:`<span class="t">LE DOUBLE VISAGE DE LA TECHNIQUE</span>
                 <b>LA TECHNIQUE</b>
               /              \\
     <b>LIBÉRATION</b>               <b>ALIÉNATION / DANGER</b>
  guérit (médecine)          bombe atomique, surveillance
  libère du travail pénible  dépendance, chômage techno
  prolonge la vie            épuise la planète
               \\              /
  → pas neutre : elle transforme nos besoins,
    nos relations, notre pensée
  → « ce qu'on PEUT faire, DOIT-on le faire ? »`,
exemples:[
 "<b>L'IA</b> (ChatGPT, voiture autonome) : outil ou remplacement de l'homme ? Qui est responsable en cas d'accident ?",
 "<b>Le nucléaire</b> : même science → énergie civile ou Hiroshima. Question de l'usage et de la responsabilité.",
 "<b>Le smartphone</b> : il nous « augmente » mais capte notre attention et crée la dépendance."
],
citations:[
 ["La main est l'outil des outils.","Aristote"],
 ["Science sans conscience n'est que ruine de l'âme.","Rabelais"]
],
videos:[
 {chan:"SchoolMouv", titre:"Révisions bac philo : La technique", dur:"~5 min", url:"https://www.youtube.com/watch?v=A7ueRNQSjrY"},
 {chan:"Cyrus North", titre:"Le mythe de Prométhée", dur:"~8 min", url:"https://www.youtube.com/results?search_query=cyrus+north+prom%C3%A9th%C3%A9e", search:true},
 {chan:"Monsieur Phi", titre:"IA & philo (pour briller en exemple)", dur:"10–20 min", url:"https://www.youtube.com/results?search_query=monsieur+phi+intelligence+artificielle", search:true}
]
},
{
id:"verite", titre:"La vérité", emoji:"🔍", couleur:"#0E7C7B",
oneliner:"La vérité = accord entre ce que je dis et la réalité. Le réflexe : opposer OPINION et CONNAISSANCE.",
definition:[
 "Accord entre ce que je pense/dis et <b>la réalité</b> (adéquation).",
 "À distinguer de : la <b>réalité</b> (ce qui existe), l'<b>opinion</b> (croyance non fondée), la <b>sincérité</b> (dire ce qu'on croit vrai, même si c'est faux)."
],
problematiques:[
 "Peut-on atteindre une vérité certaine, ou « à chacun sa vérité » ? (phrase qui se contredit elle-même !)",
 "La vérité scientifique est-elle définitive ? (non : révisable)",
 "Faut-il toujours dire la vérité ? (conflit avec la morale)"
],
auteurs:[
 "<span class='auteur'>Platon</span> : <b>allégorie de la caverne</b> — nous prenons les ombres (opinions) pour la réalité ; philosopher = se libérer. Doxa ≠ epistémè.",
 "<span class='auteur'>Descartes</span> : le <b>doute méthodique</b> → « Je pense, donc je suis » (cogito), première certitude.",
 "<span class='auteur'>Nietzsche</span> : « il n'y a que des interprétations » ; la « vérité » sert souvent des intérêts.",
 "<span class='auteur'>Popper</span> : une théorie est scientifique si elle est <b>falsifiable</b> (réfutable). La science progresse par essais/erreurs."
],
schema:`<span class="t">LA CAVERNE DE PLATON</span>
[Prisonniers enchaînés] → OMBRES sur le mur = opinions, illusions
        ↓ libération (douloureuse !)
[Sortie de la caverne]  → le SOLEIL = la vérité, les Idées
        ↓ retour
[Le philosophe redescend] → on refuse de le croire
                            (Socrate condamné)

<span class="t">OPINION → CONNAISSANCE</span>
"je crois que…"  →  "je peux DÉMONTRER que…"
   passage = démonstration, expérience, doute`,
exemples:[
 "<b>Fake news / complotisme</b> : pourquoi préférer une croyance confortable à une vérité dérangeante ? (la caverne 2.0 : bulles de filtres)",
 "<b>Galilée</b> : la vérité scientifique contre l'opinion établie.",
 "<b>Newton → Einstein</b> : « vrai » pendant 200 ans puis dépassé → la vérité scientifique est révisable (Popper)."
],
citations:[
 ["Je pense, donc je suis.","Descartes"],
 ["Il n'y a pas de faits, il n'y a que des interprétations.","Nietzsche"]
],
videos:[
 {chan:"SchoolMouv", titre:"Révisions bac philo : La Vérité", dur:"~5 min", url:"https://www.youtube.com/watch?v=62UQ2aR53X4"},
 {chan:"Cyrus North", titre:"L'Allégorie de la Caverne (Coup de Phil' #1)", dur:"~7 min", url:"https://www.youtube.com/watch?v=r4cjmgElt9Y"},
 {chan:"Monsieur Phi", titre:"Vérité, doute, définitions", dur:"10–20 min", url:"https://www.youtube.com/results?search_query=monsieur+phi+v%C3%A9rit%C3%A9", search:true}
]
}
];

/* ---------- Rendu ---------- */
const tabs = document.getElementById('tabs');
const main = document.getElementById('main');

DATA.forEach((n,i)=>{
  const b = document.createElement('button');
  b.className='tab'; b.role='tab'; b.textContent=n.emoji+' '+n.titre;
  b.style.setProperty('--tc', n.couleur);
  b.onclick=()=>show(i);
  tabs.appendChild(b);

  const sec = document.createElement('section');
  sec.className='fiche'; sec.style.setProperty('--c', n.couleur);
  sec.innerHTML = `
    <div class="fiche-head">
      <div>
        <div class="ref">FICHE ${String(i+1).padStart(2,'0')} / 07</div>
        <h2>${n.emoji} ${n.titre}</h2>
      </div>
      <button class="timer" data-i="${i}">⏱ Lancer 5:00</button>
    </div>
    <p class="one-liner">${n.oneliner}</p>
    <div class="grid2">
      <div class="bloc"><h3>Définition</h3><ul>${n.definition.map(d=>`<li>${d}</li>`).join('')}</ul></div>
      <div class="bloc"><h3>Problématiques clés</h3><ul>${n.problematiques.map(p=>`<li>${p}</li>`).join('')}</ul></div>
    </div>
    <div class="bloc"><h3>Auteurs & points clés</h3><ul>${n.auteurs.map(a=>`<li>${a}</li>`).join('')}</ul></div>
    <div class="schema">${n.schema}</div>
    <div class="grid2">
      <div class="bloc"><h3>Exemples concrets</h3><ul>${n.exemples.map(e=>`<li>${e}</li>`).join('')}</ul></div>
      <div class="bloc"><h3>Citations à replacer</h3>${n.citations.map(c=>`<div class="cite">« ${c[0]} »<span>— ${c[1]}</span></div>`).join('')}</div>
    </div>
    <div class="bloc"><h3>🎬 Vidéos pour réviser</h3>
      <div class="videos">${n.videos.map(v=>`
        <a class="vid ${v.search?'search':''}" href="${v.url}" target="_blank" rel="noopener">
          <div class="chan">${v.chan}</div>
          <div class="vtitle">${v.titre}</div>
          <div class="dur">${v.dur}${v.search?' · recherche YouTube':''}</div>
        </a>`).join('')}
      </div>
    </div>`;
  main.appendChild(sec);
});

/* Bloc bonus méthode (toujours visible en dernier onglet) */
const bonus = document.createElement('section');
bonus.className='fiche'; bonus.style.setProperty('--c','#1B2A4A');
bonus.innerHTML = `
  <div class="fiche-head"><div>
    <div class="ref">BONUS</div><h2>🎯 Méthode & réflexes</h2>
  </div></div>
  <div class="schema"><span class="t">STRUCTURE DE DISSERTATION (à mémoriser)</span>
<b>INTRO</b> : accroche → définir les termes → problème → annoncer le plan
<b>I.</b>   THÈSE      (réponse évidente, sens commun)
<b>II.</b>  ANTITHÈSE  ("mais on peut objecter que…")
<b>III.</b> SYNTHÈSE   (dépassement : redéfinir le terme clé)
<b>CONCLUSION</b> : répondre clairement à la question posée</div>
  <div class="bloc"><h3>Le réflexe en or : la distinction de chaque notion</h3>
  <table class="method">
    <tr><th>Notion</th><th>Distinction clé</th></tr>
    <tr><td>🎨 L'art</td><td>beau / utile</td></tr>
    <tr><td>⚖️ La justice</td><td>légal / légitime</td></tr>
    <tr><td>🕊️ La liberté</td><td>faire ce qu'on veut / autonomie</td></tr>
    <tr><td>🌿 La nature</td><td>nature / culture</td></tr>
    <tr><td>🕯️ La religion</td><td>croire / savoir</td></tr>
    <tr><td>🔧 La technique</td><td>moyen neutre / puissance dangereuse</td></tr>
    <tr><td>🔍 La vérité</td><td>opinion / connaissance</td></tr>
  </table></div>
  <div class="bloc"><h3>Chaînes YouTube fiables</h3>
  <table class="method">
    <tr><th>Chaîne</th><th>Style</th><th>Durée</th></tr>
    <tr><td><a href="https://www.youtube.com/@CyrusNorth" target="_blank" rel="noopener">Cyrus North (Le Coup de Phil')</a></td><td>drôle, auteurs & concepts</td><td>5–10 min</td></tr>
    <tr><td><a href="https://www.youtube.com/@LePrecepteurPodcast" target="_blank" rel="noopener">Le Précepteur</a></td><td>calme, très clair, profond</td><td>extraits/shorts</td></tr>
    <tr><td><a href="https://www.youtube.com/@MonsieurPhi" target="_blank" rel="noopener">Monsieur Phi</a></td><td>philo + science + pop culture</td><td>10–20 min</td></tr>
    <tr><td><a href="https://www.youtube.com/@lesbonsprofs" target="_blank" rel="noopener">Les Bons Profs</a></td><td>format scolaire, l'essentiel</td><td>~5 min</td></tr>
    <tr><td><a href="https://www.youtube.com/@annabac" target="_blank" rel="noopener">Annabac</a></td><td>13 vidéos couvrant le programme</td><td>~6 min</td></tr>
    <tr><td><a href="https://www.youtube.com/@SchoolMouv" target="_blank" rel="noopener">SchoolMouv</a></td><td>révisions bac par notion</td><td>~5 min</td></tr>
  </table></div>`;
main.appendChild(bonus);

const bTab = document.createElement('button');
bTab.className='tab'; bTab.textContent='🎯 Méthode';
bTab.style.setProperty('--tc','#1B2A4A');
bTab.onclick=()=>show(DATA.length);
tabs.appendChild(bTab);

/* ---------- Chrono 5 min (déclaré AVANT show(0) pour éviter la TDZ) ---------- */
let tInt=null, tBtn=null;

function stopTimer(){
  if(tInt){ clearInterval(tInt); tInt=null; }
  if(tBtn){ tBtn.textContent='⏱ Lancer 5:00'; tBtn.classList.remove('on'); tBtn=null; }
}

document.addEventListener('click', e=>{
  const btn = e.target.closest('.timer'); if(!btn) return;
  if(tBtn===btn){ stopTimer(); return; }
  stopTimer();
  tBtn = btn;
  btn.classList.add('on');
  let s = 300;
  const tick = ()=>{
    const m = Math.floor(s/60), sec = String(s%60).padStart(2,'0');
    btn.textContent = s>0 ? `⏱ ${m}:${sec}` : '✅ Fiche relue !';
    if(s<=0){ clearInterval(tInt); tInt=null; }
    s--;
  };
  tick();
  tInt = setInterval(tick, 1000);
});

/* ---------- Affichage initial ---------- */
function show(i){
  document.querySelectorAll('.fiche').forEach((s,k)=>s.classList.toggle('show',k===i));
  document.querySelectorAll('.tab').forEach((t,k)=>t.classList.toggle('active',k===i));
  window.scrollTo({top:0,behavior:'smooth'});
  stopTimer();
}
show(0);
</script>
</body>
</html>
