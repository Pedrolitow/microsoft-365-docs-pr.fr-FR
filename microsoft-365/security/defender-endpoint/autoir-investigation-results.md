---
title: Détails et résultats d’une enquête automatisée
description: Pendant et après un examen automatisé, vous pouvez afficher les résultats et les principales conclusions
keywords: automatisé, examen, résultats, analyse, détails, correction, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.date: 02/02/2021
ms.openlocfilehash: c11d9cd1ce4c2ca49315ec62b51c23ef981555f4
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51067326"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Détails et résultats d’une enquête automatisée

**S’applique à :**
- Microsoft Defender pour point de terminaison

Avec Microsoft Defender pour le [](automated-investigations.md) point de terminaison, lorsqu’une enquête automatisée s’exécute, des détails sur cet examen sont disponibles pendant et après le processus d’examen automatisé. Si vous disposez des autorisations nécessaires, vous pouvez afficher ces détails dans une vue Détails de l'examen. La vue Détails de l’examen vous fournit l’État à jour et la possibilité d’approuver les actions en attente. 

## <a name="new-unified-investigation-page"></a>(NOUVEAU!) Page Examen unifié

La page d’examen a récemment été mise à jour pour inclure des informations sur vos appareils, votre courrier électronique et le contenu de collaboration. La nouvelle page d’enquête unifiée définit un langage commun et fournit une expérience unifiée pour les enquêtes automatiques dans Microsoft Defender pour [Endpoint](microsoft-defender-advanced-threat-protection.md) et [Microsoft Defender pour Office 365.](/microsoft-365/security/defender-365-security/office-365-atp) 

> [!TIP]
> Pour en savoir plus sur ce qui change, voir [(NOUVEAU!) Page d’examen unifié](/microsoft-365/security/mtp/mtp-autoir-results).

## <a name="open-the-investigation-details-view"></a>Ouvrir la vue Détails de l’examen

Vous pouvez ouvrir une vue Détails de l’examen avant impression comme suit :
- [Sélectionnez un élément dans le centre de notifications](#select-an-item-in-the-action-center)
- [Sélectionnez un examen dans une page de détails d’incident](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Sélectionnez un élément dans le centre de notifications

Le centre de [mesures amélioré](auto-investigation-action-center.md) regroupe des [actions](manage-auto-investigation.md#remediation-actions) de correction sur vos appareils, des & de collaboration et des identités. Les actions répertoriées incluent des actions de correction qui ont été prises automatiquement ou manuellement. Dans le centre de actions, vous pouvez afficher les actions en attente d’approbation et les actions qui ont déjà été approuvées ou terminées. Vous pouvez également accéder à d’autres détails, tels qu’une page d’enquête.

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 
2. Dans le volet de navigation, choisissez **Centre de notifications**. 
3. Sous l’onglet **En attente** ou **Historique**, sélectionnez un élément. Son volet volant s’ouvre.
4. Examinez les informations dans le volet volant, puis prenez l’une des étapes suivantes :
   - Sélectionnez **Ouvrir la page Examen** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Rejeter** pour empêcher une action en attente d’être prise.
   - Sélectionnez **Go hunt** (Aller à la recherche) pour passer [à la recherche avancée](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Ouvrez un examen dans une page de détails d’incident

La page Détails de l’incident permet d’afficher des informations détaillées sur un incident, notamment des alertes qui ont déclenché des informations sur les appareils, les comptes utilisateurs ou les boîtes aux lettres concernés.

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 
2. Dans le volet de navigation, sélectionnez **Incidents &**  >  **alertes Incidents**. 
3. Sélectionnez un élément dans la liste, puis choisissez **Ouvrir la page Incident.**
4. Sélectionnez **l’onglet** Examens, puis un examen dans la liste. Son volet volant s’ouvre.
5. Sélectionnez **Ouvrir la page Examen.** 

## <a name="investigation-details"></a>Détails de l’examen

Utilisez la vue Détails de l’examen pour afficher les activités passées, actuelles et en attente relatives à un examen. La vue Détails de l’examen est semblable à l’image suivante :

Dans la vue Détails de l’examen, vous pouvez consulter des informations sur les onglets **Graphique de l'examen**, **Alertes**, **Appareils**, **Identités**, **Principales conclusions**, **Entités**, **Journal** et **Actions en attente**, comme décrit dans le tableau suivant.

> [!NOTE]
> Les onglets spécifiques que vous voyez dans une page de détails d’enquête dépendent de ce que comprend votre abonnement. Par exemple, si votre abonnement n’inclut pas Microsoft Defender pour Office 365 Plan 2, vous ne verrez pas d’onglet **Boîtes aux** lettres.

| Tab | Description |
|:--------|:--------|
| **Graphique de l'examen**   | Fournit une représentation visuelle de l’examen. Décrit les entités et répertorie de menaces détectées, ainsi que les alertes et l’attente d’une approbation.<br/>Vous pouvez sélectionner un élément sur le graphique pour afficher plus de détails. Par exemple, la sélection de l’icône **Preuve** vous permet d’utiliser l’onglet Preuves, où vous pouvez voir les entités détectées et leurs verdicts.  |
| **Alertes**    | Répertorie les alertes associées à l’examen. Les alertes peuvent être le fait de fonctionnalités de protection contre les menaces sur l’appareil d’un utilisateur, dans les applications Office, cloud app security et d’autres fonctionnalités de Microsoft 365 Defender.|
| **Appareils** | Répertorie les appareils inclus dans l’examen, ainsi que leur niveau de correction. (Les niveaux de correction correspondent au niveau [d’automatisation des groupes d’appareils.)](automation-levels.md) |
| **Boîtes aux lettres** |Répertorie les boîtes aux lettres qui sont touchées par les menaces détectées.  |
| **Utilisateurs**  | Répertorie les comptes d’utilisateurs qui sont touchés par les menaces détectées. |
| **Preuve** | Répertorie les éléments de preuve élevés par les alertes/enquêtes. Inclut les verdicts (*malveillants,* suspects ou aucune menace *trouvée)* et l’état de correction. |
| **Entities**  | Fournit des détails sur chaque entité analysée, y compris un verdict pour chaque type d’entité *(* *malveillant,* suspect ou aucune *menace trouvée).*|
|**Log**    | Fournit une vue chronologique et détaillée de toutes les actions d’investigation entreprises après le déclenchement d’une alerte.|
| **Actions en attente** | Répertorie les éléments qui nécessitent une approbation pour continuer. Go to the Action center ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ) to approve pending actions. |

## <a name="see-also"></a>Voir aussi

- [Examiner les actions de correction à la suite d’un examen automatisé](manage-auto-investigation.md)
- [Afficher et organiser la file d’attente Microsoft Defender pour les incidents de point de terminaison](view-incidents-queue.md)