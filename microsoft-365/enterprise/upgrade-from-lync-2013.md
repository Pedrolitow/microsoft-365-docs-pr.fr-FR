---
title: Mise à niveau à partir de Lync Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Recherchez des informations et des ressources à mettre à niveau à partir de Lync Server 2013. Le support prend fin le 11 avril 2023.
ms.openlocfilehash: 72b161c608ba9ac9430957b174b864943e691b76
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67740760"
---
# <a name="upgrading-from-lync-server-2013"></a>Mise à niveau à partir de Lync Server 2013

Microsoft Lync Server 2013 prendra fin le **11 avril 2023**. Cet article fournit des ressources pour vous aider à mettre à niveau votre déploiement Lync Server existant vers Microsoft Teams ou Skype Entreprise localement.

## <a name="what-is-end-of-support"></a>Qu’est-ce que *la fin du support* ?

La plupart des produits Microsoft ont un cycle de vie de support, au cours duquel ils bénéficient de nouvelles fonctionnalités, correctifs de bogues, correctifs de sécurité, et ainsi de suite. Après la date de fin du support, le produit ne cesse pas de fonctionner, mais Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Cela signifie qu’il n’y aura pas d’autres mises à jour, correctifs ou correctifs pour le produit (y compris les correctifs/correctifs de sécurité). pomoc techniczna firmy Microsoft aura entièrement déplacé ses efforts de prise en charge vers des versions plus récentes.

## <a name="plan-ahead"></a>Planifier

Vérifiez les dates auxquelles la prise en charge se termine sur le [site product lifecycle](/lifecycle/products/microsoft-lync-server-2013). Planifiez vos mises à niveau ou vos migrations en tenant compte de ces dates. N’oubliez pas que votre produit *ne cessera pas de fonctionner* à la date indiquée. Toutefois, étant donné que votre installation ne sera plus corrigé après cette date, vous souhaiterez planifier une transition en douceur vers la prochaine version du produit. Le tableau ci-dessous répertorie les options disponibles.

|Fin du produit de support|Pris en charge|Recommandé|
|---|---|---|
|Lync Server 2013|Mise à niveau vers Skype Entreprise Server 2015 ou 2019|Mettre à niveau vers Microsoft Teams

## <a name="whats-next"></a>Étape suivante

Nous vous recommandons de procéder à une mise à niveau vers Microsoft Teams. Microsoft Teams étend les fonctionnalités de Lync Server, en regroupant les conversations, les réunions, les appels, la collaboration, l’intégration d’applications et le stockage de fichiers dans une interface unique. Teams permet de simplifier la façon dont les utilisateurs effectuent leurs tâches, d’améliorer la satisfaction des utilisateurs et d’accélérer les résultats opérationnels. Nous développons continuellement les fonctionnalités Teams pour vous offrir de nouveaux moyens de communication et de collaboration, lever les barrières organisationnelles et géographiques, et renforcer l’efficacité des processus et des décisions.

Si vous ne pouvez pas effectuer de mise à niveau vers Microsoft Teams, vous pouvez effectuer une mise à niveau vers Skype Entreprise Server 2015 ou 2019. L’une des principales considérations à prendre en compte en matière de planification est que ces deux produits arriveront à expiration le 14 octobre 2025. Pour plus d’informations, consultez les pages de cycle de vie de support suivantes :

- [informations sur le cycle de vie du support Skype Entreprise Server 2015](/lifecycle/products/skype-for-business-server-2015)
- [informations sur le cycle de vie du support Skype Entreprise Server 2019](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Mettre à niveau vers Microsoft Teams

Nous avons des conseils détaillés sur la mise à niveau vers Microsoft Teams à partir de votre déploiement local. Tout d’abord, nous allons aborder certaines exigences techniques clés. Vous devez établir une connectivité hybride, ce qui vous permettra de déplacer vos utilisateurs vers Teams. [Planifier la connectivité hybride](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) donne une vue d’ensemble de la configuration d’un environnement hybride. Même si l’article se concentre sur Skype Entreprise, tous les concepts s’appliquent également à Lync Server 2013. Pour plus d’informations sur la version requise pour Lync Server 2013, consultez la section [relative à la version requise du serveur](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) .

Vous devez également vous assurer que votre déploiement de Lync Server 2013 est entièrement à jour. Nous publions une [liste de toutes les dernières mises à jour pour Lync Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164) . Toutefois, la mise à jour suivante est un prérequis pour une mise à niveau vers Microsoft Teams :

- [Mise à jour cumulative 5.0.8308.1149 de septembre 2021 pour Lync Server 2013, Composants principaux](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043) : cette mise à jour remplace l’authentification Live ID par le protocole d’authentification OAuth pour l’applet `Move-CSUser` de commande, qui est utilisé pour déplacer des utilisateurs locaux vers Microsoft Teams.

Même si l’expérience utilisateur dans Microsoft Teams est beaucoup plus riche et supérieure à Lync, elle est également radicalement différente. Par conséquent, vous devez également préparer votre organisation et vos utilisateurs pour garantir une adoption rapide de Microsoft Teams. Nous disposons d’une multitude d’informations sur la préparation de votre organisation, la planification de votre mise à niveau vers Teams et la réussite du déploiement.

**Nous vous recommandons de commencer sur notre [portail de mise à niveau Teams](/MicrosoftTeams/upgrade-skype-teams)** , où vous trouverez des informations techniques, des ressources de formation, des liens vers des sessions Ignite, des ressources d’aide disponibles, des études de cas, etc.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Capture d’écran du portail de mise à niveau Teams":::

### <a name="upgrade-to-skype-for-business-server"></a>Effectuer la mise à niveau vers Skype Entreprise Server

Le chemin d’accès à Skype Entreprise Server va être différent en fonction de la version vers laquelle vous choisissez de mettre à niveau. Skype Entreprise Server 2015 prend en charge une mise à niveau sur place à partir de Lync Server 2013. D’autre part, pour effectuer une mise à niveau vers Skype Entreprise Server 2019, vous devez d’abord introduire Skype Entreprise Server 2019 à votre installation de Lync Server 2013 via l’ajout d’un ou plusieurs nouveaux serveurs, puis transférer des opérations vers les nouveaux serveurs 2019 que vous avez ajoutés.

Un point important à prendre en compte est que la phase de support actuelle pour chaque produit : Skype Entreprise 2019 est en support standard et Skype Entreprise 2015 est actuellement en support étendu.  Par conséquent, nous vous recommandons d’effectuer une mise à niveau vers Skype Entreprise Server 2019. Pour en savoir plus sur la différence entre le support standard et le support étendu, consultez [politique de cycle de vie fixe](/lifecycle/policies/fixed).

Pour plus d’informations sur chaque scénario de mise à niveau, consultez les ressources suivantes.

- [Mise à niveau vers Skype Entreprise Server 2019](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Mise à niveau vers Skype Entreprise Server 2015](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
