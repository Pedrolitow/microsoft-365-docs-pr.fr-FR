---
title: Rechercher des e-mails et corriger les menaces à l’aide de l’Explorateur de menaces dans Microsoft 365 Defender
description: Étapes de correction manuelle dans l’Explorateur de menaces dans Microsoft 365 Defender, notamment comment obtenir les meilleures performances et les scénarios qui appellent la correction.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: c6d887e7b50c3bfeddb967340045f6b2dbf96b0c
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67107324"
---
# <a name="steps-to-use-manual-email-remediation-in-threat-explorer"></a>Étapes d’utilisation de la correction manuelle des e-mails dans l’Explorateur de menaces

Email correction est une fonctionnalité déjà existante qui permet aux administrateurs d’agir sur les e-mails qui sont des menaces.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin
- Microsoft Defender pour Office 365 plan 2 (inclus dans les plans E5)
- Autorisations suffisantes (veillez à accorder le rôle [recherche et vidage](https://sip.security.microsoft.com/securitypermissions) de compte)

## <a name="create-and-track-the-remediation"></a>Créer et suivre la correction

1. **Sélectionnez une menace à corriger** dans [l’Explorateur de menaces](https://security.microsoft.com/threatexplorer) , puis sélectionnez le bouton **Actions** de message, qui vous proposera des options telles que *la suppression réversible* ou la *suppression définitive*.
1. Le volet latéral s’ouvre et demande des détails tels qu’un nom pour la correction, la gravité et la description. Une fois les informations examinées, **appuyez sur Envoyer**.
1. Dès que l’administrateur approuve cette action, il voit l’ID d’approbation et un lien vers le centre d’action Microsoft 365 Defender [ici](https://security.microsoft.com/action-center/history). Cette page est l’endroit où **les actions peuvent être suivies**.

    1. **Administration alerte d’action** : une alerte système s’affiche dans la file d’attente d’alerte avec le nom « Action administrative envoyée par un administrateur ». Cela indique qu’un administrateur a pris l’action de corriger une entité. Il fournit des détails tels que le nom de l’administrateur qui a effectué l’action, ainsi que le lien et l’heure de l’enquête. Cela rend les administrateurs conscients de chaque action importante, comme la correction, effectuée sur les entités.
    1. **Administration investigation de l’action** : étant donné que l’analyse sur les entités a déjà été effectuée par l’administrateur et que c’est ce qui a conduit à l’action effectuée, aucune analyse supplémentaire n’est effectuée par le système. Il affiche des détails tels que l’alerte associée, l’entité sélectionnée pour la correction, l’action effectuée, l’état de correction, le nombre d’entités et l’approbateur de l’action. Cela permet aux administrateurs de suivre l’enquête et les actions effectuées *manuellement* : une enquête d’action d’administrateur.
1. **Les journaux d’activité d’action dans le centre d’actions unifié** - Historique et journaux d’action pour les actions de messagerie telles que la suppression réversible et le déplacement vers le dossier d’éléments supprimés, sont *tous disponibles dans une vue centralisée* sous l’onglet **Historique** unifié **du Centre** >  d’actions. 
1. **Filtres dans le centre d’actions unifié** : il existe plusieurs filtres tels que le nom de correction, l’ID d’approbation, l’ID d’investigation, l’état, la source d’action et le type d’action. Elles sont utiles pour rechercher et suivre les actions de messagerie dans le centre d’action unifié.

> [!IMPORTANT]
> Performances Pour de meilleures performances, la correction doit être effectuée par lots de *50 000 ou moins*. Réduisez le résultat de la recherche à l’aide de *l’emplacement de remise le plus récent* et déclenchez la correction de l’e-mail si l’e-mail se trouve dans un dossier remédiable comme Boîte de réception, Courrier indésirable, Supprimé, par exemple.

## <a name="scenarios-that-call-for-email-remediation"></a>Scénarios qui appellent une correction par e-mail

Voici les scénarios de correction des e-mails :

1. Dans le cadre d’une enquête, SecOps identifie une menace dans la boîte aux lettres d’un utilisateur final et souhaite effacer le ou les e-mails problématiques.
1. Lorsque les actions de messagerie suggérées dans Air (Automated Investigation and Response) sont approuvées par SecOps, l’action de correction se déclenche automatiquement pour le cluster de courrier ou de messagerie donné.

Deux scénarios de correction manuelle des e-mails :

1. Le scénario principal :
    1. Les actions manuelles effectuées sur les e-mails (par exemple, à l’aide de l’Explorateur de menaces ou de la chasse avancée) sont visibles uniquement dans le centre d’action Defender pour Office 365 hérité (Email et collaboration > Examiner > Centre d’actions dans le Centre d’actions - Sécurité Microsoft 365).  
1. Scénario d’approbation en deux étapes :
    1. Actions manuelles en attente d’approbation à l’aide du processus d’approbation en deux étapes (1. L’e-mail a été ajouté à la correction par un analyste, 2. L’e-mail a été examiné et approuvé par un autre analyste).

Étant donné les scénarios courants, la correction de l’e-mail peut être déclenchée de trois manières différentes.

1. **Correction basée sur une requête** : en sélectionnant tous les résultats de recherche avec une requête (200 000 e-mails peuvent être envoyés au maximum).
1. **Correction triée à** la main : sélection d’e-mails un par un en cliquant sur la case à cocher (100 e-mails peuvent être envoyés à la fois).
1. **Correction basée sur les requêtes avec exclusions** : sélection de tous les e-mails, puis suppression manuelle de quelques messages (la requête peut contenir un maximum de 1 000 e-mails et le nombre maximal d’exclusions est de 100).

## <a name="next-steps"></a>Étapes suivantes
1. Accédez au [Portail Microsoft 365 Defender](https://security.microsoft.com) et connectez-vous.
1. Dans le volet de navigation, sélectionnez **Centre d’actions**.
1. Accédez à l’onglet **Historique** , puis cliquez sur n’importe quelle liste d’approbation en attente. Il ouvre un volet latéral.  
1. Suivez l’état de l’action dans le centre d’action unifié.

## <a name="more-information"></a>Plus d’informations

[En savoir plus sur la correction des e-mails](../../office-365-security/air-review-approve-pending-completed-actions.md)
