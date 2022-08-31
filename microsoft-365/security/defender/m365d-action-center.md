---
title: Accéder au centre de notifications pour afficher et approuver vos tâches d’enquête et de correction automatisées
description: Utiliser le Centre d’actions pour afficher des détails sur l’investigation automatisée et approuver les actions en attente
keywords: Centre d’action, protection contre les menaces, investigation, alerte, en attente, automatisée, détection
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 07/27/2022
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
ms.openlocfilehash: 9a44ea87a38228c5ec012f0fe507bb3c9d6f66bb
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67475479"
---
# <a name="the-action-center"></a>Centre de notifications

**S’applique à :**
- Microsoft 365 Defender

Le centre d’action fournit une expérience « unique volet de verre » pour les tâches d’incident et d’alerte telles que :

- Approbation des actions de correction en attente.
- Affichage d’un journal d’audit des actions de correction déjà approuvées.
- Évaluation des actions de correction terminées.

Étant donné que le Centre d’action fournit une vue complète des Microsoft 365 Defender au travail, votre équipe des opérations de sécurité peut fonctionner plus efficacement et plus efficacement.

## <a name="the-unified-action-center"></a>Centre d’action unifié

Le centre d’actions unifié ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) répertorie les actions de correction en attente et terminées pour vos appareils, le courrier électronique & le contenu de collaboration et les identités dans un seul emplacement.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Centre d’action unifié dans le portail Microsoft 365 Defender." lightbox="../../media/m3d-action-center-unified.png":::

Par exemple : 

- Si vous utilisiez précédemment le Centre de conformité & sécurité Office 365 ([https://protection.office.com](https://protection.office.com)), essayez le centre d’action unifié dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.
- Si vous utilisiez le centre d’action dans le Centre de sécurité Microsoft Defender ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)), essayez le centre d’action unifié dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.
- Si vous utilisiez déjà le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, vous verrez plusieurs améliorations dans le Centre d’actions ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

Le centre d’action unifié regroupe les actions de correction dans Defender pour point de terminaison et Defender pour Office 365. Il définit un langage commun pour toutes les actions de correction et fournit une expérience d’investigation unifiée. Votre équipe des opérations de sécurité dispose d’une expérience de « volet unique » pour afficher et gérer les actions de correction.  

Vous pouvez utiliser le Centre d’actions unifié si vous disposez des autorisations appropriées et d’un ou plusieurs des abonnements suivants :

