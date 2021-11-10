---
title: Mise à niveau à SharePoint 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: sharepoint-server-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Trouvez des informations et des ressources à mettre à niveau depuis SharePoint Server 2013 et SharePoint Foundation 2013. Le support pour les deux se termine le 11 avril 2023.
ms.openlocfilehash: 05f545b67d60d6bcc45587049e49a5f5c1f6d654
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889884"
---
# <a name="upgrading-from-sharepoint-2013"></a>Mise à niveau à SharePoint 2013

Les Microsoft SharePoint Server 2013 et SharePoint Foundation 2013 atteindront la fin du support le **11 avril 2023.** Cet article fournit des ressources pour vous aider à migrer vos données SharePoint Server existantes vers SharePoint Online dans Microsoft 365 ou mettre à niveau votre environnement local SharePoint 2013. Pour le reste de cet article, nous allons utiliser SharePoint 2013 pour faire référence à SharePoint Server 2013 et SharePoint Foundation 2013.

## <a name="what-is-end-of-support"></a>Qu’est-ce *que la fin de la prise en charge*?

La plupart des produits Microsoft ont un cycle de vie de support, au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogue, des correctifs de sécurité, etc. Après la date de fin du support, le produit ne cesse pas de fonctionner, mais Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.

- Correctifs de sécurité pour les vulnérabilités qui peuvent rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Cela signifie qu’il n’y aura pas de mises à jour, de correctifs ou de correctifs supplémentaires pour le produit (y compris les correctifs/correctifs de sécurité). Le support Microsoft aura entièrement déplacé ses efforts de support vers des versions plus récentes.

> [!NOTE]
> Un cycle de vie des logiciels dure généralement cinq ans de support classique à partir de la version initiale, et potentiellement jusqu’à 5 ans supplémentaires de support étendu. [Les fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) peuvent vous aider à passer à la version suivante du logiciel ou à migrer vers Microsoft 365 (ou les deux). Assurez-vous de connaître également les dates de fin de prise en charge des technologies sous-jacentes critiques, en particulier pour la version de Microsoft SQL Server que vous utilisez avec SharePoint. Pour plus d’informations, voir [Politique de cycle de vie fixe.](https://support.microsoft.com/help/14085)

## <a name="plan-ahead"></a>Planifier à l’avance

Vérifiez les dates qui se terminent sur le site Cycle de vie du produit [pour SharePoint Server 2013](/lifecycle/products/sharepoint-server-2013) [et SharePoint Foundation 2013](/lifecycle/products/sharepoint-foundation-2013). Planifiez vos mises à niveau ou migrations en ayant ces dates à l’esprit. N’oubliez pas *que votre produit ne cessera pas de fonctionner* à la date répertoriée. Toutefois, étant donné que votre installation ne sera plus corrigé après cette date, vous souhaiterez planifier une transition en douceur vers la prochaine version du produit. Le tableau ci-dessous répertorie les options disponibles.

|Produit de fin de support|Good|Meilleure|Idéale|
|---|---|---|---|
|SharePoint Server 2013<BR>SharePoint Foundation 2013|Mise à niveau vers SharePoint Server 2016 ou 2019|Mise à niveau vers SharePoint Server Édition d’abonnement|Migrer vers SharePoint dans Microsoft 365

## <a name="whats-next"></a>Étape suivante

Nous vous recommandons de migrer vers SharePoint dans Microsoft 365 pour tirer parti des dernières solutions de collaboration, d’intelligence et de sécurité dans Microsoft 365. Les fonctionnalités d’expérience Microsoft 365 sont conçues pour être attrayantes, flexibles et performantes.

Si vous avez besoin de maintenir un déploiement SharePoint local, nous vous recommandons un déploiement hybride qui vous permettra de migrer autant de fonctionnalités SharePoint que possible pour SharePoint dans Microsoft 365. Voir [SharePoint hybride](/sharepoint/hybrid/hybrid) pour en savoir plus sur une implémentation hybride et la planifier.

### <a name="migrate-to-sharepoint-in-microsoft-365"></a>Migrer vers SharePoint dans Microsoft 365

Vous pouvez utiliser l’outil SharePoint Migration Tool (SPMT) pour migrer vos sites et votre contenu vers SharePoint dans Microsoft 365. Nous avons une bibliothèque complète de contenu qui peut vous aider à planifier l’avenir, à effectuer votre migration et à résoudre les problèmes que vous pouvez rencontrés. [Une vue d’ensemble SharePoint’outil](/sharepointmigration/introducing-the-sharepoint-migration-tool) de migration est un bon point de départ.

### <a name="upgrade-to-sharepoint-server-subscription-edition"></a>Mise à niveau vers SharePoint Server Édition d’abonnement

Même s’il n’existe pas de chemin d’accès direct pour la mise à niveau de SharePoint 2013 vers Subscription Edition, il s’agit toujours de la deuxième meilleure option. La principale raison est que SharePoint Server Subscription Edition introduit un modèle de mise à jour continue qui élimine la nécessité de publier de nouvelles versions majeures de SharePoint Server à l’avenir.

Pour mettre à niveau vers Subscription Edition, vous devez SharePoint Server 2016 ou 2019. Étant donné qu’il n’existe pas non plus de chemin d’accès direct entre SharePoint 2013 et 2019, votre meilleure option consiste à passer d’abord à la version 2016, puis à la mise à niveau vers Subscription Edition. Consultez les liens ci-dessous pour en savoir plus sur et planifier votre mise à niveau vers Subscription Edition :

- [Mise à niveau vers SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Mise à niveau vers SharePoint Server Édition d’abonnement](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-subscription-edition)

Même si vous avez besoin de maintenir un déploiement SharePoint local, nous vous recommandons de migrer des parties de vos sites ou de votre contenu vers Microsoft 365 avec une implémentation hybride [SharePoint](/sharepoint/hybrid/hybrid) pour commencer à tirer parti des expériences de collaboration modernes, des fonctionnalités de sécurité et de conformité dans Microsoft 365.  

### <a name="upgrade-to-sharepoint-server-2016-or-2019"></a>Mise à niveau vers SharePoint Server 2016 ou 2019

SharePoint Server 2016 et 2019 sont des plateformes pris en charge si vous prévoyez de maintenir votre déploiement SharePoint local au-delà de la fin de la prise en charge pour 2013. Toutefois, les deux versions atteindront la fin de la prise en charge **le 14 juillet 2026.** Cela signifie que vous devrez planifier une autre mise à niveau dans les 3 ans après la date de fin du support pour 2013. Voici les pages de cycle de vie de support pour les deux produits :

- [SharePoint Server 2016 support lifecycle dates](/lifecycle/products/sharepoint-server-2016)
- [SharePoint Server 2019 dates de cycle de vie du support](/lifecycle/products/sharepoint-server-2019)

Pour en savoir plus et planifier votre mise à niveau, consultez les articles suivants :

- [Mise à niveau vers SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Mise à niveau vers SharePoint Server 2019](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2019)

Même si vous avez besoin de maintenir un déploiement SharePoint local, nous vous recommandons de migrer des parties de vos sites ou de votre contenu vers Microsoft 365 avec une implémentation hybride [SharePoint](/sharepoint/hybrid/hybrid) pour commencer à tirer parti des expériences de collaboration modernes, des fonctionnalités de sécurité et de conformité dans Microsoft 365.  
