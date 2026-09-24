# Spreeknotities — Van vrachtschip naar containers

*Volgorde exact gelijk aan presentatie.html. Elke sectie = één dia.*

---

**Dia 1 — Titel**
"Goedemiddag allemaal. Vandaag neem ik jullie mee in waar we met onze software naartoe bouwen: van één groot geheel, naar losse, moderne containers."

---

**Dia 2 — Waar we vandaan komen**
"Onze huidige applicaties, deels geschreven in VB.NET, doen al jarenlang goed hun werk. Maar ze zijn opgeleverd als één groot geheel — alles zit aan elkaar vast. Een kleine aanpassing op de ene plek kan zomaar het hele systeem raken. En bij uitrol bouwen we in feite één enorm vrachtschip, vol met alles aan boord. Voor elke nieuwe klant moeten we dat schip opnieuw beladen: alle instellingen handmatig verzamelen en inregelen. Dat kost tijd."

---

**Dia 3 — Waar we naartoe bouwen**
"In de nieuwe opzet bouwen we onze containers als vaste, herbruikbare sjablonen. Precies één keer gebouwd, goed getest. Die sjablonen kopiëren of klonen we simpelweg voor elke klant. Klantspecifieke instellingen bakken we niet meer in, maar voeren we van buitenaf in. Resultaat: snellere uitrol, minder handwerk, eenvoudiger onderhoud."

---

**Dia 4 — De spelers in dit verhaal**
"Laat ik de belangrijkste spelers even introduceren. Unit4 CODA is het externe pakhuis waar onze financiële gegevens liggen. Tot nu toe hadden we daar een vaste kade-lijn naartoe, die om diverse redenen binnenkort verbroken wordt. Onze Blazor-website is het loket waar iedereen mee werkt. De Sync Engine is onze eigen vrachtwagen, die zelf de gegevens ophaalt zodra die lijn wegvalt. In totaal hebben we 12 containers: 10 met verwerkings-engines, 1 met de Blazor FrontEnd, en 1 met de Bank Statement API. Twee engines zijn al vervangen: BSPM Read Engine en Filter Engine. Calculate Match Engine volgt binnenkort."

---

**Dia 5 — Elke container is een klein fabriekje**
"Elke container is niet zomaar een doos — er zit een klein fabriekje in. Dat fabriekje doet één ding, en doet dat goed. Maar de fabriekjes praten niet rechtstreeks met elkaar. Ze zetten hun halffabricaat neer in een groot magazijn — de Crescendo database. Daar ligt het klaar totdat het volgende fabriekje het oppikt, ermee verder werkt, en het resultaat weer terugzet in het magazijn."

---

**Dia 6 — Zo ziet het eruit (architectuur)**
"Hier zie je het geheel bij elkaar. Links de Bank Statement API, de Blazor FrontEnd en de Sync-engine. In het midden ons magazijn, de Crescendo database. Rechts onze reeks engines, waarvan de eerste twee al vernieuwd zijn. Drie dingen wil ik hier benadrukken: één, alles praat via dat ene gedeelde magazijn — geen directe koppelingen onderling, dat maakt vervanging veilig. Twee, we vervangen engines één voor één; omdat alles via dezelfde database loopt, kunnen oud en nieuw gewoon naast elkaar draaien. Drie, we hoeven niet meer live in CODA te graven — dat scheelde vroeger performance, nu staat alles lokaal klaar dankzij Sync."

---

**Dia 7 — Waarom de Sync Engine?**
"Vroeger haalden we gegevens live op uit de externe CODA-database, via een vaste lijn, met joins tussen interne en externe data. Dat kan traag zijn en is afhankelijk van het netwerk. Nu houden we een eigen, lokale kopie van de benodigde gegevens bij, netjes gesynchroniseerd, en klaar voor als die lijn ooit wegvalt. Dat maakt ons sneller, overzichtelijker en stabieler."

---

**Dia 8 — Even kijken: oud vs. nieuw (intro)**
"Genoeg over de techniek — laten we een aantal schermen bekijken. Steeds eerst het oude scherm, en dan meteen hetzelfde scherm in de nieuwe applicatie."

---

**Dia's 9-20 — Screenshot-vergelijkingen (oud/nieuw paren)**
*Per paar (bijv. Navigatie, Bank Statement Masters, Filter Rules overzicht/detail, Selector Masters): "Dit is het oude scherm voor [naam]. En dit... is hetzelfde scherm in de nieuwe applicatie." (Laat de wipe-overgang het werk doen — even stil zijn tijdens de animatie versterkt het effect.)*

---

