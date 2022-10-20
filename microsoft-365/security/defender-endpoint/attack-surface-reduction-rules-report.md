---
title: Rapports de règles de réduction de la surface d’attaque (ASR)
description: Fournit des informations sur les détections de règles de réduction de la surface d’attaque (ASR), la configuration, les menaces de blocage et les méthodes pour activer trois règles et exclusions standard.
keywords: Règles de réduction de la surface d’attaque, ASR, règles asr, hanches, système de prévention des intrusions de l’hôte, règles de protection, règles anti-exploitation, antiexploitation, règles d’exploitation, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles ASR, description des règles ASR
ms.mktglfcycl: manage
ms.sitesec: library
ms.service: microsoft-365-security
ms.subservice: mde
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar,
manager: dansimp
ms.custom: asr
ms.topic: conceptual
ms.collection:
- m365-security
- tier2
ms.date: 08/25/2022
search.appverid: met150
ms.openlocfilehash: 71f3ca2deba321624c1ec529ea0a74c638b12638
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631719"
---
# <a name="attack-surface-reduction-asr-rules-report"></a>Rapport de règles de réduction de la surface d’attaque (ASR)

**S’applique à :**

- [Microsoft Microsoft 365 Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plates-formes:**

- Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Le rapport de règles de réduction de la surface d’attaque (ASR) fournit des informations sur les _règles de réduction de la surface d’attaque_ appliquées aux appareils de votre organisation. Ce rapport fournit également des informations sur les éléments suivants :

- menaces détectées
- menaces bloquées
- appareils qui ne sont pas configurés pour utiliser les règles de protection standard pour bloquer les menaces

En outre, ce rapport fournit une interface facile à utiliser qui vous permet d’effectuer les opérations suivantes :

- Afficher les détections de menaces
- Afficher la configuration des règles ASR
- Configurer (ajouter) des exclusions
- Activez facilement la _protection de base_ en activant les trois règles ASR les plus recommandées avec un seul bouton bascule
- Descendre dans la page pour collecter des informations détaillées

Pour plus d’informations sur les règles de réduction de la surface d’attaque individuelles, consultez [la référence des règles de réduction de la surface](attack-surface-reduction-rules-reference.md) d’attaque.

## <a name="prerequisites"></a>Configuration requise

> [!IMPORTANT]
> Pour que Windows&nbsp;Server&nbsp;2012&nbsp;R2 et Windows&nbsp;Server&nbsp;2016 apparaissent dans le **rapport des règles de réduction de la surface d’attaque**, ces appareils doivent être intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution).

## <a name="report-access-permissions"></a>Autorisations d’accès aux rapports

Pour accéder au **rapport des règles de réduction de la surface d’attaque** dans le tableau de bord Sécurité Microsoft 365, les autorisations suivantes sont requises :

| Type d’autorisation | Autorisation | Nom d’affichage de l’autorisation |
|:---|:---|:---|
| Application | Machine.Read.All | 'Lire tous les profils d’ordinateur' |
|Déléguée (compte professionnel ou scolaire) | Machine.Read | « Lire les informations de l’ordinateur » |

Pour attribuer ces autorisations :

1. Connectez-vous à Microsoft 365 Defender à l’aide <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">d’un</a> compte avec un rôle d’administrateur de sécurité ou de Administrateur général attribué.
1. Dans le volet de navigation, sélectionnez **Paramètres des rôles** \> **de points de terminaison** \> (sous **Autorisations**).
1. Sélectionnez le rôle que vous souhaitez modifier.
1. Sélectionnez **Modifier**.
1. Dans **Modifier le rôle**, sous l’onglet **Général** , dans **le nom** du rôle, tapez un nom pour le rôle.
1. Dans **Description** , tapez un bref résumé du rôle.
1. Dans **Autorisations**, sélectionnez **Afficher les données**, puis sous **Afficher les données** , sélectionnez Réduction de **la surface d’attaque**.

Pour plus d’informations sur la gestion des rôles d’utilisateur, consultez [Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle](user-roles.md).

## <a name="navigation"></a>Navigation

