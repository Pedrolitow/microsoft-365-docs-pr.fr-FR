---
title: Mise à niveau à partir de Lync Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Recherchez des informations et des ressources à mettre à niveau à partir de Lync Server 2013. Le support prend fin le 11 avril 2023.
ms.openlocfilehash: a770ce6acab4320bc84e920b1c527e9c63e72bbb
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889868"
---
# <a name="upgrading-from-lync-server-2013"></a>Mise à niveau à partir de Lync Server 2013

Microsoft Lync Server 2013 prendra fin le **11 avril 2023.** Cet article fournit des ressources pour vous aider à mettre à niveau votre déploiement Lync Server existant vers Microsoft Teams ou Skype Entreprise sur site.

## <a name="what-is-end-of-support"></a>Qu’est-ce *que la fin de la prise en charge*?

La plupart des produits Microsoft ont un cycle de vie de support, au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogue, des correctifs de sécurité, etc. Après la date de fin du support, le produit ne cesse pas de fonctionner, mais Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.

- Correctifs de sécurité pour les vulnérabilités qui peuvent rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Cela signifie qu’il n’y aura pas de mises à jour, de correctifs ou de correctifs supplémentaires pour le produit (y compris les correctifs/correctifs de sécurité). Le support Microsoft aura entièrement déplacé ses efforts de support vers des versions plus récentes.

## <a name="plan-ahead"></a>Planifier à l’avance

Vérifiez les dates de fin de la prise en charge sur le [site cycle de vie du produit.](/lifecycle/products/lync-server-2013) Planifiez vos mises à niveau ou migrations en ayant ces dates à l’esprit. N’oubliez pas *que votre produit ne cessera pas de fonctionner* à la date répertoriée. Toutefois, étant donné que votre installation ne sera plus corrigé après cette date, vous souhaiterez planifier une transition en douceur vers la prochaine version du produit. Le tableau ci-dessous répertorie les options disponibles.

|Produit de fin de support|Pris en charge|Recommandé|
|---|---|---|
|Lync Server 2013|Mise à niveau vers Skype Entreprise Server 2015 ou 2019|Mettre à niveau vers Microsoft Teams

## <a name="whats-next"></a>Étape suivante

Nous vous recommandons de mettre à niveau vers Microsoft Teams. Microsoft Teams étend les fonctionnalités de Lync Server, en regroupant la conversation, les réunions, les appels, la collaboration, l’intégration d’applications et le stockage de fichiers dans une interface unique. Teams simplifie la façon dont les utilisateurs s’en sortent, améliorent la satisfaction des utilisateurs et accélèrent les résultats de l’entreprise. Nous développons continuellement les fonctionnalités Teams pour vous offrir de nouveaux moyens de communication et de collaboration, lever les barrières organisationnelles et géographiques, et renforcer l’efficacité des processus et des décisions.

Si vous ne pouvez pas mettre à niveau vers Microsoft Teams, vous pouvez mettre à niveau vers Skype Entreprise Server 2015 ou 2019. Il est important de tenir compte de la planification pour savoir que ces deux produits atteindront la fin du support le 14 octobre 2025. Pour plus d’informations, consultez les pages de cycle de vie de support suivantes :

- [Skype Entreprise Server 2015 sur le cycle de vie du support](/lifecycle/products/skype-for-business-server-2015)
- [Skype Entreprise Server de cycle de vie du support technique 2019](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Mettre à niveau vers Microsoft Teams

Nous avons des instructions détaillées sur la mise à Microsoft Teams à partir de votre déploiement local. Tout d’abord, examinons quelques-unes des principales exigences techniques. Vous devez établir une connectivité hybride qui vous permettra de déplacer vos utilisateurs vers Teams. [Planifier la connectivité hybride donne](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) une vue d’ensemble de la configuration hybride. Même si l’article est axé sur Skype Entreprise, tous les concepts s’appliquent également à Lync Server 2013. Consultez [la section sur la version du](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) serveur requise pour obtenir des détails spécifiques à Lync Server 2013.

Vous devez également vous assurer que votre déploiement Lync Server 2013 est entièrement à jour. Nous publions une liste de toutes les dernières mises à jour pour [Lync Server 2013.](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164) Toutefois, la mise à jour suivante est une condition préalable pour une mise à niveau vers Microsoft Teams :

- Mise à jour cumulative [5.0.8308.1149 de septembre 2021 pour Lync Server 2013, Composants](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043)principaux : cette mise à jour remplace l’authentification Live ID par le protocole d’authentification OAuth pour la cmdlet, qui est utilisé pour déplacer des utilisateurs locaux vers `Move-CSUser` Microsoft Teams.

Même si l’expérience utilisateur dans Microsoft Teams est beaucoup plus riche et supérieure à Lync, elle est également considérablement différente. Par conséquent, vous devrez également préparer votre organisation et vos utilisateurs pour garantir une adoption rapide des Microsoft Teams. Nous avons un grand nombre d’informations disponibles sur la façon de préparer votre organisation, planifier votre mise à niveau vers Teams et garantir un déploiement réussi. 

Nous vous recommandons de commencer sur notre portail de mise à **[niveau Teams](/MicrosoftTeams/upgrade-skype-teams)** où vous trouverez des informations techniques, des ressources de formation, des liens vers des sessions Ignite, des ressources d’aide disponibles, des études de cas, etc.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Capture d’écran du portail Teams de mise à niveau":::

### <a name="upgrade-to-skype-for-business-server"></a>Effectuer la mise à niveau vers Skype Entreprise Server

Le chemin d’Skype Entreprise Server sera différent en fonction de la version que vous choisissez de mettre à niveau. Skype Entreprise Server 2015 prend en charge une mise à niveau sur place à partir de Lync Server 2013. En revanche, pour mettre à niveau vers Skype Entreprise Server 2019, vous devez d’abord présenter Skype Entreprise Server 2019 à votre organisation Lync Server 2013, puis transférer les opérations vers le nouveau serveur. 

Il est important de prendre en compte le fait que la phase de support actuelle pour chaque produit : Skype Entreprise 2019 est dans le support classique et Skype Entreprise 2015 est actuellement en prise en charge étendue.  Par conséquent, nous vous recommandons d’Skype Entreprise Server 2019. Pour en savoir plus sur la différence entre le support classique et le support étendu, consultez [la politique de cycle de vie fixe.](/lifecycle/policies/fixed)

Consultez les ressources suivantes pour obtenir des informations détaillées sur chaque scénario de mise à niveau.

- [Mise à niveau vers Skype Entreprise Server 2019](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Mise à niveau vers Skype Entreprise Server 2015](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
