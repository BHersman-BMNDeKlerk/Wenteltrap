# Wenteltrap generator

Parametrische generator voor een stalen wenteltrap met eiken treden, met 3D-weergave in de browser,
toetsing van de trapafmetingen en export naar IFC.

## Gebruik

Open `index.html` in een browser. Er is geen installatie of build nodig. De pagina laadt three.js en de
lettertypen van een CDN, dus er is een internetverbinding nodig.

- **Parameters** (links): straal en binnenstraal van de treden, looplijn, verdiepingshoogte, aantal optreden,
  draaihoek, starthoek, draairichting, tredendikte, boomhoogtes en leuninghoogte.
- **Onderdelen**: stootborden, vloer boven, binnen- en buitenleuning, looplijn, kolom KK250/10 en de
  koppeling van de trap aan de kolom op drie punten.
- **Aanzichten**: 3D, bovenaanzicht en vooraanzicht.
- **Standaardwaarden herstellen** zet alle parameters terug.
- **IFC exporteren** slaat het model op als IFC4-bestand, zonder de vloer.

## Uitgangspunten

- Trap rechtsom omhoog, 270 graden, de bovenste trede op vloerhoogte.
- Handregel buis 42,4 mm, balusters plat 60x12, binnen- en buitenboom van plaat 300x10,
  tredendragers van plaat 3 mm, eiken treden van 54 mm met een antislipstrook.
- Standaard: treden R = 1500 mm, binnenstraal 400 mm, looplijn 400 mm uit de binnenzijde,
  verdiepingshoogte 3750 mm, 18 optreden, leuninghoogte 1000 mm.

## Controle

De controlestrook toetst optrede, aantrede op de looplijn, afstand van de looplijn tot de zijkant, breedte,
vrije hoogte en traphoogte aan Bbl tabel 4.26 (nieuwbouw), naar keuze voor een woning, overige
gebruiksfuncties of een trap die uitsluitend voor ontvluchten dient.

De grenswaarden zijn overgenomen uit samenvattingen van de tabel, niet uit de officiele tekst.
Controleer ze op wetten.overheid.nl voordat je erop toetst.

## Beperkingen

- De generator toetst alleen afmetingen. Sterkte en stijfheid van de trap, de koppelingen en de leuning
  worden niet berekend.
- De IFC-geometrie bestaat uit driehoeksvlakken. Het bestand is bedoeld voor coordinatie en visuele
  controle, niet als productiemodel.
