# Project Analyse 

Net zoals bij Smart Systems werken we met een probleemstelling. Voor Internet
of Things is deze breder gedefinieerd. Voor een geslaagd project moet je de
scope van de probleemstelling gaan verkleinen naar een haalbaar project. Dit
gebeurt in het volgend stuk. Dit proces is essentieel voor een geslaagd project
en hierdoor is de analyse kritieker dan bij Smart Systems. Ga hier niet te licht
over!  

Hieronder beschrijven jullie de probleemstelling dat tijdens IoT  word
behandelt. Voor dit probleem stellen jullie een oplossing voor in de analyse .


De problemen die opgelost worden tijdens het vak Internet of Things hebben
meestal als oplossing een Smart Objects gecombineerd met ondersteunende back
-en frontend. Deze componenten worden in de project analyse gedefinieerd. 

## Probleemstelling 

Voor deze sectie van de analyse beschrijf je het hoofdprobleem in maximaal 2
tot 5 zinnen. Daarna deel je het probleem op in minimum 10 delen (Als bulletpoints).    

## Analyse

### Abstract

In het abstract wordt het voorstel tot oplossing beknopt beschreven. Voor dit
te doen schrijf je een korte tekst van min 250 woorden en max 500 woorden. Dit
komt neer op halve tot een volle bladzijde. Je ondersteund dit met een diagram
van de algemene architectuur.

<img style="display:block; margin: auto;" src="../../img/lorawan_architecture.jpg" alt="">
<p style="text-align: center; font-weight: bold"> Voorbeeld: het diagram van de algemene architectuur van LoRaWAN. </p>


### Smart Object (Hardware Analyse)

IoT is een hardware project. De focus ligt op het ontwikkelen van een fysiek
object. Dit object krijgt prioriteit tijdens dit vak, niet de front end of back
end die nodig is voor een volwaardige oplossing. De tijd is beperkt dus word er
een focus gelegd. Dit object uit zich in een Smart Object. Een Smart Object kan
beschreven worden aan de hand van de 4 volgende criteria. 

1. Monitoring
2. Controle
3. Optimalisatie
4. Autonomie

De criteria zijn geordend volgens stijgende complexiteit. Monitoring is
eenvoudiger dan een object volledig autonoom te maken. Hierdoor kan je de
criteria ook gebruiken als leidraad doorheen het iteratief proces dat we
gebruiken in IoT. Als je prototype ontwikkelt zorg er eerst voor dat het al
data kan verzamelen vooraleer dat het volledig autonoom is.

Aan de hand van bovenstaand criteria wordt er een of meerdere Smart Objects
gedefinieerd die een oplossing bied voor de probleemstelling in het project. Om
een geslaagd project moet er meerdere werkende Smart Objects zijn. Dit mogen
meerdere van hetzelfde type zijn of verschillende soorten objecten. Zo
vervolledigen jullie het Things gedeelte van IoT. Je moet nog al het
achterliggende voorzien om deze met Smart Objects met elkaar te laten spreken.

Een Smart Object is niet van nature uit een extensie van een bestaand product.
Het is ook een object dat toegevoegd kan worden aan een bestaand proces.  Jaar
op jaar worden op de akker groenten geteeld. Hoe kunnen we deze akker slim
maken? Het is geen fysiek stuk hardware waar we iets aan kunnen toevoegen. Er
kan wel een Smart Object gebouwd worden dat het landbouw proces optimaliseert. 

Beschrijf in dit deel de nodige Smart Objects voor jullie project. Naast de
beschrijving voorzie ook het volgende: 

* Blokdiagram 
* Specificaties
* Argumentatie
* Elektrisch schema
* State diagram
* Flowchart

Hieronder kan je een voorbeeld vinden van elk diagram.


#### Blokdiagram

In het blokdiagram deel je het hardware probleem op in grote delen en kan je zien hoedat ze met elkaar gelinkt zijn.

<img style="display:block; margin: auto;" src="../../img/basic_block.png" alt="">
<p style="text-align: center; font-weight: bold"> Voorbeeld: Blok diagram </p>


#### Specificaties
Voor elke blok in het blok diagram van een Smart Object stel je de
specificaties en/of elektrische karakteristieken op. Deze worden in het
volgende formaat meegeven in de analyse.

| Blok           | Specificatie    | Min  | Nominaal | Max    |
| --             | --              | --   | --       | --     |
| Motor Power    | Werkspanning    | 7V   | 7.2V     | 7.V    |
| (Loodbatterij) | Stroom          |      | 500mA    | 2A     |
|                | Capaciteit      |      | 2700mAh  | &nbsp; |
| ATmega328p     | F<sub>cpu</sub> |      | 16 MHz   |        |
|                | Werkspanning    | 4.8V | 5V       | 5.2V   |
 

