---
title: Comment hiérarchiser et gérer les enquêtes et réponses automatisées (AIR).
description: Procédure d’analyse et d’approbation des actions AIR directement à partir du Centre d’actions. Lorsque des alertes sont déclenchées, l’analyse automatisée et la réponse (AIR) détermine l’étendue de l’impact d’une menace dans votre organisation et fournit des actions de correction recommandées.
search.product: ''
ms.service: microsoft-365-security
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
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: 6532def135183bb67a2d8e5d98e2561deb70bec0
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67742134"
---
# <a name="prioritize-and-manage-automated-investigations-and-response-air"></a>Hiérarchiser et gérer les enquêtes et réponses automatisées (AIR)

Air (Automated Investigation and Response) permet à votre équipe chargée des opérations de sécurité de gagner du temps et des efforts.

- Lorsque des alertes sont déclenchées, une investigation automatisée détermine l’étendue de l’impact d’une menace dans votre organisation et fournit des actions de correction recommandées.
- Les équipes de sécurité peuvent gagner du temps en tirant parti de l’automatisation AIR pour réduire le besoin de chasse manuelle.
- Ces investigations peuvent identifier les e-mails qui n’ont pas été nettoyés par le vidage automatique de zéro heure (ZAP) ou d’autres corrections.
- Les enquêtes AIR identifient également les configurations de boîte aux lettres qui peuvent être risquées ou indiquer une boîte aux lettres compromise.

Les actions d’investigation (et les investigations) sont accessibles à partir de plusieurs points du portail de sécurité Microsoft : par le biais *d’incidents*, *d’alertes* ou de *Centre d’actions*. L’utilisation des administrateurs est basée sur le flux de travail qu’un administrateur poursuit.

## <a name="why-use-the-action-center-workflow"></a>Pourquoi utiliser le flux de travail du Centre d’actions

À mesure que des enquêtes automatisées sur *Email & contenu de collaboration* entraînent des verdicts, tels que *malveillants* ou *suspects*, certaines actions de correction sont créées. Les actions de correction suggérées ne sont pas effectuées automatiquement. SecOps doit accéder à chaque enquête pour *approuver* ces actions suggérées. Dans le *Centre d’actions* , toutes les actions en attente sont agrégées pour approbation rapide.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 plan 2 ou supérieur (inclus avec E5)
- Autorisations suffisantes (lecteur sécurité, opérations de sécurité ou administrateur de sécurité, ainsi que le rôle [de recherche et de vidage](../permissions-microsoft-365-security-center.md) )

## <a name="steps-to-analyze-and-approve-air-actions-directly-from-the-action-center"></a>Étapes d’analyse et d’approbation des actions AIR directement à partir du Centre d’actions

1. Accédez à [Microsoft 365 Defender portail](https://security.microsoft.com/action-center) et connectez-vous.
2. Lorsque le Centre d’actions se charge, filtrez et hiérarchisez en cliquant sur les colonnes pour trier les actions, ou appuyez sur **Filtres** pour appliquer un filtre tel que le *type d’entité* (pour une URL particulière) ou un type d’action (par exemple, un e-mail de suppression réversible).
3. Un menu volant s’ouvre une fois qu’une action est cliqué. Il apparaît sur le côté droit de l’écran pour révision.
4. Pour plus d’informations sur la raison pour laquelle une action est demandée, sélectionnez **Ouvrir la page d’investigation** dans le menu volant pour en savoir plus sur l’enquête ou les alertes liées à cette action. (Les administrateurs peuvent également approuver les actions affichées sur la page d’enquête en sélectionnant l’onglet *Actions en attente* .)
5. Sinon, **sélectionnez Approuver** pour effectuer l’action recommandée directement à partir du Centre d’actions.
6. Refusez l’action, si vous déterminez qu’elle n’est pas nécessaire.

## <a name="check-air-history"></a>Vérifier l’historique AIR

1. Accédez au [portail Microsoft 365 Defender](https://security.microsoft.com) et connectez-vous.
2. Dans le volet de navigation de gauche, développez **Action & soumissions** , puis cliquez sur **Centre d’actions**.
3. Lorsque le Centre d’action se charge, appuyez sur l’onglet **Historique** .
4. Affichez l’historique de l’AIR, y compris les décisions prises, la source d’action et l’administrateur qui a pris la décision, le cas échéant.

## <a name="more-information"></a>Informations supplémentaires

[Afficher les résultats d’une enquête automatisée dans Microsoft 365 - Office 365 | Microsoftova dokumentacija](../air-view-investigation-results.md)

[En savoir plus sur l’approbation et le rejet des actions en attente à partir de la page Investigation](../air-review-approve-pending-completed-actions.md)
