---
title: Accéder au centre de notifications pour afficher et approuver vos tâches d’enquête et de correction automatisées
description: Utiliser le centre de notifications pour afficher des détails sur l’enquête automatiser et approuver les actions en attente
keywords: Centre de notifications, protection contre les menaces, enquête, alerte, en attente, automatisé, détection
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.date: 09/16/2020
ms.openlocfilehash: 4d4aa8afc7a17d2f9f0ae2d48404d7a3da553d47
ms.sourcegitcommit: 7c0873d2a804f17697844fb13f1a100fabce86c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47962262"
---
# <a name="the-action-center"></a>Le Centre de notifications

**S’applique à :**
- Protection Microsoft contre les menaces

Utilisez le centre de notifications pour afficher les résultats des enquêtes actuelles et antérieures sur les appareils et les boîtes aux lettres de votre organisation. Selon le type de menace et le verdict résultant, les [actions de correction](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-remediation-actions) se produisent automatiquement ou après approbation de l’équipe des opérations de sécurité de votre organisation. Toutes les actions de correction, qu’elles soient en attente d’approbation ou qu’elles aient déjà été approuvées, sont regroupées dans le centre de notifications. 

![Centre de notifications](../../media/air-actioncenter.png)

## <a name="a-single-pane-of-glass-experience"></a>Expérience de type « écran unique »

Le centre de notifications offre une expérience de type « écran unique » pour certaines tâches :
- Approbation des actions de correction en attente ;
- Affichage d’un journal d’audit des actions de correction déjà approuvées ; et
- Évaluation des actions de correction terminées.

L’équipe en charge des opérations de sécurité peut fonctionner de façon plus efficace, car le centre de notifications offre une vue complète de la Protection Microsoft contre les menaces en fonctionnement.

## <a name="go-to-the-action-center"></a>Accéder au centre de notifications

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Dans le centre de maintenance, deux onglets s’affichent : **en attente** et **historique**.

    - L’onglet **En attente** répertorie les enquêtes devant être réexaminées et approuvées par un membre de l’équipe en charge des opérations de sécurité pour continuer. Veillez à examiner les éléments en attente affichés ici et à effectuer les actions appropriées.

    - L’onglet **Historique** répertorie les enquêtes passées et les actions de correction qui ont été effectuées automatiquement. Vous pouvez afficher des données pour le dernier jour, la dernière semaine, le dernier mois ou les six derniers mois.

4. Pour afficher uniquement les colonnes désirées, sélectionnez **Personnaliser les colonnes**.<br/>![Centre de notifications dans la Protection Microsoft contre les menaces](../../media/mtp-action-center.png)

5. Sélectionnez un élément dans la liste pour afficher des détails supplémentaires sur une enquête. La vue Détails de l’enquête s’ouvre.<br/>![Détails de l’enquête](../../media/mtp-air-investdetails.png)

    - Si l’enquête concerne du contenu de messagerie (par exemple, l’entité est une boîte aux lettres), des détails d’enquête s’ouvrent dans le centre de sécurité & conformité ( [https://protection.office.com/threatinvestigation](https://protection.office.com/threatinvestigation) ). 

    - Si l’enquête implique un appareil, les détails de l’enquête s’affichent dans le centre de sécurité ([https://security.microsoft.com](https://security.microsoft.com)). 

> [!TIP]
> Si vous pensez qu’un message a été manqué ou incorrectement détecté par les fonctionnalités d’analyse et de réponse automatiques dans Microsoft Threat Protection, faites-le nous savoir. Découvrez [Comment signaler des faux positifs/négatifs dans les capacités d’inspection et de réponse automatiques de Microsoft Threat Protection](mtp-autoir-report-false-positives-negatives.md).

## <a name="available-actions"></a>Actions disponibles

Les actions de correction étant prises, elles sont répertoriées sous l’onglet historique dans le centre de maintenance. Ces actions sont les suivantes :

- Collecter un package d’enquête 
- Isoler l’appareil (cette action peut être inachevée) 
- Ordinateur débarquement 
- Exécution du code de la version 
- Débloquer de la quarantaine 
- Exemple de requête 
- Restreindre l’exécution du code (cette action peut être terminée) 
- Exécuter l’analyse antivirus 
- Arrêter et mettre en quarantaine 

## <a name="required-permissions-for-action-center-tasks"></a>Autorisations requises pour les tâches du centre de notifications

Pour approuver ou rejeter des actions en attente dans le centre de notifications, vous devez disposer des autorisations définies dans le tableau suivant :

|Action de correction |Rôles et des autorisations requis |
|--|----|
|Correction de Microsoft Defender – Protection avancée contre les menaces (appareils) |Rôle Administrateur de la sécurité attribué dans Azure Active Directory ([https://portal.azure.com](https://portal.azure.com)) ou dans le Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- ou ---<br/>Rôle Actions de correction actives attribué dans Microsoft Defender – Protection avancée contre les menaces <br/> <br/> Pour en savoir plus, consultez les ressources suivantes : <br/>- [Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)<br/>- [Créer et gérer des rôles pour le contrôle d’accès basé sur les rôles (Microsoft Defender – Protection avancée contre les menaces)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles)  |
|Correction Office 365 – Protection avancée contre les menaces (contenu et courrier Office)  |Rôle Administrateur de la sécurité attribué dans Azure Active Directory ([https://portal.azure.com](https://portal.azure.com)) ou dans le Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- et --- <br/>Recherche et purger le rôle auquel est attribué le centre de sécurité & conformité ( [https://protection.office.com](https://protection.office.com) ) <br/><br/>**Important**: si le rôle administrateur de sécurité est affecté uniquement dans le centre de sécurité & conformité, vous ne serez pas en mesure d’accéder au centre de maintenance ou aux fonctionnalités de protection contre les menaces Microsoft. Vous devez avoir le rôle Administrateur de la sécurité attribué dans Azure Active Directory ou dans le Centre d’administration Microsoft 365. <br/><br/>Pour en savoir plus, consultez les ressources suivantes : <br/>- [Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)<br/>- [Autorisations dans le centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!NOTE]
> Les utilisateurs qui ont le rôle Administrateur général attribué dans Azure Active Directory peuvent approuver ou rejeter toute action en attente dans le centre de notifications. Toutefois, il est recommandé à votre organisation de limiter le nombre de personnes auxquelles le rôle Administrateur général est attribué. Nous vous recommandons d’utiliser les rôles Administrateur de la sécurité, Actions de correction actives et Rechercher et purger répertoriés ci-dessus pour les autorisations du centre de notifications.

## <a name="next-steps"></a>Étapes suivantes 

- [Approuver ou rejeter les actions en attente à la suite d’une enquête automatisée](mtp-autoir-actions.md)
- [Afficher les résultats d’une enquête automatisée](mtp-autoir-results.md)

