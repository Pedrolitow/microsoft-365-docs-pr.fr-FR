---
title: Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Vue d’ensemble de la connectivité réseau dans le centre d’administration Microsoft 365 (version d’évaluation)
ms.openlocfilehash: 7171565b6bd3bfba3defb49b51349c95d1598367
ms.sourcegitcommit: 234726a1795d984c4659da68f852d30a4dda5711
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "46794293"
---
# <a name="network-connectivity-in-the-microsoft-365-admin-center-preview"></a>Connectivité réseau dans le centre d’administration Microsoft 365 (version d’évaluation)

Le centre d’administration 365 de Microsoft includesaggregated les mesures de connectivité réseau collectées à partir de votre client Microsoft 365 et disponibles uniquement par les utilisateurs administratifs de votre client. Les **évaluations réseau** et les informations sur le **réseau** s’affichent dans le centre d’administration Microsoft 365 sous **intégrité | Connectivité**.

![Page des performances du réseau](../media/m365-mac-perf/m365-mac-perf-page-nav.png)

Lorsque vous accédez à la page connectivité réseau, vous verrez un volet de vue d’ensemble contenant une carte des performances réseau globales, une évaluation du réseau pour l’étendue de l’ensemble du client, ainsi qu’une liste des problèmes actuels. À partir de la vue d’ensemble, vous pouvez accéder à des mesures et des problèmes de performances réseau spécifiques par emplacement. Pour plus d’informations, reportez-vous à [Network performance Overview dans le centre d’administration 365 de Microsoft](#network-performance-overview-in-the-microsoft-365-admin-center).

## <a name="pre-requisites-for-network-connectivity-assessments-to-appear"></a>Conditions préalables à l’affichage des évaluations de connectivité réseau

Il existe trois options pour l’évaluation du réseau à partir de vos emplacements de bureau :

### <a name="1-enable-windows-location-services"></a>1. activer les services d’emplacement Windows

Pour cette option, vous devez disposer d’au moins deux ordinateurs en cours d’exécution à chaque emplacement de bureau qui prennent en charge les conditions préalables. OneDrive pour Windows version 19,232 ou ultérieure doit être installé sur chaque ordinateur. Pour plus d’informations sur les versions de OneDrive, consultez les [notes de publication de onedrive](https://support.office.com/article/onedrive-release-notes-845dcf18-f921-435e-bf28-4e24b95e5fc0). Les mesures du réseau sont planifiées pour être ajoutées dans d’autres applications clientes Office 365 dans un futur proche.

Le service d’emplacement Windows doit être accepté sur les ordinateurs. Vous pouvez le tester en exécutant l’application **Maps** et en vous localisant. Il peut être activé sur un seul ordinateur avec l’emplacement de confidentialité des **paramètres**  ->  **Privacy**  ->  **Location** où le paramètre « autoriser les applications à accéder à votre emplacement » doit être activé. Le consentement des services d’emplacement Windows peut être déployé sur des PC à l’aide de MDM ou de la stratégie de groupe avec le paramètre _LetAppsAccessLocation_.

Vous n’avez pas besoin d’ajouter des emplacements dans le centre d’administration avec cette méthode, car ils sont automatiquement identifiés à la résolution de la ville. Vous ne pouvez pas afficher plusieurs emplacements de bureau dans une ville à l’aide des services d’emplacement Windows.

Les machines doivent disposer de la mise en réseau Wi-Fi plutôt que d’un câble Ethernet. Les machines disposant d’un câble Ethernet ne disposent pas d’informations d’emplacement précises.

Les exemples de mesures et les emplacements de bureau doivent commencer à apparaître 24 heures après que ces conditions préalables ont été satisfaites.

### <a name="2-add-locations-and-provide-lan-subnet-information"></a>2. ajouter des emplacements et fournir des informations de sous-réseau LAN

Pour cette option, ni les services de localisation Windows ni le Wi-Fi ne sont requis. Vous avez besoin de OneDrive pour Windows version 20.161.0811.0001 ou une version ultérieure installée sur chaque commputer à l’emplacement.

Vous devez également ajouter des emplacements dans la page connectivité réseau du centre d’administration ou pour les importer à partir d’un fichier CSV. Les emplacements ajoutés doivent inclure les informations de sous-réseau de votre réseau local Office.

Étant donné que vous ajoutez les emplacements, vous pouvez avoir plusieurs bureaux définis dans une ville.

Les exemples de mesures et les emplacements de bureau doivent commencer à apparaître 24 heures après que ces conditions préalables ont été satisfaites.

### <a name="3-manually-gather-test-reports-with-the-microsoft-365-network-connectivity-test-tool"></a>3. recueillez manuellement des rapports de test avec l’outil de test de connectivité réseau Microsoft 365

Pour cette option, vous devez identifier une personne à chaque emplacement. Demandez-lui de procéder au [test de connectivité réseau Microsoft 365](https://connectivity.office.com) sur un ordinateur Windows sur lequel il dispose d’autorisations d’administration. Sur le site Web, ils doivent se connecter à leur compte Office 365 sur le même client que vous souhaitez voir les résultats. Ensuite, cliquez sur exécuter le test. Pendant le test, un EXE de test de connectivité est téléchargé. Elles doivent également être ouvertes et exécutées. Une fois les tests terminés, le résultat du test est téléchargé vers Microsoft.

Les rapports de test sont liés à un emplacement s’il a été ajouté avec des informations de sous-réseau de réseau local, sinon ils apparaissent uniquement à l’emplacement de la ville.

Les exemples de mesures et les emplacements de bureau doivent commencer à apparaître à 2-3 minutes après l’exécution d’un résultat de test.

## <a name="how-do-i-use-this-information"></a>Comment utiliser ces informations ?

**Network Insights**, leurs recommandations de performances et évaluations réseau associées sont destinées à faciliter la conception des périmètres réseau pour vos emplacements de bureau. Chaque vue fournit des détails sur les caractéristiques de performances d’un problème commun spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre client. **Recommandations** en matière de performances pour chaque modèle Network Insight apporter des modifications de conception de l’architecture réseau spécifique que vous pouvez apporter pour améliorer l’expérience utilisateur liée à la connectivité réseau Microsoft 365. L’évaluation du réseau montre l’impact de la connectivité réseau sur l’expérience utilisateur, ce qui permet de comparer différentes connexions réseau d’emplacement utilisateur.

Les **évaluations de réseau** convertissent un agrégat de nombreuses métriques de performances réseau en un instantané de l’état de votre réseau d’entreprise, représenté par une valeur de points comprise entre 0-100. Les évaluations réseau sont étendues à la fois à l’ensemble du client et à chaque emplacement géographique à partir duquel les utilisateurs se connectent à votre client, ce qui permet aux administrateurs de Microsoft 365 de mieux appréhender instantanément un Gestalt de l’état du réseau de l’entreprise et d’accéder rapidement à un rapport détaillé sur un emplacement Office global.

Les entreprises complexes disposant de plusieurs emplacements de bureau et d’architectures de périmètre réseau non négligeables peuvent tirer parti de ces informations lors de leur intégration initiale à Microsoft 365 ou pour corriger les problèmes de performances réseau découverts avec la croissance de l’utilisation. Cette fonction n’est généralement pas nécessaire pour les petites entreprises utilisant Microsoft 365 ou toute entreprise qui dispose déjà d’une connectivité réseau simple et directe. Les entreprises disposant de plus de 500 utilisateurs et de plusieurs emplacements de bureau sont censées tirer le meilleur parti.

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont uniquement disponibles pour les locataires Microsoft 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="enterprise-network-connectivity-challenges"></a>Défis de connectivité du réseau d’entreprise

![Réseau client vers Cloud](../media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

De nombreuses entreprises ont des configurations de périmètre réseau qui se sont produites au fil du temps et qui sont principalement conçues pour prendre en charge l’accès aux sites Web des employés où la plupart des sites Web ne sont pas connus à l’avance et ne sont pas approuvés. L’objectif de ce site est d’éviter les attaques de programmes malveillants et de pêche à partir de ces sites Web inconnus. Cette stratégie de configuration réseau, tout en étant utile à des fins de sécurité, peut entraîner une dégradation des performances utilisateur et de l’expérience utilisateur de Microsoft 365.

## <a name="how-we-can-solve-these-challenges"></a>Comment nous pouvons résoudre ces problèmes

Les entreprises peuvent améliorer l’expérience utilisateur générale et sécuriser leur environnement en suivant les [principes de connectivité d’Office 365](https://aka.ms/pnc) et en utilisant la fonctionnalité de connectivité réseau centre d’administration Microsoft 365. Dans la plupart des cas, le suivi de ces principes généraux aura un impact positif significatif sur la latence des utilisateurs finaux, la fiabilité des services et les performances globales de Microsoft 365.

Microsoft est parfois invité à examiner les problèmes de performances réseau liés à Microsoft 365 pour les grandes entreprises, et ceux-ci ont souvent une cause principale liée à l’infrastructure de sortie du réseau des clients. Lors de la détection d’une cause racine commune d’un problème de périmètre réseau client, nous cherchons à identifier les mesures de test simples qui l’identifient. Un test avec un seuil de mesure qui identifie un problème spécifique est utile, car nous pouvons tester la même mesure dans n’importe quel emplacement, indiquer si cette cause première existe et la partager en tant que Network Insight avec l’administrateur.

Certains aspects du réseau indiquent simplement un problème qui nécessite une nouvelle enquête. Un Network Insight où nous avons suffisamment de tests pour afficher une action corrective spécifique pour corriger la cause principale est mentionné comme une **action recommandée**. Ces recommandations, basées sur des métriques vivantes qui révèlent des valeurs situées en dehors d’un seuil prédéterminé, sont bien plus importantes que les conseils de bonne pratique générale, car ils sont spécifiques à votre environnement et affichent l’amélioration effective une fois que les modifications recommandées ont été apportées.

## <a name="network-connectivity-overview-in-the-microsoft-365-admin-center"></a>Vue d’ensemble de la connectivité réseau dans le centre d’administration Microsoft 365

Microsoft a des mesures réseau existantes à partir de plusieurs clients de bureau et Web Office qui prennent en charge le fonctionnement de Microsoft 365. Ces mesures sont désormais utilisées pour fournir des informations sur la conception de l’architecture réseau et une évaluation du réseau qui sont affichées dans la page **connectivité réseau** du centre d’administration 365 de Microsoft.

Par défaut, les informations d’emplacement approximatives associées aux mesures du réseau identifient la ville où se trouvent les appareils clients. L’évaluation du réseau à chaque emplacement est illustrée par la couleur et le nombre d’utilisateurs par rapport à chaque emplacement est représenté par la taille du cercle.

![Plan de présentation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-map.png)

La page vue d’ensemble indique également l’évaluation du réseau pour le client sous la forme d’une moyenne pondérée sur tous les bureaux.

![Évaluation du réseau](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Informations spécifiques sur les performances et les informations du réseau d’emplacement de bureau

La sélection d’un emplacement de bureau ouvre une page de résumé spécifique à l’emplacement présentant les détails de la sortie réseau identifiée à partir de mesures pour cet emplacement de bureau.

![Informations sur le réseau, détails par emplacement](../media/m365-mac-perf/m365-mac-perf-locations-plan-overview.png)

La page de résumé des emplacements Office indique également l’évaluation du réseau de l’emplacement, l’historique de l’évaluation du réseau, une comparaison de l’évaluation de cet emplacement aux autres clients de la même ville, ainsi qu’une liste d’informations et de recommandations spécifiques que vous pouvez entreprendre pour améliorer les performances et la fiabilité du réseau. Les emplacements avec des recommandations spécifiques peuvent également inclure une amélioration potentielle de la latence.

Les comparaisons entre les clients de la même ville sont basées sur l’attente que tous les clients ont un accès égal aux fournisseurs de services réseau, à l’infrastructure de télécommunications et aux points de présence réseau Microsoft voisins.

![Emplacements des informations sur le réseau](../media/m365-mac-perf/m365-mac-perf-locations.png)

L’onglet Détails de la page emplacement du Bureau affiche les résultats de mesure spécifiques qui ont été utilisés pour trouver des informations, des recommandations et l’évaluation du réseau. Cela permet aux ingénieurs réseau de valider les recommandations et facteurs dans les contraintes ou les spécificités de leur environnement.

![Détails spécifiques à l’emplacement](../media/m365-mac-perf/m365-mac-perf-locations-plan-details-all.png)

## <a name="csv-import-for-lan-subnet-office-locations"></a>Importation CSV pour les emplacements de sous-réseau LAN

Pour l’identification de sous-réseau local, vous devez ajouter chaque locaiton à l’avance. Au lieu d’ajouter des emplacements de bureau individuels dans l’onglet **emplacements** , vous pouvez les importer à partir d’un fichier CSV. Il se peut que vous puissiez obtenir ces données à partir d’autres emplacements que vous stockez, tels que le tableau de bord de qualité des appels ou les sites et services Active Directory.

Dans le fichier CSV, un emplacement de ville découvert est étiqueté **ville**, et un emplacement de bureau ajouté manuellement est **emplacement**.

1. Dans la fenêtre principale _connectivité à Microsoft 365_ , cliquez sur l’onglet **emplacements** .
1. Cliquez sur le bouton **Importer** situé au-dessus de la liste emplacements. Le menu volant **importer des emplacements de bureau** s’affiche.

   ![Message d’erreur d’importation CSV](../media/m365-mac-perf/m365-mac-perf-import.png)

1. Cliquez sur le lien **Télécharger les emplacements Office actifs (. csv)** pour exporter la liste des emplacements actuels vers un fichier CSV, puis enregistrez-le sur votre disque dur local. Vous obtiendrez un fichier CSV au format correct avec des en-têtes de colonne vers lesquels vous pouvez ajouter des emplacements. Vous pouvez laisser les emplacements exportés existants comme ils le sont ; elles ne sont pas dupliquées lorsque vous importez le fichier CSV mis à jour. Si vous souhaitez modifier l’adresse d’un emplacement existant, celle-ci est mise à jour lorsque vous importez le fichier CSV. Vous ne pouvez pas modifier l’adresse d’une ville découverte.
1. Ouvrez le fichier CSV et ajoutez vos emplacements en remplissant les champs suivants sur une nouvelle ligne pour chaque emplacement que vous souhaitez ajouter. Laissez tous les autres champs vides ; les valeurs que vous entrez dans d’autres champs seront ignorées.
   1. **Address** (Required) : adresse physique de l’Office
   1. **Latitude** (facultatif) : renseigné à partir de la recherche de cartes Bing si vide
   1. **Longitude** (facultative) : renseigné à partir de la recherche de cartes Bing si vide
   1. **Plages d’adresses IP sortantes 1-5** (facultatif) : pour chaque plage, entrez le nom du circuit suivi d’une liste d’adresses CIDR IPv4 ou IPv6 valides séparées par des espaces. Ces valeurs sont utilisées pour différencier plusieurs emplacements Office où vous utilisez les mêmes adresses IP de sous-réseau de réseau local.
   1. **LanIps** (obligatoire) : répertoriez les plages de sous-réseau LAN utilisées à cet emplacement de bureau.
1. Une fois que vous avez ajouté vos emplacements de bureau et enregistré le fichier, cliquez sur le bouton **Parcourir** en regard du champ **charger le champ terminé** , puis sélectionnez le fichier csv enregistré.
1. Le fichier sera automatiquement validé. S’il existe des erreurs de validation, le message d’erreur indique que _le fichier d’importation contient des erreurs. Examinez les erreurs, corrigez le fichier d’importation, puis réessayez._ Cliquez sur le lien Détails de l' **erreur Open** pour obtenir la liste des erreurs de validation de champ spécifiques.

   ![Message d’erreur d’importation CSV](../media/m365-mac-perf/m365-mac-perf-import-error.png)

1. S’il n’y a pas d’erreurs dans le fichier, le message _le rapport est prêt. Emplacements trouvés x à ajouter et emplacements à mettre à jour._ Cliquez sur le bouton **Importer** pour charger le fichier CSV.

   ![Message d’importation CSV prêt](../media/m365-mac-perf/m365-mac-perf-import-ready.png)

## <a name="faq"></a>FAQ

### <a name="what-is-a-microsoft-365-service-front-door"></a>Qu’est-ce qu’une porte d’accès avant du service Microsoft 365 ?

Le service frontal Microsoft 365 est un point d’entrée sur le réseau mondial de Microsoft où les clients et les services Office mettent fin à leur connexion réseau. Pour une connexion réseau optimale à Microsoft 365, il est recommandé que votre connexion réseau soit arrêtée dans le volet frontal Microsoft 365 le plus proche.

>[!NOTE]
>Le service frontal de service Microsoft 365 n’a pas de relation directe avec le produit du service de la porte frontale Azure disponible sur Azure Marketplace.

### <a name="what-is-an-optimal-microsoft-365-service-front-door"></a>Qu’est-ce qu’une porte d’avance sur le service Microsoft 365 ?

Une porte de service frontale Microsoft 365 optimale est celle qui est la plus proche de la sortie de votre réseau, généralement dans votre ville ou votre région de métro. Utilisez le [test de connectivité de microsoft 365](office-365-network-mac-perf-onboarding-tool.md) pour déterminer l’emplacement de votre service Microsoft 365 et de votre porte de service frontal optimale. Si l’outil détermine que votre porte avant de l’utilisation est optimale, vous vous connectez de manière optimale au réseau global de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu’est-ce qu’un emplacement de sortie Internet ?

L’emplacement de sortie Internet est l’emplacement où votre trafic réseau quitte votre réseau d’entreprise et se connecte à Internet. Elle est également identifiée comme l’emplacement où vous avez un périphérique de traduction d’adresses réseau (NAT) et généralement l’endroit où vous vous connectez avec un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement Internet sortant, cela peut indiquer une sorte de trajet WAN important.

## <a name="related-topics"></a>Rubriques connexes

[Informations sur le réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Microsoft 365 Network Assessment (aperçu)](office-365-network-mac-perf-score.md)

[Test de connectivité Microsoft 365 dans le centre d’administration M365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-location-services.md)
