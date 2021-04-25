---
title: Connectivité réseau dans le Centre d'administration Microsoft 365 (prévisualisation)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
description: Vue d'ensemble de la connectivité réseau dans le Centre d'administration Microsoft 365 (aperçu)
ms.openlocfilehash: c3ce053ecc859d3ac0cf53b0a132a7032ce6a87a
ms.sourcegitcommit: f000358c01a8006e5749a86b256300ee3a73174c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51994676"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center-preview"></a>Connectivité réseau dans le Centre d'administration Microsoft 365 (prévisualisation)

Le Centre d'administration Microsoft 365 inclut désormais des mesures agrégées de connectivité réseau collectées auprès de votre client Microsoft 365 et disponibles uniquement pour les utilisateurs administratifs de votre client.

> [!div class="mx-imgBorder"]
> ![Outil de test de connectivité réseau](../media/m365-mac-perf/m365-mac-perf-admin-center.png)

**Les évaluations réseau** et les informations réseau sont **affichées** dans le Centre d'administration Microsoft 365 sous **Informations | Connectivité**.

> [!div class="mx-imgBorder"]
> ![Page Performances du réseau](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

>[!NOTE]
>L'outil de test de connectivité réseau prend en charge les clients de WW Commercial et d'Allemagne, mais pas GCC Moderate, GCC High, DoD ou China.

Lorsque vous accédez pour la première fois à la page de performances réseau, vous voyez un volet de vue d'ensemble contenant une carte des performances globales du réseau, une évaluation réseau étendue à l'ensemble du client et une liste des problèmes actuels. À partir de la vue d'ensemble, vous pouvez descendre dans le détail pour afficher des mesures et des problèmes de performances réseau spécifiques par emplacement. Pour plus d'informations, voir vue d'ensemble des performances réseau dans le Centre d'administration [Microsoft 365.](#network-connectivity-overview-in-the-microsoft-365-admin-center)

Vous pouvez être invité à participer à la prévisualisation publique pour cette fonctionnalité au nom de votre organisation. L'acceptation se produit généralement immédiatement, après quoi vous voyez la page de connectivité réseau. 

Lors de la navigation vers la page de connectivité réseau, vous verrez un volet de vue d'ensemble contenant une carte des performances globales du réseau, une évaluation réseau étendue à l'ensemble du client, un pourcentage de vos utilisateurs travaillant à distance par rapport au site, ainsi qu'une liste des problèmes actuels pour prendre des mesures ou pour poursuivre la recherche. Pour accéder à cette page, vous devez être administrateur de l'organisation dans Microsoft 365. Le rôle d'administration lecteur de rapports aura un accès en lecture à ces informations. Pour configurer des emplacements et d'autres éléments de connectivité réseau, un administrateur doit faire partie d'un rôle d'administrateur de serveur tel que le rôle d'administrateur de support technique du service. À partir de la vue d'ensemble, vous pouvez descendre dans le détail pour afficher des mesures et des problèmes de performances réseau spécifiques par emplacement. 

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Conditions préalables à l'apparition des évaluations de la connectivité réseau

To get started, turn on your location opt-in setting to automatically collect data from devices using Windows Location Services, go to your Locations list to add or upload location data, or run the Microsoft 365 network connectivity test from your office locations. La connectivité réseau peut être évaluée au sein de l'organisation, toute amélioration de la conception réseau devra être effectuée pour des emplacements de bureau spécifiques. Les informations de connectivité réseau sont fournies pour chaque emplacement de bureau une fois ces emplacements déterminés. Il existe trois options pour obtenir des évaluations réseau à partir de vos bureaux :

### <a name="1-enable-windows-location-services"></a>1. Activer les services de localisation Windows

Pour cette option, vous devez avoir au moins deux ordinateurs en cours d'exécution à chaque emplacement de bureau qui prendre en charge les conditions préalables. La version de OneDrive pour Windows doit être à jour et installée sur chaque ordinateur. Pour plus d'informations sur les versions de OneDrive, voir les [notes de publication de OneDrive.](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0) Des mesures réseau seront bientôt ajoutées à d'autres applications clientes Office 365.

Le service d'emplacement Windows doit être accepté sur les ordinateurs. Vous pouvez le tester en exécutant l'application **Cartes** et en vous localisant vous-même. Il peut être activé sur un seul ordinateur avec **paramètres | Confidentialité | Emplacement** où le paramètre _Autoriser les applications à accéder à_ votre emplacement doit être activé. Le consentement des services d'emplacement Windows peut être déployé sur des PC à l'aide de la gestion des appareils de gestion des appareils de gestion des appareils ou de la stratégie de groupe avec le paramètre _LetAppsAccessLocation_.

Il n'est pas nécessaire d'ajouter des emplacements dans le Centre d'administration avec cette méthode, car ils sont automatiquement identifiés au niveau de la résolution de la ville. Vous ne pouvez pas afficher plusieurs bureaux dans une ville à l'aide des services d'emplacement Windows. Les informations d'emplacement sont également arrondies aux 300 mètres les plus proches sur 300 mètres avant d'être téléchargées afin que les informations d'emplacement plus précises ne sont pas accessibles.

Les ordinateurs doivent avoir Wi-Fi réseau au lieu d'un câble ethernet. Les ordinateurs avec un câble ethernet n'ont pas d'informations précises sur l'emplacement.

Les exemples de mesure et les emplacements de bureau doivent commencer à apparaître 24 heures après que ces conditions préalables ont été remplies.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. Ajouter des emplacements et fournir des informations sur le sous-réseau laN

Pour cette option, ni les services d'emplacement Windows Wi-Fi ne sont requis. Votre version de OneDrive pour Windows doit être à jour et installée sur au moins un ordinateur à l'emplacement.

Vous devez également ajouter des emplacements dans la **page Emplacements** ou les importer à partir d'un fichier CSV. Les emplacements ajoutés doivent inclure les informations de votre sous-réseau local office.

Cette option vous permet de définir plusieurs bureaux dans une ville.

Toutes les mesures de test des ordinateurs clients incluent les informations du sous-réseau local, qui sont corrélées avec les détails de l'emplacement du bureau que vous avez entrés. Les exemples de mesure et les emplacements de bureau doivent commencer à apparaître 24 heures après que ces conditions préalables ont été remplies.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. Collecter manuellement des rapports de test avec l'outil de test de connectivité réseau Microsoft 365

Pour cette option, vous devez identifier une personne à chaque emplacement. Demandez-leur d'utiliser le test de connectivité réseau [Microsoft 365](https://connectivity.office.com) sur un ordinateur Windows sur lequel ils ont des autorisations administratives. Sur le site web, ils doivent se connectent à leur compte Office 365 pour la même organisation que celle dont vous souhaitez voir les résultats. Ensuite, ils doivent cliquer **sur Exécuter le test.** Pendant le test, il existe un exE de test de connectivité téléchargé. Ils doivent ouvrir et exécuter cette opération. Une fois les tests terminés, les résultats du test sont téléchargés vers le Centre d'administration.

Les rapports de test sont liés à un emplacement s'il a été ajouté avec des informations de sous-réseau laN, sinon ils sont affichés uniquement à l'emplacement de la ville.

Les échantillons de mesure et les emplacements de bureau doivent commencer à apparaître 2 à 3 minutes après la fin d'un rapport de test. Pour plus d'informations, voir Test de connectivité réseau [Microsoft 365 (prévisualisation).](office-365-network-mac-perf-onboarding-tool.md)

## <a name="how-do-i-use-this-information"></a>Comment utiliser ces informations ?

**Les informations sur le réseau,** leurs recommandations en matière de performances associées et les évaluations réseau sont conçues pour vous aider à concevoir des périmètres réseau pour vos bureaux. Chaque aperçu fournit des détails sur les caractéristiques de performances d'un problème réseau commun spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre client. **Les recommandations de performances** pour chaque aperçu réseau proposent des modifications spécifiques à la conception de l'architecture réseau que vous pouvez apporter pour améliorer l'expérience utilisateur liée à la connectivité réseau Microsoft 365. L'évaluation du réseau montre l'impact de la connectivité réseau sur l'expérience utilisateur, ce qui permet de comparer les différentes connexions réseau d'emplacement utilisateur.

**Les évaluations réseau** regroupent de nombreuses mesures de performances réseau dans un instantané de l'état de votre réseau d'entreprise, représenté par une valeur de points de 0 à 100. Les évaluations réseau sont limitées à l'ensemble du client et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre client, offrant aux administrateurs Microsoft 365 un moyen simple de saisir instantanément un gestalt de l'état du réseau de l'entreprise et d'obtenir rapidement un rapport détaillé pour n'importe quel emplacement de bureau global.

Les entreprises complexes avec plusieurs bureaux et des architectures de périmètre réseau non triviales peuvent tirer parti de ces informations lors de leur intégration initiale à Microsoft 365 ou pour résoudre les problèmes de performances réseau détectés avec la croissance de l'utilisation. Cela n'est généralement pas nécessaire pour les petites entreprises qui utilisent Microsoft 365 ou les entreprises qui ont déjà une connectivité réseau simple et directe. Les entreprises de plus de 500 utilisateurs et de plusieurs bureaux devraient en tirer le meilleur parti.

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le Centre d'administration Microsoft 365 sont actuellement en état de prévisualisation et sont uniquement disponibles pour les clients Microsoft 365 qui ont été inscrits au programme d'aperçu des fonctionnalités.

## <a name="enterprise-network-connectivity-challenges"></a>Défis de connectivité réseau d'entreprise

> [!div class="mx-imgBorder"]
> ![Réseau client vers le cloud](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

De nombreuses entreprises ont des configurations de périmètre réseau qui ont évolué au fil du temps et sont principalement conçues pour prendre en charge l'accès au site web Internet des employés, où la plupart des sites web ne sont pas connus à l'avance et ne sont pas sécurisés. L'objectif le plus indispensable est d'éviter les programmes malveillants et les attaques par hameçonnage à partir de ces sites web inconnus. Cette stratégie de configuration réseau, bien qu'utile à des fins de sécurité, peut entraîner une dégradation des performances et de l'expérience utilisateur de Microsoft 365.

## <a name="how-we-can-solve-these-challenges"></a>Comment pouvons-nous résoudre ces défis ?

Les entreprises peuvent améliorer l'expérience utilisateur générale et sécuriser leur environnement en suivant les principes de connectivité [d'Office 365](./microsoft-365-network-connectivity-principles.md) et en utilisant la fonctionnalité de connectivité réseau du Centre d'administration Microsoft 365. Dans la plupart des cas, le fait de suivre ces principes généraux aura un impact positif significatif sur la latence des utilisateurs finaux, la fiabilité du service et les performances globales de Microsoft 365.

Microsoft est parfois invité à examiner les problèmes de performances réseau liés à Microsoft 365 pour les clients grandes entreprises, et ceux-ci ont souvent une cause première liée à l'infrastructure de périmètre du réseau du client. Lorsqu'une cause première courante d'un problème de périmètre de réseau client est trouvée, nous cherchons à identifier des mesures de test simples qui l'identifient. Un test avec un seuil de mesure qui identifie un problème spécifique est utile, car nous pouvons tester la même mesure à n'importe quel emplacement, déterminer si cette cause première est présente et la partager en tant qu'informations réseau avec l'administrateur.

Certaines informations sur le réseau indiquent simplement un problème qui doit faire l'objet d'un examen plus approfondie. Une information réseau dans laquelle nous avons suffisamment de tests pour afficher une action de correction spécifique pour corriger la cause première est répertoriée comme **une action recommandée.** Ces recommandations, basées sur des mesures dynamiques qui révèlent des valeurs situées en dehors d'un seuil prédéterminé, sont beaucoup plus utiles que les conseils généraux des meilleures pratiques, car elles sont propres à votre environnement et montrent l'amélioration réelle une fois que les modifications recommandées ont été apportées.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Vue d'ensemble de la connectivité réseau dans le Centre d'administration Microsoft 365

Microsoft dispose de mesures réseau existantes à partir de plusieurs clients office de bureau et web qui prendre en charge le fonctionnement de Microsoft 365. Ces mesures sont désormais utilisées pour fournir des informations sur la conception de l'architecture réseau et une évaluation du réseau qui sont affichées dans la **page** Connectivité réseau du Centre d'administration Microsoft 365.

Par défaut, les informations d'emplacement approximatives associées aux mesures réseau identifient la ville où se trouvent les appareils clients. L'évaluation réseau à chaque emplacement est affichée avec la couleur et le nombre relatif d'utilisateurs à chaque emplacement est représenté par la taille du cercle.

> [!div class="mx-imgBorder"]
> ![Carte de vue d'ensemble des informations réseau](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

La page vue d'ensemble présente également l'évaluation réseau pour le client sous la mesure d'une moyenne pondérée dans tous les bureaux.

> [!div class="mx-imgBorder"]
> ![Évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

Vous pouvez afficher une vue de table des emplacements où ils peuvent être filtrés, triés et modifiés dans l'onglet **Emplacements.** Les emplacements avec des recommandations spécifiques peuvent également inclure une amélioration potentielle estimée de la latence. Cette valeur est calculée en prenant la latence médiane des utilisateurs de votre organisation à l'emplacement et en soustrayant la latence médiane pour toutes les organisations dans la même ville.

> [!div class="mx-imgBorder"]
> ![Emplacements d'informations réseau](../media/m365-mac-perf/m365-mac-perf-locations.png)

## <a name="remote-worker-assessment-and-user-connection-metrics"></a>Mesures de l'évaluation du travail à distance et de la connexion utilisateur

Nous classons les journaux de trafic réseau en tant qu'utilisateurs distants ou sur site et afficheons leurs pourcentages dans la section mesures de connexion utilisateur du volet vue d'ensemble. Pour les villes où vous avez des utilisateurs distants, vous trouverez le score d'évaluation du réseau distant spécifique à l'emplacement lorsque vous ouvrez la page de cet emplacement. La liste des emplacements aura à la fois des bureaux et des villes de travail à distance, qui peuvent être filtrés et triés. Nous fournissons le score d'évaluation des travailleurs à distance, avec répartition des points pour Exchange, SharePoint et Teams.

Les informations sur la mise en réseau des particuliers sont regroupées et signalées au niveau de la ville et limitées aux villes avec un minimum de 5 employés distants. Nous n'identifions pas les employés individuels travaillant à domicile.

Les emplacements sont classés automatiquement sur site ou à distance. Toutefois, vous avez la possibilité d'entrer manuellement toutes vos adresses IP de sortie sur site pour garantir une classification à 100 %. Si vous décidez d'accéder à cet itinéraire, vous devez cocher manuellement la case à cocher Entrer toutes les **adresses IP** de sortie sur site dans le volant Paramètres des emplacements après avoir ajouté toutes vos adresses IP de sortie. Une fois cette étape effectuée, tous les journaux de trafic réseau provenant d'adresses IP de sortie que vous avez marquées comme étant sur site seront toujours classés en tant que bureaux et toutes les autres adresses IP de sortie seront classées comme adresses IP distantes.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Synthèse et informations sur les performances réseau de l'emplacement des bureaux spécifiques

La sélection d'un emplacement de bureau ouvre une page récapitulatif propre à un emplacement affichant les détails de la sortie réseau identifiée à partir des mesures de cet emplacement.

> [!div class="mx-imgBorder"]
> ![Informations réseau détaillées par emplacement](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

Une carte du réseau de périmètre pour les utilisateurs de votre organisation à l'emplacement est affichée avec tout ou partie de ces éléments :

- **Emplacement du bureau** : emplacement du bureau pour la page que vous regardez
- **Périmètre réseau** : emplacement de l'adresse IP source pour les connexions à partir de l'emplacement du bureau. Cela dépend de la précision des bases de données d'emplacements ip géographiques
- **Porte d'entrée du service** Exchange optimale : l'une des portes d'entrée du service Exchange recommandées à qui les utilisateurs de cet emplacement de bureau doivent se connecter
- **Porte d'entrée d'Exchange sous-optimale** : une porte d'entrée du service Exchange à qui les utilisateurs sont connectés, mais qui n'est pas recommandée
- **Porte d'entrée du service SharePoint** optimale : l'une des porte d'entrée de service SharePoint recommandées à qui les utilisateurs de cet emplacement de bureau doivent se connecter
- **Porte d'entrée du service SharePoint sous-optimale** : une porte d'entrée du service SharePoint à qui les utilisateurs sont connectés, mais qui n'est pas recommandée
- Serveur de résolution récursive **DNS** : emplacement à partir d'une base de données IP géographique du résolveur récursif DNS détecté utilisé pour Exchange Online (si disponible)
- **Votre serveur proxy :** emplacement à partir d'une base de données IP géographique du serveur proxy détecté (si disponible) 

La page récapitulatif de l'emplacement du bureau affiche également l'évaluation réseau de l'emplacement, l'historique de l'évaluation du réseau, une comparaison de l'évaluation de cet emplacement avec d'autres clients de la même ville, ainsi qu'une liste d'informations et de recommandations spécifiques que vous pouvez entreprendre pour améliorer les performances et la fiabilité du réseau.

Les comparaisons entre les clients d'une même ville sont basées sur l'attente que tous les clients ont un accès égal aux fournisseurs de services réseau, à l'infrastructure de télécommunications et aux points de présence réseau Microsoft à proximité.

Les noms d'emplacement peuvent être personnalisés lors de l'ajout d'un nouvel emplacement ou de la modification d'un emplacement existant dans le flyout d'emplacement. Cela vous offre la possibilité de personnaliser vos noms d'emplacement à tout moment. En outre, lorsque vous ajoutez des sous-réseaux LAN directement dans le volant d'emplacements, nous montrons une liste de listes de sous-réseaux LAN de correspondances soft que vous pouvez sélectionner. Les noms de circuits pour des adresses IP de sortie d'office spécifiques peuvent également être ajoutés et modifiés.

L'onglet Détails de la page d'emplacement du bureau affiche les résultats de mesure spécifiques qui ont été utilisés pour obtenir des informations, des recommandations et l'évaluation du réseau. Cela permet aux ingénieurs réseau de valider les recommandations et de prendre en compte les contraintes ou les spécificités de leur environnement. Vous trouverez également le nombre estimé d'utilisateurs pour les échantillons collectés dans ces bureaux, ainsi que les travailleurs à distance dans cette ville.

> [!div class="mx-imgBorder"]
> ![Détails spécifiques à l'emplacement](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)


## <a name="sharing-network-assessment-data-with-microsoft"></a>Partage des données d'évaluation du réseau avec Microsoft

Par défaut, les évaluations réseau de votre organisation et les informations réseau sont partagées avec les employés de Microsoft. Cela n'inclut pas les données personnelles de votre personnel, mais uniquement les mesures d'évaluation réseau spécifiques et les informations réseau affichées dans le Centre d'administration pour vos bureaux. Il n'inclut pas non plus les noms de vos bureaux ou adresses postales. Vous devez donc leur indiquer la ville et l'ID de support du bureau dont vous souhaitez discuter. Si cette information est désactivée, les ingénieurs Microsoft avec qui vous discutez de votre connectivité réseau ne peuvent pas afficher ces informations. L'activation de ce paramètre ne partage que les données futures à compter du jour suivant son activation.

## <a name="csv-import-for-lan-subnet-office-locations"></a>Importation CSV pour les emplacements de bureau de sous-réseau local

Pour l'identification des bureaux de sous-réseau local, vous devez ajouter chaque emplacement à l'avance. Au lieu d'ajouter des emplacements de bureau individuels dans l'onglet **Emplacements,** vous pouvez les importer à partir d'un fichier CSV. Vous pourrez peut-être obtenir ces données à partir d'autres emplacements que vous avez stockés, tels que le Tableau de bord de qualité des appels ou les sites et services Active Directory.

Dans le fichier CSV, un emplacement de ville découvert apparaît dans la colonne userEntered comme vide, et un emplacement de bureau ajouté manuellement indique 1.

1. Dans la fenêtre _principale Connectivité à Microsoft 365,_ cliquez sur **l'onglet** Emplacements.

1. Cliquez sur le **bouton Importer** juste au-dessus de la liste des emplacements. Le **volant Importer les emplacements** des bureaux s'affiche.

   > [!div class="mx-imgBorder"]
   > ![Message d'importation CSV](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Cliquez sur le lien Télécharger les emplacements du bureau **actuel (.csv)** pour exporter la liste des emplacements actuels vers un fichier CSV et enregistrez-le sur votre disque dur local. Cela vous fournira un fichier CSV correctement formaté avec des en-tête de colonne à laquelle vous pouvez ajouter des emplacements. Vous pouvez laisser les emplacements exportés existants tels qu'ils sont ; Elles ne seront pas dupliquées lorsque vous importez le CSV mis à jour. Si vous souhaitez modifier l'adresse d'un emplacement existant, elle sera mise à jour lorsque vous importez le CSV. Vous ne pouvez pas modifier l'adresse d'une ville découverte.

1. Ouvrez le CSV et ajoutez vos emplacements en remplissant les champs suivants sur une nouvelle ligne pour chaque emplacement que vous souhaitez ajouter. Laissez tous les autres champs vides ; les valeurs que vous entrez dans d'autres champs seront ignorées.

   1. **userEntered** (obligatoire) : doit être 1 pour un nouvel emplacement de bureau de sous-réseau local en cours d'ajout
   1. **Nom** (obligatoire) : nom de l'emplacement du bureau
   1. **Adresse** (obligatoire) : adresse physique du bureau
   1. **Latitude** (facultatif) : rempli à partir de bing cartes recherche de l'adresse si vide
   1. **Longitude** (facultative) : remplie à partir de bing cartes recherche de l'adresse si vide
   1. Sortie des **plages d'adresses IP 1 à 5** (facultatives) : pour chaque plage, entrez le nom du circuit suivi d'une liste séparée par des espaces d'adresses CIDR IPv4 ou IPv6 valides. Ces valeurs sont utilisées pour différencier plusieurs emplacements de bureau où vous utilisez les mêmes adresses IP de sous-réseau local. Les plages d'adresses IP de sortie doivent toutes être de /24 taille réseau et le /24 n'est pas inclus dans l'entrée.
   1. **LanIps** (obligatoire) : rép.des plages de sous-réseaux LAN en cours d'utilisation à cet emplacement de bureau. Les ID de sous-réseau local doivent avoir une taille de réseau CIDR incluse, où la taille du réseau peut être comprise entre /8 et /29. Plusieurs plages de sous-réseaux LAN peuvent être séparées par une virgule ou un point-virgule.
   
1. Une fois que vous avez ajouté vos emplacements de bureau  et enregistré le fichier, cliquez sur le bouton Parcourir en haut du champ Télécharger le champ terminé et sélectionnez le fichier CSV enregistré. 

1. Le fichier est automatiquement validé. S'il existe des erreurs de validation, vous verrez le message d'erreur : Il existe certaines _erreurs dans le fichier d'importation. Examinez les erreurs, corrigez le fichier d'importation, puis réessayez._ Cliquez sur le lien **Ouvrir les détails de l'erreur** pour obtenir la liste des erreurs de validation de champ spécifiques.

   > [!div class="mx-imgBorder"]
   > ![Message d'erreur d'importation CSV](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. S'il n'y a aucune erreur dans le fichier, vous verrez le message : _Le rapport est prêt. Emplacements x trouvés à ajouter et x emplacements à mettre à jour._ Cliquez sur **le bouton** Importer pour télécharger le CSV.

   > [!div class="mx-imgBorder"]
   > ![Message prêt à l'importation CSV](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>FAQ

### <a name="what-is-a-microsoft-365-service-front-door"></a>Qu'est-ce qu'une porte d'entrée du service Microsoft 365 ?

La porte d'entrée du service Microsoft 365 est un point d'entrée sur le réseau mondial de Microsoft où les clients et services Office terminent leur connexion réseau. Pour une connexion réseau optimale à Microsoft 365, il est recommandé d'interrompre votre connexion réseau sur la porte d'entrée Microsoft 365 la plus proche.

>[!NOTE]
>La porte d'entrée du service Microsoft 365 n'a pas de relation directe avec le produit azure front door service disponible sur azure marketplace.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>Qu'est-ce qu'une porte d'entrée de service Microsoft 365 optimale ?

Une porte d'entrée du service Microsoft 365 optimale est celle qui est la plus proche de la sortie de votre réseau, généralement dans votre ville ou votre région. Utilisez l'outil de test de connectivité [Microsoft 365 (prévisualisation)](office-365-network-mac-perf-onboarding-tool.md) pour déterminer l'emplacement de la porte d'entrée du service Microsoft 365 en cours d'utilisation et la porte d'entrée du service optimale. Si l'outil détermine que votre porte frontale en cours d'utilisation est optimale, vous vous connectez de manière optimale au réseau global de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu'est-ce qu'un emplacement de sortie Internet ?

L'emplacement de sortie Internet est l'emplacement où votre trafic réseau quitte votre réseau d'entreprise et se connecte à Internet. Il s'agit également de l'emplacement où vous avez un périphérique de traduction d'adresses réseau (NAT) et généralement où vous vous connectez à un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement de sortie Internet, cela peut indiquer un retour arrière wan important.

### <a name="what-license-is-needed-for-this-capability"></a>Quelle licence est nécessaire pour cette fonctionnalité ?

Vous avez besoin d'une licence qui permet d'accéder au Centre d'administration Microsoft 365.

## <a name="related-topics"></a>Voir aussi

[Informations réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Microsoft 365 (prévisualisation)](office-365-network-mac-perf-score.md)

[Outil de test de connectivité Microsoft 365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)

[Services d'emplacement de connectivité réseau Microsoft 365 (prévisualisation)](office-365-network-mac-location-services.md)
