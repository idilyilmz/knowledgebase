# Modelvalidatie

Auteur: Idil Yilmaz

## 1. Aanleiding en context

### 1.1 Waarom dit onderwerp?

Binnen het fashion-police project wordt een segmentatiemodel ingezet dat kledingklassen herkent op pixelniveau. De kwaliteit van dat model bepaalt direct hoe geloofwaardig de installatie overkomt bij bezoekers. Toch wordt die kwaliteit nergens automatisch gecontroleerd. Wanneer het model wordt aangepast of opnieuw getraind, is er geen geautomatiseerde check die signaleert of de prestaties zijn verslechterd.

Dit onderzoek richt zich op die gat: hoe kan modelkwaliteit structureel en automatisch worden gevalideerd als onderdeel van de bestaande CI/CD-pipeline?

### 1.2 Context van het project

Het fashion-police project is een groepsopdracht binnen de studio Responsible AI (HBO-ICT, HvA). De opdracht is om een AI-installatie te bouwen die HvA-studenten classificeert op basis van kledingkeuze. De installatie draait op een Raspberry Pi en maakt gebruik van een pipeline waarin YOLO personen detecteert en DeepLabV3 de kledingsegmentatie uitvoert. De volledige projectbeschrijving volgt in hoofdstuk 3.

### 1.3 Huidige situatie van de CI/CD-pipeline

Het project maakt gebruik van een GitLab CI/CD-pipeline die automatisch wordt geactiveerd bij elke codewijziging. De pipeline installeert dependencies via uv, voert tests uit via pytest en publiceert documentatie via MkDocs.

De pipeline controleert daarmee of de code correct werkt, maar niet of het segmentatiemodel nog betrouwbare voorspellingen doet. Een modelwijziging die de segmentatiekwaliteit verslechtert, komt door de huidige pipeline zonder waarschuwing.

### 1.4 Probleemstelling

Er is geen automatische validatie van de modelkwaliteit in de CI/CD-pipeline. Hierdoor kunnen regressies (situaties waarin een nieuw model slechter presteert dan het vorige) onopgemerkt blijven. Voor een project waarbij de geloofwaardigheid van de installatie direct afhangt van de segmentatiekwaliteit, is dit een concreet risico.

De vraag is daarom: hoe kan de kwaliteit van het segmentatiemodel automatisch worden gevalideerd als vaste stap in de GitLab CI/CD-pipeline?

## 2. Onderzoeksvraag en deelvragen

### 2.1 Hoofdvraag / onderzoeksvraag

Hoe kan de kwaliteit van segmentatiemodellen in het fashion-police project automatisch worden gevalideerd in de GitLab CI/CD-pipeline?

### 2.2 Deelvragen

*Analyse*

1. Wat is het fashion-police project?
2. Wat zijn segmentatiemodellen?
3. Wat is een CI/CD-pipeline?

*Advies*

4. Welk segmentatiemodel past het best bij het fashion-police project?

// overgeslagen voor nu 

*Ontwerpen*

5. Hoe ziet een automatische validatiestap in de GitLab CI/CD-pipeline eruit?

// overgeslagen voor nu 

*Realiseren*

6. Voldoet het huidige segmentatiemodel aan de vastgestelde kwaliteitseis?

### 2.3 Onderzoeksmethoden

Voor dit onderzoek zijn twee methoden ingezet. 
Voor deelvraag 1 is gebruikgemaakt van beschikbaar materiaal: projectdocumentatie, GitLab-issues en gesprekken binnen het team vormen de basis voor de beschrijving van het fashion-police project. 
Voor deelvragen 2, 3 en 4 is een literatuurstudie uitgevoerd aan de hand van wetenschappelijke publicaties, technische documentatie en vakinhoudelijke bronnen. 
De bronnen zijn geselecteerd op relevantie voor de projectcontext: semantische segmentatie op embedded hardware met beperkte trainingsdata.

## 3. Het fashion-police project 

### 3.1 Lectoraten en studiocontext 

Het fashion-police project is een groepsopdracht binnen de studio Responsible AI (HBO-ICT, HvA). Deze opdracht komt voort uit een samenwerking tussen twee HvA-lectoraten: Responsible IT en Fashion Research & Technology.

*Responsible IT* onderzoekt hoe digitale technologie op een verantwoorde en ethische bewuste manier ontwikkeld kan worden. *Fashion Research & Technologie* zich richt op de rol van data en technologie in de modeketen.