- [Defender pour point de terminaison](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Pour en savoir plus, consultez [Configuration requise](./prerequisites.md).

Vous pouvez accéder à la liste des actions en attente d’approbation de deux manières différentes :

- Accédez à [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center); ou
- Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans la carte de réponse & examen automatisé, **sélectionnez Approuver dans le Centre d’actions**.

## <a name="using-the-action-center"></a>Utilisation du centre d’actions

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. Ou, dans la carte de réponse & examen automatisé, **sélectionnez Approuver dans le Centre d’action**.

3. Utilisez les onglets **Actions en attente** et **Historique** . Le tableau suivant récapitule ce que vous verrez sous chaque onglet :

   |Tab  |Description  |
   |---------|---------|
   |**Pending**     | Affiche une liste des actions qui nécessitent une attention particulière. Vous pouvez approuver ou rejeter des actions une par une, ou sélectionner plusieurs actions si elles ont le même type d’action (par exemple, fichier de mise en quarantaine). <br/><br/>Veillez à examiner et approuver (ou rejeter) les actions en attente dès que possible afin que vos enquêtes automatisées puissent se terminer en temps voulu.       |
   |**Historique**     | Sert de journal d’audit pour les actions qui ont été effectuées, par exemple : <br/>- Mesures correctives prises à la suite d’enquêtes automatisées <br/>- Actions de correction effectuées sur des messages électroniques, des fichiers ou des URL suspects ou malveillants<br/>- Actions de correction approuvées par votre équipe des opérations de sécurité <br/>- Commandes exécutées et actions de correction appliquées pendant les sessions Live Response<br/>- Actions de correction effectuées par votre protection antivirus<br/><br/>Fournit un moyen d’annuler certaines actions (voir [Annuler les actions terminées](m365d-autoir-actions.md#undo-completed-actions)).        |

4. Vous pouvez personnaliser, trier, filtrer et exporter des données dans le Centre d’actions.

   :::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="Capture d’écran montrant les fonctionnalités de tri, de filtrage et de personnalisation du Centre d’actions." lightbox="../../media/m3d-action-center-columnsfilters.png":::

   - Sélectionnez un en-tête de colonne pour trier les éléments dans l’ordre croissant ou décroissant.
   - Utilisez le filtre de période pour afficher les données du dernier jour, semaine, 30 jours ou 6 mois.
   - Choisissez les colonnes que vous souhaitez afficher.
   - Spécifiez le nombre d’éléments à inclure sur chaque page de données.
   - Utilisez des filtres pour afficher uniquement les éléments que vous souhaitez voir.
   - Sélectionnez **Exporter** pour exporter les résultats vers un fichier .csv.

## <a name="actions-tracked-in-the-action-center"></a>Actions suivies dans le centre d’actions

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
- Contenir des appareils à partir du réseau

En plus des actions de correction qui sont effectuées automatiquement à la suite [d’enquêtes automatisées](m365d-autoir.md), le Centre d’actions effectue également le suivi des actions que votre équipe de sécurité a prises pour traiter les menaces détectées et les actions qui ont été prises en raison des fonctionnalités de protection contre les menaces dans Microsoft 365 Defender. Pour plus d’informations sur les actions de correction automatiques et manuelles, consultez [Actions de correction](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Affichage des détails de la source d’action

(**NOUVEAU!**) Le centre d’actions amélioré inclut désormais une colonne **source d’action** qui vous indique d’où provient chaque action. Le tableau suivant décrit les valeurs **de source d’action** possibles :

| Valeur de la source d’action | Description |
|:-----|:---|
| **Action manuelle de l’appareil** | Action manuelle effectuée sur un appareil. Par exemple, [l’isolation de l’appareil](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) ou la [mise en quarantaine de fichiers](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **Action de messagerie manuelle** | Action manuelle effectuée sur l’e-mail. Par exemple, la suppression réversible de messages électroniques ou la [correction d’un message électronique](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Action d’appareil automatisé** | Action automatisée effectuée sur une entité, telle qu’un fichier ou un processus. L’envoi d’un fichier en quarantaine, l’arrêt d’un processus et la suppression d’une clé de Registre sont des exemples d’actions automatisées. (Voir [Actions de correction dans Microsoft Defender pour point de terminaison](../defender-endpoint/manage-auto-investigation.md#remediation-actions).) |
| **Action de messagerie automatisée** | Action automatisée effectuée sur le contenu d’un e-mail, tel qu’un e-mail, une pièce jointe ou une URL. Les exemples d’actions automatisées incluent la suppression réversible des messages électroniques, le blocage des URL et la désactivation du transfert de courrier externe. (Voir [Actions de correction dans Microsoft Defender pour Office 365](../office-365-security/air-remediation-actions.md).) |
| **Action de chasse avancée** | Actions effectuées sur des appareils ou des e-mails avec [repérage avancé](./advanced-hunting-overview.md). |
| **Action de l’Explorateur** | Actions effectuées sur le contenu de l’e-mail avec [l’Explorateur](../office-365-security/threat-explorer.md). |
| **Action de réponse dynamique manuelle** | Actions effectuées sur un appareil avec [une réponse active](../defender-endpoint/live-response.md). Par exemple, la suppression d’un fichier, l’arrêt d’un processus et la suppression d’une tâche planifiée. |
| **Action de réponse en direct** | Actions effectuées sur un appareil avec [Microsoft Defender pour point de terminaison API](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). Parmi les actions, citons l’isolation d’un appareil, l’exécution d’une analyse antivirus et l’obtention d’informations sur un fichier. |

## <a name="required-permissions-for-action-center-tasks"></a>Autorisations requises pour les tâches du centre de notifications

Pour effectuer des tâches, telles que l’approbation ou le rejet d’actions en attente dans le Centre d’actions, vous devez disposer d’autorisations attribuées comme indiqué dans le tableau suivant :

|Action de correction |Rôles et des autorisations requis |
|--|----|
|correction Microsoft Defender pour point de terminaison (appareils) |**Rôle Administrateur de sécurité** attribué dans Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) ou dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- ou ---<br/>**Rôle d’actions de correction active** attribué dans Microsoft Defender pour point de terminaison <br/> <br/> Pour en savoir plus, consultez les ressources suivantes : <br/>- [Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle (Microsoft Defender pour point de terminaison)](../defender-endpoint/user-roles.md)  |
|correction Microsoft Defender pour Office 365 (contenu office et e-mail)  |**Rôle Administrateur de la sécurité** attribué dans Azure AD ([https://portal.azure.com](https://portal.azure.com)) ou dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- et --- <br/>**Rôle de recherche et de vidage** attribué dans le Centre de sécurité & conformité ([https://protection.office.com](https://protection.office.com)) <br/><br/>**IMPORTANT** : Si vous avez le rôle **Administrateur de la sécurité** attribué uniquement dans le Centre de conformité & sécurité (Office 365 Security & Compliance Center [https://protection.office.com](https://protection.office.com)), vous ne pourrez pas accéder au Centre d’actions ou aux fonctionnalités de Microsoft 365 Defender. Le rôle **Administrateur de la sécurité** doit être attribué dans Azure AD ou le Centre d'administration Microsoft 365. <br/><br/>Pour en savoir plus, consultez les ressources suivantes : <br/>- [Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Autorisations dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Les utilisateurs auxquels le rôle **Administrateur général** est attribué dans Azure AD peuvent approuver ou rejeter toute action en attente dans le Centre d’actions. Toutefois, en guise de bonne pratique, votre organisation doit limiter le nombre de personnes auxquelles le rôle **Administrateur général** est attribué. Nous vous recommandons d’utiliser **l’administrateur de sécurité**, **les actions de correction active** et les rôles **de recherche et de vidage** répertoriés dans le tableau précédent pour les autorisations du Centre d’actions.

## <a name="next-step"></a>Étape suivante 

- [Afficher et gérer les actions de correction](m365d-autoir-actions.md)
