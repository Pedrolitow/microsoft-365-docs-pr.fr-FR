---
title: Accéder au centre de notifications pour afficher et approuver vos tâches d’enquête et de correction automatisées
description: Utiliser le centre de notifications pour afficher des détails sur l’enquête automatiser et approuver les actions en attente
keywords: Centre de notifications, protection contre les menaces, enquête, alerte, en attente, automatisé, détection
search.appverid: met150
ms.prod: m365-security
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
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.date: 12/09/2020
ms.technology: m365d
ms.openlocfilehash: 45e02e4ce7d5d813cc8215a1f27ed9c415707cb1
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930425"
---
# <a name="the-action-center"></a>Le Centre de notifications

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Utilisez le centre de actions ( ) pour voir les résultats des enquêtes actuelles et passées sur les appareils et boîtes aux lettres de [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) votre organisation. Selon le type de menace et le verdict qui en résulte, des [actions](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-remediation-actions) de correction peuvent se produire automatiquement ou après approbation par l’équipe des opérations de sécurité de votre organisation. Toutes les actions de correction, qu’elles soient en attente d’approbation ou qu’elles aient déjà été approuvées, sont regroupées dans le centre de notifications. 

![Centre de notifications](../../media/air-actioncenter.png)

## <a name="a-single-pane-of-glass-experience"></a>Expérience de type « écran unique »

Le centre de notifications offre une expérience de type « écran unique » pour certaines tâches :
- Approbation des actions de correction en attente ;
- Affichage d’un journal d’audit des actions de correction déjà approuvées ; et
- Évaluation des actions de correction terminées.

Votre équipe des opérations de sécurité peut fonctionner plus efficacement, car le centre de sécurité fournit une vue complète de Microsoft 365 Defender au travail.

## <a name="go-to-the-action-center"></a>Accéder au centre de notifications

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Dans le centre de actions, vous verrez deux onglets : **En attente et** **Historique.**

    - L’onglet **En attente** répertorie les enquêtes devant être réexaminées et approuvées par un membre de l’équipe en charge des opérations de sécurité pour continuer. Veillez à examiner les éléments en attente affichés ici et à effectuer les actions appropriées.

    - L’onglet **Historique** répertorie les enquêtes passées et les actions de correction qui ont été effectuées automatiquement. Vous pouvez afficher des données pour le dernier jour, la dernière semaine, le dernier mois ou les six derniers mois.

4. Pour afficher uniquement les colonnes désirées, sélectionnez **Personnaliser les colonnes**.<br/>![Centre de actions dans Microsoft 365 Defender](../../media/mtp-action-center.png)