Yuri Westplat is een designer en onderzoeker bij Responsible IT en treedt op als opdrachtgever. 

### 3.2 Aanleiding

Er zijn veel meer AI-surveillancesystemen in openbare ruimtes. 
De aanleiding ligt precies hierin. 
Zulke systemen analyseren camerabeelden live en delen mensen automatisch in categorieën. 
Denk bijvoorbeeld aan gezichtsherkenning of gedragsanalyse. 
Dit zijn systemen die weinig menselijk ingrijpen vereisen en toezicht automatiseren. Hierdoor zijn ze aantrekkelijk voor overheden en bedrijven. 
Daarnaast is het vaak onduidelijk voor buitenstaanders welke aannames, fouten en vooroordelen er in deze modellen meespelen.

Het lectoraat Responsible IT ziet dit als een maatschappelijk vraagstuk dat om kritische reflectie vraagt. 
Niet alleen in theorie maar juist via praktische ervaring met de technologie zelf. 

Methodologisch volgt het project het principe van Critical Making. 
Dit betekent dat problematische technologie nagebouwd wordt om de verborgen aannames aan het licht te brengen. 
Daarnaast wordt in iedere iteratie getest met de doelgroep jongeren tot 23 jaar. 

### 3.3 Opdracht

De opdracht luidt: ontwerp en bouw een AI-installatie die HvA-studenten classificeert op basis van hun kledingkeuze. 
De uitdaging is om op basis van gedetecteerde kledingstukken te voorspellen van welke opleiding een student afkomstig is.

Er wordt verwacht dat de resulterende installatie interactief is. 
Daarnaast zal het survaillancesysteem op een speelse wijze inzichtelijk gemaakt moeten worden. 
Bezoekers moeten ervaren hoe data, modellen en ontwerpkeuze samen bepalen hoe mensen ongevraagd worden geclassificeerd en beoordeeld.

Het doel is niet een zo precies mogelijke voorspelling. 
Maar juist een zichtbare demonstratie van hoe subjectieve aannames in technische systemen worden gepresenteerd als objectieve feiten.

### 3.4 Technische invulling

De applicatie bestaat uit een backend die een getraind segmentatiemodel laadt en beschikbaar stelt aan een eenvoudige frontend. 
Wanneer een bezoeker voor de installatie staat, wordt een beeld vanuit een camera doorgestuurd naar het model. 
Het model bepaalt per pixel tot welke kledingklasse die behoort, en geeft het resultaat terug als een gekleurd masker over de oorspronkelijke afbeelding. 
Op die manier ziet de bezoeker letterlijk hoe het systeem zijn of haar kleding "leest". 
Het project bevat daarnaast functionaliteit om gezichten te vervagen voordat beelden worden getoond, om de privacy van bezoekers te beschermen.

Het segmentatiemodel zelf is een DeepLabV3-architectuur, getraind op negen vooraf gedefinieerde kledingklassen. 
De kwaliteit van dat model bepaalt direct hoe geloofwaardig de installatie overkomt: wanneer het masker grove fouten bevat, wordt de demonstratie van automatische classificatie ondergraven. 
Dit maakt modelkwaliteit niet alleen een technisch, maar ook een inhoudelijk vraagstuk binnen het project.

### 3.5 Conclusie: wat is het fashion-police project?

Het fashion-police project is een kritische AI-installatie die kledingsegmentatie inzet om HvA-studenten te classificeren op basis van kledingkeuze. 
De technische kern bestaat uit een YOLO-pose pipeline voor persoonsdetectie en DeepLabV3 voor kledingsegmentatie, draaiend op een Raspberry Pi. 
De kwaliteit van het segmentatiemodel is daarbij niet alleen een technisch vraagstuk: een slecht masker ondermijnt de inhoudelijke boodschap van de installatie. 
Dit maakt modelvalidatie relevant voor zowel de werking als de geloofwaardigheid van het systeem.

## 4. Segmentatiemodellen

### 4.1 Wat is beeldsegmentatie?

Wanneer we het over beeldsegmentatie hebben, hebben we het over een vorm van computer vision (CV) waarbij een afbeelding wordt opgedeeld in betekenisvolle regio's. 
Dat is niet zo bij classificatie, hierbij wordt één label aan een hele afbeelding gegeven. 
Ook bij object detectie, waarbij objecten wordt omsloten met een bounding box, kent segmentatie aan iedere afzonderlijke pixel een klasse toe. 
Het resultaat hiervan is een masker dat exact aangeeft welke pixels tot welk object of welke categorie behoren. [1]

