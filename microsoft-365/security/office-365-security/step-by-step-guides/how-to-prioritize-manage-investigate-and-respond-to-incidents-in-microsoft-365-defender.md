---
title: Comment hiérarchiser, gérer, examiner et répondre aux incidents dans Microsoft 365 Defender
description: Étapes de gestion des alertes déclenchées dans Microsoft 365 Defender. Recherche automatisée d’investigation et de réponse (AIR) dans l’abonnement et détermine l’impact et l’étendue d’une menace, et combine les informations en un seul incident.
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
ms.openlocfilehash: 18127cd732c0e2e1392a9c62e221dadfbd123246
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66991944"
---
# <a name="prioritize-manage-investigate--respond-to-incidents-in-microsoft-365-defender"></a>Hiérarchiser, gérer, examiner & répondre aux incidents dans Microsoft 365 Defender

Lorsque des alertes sont déclenchées dans Microsoft 365 Defender, l’investigation et la réponse automatisées (AIR) se déclenchent pour rechercher dans l’abonnement d’une organisation, déterminer l’impact et l’étendue de la menace, et rassembler les informations dans un incident unique afin que les administrateurs n’aient pas à gérer plusieurs incidents.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 plan 2 ou supérieur
- Autorisations suffisantes (lecteur sécurité, opérations de sécurité ou administrateur de sécurité, ainsi que le rôle [de recherche et de vidage](../permissions-microsoft-365-security-center.md) )

## <a name="prioritize--manage-incidents"></a>Hiérarchiser & gérer les incidents

Accédez à la page https://security.microsoft.com/incidentsIncidents du portail de sécurité.

Lorsque la page Incident se charge, vous pouvez filtrer et hiérarchiser en cliquant sur les colonnes pour trier les actions ou en appuyant sur Filtres pour appliquer un filtre tel que la source de données, les balises ou l’état.

Vous disposez maintenant d’une liste hiérarchisée d’incidents, à partir de laquelle vous pouvez choisir de renommer, d’affecter, de classer, de baliser, de modifier l’état ou d’ajouter des commentaires via le bouton Gérer les incidents.

Utilisez les filtres pour vous assurer que les éléments Microsoft Defender pour Office sont inclus.

Si vous recherchez des alertes spécifiques, utilisez la fonctionnalité de recherche d’incident (*rechercher un nom ou un ID*) ou envisagez d’utiliser le filtrage de file d’attente d’alertes sur une alerte spécifique.

## <a name="investigate--respond-to-incidents"></a>Examiner & répondre aux incidents

Une fois que vous avez hiérarchisé votre file d’attente d’incidents, cliquez sur l’incident que vous souhaitez examiner pour charger la page Vue d’ensemble des incidents. Il y aura des informations utiles telles que *MITRE ATT&techniques CK observées* et une *chronologie de l’attaque*.

Les onglets situés en haut de la page d’incident vous permettent d’explorer plus de détails, tels que les utilisateurs affectés, les boîtes aux lettres, les points de terminaison, et ainsi de suite.

L’onglet *Preuve et réponse* affiche les éléments identifiés comme liés à l’alerte d’origine via l’enquête.

Tous les éléments indiquant *l’action en attente* dans la preuve et la réponse attendent l’approbation d’un administrateur.  Le tri par colonne d’état de correction dans la vue *Toutes les preuves* est recommandé, suivi d’un clic sur l’entité ou le cluster pour charger le menu volant dans lequel vous pouvez ensuite approuver les actions le cas échéant.

Si vous devez comprendre plus en détail les éléments impliqués, vous pouvez utiliser le graphique d’incident pour voir la liaison visuelle des preuves et des entités impliquées. Vous pouvez également passer en revue les investigations sous-jacentes, qui afficheront davantage d’entités et d’éléments impliqués dans l’événement de sécurité.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez commencer à utiliser *le Centre d’actions* pour agir sur les éléments d’action en attente de tous les incidents de votre organisation si vous souhaitez vous concentrer sur les éléments d’action pour lesquels AIR doit être approuvé.  

## <a name="more-information"></a>Informations supplémentaires

[Gérer les incidents dans Microsoft 365 Defender | Microsoft Docs](../../defender/manage-incidents.md)

[Fonctionnement de l’investigation et de la réponse automatisées dans Microsoft Defender pour Office 365](../automated-investigation-response-office.md)

[Actions de correction dans Microsoft Defender pour Office 365](../air-remediation-actions.md)