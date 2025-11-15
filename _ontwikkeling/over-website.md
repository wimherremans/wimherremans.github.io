---
title: "Over de ontwikkeling van deze website"
layout: default
---
<div id="inhoud-ontwikkeling">
    <h3 id="inhoud">Inhoudstafel</h3>
    <p><a href="#jekyll">Jekyll</a></p>
    <p><a href="#mappenstructuur">Mappenstructuur</a></p>
    <p><a href="#layout-website">De layout van deze website</a></p>
    <p><a href="#foto-docs">Foto’s en documenten</a></p>
    <p><a href="#foto-albums">Fotoalbums</a></p>
    <p><a href="#nieuwsbrieven">Nieuwsbrieven</a></p>
    <p><a href="#navigatie-menu">Navigatiemenu</a></p>
    <p><a href="#relative-url"><em>baseurl</em> en <em>relative_url</em></a></p>
    <p><a href="#permalink">Permalink</a></p>
    <p><a href="#verslagen">Verslagen</a></p>
</div>

### Jekyll {#jekyll}

Deze website is ontwikkeld met
<a href="https://jekyllrb.com/" target="_blank">Jekyll</a>. Dat is een
gereedschap dat een statische website genereert. Dat wil zeggen dat de html van
webpagina's die door de webserver naar de browser gestuurd worden niet door de
webserver worden gegenereerd. De html van de webpagina's wordt op de computer
van de ontwikkelaar gegenereerd met Jekyll als gereedschap en vervolgens
overgestuurd naar de webserver, die ze niet verandert of interpreteert.

Jekyll heeft een aantal interessante eigenschappen die het mogelijk maken een
website met meerder pagina's te ontwerpen die toch een grote uniformiteit
vertonen zonder dat de ontwikkelaar html-code moet dupliceren. In het bijzonder
maakt Jekyll het gemakkelijk ervoor te zorgen dat alle pagina's dezelfde header,
navigatiemenu en footer hebben. Als een van deze elementen moet gewijzigd
worden, moet die wijziging maar op één plaats gebeuren.

De volgende kenmerken van Jekyll maken dat mogelijk.

- Jekyll maakt het mogelijk sjablonen voor webpagina's te ontwerpen die vervolgens
  worden toegepast op de te ontwerpen webpagina's. Jekyll duidt die sjablonen
  aan met de term *layout*.

- Jekyll biedt de mogelijkheid om html fragmenten te includeren in webpagina's.
  Daarbij is het zelfs mogelijk parameters door te geven die het gedrag van die
  html fragmenten beïnvloedt. Voorbeelden waarvoor zo'n html fragmenten kunnen
  gebruikt worden:

    - de header van de webpagina;
    
    - de footer van de webpagina;
    
    - het navigatiemenu;
    
    - een fotoalbum.

- Een webpagina kan rechtstreeks in html ontworpen worden, maar ook in
 <a href="https://www.markdownguide.org/" target="_blank">Markdown</a>, een
opmaaktaal die veel eenvoudiger is dan html en dus ook veel minder mogelijkheden
heeft, maar die voor tekst en tabellen zeer goed werkt. Deze webpagina is bv.
volledig in markdown geschreven. Afbeeldingen in een webpagina brengen kan wel,
maar dan heb je geen controle over de positionering en afmetingen van de
afbeelding. Dat is wel op te lossen door de afbeelding in te voegen via een
voorgedefinieerde layout.

- Het bronbestand voor een webpagina, html of markdown, bevat in het begin gegevens
  die *front matter* genoemd worden. Dergelijke gegevens zijn o.a.:

   - title: de titel van de webpagina;
   
   - layout: het sjabloon dat bij het genereren van de pagina zal worden toegepast;
   
   - foto: een pad naar een foto die door het sjabloon in de gegenereerde pagina
     zal worden geplaatst:
     
   - album: de naam van een fotalbum dat kan worden ingevoegd in de webpagina.

- Jekyll ondersteunt een *sjabloon taal* die
 <a href="https://shopify.github.io/liquid/" target="_blank">Liquid</a>