Pour accéder aux cartes récapitulatives du rapport sur les règles de réduction de la surface d’attaque

1. Ouvrez **Microsoft 365 Defender** portail.
1. Dans le volet gauche, cliquez sur **Rapports** et, dans la section principale, sous **Rapports** , sélectionnez **Rapport de sécurité**.
1. Faites défiler jusqu’aux **appareils** pour trouver les cartes récapitulatives des **règles de réduction de la surface d’attaque** .

Les cartes de rapport récapitulatives pour les règles ASR sont indiquées dans la figure suivante.

>:::image type="content" source="images/attack-surface-reduction-rules-report-summary.png" alt-text="Affiche les cartes récapitulatives du rapport des règles ASR" lightbox="images/attack-surface-reduction-rules-report-summary.png":::

## <a name="asr-rules-report-summary-cards"></a>Cartes récapitulatives du rapport des règles ASR

Le résumé du rapport de règles ASR est divisé en deux cartes :

- [Carte récapitulative **des détections de règle ASR**](#asr-rules-detections-summary-card)
- [Carte récapitulative de **configuration de règle ASR**](#asr-rules-configuration-summary-card)

### <a name="asr-rules-detections-summary-card"></a>Carte récapitulative des détections de règles ASR

Affiche un résumé du nombre de menaces détectées bloquées par les règles ASR.

Fournit deux boutons « action » :

- Afficher les détections : ouvre les **règles de réduction de la surface d’attaque** >'onglet **Détections** principale
- Ajouter des exclusions : ouvre les **règles de réduction de la surface d’attaque** >'onglet **Exclusions** principal

:::image type="content" source="images/attack-surface-reduction-rules-report-main-detections-card.png" alt-text="Affiche la carte de détections récapitulatives du rapport de règles ASR." lightbox="images/attack-surface-reduction-rules-report-main-detections-card.png":::

Cliquer sur le lien **détections de règles ASR** en haut de la carte ouvre également [l’onglet Détections des règles de réduction de la surface d’attaque](#attack-surface-reduction-rules-main-detections-tab) principal.

### <a name="asr-rules-configuration-summary-card"></a>Carte récapitulative de configuration des règles ASR

**La section supérieure** se concentre sur trois règles recommandées, qui protègent contre les techniques d’attaque courantes. Cette carte affiche des informations d’état actuel sur les ordinateurs de votre organisation dont les [trois \(règles de protection standard ASR\)](#simplified-standard-protection-option) suivantes sont définies en **mode bloc**, **en mode Audit** ou **désactivées** (non configurées). Le bouton **Protéger les appareils** affiche des détails de configuration complets uniquement pour les trois règles ; les clients peuvent rapidement prendre des mesures pour activer ces règles.

**La section inférieure** présente six règles en fonction du nombre d’appareils non protégés par règle. Le bouton « Afficher la configuration » affiche tous les détails de la configuration pour toutes les règles ASR. Le bouton « Ajouter une exclusion » affiche la page Ajouter une exclusion avec tous les noms de fichiers/processus détectés répertoriés pour le Centre d’opérations de sécurité (SOC) à évaluer. La page **Ajouter une exclusion** est liée à Microsoft Endpoint Manager (MEM).

Fournit deux boutons « action » :

- Configuration de l’affichage : ouvre les **règles de réduction de la surface d’attaque** >'onglet **Détections** principale
- Ajouter des exclusions : ouvre les **règles de réduction de la surface d’attaque** >'onglet **Exclusions** principal

:::image type="content" source="images/attack-surface-reduction-rules-report-main-detections-configuration-card.png" alt-text="Affiche la carte de configuration récapitulative du rapport de règles ASR." lightbox="images/attack-surface-reduction-rules-report-main-detections-configuration-card.png":::

Cliquer sur le lien de **configuration des règles ASR** en haut de la carte ouvre également [l’onglet Configuration des règles de réduction de la surface d’attaque](#attack-surface-reduction-rules-main-configuration-tab) principal.

#### <a name="simplified-standard-protection-option"></a>Option de protection standard simplifiée

La carte récapitulative de configuration fournit un bouton pour **protéger les appareils** avec les trois règles de protection standard. Au minimum, Microsoft vous recommande d’activer ces trois règles de protection standard de réduction de la surface d’attaque :

- [Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](attack-surface-reduction-rules-reference.md#block-credential-stealing-from-the-windows-local-security-authority-subsystem)
- [Bloquer l’abus de pilotes signés vulnérables exploités](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers)
- [Bloquer la persistance via l’abonnement aux événements WMI (Windows Management Instrumentation)](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription)

Pour activer les trois règles de protection standard :

1. Sélectionnez **Protéger les appareils**. **L’onglet Configuration principal s’ouvre**.
1. Sous l’onglet **Configuration** , **les règles de base** basculent automatiquement de **Toutes les règles** vers **les règles de protection Standard** activées.
1. Dans la liste **Des appareils** , sélectionnez les appareils pour lesquels vous souhaitez appliquer les règles de protection standard, puis **sélectionnez Enregistrer**.

Cette carte comporte deux autres boutons de navigation :

- **Configuration de l’affichage** : ouvre les **règles de réduction de la surface d’attaque** >'onglet **Configuration** principal.
- **Ajouter des exclusions** : ouvre les **règles de réduction de la surface d’attaque** >'onglet **Exclusions** principal.

Cliquer sur le lien de **configuration des règles ASR** en haut de la carte ouvre également [l’onglet Configuration des règles de réduction de la surface d’attaque](#attack-surface-reduction-rules-main-configuration-tab) principal.

## <a name="attack-surface-reduction-rules-main-tabs"></a>Onglets principaux des règles de réduction de la surface d’attaque

Bien que les cartes récapitulatives des rapports de règles ASR soient utiles pour obtenir un résumé rapide de l’état de vos règles ASR, les onglets principaux fournissent des informations plus détaillées avec des fonctionnalités de filtrage et de configuration :

- [Onglet Détections](#attack-surface-reduction-rules-main-detections-tab)
- [Onglet Configuration](#attack-surface-reduction-rules-main-configuration-tab)
- [Onglet Exclusions](#attack-surface-reduction-rules-add-exclusions-tab)

### <a name="search-capabilities"></a>Fonctionnalités de recherche

 La fonctionnalité de recherche est ajoutée aux onglets principaux **Détection**, **Configuration** et **Ajout d’exclusion** . Avec cette fonctionnalité, vous pouvez effectuer une recherche à l’aide de l’ID d’appareil, du nom de fichier ou du nom du processus.

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-tabs-search.png" alt-text="Affiche la fonctionnalité de recherche de rapport de règles ASR." lightbox="images/attack-surface-reduction-rules-report-main-tabs-search.png":::

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-tabs-search-configuration-tab.png" alt-text="Affiche la fonctionnalité de recherche de rapport de règles ASR sous l’onglet Configuration." lightbox="images/attack-surface-reduction-rules-report-main-tabs-search-configuration-tab.png":::

### <a name="filtering"></a>Filtrage

Le filtrage vous permet de spécifier les résultats retournés :

- **La date**  vous permet de spécifier une plage de dates pour les résultats de données.
- **Filters**

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-detections-filtering.png" alt-text="Affiche la fonctionnalité de filtrage des rapports de règles ASR" lightbox="images/attack-surface-reduction-rules-report-main-detections-filtering.png":::

### <a name="attack-surface-reduction-rules-main-detections-tab"></a>Onglet Détections principales des règles de réduction de la surface d’attaque

- **Détections d’audit**  Indique le nombre de détections de menaces capturées par les règles définies en mode _Audit_ .
- **Détections bloquées** Indique le nombre de détections de menaces bloquées par des règles définies en mode _bloc_ .
- **Graphe volumineux et consolidé** Affiche les détections bloquées et auditées.

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-detections-tab.png" alt-text="Affiche l’onglet Détections principales du rapport de règles ASR, avec _Audit detections_ et _Blocked detections_ décrits." lightbox="images/attack-surface-reduction-rules-report-main-detections-tab.png":::

Les graphiques fournissent des données de détection sur la plage de dates affichée, avec la possibilité de pointer sur un emplacement spécifique pour collecter des informations spécifiques à la date.

La section inférieure du rapport répertorie les menaces détectées , par appareil, avec les champs suivants :

| Nom du champ| Définition |
|:---|:---|
| Fichier détecté | Fichier déterminé pour contenir une menace possible ou connue |
| Détecté le | Date à laquelle la menace a été détectée |
| Bloqué audité\/? | Indique si la règle de détection de l’événement spécifique était en mode Bloc ou Audit |
| Rule | Quelle règle a détecté la menace ? |
| Application source | Application qui a effectué l’appel au « fichier détecté » incriminé |
| Device | Nom de l’appareil sur lequel l’événement Audit ou Bloquer s’est produit |
| Groupe d’appareils | Groupe Active Directory auquel appartient l’appareil |
| Utilisateur |  Compte d’ordinateur responsable de l’appel |
| Éditeur | L’entreprise qui a publié l'.exe ou l’application particulière |

Pour plus d’informations sur les modes d’audit et de bloc des règles ASR, consultez [Modes de règle de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md#asr-rule-modes).

#### <a name="actionable-flyout"></a>Menu volant actionnable

La page principale « Détection » contient la liste de toutes les détections (fichiers/processus) au cours des 30 derniers jours. Sélectionnez l’une des détections à ouvrir avec des fonctionnalités d’exploration.

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-detections-flyout.png" alt-text="Affiche le menu volant de l’onglet Détections principales du rapport de règles ASR" lightbox="images/attack-surface-reduction-rules-report-main-detections-flyout.png":::

La section **Exclusion et impact possibles** fournit l’impact du fichier ou du processus sélectionné. Vous pouvez :

- Sélectionnez **Go Hunt** qui ouvre la page de requête De chasse avancée
- **La page Ouvrir le fichier** ouvre Microsoft Defender pour point de terminaison détection (MDE)
- Le bouton **Ajouter une exclusion** est lié à la page principale Ajouter une exclusion.

L’image suivante montre comment la page de requête De chasse avancée s’ouvre à partir du lien sur le menu volant actionnable :

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-detections-flyout-hunting.png" alt-text="Affiche le lien volant de l’onglet Détections principales du rapport des règles (ASR) ouvrant la chasse avancée" lightbox="images/attack-surface-reduction-rules-report-main-detections-flyout-hunting.png":::

Pour plus d’informations sur la chasse avancée, consultez [La chasse proactive contre les menaces avec la chasse avancée dans Microsoft 365 Defender](advanced-hunting-overview.md)

### <a name="attack-surface-reduction-rules-main-configuration-tab"></a>Onglet Configuration principal des règles de réduction de la surface d’attaque

L’onglet **Configuration** principal des règles ASR fournit des détails de configuration des règles ASR récapitulatives et par appareil. L’onglet Configuration comporte trois aspects principaux :

**Règles de base** Fournit une méthode permettant de basculer les résultats entre **les règles de base** et **toutes les règles**. Par défaut, **les règles de base** sont sélectionnées.

**Vue d’ensemble de la configuration de l’appareil** Fournit un instantané actuel des appareils dans l’un des états suivants :

- Tous les appareils exposés (appareils avec prérequis manquants, règles en mode Audit, règles mal configurées ou règles non configurées)
- Appareils avec des règles non configurées
- Appareils avec des règles en mode audit
- Appareils avec des règles en mode bloc

**La section inférieure sans nom** de l’onglet Configuration fournit une liste de l’état actuel de vos appareils (par appareil) :

- Appareil (nom)
- Configuration globale (si toutes les règles sont activées ou désactivées)
- Règles en mode bloc (nombre de règles par appareil définies pour bloquer)
- Règles en mode audit (nombre de règles en mode audit)
- Règles désactivées (règles désactivées ou non activées)
- ID d’appareil (GUID d’appareil)

Ces éléments sont illustrés dans la figure suivante.

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-configuration-tab.png" alt-text="Affiche l’onglet configuration principale du rapport de règles ASR" lightbox="images/attack-surface-reduction-rules-report-main-configuration-tab.png":::

Pour activer les règles ASR :

1. Sous **Appareil**, sélectionnez l’appareil ou les appareils pour lesquels vous souhaitez appliquer des règles ASR.
1. Dans la fenêtre de menu volant, vérifiez vos sélections, puis sélectionnez **Ajouter à la stratégie**.

**L’onglet Configuration** et le menu volant _Ajouter une règle_ sont affichés dans l’image suivante.

> [REMARQUE!] Si vous avez des appareils qui nécessitent l’application de différentes règles ASR, vous devez les configurer individuellement.

>:::image type="content" source="images/attack-surface-reduction-rules-report-configuration-add-to-policy.png" alt-text="Affiche le menu volant des règles ASR pour ajouter des règles ASR aux appareils" lightbox="images/attack-surface-reduction-rules-report-configuration-add-to-policy.png":::

### <a name="attack-surface-reduction-rules-add-exclusions-tab"></a>Onglet Ajouter des exclusions des règles de réduction de la surface d’attaque

L’onglet **Ajouter des exclusions** présente une liste classée de détections par nom de fichier et fournit une méthode pour configurer les exclusions. Par défaut, **les informations Ajouter des exclusions** sont répertoriées pour trois champs :

- **Nom du fichier** Nom du fichier qui a déclenché l’événement de règles ASR.
- **Détections** Nombre total d’événements détectés pour le fichier nommé. Les appareils individuels peuvent déclencher plusieurs événements de règles ASR.
- **Dispositifs** Nombre d’appareils sur lesquels la détection s’est produite.

>:::image type="content" source="images/attack-surface-reduction-rules-report-exclusion-tab.png" alt-text="Affiche l’onglet Ajouter des exclusions du rapport de règles ASR" lightbox="images/attack-surface-reduction-rules-report-exclusion-tab.png":::

> [!IMPORTANT]
> L’exclusion de fichiers ou de dossiers peut réduire considérablement la protection fournie par les règles ASR. Les fichiers exclus sont autorisés à s’exécuter et aucun rapport ou événement n’est enregistré.
> Si les règles ASR détectent des fichiers qui, selon vous, ne doivent pas être détectés, vous devez [d’abord utiliser le mode audit pour tester la règle](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit).

Lorsque vous sélectionnez un fichier, un **résumé &'impact attendu** s’ouvre, présentant les types d’informations suivants :

- **Fichiers sélectionnés**  Nombre de fichiers que vous avez sélectionnés pour exclusion
- **(_nombre de_) détections**  Indique la réduction attendue des détections après l’ajout des exclusions sélectionnées.  La réduction des détections est représentée graphiquement pour **les détections réelles** et **les détections après exclusions**
- **(_nombre d'_) appareils affectés** Indique la réduction attendue des appareils qui signalent les détections pour les exclusions sélectionnées.

La page Ajouter une exclusion comporte deux boutons pour les actions qui peuvent être utilisées sur tous les fichiers détectés (après sélection). Vous pouvez :

- **Ajoutez une exclusion** qui ouvre la page de stratégie ASR Microsoft Endpoint Manager (MEM). Pour plus d’informations, consultez : [MEM](https://enable-attack-surface-reduction.md#mem) dans « Enable ASR rules alternate configuration methods ».
- **Obtenir les chemins d’exclusion** qui téléchargent les chemins d’accès aux fichiers dans un format csv

>:::image type="content" source="images/attack-surface-reduction-rules-report-main-add-exclusions-flyout.png" alt-text="Affiche le résumé de l’impact du menu volant de l’onglet Ajouter des exclusions dans le rapport de règles ASR" lightbox="images/attack-surface-reduction-rules-report-main-add-exclusions-flyout.png":::

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment.md)
- [Planifier le déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-plan.md)
- [Tester des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-test.md)
- [Activer des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-implement.md)
- [Utiliser des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)
- [Rapport des règles ASR\) de réduction de \(la surface d’attaque](attack-surface-reduction-rules-report.md)
- [Référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)
