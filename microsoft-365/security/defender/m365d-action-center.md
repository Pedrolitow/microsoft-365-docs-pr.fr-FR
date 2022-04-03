---
title: Accéder au centre de notifications pour afficher et approuver vos tâches d’enquête et de correction automatisées
description: Utiliser le centre de gestion des actions pour afficher les détails sur l’examen automatisé et approuver les actions en attente
keywords: Centre de gestion des menaces, protection contre les menaces, examen, alerte, en attente, automatisé, détection
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 0bd86f7ba05ce04743f547292105875f3b8234b1
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499064"
---
# <a name="the-action-center"></a>Centre de notifications

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le centre de sécurité fournit une expérience de « volet unique » pour les tâches d’incident et d’alerte telles que :

- Approbation des actions de correction en attente.
- Affichage d’un journal d’audit des actions de correction déjà approuvées.
- Évaluation des actions de correction terminées.

Étant donné que le centre de gestion des actions offre une vue complète des Microsoft 365 Defender au travail, votre équipe des opérations de sécurité peut fonctionner plus efficacement.

## <a name="the-unified-action-center"></a>Centre de l’action unifiée

Le centre de actions unifié ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) répertorie les actions de correction en attente et terminées pour vos appareils, la messagerie & contenu de collaboration et les identités dans un seul emplacement.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Centre de actions unifié dans le portail Microsoft 365 Defender’entreprise." lightbox="../../media/m3d-action-center-unified.png":::

Par exemple : 

- Si vous utilisiez précédemment le Centre Office 365 sécurité & conformité ([https://protection.office.com](https://protection.office.com)), essayez le centre de actions unifié dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le portail Microsoft 365 Defender client</a>.
- Si vous utilisiez le centre de actions dans le Centre de sécurité Microsoft Defender ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)), essayez le centre de actions unifié dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le Microsoft 365 Defender web</a>.
- Si vous utilisiez déjà <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le portail Microsoft 365 Defender</a>, vous verrez plusieurs améliorations dans le centre de actions ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

Le centre de mise en œuvre unifié regroupe les actions de correction dans Defender pour Le point de terminaison et Defender pour Office 365. Il définit un langage commun pour toutes les actions de correction et fournit une expérience d’examen unifiée. Votre équipe des opérations de sécurité dispose d’une expérience de « volet unique » pour afficher et gérer les actions de correction.  

Vous pouvez utiliser le centre de l’action unifiée si vous avez les autorisations appropriées et un ou plusieurs des abonnements suivants :