wordt genoemd. Dat is een taal die in layouts, fragmenten en webpagina's
kan gebruikt worden om html te genereren afhankelijk van de site configuratie
(gedefinieerd in _config.yml, zie verder) en van de *front matter* gegevens.

[Terug naar inhoudstafel](#inhoud)

### De mappenstructuur {#mappenstructuur}

Voor deze website is de volgende mappenstructuur gebruikt.
~~~
.
├── _config.yml  # configuratie van deze website
├── _home
|     ├── index.html # home page
|     ├── maandagenda.md
|     ├── terugkerend.md
|     └── nieuwsbrieven.html
├── _activiteiten
|     ├── biljart.md
|     ├── bridge.md
|     ├── petanque.html
|     ├── plezier-fietsers.md
|     ├── sportieve-fietsers.md
|     └── hobby-handwerk.md
├── _allerlei
|     ├── geschiedenis.md
|     ├── privay.md
|     ├── verwijzingen.html
|     └── over-website.md  # pagina die je nu leest
├── assets
|     ├── bijlagen  # foto's, documenten, albums die getoond worden in wepagina's
|     |     ├── activiteiten
|     |     ├── allerlei
|     |     ├── home
|     |     └── nieuwsbrieven
|     └── css  # stylesheets
├── _data  # niet gebruikt
├── _drafts
│       └── contact.html
├── _includes
|     ├── meta.html
│     ├── header.html
│     ├── nav.html
|     ├── footer.html
|     └── fotoalbum.html
├── _layouts
│     └── default.html
├── _ontwikkeling
|     ├── index.html
|     ├── over-website.md
|     └── test.html
├── _posts  # hier komen de verslagen. Zie verder.
│     ├── 2025-10-23-somme.html
│     ├── 2025-10-25-video-elewijt.html
│     └── 2025-10-28-verslag-fietstocht.html
├── _sass # niet gebruikt bij deze website: alle scss in assets
└── _site # hier komt de gegenereerde website
~~~

Wat je hier ziet is de mappenstructuur van alles wat Jekyll gebruikt als
bron om de website te genereren. De enige uitzondering daarop is de map "_site".
Dat is geen bronmap, maar de map waarin Jekyll de bestanden wegschrijft die
moeten worden opgeladen naar de webserver. Al de rest blijft op de computer
van de ontwikkelaar.

**Nota**:

 1. *Dit betekent wel dat snel een bestandje op de webserver aanpassen
    om iets te corrigeren niet meer kan omdat daarmee de bron niet gecorrigeerd is
    en dus bij een volgende uitvoering van Jekyll zal worden tenietgedaan. Alle
    correcties moeten gebeuren in de bronbestanden. In sommige gevallen, bv. bij
    een update in header, footer of menu zal dat betekenen dat je de volledige
    website (map "_site") terug moet opladen.*

 2. *Wat wel kan is dat je bv. één bronbestand bijwerkt, Jekyll opnieuw laat
    lopen en vervolgens alleen de overeenkomstige webpagina overstuurt naar de
    webserver.*

[Terug naar inhoudstafel](#inhoud)

### De layout van deze website {#layout-website}

De layout van de webpagina's van deze website zijn volledig gedefinieerd in het
sjabloon *_layout/default.html*.

Hieronder zie je de inhoud van *default.html*.

{% raw -%}
~~~
<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" -}}">
<head>
    {% include meta.html -%}
</head>
    <body>
        <div id="whole-page">
            <header>
                {% include header.html -%}
                {% include nav.html -%}
            </header>
            <main id="page-content">
                <h2 style="text-align: center;">{{ page.title -}}</h2>
                {% if page.auteur != "" -%}
                    <p style="font-size: small;">{{ page.auteur -}} - {{ page.date | date: "%d %B %Y" -}}</p>
                {% endif -%}
                {% if page.foto != "" -%}
                    <img src="{{ page.foto | relative_url -}}" alt="Foto niet gevonden" class="inline-left">
                {% endif -%}
                {{ content -}}
            </main>
            <footer>
                {% include footer.html -%}
            </footer>
        </div>
  </body>
</html>
~~~
{% endraw -%}

Alles wat tussen accolades met "%" staat is programma code in de *Liquid* taal
die wordt uitgevoerd als Jekyll de website bouwt.

Alles wat tussen dubbele accolades staat wordt bij het bouwprocess vervangen
door de waarde van de variabele die tussen de accolades staat. We zien hier
meerdere voorbeelden van variabelen:

  - *content* is de variable die de inhoud van het bronbestand van de webpagina
    bevat nadat die door Jekyll is omgezet naar zuivere html. D.w.z. markdown
    is omgezet naar html en alle Liquid code die eventueel in het bronbestand
    staat is uitgevoerd.

  - *site.lang* is een configuatie parameter die kan ingesteld worden in het
    bestand *_config.yml*.
    
  - *page.foto* krijgt een waarde in de *front matter* van de bron van de pagina.
    Hier is bv. de front matter van de pagina voor de biljart activiteit. De front
    matter is te vinden in de eerste lijnen van het bronbestand. Begin en einde
    worden aangeduid met "- - -".
    
~~~
      ---
      layout: default
      title: "Biljart"
      foto: "/assets/bijlagen/activiteiten/biljart/OkraBiljart_02.jpg"
      ---
~~~

  - Ook *page.title* krijgt een waarde in de *front matter* van de bron van
    de pagina.

  - *page.auteur* is alleen bedoeld voor "posts" en krijgt ook een waarde
    in de front matter. De default is "" voor alle pagina's en "onbekend"
    voor posts.

Merk op dat de default layout de mogelijkheid biedt om een foto in de webpagina
te plaatsen door alleen maar de *foto* front matter parameter naar een foto
te laten verwijzen. De positionering van de foto wordt door de layout bepaald.
Als de webpagina geen extra foto's nodig heeft, kan de webpagina volledig
in markdown geschreven worden.

[Terug naar inhoudstafel](#inhoud)

### Foto's en documenten {#foto-docs}

Alle foto's en documenten zijn terug te vinden onder de map assets/bijlagen
en submappen daarvan.

Ik heb ernaar gestreefd een duidelijk verband te behouden tussen de locatie
van de bronbestanden van de webpagina's en de locatie van hun bijbehorende
foto's en documenten. Dat is best uit te leggen aan de hand van het voorbeeld
 van de foto's die worden weergeven op de pagina over petanque.

 De bron van de pagina over petanque bevindt zich op:

 /_activiteiten/petanque.html

 De bijhorende foto's heb ik gezet op

 /assets/bijlagen/activiteiten/petanque

 Daarin staat de foto die op de pagina getoond wordt, maar ook nog een submap
 met de naam "album" die 9 foto's bevat die als een album getoond worden
 op de pagina.
 
 [Terug naar inhoudstafel](#inhoud)

### Fotoalbums {#foto-albums}

Er is een speciaal html fragment (_includes/fotoalbum.html) gemaakt voor deze
 website. Deze include kan in een webpagina worden opgeroepen. Hieronder zie je
 een voorbeeld uit petanque.html:
 
 {% raw -%}
 ~~~
 {% include fotoalbum.html album = "petanque" %}
 ~~~
 {% endraw -%}

Jekyll toont op die plaats alle foto's van het album "petanque" in een raster
van 3 kolommen en zoveel rijen als nodig. Elke foto is aanklikbaar voor een
vergrootte weergave.

Wat nog ontbreekt is hoe we Jekyll wijsmaken waar de foto's van het album
petanque staan.

Dat doen we via het configuratiebestand _config.yml. We kunnen daarin "default"
frontmatter parameters definiëren voor bestanden, ook voor bestanden zoals
foto's of documenten die zelf geen front matter kunnen bevatten omdat we er geen
tekst kunnen in schrijven.

Hieronder zie je hoe in de *defaults* in _config.yml 2 albums worden gedefinieerd.

~~~
defaults:
  - scope:
        path: "assets/bijlagen/posts/2025-10-23-somme/album"
    values:
        album: "2025-10-23-somme"
  - scope:
        path: "assets/bijlagen/activiteiten/petanque/album"
    values:
        album: "petanque"

~~~

Daarin zie je dat alle bestanden in de map "assets/bijlagen/activiteiten/petanque/album"
een front matter gegeven album: "petanque" krijgen. Dat biedt ons de mogelijkheid
alle foto's van het album in een lijst te zetten waarmee Jekyll dan html code
kan genereren om het album te tonen. Zie hieronder de bron van de include
fotoalbum.html

{% raw %}
~~~
<div class="fotoalbum">
    {% assign album-images = site.static_files | where: "album", include.album %}
    {% for myimage in album-images %}
        <a href="{{ myimage.path }}" target="_self"> <img src="{{ myimage.path }}" alt="{{ myimage.name }}"></a>
    {% endfor %}
</div>
~~~
{% endraw %}

*include.album* is de parameter die bij de oproep vanuit petanque.html de waarde
"petanque" krijgt.

Het resultaat kun je zien in de webpagina Activiteiten → Petanque.

[Terug naar inhoudstafel](#inhoud)

### Nieuwsbrieven {#nieuwsbrieven}

De webpagina "Nieuwsbrieven" wordt automatisch gegenereerd aan de hand van
de bestanden die worden opgeslagen in de map "/assets/bijlagen/nieuwsbrieven".

Daaronder vind je een map voor dit jaar en vorig jaar.

In elke jaarmap vind je een map *jaar* en een map *maanden*.

In de map *jaar* vind je juist één PDF met het jaarprogramma.

In de map *maanden* vind je de maandelijkse nieuwsbrieven.

Het programma in de nieuwsbrieven webpagina toont de jaarprogramma's van het
lopende en het vorige jaar. Het steunt op de naamgeving die tot
nu toe gebruikt werd voor de maandelijkse nieuwsbrieven:

  1. OKRANieuwsFebruari2025.pdf
  2. OKRANieuwsMaart2025.pdf
  3. OKRANieuwsApril2025.pdf
  4. OKRANieursMei2025.pdf
  5. OKRANieuwsJuni2025.pdf
  6. OKRANieuwsZomer2025.pdf
  7. OKRANieuwsSeptember2025.pdf
  8. OKRANieuwsOktober2025.pdf
  9. OKRANieuwsNovemer2025.pdf
 10. OKRANieuwsWinter2025.pdf

Zolang deze naamgeving wordt aangehouden kan een nieuwsbrief op de website
worden toegevoegd door alleen maar de PDF in de juiste map te plaatsen en
Jekyll opnieuw laten lopen. Daarna de gegeneerde webpagina "_site/nieuwsbrieven.html"
opladen naar de webserver.

Het programma in de nieuwsbrieven webpagina geeft alleen de nieuwsbrieven van de
laatste 2 jaren. Het programma steunt ook op de instellingen in "_config.yml". 
Bij "defaults" vind je daarin het volgende:

~~~
defaults:
  - scope:
        path: "assets/bijlagen/home/nieuwsbrieven/2025/jaar"
    values:
        brief: "dit-jaar"
  - scope:
        path: "assets/bijlagen/home/nieuwsbrieven/2024/jaar"
    values:
        brief: "vorig-jaar"
  - scope:
        path: "assets/bijlagen/home/nieuwsbrieven/2025/maanden"
    values:
        brief: "maand-dit-jaar"
  - scope:
        path: "assets/bijlagen/home/nieuwsbrieven/2024/maanden"
    values:
        brief: "maand-vorig-jaar"
~~~

Als in het begin van een nieuw jaar de eerste maandelijkse nieuwsbrief wordt
gepubliceerd moet het "_config.yml" bestand aangepast worden. Bv. bij het begin
van 2026 wordt 2026 "dit-jaar" en 2025 "vorig-jaar". De wijziging beperkt zich
dus tot 2025 overschrijven met 2026 en 2024 overschrijven met 2025.

De nieuwsbrieven van 2024 kunnen dan eventueel verwijderd worden door de submap
2024 te verwijderen. Ze worden in ieder geval niet meer getoond op de webpagina.

[Terug naar inhoudstafel](#inhoud)

### Navigatiemenu {#navigatie-menu}

Het navigatiemenu wordt automtisch gegenereerd vanuit "_includes/nav.html"
gebaseerd op de data in _config.yml.

Hieronder zie je de menudefinitie in "_config.yml".

~~~
#
# MENU
#   Een array van menu-items.
#   "label" is de string die getoond wordt voor het menu-item
#   "url" is de url waar het menu-item naar wijst
#   "children" is de lijst van de sub-menu-items 
#   Als "children" niet leeg is, wordt het hoofd-menu-item geen verwijzing
#   naar een webpagina, maar wordt het een knop om een dropdown menu te openen.
menu:
  - label: "Welkom"
    url: "/"
    children: ""
  - label: "Agenda"
    url: "/maandagenda.html"
    children: ""
  - label: "Terugkerend"
    url: "/terugkerend.html"
    children: ""
  - label: "Activiteiten"
    url: ""
    children:
      - label: "Terugkerende activiteiten"
        url: "/terugkerend.html"
      - label: "Biljart"
        url: "/activiteiten/biljart/"
      - label: "Bridge"
        url: "/activiteiten/bridge/"
      - label: "Petanque"
        url: "/activiteiten/petanque/"
      - label: "Hobby & Handwerk"
        url: "/activiteiten/hobby-handwerk/"
      - label: "Plezierfietsers"
        url: "/activiteiten/plezier-fietsers/"
      - label: "Sportieve fietsers"
        url: "/activiteiten/sportieve-fietsers/"
  - label: "Nieuwsbrieven"
    url: "/nieuwsbrieven.html/"
    children: ""
  - label: "Allerlei"
    url: ""
    children:
      - label: "Contactpersonen"
        url: "/allerlei/contactpersonen/"
      - label: "Verslagen"
        url: "/allerlei/verslagen/"
      - label: "Geschiedenis"
        url: "/allerlei/geschiedenis/"
      - label: "Privacy"
        url: "/allerlei/privacy/"
      - label: "Verwijzingen"
        url: "/allerlei/verwijzingen/"
# Een apart menu MENU-ONTWIKKELING wordt normaal niet getoond. Het verschijnt
# alleen als in de browser adresbalk expliciet https://okraranst.be/ontwikkeling
# wordt opgeroepen.
menu-ontwikkeling:
  - label: "Home"
    url: "/"
    children: ""
  - label: "Ontwikkeling"
    url: ""
    children:
      - label: "Index"
        url: "/ontwikkeling/"
      - label: "Over deze website"
        url: "/ontwikkeling/over-website.html"
      - label: "Test Liquid"
        url: "/ontwikkeling/test.html"
~~~

Hieronder zie je de code van nav.html. Buiten Liquid bevat het ook javascript
om een dropdown menu te openen als de gebruiker op het parent-menu klikt en het
te sluiten als de gebruiker ergens buiten het menu klikt.

~~~
{% raw -%}
<nav class="hornav">
    {% if page.collection == "ontwikkeling" -%}
        {% assign menu-list = site.menu-ontwikkeling -%}
    {% else -%}
        {% assign menu-list = site.menu -%}
    {% endif -%}
    {% for item in menu-list -%}
        {% if item.children == "" -%}
            <a href="{{ item.url | relative_url -}}" class="hor-item">{{ item.label -}}</a>
        {% else -%}
            <div class="dropdown">
                <button class="hor-item dropbtn"
                onclick="document.getElementById('dropdown-{{ item.label -}}').classList.toggle('show');">
                    {{ item.label -}}
                </button>
                <div id="dropdown-{{ item.label -}}" class="dropdown-content">
                    {% for child in item.children -%}
                        <a href="{{ child.url | relative_url -}}" class="vert-item" >{{ child.label -}}</a>
                    {% endfor -%}
                </div>
            </div>
        {% endif -%}
    {% endfor -%}
</nav>

<script type="text/javascript" >
// Close the dropdown menu if the user clicks outside of it
    window.onclick = function(event) {
        if (!event.target.matches('.dropbtn')) {
            var dropdowns = document.getElementsByClassName("dropdown-content");
            var i;
        for (i = 0; i < dropdowns.length; i++) {
            var openDropdown = dropdowns[i];
            if (openDropdown.classList.contains('show')) {
                openDropdown.classList.remove('show');
            }
        }
      }
    }
</script>
{% endraw -%}
~~~

[Terug naar inhoudstafel](#inhoud)

### *baseurl* en *relative_url* {#relative-url}

Stel bv. dat we de website niet zouden installeren op https://okraranst.be/ maar
op https://okraranst.be/experiment/.

Als je niets verandert aan de website, zullen alle interne verwijzingen mislukken.
D.w.z. het navigatie menu werkt niet meer en de webserver vindt de foto's niet meer.

Jekyll heeft een zeer intelligente oplossing daarvoor.

Er is namelijk een configuratieparameter *baseurl* in "_config.yml".

Initieel staat er:

~~~
baseurl: "" # the subpath of your site, e.g. /blog
~~~

Als de website op https://okraranst.be/experiment/ gaat komen moet je invullen:

~~~
baseurl: "/experiment"
~~~

Dat werkt maar als je bij de interne verwijzingen een speciale functie van Jekyll
gebruikt. Stel dat ik een foto wil tonen op een webpagina:

~~~
<img src="/assets/bijlagen/home/Ranst-centrum.png" class="inline-right">
~~~

Maar als ik de website verplaats naar de submap "/experiment" zal deze foto niet
gevonden worden want in de hoofdmap van de webserver is er geen map
"/assets" of alleszins niet de juiste. Ik zou de html dan moeten veranderen naar:

~~~
<img src="/experiment/assets/bijlagen/home/Ranst-centrum.png" class="inline-right">
~~~

Het zou een hele klus zijn om alle interne verwijzingen te veranderen.

Als je die html bij het ontwerp schrijft als volgt

{% raw -%}
~~~
<img src="{{ "/assets/bijlagen/home/Ranst-centrum.png" | relative_url }}" class="inline-right">
~~~
{% endraw -%}

dan zal die Liquid code de baseurl (/experiment) vóór de opgegeven url plakken.

Je vindt de uitleg daarvoor hier: <a href="https://jekyllrb.com/docs/liquid/filters/" target="_blank">Liquid Filters</a>.

Verplaatsen van de website is dus alleen maar de baseurl aanpassen en de website
opnieuw genereren met Jekyll.

[Terug naar inhoudstafel](#inhoud)

### Permalink {#permalink}

Het standaard gedrag van Jekyll bij het bouwen van de website is dat alle
bronbestanden worden omgezet naar een html-bestand op basis van hun sjabloon. Ze
worden dan weggeschreven in de map "_site" of submappen daarvan. Een bronbestand
dat in de submap "_activiteiten" staat zal op "_site" worden geplaatst in de
submap "activiteiten". Het bronbestand van de pagina over petanque staat op
"_activiteiten/petanque.md" en zal door Jekyll, na omzetting naar html
geschreven worden in "_site/activiteiten/petanque.html".

Dat betekent dat de URL naar de webpagina voor petanque de volgende is:

URL: https://okraranst.be/activiteiten/petanque.html

Sommige mensen beschouwen zo'n URL lelijk vanwege ".html".

Jekyl heeft daarvoor het concept *permalink* ontwikkeld. Zie
<a href="https://jekyllrb.com/docs/permalinks/" target="_blank">Permalinks</a>.

 Je kunt in het bronbestand "_activiteiten/petanque.md" de volgende front matter
 zetten:

~~~
---
layout: default
title: "Petanque"
foto: "/assets/bijlagen/activiteiten/petanque/OkraPetanque_01.jpg"
permalink: "/activiteiten/petanque/"
---
~~~

Als Jekyll de website genereert, dan schrijft hij de genereerde html niet in

_site/activiteiten/petanque.html

maar in

_site/activiteiten/petanque/index.html

Daardoor wordt de URL de volgende:

URL: https://okraranst.be/activiteiten/petanque

Als je in elk bronbestand zo'n permalink moet zetten wordt dat nogal omslachtig.

Jekyll heeft daar weer een mooie oplossing voor. Je kunt *permalink* niet alleen
definiëren in de front matter van de bronbestanden, maar ook in "_config.yml".

Daarin kun je een *permalink* definitie zetten die een soort default is voor alle
webpagina's en je kunt een meer specifieke *permalink* definitie zetten voor
elke *collection*. Een *collection* is een verzameling van webpagina's waarvan
de bronbestanden in een submap van de hoofdmap zitten. Deze submappen moeten
altijd een naam hebben die begint met een underscore (_). Hieronder zie je
de collections definitie voor deze website en de permalink definitie voor
elk daarvan.

~~~
#
# PERMALINK kan bepaald worden op niveau van de site, van de collections en
# op niveau van de webpagina's in de front matter.
# permalink bepaalt de mappenstructuur van de gegenereerde website (_site/).
# De mappenstructuur bepaalt impliciet de URLs van de webpagina's.
# Zie https://jekyllrb.com/docs/permalinks/ voor meer uitleg.
#
# Ik heb hier gekozen voor een definitie op niveau van de page collections.
# permalink: op niveau van de site heb ik niet gebruikt.
#
# Hier worden page COLLECTIONS gedefinieerd. Dat zijn webpagina's waarvan de
# bronbestanden in een submap worden geplaatst en die op een of andere manier
# samenhoren. Voor de hier gedefinieerde collections moeten de bronbestanden
# geschreven worden in de submappen "_activiteiten", "_allerlei", "_posts" en
# "_drafts" en "_ontwikkeling"
#
# Belangrijke opmerking: de "/" aan het einde van de permalink definitie is
# belangrijk. Als die ontbreekt moet de url wel de extensie ".html" bevatten.
collections:
    home:
        output: true
        permalink: /:name:output_ext
    activiteiten:
        output: true
        permalink: /:collection/:name/
    allerlei:
        output: true
        permalink: /:collection/:name/
    posts:
        output: true
        permalink: /:collection/:name/
    ontwikkeling:
        output: true
        permalink: /:collection/:name:output_ext
    drafts:
        output: false
        permalink: /:collection/:name/
~~~

De "activiteiten" collection bestaat uit de bronbestanden in de submap
"_activiteiten". De *permalink* definitie is "/:collection/:name/". Hierin
betekent ":collection" de naam van de collection en ":name" de filenaam van
het bronbestand maar zonder de extensie. Voor het bronbestand "biljart.md" in de
submap "_activiteiten" zal de URL dus "/activiteiten/biljart" worden. Dat betekent
dat Jekyll de webpagina zal wegschrijven in "_site" als
"_site/activiteiten/biljart/index.html".

Verder heb ik een permalink definitie op site niveau gezet in "_config.yml" die
van toepassing is voor de bronbestanden die in de hoofdmap staan:

~~~
permalink: /:basename/
~~~

[Terug naar inhoudstafel](#inhoud)

### Verslagen {#verslagen}

Verslagen maken gebruik van het Jekyll concept *posts*. Daarmee wordt eigenlijk
"blog posts" bedoeld. Het verschil tussen een gewone webpagina en een *post* is
het volgende.

Een post is een webpagina waarbij de datum belangrijk is. Het is bv. een
verslag over een gebeurtenis. Het is in ieder geval iets waarbij de datum waarop
het gepubliceerd wordt belangrijk is.

In een Jekyll project worden de bronbestanden van posts in de map "_posts"
geplaatst. Jekyll veronderstelt dat de volgende conventie wordt gevolgd
voor de naam van die bronbestanden:

YYYY-MM-DD-naam-van-het-verslag.md

Jekyll plaatst de daaruit gegenereerde webpagina standaard in

_site/YYYY/MM/DD/naam-van-het verslag.html

Door de hierboven gedefinieerde *permalink* voor de *posts* collection wordt dat
echter:

_site/posts/YYY-MM-DD-naam-van-het-verslag.html

De datum van het verslag is impliciet een front matter gegeven dat kan worden
gebruikt in Liquid met "page.date".

Jekyll biedt daarenboven nog de mogelijkheid om *tags* en *categories* toe te
kennen aan posts, maar dat heb ik tot nu toe nog niet gebruikt. Zie
<a href="https://jekyllrb.com/docs/posts/" target="_blank">Posts</a>
in de Jekyll documentatie.

[Terug naar inhoudstafel](#inhoud)