#### Onderliggende argumentatie 
Voor elk blok van het blokdiagram moet je ook een argumentatie geven waarom deze gebruikt wordt in
de voorgestelde oplossing in de analyse. Geef ook mogelijke alternatieven. Geef
deze informatie in het volgend formaat: 

| Blok            | Argumentatie                                                                                                                                                                                                                                   | Alternatieven           |
| --              | --                                                                                                                                                                                                                                             | --                      |
| Motor Power     | De loodbatterij is oplaadbaar en levert de correcte spanning voor de motorsturing. De LiPo batterij is een betere oplossing vooral door gewicht en beter behoud van capaciteit. De loodbatterij was beschikbaar en moest niet aangkocht worden | LiPo, Powerbank         |
| Wireless Driver | We maken gebruik van een nRF24L01 omdat de simpelste manier van communicatie is, geen protocol en een simpele communicatie voorziet.                                                                                                           | Bluetooth, ZigBee, WiFi |


#### Elektrisch schema   

<img style="display:block; margin: auto;" src="../../img/example_schematic.png" alt="">
<p style="text-align: center; font-weight: bold"> Voorbeeld: Elektrisch schema </p>


### Software analyse

Om onze software te analyseren is een top down methodologie aangeraden. Eerst
moeten we zien wat onze datastromen zijn. Welke data word er genereerd in het
systeem, wat voor data kunnen we injecteren voor het systeem. Deze vraag is
cruciaal om parallel in team te kunnen werken. Dit moet in het begin bepaald
worden zodat je als individu aan aparte blok kunt werken van het systeem.

Als je bepaalt hebt wat voor data er in en uit een specifieke blok van het
systeem komt, moet je ook nog bepalen in welk formaat dit gebeurt. Om dit
succesvol te doen moet er ook rekening gehouden worden met de hardware
restricties. JSON versturen over I²C met een Arduino is gedoemd om  te falen.

Voor de starten geef je aan welke data er in en/of uit een specifieke blok komt
van de hardware analyse. We geven dit weer in het volgend formaat: 

#### Data in / Out

| Blok         | Data In                               | Data Uit                              |
| --           | --                                    | --                                    |
| Motor Driver | 2x PWM Signaal                        | N.V.T.                                |
| ATMega328P   | Configuratie instellingen, Sensordata | Configuratie instellingen, Sensordata |

Bij de ATMega328p zien we dat de data uit gelijk is aan de data in. Hieruit
kunnen we afleiden dan we data van ons systeem remote kunnen opvragen via de
Wireless Driver. Deze functionaliteit moet in elk project zitten.

**Maak de oplijsting voor de in en uit data van de voorgestelde oplossing in
bovenstaand formaat en voeg deze toe aan de analyse**

De machine die als mogelijke oplossing word aangebodendat we aanbieden kan in
zich in verschillende states vinden en kan transitioneren tussen verschillende
states. Om de embedded code in het project eenvoudig te kunnen debugen moeten
we weten in welke state de code zicht bevindt. Om deze states te defineren
maken we gebruik van een state diagram. Een voorbeeld hiervan kan je hieronder
terugvinden. 

<img style="display:block; margin: auto;" src="./deliverables/img/state_diagram.png" alt="">

#### State diagram
**Voeg aan de analyse een state diagram toe van de voorgestelde oplossing**
*Een goed voorbeeld van een complexer state diagram kan je hier terugvinden:
![State Diagram nRF24L01](http://m8ta.com/images/470_1.png)*


#### Flowchart
Om te wisselen tussen de verschillende states moeten we de flow hiervan beschrijven in een flowchart 

<img style="display:block; margin: auto;" src="./deliverables/img/flow_chart.png" alt="">

**Voeg in de analyse voor elke state transition een flowchart. Verduidelijk de
nodige processen met flowchart waar nodig.**

*Op deze manier bouwen we onze software modulair. Dit is een vereiste doorheen
het project. Je werkt met meerde tijdens het project aan aparte blokken om dit
mogelijk te maken moeten de interface tusssen de aparte blokken gekend zijn.*

####  Mockup
Als er een grafische interface nodig, dienen hiervoor mock ups gemaakt worden.
<img style="display:block; margin: auto;" src="./deliverables/img/mockup.png" alt="">

**Als er mock ups nodig zijn voeg deze toe aan de analyse**

## Wat moet er allemaal in je analyse document

- Probleemstelling
- Abstract
- Smart Object (Hardware Analyse)
  - Hardware blokdiaram
  - Specificatie tabel
  - Argumentatie en alternatieven tabel
- Software analyse
  - Data In -en Outputs
  - State diagram
  - Flowchart
  - Mockup (Indien GUI) 

Het analyse document wordt in de documentatie repo geplaatst