Daarnaast kan segmentatie onderscheidt worden binnen drie varianten:
- Semantische segmentatie: Hierin wordt elke pixel toegewezen aan een klasse, zonder onderscheid te maken tussen meerdere objecten van dezelfde klasse. 
- Instance segmentatie: Hier wordt de onderscheid wel gemaakt, hij kan bijvoorbeeld twee aparte truien naast elkaar herkennen als twee verschillende instanties. 
- Panoptic segmentatie: Hierin wordt *semantische* en *instance segmentatie* gecombineerd: elk pixel krijgt zowel een klasse, als waar van toepassing een instance-identiteit. [2]

Voor het fashion-police project is *semantische segmentatie* de meest logische variant. 
De uiteindelijke installatie zal kledingkeuzes per persoon koppelen aan een opleiding, dit lijkt in dat geval op *instance segmentation*. 
Maar het scheiden van personen wordt al eerder in de pipeline opgelost door een pose-model, dat personen detecteert en uitsnijdt voordat het beeld bij het segmentatiemodel komt. 

Per uitgesneden persoon hoeft het segmentatiemodel daarmee alleen vast te stellen welke kledingklasse zichtbaar zijn, niet hoeveel exemplaren van dezelde klasse er aanwezig zijn. 
Semantische segmentatie is voor die taak voldoende en bovendien rekenkundig lichter dan instance segmentatie. Dat is van belang voor de Raspberry Pi-deployment. 

### 4.2 Kwaliteit meten: gangbare metrics

De segmentatie werkt op pixelniveau. Dat vraagt om metrics die de overeenkomst tussen het voorspelde masker en het grondwaarheidsmasker uitdrukken.

De volgende drie metrics komen het vaakst terug:

- Pixel accuracy. Dit geeft het percentage pixels dat juist is geclassificeerd. De metric is eenvoudig te begrijpen, maar weinig informatief bij onevenwichtige klasseverdelingen. Zo kan een afbeelding waarin het grootste deel van de pixels achtergrond is al snel een hoge score opleveren, zonder dat het model de daadwerkelijke kledingklassen goed voorspelt.
- Intersection over Union (IoU). IoU vergelijkt voor één klasse het overlappende gebied tussen voorspelling en grondwaarheid met het gecombineerde gebied. Een IoU van 1 betekent perfecte overlap, een IoU van 0 betekent geen overlap. Wanneer deze score per klasse wordt berekend en gemiddeld, ontstaat de mean IoU (mIoU), de standaardmetric voor semantische segmentatie in academisch onderzoek.
- Dice-coëfficiënt. Dit lijkt op IoU maar weegt de overlap zwaarder mee. De metric wordt vooral in medische beeldsegmentatie gebruikt en is gevoeliger voor kleine objecten. Voor toepassingen met grotere, duidelijk afgebakende klassen biedt Dice geen meerwaarde boven mIoU. [3]

Van de drie metrics sluit mIoU het best aan op de projectcontext: de metric is klasse-specifiek en robuust bij onevenwichtige klasseverdelingen, wat bij negen kledingklassen relevant is. Pixel accuracy is daarvoor te grof, en Dice is ontworpen voor een toepassingsgebied dat niet overeenkomt met kledingsegmentatie.

### 4.3 Architecturen voor semantische segmentatie

Er bestaan veel modelarchitecturen voor semantische segmentatie. 
In dit onderzoek zijn er drie relevant: het model dat momenteen wordt gebruikt en twee veelvoorkomende alternatieven uit de literatuur. 

#### 4.3.1 DeepLabV3

DeepLabV3 is een model voor semantische segmentatie. 
Dit betekent dat het model voor elke pixel in een afbeelding bepaalt bij welk object die hoort, zoals een persoon, auto of achtergrond. 

In deze applicatie wordt DeepLabV3 gebruikt met een ResNet-50 core. 
Het model is vooraf getraind en beschikbaar via PyTorch. 
Afbeeldingen worden eerst genormaliseerd en daarna door het model verwerkt. 

De uitvoering van het model is een segmentatiemasker waarin elke pixel een klasse krijgt. 
Daarna worden de klassen met verschillende kleuren weergegeven zodat de segmentatie zichtbaar wordt.

