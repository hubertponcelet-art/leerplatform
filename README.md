[index.html](https://github.com/user-attachments/files/27359530/index.html)
<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Het Oude Rome — Leerplatform 2e jaar</title>
<style>
:root {
  --c1: #1a3a5c;
  --c2: #b8860b;
  --c3: #f5f0e8;
  --bg: #fefcf7;
  --txt: #1e1e1e;
  --ok: #2e7d32;
  --err: #c62828;
  --border: #d0c8b8;
  --highlight: #fff3cd;
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
  font-size: 17px;
  line-height: 1.65;
  color: var(--txt);
  background: var(--bg);
  max-width: 900px;
  margin: 0 auto;
  padding: 12px 16px 60px;
}
h1 { font-size: 1.6em; color: var(--c1); margin-bottom: 8px; }
h2 { font-size: 1.3em; color: var(--c1); margin: 20px 0 8px; border-bottom: 2px solid var(--c2); padding-bottom: 4px; }
h3 { font-size: 1.1em; color: var(--c2); margin: 14px 0 6px; }

/* NAV */
.topbar { background: var(--c1); color: #fff; padding: 14px 18px; border-radius: 8px; margin-bottom: 16px; }
.topbar h1 { color: #fff; font-size: 1.4em; margin: 0; }
.progress-bar { margin-top: 8px; font-size: 0.85em; color: var(--c3); }

.nav-row { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 12px; }
.nav-btn {
  padding: 10px 18px;
  border: 2px solid var(--c1);
  background: #fff;
  color: var(--c1);
  font-size: 16px;
  font-weight: 600;
  border-radius: 6px;
  cursor: pointer;
  min-width: 120px;
  text-align: center;
}
.nav-btn:hover, .nav-btn:focus { background: var(--c3); }
.nav-btn.active { background: var(--c1); color: #fff; }

.topic-btn {
  padding: 8px 14px;
  border: 2px solid var(--c2);
  background: #fff;
  color: var(--c2);
  font-size: 15px;
  font-weight: 600;
  border-radius: 6px;
  cursor: pointer;
}
.topic-btn:hover, .topic-btn:focus { background: var(--highlight); }
.topic-btn.active { background: var(--c2); color: #fff; }

/* CONTENT */
.section { display: none; }
.section.visible { display: block; }
.card {
  background: #fff;
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 16px 18px;
  margin-bottom: 14px;
}
.key { background: var(--highlight); padding: 2px 6px; border-radius: 3px; font-weight: 600; }
.datum { color: var(--c2); font-weight: 700; }

/* EXERCISES */
.q-block {
  background: #fff;
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 16px;
  margin-bottom: 14px;
}
.q-block p { margin-bottom: 8px; font-weight: 600; }
.q-block label { display: block; padding: 6px 10px; margin: 4px 0; border-radius: 4px; cursor: pointer; }
.q-block label:hover { background: var(--c3); }
.q-block input[type="radio"], .q-block input[type="checkbox"] { margin-right: 8px; }
.q-block input[type="text"] {
  padding: 8px 12px;
  border: 2px solid var(--border);
  border-radius: 4px;
  font-size: 16px;
  width: 100%;
  max-width: 400px;
}
.feedback { padding: 8px 12px; border-radius: 4px; margin-top: 8px; font-size: 0.95em; display: none; }
.feedback.correct { display: block; background: #e8f5e9; color: var(--ok); border: 1px solid var(--ok); }
.feedback.wrong { display: block; background: #ffebee; color: var(--err); border: 1px solid var(--err); }

.check-btn {
  padding: 8px 20px;
  background: var(--c1);
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  cursor: pointer;
  margin-top: 6px;
}
.check-btn:hover { opacity: 0.9; }

.score-bar {
  background: var(--c1);
  color: #fff;
  padding: 10px 16px;
  border-radius: 6px;
  margin-bottom: 14px;
  font-weight: 600;
  font-size: 1em;
  position: sticky;
  top: 0;
  z-index: 10;
}

/* PDF BUTTONS */
.dl-btn {
  display: inline-block;
  padding: 12px 24px;
  background: var(--c2);
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  margin: 6px 8px 6px 0;
  text-decoration: none;
}
.dl-btn:hover { opacity: 0.9; }

/* TIMER */
.timer-box {
  background: var(--c3);
  padding: 10px 16px;
  border-radius: 6px;
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}
.timer-box button { padding: 6px 14px; font-size: 15px; border-radius: 4px; border: 1px solid var(--c1); background: #fff; cursor: pointer; }
.timer-display { font-size: 1.3em; font-weight: 700; color: var(--c1); font-variant-numeric: tabular-nums; }

/* DRAG */
.drag-zone { min-height: 44px; border: 2px dashed var(--border); border-radius: 6px; padding: 8px; margin: 4px 0; display: flex; flex-wrap: wrap; gap: 6px; }
.drag-item {
  padding: 6px 14px;
  background: var(--c1);
  color: #fff;
  border-radius: 4px;
  cursor: grab;
  font-size: 15px;
  user-select: none;
}
.drag-item:active { cursor: grabbing; }
.drop-slot { min-width: 80px; min-height: 36px; border: 2px solid var(--c2); border-radius: 4px; padding: 4px 8px; display: inline-flex; align-items: center; }

@media (max-width: 600px) {
  body { font-size: 16px; padding: 8px 10px 50px; }
  .nav-btn, .topic-btn { min-width: auto; padding: 8px 12px; font-size: 14px; }
  .nav-row { gap: 6px; }
}
@media print { .topbar, .nav-row, .check-btn, .dl-btn, .timer-box, .score-bar { display: none; } }
</style>
</head>
<body>

<div class="topbar">
  <h1>Het Oude Rome</h1>
  <div class="progress-bar" id="progressBar">Kies een module en topic om te starten</div>
</div>

<!-- MODULE NAV -->
<div class="nav-row" id="moduleNav">
  <button class="nav-btn" onclick="showModule('cours')">1. Cursus</button>
  <button class="nav-btn" onclick="showModule('exercices')">2. Oefeningen</button>
  <button class="nav-btn" onclick="showModule('examen')">3. Examen (PDF)</button>
  <button class="nav-btn" onclick="showModule('correctif')">4. Correctiesleutel</button>
</div>

<!-- TOPIC NAV -->
<div class="nav-row" id="topicNav" style="display:none;">
  <button class="topic-btn" onclick="showTopic(0)">Les 17</button>
  <button class="topic-btn" onclick="showTopic(1)">Les 18</button>
  <button class="topic-btn" onclick="showTopic(2)">Les 19</button>
  <button class="topic-btn" onclick="showTopic(3)">Les 20</button>
  <button class="topic-btn" onclick="showTopic(4)">Les 21</button>
  <button class="topic-btn" onclick="showTopic(5)">Les 22</button>
  <button class="topic-btn" onclick="showTopic(6)">Les 23+25</button>
</div>

<!-- ==================== MODULE 1: COURS ==================== -->
<div id="mod-cours" class="section">

<!-- TOPIC 0: Les 17 -->
<div class="topic-content" data-topic="0">
<h2>Les 17: Rome begint als een bescheiden koninkrijk</h2>

<div class="card">
<h3>1. Het ontstaan van Rome: de mythe</h3>
<p>Volgens de mythe stammen de Romeinen af van de <span class="key">Trojaan Aeneas</span>. Na de val van Troje vluchtte hij naar Italië.</p>
<p>Zijn nakomelingen <span class="key">Romulus en Remus</span> zouden Rome hebben gesticht. Romulus doodde Remus en werd de eerste koning.</p>
<p>De stad Rome werd volgens de mythe gesticht in <span class="datum">753 v.C.</span> Deze mythe dateert pas uit de <span class="datum">3e eeuw v.C.</span> — dat is eeuwen later, dus de betrouwbaarheid is beperkt.</p>
</div>

<div class="card">
<h3>2. Het ontstaan van Rome: de feiten</h3>
<p>De Romeinen zijn <span class="key">Indo-Europeanen</span> die zich omstreeks <span class="datum">1000 v.C.</span> op het <span class="key">Italische schiereiland</span> hebben gevestigd.</p>
<p>In de <span class="datum">10e eeuw v.C.</span> ontstaan de eerste <span class="key">nederzettingen</span> in <span class="key">Latium</span>.</p>
<p>Kenmerken van Latium: vruchtbare grond, centraal gelegen, nabij de Tiber. De eerste bewoners waren eenvoudige <span class="key">boeren</span> en <span class="key">herders</span>.</p>
</div>

<div class="card">
<h3>3. De gunstige ligging van Rome</h3>
<p>Rome is gelegen aan de <span class="key">Tiber</span> (rivier). Dit gaf Rome een goede positie.</p>
<p>Rome ligt midden op de verbindingsweg tussen het <span class="key">noorden</span> en het <span class="key">zuiden</span> van Italië. De heuvels en moerassen vormen een natuurlijke <span class="key">verdediging</span> tegen vijanden.</p>
<p>De afstand tussen Rome en de zee is groot genoeg om <span class="key">veilig</span> te zijn voor zeerovers. De Tiber is ideaal voor het transport van <span class="key">handelswaren</span> en het bereiken van de zee.</p>
</div>

<div class="card">
<h3>4. Volkeren op het Italische schiereiland</h3>
<p><span class="key">Noordwest-Italië</span> (tussen Tiber en Arno): de <span class="key">Etrusken</span>.</p>
<p><span class="key">Midden-Italië</span>: Italische volksstammen, waaronder de <span class="key">Latijnen</span> en de <span class="key">Samnieten</span>.</p>
<p><span class="key">Zuid-Italië</span>: de <span class="key">Grieken</span>, die hier kolonies stichtten tussen de <span class="datum">8e en 5e eeuw v.C.</span></p>
</div>

<div class="card">
<h3>5. De Romeinse familia</h3>
<p>De <span class="key">familia</span> = het hele huishouden. Dit omvat de vader, moeder, kinderen, slaven en bezittingen.</p>
<p>Aan het hoofd stond de <span class="key">pater familias</span> (de vader). Hij had absolute macht over zijn familie. De vrouw had weinig rechten en stond onder gezag van haar man.</p>
<p>Een <span class="key">gens</span> = een groep families die beweerden van dezelfde voorvader af te stammen.</p>
</div>

<div class="card">
<h3>6. Bevolkingsgroepen</h3>
<p><span class="key">Patriciërs</span> (adel): geloven dat ze afstammelingen zijn van de stichters van Rome. Bezitten alle grond = grootgrondbezitters. Ze kiezen en adviseren de koning.</p>
<p><span class="key">Plebejers</span> (gewone burgers): ambachtslui, kleine boeren en handelaars. Zijn vrij, maar hebben geen politieke macht. Werken op de gronden van de patriciërs — dit schept afhankelijkheid, maar ook bescherming.</p>
<p><span class="key">Slaven</span>: krijgsgevangenen of schuldenaren. Zwaar onderdrukt. Weinig tot geen rechten. Worden gezien als een bezit.</p>
</div>

<div class="card">
<h3>7. Het koningschap</h3>
<p>De eerste bestuursvorm van de Romeinen was een <span class="key">koninkrijk</span>, met aan het hoofd een <span class="key">koning</span>.</p>
<p>De koning werd gekozen voor het <span class="key">leven</span>. Hij leidde het leger, sprak recht en leidde religieuze ceremonies. Hij bezat zo goed als alle macht.</p>
<p>De koning vroeg advies aan de <span class="key">senaat</span> = raad van oudsten (pater familias van de belangrijkste gentes). Hij kon ook de <span class="key">volksvergadering</span> samenroepen, waarin alle mannelijke burgers zaten. Zij bevestigden de koning.</p>
</div>

<div class="card">
<h3>8. Etruskische invloed</h3>
<p><span class="key">Politiek</span>: een koninkrijk als bestuursvorm.</p>
<p><span class="key">Religie</span>: augures (voorspellers) die de toekomst probeerden te voorspellen aan de hand van tekens in de natuur.</p>
<p><span class="key">Cultuur</span>: alfabet, bouwkunst (rondbogen, bakstenen), bouwen van tempels en riolen. Via de Etrusken kwamen de Romeinen in contact met de <span class="key">Grieken</span>, die een grote culturele invloed hadden = kunst, wetenschap.</p>
</div>
</div>

<!-- TOPIC 1: Les 18 -->
<div class="topic-content" data-topic="1">
<h2>Les 18: De Romeinse republiek</h2>

<div class="card">
<h3>1. Van koninkrijk naar republiek</h3>
<p>De eerste bestuursvorm was een <span class="key">koninkrijk</span> (<span class="datum">753 v.C. – 509 v.C.</span>). Het probleem: koningen kregen na verloop van tijd te veel macht.</p>
<p>Ze hielden geen rekening meer met de <span class="key">senaat</span> en de <span class="key">volksvergadering</span>.</p>
<p>De laatste koning, <span class="key">Tarquinius Superbus</span>, werd verjaagd in <span class="datum">509 v.C.</span> Het bestuur ondergaat zware hervormingen = de <span class="key">republiek</span> is geboren.</p>
</div>

<div class="card">
<h3>2. De instellingen van de republiek</h3>
<p><span class="key">Twee consuls</span>: regeerperiode van 1 jaar. Gekozen door de volksvergadering. Ze leiden het leger en het dagelijks bestuur.</p>
<p><span class="key">De senaat</span>: regeerperiode voor het leven. Kiest de twee consuls. Beslist over oorlog en vrede. Dient wetten in.</p>
<p><span class="key">Volksvergadering</span>: alle mannelijke burgers. Keurt wetten goed of af. Gekozen door de patriciërs (in het begin).</p>
</div>

<div class="card">
<h3>3. Beperkingen op de macht</h3>
<p>De twee consuls <span class="key">controleren</span> elkaar. Elk heeft een <span class="key">vetorecht</span> = het recht om andermans beslissingen tegen te houden.</p>
<p>Als de twee consuls niet overeenkomen, mag de senaat een <span class="key">dictator</span> aanstellen. Deze krijgt <span class="key">6 maanden</span> de tijd om de crisis op te lossen.</p>
<p>Elk besluit van de volksvergadering moet <span class="key">goedgekeurd</span> worden door de senaat voordat het geldig is.</p>
</div>

<div class="card">
<h3>4. De gelijkheidsstrijd van de plebejers</h3>
<p><span class="datum">500 v.C.</span>: Rome start met de <span class="key">verovering</span> van het Italische schiereiland. Hiervoor zijn extra soldaten en geld nodig — de plebejers worden opgeroepen als soldaten en moeten extra belastingen betalen.</p>
<p>In ruil beloven de patriciërs het <span class="key">volwaardige burgerschap</span> en deelname aan de volksvergadering. Maar de plebejers zijn weg van huis: geen oogst, geen stemrecht in de praktijk.</p>
<p>Ze eisen meer politieke rechten. De patriciërs luisteren niet. De plebejers weigeren te vechten = begin van de <span class="key">gelijkheidsstrijd</span> (<span class="datum">498 v.C.</span>).</p>
</div>

<div class="card">
<h3>5. Verloop van de gelijkheidsstrijd (498 – 287 v.C.)</h3>
<p>Stap 1: Nieuwe functie — de <span class="key">volkstribuun</span>. Hij verdedigt de belangen van de plebejers in de volksvergadering. Hij kan beslissingen van andere instellingen tegenhouden (vetorecht).</p>
<p>Stap 2: De <span class="key">wetten</span> die geldig zijn voor heel het Romeinse volk worden vastgelegd (schriftelijk).</p>
<p>Stap 3 (<span class="datum">367 v.C.</span>): Eén van de twee consuls mag een plebejer zijn. Stap 4 (<span class="datum">287 v.C.</span>): Plebejers en patriciërs worden <span class="key">juridisch gelijkgesteld</span> = <span class="key">Lex Hortensia</span>.</p>
</div>

<div class="card">
<h3>6. Nieuwe ongelijkheden</h3>
<p>Ondanks de Lex Hortensia blijven er problemen. Om consul te worden, moest je veel politieke ervaring hebben, je werd niet betaald, en je had veel geld nodig voor campagnes.</p>
<p>Gevolg: enkel <span class="key">rijke plebejers</span> haalden hoge functies. Ze vergaten al snel de wensen van het gewone volk.</p>
<p>Zo ontstaan twee nieuwe groepen: de <span class="key">nobilis</span> (rijke elite) en de <span class="key">proletariërs</span> (bezitlozen).</p>
</div>
</div>

<!-- TOPIC 2: Les 19 -->
<div class="topic-content" data-topic="2">
<h2>Les 19: Rome wordt machtig</h2>

<div class="card">
<h3>1. Rome wordt leider van de Latijnse bond</h3>
<p>Na de invoering van de republiek wordt Rome <span class="key">leider van de Latijnse bond</span>. Rome is de grootste stad van <span class="key">Latium</span> (= het gebied waarin Rome gelegen is).</p>
<p>Rondom Rome woonden ook andere volkeren: de Sabini, Equi, Volsci, Hernici en Aurunces. Rome moest deze volkeren eerst overwinnen om te kunnen uitbreiden.</p>
</div>

<div class="card">
<h3>2. De Galliërs bezetten Rome (390 v.C.)</h3>
<p><span class="datum">390 v.C.</span>: de <span class="key">Galliërs</span> (Kelten) veroveren Rome voor korte tijd. Hun leider was <span class="key">Brennus</span>.</p>
<p>De Romeinen waren zo verrast dat ze hun wapens lieten vallen en wegvluchtten. De Galliërs wandelden vol ongeloof de onverdedigde stadspoort door. Na <span class="key">7 maanden</span> vonden de Kelten de stad maar niks en eisten ze <span class="key">losgeld</span>. Tevreden met hun zakken vol geld vertrokken ze weer.</p>
</div>

<div class="card">
<h3>3. Rome verovert heel Italië</h3>
<p>Na het vertrek van de Kelten veroveren de Romeinen de meeste <span class="key">Latijnse steden</span>. De meeste steden krijgen het Romeinse <span class="key">burgerrecht</span>, met evenveel rechten en plichten als de oorspronkelijke Romeinen.</p>
<p>Ook de <span class="key">Etrusken</span> (volk tussen Tiber en Arno) worden veroverd. Tenslotte verovert Rome de <span class="key">Griekse kolonies</span> in het zuiden van Italië.</p>
<p><span class="datum">270 v.C.</span>: Rome regeert nu over heel Italië, ten zuiden van de <span class="key">Po</span> (rivier in Noord-Italië).</p>
</div>

<div class="card">
<h3>4. De stad Carthago</h3>
<p><span class="datum">814 v.C.</span>: Carthago werd gesticht door de <span class="key">Feniciërs</span>. Het lag op de noordkust van <span class="key">Afrika</span> (huidige Tunesië).</p>
<p>Carthago was een machtige <span class="key">handelsstad</span>. Ze bezaten op dat moment de <span class="key">grootste haven</span> in het Middellandse Zeegebied: een handelshaven (500m x 200m) en een marinehaven (300m diameter).</p>
</div>

<div class="card">
<h3>5. De Punische oorlogen — overzicht</h3>
<p>Dit zijn de oorlogen tussen <span class="key">Rome</span> en <span class="key">Carthago</span>. Ze vinden plaats tussen <span class="datum">264 v.C.</span> en <span class="datum">146 v.C.</span> In totaal zijn er <span class="key">drie</span> Punische oorlogen.</p>
<p>De Romeinen noemden de Carthagers <span class="key">"Poeni"</span> omdat ze de 'P' van Phoeniciërs niet correct konden uitspreken.</p>
</div>

<div class="card">
<h3>6. De eerste Punische oorlog (264 – 241 v.C.)</h3>
<p>Reden: beide partijen willen de <span class="key">controle</span> over het eiland <span class="key">Sicilië</span>. Hier is een grote <span class="key">graanvoorraad</span> (vruchtbaar gebied).</p>
<p><span class="key">Rome wint</span> en verwerft zo haar eerste gebieden buiten Italië. Belangrijk gevolg: Carthago verliest haar <span class="key">oorlogsvloot</span>.</p>
</div>

<div class="card">
<h3>7. De tweede Punische oorlog (218 – 201 v.C.)</h3>
<p>Omdat Carthago na de 1e Punische oorlog haar vloot verloor, beslist generaal <span class="key">Hannibal Barkas</span> om via het noorden aan te vallen. Hij trekt met een groot leger en <span class="key">42 olifanten</span> door de <span class="key">Alpen</span> naar Italië.</p>
<p><span class="key">Hannibal Barkas</span> (247–183 v.C.): zijn voornaam betekent "genade van Ba'al" (god), zijn achternaam "bliksem". Hij groeide op in de legerkampen van zijn vader. Hij was een geniale tacticus.</p>
<p>Bij de <span class="key">Slag bij Cannae</span> (216 v.C.) bezorgde Hannibal het Romeinse leger de bloedigste nederlaag ooit: <span class="key">60.000 tot 80.000 doden</span> in 8 uur tijd. Zijn tactiek wordt vandaag nog onderwezen in militaire academies.</p>
</div>

<div class="card">
<h3>8. Hoe Rome toch de 2e oorlog won</h3>
<p>Ondanks Hannibals overwinningen bleef de meerderheid van de bondgenoten in Midden-Italië (<span class="key">Latijnse bond</span>) trouw aan Rome.</p>
<p>De Romein <span class="key">Scipio Africanus</span> lokte Hannibal uit Italië door naar <span class="key">Zama</span> (Noord-Afrika) te trekken. Daar versloeg hij Hannibal in <span class="datum">202 v.C.</span> — de olifanten werden met vuur verslagen.</p>
<p>Na de oorlog vluchtte Hannibal naar Syrië. Toen de Romeinen dat ontdekten, pleegde hij zelfmoord met gif.</p>
</div>

<div class="card">
<h3>9. De derde Punische oorlog (149 – 146 v.C.)</h3>
<p>Na de 2e oorlog groeide de Carthaagse <span class="key">economie</span> weer. De Carthaagse landbouw beconcurreerde de Romeinse. Senator <span class="key">Cato</span> wilde hier een eind aan maken.</p>
<p>Cato sloot elke senaatstoespraak af met: <span class="key">"Overigens ben ik van mening dat Carthago verwoest moet worden!"</span> — ongeacht het onderwerp. Hij overleed in 149 v.C. en maakte de verwoesting zelf niet mee.</p>
<p>De Romeinen <span class="key">vernietigden Carthago volledig</span>: stadsmuren neergehaald, 50.000 overlevenden als slaven verkocht, grond met zout onvruchtbaar gemaakt. Een eeuw lang mocht hier niemand wonen, tot keizer Augustus het verbod ophief.</p>
</div>

<div class="card">
<h3>10. Gevolgen van de Punische oorlogen</h3>
<p><span class="datum">146 v.C.</span>: Carthago wordt ingelijfd als de Romeinse provincie <span class="key">Africa</span>.</p>
<p>Rome wordt de grootste <span class="key">militaire</span> en <span class="key">economische</span> macht in het Middellandse Zeegebied.</p>
</div>

<div class="card">
<h3>11. Verdeel en heers (divide et impera)</h3>
<p>Rome groeit van een boerendorpje tot heer en meester van de Middellandse Zee. Hoe zo een groot gebied controleren? Via de <span class="key">verdeel-en-heerstactiek</span>.</p>
<p><span class="key">Onderworpen statuut</span> (ongunstig): moet extra belastingen betalen, mag zichzelf niet besturen. Kan een beter statuut krijgen door Rome trouw te dienen en niet in opstand te komen.</p>
<p><span class="key">Bevoorrecht statuut</span> (gunstig): moet belastingen betalen en soldaten leveren. In ruil biedt Rome <span class="key">bescherming</span>. Mag eigen bestuur behouden. Kan statuut verliezen bij opstand of ontrouw.</p>
</div>
</div>

<!-- TOPIC 3: Les 20 -->
<div class="topic-content" data-topic="3">
<h2>Les 20: De veroveringen wijzigen de Romeinse samenleving</h2>

<div class="card">
<h3>1. De kleine boer gaat ten onder</h3>
<p>Reden 1: Het Romeinse leger bestond voornamelijk uit <span class="key">boeren</span> (arme plebejers). Tijdens oorlogen konden ze hun grond niet bewerken.</p>
<p>Reden 2: Om oorlogen te financieren verhoogt Rome de <span class="key">belastingen</span>, die ook de gewone boer moet meebetalen.</p>
<p>Reden 3: Na de oorlogen kan men niet <span class="key">concurreren</span> met de goedkopere landbouwproducten die vanuit de veroverde gebieden worden ingevoerd.</p>
</div>

<div class="card">
<h3>2. Plattelandsvlucht</h3>
<p><span class="key">Plattelandsvlucht</span> = het verschijnsel dat boeren hun platteland verlaten en naar de stad trekken. De arme boeren <span class="key">verkopen</span> hun bezittingen aan <span class="key">grootgrondbezitters</span> (patriciërs en rijke plebejers).</p>
<p>Deze grootgrondbezitters vormen <span class="key">latifundia</span> = enorme landgoederen in bezit van één rijke man. De boerenhofsteden werden gesloopt.</p>
<p>De verarmde boeren trekken naar de stad <span class="key">Rome</span> om daar werk te zoeken.</p>
</div>

<div class="card">
<h3>3. Arm versus rijk in Rome</h3>
<p>De gewezen boer vindt in Rome <span class="key">geen</span> werk. Reden: <span class="key">slavenarbeid</span> is veel goedkoper. Toch blijven meer en meer boeren toestromen. Rome wordt een stad met een kleine groep rijken en een steeds groter wordende groep armen.</p>
<p><span class="key">Proletariërs</span> (bezitlozen): verarmde boeren (plebejers) en slaven. Ze beschikken over <span class="key">stemrecht</span> — wie hun stem wil, moet ervoor betalen (uitgezonderd slaven). Ze zijn met veel (100.000-en). Voedseltekort = opstanden!</p>
<p><span class="key">Nobilis</span> (bezittenden): aristocraten/patriciërs en rijke plebejers (na Lex Hortensia). Zij besturen het Romeinse Rijk en moeten voor de proletariërs zorgen, anders dreigen opstanden. Daarom organiseren ze <span class="key">Brood & Spelen</span>.</p>
</div>

<div class="card">
<h3>4. De Gracchen proberen de boerenstand te herstellen</h3>
<p><span class="key">Tiberius</span> en <span class="key">Gaius</span> Gracchus (de Gracchen): afkomstig uit een <span class="key">patricische</span> familie. Beiden werden <span class="key">volkstribuun</span> en probeerden als zodanig de macht van de nobilis te breken.</p>
<p>Hun drie wetten: <span class="key">Landwet</span> = staatsland (in bezit van de senaat) onder de arme boeren verdelen. <span class="key">Graanwet</span> = goedkoper graan voor de armen. <span class="key">Legerwet</span> = soldaten krijgen gratis kledij en gevechtsuitrusting, vanaf 17 jaar oproepbaar.</p>
<p>Afloop: Tiberius werd vermoord in <span class="datum">133 v.C.</span> samen met 3000 aanhangers. Gaius onderging hetzelfde lot in <span class="datum">121 v.C.</span> Ze werden te populair bij de proletariërs = te machtig! Hun maatregelen werden <span class="key">ingetrokken</span>.</p>
</div>

<div class="card">
<h3>5. Optimates versus populares</h3>
<p>Na de dood van de Gracchen ontstaan twee politieke kampen. Rome wordt ondergedompeld in een eeuw van bloederige <span class="key">burgeroorlogen</span> tussen beide groepen.</p>
<p><span class="key">Optimates</span>: burgers uit rijke (patricische) families met al veel politieke ervaring. Willen dat de macht bij de <span class="key">senaat</span> blijft. Partij van de rijken. Stemmen van de nobilis. Bekende leden: <span class="key">Sulla, Crassus, Pompeius</span>.</p>
<p><span class="key">Populares</span>: burgers uit families die nog geen politieke ervaring hebben. Willen alle macht aan de <span class="key">volksvergadering</span> geven. Partij van het gewone volk. Stemmen van proletariërs en het kleine volk. Bekende leden: <span class="key">Marius, Caesar, Marcus Antonius</span>.</p>
</div>
</div>

<!-- TOPIC 4: Les 21 -->
<div class="topic-content" data-topic="4">
<h2>Les 21: De burgeroorlogen</h2>

<div class="card">
<h3>1. Buitenlandse bedreigingen</h3>
<p>Eind <span class="datum">2e eeuw v.C.</span>: Rome krijgt te maken met buitenlandse bedreigingen. De koning van <span class="key">Numidië</span> en <span class="key">Germaanse</span> stammen bedreigen het rijk.</p>
<p>De volksvergadering benoemt <span class="key">Marius</span> tot consul. Marius is lid van de <span class="key">populares</span>.</p>
</div>

<div class="card">
<h3>2. Marius' legerhervorming</h3>
<p>Marius vult zijn leger aan met mannen uit de <span class="key">bezitloze</span> klasse (proletariërs). Dit was revolutionair.</p>
<p>Motivatie: ze worden <span class="key">betaald</span>, krijgen recht op voedsel en uitrusting, en bij pensioen een stuk <span class="key">grond</span> in een veroverd gebied.</p>
<p>Gevolg: soldaten luisteren vooral naar de <span class="key">generaal</span> die hen bezittingen belooft. Macht van de consul stijgt, macht van de senaat daalt. Van <span class="key">burgerleger</span> naar <span class="key">beroepsleger</span>.</p>
</div>

<div class="card">
<h3>3. Marius vs. Sulla (88 – 81 v.C.)</h3>
<p>Na de bondgenotenoorlog (<span class="datum">91 v.C.</span>) dreigt <span class="key">Mithridates</span> (koning van Pontus in Klein-Azië).</p>
<p>De senaat kiest <span class="key">Sulla</span> (optimates) om te strijden. Marius gaat niet akkoord. Sulla trekt toch naar Klein-Azië. Marius en zijn leger vermoorden aanhangers van Sulla.</p>
<p>Na Marius' dood keert Sulla terug. Hij wordt <span class="key">dictator</span>: vervolgt aanhangers van de populares, beperkt de macht van de volkstribuun. De echte macht ligt niet langer bij de senaat, maar bij wie het sterkste leger heeft.</p>
</div>

<div class="card">
<h3>4. Nieuwe problemen na Sulla</h3>
<p>Bedreigingen: <span class="key">zeerovers</span>, koning Mithridates, een <span class="key">slavenopstand</span> (olv Spartacus), corrupte gouverneurs.</p>
<p>Drie sterke mannen vormen een <span class="key">triumviraat</span>: <span class="key">Pompeius</span> (optimates), <span class="key">Caesar</span> (populares), en <span class="key">Crassus</span>. Zij besturen het rijk samen.</p>
</div>

<div class="card">
<h3>5. Pompeius vs. Caesar (49 – 45 v.C.)</h3>
<p>Verdeling: Crassus krijgt Syrië (sneuvelt), Pompeius krijgt Rome (steun senaat), Caesar krijgt Gallië (verovert het volledig → enorme roem).</p>
<p><span class="key">Pompeius</span> vreest zijn macht te verliezen. Met steun van de senaat verklaart hij Caesar de oorlog.</p>
<p>Caesar <span class="key">wint</span> en wordt <span class="key">dictator voor het leven</span>. Maar in <span class="datum">44 v.C.</span> wordt hij <span class="key">vermoord</span> (complot, o.a. door Brutus).</p>
</div>

<div class="card">
<h3>6. Octavianus vs. Marcus Antonius (32 – 31 v.C.)</h3>
<p>Na Caesars dood: <span class="key">Marcus Antonius</span> en <span class="key">Octavianus</span> (adoptiezoon Caesar) schakelen de moordenaars uit.</p>
<p>Nieuw triumviraat: Octavianus, Marcus Antonius, Lepidus. Lepidus is militair te zwak. Marcus Antonius sluit een verbond met <span class="key">Cleopatra</span> (Egypte).</p>
<p>De senaat ziet dit als een bedreiging (staatsgreep). Octavianus verslaat het koppel bij de <span class="key">Slag bij Actium</span> (<span class="datum">31 v.C.</span>). Egypte wordt bij het Romeinse Rijk gevoegd. Het <span class="key">keizerrijk</span> begint.</p>
</div>
</div>

<!-- TOPIC 5: Les 22 -->
<div class="topic-content" data-topic="5">
<h2>Les 22: Augustus, de eerste keizer</h2>

<div class="card">
<h3>1. Octavianus wordt Augustus</h3>
<p><span class="datum">27 v.C.</span>: Octavianus herstelt de republiek na de burgeroorlogen. Hij geeft de senaat haar macht terug — althans schijnbaar.</p>
<p>De senaat vreest nieuwe burgeroorlogen. Octavianus mag het rijk blijven besturen. Hij krijgt twee titels: <span class="key">Princeps</span> (= eerste burger) en <span class="key">Augustus</span> (= verhevene).</p>
</div>

<div class="card">
<h3>2. Van schijnrepubliek naar keizerrijk</h3>
<p>Alle instellingen van de republiek blijven bestaan. Maar Octavianus neemt de belangrijkste functies: <span class="key">imperator</span> (opperbevelhebber leger), <span class="key">volkstribuun</span> (vetorecht), <span class="key">organisator festiviteiten</span> (populair).</p>
<p>De senaat houdt de rustige provincies. Augustus houdt de <span class="key">onrustige grensprovincies</span> (groot leger nodig) en <span class="key">rijke provincies</span> (graanvoorraden, zoals Egypte).</p>
<p>Stilletjes trekt Octavianus alle macht naar zich toe = <span class="key">autocratie</span>. Het Romeinse keizerrijk loopt van <span class="datum">27 v.C.</span> tot <span class="datum">476 n.C.</span></p>
</div>

<div class="card">
<h3>3. Augustus versterkt zijn macht</h3>
<p>Egypte levert grote <span class="key">graanvoorraden</span> op. Augustus deelt regelmatig brood en geld uit aan de armen (<span class="key">Brood & Spelen</span>).</p>
<p>Hij laat grote <span class="key">bouwwerken</span> uitvoeren en zet daarvoor proletariërs aan het werk (= inkomen). Hij organiseert gratis spelen (gladiatoren). Het volk verzet zich dus niet.</p>
</div>

<div class="card">
<h3>4. Natuurlijke grenzen</h3>
<p>Augustus bakent het rijk af met <span class="key">natuurlijke grenzen</span>: in het westen en zuiden de Atlantische Oceaan en de Sahara, in het noorden de <span class="key">Rijn</span> en <span class="key">Donau</span>, in het oosten de <span class="key">Eufraat</span>.</p>
<p>Tactiekwissel: vóór Augustus = <span class="key">uitbreidingstactiek</span>. Vanaf Augustus = <span class="key">verdedigingstactiek</span>.</p>
<p><span class="key">Legioenen</span> verdedigen de grenzen. In opstandige provincies zijn troepen aanwezig. Op de Middellandse Zee houdt een vloot alles in het oog. Men spreekt van de <span class="key">Pax Romana</span> = het Romeinse leger zorgt voor vrede en welvaart.</p>
</div>

<div class="card">
<h3>5. Opvolging</h3>
<p>Augustus hoopte op een mannelijk familielid als opvolger. Al zijn mogelijke opvolgers stierven vrij jong, onder verdachte omstandigheden.</p>
<p>Hij adopteerde twee zonen van zijn derde vrouw. <span class="key">Tiberius</span> volgde hem op na zijn dood in <span class="datum">14 n.C.</span></p>
</div>
</div>

<!-- TOPIC 6: Les 23+25 -->
<div class="topic-content" data-topic="6">
<h2>Les 23 + 25: Bloei en verval van het Romeinse Rijk</h2>

<div class="card">
<h3>1. De eerste keizers na Augustus (14 – 68 n.C.)</h3>
<p><span class="datum">14 n.C.</span>: Augustus sterft, opgevolgd door <span class="key">Tiberius</span> (zijn adoptiefzoon). Tiberius en zijn opvolgers zijn allemaal familie van elkaar, maar geen goede leiders.</p>
<p>Vooral <span class="key">Caligula</span> en <span class="key">Nero</span> zijn bloeddorstig en gestoord. De senaat probeert de republiek te herstellen maar faalt: de senaat is onderling verdeeld (populares vs optimates).</p>
<p>Ondanks de slechte heerschappij groeit de macht: <span class="key">Mare Nostrum</span> = alle landen rond de Middellandse Zee behoren tot het R.R. <span class="datum">68 n.C.</span>: Nero pleegt zelfmoord → de Flaviërs komen aan de macht.</p>
</div>

<div class="card">
<h3>2. De Flaviërs (69 – 96 n.C.)</h3>
<p>Eerste keizer: <span class="key">Vespasianus</span>. Probleem: opstand van de Joden in Palestina. Samen met zijn zoon <span class="key">Titus</span> onderdrukt hij die opstand en verwoest Jeruzalem → het Joodse volk verspreidt zich.</p>
<p>De Flaviërs laten belangrijke bouwwerken bouwen, zoals het <span class="key">Colosseum</span>.</p>
<p>Laatste Flaviër: <span class="key">Domitianus</span> (tweede zoon). Voltooit de verovering van Brittannië. Wordt vermoord na een schrikbewind.</p>
</div>

<div class="card">
<h3>3. De adoptiekeizers (96 – 180 n.C.)</h3>
<p>De regerende keizer zoekt een bekwame opvolger en <span class="key">adopteert</span> die. <span class="key">Trajanus</span>: Spaanse afkomst, goede generaal en bestuurder, breidt het R.R. uit tot zijn <span class="key">grootste omvang</span>.</p>
<p><span class="key">Hadrianus</span>: stopt de veroveringen, geeft sommige gebieden terug. Laat de <span class="key">limes</span> (grenzen) versterken (vb. Muur van Hadrianus). Het R.R. kent de <span class="key">Pax Romana</span> (Romeinse Vrede).</p>
<p>Grote bouwwerken: aquaducten, tempels, wegen, badhuizen. <span class="key">Marcus Aurelius</span>: invallen van Germanen, start grensoorlogen. <span class="key">Commodus</span>: slecht bestuurder, interesse in spelen → macht valt uiteen.</p>
</div>

<div class="card">
<h3>4. Soldatenkeizers en de crisis van de 3e eeuw</h3>
<p><span class="datum">192 n.C.</span>: Commodus wordt vermoord. Generaals trekken met hun legers naar Rome → burgeroorlog. Winnaar: <span class="key">Severus</span>. Rome wordt bestuurd door soldatenkeizers.</p>
<p>Keizers volgen elkaar in sneltempo op. Generaals beloven steeds meer geld aan hun troepen → hogere belastingen → economie lijdt. Grenzen blijven onbeschermd → buurvolkeren vallen binnen.</p>
<p>Gevolgen: handel ontregeld, landbouwproductie daalt, bevolkingsaantal daalt (oorlogen, hongersnood, ziektes). Rijke gebieden willen zich afscheiden.</p>
</div>

<div class="card">
<h3>5. Diocletianus en Constantijn</h3>
<p><span class="datum">284 n.C.</span>: <span class="key">Diocletianus</span> wordt keizer via een staatsgreep. Hij ontneemt de senaat het laatste restje macht. De keizer = enige machthebber, moet vereerd worden als een god.</p>
<p>Hij <span class="key">splitst</span> het rijk in twee delen: Oost en West = <span class="key">Tetrarchie</span> (vier heersers: 2 keizers + 2 medekeizers).</p>
<p><span class="datum">306 n.C.</span>: <span class="key">Constantijn</span> schenkt de christenen <span class="key">godsdienstvrijheid</span>. Hij maakt van Byzantium de nieuwe hoofdstad: <span class="key">Constantinopel</span>.</p>
</div>

<div class="card">
<h3>6. Volksverhuizingen en het einde</h3>
<p>Problemen: verzwakte legioenen en nieuwe volksverhuizingen. Barbaarse stammen (vb. <span class="key">Germanen</span>) willen zich vestigen in het R.R.: ze zoeken betere levensomstandigheden en vluchten voor de <span class="key">Hunnen</span> (Aziatisch volk).</p>
<p>Sommige stammen mogen zich vestigen als <span class="key">hulptroepen</span> (foederati), maar dit mislukt.</p>
<p><span class="datum">395 n.C.</span>: Theodosius splitst het R.R. definitief in <span class="key">West</span> (verdwijnt <span class="datum">476 n.C.</span>) en <span class="key">Oost</span> (verdwijnt <span class="datum">1453</span>).</p>
</div>
</div>

</div><!-- end mod-cours -->

<!-- ==================== MODULE 2: EXERCICES ==================== -->
<div id="mod-exercices" class="section">
<div class="score-bar" id="scoreBar">Score: 0/0 — Kies een topic om te beginnen</div>
<div class="timer-box" id="timerBox">
  <label><input type="checkbox" id="timerToggle" onchange="toggleTimer()"> Timer activeren</label>
  <span class="timer-display" id="timerDisplay">00:00</span>
  <button onclick="resetTimer()">Reset</button>
</div>
<div id="exerciseArea"></div>
</div>

<!-- ==================== MODULE 3: EXAMEN ==================== -->
<div id="mod-examen" class="section">
<h2>Examens downloaden (PDF — A4, manuscrit)</h2>
<p>Klik op een topic om het examen te genereren. Elk examen bevat genummerde vragen met ruimte voor handgeschreven antwoorden, barème op /20.</p>
<div id="examenButtons"></div>
<div id="examenPreview" style="margin-top:16px;"></div>
</div>

<!-- ==================== MODULE 4: CORRECTIF ==================== -->
<div id="mod-correctif" class="section">
<h2>Correctiesleutels downloaden</h2>
<p>Gedetailleerde antwoorden met puntenverdeling per vraag. Totaal op /20.</p>
<div id="correctifButtons"></div>
<div id="correctifPreview" style="margin-top:16px;"></div>
</div>

<script>
// ======================== DATA ========================
const TOPICS = [
  "Les 17: Rome als koninkrijk",
  "Les 18: De Romeinse republiek",
  "Les 19: Rome wordt machtig",
  "Les 20: Veroveringen wijzigen de samenleving",
  "Les 21: De burgeroorlogen",
  "Les 22: Augustus, de eerste keizer",
  "Les 23+25: Bloei & verval"
];

// EXERCISE DATA: array per topic, each item = {type, question, options?, answer, explanation}
const EXERCISES = [
  // TOPIC 0: Les 17
  [
    {type:"mcq", q:"Wanneer werd Rome volgens de mythe gesticht?", opts:["509 v.C.","753 v.C.","1000 v.C.","814 v.C."], ans:1, expl:"Volgens de mythe is Rome gesticht in 753 v.C. door Romulus."},
    {type:"mcq", q:"Wie zijn volgens de mythe de stichters van Rome?", opts:["Aeneas en Dido","Romulus en Remus","Julius en Augustus","Tarquinius en Brutus"], ans:1, expl:"Romulus en Remus zijn de mythische stichters. Romulus doodde Remus."},
    {type:"tf", q:"De Romeinen zijn Indo-Europeanen.", ans:true, expl:"Correct. De Romeinen zijn Indo-Europeanen die zich rond 1000 v.C. in Italië vestigden."},
    {type:"fill", q:"De eerste nederzettingen ontstonden in de regio ________.", ans:"latium", expl:"Latium is het gebied waar de eerste Romeinse nederzettingen ontstonden."},
    {type:"mcq", q:"Aan welke rivier is Rome gelegen?", opts:["Po","Arno","Tiber","Donau"], ans:2, expl:"Rome is gelegen aan de Tiber."},
    {type:"tf", q:"De Etrusken woonden in Zuid-Italië.", ans:false, expl:"Fout. De Etrusken woonden in Noordwest-Italië, tussen de Tiber en de Arno."},
    {type:"mcq", q:"Wie stond aan het hoofd van de Romeinse familia?", opts:["De moeder","De pater familias","De oudste zoon","De senaat"], ans:1, expl:"De pater familias (vader) stond aan het hoofd van het hele huishouden."},
    {type:"fill", q:"De rijke grondbezitters in Rome heten de ________.", ans:"patriciërs", expl:"Patriciërs waren de adel en grootgrondbezitters in Rome."},
    {type:"mcq", q:"Welk volk had invloed op de Romeinse bouwkunst (rondbogen, bakstenen)?", opts:["Grieken","Feniciërs","Etrusken","Kelten"], ans:2, expl:"De Etrusken leerden de Romeinen werken met rondbogen en bakstenen."},
    {type:"tf", q:"De eerste bestuursvorm van Rome was een republiek.", ans:false, expl:"Fout. De eerste bestuursvorm was een koninkrijk."},
    {type:"mcq", q:"Wat is een 'gens'?", opts:["Een soort tempel","Een groep families met dezelfde voorvader","Een Romeins leger","Een type munt"], ans:1, expl:"Een gens is een groep families die beweerden van dezelfde voorvader af te stammen."},
    {type:"fill", q:"De Grieken stichtten kolonies in het ________ van Italië.", ans:"zuiden", expl:"De Grieken vestigden zich in Zuid-Italië (Magna Graecia)."}
  ],
  // TOPIC 1: Les 18
  [
    {type:"mcq", q:"In welk jaar werd de Romeinse republiek gesticht?", opts:["753 v.C.","509 v.C.","287 v.C.","264 v.C."], ans:1, expl:"De republiek werd gesticht in 509 v.C. na de verdrijving van Tarquinius Superbus."},
    {type:"fill", q:"De laatste Romeinse koning heette Tarquinius ________.", ans:"superbus", expl:"Tarquinius Superbus werd verjaagd in 509 v.C."},
    {type:"mcq", q:"Hoeveel consuls bestuurden de Romeinse republiek?", opts:["1","2","3","4"], ans:1, expl:"Er waren twee consuls die elkaar controleerden."},
    {type:"tf", q:"De consuls werden gekozen voor het leven.", ans:false, expl:"Fout. Consuls werden gekozen voor 1 jaar."},
    {type:"mcq", q:"Wat is het vetorecht?", opts:["Het recht om wetten te maken","Het recht om oorlog te verklaren","Het recht om beslissingen tegen te houden","Het recht om belastingen te heffen"], ans:2, expl:"Vetorecht = het recht om andermans beslissingen tegen te houden."},
    {type:"fill", q:"Als de consuls niet overeenkwamen, mocht de senaat een ________ aanstellen.", ans:"dictator", expl:"Een dictator kreeg 6 maanden om een crisis op te lossen."},
    {type:"mcq", q:"Welke wet stelde plebejers en patriciërs juridisch gelijk?", opts:["Lex Julia","Lex Hortensia","Lex Aquilia","Lex Cornelia"], ans:1, expl:"De Lex Hortensia (287 v.C.) maakte plebejers juridisch gelijk aan patriciërs."},
    {type:"tf", q:"Vanaf 367 v.C. mocht één consul een plebejer zijn.", ans:true, expl:"Correct. Dit was een belangrijke stap in de gelijkheidsstrijd."},
    {type:"mcq", q:"Wie verdedigde de belangen van de plebejers?", opts:["De consul","De dictator","De volkstribuun","De augur"], ans:2, expl:"De volkstribuun verdedigde de belangen van de plebejers en had vetorecht."},
    {type:"fill", q:"De rijke elite in de late republiek heette de ________.", ans:"nobilis", expl:"De nobilis waren de nieuwe rijke elite (patriciërs + rijke plebejers)."},
    {type:"tf", q:"In de Romeinse republiek werd je betaald als politicus.", ans:false, expl:"Fout. In de Romeinse politiek werd je niet betaald, wat het voor armen onmogelijk maakte om hoge functies te bekleden."},
    {type:"mcq", q:"Wat was de aanleiding van de gelijkheidsstrijd?", opts:["Te hoge belastingen","Plebejers moesten vechten maar kregen geen rechten","Invasie van de Kelten","Conflict met Carthago"], ans:1, expl:"Plebejers moesten soldaten leveren en belastingen betalen, maar kregen niet de beloofde rechten."}
  ],
  // TOPIC 2: Les 19
  [
    {type:"mcq", q:"Door welk volk werd Carthago gesticht?", opts:["Grieken","Etrusken","Feniciërs","Kelten"], ans:2, expl:"Carthago werd gesticht door de Feniciërs in 814 v.C."},
    {type:"fill", q:"De oorlogen tussen Rome en Carthago heten de ________ oorlogen.", ans:"punische", expl:"Punische oorlogen — de Romeinen noemden Carthagers 'Poeni'."},
    {type:"mcq", q:"Hoeveel Punische oorlogen waren er?", opts:["2","3","4","5"], ans:1, expl:"Er waren drie Punische oorlogen (264–146 v.C.)."},
    {type:"mcq", q:"Over welk eiland ging de eerste Punische oorlog?", opts:["Sardinië","Corsica","Kreta","Sicilië"], ans:3, expl:"Beide partijen wilden de heerschappij over Sicilië (graanproductie)."},
    {type:"fill", q:"De Gallische leider die Rome bezette in 390 v.C. heette ________.", ans:"brennus", expl:"Brennus leidde het Gallische leger richting Rome. Na 7 maanden eisten ze losgeld."},
    {type:"mcq", q:"Hoeveel olifanten nam Hannibal mee door de Alpen?", opts:["12","27","42","60"], ans:2, expl:"Hannibal nam 42 olifanten mee op zijn tocht door de Alpen."},
    {type:"tf", q:"Rome verloor de tweede Punische oorlog.", ans:false, expl:"Fout. Rome won uiteindelijk dankzij de trouw van de bondgenoten en de overwinning van Scipio Africanus bij Zama."},
    {type:"mcq", q:"Bij welke slag verloor Rome 60.000 tot 80.000 soldaten in 8 uur?", opts:["Slag bij Zama","Slag bij Cannae","Slag bij Actium","Slag bij Trebia"], ans:1, expl:"Bij de Slag bij Cannae (216 v.C.) bezorgde Hannibal het Romeinse leger de bloedigste nederlaag ooit."},
    {type:"fill", q:"De Romeinse generaal die Hannibal versloeg bij Zama heette Scipio ________.", ans:"africanus", expl:"Scipio Africanus lokte Hannibal uit Italië en versloeg hem bij Zama in 202 v.C."},
    {type:"mcq", q:"Welke senator sloot elke toespraak af met de eis om Carthago te vernietigen?", opts:["Cicero","Cato","Brutus","Scipio"], ans:1, expl:"Senator Cato sloot elke senaatstoespraak af met: 'Overigens ben ik van mening dat Carthago verwoest moet worden!'"},
    {type:"tf", q:"Na de vernietiging van Carthago werd het gebied onvruchtbaar gemaakt met zout.", ans:true, expl:"Correct. De grond werd omgeploegd met zout zodat er niets meer kon groeien."},
    {type:"mcq", q:"Hoe noemden de Romeinen hun verdeel-en-heerstactiek?", opts:["Pax Romana","Divide et impera","Mare Nostrum","Lex Hortensia"], ans:1, expl:"Divide et impera = verdeel en heers."},
    {type:"fill", q:"In 270 v.C. regeert Rome over heel Italië ten zuiden van de rivier de ________.", ans:"po", expl:"De Po is de grote rivier in Noord-Italië."},
    {type:"mcq", q:"Wat verloor Carthago na de eerste Punische oorlog?", opts:["Haar leger","Haar oorlogsvloot","Haar handelsroutes","Haar koning"], ans:1, expl:"Na de eerste Punische oorlog verloor Carthago haar oorlogsvloot, wat Hannibal dwong via land aan te vallen."},
    {type:"tf", q:"De Galliërs bezetten Rome 7 maanden lang voordat ze losgeld eisten.", ans:true, expl:"Correct. Na 7 maanden vonden de Kelten de stad maar niks en eisten ze losgeld."},
    {type:"mcq", q:"Wat betekent de achternaam 'Barkas' van Hannibal?", opts:["Leeuw","Bliksem","Overwinnaar","Strijder"], ans:1, expl:"Barkas betekent 'bliksem'. Hannibal betekent 'genade van Ba'al' (god)."}
  ],
  // TOPIC 3: Les 20
  [
    {type:"mcq", q:"Waarom gingen kleine Romeinse boeren ten onder?", opts:["Ze werden aangevallen door piraten","Ze moesten vechten en konden hun land niet bewerken","Ze weigerden belastingen te betalen","Ze verhuisden vrijwillig naar Gallië"], ans:1, expl:"Boeren moesten dienen als soldaat en konden intussen hun land niet bewerken."},
    {type:"fill", q:"Goedkope arbeid door ________ maakte het moeilijk voor verarmde boeren om werk te vinden in Rome.", ans:"slaven", expl:"Slavenarbeid was veel goedkoper dan vrije arbeid."},
    {type:"mcq", q:"Wat is 'plattelandsvlucht'?", opts:["Boeren die naar het platteland trekken","Boeren die hun platteland verlaten en naar de stad trekken","Een militaire operatie op het platteland","De verwoesting van dorpen door het leger"], ans:1, expl:"Plattelandsvlucht = het verschijnsel dat boeren hun platteland verlaten en naar de stad trekken."},
    {type:"fill", q:"De grote landgoederen van één rijke eigenaar heetten ________.", ans:"latifundia", expl:"Latifundia = enorme landgoederen in bezit van één rijke man, na het opkopen van boerengronden."},
    {type:"tf", q:"De Gracchen waren afkomstig uit een arme familie.", ans:false, expl:"Fout. De Gracchen kwamen uit een patricische (rijke) familie."},
    {type:"mcq", q:"Welke functie bekleedden de Gracchen?", opts:["Consul","Dictator","Volkstribuun","Senator"], ans:2, expl:"Beide broers waren volkstribuun en probeerden zo de macht van de nobilis te breken."},
    {type:"mcq", q:"Wat wilde de Landwet van de Gracchen bereiken?", opts:["Nieuwe wegen aanleggen","Staatsland verdelen onder arme boeren","Hogere belastingen voor de rijken","Slaven bevrijden"], ans:1, expl:"De Landwet wilde staatsland (in bezit van de senaat) verdelen onder de arme boeren."},
    {type:"mcq", q:"In welk jaar werd Tiberius Gracchus vermoord?", opts:["146 v.C.","133 v.C.","121 v.C.","91 v.C."], ans:1, expl:"Tiberius werd vermoord in 133 v.C. samen met 3000 aanhangers. Gaius volgde in 121 v.C."},
    {type:"fill", q:"De partij van de rijke senatoren heette de ________.", ans:"optimates", expl:"Optimates vertegenwoordigden de belangen van de rijke elite en wilden dat de macht bij de senaat bleef."},
    {type:"mcq", q:"Wie was een bekend lid van de populares?", opts:["Sulla","Crassus","Pompeius","Caesar"], ans:3, expl:"Caesar was een bekend lid van de populares. Sulla, Crassus en Pompeius waren optimates."},
    {type:"tf", q:"De populares wilden alle macht aan de volksvergadering geven.", ans:true, expl:"Correct. De populares kwamen op voor het gewone volk en wilden alle macht aan de volksvergadering."},
    {type:"mcq", q:"Wat organiseerden de rijken om opstanden van het volk te voorkomen?", opts:["Verkiezingen","Brood & Spelen","Oorlogen","Handelsreizen"], ans:1, expl:"Brood & Spelen: gratis voedsel en entertainment om het volk tevreden te houden."},
    {type:"tf", q:"Na de Lex Hortensia verdwenen alle sociale problemen in Rome.", ans:false, expl:"Fout. Politieke gelijkheid loste de economische problemen niet op. Enkel rijke plebejers profiteerden echt."},
    {type:"fill", q:"De bezitloze armen in Rome heetten de ________.", ans:"proletariërs", expl:"Proletariërs waren de bezitloze klasse in Rome."},
    {type:"mcq", q:"Welke Gracchus-wet zorgde voor goedkoper graan?", opts:["Landwet","Graanwet","Legerwet","Lex Hortensia"], ans:1, expl:"De Graanwet zorgde voor goedkoper graan voor de armen."},
    {type:"mcq", q:"Sulla, Crassus en Pompeius behoorden tot welke politieke groep?", opts:["Populares","Optimates","Proletariërs","Volkstribunen"], ans:1, expl:"Sulla, Crassus en Pompeius waren bekende leden van de optimates (partij van de senaat)."}
  ],
  // TOPIC 4: Les 21
  [
    {type:"mcq", q:"Tot welke politieke groep behoorde Marius?", opts:["Optimates","Populares","Patriciërs","Flaviërs"], ans:1, expl:"Marius was lid van de populares."},
    {type:"fill", q:"Marius vulde zijn leger aan met mannen uit de ________ klasse.", ans:"bezitloze", expl:"Marius rekruteerde proletariërs — revolutionair voor die tijd."},
    {type:"tf", q:"Na Marius' hervorming luisterden soldaten vooral naar de senaat.", ans:false, expl:"Fout. Soldaten luisterden naar de generaal die hen bezittingen beloofde. De macht van de senaat daalde."},
    {type:"mcq", q:"Wie was Sulla's politieke tegenstander?", opts:["Caesar","Pompeius","Marius","Octavianus"], ans:2, expl:"Marius (populares) en Sulla (optimates) vochten de eerste burgeroorlog uit."},
    {type:"mcq", q:"Wie leidde de slavenopstand in Zuid-Italië?", opts:["Hannibal","Cato","Spartacus","Mithridates"], ans:2, expl:"Spartacus leidde een grote slavenopstand."},
    {type:"fill", q:"Het samenwerkingsverband van Pompeius, Caesar en Crassus heet een ________.", ans:"triumviraat", expl:"Een triumviraat is een bestuur door drie personen."},
    {type:"mcq", q:"In welk jaar werd Caesar vermoord?", opts:["49 v.C.","44 v.C.","31 v.C.","27 v.C."], ans:1, expl:"Caesar werd vermoord in 44 v.C. door een complot."},
    {type:"tf", q:"Caesar veroverde Gallië vanuit zijn positie als consul.", ans:true, expl:"Correct. Caesar kreeg de Gallische provincies toegewezen en veroverde van daaruit heel Gallië."},
    {type:"mcq", q:"Wie versloeg Marcus Antonius en Cleopatra bij Actium?", opts:["Caesar","Sulla","Pompeius","Octavianus"], ans:3, expl:"Octavianus versloeg het koppel bij de Slag bij Actium in 31 v.C."},
    {type:"fill", q:"Na de Slag bij Actium voegde Octavianus het ________ rijk toe aan het R.R.", ans:"egyptische", expl:"Egypte werd een Romeinse provincie na de overwinning op Cleopatra."},
    {type:"tf", q:"De bondgenotenoorlog brak uit omdat bondgenoten het Romeinse burgerrecht wilden.", ans:true, expl:"Correct. In 91 v.C. kwamen bondgenoten in opstand voor het burgerrecht. De senaat gaf uiteindelijk toe."},
    {type:"mcq", q:"Wat voor soort leger had Rome vóór Marius?", opts:["Beroepsleger","Burgerleger","Huurlingenleger","Slavenleger"], ans:1, expl:"Vóór Marius bestond het Romeinse leger uit burgers met bezittingen (burgerleger)."}
  ],
  // TOPIC 5: Les 22
  [
    {type:"mcq", q:"Welke twee titels kreeg Octavianus van de senaat?", opts:["Consul en Dictator","Rex en Imperator","Princeps en Augustus","Tribunus en Censor"], ans:2, expl:"Princeps (eerste burger) en Augustus (verhevene)."},
    {type:"fill", q:"Octavianus' tactiek om schijnbaar de republiek te behouden maar alle macht naar zich toe te trekken heet ________.", ans:"autocratie", expl:"Autocratie = alleenheerschappij, hoewel de instellingen van de republiek schijnbaar bleven bestaan."},
    {type:"tf", q:"Augustus behield de macht over de grensprovincies.", ans:true, expl:"Correct. Augustus hield de onrustige grensprovincies (met grote legers) en de rijke provincies (met graanvoorraden)."},
    {type:"mcq", q:"Welke tactiek paste Augustus toe om het rijk te verdedigen?", opts:["Uitbreidingstactiek","Verdedigingstactiek","Guerrillatactiek","Diplomatieke tactiek"], ans:1, expl:"Augustus schakelde over van uitbreiding naar verdediging met natuurlijke grenzen."},
    {type:"fill", q:"De lange periode van vrede en welvaart onder Augustus heet de Pax ________.", ans:"romana", expl:"Pax Romana = Romeinse Vrede."},
    {type:"mcq", q:"Welke rivieren vormden de noordgrens van het Romeinse Rijk?", opts:["Tiber en Po","Rijn en Donau","Arno en Eufraat","Nijl en Tigris"], ans:1, expl:"De Rijn en de Donau vormden de noordgrens."},
    {type:"tf", q:"Het Romeinse keizerrijk duurde van 27 v.C. tot 476 n.C.", ans:true, expl:"Correct. Van Augustus (27 v.C.) tot de val van het West-Romeinse Rijk (476 n.C.)."},
    {type:"mcq", q:"Waarom deelde Augustus brood en geld uit?", opts:["Uit persoonlijke gulheid","Om opstanden te voorkomen","Om de senaat tevreden te stellen","Omdat de wet het verplichtte"], ans:1, expl:"Augustus gebruikte Brood & Spelen om het volk tevreden en rustig te houden."},
    {type:"fill", q:"De rivier die de oostgrens van het Romeinse Rijk vormde, was de ________.", ans:"eufraat", expl:"De Eufraat vormde de natuurlijke oostgrens."},
    {type:"mcq", q:"Wie volgde Augustus op?", opts:["Nero","Caligula","Tiberius","Vespasianus"], ans:2, expl:"Tiberius, de adoptiefzoon van Augustus, volgde hem op in 14 n.C."},
    {type:"tf", q:"Augustus werd door de senaat gedwongen om af te treden.", ans:false, expl:"Fout. Augustus behield de macht tot zijn dood in 14 n.C. en werd niet gedwongen af te treden."},
    {type:"mcq", q:"Wat was de functie van imperator?", opts:["Rechter","Opperbevelhebber van het leger","Schatbewaarder","Hogepriester"], ans:1, expl:"Imperator = opperbevelhebber van het leger, één van Augustus' belangrijkste functies."}
  ],
  // TOPIC 6: Les 23+25
  [
    {type:"mcq", q:"Welke keizers waren berucht bloeddorstig?", opts:["Trajanus en Hadrianus","Tiberius en Vespasianus","Caligula en Nero","Augustus en Commodus"], ans:2, expl:"Caligula en Nero staan bekend als bloeddorstig en gestoord."},
    {type:"fill", q:"'Mare Nostrum' betekent 'Onze ________'.", ans:"zee", expl:"Mare Nostrum = Onze Zee. Alle landen rond de Middellandse Zee behoorden tot het R.R."},
    {type:"mcq", q:"Wie was de eerste Flavische keizer?", opts:["Titus","Domitianus","Vespasianus","Nerva"], ans:2, expl:"Vespasianus was de eerste keizer van de Flaviërs (69 n.C.)."},
    {type:"tf", q:"Het Colosseum werd gebouwd door de Flaviërs.", ans:true, expl:"Correct. Het Colosseum werd gebouwd ter nagedachtenis van hun overwinningen."},
    {type:"mcq", q:"Onder welke keizer bereikte het Romeinse Rijk zijn grootste omvang?", opts:["Augustus","Hadrianus","Trajanus","Constantijn"], ans:2, expl:"Onder Trajanus bereikte het Romeinse Rijk zijn grootste uitbreiding."},
    {type:"fill", q:"Hadrianus liet de grenzen (= ________) van het Romeinse Rijk versterken.", ans:"limes", expl:"De limes zijn de versterkte grenzen van het Romeinse Rijk."},
    {type:"mcq", q:"Wat deed Diocletianus met het Romeinse Rijk?", opts:["Hij vergrootte het","Hij splitste het in tweeën","Hij gaf het terug aan de senaat","Hij maakte er een democratie van"], ans:1, expl:"Diocletianus splitste het rijk in een Oost- en West-Romeins Rijk (Tetrarchie)."},
    {type:"tf", q:"Constantijn maakte van Byzantium de nieuwe hoofdstad (Constantinopel).", ans:true, expl:"Correct. Constantinopel werd de nieuwe hoofdstad van het Oost-Romeinse Rijk."},
    {type:"mcq", q:"Waarom wilden Germaanse stammen zich in het R.R. vestigen?", opts:["Ze wilden het R.R. vernietigen","Ze zochten betere levensomstandigheden en vluchtten voor de Hunnen","Ze wilden Romeins burgerrecht","Ze wilden handel drijven"], ans:1, expl:"Germanen zochten beter land/klimaat en vluchtten voor de Hunnen."},
    {type:"fill", q:"In het jaar ________ n.C. splitste Theodosius het Romeinse Rijk definitief.", ans:"395", expl:"In 395 n.C. werd het rijk definitief gesplitst in West en Oost."},
    {type:"mcq", q:"Wanneer viel het West-Romeinse Rijk?", opts:["395 n.C.","410 n.C.","476 n.C.","1453 n.C."], ans:2, expl:"Het West-Romeinse Rijk viel in 476 n.C."},
    {type:"tf", q:"De soldatenkeizers brachten stabiliteit in het Romeinse Rijk.", ans:false, expl:"Fout. De soldatenkeizers volgden elkaar in sneltempo op en brachten chaos, hogere belastingen en economische crisis."}
  ]
];

// EXAM DATA per topic
const EXAMS = [
  { title:"Les 17: Rome als koninkrijk", questions:[
    {q:"Wanneer werd Rome volgens de mythe gesticht en door wie? (2pt)", a:"753 v.C. door Romulus (en Remus). Romulus doodde Remus en werd de eerste koning.", pts:2},
    {q:"De Romeinen zijn Indo-Europeanen. Wanneer vestigden ze zich op het Italische schiereiland? (1pt)", a:"Omstreeks 1000 v.C.", pts:1},
    {q:"Noem drie redenen waarom Rome een gunstige ligging had. (3pt)", a:"1) Midden op verbindingsweg N-Z Italië. 2) Heuvels/moerassen = natuurlijke verdediging. 3) Tiber ideaal voor transport + afstand tot zee = veilig voor zeerovers.", pts:3},
    {q:"Welke drie volkeren bewoonden het Italische schiereiland vóór de opkomst van Rome? Geef per volk aan waar ze woonden. (3pt)", a:"Etrusken (NW-Italië, tussen Tiber en Arno), Italische volksstammen/Latijnen (Midden-Italië), Grieken (Zuid-Italië, kolonies 8e-5e eeuw v.C.).", pts:3},
    {q:"Beschrijf de drie bevolkingsgroepen in de Romeinse samenleving. (3pt)", a:"Patriciërs: adel, grootgrondbezitters, politieke macht. Plebejers: vrije burgers, geen politieke macht, werken op grond patriciërs. Slaven: krijgsgevangenen, geen rechten, worden gezien als bezit.", pts:3},
    {q:"Wie stond aan het hoofd van de Romeinse familia en welke macht had hij? (2pt)", a:"De pater familias. Hij had absolute macht over zijn hele huishouden (vrouw, kinderen, slaven, bezittingen).", pts:2},
    {q:"Noem drie domeinen waarop de Etrusken de Romeinen beïnvloedden. (3pt)", a:"1) Politiek: koninkrijk als bestuursvorm. 2) Religie: augures/voorspellers. 3) Cultuur: alfabet, bouwkunst (rondbogen, tempels, riolen).", pts:3},
    {q:"Leg uit wat een 'gens' is. (1pt)", a:"Een groep families die beweerden van dezelfde voorvader af te stammen.", pts:1},
    {q:"Waarom is de stichtingsmythe van Rome niet betrouwbaar? (2pt)", a:"De mythe dateert pas uit de 3e eeuw v.C. — dat is eeuwen na de veronderstelde stichting (753 v.C.). Door het grote tijdsverschil is de betrouwbaarheid beperkt.", pts:2}
  ]},
  { title:"Les 18: De Romeinse republiek", questions:[
    {q:"Waarom werd de laatste koning, Tarquinius Superbus, verjaagd? Wanneer? (2pt)", a:"Hij had te veel macht en hield geen rekening meer met de senaat en volksvergadering. In 509 v.C.", pts:2},
    {q:"Beschrijf de drie belangrijkste instellingen van de Romeinse republiek en hun taken. (6pt)", a:"Consuls (2 stuks): 1 jaar, leiden leger + dagelijks bestuur. Senaat: voor het leven, beslist over oorlog/vrede, keurt wetten, kiest consuls. Volksvergadering: alle mannelijke burgers, keurt wetten goed/af.", pts:6},
    {q:"Hoe werden de consuls gecontroleerd? Noem twee mechanismen. (2pt)", a:"1) Ze zijn met twee en controleren elkaar. 2) Ze hebben vetorecht: het recht om elkaars beslissingen tegen te houden.", pts:2},
    {q:"Wat is een dictator in de Romeinse republiek? (2pt)", a:"Iemand die door de senaat wordt aangesteld wanneer de twee consuls niet overeenkomen. Hij krijgt 6 maanden om de crisis op te lossen.", pts:2},
    {q:"Beschrijf de vier stappen van de gelijkheidsstrijd der plebejers (498-287 v.C.). (4pt)", a:"1) Functie van volkstribuun (verdedigt plebejers, vetorecht). 2) Wetten worden schriftelijk vastgelegd. 3) 367 v.C.: één consul mag plebejer zijn. 4) 287 v.C.: Lex Hortensia = juridische gelijkstelling.", pts:4},
    {q:"Wat was de Lex Hortensia en wanneer werd die ingevoerd? (2pt)", a:"De Lex Hortensia (287 v.C.) stelde plebejers en patriciërs juridisch gelijk.", pts:2},
    {q:"Waarom loste de Lex Hortensia de sociale problemen niet op? (2pt)", a:"Om hoge functies te bekleden had je geld nodig (campagne, ervaring, geen loon). Alleen rijke plebejers profiteerden. Zo ontstond een nieuwe elite (nobilis) vs. bezitlozen (proletariërs).", pts:2}
  ]},
  { title:"Les 19: Rome wordt machtig", questions:[
    {q:"Wanneer en door wie werd Carthago gesticht? Geef twee kenmerken. (2pt)", a:"814 v.C. door de Feniciërs. Gelegen op de noordkust van Afrika. Machtige handelsstad met grote haven.", pts:2},
    {q:"Beschrijf oorzaak en afloop van de eerste Punische oorlog. (2pt)", a:"Oorzaak: strijd om heerschappij over Sicilië (graanproductie). Afloop: Rome wint, verwerft eerste gebieden buiten Italië.", pts:2},
    {q:"Beschrijf de rol van Hannibal in de tweede Punische oorlog. (3pt)", a:"Hannibal trok met leger + olifanten door de Alpen naar Italië. Hij versloeg de Romeinen meermaals, maar dankzij de trouw van bondgenoten (Latijnse bond) won Rome uiteindelijk.", pts:3},
    {q:"Hoe eindigde de derde Punische oorlog? Noem drie gevolgen voor Carthago. (3pt)", a:"Carthago werd volledig verwoest: muren neergehaald, 50.000 als slaven verkocht, grond met zout onvruchtbaar gemaakt.", pts:3},
    {q:"Leg de verdeel-en-heerstactiek uit. Beschrijf de twee soorten statuten. (4pt)", a:"Gunstig: belastingen + soldaten leveren, in ruil bescherming + eigen bestuur. Verlies bij opstand. Ongunstig: extra belastingen, geen eigen bestuur, kans op gunstig statuut bij trouw.", pts:4},
    {q:"Wat gebeurde er in 390 v.C.? (2pt)", a:"De Galliërs (Kelten) veroverden Rome voor korte tijd, eisten losgeld, en Rome betaalde. Daarna trokken ze weer weg.", pts:2},
    {q:"In welk jaar regeert Rome over heel Italië (ten zuiden van de Po)? (1pt)", a:"270 v.C.", pts:1},
    {q:"Wat wordt Carthago na de vernietiging in 146 v.C.? (1pt)", a:"De Romeinse provincie Africa.", pts:1},
    {q:"Waarom is Sicilië zo belangrijk in de eerste Punische oorlog? (2pt)", a:"Sicilië had grote graanproductie (vruchtbaar gebied). Beide partijen wilden de heerschappij over dit strategische eiland.", pts:2}
  ]},
  { title:"Les 20: Veroveringen wijzigen de samenleving", questions:[
    {q:"Noem drie redenen waarom de kleine Romeinse boer ten onderging. (3pt)", a:"1) Boeren moesten als soldaat dienen → land niet bewerkt. 2) Rome verhoogt belastingen. 3) Goedkope producten uit veroverde gebieden → oneerlijke concurrentie.", pts:3},
    {q:"Wat deden de verarmde boeren? (2pt)", a:"Ze verkochten hun bezittingen aan grootgrondbezitters en trokken naar Rome om werk te zoeken.", pts:2},
    {q:"Waarom vonden verarmde boeren weinig werk in Rome? (1pt)", a:"Slavenarbeid was veel goedkoper.", pts:1},
    {q:"Wie waren de Gracchen? Noem hun drie wetten met inhoud. (4pt)", a:"Tiberius en Gaius Gracchus, uit vooraanstaande familie. Akkerweg: staatsland verdelen onder arme boeren. Graanwet: goedkoper graan. Legerwet: gratis kleding/uitrusting voor soldaten, oproepbaar vanaf 17 jaar.", pts:4},
    {q:"Wat gebeurde er met de Gracchen en waarom? (2pt)", a:"Beide werden vermoord omdat ze te populair werden bij de proletariërs (te machtig). Hun maatregelen werden teruggedraaid.", pts:2},
    {q:"Beschrijf het verschil tussen optimates en populares. (4pt)", a:"Optimates: rijke families, veel politieke ervaring, partij van de senaat, willen veranderingen voor rijken. Populares: nog weinig politieke ervaring, willen veranderingen voor het gewone volk, stemmen van proletariërs en klein volk.", pts:4},
    {q:"Wat is 'Brood & Spelen' en waarom werd het georganiseerd? (2pt)", a:"Gratis voedsel en entertainment (gladiatorenspelen) voor het volk. Doel: opstanden voorkomen door de armen tevreden te houden.", pts:2},
    {q:"Wie waren de proletariërs? (2pt)", a:"Bezitloze armen: verarmde boeren (plebejers) en vrijgelaten slaven. Ze hadden wel stemrecht en waren met 100.000-en.", pts:2}
  ]},
  { title:"Les 21: De burgeroorlogen", questions:[
    {q:"Beschrijf Marius' legerhervorming en noem drie gevolgen. (4pt)", a:"Marius vulde het leger aan met bezitlozen (proletariërs). Gevolgen: 1) Soldaten werden betaald. 2) Ze kregen grond bij pensioen. 3) Ze luisterden naar de generaal (niet de senaat) → macht consul steeg, macht senaat daalde.", pts:4},
    {q:"Beschrijf kort het verloop van de eerste burgeroorlog (Marius vs. Sulla). (3pt)", a:"Senaat kiest Sulla (optimates) voor strijd tegen Mithridates. Marius (populares) gaat niet akkoord. Sulla trekt naar Klein-Azië, Marius vermoordt Sulla-aanhangers. Na Marius' dood keert Sulla terug als dictator.", pts:3},
    {q:"Noem vier bedreigingen waarmee Rome na Sulla te maken kreeg. (2pt)", a:"1) Zeerovers. 2) Koning Mithridates. 3) Slavenopstand (Spartacus). 4) Corrupte gouverneurs.", pts:2},
    {q:"Wat is een triumviraat? Noem de drie leden van het eerste triumviraat. (2pt)", a:"Bestuur door drie personen. Pompeius, Caesar en Crassus.", pts:2},
    {q:"Beschrijf de aanloop naar en afloop van de tweede burgeroorlog (Pompeius vs. Caesar). (3pt)", a:"Caesar verovert Gallië, wordt te machtig. Pompeius verklaart met steun senaat de oorlog. Caesar wint, wordt dictator voor het leven. In 44 v.C. vermoord.", pts:3},
    {q:"Beschrijf de derde burgeroorlog (Octavianus vs. Marcus Antonius). (3pt)", a:"Marcus Antonius sluit verbond met Cleopatra (Egypte). Senaat ziet dit als bedreiging. Octavianus verslaat hen bij Actium (31 v.C.). Beiden plegen zelfmoord. Egypte wordt Romeinse provincie. Keizerrijk begint.", pts:3},
    {q:"Waarom was de overgang van burgerleger naar beroepsleger zo belangrijk? (3pt)", a:"Voorheen: burgers met bezit vochten ter verdediging → wilden snel terug. Nu: bezitlozen vochten voor bezittingen → gehoorzaamden de generaal. Dit verschoof de macht van senaat naar legerleiders.", pts:3}
  ]},
  { title:"Les 22: Augustus, de eerste keizer", questions:[
    {q:"Welke twee titels kreeg Octavianus en wat betekenen ze? (2pt)", a:"Princeps (= eerste burger) en Augustus (= verhevene).", pts:2},
    {q:"Hoe hield Augustus de schijn op van een republiek terwijl hij alle macht had? (4pt)", a:"Alle instellingen bleven bestaan. Maar hij nam de belangrijkste functies: imperator (leger), volkstribuun (vetorecht), organisator festiviteiten. Hij behield onrustige + rijke provincies. De senaat hield enkel rustige provincies.", pts:4},
    {q:"Noem drie manieren waarop Augustus zijn populariteit versterkte. (3pt)", a:"1) Brood en geld uitdelen (dankzij Egyptisch graan). 2) Grote bouwwerken (werk voor proletariërs). 3) Gratis spelen (gladiatoren).", pts:3},
    {q:"Welke natuurlijke grenzen koos Augustus? Noem er minstens vier. (2pt)", a:"West/Zuid: Atlantische Oceaan, Sahara. Noord: Rijn, Donau. Oost: Eufraat. (+Zwarte Zee)", pts:2},
    {q:"Leg het verschil uit tussen de uitbreidingstactiek (vóór Augustus) en de verdedigingstactiek (vanaf Augustus). (3pt)", a:"Vóór Augustus: focus op verovering en uitbreiding. Vanaf Augustus: focus op verdedigen en beschermen via legioenen aan grenzen, troepen in opstandige provincies, en een vloot op de Middellandse Zee.", pts:3},
    {q:"Wat is de Pax Romana? (2pt)", a:"De Romeinse Vrede: een lange periode van vrede en welvaart. Het Romeinse leger zorgt voor stabiliteit in het keizerrijk.", pts:2},
    {q:"Hoe werd Augustus' opvolgingsprobleem opgelost? (2pt)", a:"Al zijn mannelijke opvolgers stierven jong. Hij adopteerde twee zonen van zijn derde vrouw. Tiberius volgde hem op na zijn dood in 14 n.C.", pts:2},
    {q:"Wat betekent autocratie? (2pt)", a:"Alleenheerschappij. Eén persoon (Augustus) bezit alle macht, hoewel de instellingen van de republiek schijnbaar bleven bestaan.", pts:2}
  ]},
  { title:"Les 23+25: Bloei & verval", questions:[
    {q:"Noem twee kenmerken van de eerste keizers na Augustus (14-68 n.C.). (2pt)", a:"1) Allemaal familie van elkaar. 2) Geen goede leiders (Caligula en Nero waren bloeddorstig/gestoord).", pts:2},
    {q:"Welk bouwwerk lieten de Flaviërs bouwen en waarom? (2pt)", a:"Het Colosseum, ter nagedachtenis van hun overwinningen.", pts:2},
    {q:"Leg het adoptiekeizerssysteem uit. (2pt)", a:"De regerende keizer zoekt een bekwame opvolger en adopteert die, zodat de meest geschikte persoon (niet per se familie) opvolgt.", pts:2},
    {q:"Noem twee belangrijke verwezenlijkingen van keizer Hadrianus. (2pt)", a:"1) Liet de limes (grenzen) versterken (Muur van Hadrianus). 2) Stopte de veroveringen en gaf gebieden terug → Pax Romana.", pts:2},
    {q:"Beschrijf de crisis van de 3e eeuw (soldatenkeizers). Noem oorzaken en gevolgen. (4pt)", a:"Generaals grijpen de macht → keizers volgen snel op. Ze beloven soldaten meer geld → hogere belastingen. Grenzen onbeschermd → invallen. Gevolgen: handel ontregeld, landbouw daalt, bevolking daalt, gebieden willen zich afscheiden.", pts:4},
    {q:"Welke hervormingen voerde Diocletianus door? (3pt)", a:"1) Ontnam de senaat het laatste restje macht (keizer = enige machthebber, vereerd als god). 2) Splitste het rijk in Oost en West. 3) Voerde de Tetrarchie in (4 heersers: 2 keizers + 2 medekeizers).", pts:3},
    {q:"Noem twee verwezenlijkingen van Constantijn. (2pt)", a:"1) Godsdienstvrijheid voor de christenen. 2) Nieuwe hoofdstad: Constantinopel (voorheen Byzantium).", pts:2},
    {q:"Wanneer en door wie werd het R.R. definitief gesplitst? Wanneer vielen de twee delen? (3pt)", a:"395 n.C. door keizer Theodosius. West-Romeinse Rijk valt in 476 n.C. Oost-Romeinse Rijk valt in 1453.", pts:3}
  ]}
];

// ======================== STATE ========================
let currentModule = null;
let currentTopic = -1;
let score = 0;
let total = 0;
let timerOn = false;
let timerInterval = null;
let timerSeconds = 0;

// ======================== NAV ========================
function showModule(mod) {
  currentModule = mod;
  currentTopic = -1;
  document.querySelectorAll('.section').forEach(s => s.classList.remove('visible'));
  document.getElementById('mod-' + mod).classList.add('visible');
  document.querySelectorAll('#moduleNav .nav-btn').forEach((b,i) => {
    b.classList.toggle('active', ['cours','exercices','examen','correctif'][i] === mod);
  });
  document.getElementById('topicNav').style.display = 'flex';
  document.querySelectorAll('.topic-btn').forEach(b => b.classList.remove('active'));
  // hide all topic contents
  document.querySelectorAll('.topic-content').forEach(tc => tc.style.display='none');
  if(mod === 'examen') buildExamenButtons();
  if(mod === 'correctif') buildCorrectifButtons();
  updateProgress();
}

function showTopic(idx) {
  currentTopic = idx;
  document.querySelectorAll('.topic-btn').forEach((b,i) => b.classList.toggle('active', i===idx));
  if(currentModule === 'cours') {
    document.querySelectorAll('#mod-cours .topic-content').forEach(tc => {
      tc.style.display = tc.dataset.topic == idx ? 'block' : 'none';
    });
  } else if(currentModule === 'exercices') {
    score = 0; total = 0;
    renderExercises(idx);
  } else if(currentModule === 'examen') {
    renderExamPreview(idx);
  } else if(currentModule === 'correctif') {
    renderCorrectifPreview(idx);
  }
  updateProgress();
}

function updateProgress() {
  const pb = document.getElementById('progressBar');
  if(currentTopic < 0) { pb.textContent = "Kies een topic om te starten"; return; }
  let modName = {cours:"Cursus",exercices:"Oefeningen",examen:"Examen",correctif:"Correctiesleutel"}[currentModule]||"";
  pb.textContent = `${modName} — Topic ${currentTopic+1}/7: ${TOPICS[currentTopic]}`;
  if(currentModule === 'exercices') pb.textContent += ` — Score: ${score}/${total}`;
}

// ======================== EXERCISES ========================
function renderExercises(topicIdx) {
  const area = document.getElementById('exerciseArea');
  const qs = shuffle([...EXERCISES[topicIdx]]);
  score = 0; total = qs.length;
  document.getElementById('scoreBar').textContent = `Score: 0/${total} — ${TOPICS[topicIdx]}`;
  let html = '';
  qs.forEach((q, i) => {
    html += `<div class="q-block" id="qb${i}">`;
    html += `<p>Vraag ${i+1}/${total}: ${q.q}</p>`;
    if(q.type === 'mcq') {
      const shuffledOpts = q.opts.map((o,oi) => ({text:o, origIdx:oi}));
      // keep order for simplicity, randomization is at question level
      shuffledOpts.forEach((o, oi) => {
        html += `<label><input type="radio" name="q${i}" value="${o.origIdx}"> ${o.text}</label>`;
      });
      html += `<button class="check-btn" onclick="checkMCQ(${i},${q.ans})">Controleer</button>`;
    } else if(q.type === 'tf') {
      html += `<label><input type="radio" name="q${i}" value="true"> Waar</label>`;
      html += `<label><input type="radio" name="q${i}" value="false"> Onwaar</label>`;
      html += `<button class="check-btn" onclick="checkTF(${i},${q.ans})">Controleer</button>`;
    } else if(q.type === 'fill') {
      html += `<input type="text" id="fi${i}" placeholder="Typ je antwoord…">`;
      html += `<button class="check-btn" onclick="checkFill(${i},'${q.ans.toLowerCase()}')">Controleer</button>`;
    }
    html += `<div class="feedback" id="fb${i}" data-expl="${q.expl}"></div>`;
    html += `</div>`;
  });
  area.innerHTML = html;
  resetTimer();
}

function showFeedback(idx, correct, expl) {
  const fb = document.getElementById('fb'+idx);
  fb.className = 'feedback ' + (correct ? 'correct' : 'wrong');
  fb.textContent = correct ? '✓ Juist! ' + expl : '✗ Fout. ' + expl;
  if(correct) score++;
  document.getElementById('scoreBar').textContent = `Score: ${score}/${total} — ${TOPICS[currentTopic]}`;
  updateProgress();
  // disable inputs
  const block = document.getElementById('qb'+idx);
  block.querySelectorAll('input, button.check-btn').forEach(el => el.disabled = true);
}

function checkMCQ(idx, correctIdx) {
  const sel = document.querySelector(`input[name="q${idx}"]:checked`);
  if(!sel) return;
  const expl = document.getElementById('fb'+idx).dataset.expl;
  showFeedback(idx, parseInt(sel.value) === correctIdx, expl);
}

function checkTF(idx, correctVal) {
  const sel = document.querySelector(`input[name="q${idx}"]:checked`);
  if(!sel) return;
  const expl = document.getElementById('fb'+idx).dataset.expl;
  showFeedback(idx, (sel.value === 'true') === correctVal, expl);
}

function checkFill(idx, correctAns) {
  const val = document.getElementById('fi'+idx).value.trim().toLowerCase();
  const expl = document.getElementById('fb'+idx).dataset.expl;
  // flexible matching
  const correct = val.length > 0 && (correctAns.includes(val) || val.includes(correctAns) || levenshtein(val, correctAns) <= 2);
  showFeedback(idx, correct, expl);
}

function levenshtein(a,b) {
  const m = a.length, n = b.length;
  const d = Array.from({length:m+1}, (_,i) => Array.from({length:n+1}, (_,j) => i||j));
  for(let i=1;i<=m;i++) for(let j=1;j<=n;j++)
    d[i][j] = Math.min(d[i-1][j]+1, d[i][j-1]+1, d[i-1][j-1]+(a[i-1]!==b[j-1]?1:0));
  return d[m][n];
}

function shuffle(arr) {
  for(let i=arr.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[arr[i],arr[j]]=[arr[j],arr[i]];}
  return arr;
}

// TIMER
function toggleTimer() {
  timerOn = document.getElementById('timerToggle').checked;
  if(timerOn) startTimer(); else stopTimer();
}
function startTimer() {
  if(timerInterval) return;
  timerInterval = setInterval(() => {
    timerSeconds++;
    const m = String(Math.floor(timerSeconds/60)).padStart(2,'0');
    const s = String(timerSeconds%60).padStart(2,'0');
    document.getElementById('timerDisplay').textContent = m+':'+s;
  }, 1000);
}
function stopTimer() { clearInterval(timerInterval); timerInterval=null; }
function resetTimer() { stopTimer(); timerSeconds=0; document.getElementById('timerDisplay').textContent='00:00'; if(timerOn) startTimer(); }

// ======================== EXAMEN (printable HTML) ========================
function buildExamenButtons() {
  let html = '';
  TOPICS.forEach((t,i) => {
    html += `<button class="dl-btn" onclick="showTopic(${i})">${t}</button> `;
  });
  document.getElementById('examenButtons').innerHTML = html;
}

function renderExamPreview(idx) {
  const exam = EXAMS[idx];
  let totalPts = exam.questions.reduce((s,q) => s+q.pts, 0);
  let html = `<div class="card">
    <h2>Examen: ${exam.title}</h2>
    <p><strong>Naam:</strong> ______________________ <strong>Datum:</strong> ________ <strong>Klas:</strong> ________</p>
    <p><strong>Totaal: /20</strong> (${totalPts} punten verdeeld over ${exam.questions.length} vragen)</p>
    <hr style="margin:12px 0;">`;
  exam.questions.forEach((q,i) => {
    html += `<p><strong>Vraag ${i+1}</strong> ${q.q}</p>`;
    html += `<div style="border-bottom:1px dotted #999; min-height:${Math.max(60, q.pts*30)}px; margin:8px 0 16px;"></div>`;
  });
  html += `<p style="margin-top:16px;"><button class="dl-btn" onclick="printExam(${idx})">🖨️ Afdrukken / PDF opslaan</button></p>`;
  html += `</div>`;
  document.getElementById('examenPreview').innerHTML = html;
}

function printExam(idx) {
  const exam = EXAMS[idx];
  let totalPts = exam.questions.reduce((s,q) => s+q.pts, 0);
  let w = window.open('','','width=800,height=600');
  let html = `<!DOCTYPE html><html><head><meta charset="UTF-8"><title>Examen ${exam.title}</title>
  <style>
    body{font-family:'Segoe UI',Arial,sans-serif;font-size:14px;line-height:1.5;padding:20px 30px;color:#1e1e1e;}
    h1{font-size:1.4em;margin-bottom:4px;}
    .header{border-bottom:2px solid #333;padding-bottom:8px;margin-bottom:16px;}
    .q{margin-bottom:20px;}
    .q p{margin:0 0 4px;}
    .answer-space{border-bottom:1px dotted #999;min-height:60px;margin:4px 0 8px;}
    .pts{float:right;color:#666;font-size:0.9em;}
    @media print{body{padding:10px 20px;}}
  </style></head><body>
  <div class="header">
    <h1>Examen: ${exam.title}</h1>
    <p><strong>Naam:</strong> ______________________________ <strong>Datum:</strong> ____________ <strong>Klas:</strong> ________</p>
    <p><strong>Totaal: ______ /20</strong></p>
  </div>`;
  exam.questions.forEach((q,i) => {
    html += `<div class="q"><p><strong>Vraag ${i+1}.</strong> ${q.q} <span class="pts">${q.pts}pt</span></p>`;
    const lines = Math.max(3, q.pts * 2);
    for(let l=0;l<lines;l++) html += `<div class="answer-space"></div>`;
    html += `</div>`;
  });
  html += `</body></html>`;
  w.document.write(html);
  w.document.close();
  w.focus();
  setTimeout(() => w.print(), 500);
}

// ======================== CORRECTIF ========================
function buildCorrectifButtons() {
  let html = '';
  TOPICS.forEach((t,i) => {
    html += `<button class="dl-btn" onclick="showTopic(${i})">${t}</button> `;
  });
  document.getElementById('correctifButtons').innerHTML = html;
}

function renderCorrectifPreview(idx) {
  const exam = EXAMS[idx];
  let html = `<div class="card">
    <h2>Correctiesleutel: ${exam.title}</h2>
    <p><strong>Totaal: /20</strong></p>
    <hr style="margin:12px 0;">`;
  exam.questions.forEach((q,i) => {
    html += `<div style="margin-bottom:16px; padding:10px; background:#f8f8f0; border-radius:6px;">`;
    html += `<p><strong>Vraag ${i+1}</strong> (${q.pts} pt): ${q.q}</p>`;
    html += `<p style="color:#2e7d32;"><strong>Antwoord:</strong> ${q.a}</p>`;
    html += `<p style="color:#666; font-size:0.9em;"><em>Puntenverdeling: ${q.pts} punt(en). Deelpunten mogelijk bij gedeeltelijk correct antwoord.</em></p>`;
    html += `</div>`;
  });
  html += `<p style="margin-top:16px;"><button class="dl-btn" onclick="printCorrectif(${idx})">🖨️ Afdrukken / PDF opslaan</button></p>`;
  html += `</div>`;
  document.getElementById('correctifPreview').innerHTML = html;
}

function printCorrectif(idx) {
  const exam = EXAMS[idx];
  let w = window.open('','','width=800,height=600');
  let html = `<!DOCTYPE html><html><head><meta charset="UTF-8"><title>Correctiesleutel ${exam.title}</title>
  <style>
    body{font-family:'Segoe UI',Arial,sans-serif;font-size:13px;line-height:1.5;padding:20px 30px;color:#1e1e1e;}
    h1{font-size:1.3em;margin-bottom:4px;}
    .q{margin-bottom:14px;padding:8px;background:#f8f8f0;border-radius:4px;}
    .q p{margin:0 0 4px;}
    .ans{color:#2e7d32;font-weight:600;}
    @media print{body{padding:10px 20px;}}
  </style></head><body>
  <h1>Correctiesleutel: ${exam.title}</h1>
  <p><strong>Totaal: /20</strong></p><hr>`;
  exam.questions.forEach((q,i) => {
    html += `<div class="q"><p><strong>V${i+1}</strong> (${q.pts}pt): ${q.q}</p>`;
    html += `<p class="ans">→ ${q.a}</p>`;
    html += `<p style="color:#666;font-size:0.85em;">Deelpunten mogelijk.</p></div>`;
  });
  html += `</body></html>`;
  w.document.write(html);
  w.document.close();
  w.focus();
  setTimeout(() => w.print(), 500);
}

// ======================== INIT ========================
document.addEventListener('DOMContentLoaded', () => {
  // nothing to init
});
</script>
</body>
</html>
