# AAPS sur montres Wear OS

Vous pouvez installer l'application AndroidAPS sur votre montre connectée **Wear OS**. La version montre de AAPS vous permet de :

* **afficher les données sur votre montre** : en fournissant des [cadrans personnalisés](#aaps-watchfaces) ou dans des cadrans standards avec l'utilisation de [complications](#complications)
* **contrôler AAPS du téléphone** : pour faire un bolus, définir une cible temporaire, etc. 

### Avant d'acheter la montre...

* Certaines fonctions comme les *complications* nécessitent une version 2.0 ou plus récente de Wear OS
* Google a rebaptisé *Android Wear 1.x* en *Wear OS* depuis la version 2.x, donc quand il est indiqué *Android Wear* il est possible que ce soit une ancienne version 1.x du système
* Si la description indique seulement *Compatibilité avec Android* et *iOS* - cela **ne signifie pas** que la montre fonctionne sous *Wear OS* - cela peut tout à fait être une autre sorte de système d'exploitation spécifique au fournisseur **qui n'est pas compatible avec les cadrans AAPS !**
* Vérifiez la [liste des téléphones et des montres testés](../Getting-Started/Phones#list-of-tested-phones) et [demandez à la communauté](../Where-To-Go-For-Help/Connect-with-other-users.md) si vous avez un doute si votre montre sera prise en charge

### Construction de la version Wear OS d'AAPS

Pour compiler la version Wear OS de AAPS vous devez choisir la version "fullRelease" quans vous [générez l'APK](../Installing-AndroidAPS/Building-APK.md) (ou "pumpRelease" qui permet juste de contrôler à distance la pompe sans boucle).

Assurez vous que les deux versions de AAPS (téléphone et montre) sont signées avec la même clé !

Wear variant of APK need to be installed on watch in the same way you will install phone APK on phone. It may require enabling *developer mode* on watch and uploading and installing APK on watch with: `adb install wear-full-release.apk`

When using wear version of AAPS, always update it together with phone version of app - keep their versions in sync.

### Configuration sur le téléphone

Dans AndroidAPS, dans le Générateur de configuration, vous devez [activer Wear](../Configuration/Config-Builder#wear).

## Contrôler AAPS depuis la montre

AndroidAPS est conçu pour être *contrôlé* par les montres Android Wear. Si vous voulez commander AAPS depuis la montre (bolus etc) alors dans les "Paramètres Wear" vous devez activer "Commandes depuis la montre".

Les fonctions suivantes peuvent être déclenchées à partir de la montre :

* définir une cible temporaire
* administrer un bolus
* administrer des eGlucides
* utilisez le calculateur de bolus (les paramètres à prendre en compte dans le calculs peuvent être définis dans [Paramètres de l'Assistant](../Configuration/Config-Builder#wear) sur le téléphone)
* vérifier l'état de la boucle et de la pompe
* montrer le DTI (Dosage Total d'Insuline quotidien = bolus + basale par jour)

## Cadrans AAPS

Il y a plusieurs cadrans à choisir qui inclus le delta moyen, l'IA, le débit temporaire de basal actuel et les profils de basal + le graphique de lecture MGC.

Vérifiez que les notifications d'AndroidAPS ne sont pas bloquées sur la montre. La confirmation de l'action (par ex. bolus, cible temporaire) est envoyée par une notification que vous devrez glisser et cocher.

Pour accéder plus rapidement au menu AAPS, appuyez deux fois sur votre Gly. Avec un double appui sur la courbe Gly vous pouvez changer l'échelle de temps.

## Cadrans disponibles

![Cadrans disponibles](../images/Watchface_Types.png)

## Cadran AAPSv2 - Légende

![Légende du cadran AndroidAPSv2](../images/Watchface_Legend.png)

A - temps écoulé depuis le dernier calcul de la boucle

B - lecture du capteur MGC

C - nombre de minutes depuis la dernière lecture MGC

D - changement par rapport à la dernière lecture MGC (en mmol ou mg/dl)

E - variation moyenne des lectures MGC depuis 15 minutes

F - niveau de batterie du téléphone

G - débits de basal (en U/h ou en % pendant un DBT)

H - IG (BGI) Impact Glycémique -> l'augmentation ou diminution que "devrait" avoir la glycémie en fonction de l'activité de l'insuline seule.

I - glucides (glucides actifs | e-glucides à venir)

J - Insuline Active (de bolus | de basal)

## Accès menu principal de AAPS

Pour accéder au menu principal d'AAPS, vous pouvez utiliser les options suivantes :

* double appui sur votre valeur de glycémie
* sélectionnez l'icône AAPS dans les applications de la montre
* appuyez sur la complication AAPS (si configuré pour le menu)

## Paramètres (dans la montre)

Pour accéder aux paramètres du cadran, entrez dans le menu principal AAPS, faites glisser vers le haut et sélectionnez "Paramètres".

L'étoile remplie est pour l'état activé (**On**), et l'étoile vide indique que le paramètre est désactivé (**Off**) :

![Paramètres On/Off](../images/Watchface_Settings_On_Off.png)

### Paramètres du compagnon AAPS

* **Vibrer sur Bolus** (par défaut `Oui`):
* **Unités des Actions** (par défaut `mg/dl`) : si **On** l'unité des actions est `mg/dl`, si **Off** l'unité est `mmol/l`. Utilisé lors de la définition d'une CT à partir de la montre.

### Paramètres cadran

* **Afficher Date** (par défaut `Off`): remarque, la date n'est pas disponible sur tous les cadrans
* **Afficher IA** (par défaut `On`) : afficher ou non la valeur de l'IA (le paramétrage de l'affichage des valeurs détaillées est dans les paramètres Wear du Générateur de configurations de AAPS)
* **Afficher GA** (par défaut `On`) : afficher ou non la valeur GA
* **Afficher Delta** (par défaut `On`) : afficher ou non la variation de Gly des 5 dernières minutes
* ** Afficher Delta Moyen** (par défaut `On`) : afficher ou non la variation moyenne des Gly des 15 dernières minutes
* **Afficher Batterie Téléphone** (par défaut `On`) : batterie du téléphone en %. Rouge si en dessous de 30%.
* **Afficher Batterie Système** (par défaut `Off`) : la batterie système est une synthèse de la batterie du Téléphone, de la pompe et de la pile du capteur (en général la plus faible des 3 valeurs)
* **Afficher Basale** (par défaut `On`) : afficher ou non le débit de basal (en U/h ou en % si DBT)
* **Afficher État Boucle** (par défaut `On`) : afficher ou non le nombre de minutes depuis le dernier calcul de boucle (les flèches autour de la valeur deviennent rouge si au-dessus de 15').
* **Afficher Glycémie** (par défaut `On`) : afficher ou non la dernière valeur de glycémie
* **Afficher flèche** (par défaut `On`) : afficher ou non la flèche de tendance Gly
* **Afficher Min Passées** (par défaut `On`) : afficher ou non le nombre de minutes depuis la dernière lecture.
* **Sombre** (par défaut `On`) : Vous pouvez changer l'arrière plan du cadran de noir à blanc (sauf pour les cadrans Cockpit et Steampunk)
* **Surbrillance Basale** (par défaut `Off`) : Améliorer la visibilité des débits de basal et basales temporaires
* **Séparateur** (par défaut `Off`) : pour les cadrans AAPS, AAPSv2 et AAPS(Large), affiche le fond du séparateur contrasté avec l'arrière plan (**Off**) ou de la même couleur que l'arrière plan (**On**)
* **Echelle Graphique** (par défaut `3 heures`) : vous pouvez sélectionner dans le sous-menu de la durée max de votre graphique entre 1 heure et 5 heures.

### Paramètre Interface Utilisateur

* **Design de saisie** : avec ce parametre, vous pouvez sélectionner la position des boutons "+" et "-" quand vous entrez des commandes pour AAPS (CT, Insuline, Glucides...)

![Options interfaces d'entrée](../images/Watchface_InputDesign.png)

### Paramètres spécifiques à certains cadrans

#### Cadran Steampunk

* **Précision Delta** (par défaut `Moyenne`)

![Jauge Steampunk](../images/Watchface_Steampunk_Gauge.png)

#### Cadran Cercle

* **Gros chiffres** (par défaut `Off`) : Augmenter la taille du texte pour améliorer la visibilité
* **Historique** (par défaut `Off`) : Afficher graphiquement l'historique des Gly avec des cercles gris à l'intérieur de l'anneau vert de l'heure
* **Historique Léger** (par défaut `On`) : cercles plus discrets avec un gris foncé
* **Animations** (par défaut `On`) : Si activé, sur les montres supportée et hors mode économie d'énergie basse résolution, le cercle du cadran est animé

### Paramètres des commandes

* **Assistant dans Menu** (par défaut `On`) : Autoriser l'action Assistant dans le menu principal pour renseigner les Glucides et faire des Bolus à partir de la montre
* **Amorcer dans Menu** (par défaut `Off`) : Autoriser l'action Amorcer/Remplir à partir de la montre
* **Cible unique** (par défaut `On`):
  
  * `On` : vous définissez une valeur unique pour une CT
  * `Off`: vous définissez une cible basse et haute pour une CT

* **Assistant Pourcentage** (par défaut `Off`) : Autoriser la correction du bolus à partir de l'assistant (valeur saisie en pourcentage avant la confirmation)

## Complications

La *complication* est un terme issu de l'horlogerie traditionnelle, il décrit l'ajout à la montre principale d'une autre petite fenêtre ou sous-cadran (avec date, jour de la semaine, phase lunaire, etc.). Wear OS 2. apporte cette métaphore pour permettre aux fournisseurs de données personnalisés, comme la météo, les notifications, compteurs de fitness et plus encore, d'ajouter ces informations à tous les cadrans qui supportent les complications.

AndroidAPS Wear OS prend en charge les complications depuis la version `2.6`, et permet à tout les cadrans qui supporte les complications d'être configuré pour afficher les données liées à AAPS (Gly avec tendance, IA, GA, etc.).

Les complications servent également de **raccourci** aux fonctions AAPS. En appuyant dessus, vous pouvez ouvrir les menus et dialogues de AAPS (selon la complication et la configuration).

![Complication sur les cadrans](../images/Watchface_Complications_On_Watchfaces.png)

### Types de Complication

AAPS Wear OS ne fournit que des données brutes, selon les formats prédéfinis. Il revient au cadran récepteur de décider où et comment mettre en forme les complications, y compris sa mise en page, sa bordure, sa couleur et sa police. Parmi les nombreux types de complications Wear OS disponibles, AAPS utilise :

* `TEXTE COURT` - Contient deux lignes de texte, 7 caractères chacune, parfois appelés valeur et étiquette. Il est généralement affiché à l'intérieur d'un cercle ou d'une petite pilule - l'un au-dessous de l'autre, ou côte à côte. C'est une complication très compacte. AAPS essaye de supprimer les caractères inutiles pour l'ajuster : en arrondissant les valeurs, en supprimant les zéros de début et de fin des valeurs, etc.
* `TEXTE LONG` - Contient deux lignes de texte, d'environ 20 caractères chacune. Il est généralement affiché à l'intérieur d'un rectangle ou d'une longue pilule - l'une en dessous d'un autre. Il est utilisé pour plus de détails et des statuts textuels.
* `PLAGE DE VALEUR` - Utilisée pour les valeurs d'une plage prédéfinie, comme un pourcentage. It contains icon, label and is usually rendered as circle progress dial.
* `GRANDE IMAGE` - Image d'arrière-plan personnalisée qui peut être utilisée (si pris en charge par le cadran) en arrière-plan.

### Paramètres des complications

Pour ajouter une complication à un cadran, configurez-le par un appui long et cliquez sur la roue crantée en dessous. Selon la façon dont s'effectue le paramétrage du cadran - soit cliquez sur les espaces réservés, soit entrez dans le menu de paramétrage des complications du cadran. Les complications de AAPS sont regroupées dans le sous-menu AAPS.

Quand vous configurez les complications dans un cadran, Wear OS présente et filtre la liste des complications qui sont adaptées à la zone sélectionnée dans le cadran. Si certaines complications ne sont pas dans la liste, c'est probablement parce qu'elle ne peut pas être utilisée à cet endroit.

### Complications fournies par AAPS

AndroidAPS fournit les complications suivantes :

![Liste des complications AAPS](../images/Watchface_Complications_List.png)

* **Gly, GA & IA** (`TEXTE COURT`, ouvre *Menu*) : Affiche *Débit de Basal* sur la première ligne et *Glucides Actifs* et *Insuline Active* sur la deuxième ligne.
* **Glycémie** (`TEXTE COURT`, ouvre *Menu*) : Affiche la valeur de la*Glycémie* et la flèche de *tendance* sur la première ligne et *l'âge de la mesure* et le *delta Gly* sur la deuxième ligne.
* ** GA & IA ** (`TEXTE COURT`, ouvre *Menu*) : affiche * Glucides Actifs* sur la première ligne et *Insuline Active* sur la deuxième ligne.
* **GA Détaillé** (`TEXTE COURT`, ouvre *Assistant*) : affiche la valeur courante de *Glucides Actifs* sur la première ligne et les glucides planifiés (Glucides étendus à venir) sur la deuxième ligne.
* **Icone GA** (`TEXTE COURT`, ouvre *Assistant*) : affiche la valeur de *Glucides Actifs* avec une icône statique.
* **Statut Complet** (`TEXTE LONG`, ouvre *Menu*) : Indique que la plupart des données en même temps : *Glycémie* et flèche de *tendance*, *Delta Gly* et *âge de la mesure* sur la première ligne. Sur la deuxième ligne *Glucides Actifs*, *Insuline Active* et * Débit de basal*.
* **Statut Complet (inversé)** (`TEXTE LONG`, ouvre *Menu*) : Même données que pour le *Statut Complet *, mais les lignes sont inversées. Peut être utilisé dans certains cadrans qui ignorent l'une des deux lignes dans les `TEXTE LONG`
* ** IA Détaillé** (`TEXTE COURT`, ouvre *Bolus*) : Affiche l'*Insuline Active* totale sur la première ligne et la part d'*IA* pour le *Bolus* et la *Basale* sur la deuxième ligne.
* ** Icone IA** (`TEXTE COURT`, ouvre *Bolus*) : Affiche la valeur *Insuline Active* avec une icône statique.
* ** Batterie du téléphone** (`PLAGE DE VALEURS`, ouvre * Etats*) : Affiche le pourcentage de batterie du téléphone AAPS, tel que signalé par AAPS. Affichée avec une jauge de pourcentage avec de l'icône de la batterie qui reflète la valeur envoyée. Il peut ne pas être mis à jour en temps réel, mais lorsque d'autres données importantes de AAPS changent (en général: toutes les ~ 5 minutes avec une nouvelle mesure de *Glycémie*).

De plus, il y a trois complications de type `IMAGE LARGE` : **Fond d'écran noir**, **fond d'écran gris** et **fond d'écran clair**, affichant une image AAPS statique.

### Paramètres des complications

* **Action Appui Complication** (par défaut `Défaut`) : Décide de l'action qui s'ouvre lorsque l'utilisateur appui sur la Complication : 
  * *Défaut* : action spécifique à chaque complication *(voir la liste ci-dessus)*
  * *Menu* : menu principal AAPS
  * *Assistant* : assistant bolus - calculateur bolus
  * *Bolus* : Bolus et glucides saisis directement
  * *eGlucides* : boîte de dialogue de configuration eGlucides
  * *Etats* : sous-menu d'états
  * *Aucun* : Désactive l'action sur les complications AAPS
* **Unicode dans Complications** (par défaut `On`) : Si `On`, la complication utilise des caractères Unicode pour les symboles tels que `Δ` Delta, `⁞` séparateur de point vertical ou `⎍` symbole du débit de basal. Le rendu de ces symboles dépend de la police, et cela peut être très spécifique au cadran. Cette option permet de désactiver les symboles `Unicode` quand c'est nécessaire - si la police utilisée par le cadran personnalisé ne prend pas en charge ces symboles - pour éviter les problèmes graphiques.

## Conseils sur les performances et la durée de vie des batteries

Wear OS watches are very power-constrained devices. The size of the watch case limits the capacity of the included battery. Even with recent advancements both on hardware and software side, Wear OS watches still require daily charging.

If an experienced battery span is shorter than a day (from dusk to dawn), here are some tips to troubleshoot the issues.

Main battery-demanding areas are:

* Active display with a backlight on (for LED) or in full intensity mode (for OLED)
* Rendering on screen
* Radio communication over Bluetooth

Since we cannot compromise on communication (we need up-to-date data) and want to have the most recent data rendered, most of the optimizations can be done in *display time* area:

* Stock watchfaces are usually better optimized than custom one, downloaded from the store.
* It is better to use watchfaces that limit the amount of rendered data in inactive / dimmed mode.
* Be aware when mixing other Complications, like third party weather widgets, or other - utilizing data from external sources.
* Start with simpler watchfaces. Add one complication at the time and observe how they affect battery life.
* Try to use **Dark** theme for AAPS watchfaces, and [**Matching divider**](#watchface-settings). On OLED devices it will limit the amount of pixels lit and limit burnout.
* Check what performs better on your watch: AAPS stock watchfaces or other watchfaces with AAPS Complications.
* Observe over a few days, with different activity profiles. Most watches activate the display on glancing, movement and other usage-related triggers.
* Check your global system settings that affect performance: notifications, backlight/active display timeout, when GPS is activated.
* Check [list of tested phones and watches](../Getting-Started/Phones#list-of-tested-phones) and [ask community](../Where-To-Go-For-Help/Connect-with-other-users.md) for other users experiences and reported battery lifetime.
* **We cannot guarantee that data displayed on watchface or complication is up-to-date**. In the end, it is up to Wear OS to decide when to update a watchface or a complication. Even when the AAPS app requests update, the System may decide to postpone or ignore updates to conserve battery. When in doubt and low on battery on watch - always double-check with main AAPS app on phone.

## Dépannage de l'application wear :

* Sur Android Wear 2.0, le cadran de la montre ne s'installe plus tout seul. Vous devez aller dans le playstore sur la montre (pas le même playstore que celui du téléphone) et le trouver dans la catégorie applications installées sur votre téléphone, à partir de là, vous pouvez l'activer. Activer également les mises à jour automatiques 
* Parfois, cela peut aider de resynchroniser AAPS avec la montre car cela peut être un peu lent quand il le fait tout seul : Wear / Renvoyer toutes les données
* Enable ADB debugging in Developer Options (on watch), connect the watch via USB and start the Wear app once in Android Studio.
* If Complications does not update data - check first if AAPS watchfaces work at all.

## Afficher les données Nightscout

Si vous utilisez un autre système de bouclage et que vous voulez *voir* le détail de la boucle sur une montre Android Wear, ou si vous voulez regarder la boucle de votre enfant, vous pouvez juste construire/télécharger le fichier APK NSClient. Pour ce faire, suivez les instructions [construire l'APK](../Installing-AndroidAPS/Building-APK.md) en sélectionnant la variante de génération "NSClientRelease". Il y a plusieurs cadrans à choisir qui inclus le delta moyen, l'IA, le débit temporaire de basal actuel et les profils de basal + le graphique de lecture MGC.

# Pebble

Pebble users can use the [Urchin watchface](https://github.com/mddub/urchin-cgm) to *view* looping data (if uploaded to Nightscout), but you will not be able to interact with AndroidAPS through the watch. You can choose fields to display such as IOB and currently active temp basal rate and predictions. If open looping you can use [IFTTT](https://ifttt.com/) to create an applet that says if Notification received from AndroidAPS then send either SMS or pushover notification.