DeepLabV3 levert nauwkeurige resultaten, maar vraagt relatief veel rekenkracht tijdens inference. 
Wanneer het model voorspellingen maakt op nieuwe afbeeldingen vraagt relatief veel rekenkracht tijdens inference, dat wil zeggen wanneer het model voorspellingen maakt op nieuwe afbeeldingen. 
[4]

#### 4.3.2 U-Net

U-Net is oorspronkelijk ontwikkeld voor medische beeldsegmentatie en heeft een symmetrische opbouw met twee delen. 
Een *inkrimpen deel* en een *uitbreidend deel*. 
Het inkrimpende deel haalt informatie op uit de afbeelding via convoluties (CNN) en pooling (het verkleinen van de afbeelding om het grote geheel beter te begrijpen), terwijl het uitbreidende deel stap voor stap de exacte locatie van objecten herstelt. 

Belangrijk zijn de zogenoemde skip connections, die informatie uit het inkrimpende deel rechtstreeks doorgeven aan het uitbreidende deel, zodat ruimtelijke details bewaard blijven. 

Een groot voordeel is dat het al goed werkt met weinig trainingsvoorbeelden, mede door het slim uitbreiden van de trainingsdata via vervormingen. 
Het netwerk heeft geen volledig verbonden lagen en telt 23 convolutionele lagen, wat het relatief eenvoudig en snel maakt. [5]

#### 4.3.3 SegNet

SegNet is een segmentatiemodel met een encoder-decoder opbouw, ontwikkeld aan de Uni van Cambridge. Net als U-Net bestata het uit een inkrimpend deel (encoder) dat info uit de afbeelding haalt. En een uitbreindend deel (decoder) dat het masker stao voor stap terugbouwt naar de oorspronkelijke afbeeldingsgrootte.

Het verschil met U-Net zit in hoe info wordt doorgegeven van encoder naar decoder. In plaats van skip connections gebruikt SegNet zogeheten *max-pooling indices*: het model onthoudt bij elke verkleiningstap welke pixels het meest informatief waren. Gebruikt ook die posities later om de afbeelding efficiënt te vergroten. Dit maakt het model zuiniger in geheugengebruik dan U-Net.

SegNet is ontworpen voor gebruik in realtime situaties, zoals het analyseren van camerabeelden in een rijdende auto. Hierdoor is het model relatief snel en lichtgewicht, wat het ook interessant maaktg voor toepassingen op hardware met beperkte rekenkracht, zoals een Raspberry Pi [6]

### 4.4 Relevantie voor dit onderzoek

Voor de validatiestap die in dit onderzoek wordt voorgesteld, is het relevant dat al deze modellen via een vergelijkbare metric (mIoU) geëvalueerd kunnen worden. Daarmee staat de keuze van de metric los van de keuze van het model. De pipeline kan in principe elk semantische segmentatiemodel valideren dat een masker over de 9 kledingklassen produceert. De daadwerkelijke vergelijking en modelkeuze komen aan bos in H6.

### 4.5 Conclusie: wat zijn segmentatiemodellen?

Semantische segmentatie is de meest geschikte variant voor het fashion-police project: per uitgesneden persoon hoeft het model alleen vast te stellen welke kledingklassen zichtbaar zijn. Voor het meten van de kwaliteit van segmentatiemodellen is mIoU de meest geschikte metric. Pixel accuracy is te gevoelig voor onevenwichtige klasseverdelingen, en de Dice-coëfficiënt biedt voor dit toepassingsgebied geen meerwaarde. mIoU is de standaardmetric in academisch onderzoek naar semantische segmentatie en meet per klasse hoe goed de voorspelling overeenkomt met de grondwaarheid.

## 5. CI/CD-pipelines

### 5.1 Wat is CI/CD?

CI/CD staat voor *Continuous Integration* en *Continuous Delivery*. Bij CI wordt elke codewijziging automatisch gebouwd en getest, zodat fouten vroeg worden gesignaleerd. CD zorgt ervoor dat de code na het doorstaan van die tests altijd klaarstaat voor uitrol. [7]

### 5.2 Wat is een CI/CD-pipeline?

