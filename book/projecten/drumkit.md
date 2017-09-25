# Drumkit

Dhr. Overdulve heeft voor zijn onderzoek een toestel nodig dat drumbewegingen
kan registeren. Zie onderstaande tekst voor meer informatie

Voor het onderzoek in automatische classificatie van drum events in
polyfonische muzieksignalen d.m.v. deep learning heb ik nood aan een
gigantische hoeveelheid geannoteerde trainingsdata. Normaal gezien worden
professionals ingehuurd om vanuit een muziekfragment manueel aan te geven
wanneer een bepaald instrument werd bespeeld; b.v. een snare drum, een hi-hat
cimbaal, enzovoorts. Niet alleen is dit een erg moeizaam proces, maar er is ook
een getraind oor nodig om dit op een voldoende accurate manier te doen. Daarom
heb ik nood aan een systeem dat het proces van annotaties automatiseert om als
het ware een heel accurate ground truth te bekomen dat ik nadien kan gebruiken
om machine learning algoritmen mee te trainen.

Concreet heb ik een systeem nodig dat bestaat uit sensoren die geplaatst worden
op de verschillende drumvellen en cimbalen op een drumkit. Deze sensoren moeten
registreren wanneer er contact is tussen een drum stok en het drumvel/de
cimbaal. Heel eenvoudig zou een accelerometer hier in kunnen volstaan om de
trillingen te registreren die resulteren uit een drum aanslag. Er zijn ook
commercieel beschikbare snare/bass drum triggers die dit al doen. Eventueel
kijken naar hun design/technologie zou helpen om de sensoren te ontwikkelen.
Tegelijkertijd moet het systeem via een microfoon de audio signalen capteren en
opslaan. De output van het systeem zou een gesynchroniseerde stream moeten zijn
van gecapteerde audio signalen en timestamps (en idealiter de hardheid) van
specifieke drum events, b.v. slag op snare drum, slag op cimbaal.

