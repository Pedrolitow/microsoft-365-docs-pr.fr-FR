---
title: Détails et résultats d’une enquête automatisée
description: Pendant et après un examen automatisé, vous pouvez afficher les résultats et les principales conclusions
keywords: automatisé, examen, résultats, analyse, détails, correction, autoair
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
ms.date: 09/16/2020
ms.technology: m365d
ms.openlocfilehash: c050683bb3ed052ae4752ffdee66fe51fb99b88b
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930365"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Détails et résultats d’une enquête automatisée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Lorsqu’un examen automatisé se produit dans Microsoft 365 Defender, des détails sur cet examen sont disponibles pendant et après le processus d’examen automatisé. Si vous disposez des [autorisations nécessaires](mtp-action-center.md#required-permissions-for-action-center-tasks), vous pouvez afficher ces détails dans une vue Détails de l'examen. La vue Détails de l’examen vous fournit l’État à jour et la possibilité d’approuver les actions en attente. 

![Détails de l’examen](../../media/mtp-air-investdetails.png)

## <a name="open-the-investigation-details-view"></a>Ouvrir la vue Détails de l’examen

Vous pouvez ouvrir une vue Détails de l’examen avant impression comme suit :
- [Sélectionnez un élément dans le centre de notifications](#select-an-item-in-the-action-center)
- [Sélectionnez un examen dans une page de détails d’incident](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Sélectionnez un élément dans le centre de notifications

Utilisez le centre de notifications pour afficher les actions en attente d’approbation (sous l’onglet **En attente**) ou qui ont déjà été approuvées (sous l’onglet **Historique**). 

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Sous l’onglet **En attente** ou **Historique**, sélectionnez un élément. Si vous disposez des [autorisations nécessaires](mtp-action-center.md#required-permissions-for-action-center-tasks), vous pouvez approuver (ou refuser) les actions en attente.

### <a name="open-an-investigation-from-an-incident-details-page"></a>Ouvrez un examen dans une page de détails d’incident

La page Détails de l’incident permet d’afficher des informations détaillées sur un incident, notamment des alertes qui ont déclenché des informations sur les appareils, les comptes utilisateurs ou les boîtes aux lettres concernés.

1. Accédez à [https://security.microsoft.com](https://security.microsoft.com) et connectez-vous. 

2. Dans le volet de navigation, choisissez **Incidents**. 

3. Sélectionnez un élément dans la liste pour ouvrir la vue Détails de l’événement.<br/>![Détails de l’incident](../../media/mtp-incidentdetails-tabs.png)

4. Sous l’onglet **Examen**, sélectionnez un examen dans la liste.

## <a name="investigation-details"></a>Détails de l’examen

Utilisez la vue Détails de l’examen pour afficher les activités passées, actuelles et en attente relatives à un examen. La vue Détails de l’examen est semblable à l’image suivante :

![Détails de l’examen](../../media/mtp-air-investdetails.png)

Dans la vue Détails de l’examen, vous pouvez consulter des informations sur les onglets **Graphique de l'examen**, **Alertes**, **Appareils**, **Identités**, **Principales conclusions**, **Entités**, **Journal** et **Actions en attente**, comme décrit dans le tableau suivant.

| Tab | Description |
|--------|--------|
| **Graphique de l'examen**   | Fournit une représentation visuelle de l’examen. Décrit les entités et répertorie de menaces détectées, ainsi que les alertes et l’attente d’une approbation.<br/>Vous pouvez cliquer sur un élément sur le graphique pour afficher plus de détails. Par exemple, en cliquant sur l’icône **Menaces détectées**, vous accédez à l'onglet **Principales conclusions**. |
| **Alertes**    | Répertorie les alertes associées à l’examen. Les alertes peuvent être dues aux fonctionnalités de protection contre les menaces sur l’ordinateur d’un utilisateur, dans les applications Office, cloud app security et autres fonctionnalités de Microsoft 365 Defender.|
| **Appareils** | Répertorie les ordinateurs inclus dans l’examen et le niveau de correction.|
| **Principales conclusions**  | Répertorie les résultats de l’examen, ainsi que l’État et les actions effectuées ou en attente. Vous pouvez approuver les actions en attente pour les appareils et les identités dans sous cet onglet.|
| **Entities**  | Répertorie les activités des utilisateurs, les fichiers, les processus, les services, les pilotes, les adresses IP et les méthodes de persistance associées à l’examen, ainsi que l’État et les actions prises.|
|**Log**    | Fournit une vue détaillée de toutes les étapes effectuées pendant l’examen, ainsi que de l’État.|
| **Actions en attente** | Répertorie les éléments qui nécessitent une approbation pour continuer.|

## <a name="next-steps"></a>Étapes suivantes

- [Approuver ou refuser les actions liées à un examen et réponse automatisées](mtp-autoir-actions.md)
- [Examiner les actions de correction](mtp-remediation-actions.md)