5. Sélectionnez un élément dans la liste pour afficher des détails supplémentaires sur une enquête. La vue Détails de l’enquête s’ouvre.<br/>![Détails de l’enquête](../../media/mtp-air-investdetails.png)

    - Si l’examen porte sur le contenu du courrier électronique (par exemple, l’entité est une boîte aux lettres), les détails de l’enquête s’ouvrent dans le Centre de sécurité & conformité ( [https://protection.office.com/threatinvestigation](https://protection.office.com/threatinvestigation) ). 

    - Si l’enquête implique un appareil, les détails de l’enquête s’affichent dans le centre de sécurité ([https://security.microsoft.com](https://security.microsoft.com)). 

> [!TIP]
> Si vous pensez que quelque chose a été manqué ou détecté à tort par les fonctionnalités d’investigation et de réponse automatisées dans Microsoft 365 Defender, faites-le nous savoir ! Découvrez comment signaler les faux positifs/négatifs dans les fonctionnalités d’investigation et de réponse [automatisées (AIR) dans Microsoft 365 Defender.](mtp-autoir-report-false-positives-negatives.md)

## <a name="available-actions"></a>Actions disponibles

Lorsque des mesures correctives sont prises,  elles sont répertoriées sous l’onglet Historique dans le centre de correction. Ces actions sont les suivantes :

- Collecter le package d’examen 
- Isoler l’appareil (cette action peut être annulée) 
- Appareil hors-carte 
- Exécution du code de publication 
- Libérer de la quarantaine 
- Exemple de demande 
- Restreindre l’exécution du code (cette action peut être annulée) 
- Exécuter une analyse antivirus 
- Arrêter et mettre en quarantaine 

> [!NOTE]
> En plus des actions de correction qui sont prises automatiquement, votre équipe en charge des opérations de sécurité peut prendre des mesures manuelles pour résoudre les menaces détectées. Pour plus d’informations sur les actions de correction automatiques et manuelles, voir [Actions de correction.](mtp-remediation-actions.md)

## <a name="action-source"></a>Source d’action

(**NOUVEAU !**) Comme vous le savez, Microsoft 365 Defender regroupe des fonctionnalités d’investigation et de réponse automatisées dans plusieurs services, tels que Microsoft Defender pour [endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) et Microsoft Defender pour [Office 365.](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) Le nouveau centre de correction et amélioré inclut désormais une colonne **source Action** qui vous indique d’où vient chaque action de correction. 

Le tableau suivant décrit les valeurs possibles de **la source d’action** :

| Valeur de la source d’action | Description |
|:-----|:---|
| **Action manuelle de l’appareil** | Action manuelle sur un appareil. Par exemple, [l’isolation de l’appareil](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-devices-from-the-network) ou [la mise en quarantaine des fichiers.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts#stop-and-quarantine-files) |
| **Action de messagerie manuelle** | Action manuelle sur le courrier électronique. Un exemple inclut la suppression (ou la correction) d’un message [électronique.](https://docs.microsoft.com/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365) |
| **Action automatisée sur l’appareil** | Action automatisée entreprise sur une entité, telle qu’un fichier ou un processus. L’envoi d’un fichier en quarantaine, l’arrêt d’un processus et la suppression d’une clé de Registre sont des exemples d’actions automatisées. (Voir [les actions de correction dans Microsoft Defender pour le point de terminaison.)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-auto-investigation#remediation-actions) |
| **Action de messagerie automatisée** | Action automatisée sur le contenu du courrier électronique, telle qu’un message électronique, une pièce jointe ou une URL. Parmi les exemples d’actions automatisées, citons la suppression (à l’aide de logiciels) des messages électroniques, le blocage des URL et la désinstruction du forwarding de courrier externe. (Voir [les actions de correction dans Microsoft Defender pour Office 365.)](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-remediation-actions) |
| **Action de recherche avancée** | Actions prises sur des appareils ou des e-mails avec [un chasse avancée](https://docs.microsoft.com/microsoft-365/security/mtp/advanced-hunting-overview). |
| **Action de l’explorateur** | Actions prises sur le contenu du courrier électronique avec [l’Explorateur](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer). |
| **Action de réponse en direct manuelle** | Actions prises sur un appareil avec [réponse en direct.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/live-response) Par exemple, la suppression d’un fichier, l’arrêt d’un processus et la suppression d’une tâche programmée. |
| **Action de réponse en direct** | Actions entreprises sur un appareil à [l’aide des API Microsoft Defender pour les points de terminaison.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/management-apis#microsoft-defender-for-endpoint-apis) L’isolation d’un appareil, l’exécution d’une analyse antivirus et l’obtention d’informations sur un fichier sont des exemples d’actions. |

## <a name="required-permissions-for-action-center-tasks"></a>Autorisations requises pour les tâches du centre de notifications

Pour approuver ou rejeter des actions en attente dans le centre de notifications, vous devez disposer des autorisations définies dans le tableau suivant :

|Action de correction |Rôles et des autorisations requis |
|--|----|
|Correction de Microsoft Defender pour les points de terminaison (appareils) |Rôle Administrateur de la sécurité attribué dans Azure Active Directory ([https://portal.azure.com](https://portal.azure.com)) ou dans le Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- ou ---<br/>Rôle des actions de correction actives attribué dans Microsoft Defender pour le point de terminaison <br/> <br/> Pour en savoir plus, consultez les ressources suivantes : <br/>- [Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)<br/>- [Créer et gérer des rôles pour le contrôle d’accès basé sur un rôle (Microsoft Defender pour point de terminaison)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles)  |
|Correction de Microsoft Defender pour Office 365 (contenu et courrier Office)  |Rôle Administrateur de la sécurité attribué dans Azure Active Directory ([https://portal.azure.com](https://portal.azure.com)) ou dans le Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- et --- <br/>Rôle De recherche et de purge attribué au Centre de sécurité & conformité ( [https://protection.office.com](https://protection.office.com) ) <br/><br/>**IMPORTANT :** si le rôle Administrateur de la sécurité est attribué uniquement dans le Centre de sécurité & conformité, vous ne pourrez pas accéder au Centre de gestion des actions ou aux fonctionnalités de Microsoft 365 Defender. Vous devez avoir le rôle Administrateur de la sécurité attribué dans Azure Active Directory ou dans le Centre d’administration Microsoft 365. <br/><br/>Pour en savoir plus, consultez les ressources suivantes : <br/>- [Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)<br/>- [Autorisations dans le Centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!NOTE]
> Les utilisateurs qui ont le rôle Administrateur général attribué dans Azure Active Directory peuvent approuver ou rejeter toute action en attente dans le centre de notifications. Toutefois, il est recommandé à votre organisation de limiter le nombre de personnes auxquelles le rôle Administrateur général est attribué. Nous vous recommandons d’utiliser les rôles Administrateur de la sécurité, Actions de correction actives et Rechercher et purger répertoriés ci-dessus pour les autorisations du centre de notifications.

## <a name="next-steps"></a>Étapes suivantes 

- [Approuver ou rejeter les actions en attente à la suite d’un examen automatisé](mtp-autoir-actions.md)
- [Afficher les résultats d’une enquête automatisée](mtp-autoir-results.md)

