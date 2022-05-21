---
title: Connectivité réseau dans le centre de Administration Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
description: Vue d’ensemble de la connectivité réseau dans le centre de Administration Microsoft 365
ms.openlocfilehash: 4d23990253b96e57df04411a2207d089c90711ca
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621812"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center"></a>Connectivité réseau dans le centre de Administration Microsoft 365

Le centre Administration Microsoft 365 inclut désormais des métriques de connectivité réseau agrégées collectées à partir de votre locataire Microsoft 365 et disponibles pour être consultées uniquement par les utilisateurs administratifs de votre locataire.

> [!div class="mx-imgBorder"]
> ![Outil de test de connectivité réseau.](../media/m365-mac-perf/m365-mac-perf-admin-center.png)

**Les évaluations réseau** et **les insights réseau sont affichés** dans le Centre Administration Microsoft 365 sous **Health | Connectivité réseau**.

> [!div class="mx-imgBorder"]
> ![Page de performances réseau.](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

>[!NOTE]
>La connectivité réseau dans le Centre d’administration prend en charge les locataires de WW Commercial et d’Allemagne, mais pas Cloud de la communauté du secteur public Moderate, Cloud de la communauté du secteur public High, DoD ou Chine.

Lorsque vous accédez pour la première fois à la page de performances réseau, vous devez configurer vos emplacements pour afficher la carte des performances réseau globales, une évaluation réseau étendue à l’ensemble du locataire, le pourcentage de vos utilisateurs travaillant à distance par rapport à l’emplacement, et une liste des problèmes actuels pour prendre des mesures et/ou pour approfondir vos recherches. Dans le volet vue d’ensemble, vous pouvez explorer les métriques et les problèmes de performances réseau spécifiques par emplacement. Pour plus d’informations, consultez [la vue d’ensemble des performances réseau dans le centre de Administration Microsoft 365](#network-connectivity-overview-in-the-microsoft-365-admin-center).

Pour accéder à la page de connectivité réseau, vous devez être administrateur de l’organisation au sein de Microsoft 365. Le rôle d’administration Lecteur de rapports aura accès en lecture à ces informations. Pour configurer des emplacements et d’autres éléments de connectivité réseau, un administrateur doit avoir le rôle Administrateur du support technique.

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Conditions préalables à l’apparition des évaluations de connectivité réseau

Pour commencer, activez votre paramètre d’acceptation d’emplacement pour collecter automatiquement des données à partir d’appareils à l’aide de Windows Location Services, accédez à votre liste d’emplacements pour ajouter ou charger des données d’emplacement, ou exécutez le test de connectivité réseau Microsoft 365 à partir de vos emplacements de bureau. Ces trois options pour les informations sur l’emplacement du bureau sont détaillées ci-dessous. Bien que la connectivité réseau puisse être évaluée au sein de l’organisation, toute amélioration de la conception du réseau devra être effectuée pour des emplacements de bureau spécifiques. Les informations de connectivité réseau sont fournies pour chaque emplacement de bureau une fois que ces emplacements peuvent être déterminés. Il existe trois options pour obtenir des évaluations réseau à partir de vos emplacements de bureau :

### <a name="1-enable-windows-location-services"></a>1. Activer Windows Services d’emplacement

Pour cette option, vous devez disposer d’au moins deux ordinateurs en cours d’exécution à chaque emplacement de bureau qui prennent en charge les prérequis. OneDrive pour Windows version doit être à jour et installée sur chaque ordinateur. Pour plus d’informations sur OneDrive versions, consultez les [notes de publication OneDrive](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0). Les mesures réseau seront bientôt ajoutées à d’autres applications clientes Office 365.

Windows service d’emplacement doit être autorisé sur les machines. Vous pouvez tester cela en exécutant l’application **Cartes** et en vous localisant vous-même. Il peut être activé sur un seul ordinateur avec **Paramètres | | de confidentialité Emplacement** où le paramètre _Autoriser les applications à accéder à votre emplacement_ doit être activé. Windows le consentement location services peut être déployé sur des PC à l’aide de GPM ou de stratégie de groupe avec le paramètre _LetAppsAccessLocation_.

Vous n’avez pas besoin d’ajouter des emplacements dans le Centre d’administration avec cette méthode, car ils sont automatiquement identifiés à la résolution de ville. Plusieurs emplacements de bureaux dans la même ville ne s’affichent pas lors de l’utilisation de Windows Location Services. Les informations d’emplacement sont arrondies aux 300 mètres les plus proches par 300 mètres afin que les informations d’emplacement plus précises ne soient pas accessibles.

Les machines doivent avoir Wi-Fi réseau plutôt qu’un câble ethernet. Les machines avec un câble ethernet ne disposent pas d’informations précises sur l’emplacement.

Les échantillons de mesure et les emplacements de bureau doivent commencer à apparaître 24 heures après que ces conditions préalables ont été remplies.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. Ajouter des emplacements et fournir des informations de sous-réseau LAN

Pour cette option, ni Windows Services d’emplacement ni Wi-Fi n’est requis. Votre OneDrive pour Windows version doit être à jour et installée sur au moins un ordinateur à l’emplacement.

Veillez à ajouter également des emplacements dans la **page Emplacements** ou à les importer à partir d’un fichier CSV. Les emplacements ajoutés doivent inclure les informations de votre sous-réseau LAN office. Dans la boîte de dialogue permettant d’ajouter ou de modifier un emplacement, vous pouvez spécifier un certain nombre de sous-réseaux LAN et un certain nombre de sous-réseaux IP de sortie publique. Les sous-réseaux LAN sont requis et l’un d’eux doit correspondre à l’attribut de sous-réseau LAN sur une évaluation réseau reçue pour que les résultats s’affichent. Les super filets ne sont pas pris en charge et le sous-réseau LAN doit donc correspondre exactement.

En règle générale, les sous-réseaux LAN sont des plages d’adresses IP privées telles que définies dans RFC1918, de sorte que l’utilisation d’adresses IP publiques en tant que sous-réseaux LAN est susceptible d’être incorrecte. La boîte de dialogue affiche des suggestions de sous-réseaux LAN qui ont été vus dans les tests d’évaluation réseau récents pour votre organisation afin que vous puissiez choisir.

Si vous ajoutez des adresses IP de sortie publique, celles-ci sont utilisées en tant que différentiateurs secondaires et sont destinées lorsque vous avez plusieurs sites utilisant les mêmes plages d’adresses IP de sous-réseau LAN. Pour vous assurer que vos résultats de test s’affichent, vous devez commencer par laisser les plages d’adresses IP de sortie publiques vides. S’ils sont inclus, un résultat de test doit correspondre à la fois à l’une des plages d’adresses IP du sous-réseau LAN et à l’une des plages d’adresses IP de sortie publiques.

Cette option vous permet d’avoir plusieurs bureaux définis dans une ville.

Toutes les mesures de test des machines clientes incluent les informations du sous-réseau LAN, qui sont corrélées avec les détails de l’emplacement du bureau que vous avez entrés. Les échantillons de mesure et les emplacements de bureau doivent commencer à apparaître 24 heures après que ces conditions préalables ont été remplies.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. Collecter manuellement des rapports de test avec l’outil de test de connectivité réseau Microsoft 365

Pour cette option, vous devez identifier une personne à chaque emplacement. Demandez-leur de parcourir [Microsoft 365 test de connectivité réseau](https://connectivity.office.com) sur un ordinateur Windows sur lequel ils disposent d’autorisations administratives. Sur le site web, ils doivent se connecter à leur compte Office 365 pour la même organisation que celle que vous souhaitez voir les résultats. Ensuite, ils doivent cliquer sur **Exécuter le test**. Pendant le test, un test de connectivité EXE a été téléchargé. Ils doivent l’ouvrir et l’exécuter. Une fois les tests terminés, le résultat du test est chargé dans le Centre d’administration.

Les rapports de test sont liés à un emplacement s’ils ont été ajoutés avec des informations de sous-réseau LAN, sinon ils sont affichés à l’emplacement de la ville uniquement.

Les échantillons de mesure et les emplacements des bureaux doivent commencer à apparaître 2 à 3 minutes après la fin d’un rapport de test. Pour plus d’informations, consultez [Microsoft 365 test de connectivité réseau](office-365-network-mac-perf-onboarding-tool.md).

> [!NOTE]
> Actuellement, lorsque vous ajoutez vos emplacements de bureau à Microsoft 365 connectivité réseau dans le Centre d'administration Microsoft 365, vous pouvez fournir uniquement des adresses IPv4 pour vos sous-réseaux LAN. Egress adresses IP doivent utiliser IPv4.

## <a name="how-do-i-use-this-information"></a>Comment faire utiliser ces informations ?

**Les insights réseau**, leurs recommandations relatives aux performances et les évaluations réseau sont destinés à vous aider à concevoir des périmètres réseau pour vos emplacements de bureau. Chaque insight fournit des détails sur les caractéristiques de performances d’un problème de mise en réseau courant spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre locataire. **Les recommandations** en matière de performances pour chaque insight réseau offrent des modifications spécifiques à la conception de l’architecture réseau que vous pouvez apporter pour améliorer l’expérience utilisateur liée à Microsoft 365 connectivité réseau. L’évaluation réseau montre comment la connectivité réseau impacte l’expérience utilisateur, ce qui permet de comparer les différentes connexions réseau d’emplacement utilisateur.

**Les évaluations réseau** distillent un agrégat de nombreuses métriques de performances réseau en un instantané de l’intégrité de votre réseau d’entreprise, représenté par une valeur de points comprise entre 0 et 100. Les évaluations réseau s’appliquent à la fois à l’ensemble du locataire et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre locataire, ce qui permet aux administrateurs Microsoft 365 de saisir instantanément un gestalt de l’intégrité réseau de l’entreprise et d’explorer rapidement un rapport détaillé pour n’importe quel emplacement de bureau mondial.

Les entreprises complexes avec plusieurs bureaux et architectures de périmètre réseau non triviales peuvent tirer parti de ces informations lors de leur intégration initiale à Microsoft 365 ou pour corriger les problèmes de performances réseau détectés avec la croissance de l’utilisation. Cela n’est généralement pas nécessaire pour les petites entreprises utilisant Microsoft 365, ou pour les entreprises qui disposent déjà d’une connectivité réseau simple et directe. Les entreprises avec plus de 500 utilisateurs et plusieurs bureaux sont censées bénéficier le plus.

## <a name="enterprise-network-connectivity-challenges"></a>Enterprise problèmes de connectivité réseau

> [!div class="mx-imgBorder"]
> ![Réseau client vers le cloud.](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

De nombreuses entreprises ont des configurations de périmètre réseau, qui se sont développées au fil du temps et sont principalement conçues pour prendre en charge l’accès aux sites Web Internet des employés, où la plupart des sites web ne sont pas connus à l’avance et ne sont pas approuvés. L’objectif principal et nécessaire est d’éviter les attaques par hameçonnage et les programmes malveillants provenant de ces sites web inconnus. Cette stratégie de configuration réseau, bien qu’utile à des fins de sécurité, peut entraîner une dégradation des performances et de l’expérience utilisateur des utilisateurs Microsoft 365.

## <a name="how-we-can-solve-these-challenges"></a>Comment nous pouvons relever ces défis

Les entreprises peuvent améliorer l’expérience utilisateur générale et sécuriser leur environnement en suivant [Office 365 principes de connectivité](./microsoft-365-network-connectivity-principles.md) et en utilisant la fonctionnalité de connectivité réseau Administration Microsoft 365 Center. Dans la plupart des cas, l’application de ces principes généraux aura un impact positif significatif sur la latence des utilisateurs finaux, la fiabilité du service et les performances globales de Microsoft 365.

Microsoft est parfois invité à examiner les problèmes de performances réseau liés aux Microsoft 365 pour les clients de grande entreprise, et ceux-ci ont souvent une cause racine liée à l’infrastructure de périmètre réseau du client. Lorsqu’une cause racine courante d’un problème de périmètre de réseau client est trouvée, nous cherchons à identifier des mesures de test simples. Un test avec un seuil de mesure qui identifie un problème spécifique est utile, car nous pouvons tester la même mesure à n’importe quel emplacement, indiquer si cette cause racine est présente et la partager en tant qu’insight réseau avec l’administrateur.

Certains insights réseau indiquent simplement un problème qui nécessite une investigation plus approfondie. Un insight réseau où nous avons suffisamment de tests pour montrer une action de correction spécifique pour corriger la cause racine est répertorié comme **action recommandée**. Ces recommandations, basées sur des métriques dynamiques qui révèlent des valeurs qui se situent en dehors d’un seuil prédéterminé, sont beaucoup plus utiles que les conseils généraux en matière de bonnes pratiques, car elles sont spécifiques à votre environnement et montrent l’amélioration réelle une fois les modifications recommandées effectuées.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Vue d’ensemble de la connectivité réseau dans le centre de Administration Microsoft 365

Microsoft dispose de mesures réseau existantes à partir de plusieurs Office clients de bureau et web, qui prennent en charge le fonctionnement de Microsoft 365. Ces mesures sont désormais utilisées pour fournir des insights sur la conception de l’architecture réseau et une évaluation réseau, qui sont affichées dans la page **Connectivité réseau** du centre de Administration Microsoft 365.

Par défaut, les informations d’emplacement approximatives associées aux mesures réseau identifient la ville où se trouvent les appareils clients. L’évaluation réseau à chaque emplacement est affichée avec la couleur et le nombre relatif d’utilisateurs à chaque emplacement est représenté par la taille du cercle.

> [!div class="mx-imgBorder"]
> ![Carte de vue d’ensemble des insights réseau.](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

La page vue d’ensemble présente également l’évaluation réseau du client sous la forme d’une moyenne pondérée pour tous les emplacements de bureau.

> [!div class="mx-imgBorder"]
> ![Évaluation du réseau.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

Vous pouvez afficher une vue de table des emplacements où ils peuvent être filtrés, triés et modifiés dans l’onglet **Emplacements** . Les emplacements avec des recommandations spécifiques peuvent également inclure une amélioration de latence potentielle estimée. Cela est calculé en prenant la latence médiane des utilisateurs de votre organisation à l’emplacement et en soustrayant la latence médiane pour toutes les organisations de la même ville.

> [!div class="mx-imgBorder"]
> ![Emplacements d’insights réseau.](../media/m365-mac-perf/m365-mac-perf-locations.png)

## <a name="remote-worker-assessment-and-user-connection-metrics"></a>Métriques d’évaluation des workers distants et de connexion utilisateur

Nous classifions les journaux de trafic réseau en tant qu’utilisateurs distants ou sur site et affichons leurs pourcentages dans la section des métriques de connexion utilisateur du volet vue d’ensemble. Pour les villes où vous avez des utilisateurs distants, vous trouverez le score d’évaluation du réseau distant spécifique à l’emplacement lorsque vous ouvrez la page de cet emplacement. La liste des emplacements comporte des emplacements de bureaux et des villes de travail distantes, qui peuvent être filtrées et triées. Nous fournissons le score d’évaluation des travailleurs distants, avec la répartition des points pour Exchange, SharePoint et Teams.

Les informations de mise en réseau des utilisateurs à domicile sont agrégées et signalées au niveau de la ville et limitées aux villes avec un minimum de 5 employés distants. Nous n’identifions pas les employés qui travaillent à domicile.

Les emplacements sont automatiquement classés sur site ou distants. Toutefois, vous avez la possibilité d’entrer toutes vos adresses IP de sortie sur site manuellement pour garantir une classification à 100 %. Si vous décidez d’utiliser cette route, vous devez cocher **manuellement la case Entrée toutes les adresses IP de sortie sur site** dans le menu volant Emplacements Paramètres après avoir ajouté toutes vos adresses IP de sortie. Une fois cette opération effectuée, tous les journaux de trafic réseau des adresses IP de sortie que vous avez marquées comme étant sur site sont toujours classés en tant que bureaux et toutes les autres adresses IP de sortie sont classées comme distantes.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Résumé et insights sur les performances réseau de l’emplacement de bureau spécifique

La sélection d’un emplacement de bureau ouvre une page récapitulative spécifique à l’emplacement qui affiche les détails de la sortie réseau qui a été identifiée à partir des mesures de cet emplacement de bureau.

> [!div class="mx-imgBorder"]
> ![Détails des insights réseau par emplacement.](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

Une carte du réseau de périmètre pour les utilisateurs de votre organisation à l’emplacement est affichée avec certains ou tous ces éléments :

- **Office emplacement** : emplacement du bureau de la page que vous examinez
- **Périmètre réseau** : emplacement de l’adresse IP source pour les connexions à partir de l’emplacement du bureau. Cela dépend de la précision des bases de données d’emplacement géo-IP
- **Exchange porte d’entrée de service optimale** : l’une des portes d’entrée de service Exchange recommandées auxquelles les utilisateurs de cet emplacement de bureau doivent se connecter
- **Exchange porte d’entrée sous-optimale** : une porte d’entrée de service Exchange à laquelle les utilisateurs sont connectés, mais qui n’est pas recommandée
- **SharePoint porte d’entrée de service optimale** : l’une des portes d’entrée de service SharePoint recommandées auxquelles les utilisateurs de cet emplacement de bureau doivent se connecter
- **SharePoint porte d’entrée de service sous-optimale** : une porte d’entrée de service SharePoint à laquelle les utilisateurs sont connectés, mais qui n’est pas recommandée
- **Serveur de résolveur récursif DNS** : emplacement à partir d’une base de données IP géographique du programme de résolution récursif DNS détecté utilisé pour Exchange Online (le cas échéant)
- **Votre serveur proxy** : emplacement à partir d’une base de données IP géographique du serveur proxy détecté (le cas échéant)

La page récapitulative de l’emplacement du bureau affiche également l’évaluation réseau de l’emplacement, l’historique de l’évaluation du réseau, une comparaison de l’évaluation de cet emplacement avec d’autres clients de la même ville, ainsi qu’une liste d’informations et de recommandations spécifiques que vous pouvez entreprendre pour améliorer les performances et la fiabilité du réseau.

Les comparaisons entre les clients de la même ville sont basées sur l’attente que tous les clients aient un accès égal aux fournisseurs de services réseau, à l’infrastructure de télécommunications et aux points de présence réseau Microsoft à proximité.

Les noms d’emplacement peuvent être personnalisés lors de l’ajout d’un nouvel emplacement ou de la modification d’un emplacement existant dans le menu volant d’emplacement. Cela vous offre la possibilité de personnaliser vos noms d’emplacement à tout moment. En outre, lors de l’ajout de sous-réseaux LAN directement dans le menu volant d’emplacement, nous affichons une liste déroulante de sous-réseaux LAN mis en correspondance de manière réversible à partir de laquelle vous pouvez sélectionner. Les noms de circuit pour des adresses IP de sortie de bureau spécifiques peuvent également être ajoutés et modifiés.

L’onglet Détails de la page Emplacement du bureau affiche les résultats de mesure spécifiques qui ont été utilisés pour obtenir des insights, des recommandations et l’évaluation réseau. Cela est fourni afin que les ingénieurs réseau puissent valider les recommandations et tenir compte des contraintes ou des spécificités de leur environnement. Vous trouverez également le nombre estimé d’utilisateurs pour les échantillons collectés dans ces bureaux, ainsi que les travailleurs à distance dans cette ville.

> [!div class="mx-imgBorder"]
> ![Détails spécifiques à l’emplacement.](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

## <a name="sharing-network-assessment-data-with-microsoft"></a>Partage de données d’évaluation réseau avec Microsoft

Par défaut, les évaluations réseau de votre organisation et les insights réseau sont partagées avec les employés de Microsoft. Cela n’inclut pas les données personnelles de votre personnel, mais uniquement les métriques d’évaluation réseau et les insights réseau spécifiques affichés dans le centre d’administration pour vos emplacements de bureau. Il n’inclut pas non plus les noms des lieux de bureau ou les adresses postales. Vous devez donc leur indiquer la ville et l’ID de support du bureau dont vous souhaitez discuter. Si cette option est désactivée, les ingénieurs Microsoft avec qui vous discutez de la connectivité réseau ne peuvent pas afficher ces informations. L’activation de ce paramètre ne partage que les données futures à compter du lendemain de son activation.

## <a name="csv-import-for-lan-subnet-office-locations"></a>Importation CSV pour les emplacements de bureau du sous-réseau LAN

Pour l’identification du bureau du sous-réseau LAN, vous devez ajouter chaque emplacement à l’avance. Au lieu d’ajouter des emplacements de bureau individuels dans l’onglet **Emplacements** , vous pouvez les importer à partir d’un fichier CSV. Vous pouvez obtenir ces données à partir d’autres emplacements que vous avez stockés, tels que le tableau de bord qualité des appels ou les sites et services Active Directory

Dans le fichier CSV, un emplacement de ville découvert apparaît dans la colonne userEntered comme vide et un emplacement de bureau ajouté manuellement indique 1.

1. Dans la fenêtre _Connectivité principale à Microsoft 365_, cliquez sur l’onglet **Emplacements**.

1. Cliquez sur le bouton **Importer** juste au-dessus de la liste des emplacements. Le menu volant **Importer les emplacements du bureau** s’affiche.

   > [!div class="mx-imgBorder"]
   > ![Message d’importation CSV.](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Cliquez sur le lien **Télécharger les emplacements de bureau actuels (.csv)** pour exporter la liste des emplacements actuels dans un fichier CSV et l’enregistrer sur votre disque dur local. Vous disposerez ainsi d’un CSV correctement mis en forme avec des en-têtes de colonne auxquels vous pouvez ajouter des emplacements. Vous pouvez laisser les emplacements exportés existants tels qu’ils sont ; ils ne seront pas dupliqués lorsque vous importez le fichier CSV mis à jour. Si vous souhaitez modifier l’adresse d’un emplacement existant, elle sera mise à jour lorsque vous importez le fichier CSV. Vous ne pouvez pas modifier l’adresse d’une ville découverte.

1. Ouvrez le fichier CSV et ajoutez vos emplacements en remplissant les champs suivants sur une nouvelle ligne pour chaque emplacement que vous souhaitez ajouter. Laissez tous les autres champs vides ; les valeurs que vous entrez dans d’autres champs seront ignorées.

   1. **userEntered** (obligatoire) : doit être 1 pour l’ajout d’un nouvel emplacement de bureau du sous-réseau LAN
   1. **Nom** (obligatoire) : nom de l’emplacement du bureau
   1. **Adresse** (obligatoire) : adresse physique du bureau
   1. **Latitude** (facultatif) : renseigné à partir de Bing mappe la recherche de l’adresse si vide
   1. **Longitude** (facultatif) : renseigné à partir de Bing mappe la recherche de l’adresse si vide
   1. **Egress plages d’adresses IP 1 à 5** (facultatif) : pour chaque plage, entrez le nom du circuit suivi d’une liste séparée par un espace d’adresses CIDR IPv4 valides. Ces valeurs sont utilisées pour différencier plusieurs emplacements de bureau où vous utilisez les mêmes adresses IP de sous-réseau LAN. Egress plages d’adresses IP doivent toutes être de taille réseau /24 et /24 n’est pas inclus dans l’entrée.
   1. **LanIps** (obligatoire) : répertorie les plages de sous-réseaux LAN utilisées dans cet emplacement de bureau. Les ID de sous-réseau LAN doivent avoir une taille réseau CIDR incluse, où la taille du réseau peut être comprise entre /8 et /29. Plusieurs plages de sous-réseaux LAN peuvent être séparées par une virgule ou un point-virgule.

1. Une fois que vous avez ajouté vos emplacements de bureau et enregistré le fichier, cliquez sur le bouton **Parcourir** en regard du **Télécharger le champ terminé**, puis sélectionnez le fichier CSV enregistré.

1. Le fichier est automatiquement validé. S’il y a des erreurs de validation, vous verrez le message d’erreur : _il y a des erreurs dans le fichier d’importation. Passez en revue les erreurs, corrigez le fichier d’importation, puis réessayez._ Cliquez sur le lien **Ouvrir les détails de l’erreur** pour obtenir la liste des erreurs de validation de champ spécifiques.

   > [!div class="mx-imgBorder"]
   > ![Message d’erreur d’importation CSV.](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. S’il n’y a aucune erreur dans le fichier, le message suivant s’affiche : _le rapport est prêt. Emplacements x trouvés à ajouter et x emplacements à mettre à jour._ Cliquez sur le bouton **Importer** pour charger le fichier CSV.

   > [!div class="mx-imgBorder"]
   > ![Message prêt pour l’importation CSV.](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>FAQ

### <a name="what-is-a-microsoft-365-service-front-door"></a>Qu’est-ce qu’une porte d’entrée de service Microsoft 365 ?

La porte d’entrée du service Microsoft 365 est un point d’entrée sur le réseau mondial de Microsoft où Office clients et services mettent fin à leur connexion réseau. Pour une connexion réseau optimale à Microsoft 365, il est recommandé que votre connexion réseau soit arrêtée dans la porte d’entrée Microsoft 365 la plus proche.

>[!NOTE]
>Microsoft 365 porte d’entrée de service n’a pas de relation directe avec le produit Azure Front Door Service disponible sur la Place de marché Azure.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>Qu’est-ce qu’une porte d’entrée de service Microsoft 365 optimale ?

Une porte d’entrée de service Microsoft 365 optimale est celle qui est la plus proche de votre sortie réseau, généralement dans votre ville ou région métropolitaine. Utilisez [l’outil de test de connectivité Microsoft 365](office-365-network-mac-perf-onboarding-tool.md) pour déterminer l’emplacement de votre porte d’entrée Microsoft 365 service en service et la porte d’entrée de service optimale. Si l’outil détermine que votre porte d’entrée en service est optimale, vous vous connectez de manière optimale au réseau mondial de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu’est-ce qu’un emplacement de sortie Internet ?

L’emplacement de sortie Internet est l’emplacement où votre trafic réseau quitte votre réseau d’entreprise et se connecte à Internet. Il s’agit également de l’emplacement où vous disposez d’un appareil NAT (Network Address Translation) et généralement où vous vous connectez avec un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement de sortie Internet, cela peut indiquer une importante forme de backhaul WAN.

### <a name="what-license-is-needed-for-this-capability"></a>Quelle licence est nécessaire pour cette fonctionnalité ?

Vous avez besoin d’une licence qui fournit l’accès à la Centre d'administration Microsoft 365.

## <a name="related-topics"></a>Voir aussi

[Microsoft 365 insights réseau](office-365-network-mac-perf-insights.md)

[Microsoft 365 l’évaluation du réseau](office-365-network-mac-perf-score.md)

[Microsoft 365 outil de test de connectivité](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 services d’emplacement de connectivité réseau](office-365-network-mac-location-services.md)
