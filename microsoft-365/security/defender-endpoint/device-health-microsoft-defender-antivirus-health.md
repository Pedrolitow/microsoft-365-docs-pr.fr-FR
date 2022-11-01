---
title: Rapport d’intégrité de l’antivirus Microsoft Defender de l’appareil
description: Utilisez le rapport antivirus Microsoft Defender pour suivre l’état de l’antivirus et Microsoft Defender versions du moteur, de l’intelligence et de la plateforme antivirus.
keywords: Microsoft Defender Rapport antivirus, version du moteur, version d’intelligence et versions de plateforme, antivirus
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
ms.date: 09/06/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
ms.reviewer: mkaminska
ms.openlocfilehash: 5211cbe42ec735f914eff6fb420d9fc0baf4c883
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804419"
---
<!-- v-jweston/jweston-1 is scheduled to resume authorship Apr/May 2023.-->

# <a name="device-health-microsoft-defender-antivirus-health-report"></a>Rapport d’intégrité de l’appareil, Microsoft Defender Antivirus

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Le rapport Intégrité de l’appareil fournit des informations sur les appareils de votre organisation. Le rapport inclut des informations de tendance montrant l’état de l’antivirus et Microsoft Defender moteur antivirus, l’intelligence et les versions de la plateforme.

> [!IMPORTANT]
> Pour que Windows&nbsp;Server&nbsp;2012&nbsp;R2 et Windows&nbsp;Server&nbsp;2016 apparaissent dans les rapports d’intégrité des appareils, ces appareils doivent être intégrés à l’aide du package de solution unifiée moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution).

