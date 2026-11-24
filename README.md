# Wenteltrap generator

Parametrische generator voor een stalen wenteltrap met eiken treden, met 3D-weergave in de browser,
toetsing van de trapafmetingen en export naar IFC.

## Gebruik

Open `index.html` in een browser. Er is geen installatie of build nodig. De pagina laadt three.js en de
lettertypen van een CDN, dus er is een internetverbinding nodig.

- **Parameters** (links): straal en binnenstraal van de treden, looplijn, verdiepingshoogte, aantal optreden,
  draaihoek, starthoek, draairichting, tredendikte, boomhoogtes en leuninghoogte.
- **Onderdelen**: stootborden, vloer boven (ook transparant), binnen- en buitenleuning en looplijn.
- **Zware tredendragers**: 0 tot 4 treden krijgen een koker 100x100x5 onder de tredendrager, van boom tot
  boom. De knop "Gunstigste plekken zoeken" kiest de treden waar dat de steunpunten van de buitenboom
  het meest ontlast; de tredenummers zijn daarna los aan te passen. Elke tredendrager heeft links en
  rechts een voetplaatje tegen de boom.
- **Kolom KK250/10**: positie ten opzichte van het hart van de trap en de dikte van de vloeropbouw. Boven de
  kolom zitten een plaat van 16 mm, een liggende HEA160 langs de vloerrand en een hoeklijn van 12 mm; de
  bovenkant van de kolom volgt uit de verdiepingshoogte.
- **Koppeling aan kolom**: kokers 200x100x5 haaks uit de kolomvlakken die naar de trap wijzen (bij een kolom
  in het trapgat zijn dat er twee), onder de treden door tot aan de buitenboom. De bovenkant ligt tegen de
  laagste trede op hun weg; waar een boom hoger ligt, vult een opstand het verschil. De onderste en de
  bovenste koker zijn los aan en uit te zetten.
- **Aanzichten**: 3D, bovenaanzicht en vooraanzicht.
- **Standaardwaarden herstellen** zet alle parameters terug.
- **IFC-export**, steeds als IFC4 en zonder de vloer:
  - *IFC compleet*: de trap met de kolom, de HEA160 en de hoeklijn onder de vloer.
  - *IFC alleen trap*: de trap zonder het bestaande staal (kolom, HEA160 en hoeklijn onder de vloer).
  - *IFC draadmodel trap*: de systeemlijnen van de trap uit het rekenmodel als IFC-analysemodel
    (IfcStructuralAnalysisModel), met profielen en steunpunten: voetplaten en hoeklijn scharnierend,
    de aansluiting van de koker op de kolom ingeklemd.
  - *DXF draadmodel trap*: dezelfde systeemlijnen als 3D-lijnen in DXF (R12, mm), met een laag per
    onderdeel en de steunpunten als punten. Bedoeld voor rekenpakketten die geen IFC-analysemodel inlezen.

## Uitgangspunten

- Trap rechtsom omhoog, 270 graden, de bovenste trede op vloerhoogte.
- Handregel buis 42,4 mm, balusters plat 60x12, binnen- en buitenboom van plaat 300x10,
  tredendragers van plaat 3 mm, eiken treden van 40 mm met een antislipstrook.
- Onderaan staan de bomen op voetplaten van 250x300x20 op de constructievloer; bovenaan zitten ze vast
  aan een hoeklijn L100x100x10 langs de vloerrand, op de kanaalplaatvloer.
- Standaard: treden R = 1500 mm, binnenstraal 400 mm, looplijn 400 mm uit de binnenzijde,
  verdiepingshoogte 3750 mm, 18 optreden, leuninghoogte 1000 mm, vloeropbouw 330 mm
  (bovenkant kolom op 3240 mm).
- Standaard alleen de bovenste koker aan de kolom en geen zware tredendragers.

## Controle

De controlestrook toetst optrede, aantrede op de looplijn, afstand van de looplijn tot de zijkant, breedte,
vrije hoogte en traphoogte aan Bbl tabel 4.26 (nieuwbouw), naar keuze voor een woning, overige
gebruiksfuncties of een trap die uitsluitend voor ontvluchten dient.

De grenswaarden zijn overgenomen uit samenvattingen van de tabel, niet uit de officiele tekst.
Controleer ze op wetten.overheid.nl voordat je erop toetst.

## Belasting

Op het tabblad Belasting rekent de knop "Belasting berekenen" de krachten uit die de trap afgeeft aan de
voetplaten op de vloer beneden, de hoeklijn op de kanaalplaatvloer boven en elke koppeling aan de kolom.
De uitkomst wordt alleen bijgewerkt als je op de knop drukt; na een wijziging van de invoer staat ze als
verouderd gemarkeerd.

- Rekenmodel: lineair ruimtelijk raamwerk met de bomen, treden, kokers en kolom als staven.
- Voetplaten en hoeklijn liggen 70 mm onder het vloerpeil en zijn scharnierend; de kokers zitten star aan
  een plaat op de kolom en aan beide bomen.
- Elke koppeling heeft op de kolom een plaat van 250x300, zo breed als de kolom, met links en rechts een
  anker. De tabel geeft per koppeling de grootste trek en afschuiving per anker.
- Bij de tabel staat een schema: een plattegrond met de krachten op de vloeren en een aanzicht van de
  kolom met de krachten uit de koppelingen.
- Belasting: eigen gewicht en een veranderlijke belasting in kN/m2 op alle treden, in te vullen naar de
  gebruiksklasse. De uitkomsten zijn karakteristiek, zonder belastingfactoren.

## Beperkingen

- De belastingberekening is indicatief en vervangt de berekening van de constructeur niet. Sterkte en
  stijfheid van de onderdelen, de puntlast op een trede en de belasting op de leuning worden niet getoetst.
- De IFC-geometrie bestaat uit driehoeksvlakken. Het bestand is bedoeld voor coordinatie en visuele
  controle, niet als productiemodel.
