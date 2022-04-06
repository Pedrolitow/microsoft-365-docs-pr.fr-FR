---
title: Détails et résultats d’une enquête automatisée
description: Afficher les résultats et les principales conclusions d’une enquête automatisée dans Microsoft 365 Defender
keywords: automatisé, examen, résultats, analyse, détails, correction, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
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
ms.topic: conceptual
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 5a95980147c66fa8655f5c1b2ebe8adfff9e87c0
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501264"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Détails et résultats d’une enquête automatisée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Avec Microsoft 365 Defender, lorsqu’une enquête automatisée s’exécute, des détails sur cet examen sont disponibles pendant et après le processus d’examen automatisé.[](m365d-autoir.md) Si vous disposez des [autorisations](m365d-action-center.md#required-permissions-for-action-center-tasks) nécessaires, vous pouvez afficher ces détails dans une vue des détails de l’enquête qui vous fournit l’état à jour et la possibilité d’approuver les actions en attente. 

## <a name="new-unified-investigation-page"></a>(NOUVEAU) Page Examen unifié

La page d’examen a récemment été mise à jour pour inclure des informations sur vos appareils, votre courrier électronique et le contenu de collaboration. La nouvelle page d’enquête unifiée définit un langage commun et fournit une expérience unifiée pour les examens automatiques dans [Microsoft Defender pour Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) et [Microsoft Defender pour Office 365](../office-365-security/defender-for-office-365.md). Pour accéder à la page d’enquête unifiée, sélectionnez le lien dans la bannière jaune qui s’affiche :

- N’importe quelle page d’enquête dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">le Centre Office 365 sécurité & conformité</a>
- N’importe quelle page d’examen dans Microsoft 365 Defender portail ([https://security.microsoft.com](https://security.microsoft.com))
- Toute expérience d’incident ou de centre de Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">de sécurité</a>

## <a name="open-the-investigation-details-view"></a>Ouvrir la vue Détails de l’examen

Vous pouvez ouvrir une vue Détails de l’examen avant impression comme suit :

- [Sélectionnez un élément dans le centre de notifications](#select-an-item-in-the-action-center)
- [Sélectionnez un examen dans une page de détails d’incident](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Sélectionnez un élément dans le centre de notifications

Le centre de [mesures](m365d-action-center.md) amélioré regroupe[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) les [actions](m365d-remediation-actions.md) de correction sur vos appareils, la messagerie & le contenu de collaboration et les identités. Les actions répertoriées incluent les actions de correction qui ont été prises automatiquement ou manuellement. Dans le centre de actions, vous pouvez afficher les actions en attente d’approbation et les actions qui ont déjà été approuvées ou terminées. Vous pouvez également accéder à d’autres détails, tels qu’une page d’enquête.

> [!TIP]
> Vous devez avoir [certaines autorisations pour](m365d-action-center.md#required-permissions-for-action-center-tasks) approuver, rejeter ou annuler des actions.

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> and sign in. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Sous l’onglet **En attente** ou **Historique**, sélectionnez un élément. Son volet volant s’ouvre.

4. Examinez les informations dans le volet volant, puis prenez l’une des étapes suivantes :
   - **Sélectionnez Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - **Sélectionnez Approuver** pour lancer une action en attente.
   - **Sélectionnez Rejeter** pour empêcher une action en attente d’être prise.
   - **Sélectionnez Go hunt** (Aller à la recherche) pour passer [au recherche avancée](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Ouvrez un examen dans une page de détails d’incident

La page Détails de l’incident permet d’afficher des informations détaillées sur un incident, notamment des alertes qui ont déclenché des informations sur les appareils, les comptes utilisateurs ou les boîtes aux lettres concernés.

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> and sign in. 

2. Dans le volet de navigation, sélectionnez **Incidents & alertsIncidents** > . 

3. Sélectionnez un élément dans la liste, puis choisissez **Ouvrir la page Incident**.

4. Sélectionnez **l’onglet** Examens, puis un examen dans la liste. Son volet volant s’ouvre.

5. Sélectionnez **Ouvrir la page Examen**. 

Voici un exemple.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="Page d’examen dans le portail Microsoft 365 Defender recherche" lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>Détails de l’examen

Utilisez la vue Détails de l’examen pour afficher les activités passées, actuelles et en attente relatives à un examen. Voici un exemple.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="Page détails de l’examen dans le portail Microsoft 365 Defender recherche" lightbox="../../media/mtp-air-investdetails.png":::

Dans la vue Détails de l’examen, vous pouvez consulter des informations sur les onglets **Graphique de l'examen**, **Alertes**, **Appareils**, **Identités**, **Principales conclusions**, **Entités**, **Journal** et **Actions en attente**, comme décrit dans le tableau suivant.

> [!NOTE]
> Les onglets spécifiques que vous voyez dans une page de détails d’enquête dépendent de ce que comprend votre abonnement. Par exemple, si votre abonnement n’inclut pas Microsoft Defender pour Office 365 Plan 2, vous ne verrez pas d’onglet **Boîtes aux** lettres.

| Tab | Description |
|:--------|:--------|
| **Graphique de l'examen** | Fournit une représentation visuelle de l’examen. Décrit les entités et répertorie de menaces détectées, ainsi que les alertes et l’attente d’une approbation.<br/>Vous pouvez sélectionner un élément sur le graphique pour afficher plus de détails. Par exemple, la sélection de l’icône **Preuve** vous permet  d’utiliser l’onglet Preuves, où vous pouvez voir les entités détectées et leurs verdicts. |
| **Alertes** | Répertorie les alertes associées à l’examen. Les alertes peuvent être dues aux fonctionnalités de protection contre les menaces sur l’appareil d’un utilisateur, dans les applications Office, Microsoft Defender pour les applications cloud et d’autres fonctionnalités Microsoft 365 Defender cloud.|
| **Appareils** | Répertorie les appareils inclus dans l’examen, ainsi que leur niveau de correction. (Les niveaux de correction correspondent [au niveau d’automatisation des groupes d’appareils](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups).) |
| **Boîtes aux lettres** |Répertorie les boîtes aux lettres qui sont touchées par les menaces détectées.  |
| **Utilisateurs**  | Répertorie les comptes d’utilisateurs qui sont touchés par les menaces détectées. |
| **Preuve** | Répertorie les éléments de preuve élevés par des alertes ou des enquêtes. Inclut les verdicts (*malveillants**,* *suspects**, inconnus* ou aucune menace trouvée) et l’état de correction. |
| **Entities** | Fournit des détails sur chaque entité analysée, y compris un verdict pour chaque type d’entité *(malveillant**, suspect* ou aucune *menace trouvée*).|
|**Log** | Fournit une vue chronologique et détaillée de toutes les actions d’investigation entreprises après le déclenchement d’une alerte.|
| **Historique des actions en attente** | Répertorie les éléments qui nécessitent une approbation pour continuer. Go to the Action center ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) to approve pending actions. |

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les actions de correction](m365d-autoir-actions.md)
- [En savoir plus sur les actions de correction](m365d-remediation-actions.md)