Dans le panneau de navigation du tableau de bord sécurité Microsoft 365, sélectionnez **Rapports**, puis ouvrez **Intégrité et conformité de l’appareil**. [**L’onglet Microsoft Defender Antivirus Health**](#microsoft-defender-antivirus-health-tab) contient huit cartes qui indiquent les aspects suivants de Microsoft Defender Antivirus :
- [Carte du mode antivirus](#antivirus-mode-card)
- [Carte de version du moteur antivirus](#antivirus-engine-version-card)
- [Carte de version de l’antivirus Security Intelligence](#antivirus-security-intelligence-version-card)
- [Carte de version de la plateforme antivirus](#antivirus-platform-version-card)
- [Carte des résultats de l’analyse antivirus récente](#recent-antivirus-scan-results-card)
- [Carte de mise à jour du moteur antivirus](#antivirus-engine-updates-card)
- [Carte des mises à jour du renseignement de sécurité](#security-intelligence-updates-card)
- [Carte de mise à jour de la plateforme antivirus](#antivirus-platform-updates-card)

## <a name="report-access-permissions"></a>Autorisations d’accès aux rapports

Pour accéder au rapport d’intégrité de l’appareil et de conformité antivirus dans le tableau de bord Sécurité Microsoft 365, les autorisations suivantes sont requises :

| Nom de l’autorisation | Type d’autorisation |
|:---|:---|
| Afficher les données | Gestion des menaces et des vulnérabilités (TVM) |

Pour attribuer ces autorisations :

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> à l’aide du compte avec le rôle Administrateur de la sécurité ou Administrateur général attribué.
1. Dans le volet de navigation, sélectionnez **Paramètres Rôles** \> **de points** \> de terminaison (sous **Autorisations**).
1. Sélectionnez le rôle que vous souhaitez modifier.
1. Sélectionnez **Modifier**.
1. Dans **Modifier le rôle**, sous l’onglet **Général** , dans **Nom du** rôle, tapez un nom pour le rôle.
1. Dans **Description** , tapez un bref résumé du rôle.
1. Dans **Autorisations**, sélectionnez **Afficher les données**, puis, sous **Afficher les données** , sélectionnez **Gestion des menaces et des vulnérabilités** (TVM).

Pour plus d’informations sur la gestion des rôles d’utilisateur, consultez [Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle](user-roles.md).

## <a name="microsoft-defender-antivirus-health-tab"></a>Microsoft Defender onglet Intégrité de l’antivirus 
L’onglet Microsoft Defender Antivirus contient huit cartes qui signalent plusieurs aspects de Microsoft Defender Antivirus dans votre organisation :

Deux cartes, [la carte mode antivirus](#antivirus-mode-card) et la [carte des résultats de l’analyse antivirus récente](#recent-antivirus-scan-results-card), indiquent Microsoft Defender fonctions antivirus.

Les six autres cartes indiquent l’état de l’antivirus Microsoft Defender pour les appareils de votre organisation :

| _cartes de version_ : | _cartes de mise à jour_ {<a id="fn1">1</a>} |
|:---|:---|
| [Carte de version du moteur antivirus](#antivirus-engine-version-card) <br> [Carte de version de l’antivirus Security Intelligence](#antivirus-security-intelligence-version-card) <br> [Carte de version de la plateforme antivirus](#antivirus-platform-version-card) | [Carte de mise à jour du moteur antivirus](#antivirus-engine-updates-card) <br> [Carte des mises à jour du renseignement de sécurité](#security-intelligence-updates-card) <br> [Carte de mise à jour de la plateforme antivirus](#antivirus-platform-updates-card) |
| Les trois cartes de version fournissent des rapports volants qui fournissent des informations supplémentaires et permettent une exploration plus approfondie. | Les trois fiches de rapport à jour fournissent des liens vers des ressources pour en savoir plus. |

<sup>{[1](#fn1)}</sup> Pour les trois cartes de _mise à jour_ (également appelées cartes de création de rapports à jour), « **Aucune donnée disponible** » (ou valeur « Inconnue ») indique les appareils qui ne signalent pas l’état de mise à jour. Les appareils qui ne signalent pas l’état de mise à jour peuvent être dus à diverses raisons, par exemple :

- L’ordinateur est déconnecté du réseau.
- L’ordinateur est hors tension ou dans un état de mise en veille prolongée.
- Microsoft Defender Antivirus est désactivé.
- L’appareil est un appareil non Windows (Mac ou Linux).
- La protection cloud n’est pas activée.
- L’appareil ne répond pas aux prérequis du moteur antivirus ou de la version de la plateforme.

### <a name="prerequisites"></a>Configuration requise

Les rapports à jour génèrent des informations pour les appareils qui répondent aux critères suivants :

- Version du moteur : 1.1.19300.2+
- Version de la plateforme : 4.18.2202.1+
- Protection cloud activée
- Système d’exploitation Windows
   >[!Note]
   >Actuellement, les rapports à jour sont disponibles uniquement pour les appareils Windows. Les appareils multiplateformes tels que Mac et Linux sont répertoriés sous « Aucune donnée disponible »/Inconnu.

:::image type="content" source="images/device-health-defender-antivirus-health-tab.png" alt-text="Affiche l’onglet Microsoft Defender Antivirus Health." lightbox="images/device-health-defender-antivirus-health-tab.png":::

### <a name="card-functionality"></a>Fonctionnalité de carte

La fonctionnalité est essentiellement la même pour toutes les cartes. En cliquant sur une barre numérotée dans l’une des cartes, le menu volant **Microsoft Defender Antivirus details** s’ouvre, ce qui vous permet d’examiner les informations sur tous les appareils configurés avec le numéro de version d’un aspect sur cette carte.

:::image type="content" source="images/device-health-defender-antivirus-health-antivirus-details.png" alt-text="Affiche le menu volant des détails de l’antivirus Microsoft Defender." lightbox="images/device-health-defender-antivirus-health-antivirus-details.png":::

Si le numéro de version sur lequel vous avez cliqué est :

- Une version actuelle, la **correction requise** et la **recommandation de sécurité** ne sont pas présentes.
- Une version obsolète, une notification en haut du rapport est présente, indiquant **correction requise**, et un lien **de recommandation de sécurité** est présent. Sélectionnez le lien de recommandation de sécurité pour accéder à la console Gestion des menaces et des vulnérabilités, qui peut recommander les mises à jour antivirus appropriées.

Pour ajouter ou supprimer des types d’informations spécifiques dans le menu volant **détails de l’antivirus Microsoft Defender**, sélectionnez **Personnaliser les colonnes**. Dans **Personnaliser les colonnes**, sélectionnez ou effacez les éléments pour spécifier ce que vous souhaitez inclure dans le rapport détails de l’antivirus Microsoft Defender.

:::image type="content" source="images/device-health-defender-antivirus-engine-version-details-custom-columns.png" alt-text="Affiche les options de colonne personnalisées pour Microsoft Defender rapports d’intégrité antivirus." lightbox="images/device-health-defender-antivirus-engine-version-details-custom-columns.png":::

#### <a name="new-microsoft-defender-antivirus-filter-definitions"></a>Nouvelles définitions de filtre antivirus Microsoft Defender

Le tableau suivant contient une liste de termes nouveaux pour Microsoft Defender rapports antivirus.

| Nom de colonne | Description |
|:---|:---|
| Heure de publication du renseignement de sécurité | Indique la date de publication de Microsoft de la version de mise à jour du renseignement de sécurité sur l’appareil. Les appareils dont la durée de publication des informations de sécurité est supérieure à sept jours sont considérés comme obsolètes dans les rapports. |
| Vu pour la dernière fois | Indique la date de la dernière connexion de l’appareil. |
| Horodatage de l’actualisation des données | Indique quand les événements client ont été reçus pour la dernière fois pour la création de rapports : mode AV, version du moteur AV, version de la plateforme AV, version du renseignement de sécurité AV et informations d’analyse. |
| Heure d’actualisation de la signature | Indique quand les événements clients ont été reçus pour la dernière fois pour la création de rapports sur l’état à jour du moteur, de la plateforme et de la signature. |

Dans le menu volant : en cliquant sur le nom de l’appareil, vous êtes redirigé vers la « page Appareil » de cet appareil, où vous pouvez accéder à des rapports détaillés.

#### <a name="export-report"></a>Exporter le rapport

Il existe deux niveaux de rapports que vous pouvez exporter :

##### <a name="top-level-export"></a>Exportation de niveau supérieur

Il existe deux fonctionnalités csv d’exportation différentes via le portail :

- **Exportation de niveau supérieur**. Vous pouvez utiliser le bouton **Exporter** de niveau supérieur pour collecter un rapport d’intégrité Microsoft Defender Antivirus (limite de 500 000).

   ::image type="content » source="images/device-health-defender-antivirus-health-tab-export.png » alt-text="Affiche le bouton d’exportation de rapport de niveau supérieur » lightbox="images/device-health-defender-antivirus-health-tab-export.png »:::

- **Exportation au niveau du menu volant**. Vous pouvez utiliser le bouton **Exporter** dans les menus volants pour exporter un rapport vers une feuille de calcul Excel (limite de 100 000).

Les rapports exportés capturent des informations en fonction de votre point d’entrée dans le rapport de détails et des filtres ou colonnes personnalisées que vous avez définis.

Pour plus d’informations sur l’exportation à l’aide de l’API, consultez les articles suivants :

- [Exportation du rapport de santé antivirus de l'appareil](device-health-export-antivirus-health-report-api.md)
- [Exporter les méthodes et propriétés de l’API des détails de l’antivirus de l’appareil](device-health-api-methods-properties.md)

> [!IMPORTANT]
>
> Actuellement, seule la **réponse JSON d’intégrité de l’antivirus** est en disponibilité générale. **L’API d’intégrité antivirus via des fichiers** n’est disponible qu’en préversion publique.
>
> **La requête personnalisée de chasse avancée** n’est actuellement disponible qu’en préversion publique, même si les requêtes sont toujours visibles.

### <a name="microsoft-defender-antivirus-version-and-update-cards-functionality"></a>Microsoft Defender fonctionnalités de la version de l’antivirus et des cartes de mise à jour

Voici une description des six cartes qui indiquent la _version_ et les informations de _mise à jour_ pour Microsoft Defender moteur antivirus, le renseignement de sécurité et les composants de la plateforme :

#### <a name="full-report"></a>Rapport complet

Dans l’une des trois cartes de _version_, sélectionnez **Afficher le rapport complet** pour afficher les neuf rapports de _version_ Microsoft Defender Antivirus les plus récents pour chacun des trois types d’appareils : Windows, Mac et Linux. S’il en existe moins de neuf, ils sont tous affichés. Une catégorie **Autre** capture les versions récentes du moteur antivirus au dixième rang et en dessous, si elles sont détectées.

:::image type="content" source="images/device-health-defender-antivirus-health-view-full-report.png" alt-text="Affiche la distribution des neuf premiers systèmes d’exploitation de chaque type" lightbox="images/device-health-defender-antivirus-health-view-full-report.png":::

L’un des principaux avantages des trois cartes de _version_ est qu’elles fournissent des indicateurs rapides indiquant si les versions les plus récentes des moteurs antivirus, des plateformes et du renseignement de sécurité sont utilisées. Associées aux informations détaillées liées à la carte, les cartes de versions deviennent un outil puissant pour vérifier si les versions sont à jour et collecter des informations sur des ordinateurs individuels ou des groupes d’ordinateurs.
Dans l’idéal, lorsque vous exécutez ces rapports, ils indiquent que les versions les plus récentes de l’antivirus sont installées, par opposition aux versions antérieures.
Utilisez ces rapports pour déterminer si votre organisation tire pleinement parti des versions les plus récentes.

:::image type="content" source="images/device-health-defender-antivirus-health-antivirus-details-up-to-date.png" alt-text="Affiche Microsoft Defender détails de la version de l’antivirus" lightbox="images/device-health-defender-antivirus-health-antivirus-details-up-to-date.png":::

Pour vous assurer que votre solution anti-programme malveillant détecte les dernières menaces, obtenez automatiquement les mises à jour dans le cadre de Windows Update.

Pour plus d’informations sur les versions actuelles et sur la façon de mettre à jour les différents composants antivirus Microsoft Defender, consultez [Microsoft Defender prise en charge de la plateforme antivirus](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="card-descriptions"></a>Descriptions des cartes

Voici de brefs résumés des informations collectées signalées dans chacune des cartes de _version de l’antivirus_ :

#### <a name="antivirus-mode-card"></a>Carte du mode antivirus

Rapports sur le nombre d’appareils de votre organisation (à la date indiquée sur la carte) dans l’un des modes antivirus Microsoft Defender suivants :

| valeur | mode |
|---|---|
| 0 | Actif |
| 1 | Passif |
| 2 | Désactivé (désinstallé, désactivé ou SideBySidePassive {également appelé Analyse périodique faible}) |
| 3 | Autres (Non en cours d’exécution, Inconnu) |
| 4 | EDRBlocked |

:::image type="content" source="images/device-health-defender-antivirus-health-antivirus-mode.png" alt-text="Affiche le filtrage Microsoft Defender modes antivirus" lightbox="images/device-health-defender-antivirus-health-antivirus-mode.png":::

Vous trouverez ci-dessous des descriptions pour chaque mode :

- **Mode actif** : en mode actif, Microsoft Defender’antivirus est utilisé comme application antivirus principale sur l’appareil. Les fichiers sont analysés, les menaces corrigées et les menaces détectées sont répertoriées dans les rapports de sécurité de votre organisation et dans votre application Sécurité Windows.
- **Mode passif** : en mode passif, Microsoft Defender’antivirus n’est pas utilisé comme application antivirus principale sur l’appareil. Les fichiers sont analysés et les menaces détectées sont signalées, mais les menaces ne sont pas corrigées par Microsoft Defender Antivirus. IMPORTANT : Microsoft Defender Antivirus peut fonctionner en mode passif uniquement sur les points d'extrémité qui sont intégrés à Microsoft Defender pour point de terminaison. Voir [Configuration requise pour que Microsoft Defender Antivirus fonctionne en mode passif ](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).
- **Mode Désactivé** : synonyme de : désinstallé, désactivé, sideBySidePassive et Analyse périodique faible. Lorsqu’il est désactivé, Microsoft Defender Antivirus n’est pas utilisé. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigées. En règle générale, Microsoft ne recommande pas de désactiver ou de désinstaller Microsoft Defender Antivirus.
- **Mode Autres** - Non en cours d’exécution, Inconnu
- **EDR en mode Bloc** : en mode de détection et réponse de point de terminaison (EDR) bloqué. Voir [Détection et réponse de point de terminaison en mode bloc](edr-in-block-mode.md)

Les appareils qui sont en mode passif, LPS ou Désactivé présentent un risque potentiel pour la sécurité et doivent être examinés.

Pour plus d’informations sur LPS, consultez [Utiliser une analyse périodique limitée dans Microsoft Defender Antivirus](limited-periodic-scanning-microsoft-defender-antivirus.md).

#### <a name="recent-antivirus-scan-results-card"></a>Carte des résultats de l’analyse antivirus récente

Cette carte comporte deux graphiques à barres affichant des résultats complets pour les analyses rapides et complètes. Dans les deux graphiques, la première barre indique le taux d’achèvement des analyses et indique **Terminé**, **Annulé** ou **Échec**. La deuxième barre de chaque section fournit les codes d’erreur pour les analyses ayant échoué.
En analysant les colonnes **Des** résultats de **l’analyse mode et Analyse récente** , vous pouvez identifier rapidement les appareils qui ne sont pas en mode d’analyse antivirus actif et les appareils qui ont échoué ou annulé des analyses antivirus récentes. Vous pouvez revenir au rapport avec ces informations et recueillir plus de détails et des recommandations de sécurité. Si des codes d’erreur sont signalés dans cette carte, vous trouverez un lien pour en savoir plus sur les codes d’erreur.

Pour plus d’informations sur les versions actuelles de l’antivirus Microsoft Defender et sur la façon de mettre à jour les différents composants de l’antivirus Microsoft Defender, consultez [Gérer les mises à jour de l’antivirus Microsoft Defender et appliquer les bases de référence](manage-updates-baselines-microsoft-defender-antivirus.md).

#### <a name="antivirus-engine-version-card"></a>Carte de version du moteur antivirus

Affiche les résultats en temps réel des versions les plus récentes du moteur antivirus Microsoft Defender installées sur les appareils Windows, les appareils Mac et les appareils Linux de votre organisation. Microsoft Defender moteur antivirus est mis à jour tous les mois.
Pour plus d’informations sur les versions actuelles et sur la mise à jour des différents composants antivirus Microsoft Defender, consultez [Microsoft Defender prise en charge de la plateforme antivirus](manage-updates-baselines-microsoft-defender-antivirus.md).

#### <a name="antivirus-security-intelligence-version-card"></a>Carte de version de l’antivirus Security Intelligence

Répertorie les versions les plus courantes _Microsoft Defender Antivirus Security Intelligence_ installées sur les appareils de votre réseau.
Microsoft met continuellement à jour Microsoft Defender intelligence de sécurité pour répondre aux dernières menaces et affiner la logique de détection. Ces améliorations apportées au renseignement de sécurité améliorent Microsoft Defender capacité de l’antivirus (et d’autres solutions microsoft anti-programme malveillant) à identifier avec précision les menaces potentielles. Cette intelligence de sécurité fonctionne directement avec la protection basée sur le cloud pour fournir une protection nouvelle génération, rapide et puissante, améliorée par l’IA.

##### <a name="antivirus-platform-version-card"></a>Carte de version de la plateforme antivirus

Affiche les résultats en temps réel des versions de plateforme antivirus Microsoft Defender les plus récentes installées sur les versions des appareils Windows, Mac et Linux de votre organisation. Microsoft Defender plateforme antivirus est mise à jour mensuellement.
Pour plus d’informations sur les versions actuelles et sur la façon de mettre à jour les différents composants antivirus Microsoft Defender, consultez [Microsoft Defender prise en charge de la plateforme antivirus](manage-updates-baselines-microsoft-defender-antivirus.md)

#### <a name="up-to-date-cards"></a>Cartes à jour

Les cartes à jour indiquent l’état à jour des versions de mise à jour du **moteur antivirus**, de **la plateforme antivirus** et de la mise à jour **de Security Intelligence** . Il existe trois états possibles : _à jour_ (« True »), _obsolète_ (« False »), et _aucune donnée disponible_ (« Inconnu »).

> [!IMPORTANT]
>
> La logique utilisée pour établir des déterminations à jour a récemment été améliorée et simplifiée. Le nouveau comportement est documenté dans cette section.

Les définitions des informations _à jour_, _obsolètes_ et _aucune donnée disponible_ sont fournies pour chaque carte ci-dessous.

Microsoft Defender Antivirus utilise les critères supplémentaires « Heure d’actualisation de la signature » (la dernière fois que l’appareil a communiqué avec les rapports à jour) pour créer des rapports et des déterminations à jour pour les mises à jour du moteur, de la plateforme et de la sécurité.

L’état à jour est automatiquement marqué comme « inconnu » ou « aucune donnée disponible » si l’appareil n’a pas communiqué avec les rapports depuis plus de sept jours (heure d’actualisation de la signature >7).

Pour plus d’informations sur les termes mentionnés ci-dessus, reportez-vous à la section : [New Microsoft Defender Antivirus filter definitions](#new-microsoft-defender-antivirus-filter-definitions)

> [!NOTE]
>
> Conditions **préalables** à la création de rapports à jour
>
> Les rapports à jour génèrent des informations pour les appareils qui répondent aux critères suivants :
>
> - Version du moteur : 1.1.19300.2+
> - Version de la plateforme : 4.18.2202.1+
> - Protection cloud activée
> - Système d’exploitation Windows*
>
>*Actuellement, les rapports à jour sont disponibles uniquement pour les appareils Windows. Les appareils multiplateformes tels que Mac et Linux sont répertoriés sous « Aucune donnée disponible »
>

##### <a name="up-to-date-definitions"></a>Définitions à jour

Voici les définitions à jour du moteur et de la plateforme :

| Le moteur/plateforme sur l’appareil est considéré comme suit : | Situation |
|:---|:---|
| **à jour** | Si l’appareil a communiqué avec l’événement de rapport Defender (« Heure d’actualisation de la signature ») au cours des sept derniers jours et que l’heure de génération de la version du moteur ou de la plateforme est au cours des 60 derniers jours. |
| **obsolète** | Si l’appareil a communiqué avec l’événement de rapport Defender (« Heure d’actualisation de la signature ») au cours des sept derniers jours, mais que l’heure de génération de la version du moteur ou de la plateforme est antérieure à 60 jours. |
| **inconnu (aucune donnée disponible)** | Si l’appareil n’a pas communiqué avec l’événement de rapport (« Heure d’actualisation de la signature ») depuis plus de sept jours. |

Voici les définitions de la veille de sécurité à jour :

| La mise à jour du renseignement de sécurité est prise en compte : | Situation |
|:---|:---|
|**à jour** | Si la version du renseignement de sécurité sur l’appareil a été écrite au cours des sept derniers jours et que l’appareil a communiqué avec l’événement de rapport au cours des sept derniers jours. |

Pour plus d’informations, consultez l’article suivant :

- [Carte de mise à jour du moteur antivirus](#antivirus-engine-updates-card)
- [Carte des mises à jour du renseignement de sécurité](#security-intelligence-updates-card)
- [Carte de mise à jour de la plateforme antivirus](#antivirus-platform-updates-card)

##### <a name="antivirus-engine-updates-card"></a>Carte de mise à jour du moteur antivirus

Cette carte identifie les appareils dont les versions de moteur antivirus sont à jour ou obsolètes.

**Définition générale de « à jour »** : la version du moteur sur l’appareil est la version la plus récente du moteur. Le moteur est _généralement_ publié tous les mois, via Windows Update (WU)). Il y a une période de grâce de trois jours donnée à partir du jour où Windows Update (WU) est libéré.

Le tableau suivant présente les valeurs possibles pour les rapports à jour pour **le moteur antivirus**. L’état signalé est basé sur la dernière fois que l’événement de création de rapports a été reçu (_heure d’actualisation de la signature_). Si l’appareil n’a pas communiqué avec les rapports depuis plus de sept jours (heure d’actualisation de la signature >7 jours), l’état est automatiquement marqué comme « Inconnu » / « Aucune donnée disponible ».

| Heure de la dernière actualisation de l’événement (également appelée « Heure d’actualisation de la signature » dans les rapports) | _État signalé_ : |
|:----|:----|
| < 7 jours (nouveau) | tout rapport client (_à jour <br/> Obsolète <br/> inconnu)_ |
| > 7 jours (ancienne) | _Unknown_ |

Pour plus d’informations sur la gestion des versions de mise à jour de l’antivirus Microsoft Defender, consultez [Versions mensuelles de la plateforme et du moteur](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

#### <a name="antivirus-platform-updates-card"></a>Carte de mise à jour de la plateforme antivirus

Cette carte identifie les appareils dont les versions de plateforme antivirus sont à jour ou obsolètes.

**La définition générale de « à jour »** est que la version de la plateforme sur l’appareil est la version la plus récente de la plateforme. La plateforme est _généralement_ publiée tous les mois, via Windows Update (WU). Il y a une période de grâce de trois jours à partir du jour où WU est libéré.

Le tableau suivant présente les valeurs de rapport à jour possibles pour **antivirus Platform**. Les valeurs signalées sont basées sur la dernière fois que l’événement de création de rapports a été reçu (heure d’actualisation de la signature). Si l’appareil n’a pas communiqué avec les rapports depuis plus de sept jours (heure d’actualisation de la signature >7 jours), l’état est automatiquement marqué comme « Inconnu » ou « Aucune donnée disponible ».

| Heure de la dernière actualisation de l’événement (également appelée « Heure d’actualisation de la signature » dans les rapports) | _État signalé_ |
|:----|:----|
| < 7 jours (nouveau) | tout rapport client (_à jour <br/> Obsolète <br/> inconnu)_ |
| > 7 jours (ancienne) | _Unknown_ |

Pour plus d’informations sur la gestion des versions de mise à jour de l’antivirus Microsoft Defender, consultez [Versions mensuelles de la plateforme et du moteur](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

##### <a name="security-intelligence-updates-card"></a>Carte des mises à jour du renseignement de sécurité

Cette carte identifie les appareils dont les versions de veille de sécurité sont à jour ou obsolètes.

**La définition générale de « à jour »** est que la version du renseignement de sécurité sur l’appareil a été écrite au cours des 7 derniers jours.

Le tableau suivant présente les valeurs de rapport à jour possibles pour les mises à jour **du renseignement de sécurité** . Les valeurs signalées sont basées sur la dernière fois que l’événement de création de rapports a été reçu et l’heure de publication du renseignement de sécurité. Si l’appareil n’a pas communiqué avec les rapports depuis plus de sept jours (heure d’actualisation de la signature >7 jours), l’état est automatiquement marqué comme « Inconnu/Aucune donnée disponible ». Dans le cas contraire, la détermination est basée sur la question de savoir si le délai de publication des renseignements de sécurité est dans les sept jours.

| Heure de la dernière actualisation de l’événement <br/> (Également appelé « Heure d’actualisation de la signature » dans les rapports) | Heure de publication de Security Intelligence | _État signalé_ |
|:----|:----|:----|
| >7 jours (ancienne) | >7 jours (ancienne) | _Unknown_ |
| <7 jours (nouveau) | >7 jours (ancienne) | _Obsolète_ |
| >7 jours (ancienne) | <7 jours (nouveau) | _Unknown_ |
| <7 jours (nouveau) | <7 jours (nouveau) | Actuel |

## <a name="see-also"></a>Voir aussi

- [Exporter les méthodes et propriétés de l’API des détails de l’antivirus de l’appareil](device-health-api-methods-properties.md)
- [Exportation du rapport de santé antivirus de l'appareil](device-health-api-methods-properties.md)
- [Rapport de protection contre les menaces](threat-protection-reports.md)

> [!TIP]
> Pour plus d’informations sur les antivirus pour d’autres plateformes, consultez :
>
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