**Dia — En er is meer (extra's intro)**
"Naast een moderne uitstraling heeft de nieuwe website ook een paar praktische extra's, die het dagelijks gebruik prettiger maken."

---

**Dia — Dark mode**
"Bijvoorbeeld dark mode — met één klik te wisselen, fijn voor wie lange dagen achter het scherm zit."

---

**Dia's — Inklapbaar menu (2x)**
"Het menu is ook inklapbaar, zodat je meer ruimte krijgt voor je werk. En kijk, dat gaat met een mooie, vloeiende animatie."

---

**Dia — Bewerken via een popup**
"En bewerken kan nu via een overzichtelijke popup, zonder dat je de pagina hoeft te verlaten."

---

**Dia — Hoe weten we dat het schip goed de zee op kan?**
"Nu we het toch over schepen hebben: hoe weten we eigenlijk dat dit allemaal goed werkt? Op een scheepswerf wacht je niet tot de proefvaart om te zien of alles klopt. Er wordt op drie niveaus gekeurd, van klein onderdeel tot complete proefvaart."

---

**Dia — Onze drie soorten tests**
"Denk aan een luik op een schip. Een Unit Test controleert precies zo'n enkel luik: gaat het goed open en dicht, en is het — eenmaal dicht — ook echt waterdicht? Een Integration Test kijkt of zo'n luik goed samenwerkt met het compartiment erachter. En een Scenario Test is de complete proefvaart: het hele schip de zee op, precies zoals het straks bij de klant gebeurt."

---

**Dia — Geautomatiseerd, in kleine stappen**
"Onze tests zijn zoveel mogelijk geautomatiseerd, en gaan vanzelf af zodra we een stukje software opleveren. We werken in kleine, incrementele stapjes — geen grote big-bang releases. En elke wijziging wordt bekeken door minimaal één andere developer, ook vanuit onze SOC1-verplichtingen. Dat vier-ogen-principe, samen met geautomatiseerde tests, is onze eerste verdedigingslinie."

---

**Dia — Een solide basis voor de toekomst**
"Deze automatisering verhoogt de betrouwbaarheid van alles wat we nu toevoegen, en legt een solide fundament voor later. Zodra alle engines zijn omgezet, volgt er een grote refactor-slag, en dan vangen die tests onbedoelde bijeffecten op. We maken soms, omwille van tijd en doorloop, keuzes waar we later op terugkomen — ook als het straks echt in productie draait. Ons eerste doel is: alles kunnen wat de oude engines ook konden, tenzij iets écht overbodig is of heel klantspecifiek. Altijd met backward compatibility in gedachten, en de oude engines één voor één vervangen."

---

**Dia — Automatisch vs. handmatig testen**
"Automatisch testen verlaagt de tijd die we kwijt zijn aan handmatig testen — dat hoeft nu minder vaak. Maar het is nog geen vervanging: veel kennis zit nog in de hoofden van mensen, en niet alles is al geautomatiseerd. En het schrijven van betrouwbare tests kost ook tijd — tijd die een developer dan niet aan nieuwe features besteedt. Het is een bewuste balans, geen wondermiddel."

---

**Dia — Wat betekent dit voor ons?**
"Wat betekent dit nu voor ons, hier in dit gebouw?

Voor Sales en Management: developers hoeven zich niet meer bezig te houden met onderhoud van oude, verweven onderdelen. Er kan gericht verbeterd worden in één specifiek onderdeel, zonder de rest te raken. Het doorknippen van de vaste lijn met Unit4 CODA maakt ons ook minder afhankelijk van een andere partij. En dat geeft een voorspelbaardere roadmap — een verbetering voor bijvoorbeeld de Filter Engine hoeft niet meer te wachten op de rest van het systeem. Wel een disclaimer: het verwerken van data via Sync geeft op zichzelf weer andere uitdagingen, en de communicatie naar Unit4 heeft momenteel bekende performance issues.

Voor de functioneel consultants: het is een moderne webapplicatie, met minder klikken en overzichtelijkere schermen. We houden minder star vast aan het originele ontwerp van Unit4. En ook jullie eindgebruikers zullen dit prettiger vinden — het ziet er frisser en moderner uit, en sluit beter aan bij wat ze van andere apps in het dagelijks leven gewend zijn.

Voor technisch applicatiebeheer: nu duurt het samenstellen van een klant-omgeving lang, vergelijkbaar met het opnieuw beladen van een heel vrachtschip. Straks kopiëren of klonen we onze set containers als vaste sjablonen, met instellingen die van buitenaf worden ingevoerd. Dat geeft veel kortere doorlooptijden — en meer ruimte om je te richten op waarde toevoegen bij de klant.

En voor techniek en developers: kleiner en modulair betekent sneller ontwikkelen, met minder gedoe. Bij een probleem is meteen duidelijk in welke container het misgaat — veel minder zoekwerk. Aanpassingen zijn te doen zonder dat iets anders omvalt. En in combinatie met geautomatiseerde tests weten we sneller of alles nog werkt."

---

**Dia — Afsluiting (teamfoto's)**
"Ik wil afsluiten met een bedankje. Deze nieuwe applicaties zijn mede mogelijk gemaakt door dit team: Collin, Louis, Nick, en ikzelf, Pascal. Bedankt voor jullie aandacht!"

---

*Tip: gebruik links = volgende dia, rechts = vorige dia (muisklik), of de pijltjestoetsen op je toetsenbord.*