Een Ci/CD-pipeline is de reeks geautomatiseerde stappen die worden doorlopen bij elke nieuwe codewijziging. 
Typische stappen zijn het installeren van afhankelijkheden, uitvoeren van tests en bouwen van de app. 
Elke stap draait in een geïsoleerde omgeving, bijvoorbeeld een Docker-container. 
Hierdoor is de uitvoering reproduceerbaar. 
Als een stap mislukt, dan stopt de pipeline en wordt de ontwikkelaar op de hoogte gesteld. [8]

### 5.3 GitLab CI/CD

GitLab biedt een ingebouwde CI/CD-oplossing. De configuratie staat in een `.gitlab-ci.yml`-bestand in de root van het project. 
GitLab voert de pipeline automatisch uit bij elke PR of MR, via *runners* die de jobs afhandelen in een Docker-image naar keuze. [9]

### 5.4 De CI/CD-pipeline in het fashion-police project

De pipeline gebruikt een `python:3.12-slim` Docker-image en `uv` als package manager. 
De stappen zijn: installeren van dependencies, uitvoeren van tests via pytest, en publiceren van documentatie via MkDocs. 
Omdat de pipeline draait zonder GPU, worden CPU-only PyTorch-wheels geladen. 
Packages die grafische interfaces of gezichtsherkenning vereisen worden buiten de standaard installatie gehouden. 

### 5.5 Relevantie voor modelvalidatie
De huidige pipeline test of de code correct werkt, maar niet of het model betrouwbare voorspellingen doet. Een model kan een masker produceren zonder dat die output inhoudelijk correct is. Een automatische validatiestap zou dit gat dichten door na elke modelwijziging een evaluatie op een vaste testset uit te voeren.

### 5.6 Conclusie: wat is een CI/CD-pipeline?

Een CI/CD-pipeline automatiseert het testen en uitrollen van software bij elke codewijziging. In het fashion-police project is de pipeline functioneel voor codetests en documentatie, maar valideert het de kwaliteit van het segmentatiemodel niet. Een modelwijziging die de segmentatieprestaties verslechtert, passeert de huidige pipeline zonder waarschuwing. Het toevoegen van een automatische validatiestap lost dit op en sluit aan op de bestaande GitLab-configuratie.

## 6. Advies: keuze van het segmentatiemodel

### 6.1 Criteria voor de modelkeuze

De modelkeuze wordt beoordeeld op vier criteria, die direct voortvloeien uit de projectcontext.

*Nauwkeurigheid* is het eerste criterium. De installatie demonstreert hoe subjectieve aannames in technische systemen als objectief worden gepresenteerd. Grove fouten in het segmentatiemasker ondermijnen die boodschap.

*Rekenkracht tijdens inference* is het tweede criterium. De installatie draait op een Raspberry Pi zonder GPU. Modellen die veel rekentijd vragen zijn in die context niet bruikbaar voor realtime verwerking van camerabeelden.

*Trainbaarheid met beperkte data* is het derde criterium. De dataset bestaat uit zelfverzamelde afbeeldingen van negen kledingklassen. Modellen die goed presteren met weinig trainingsvoorbeelden hebben daardoor een voordeel.

*Integratie in de bestaande codebase* is het vierde criterium. Overstappen naar een andere architectuur brengt implementatierisico's met zich mee in een lopend project met een vaste opleverdatum.

### 6.2 Vergelijking van de architecturen

| Criterium | DeepLabV3 | U-Net | SegNet | 
| --- | --- | --- | --- |
| Nauwkeurigheid | Hoog | Hoog bij weinig data | Gemiddeld |
| Rekenkracht (inference) | Hoog | Gemiddeld | Laag | 
| Trainbaarheid met weinig data | Gemiddeld | Goed | Gemiddeld|
| Integratie in bestaande codebase | Al geïmplementeerd | Herstructurering nodig | Herstructurering nodig | 

DeepLabV3 scoort hoog op nauwkeurigheid op basis van gepubliceerde benchmarks en de resultaten van het huidige project, maar vraagt de meeste rekenkracht van de drie architecturen. [4] U-Net scoort hoog op nauwkeurigheid bij weinig trainingsdata doordat het model is ontworpen voor situaties met beperkte datasets en gebruik maakt van data-augmentatie tijdens training. [5] De rekenkracht ligt lager dan DeepLabV3, maar integratie vereist een volledige herstructurering van de bestaande modelkoppeling. SegNet scoort het laagst op nauwkeurigheid maar is expliciet ontworpen voor realtime inference op embedded hardware, wat zich vertaalt in het laagste geheugengebruik en de snelste inferentiesnelheid van de drie. [6]

