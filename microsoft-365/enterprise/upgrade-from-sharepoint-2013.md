---
title: Mise à niveau à partir de SharePoint 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.collection:
- scotvorg
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Recherchez des informations et des ressources à mettre à niveau à partir de SharePoint Server 2013 et SharePoint Foundation 2013. Prise en charge des deux extrémités le 11 avril 2023.
ms.openlocfilehash: cd2c9b233685aeeee329b5ebeafcb3ff3a27f4b3
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68193276"
---
# <a name="upgrading-from-sharepoint-2013"></a>Mise à niveau à partir de SharePoint 2013

Microsoft SharePoint Server 2013 et SharePoint Foundation 2013 prendront fin le **11 avril 2023**. Cet article fournit des ressources pour vous aider à migrer vos données SharePoint Server existantes vers SharePoint Online dans Microsoft 365 ou à mettre à niveau votre environnement SharePoint 2013 local. Pour le reste de cet article, nous allons utiliser SharePoint 2013 pour faire référence à SharePoint Server 2013 et SharePoint Foundation 2013.

## <a name="what-is-end-of-support"></a>Qu’est-ce que *la fin du support* ?

La plupart des produits Microsoft ont un cycle de vie de support, au cours duquel ils bénéficient de nouvelles fonctionnalités, correctifs de bogues, correctifs de sécurité, et ainsi de suite. Après la date de fin du support, le produit ne cesse pas de fonctionner, mais Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Cela signifie qu’il n’y aura pas d’autres mises à jour, correctifs ou correctifs pour le produit (y compris les correctifs/correctifs de sécurité). Support Microsoft aura entièrement déplacé ses efforts de prise en charge vers des versions plus récentes.

> [!NOTE]
> Un cycle de vie logiciel dure généralement cinq ans de support standard à partir de la version initiale, et peut-être jusqu’à 5 ans de support étendu supplémentaire. [Les fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) peuvent vous aider à effectuer une mise à niveau vers la version suivante du logiciel ou à migrer vers Microsoft 365 (ou les deux). Assurez-vous que vous connaissez également les dates de fin de support pour les technologies sous-jacentes critiques, en particulier pour la version de Microsoft SQL Server que vous utilisez avec SharePoint. Pour plus d’informations, consultez [Politique de cycle de vie fixe](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planifier

Vérifiez les dates auxquelles la prise en charge se termine sur le site product lifecycle pour [SharePoint Server 2013](/lifecycle/products/sharepoint-server-2013) et [SharePoint Foundation 2013](/lifecycle/products/sharepoint-foundation-2013). Planifiez vos mises à niveau ou vos migrations en tenant compte de ces dates. N’oubliez pas que votre produit *ne cessera pas de fonctionner* à la date indiquée. Toutefois, étant donné que votre installation ne sera plus corrigé après cette date, vous souhaiterez planifier une transition en douceur vers la prochaine version du produit. Le tableau ci-dessous répertorie les options disponibles.

|Fin du produit de support|Good|Mieux|Idéale|
|---|---|---|---|
|SharePoint Server 2013<BR>SharePoint Foundation 2013|Mise à niveau vers SharePoint Server 2016 ou 2019|Mise à niveau vers SharePoint Server Édition d’abonnement|Migrer vers SharePoint dans Microsoft 365

## <a name="whats-next"></a>Étape suivante

Nous vous recommandons de migrer vers SharePoint dans Microsoft 365 pour tirer parti des dernières solutions de collaboration, de renseignement et de sécurité dans Microsoft 365. Les fonctionnalités d’expérience moderne de Microsoft 365 sont conçues pour être attrayantes, flexibles et performantes.

Si vous avez besoin de maintenir un déploiement SharePoint local, nous vous recommandons un déploiement hybride qui vous permettra de migrer autant de fonctionnalités SharePoint que possible vers SharePoint dans Microsoft 365. Consultez [SharePoint hybride](/sharepoint/hybrid/hybrid) pour en savoir plus et planifier une implémentation hybride.

### <a name="migrate-to-sharepoint-in-microsoft-365"></a>Migrer vers SharePoint dans Microsoft 365

Vous pouvez utiliser l’outil de migration SharePoint (SPMT) pour migrer vos sites et votre contenu vers SharePoint dans Microsoft 365. Nous disposons d’une vaste bibliothèque de contenu qui peut vous aider à planifier à l’avance, à effectuer votre migration et à résoudre les problèmes que vous pouvez rencontrer. [La vue d’ensemble de l’outil de migration SharePoint](/sharepointmigration/introducing-the-sharepoint-migration-tool) est un bon point de départ.

### <a name="upgrade-to-sharepoint-server-subscription-edition"></a>Mise à niveau vers SharePoint Server Édition d’abonnement

Même s’il n’existe pas de chemin d’accès direct à la mise à niveau de SharePoint 2013 vers l’édition d’abonnement, il s’agit toujours de la deuxième meilleure option. La raison principale est que SharePoint Server Édition d'abonnement introduit un modèle de mise à jour continue qui élimine la nécessité de publier de nouvelles versions majeures de SharePoint Server à l’avenir.

Pour effectuer une mise à niveau vers Subscription Edition, vous devez exécuter SharePoint Server 2016 ou 2019. Étant donné qu’il n’existe pas non plus de chemin direct entre SharePoint 2013 et 2019, votre meilleure option consiste à effectuer une mise à niveau vers 2016 d’abord, puis à effectuer une mise à niveau vers l’édition Abonnement. Consultez les liens ci-dessous pour en savoir plus et planifier votre mise à niveau vers Subscription Edition :

- [Mise à niveau vers SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Mise à niveau vers SharePoint Server Édition d’abonnement](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-subscription-edition)

Même si vous avez besoin de maintenir un déploiement SharePoint local, nous vous recommandons de migrer certaines parties de vos sites ou contenus vers Microsoft 365 avec [l’implémentation hybride SharePoint](/sharepoint/hybrid/hybrid) pour commencer à tirer parti des expériences de collaboration, de la sécurité et de la conformité modernes dans Microsoft 365.  

### <a name="upgrade-to-sharepoint-server-2016-or-2019"></a>Mise à niveau vers SharePoint Server 2016 ou 2019

SharePoint Server 2016 et 2019 sont des plateformes prises en charge si vous envisagez de maintenir votre déploiement SharePoint local au-delà de la fin du support pour 2013. Toutefois, **les deux versions seront prises en charge le 14 juillet 2026**. Cela signifie que vous devrez planifier une autre mise à niveau dans les 3 ans suivant la fin de la date de support pour 2013. Voici les pages de cycle de vie de support pour les deux produits :

- [Dates de cycle de vie du support SharePoint Server 2016](/lifecycle/products/sharepoint-server-2016)
- [SharePoint Server 2019 dates de cycle de vie de prise en charge](/lifecycle/products/sharepoint-server-2019)

Pour en savoir plus et planifier votre mise à niveau, consultez les articles suivants :

- [Mise à niveau vers SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Mise à niveau vers SharePoint Server 2019](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2019)

Même si vous avez besoin de maintenir un déploiement SharePoint local, nous vous recommandons de migrer certaines parties de vos sites ou contenus vers Microsoft 365 avec [l’implémentation hybride SharePoint](/sharepoint/hybrid/hybrid) pour commencer à tirer parti des expériences de collaboration, de la sécurité et de la conformité modernes dans Microsoft 365.  