- [Defender pour point de terminaison](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Pour plus d’informations, voir [Requirements](./prerequisites.md).

## <a name="using-the-action-center"></a>Utilisation du centre de l’action

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> and sign in. 
2. Dans le volet de navigation, choisissez **Centre de notifications**. 

Lorsque vous visitez le centre de actions, vous voyez deux onglets : **Actions en attente et** **Historique**. Le tableau suivant récapitule ce que vous verrez sur chaque onglet :

|Tab  |Description  |
|---------|---------|
|**Pending**     | Affiche une liste d’actions qui nécessitent une attention particulière. Vous pouvez approuver ou rejeter des actions une par une, ou sélectionner plusieurs actions si elles ont le même type d’action (par exemple, un fichier de mise en quarantaine). <p>**CONSEIL** : veillez à examiner et à approuver (ou rejeter) les actions en attente dès que possible afin que vos enquêtes automatisées se terminent en temps voulu.       |
|**Historique**     | Sert de journal d’audit pour les actions qui ont été entreprises, telles que : <br/>- Mesures correctives prises à la suite d’enquêtes automatisées <br/>- Mesures correctives qui ont été prises sur des messages électroniques suspects ou malveillants, des fichiers ou des URL<br/>- Actions de correction approuvées par votre équipe des opérations de sécurité <br/>- Commandes qui ont été exécutés et actions de correction appliquées pendant les sessions Live Response<br/>- Mesures correctives prises par votre protection antivirus <p>Permet d’annuler certaines actions (voir [Annuler les actions terminées](m365d-autoir-actions.md#undo-completed-actions)).        |

Vous pouvez personnaliser, trier, filtrer et exporter des données dans le centre de gestion de l’action.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="Fonctionnalités de tri, de filtrage et de personnalisation du centre de gestion de l’action." lightbox="../../media/m3d-action-center-columnsfilters.png":::

- Sélectionnez un en-tête de colonne pour trier les éléments par ordre croissant ou décroit.
- Utilisez le filtre de période pour afficher les données du jour, de la semaine, des 30 ou 6 derniers mois.
- Choisissez les colonnes que vous souhaitez afficher.
- Spécifiez le nombre d’éléments à inclure sur chaque page de données.
- Utilisez des filtres pour afficher uniquement les éléments que vous souhaitez voir.
- **Sélectionnez Exporter** pour exporter les résultats vers .csv fichier.

## <a name="actions-tracked-in-the-action-center"></a>Actions suivis dans le centre de l’action

Toutes les actions de correction, qu’elles soient en attente d’approbation ou qu’elles aient déjà été approuvées, sont regroupées dans le Centre de notifications. Les actions disponibles sont les suivantes :

- Collecter un package d’examen 
- Isoler l’appareil (cette action peut être annulée) 
- Annuler l’intégration de l’ordinateur 
- Exécution du code de publication 
- Diffusion des messages en quarantaine 
- Demander un exemple 
- Restreindre l’exécution du code (cette action peut être annulée) 
- Exécuter une analyse antivirus 
- Arrêter et mettre en quarantaine 

En plus des actions de correction qui sont prises automatiquement à la suite d’enquêtes automatisées[, le](m365d-autoir.md) centre de mesures suit également les actions que votre équipe de sécurité a prises pour traiter les menaces détectées et les actions qui ont été prises à la suite des fonctionnalités de protection contre les menaces dans Microsoft 365 Defender. Pour plus d’informations sur les actions de correction automatiques et manuelles, voir [Actions de correction](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Affichage des détails de la source de l’action

(**NOUVEAU !**) Le centre de l’action amélioré inclut désormais une colonne **source Action** qui vous indique d’où chaque action vient. Le tableau suivant décrit les valeurs possibles de **la source d’action** :

| Valeur de la source d’action | Description |
|:-----|:---|
| **Action manuelle de l’appareil** | Action manuelle sur un appareil. Par exemple, [l’isolation de l’appareil](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) ou [la mise en quarantaine des fichiers](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **Action de messagerie manuelle** | Action manuelle sur le courrier électronique. Il peut s’agit, par exemple, de la suppression de messages électroniques ou de la [correction d’un message électronique](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Action automatisée sur l’appareil** | Action automatisée entreprise sur une entité, telle qu’un fichier ou un processus. L’envoi d’un fichier en quarantaine, l’arrêt d’un processus et la suppression d’une clé de Registre sont des exemples d’actions automatisées. (Voir [actions de correction dans Microsoft Defender pour le point de terminaison](../defender-endpoint/manage-auto-investigation.md#remediation-actions).) |
| **Action de messagerie automatisée** | Action automatisée sur le contenu du courrier électronique, telle qu’un message électronique, une pièce jointe ou une URL. Parmi les exemples d’actions automatisées, citons la suppression (à l’aide de logiciels) des messages électroniques, le blocage des URL et la désinstruction du forwarding de courrier externe. (Voir [les actions de correction dans Microsoft Defender pour Office 365](../office-365-security/air-remediation-actions.md).) |
| **Action de recherche avancée** | Actions prises sur des appareils ou des e-mails avec [un chasse avancée](./advanced-hunting-overview.md). |
| **Action de l’explorateur** | Actions prises sur le contenu du courrier électronique avec [l’Explorateur](../office-365-security/threat-explorer.md). |
| **Action de réponse en direct manuelle** | Actions prises sur un appareil avec [réponse en direct](../defender-endpoint/live-response.md). Par exemple, la suppression d’un fichier, l’arrêt d’un processus et la suppression d’une tâche programmée. |
| **Action de réponse en direct** | Actions prises sur un appareil à [l’aide des API Microsoft Defender pour les points de terminaison](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). L’isolation d’un appareil, l’exécution d’une analyse antivirus et l’obtention d’informations sur un fichier sont des exemples d’actions. |

## <a name="required-permissions-for-action-center-tasks"></a>Autorisations requises pour les tâches du centre de notifications

Pour effectuer des tâches, telles que l’approbation ou le rejet des actions en attente dans le centre de actions, vous devez avoir des autorisations attribuées comme répertoriés dans le tableau suivant :

|Action de correction |Rôles et des autorisations requis |
|--|----|
|Correction de Microsoft Defender pour les points de terminaison (appareils) |**Rôle Administrateur de** la sécurité attribué dans Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) ou le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- ou ---<br/>**Rôle des actions de** correction actives attribué dans Microsoft Defender pour le point de terminaison <br/> <br/> Pour en savoir plus, consultez les ressources suivantes : <br/>- [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference)<br/>- [Créer et gérer des rôles pour le contrôle d’accès basé sur un rôle (Microsoft Defender pour point de terminaison)](../defender-endpoint/user-roles.md)  |
|Microsoft Defender pour la correction Office 365 (contenu Office courrier électronique)  |**Rôle Administrateur de** la sécurité attribué dans Azure AD ([https://portal.azure.com](https://portal.azure.com)) ou le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- et --- <br/>**Rôle de recherche et** de purge attribué dans le Centre de sécurité & conformité ([https://protection.office.com](https://protection.office.com)) <br/><br/>**IMPORTANT :** si le rôle Administrateur  de la sécurité est attribué uniquement dans le Centre de sécurité & conformité Office 365 ([https://protection.office.com](https://protection.office.com)), vous ne pourrez pas accéder aux fonctionnalités du centre de Microsoft 365 Defender de sécurité. Le **rôle Administrateur de** la sécurité doit être attribué dans Azure AD ou le Centre d'administration Microsoft 365. <br/><br/>Pour en savoir plus, consultez les ressources suivantes : <br/>- [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference)<br/>- [Autorisations dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Les utilisateurs qui ont **le rôle d’administrateur** général Azure AD peuvent approuver ou rejeter toute action en attente dans le centre de gestion des actions. Toutefois, en tant que meilleure pratique, votre organisation doit limiter le nombre de personnes à  qui le rôle Administrateur général est attribué. Nous vous recommandons d’utiliser l’administrateur de **sécurité, les** actions de correction **actives** et les rôles De recherche et de purge répertoriés dans le tableau précédent pour les autorisations du centre de gestion des actions.

## <a name="next-step"></a>Étape suivante 

- [Afficher et gérer les actions de correction](m365d-autoir-actions.md)