### 6.3 Aanbeveling

Het advies is om DeepLabV3 te handhaven als segmentatiemodel. Het model is al volledig geïntegreerd in de bestaande pipeline, die YOLO gebruikt voor person extraction gevolgd door DeepLabV3 voor kledingsegmentatie. Overstappen naar een andere architectuur brengt implementatierisico's met zich mee die niet opwegen tegen de mogelijke winst.

Dit advies is gericht op het ontwikkelteam en de opdrachtgever Yuri Westplat. De aanbeveling is gebaseerd op de huidige projectfase: de conferentiedemo heeft een vaste opleverdatum en wisselen van architectuur brengt risico's met zich mee die op dit moment niet verantwoord zijn.

Een risico van het handhaven van DeepLabV3 is dat de inferentiesnelheid op de Raspberry Pi onvoldoende blijkt voor realtime verwerking. De randvoorwaarde voor dit advies is daarom dat de pipeline-optimalisatie (het vervangen van YOLO en MediaPipe door één pose-model, wat de totale latency met circa 12,5% verlaagt) succesvol wordt afgerond. Als dat niet het geval is, of als DeepLabV3 te traag blijkt na optimalisatie, is overstappen naar SegNet de aangewezen vervolgstap.

De validatiestap in de CI/CD-pipeline blijft model-onafhankelijk: zolang het segmentatiemodel een masker produceert over de negen kledingklassen, kan de kwaliteit via mIoU worden beoordeeld. De uitwerking daarvan volgt in hoofdstuk 7.

## 7. Ontwerp: automatische validatieschap (deelvraag 5 - ontwerpen)

// Dit hoofdstuk is nog in uitwerking en wordt in de volgende sprint afgerond.

## 8. Realisatie en resultaten (deelvraag 6 - realiseren)
// Dit hoofdstuk is nog in uitwerking en wordt in de volgende sprint afgerond.

## 9. Conclusie

De hoofdvraag in dit onderzoek was: hoe kan de kwaliteit van segmentatiemodellen in het fashion-police project automatisch worden gevalideerd in de GitLab CI/CD-pipeline?

Uit de analyse blijkt dat de huidige pipeline modelfouten niet detecteert: code die correct werkt kan een segmentatiemasker produceren dat inhoudelijk incorrect is. Voor een installatie waarbij de geloofwaardigheid direct afhangt van de segmentatiekwaliteit is dit een concreet risico.

mIoU is de meest geschikte metric om die kwaliteit te meten: de metric is klasse-specifiek, gangbaar in academisch onderzoek en toepasbaar op elk model dat een masker over de negen kledingklassen produceert.

Het advies is om DeepLabV3 te handhaven als segmentatiemodel voor de huidige fase, mits de pipeline-optimalisatie via één pose-model succesvol wordt afgerond. Bij onvoldoende inferentiesnelheid op de Raspberry Pi verdient SegNet de voorkeur.

De voorgestelde validatiestap (uitgewerkt in hoofdstuk 7) sluit aan op de bestaande GitLab CI/CD-configuratie en kan zonder GPU worden uitgevoerd. Daarmee biedt het een structurele oplossing voor het gesignaleerde probleem.

## 10. Koppeling met BoKSA-leeruitkomsten

| Deelvraag | Leeruitkomst |
|-----------|--------------|
| 1, 2, 3   | Analyseren   |
| 4         | Adviseren    |
| 5         | Ontwerpen    | # overgeslagen voor nu
| 6         | Realiseren   | # overgeslagen voor nu

## 11. Bronvermelding

[1] - https://learnopencv.com/intersection-over-union-iou-in-object-detection-and-segmentation/#IoU-in-Image-Segmentattion 

[2] - https://www.jeremyjordan.me/evaluating-image-segmentation-models/

[3] - https://apxml.com/courses/cnns-for-computer-vision/chapter-4-image-segmentation-techniques/segmentation-evaluation-metrics 

[4] - https://pytorch.org/hub/pytorch_vision_deeplabv3_resnet101/

[5] - https://arxiv.org/pdf/1505.04597v1 

[6] - https://arxiv.org/abs/1511.00561 

[7] - https://martinfowler.com/articles/continuousIntegration.html 

[8] - https://docs.gitlab.com/ci/pipelines/ 

[9] - https://docs.gitlab.com/runner/