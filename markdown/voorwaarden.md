# Voorwaarden voor aanlevering

## Bronsysteem
Voor het bronsysteem gelden de volgende voorwaarden:

* Het bronsysteem moet informatieobjecten en metagegevens bevatten.
* Het bronsysteem kan bestanden bevatten. 
* MDTO metagegevens kunnen worden aangeleverd vanuit het bronsysteem.
* Het bronsysteem kan alle, ook niet MDTO compliant metagegevens aanleveren aan het doelsysteem. 
* In een aanlevering van een bronsysteem kunnen ook bestanden meegeleverd worden. 

## Export bronsysteem
De archiefvormer moet in staat zijn om een export te maken uit het bronsysteem, in de vorm van een SIP. De export voldoet aan de eisen die gesteld worden aan de SIP in de MDTO standaard. 
Bij overbrenging bestaat de export uit het bronsysteem uit niet meer te wijzigen ’bevroren’ informatieobjecten. Voor deze informatieobjecten en bestanden is sprake van een verplaatsing (move). De informatieobjecten kunnen soms deel uitmaken van een hiërarchische structuur die in het bronsysteem aanwezig moet blijven. In dat geval worden de metadata van de bovenliggende structuur gekopieerd en meegeleverd in de export. Dit doet zich bijvoorbeeld voor wanneer een export wordt gemaakt van een reeks afgesloten zaakdossiers van een zaaktype dat nog actief is.

Elke organisatie kan kiezen voor:

* een **move** waarbij het informatieobject wordt verplaatst, van bronsysteem naar doelsysteem.
* een **copy**, waarbij een kopie van het informatieobject uit het bronsysteem in het doelsysteem wordt aangemaakt
* een **update**, waarbij de metagegevens van een informatieobject uit het bronsysteem worden geharmoniseerd met een informatieobject in het doelsysteem.  Bij een update bepaalt de ontvangende partij wat nog wel of niet als een update geldt en wanneer er sprake is van een copy.  
  
Het verplaatsen van informatieobjecten (move) is de aanbevolen werkwijze. 

NB. Het bestaan van informatieobjecten op twee locaties kan tot discrepanties leiden bij eventuele vervolgaanleveringen. De ontvangende partij moet als ontvangende partij het doelsysteem inrichten hoe om te gaan met de resolutie van conflicten.

## Voorwaarden doelsysteem
Voor het doelsysteem gelden de volgende voorwaarden:

* Het doelsysteem moet informatieobjecten en metagegevens kunnen opnemen.
* Het doelsysteem moet bestanden kunnen opnemen. 
* MDTO metagegevens kunnen worden verwerkt.
* Het doelsysteem kan alle, ook niet MDTO compliant metagegevens verwerken. 
  
## Voorwaarden pakbon
De ontvangende partij moet van elke aangeleverde SIP kunnen vaststellen van wie deze afkomstig is en wat de inhoud is. Bij de aanlevering van de export in een SIP levert de aanleverende organisatie daarom een zogenoemde pakbon mee. De inhoud van deze pakbon is beschreven in de module ‘Specificatie Submission Information Package (SIP)’.
Het formaat van aanlevering van de pakbon spreekt u af met uw contactpersoon bij de ontvangende partij. Het formaat kan daarmee verschillen van een op .xml of JSON gebaseerd bericht tot een e-mail.

## Aggregatieniveaus
In een aanlevering verwijst elk informatieobject naar het bovenliggende en onderliggende informatieobject. Elke aanlevering kent in ieder geval één aggregatieniveau.  Er is bij elke aanlevering een verwijzing opgenomen naar een bovenliggend aggregatieniveau in het doelsysteem. Deze wordt door de ontvangende partij vastgesteld en doorgegeven aan de aanleverende partij.  De aanleverende partij kan het bovenliggende aggregatieniveau enkel als relatie meegeven in de SIP bij de daaronder liggende informatieobjecten. In de pakbon moet een verwijzing naar het toplevel informatieobject zijn opgenomen.

## Vervolgexporten
Vervolgexporten zijn toevoegingen aan een bestaande collectie in het doelsysteem. Deze moeten voldoen aan alles wat hiervoor beschreven is voor een initiële export. Een vervolgexport bevat alleen informatieobjecten en bestanden die niet al in een voorgaande export naar het doelsysteem zijn verzonden, tenzij anders afgesproken. (Zie voorwaarden export bronsysteem)

## Wijze van verzending en bestemming
Voor de aanlevering wordt gebruik gemaakt van een geautomatiseerde, veilige verbinding, zoals bijvoorbeeld FTPS. Op welke wijze u de export verzendt naar een doelsysteem, spreekt u af met uw contactpersoon bij de ontvangende partij.
Elke levering bevat naast de metagegevens en de bestanden ook de logistieke gegevens over de aanlevering in de pakbon.

## Voorwaarde formaat van export
U levert uw SIP aan in een van de, door de ontvangende partij, toegestane  formaten aan.  
Deze kan bijvoorbeeld eisen dat de SIP verpakt  in een containerformaat, .tar of .zip, aangeleverd wordt. Dit kan dan een multi-volume .tar of .zip zijn. 

## Maximum aantal bestanden
De ontvangende partij kan een maximum stellen aan de grootte en/of het aantal bestanden in een container. Dit maximum moet vermeld zijn in de aansluitvoorwaarden van de ontvangende partij.

Wil u meer dan het maximum aantal bestanden aanleveren, dan levert u meerdere containers aan. Indien het de eerste aanlevering uit het bronsysteem betreft, dan is een van deze containers de initiële export en zijn de overige containers vervolgexporten. Dit betekent voor elke container een pakbon, met een afwijkende timestamp en hashcode.

NB. Alle bestanden tellen mee voor het maximum aantal bestanden, dus ook de mdto.xml-bestanden.

## Controle op verzending
De ontvangende partij controleert de verzending van de export naar het doelsysteem. Hiervoor maakt deze partij gebruik van de logistieke gegevens zoals deze zijn geleverd in de pakbon. Tevens vindt er een volledigheids- en integriteitscontrole plaats op de MDTO metagegevens van de informatieobjecten en bestanden.

## Berichtenservice voor controle op ontvangst
Het doelsysteem ondersteunt een berichtenservice voor aanlevering met het bronsysteem, c.q. de verzendende partij. Deze berichtenservice kan, maar hoeft niet geautomatiseerd te zijn.

De volgende berichten worden ondersteund:

* de aankondiging van een aanlevering door het bronsysteem
* de ontvangst van de aanlevering door het doelsysteem
* de opname in het doelsysteem
* foutmeldingen bij de opname in het doelsysteem.

Elk bericht bevat in ieder geval de volgende informatie:

* uniek identificatienummer van de aanlevering
* aantal informatieobjecten en aantal bestanden:
verwerkt/uitgevallen identificatie en reden van evt. uitval
* datum verzending/datum verwerking
* eventuele foutmeldingen
* afzender
* bestemming.

De foutmeldingen zijn divers en kunnen bij elke ontvangende partij verschillen. Elke foutmelding kent de volgende structuur :

* ID informatieobject / bestand ( in SIP)
* Naam informatieobject / bestand
*  reden fout:  bijv. ontbreken metagegevens of onbekend bestand.

De ontvangende partij weigert de volledige aanlevering bij een foutmelding, tenzij hierover aparte afspraken zijn gemaakt.