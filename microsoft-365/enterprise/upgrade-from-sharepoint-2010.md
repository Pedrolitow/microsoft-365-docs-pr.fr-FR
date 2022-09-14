---
title: Mise à jour à jour de SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: Recherchez des informations et des ressources à mettre à niveau à partir de SharePoint 2010 et SharePoint Server 2010. Prise en charge des deux extrémités le 13 avril 2021.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a40f64fff001e8dbbc96b20039b2bd578f4e44a0
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67672840"
---
# <a name="upgrading-from-sharepoint-2010"></a>Mise à jour à jour de SharePoint 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft SharePoint 2010 et SharePoint Server 2010 prendront fin le **13 avril 2021**. Cet article fournit des ressources pour vous aider à migrer vos données SharePoint Server 2010 existantes vers SharePoint Online dans Microsoft 365 ou à mettre à niveau votre environnement SharePoint Server 2010 local.

## <a name="what-is-end-of-support"></a>Qu’est-ce que *la fin du support* ?

La plupart des produits Microsoft ont un cycle de vie de support, au cours duquel ils bénéficient de nouvelles fonctionnalités, correctifs de bogues, correctifs de sécurité, et ainsi de suite. Après la date de fin du support, le produit ne cesse pas de fonctionner, mais Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Cela signifie qu’il n’y aura pas d’autres mises à jour, correctifs ou correctifs pour le produit (y compris les correctifs/correctifs de sécurité). Support Microsoft aura entièrement déplacé ses efforts de prise en charge vers des versions plus récentes.

Comme la fin de la prise en charge de SharePoint Server 2010 approche, supprimez les données dont vous n’avez plus besoin avant de mettre à niveau le produit et de migrer vos données importantes.

> [!NOTE]
> Un cycle de vie logiciel dure généralement dix ans à partir de la version initiale. [Les fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) peuvent vous aider à effectuer une mise à niveau vers la version suivante du logiciel ou à migrer vers la migration de Microsoft 365 (ou les deux). Assurez-vous que vous connaissez également les dates de fin de support pour les technologies sous-jacentes critiques, en particulier pour la version de Microsoft SQL Server que vous utilisez avec SharePoint. Pour plus d’informations, consultez [Politique de cycle de vie fixe](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planifier

Vérifiez les dates auxquelles la prise en charge se termine sur le [site product lifecycle](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). Planifiez vos mises à niveau ou vos migrations en tenant compte de ces dates. N’oubliez pas que votre produit *ne cessera pas de fonctionner* à la date indiquée. Toutefois, étant donné que votre installation ne sera plus corrigé après cette date, vous souhaiterez planifier une transition en douceur vers la prochaine version du produit.

Cette matrice permet de tracer un cours parmi les options de migration :

|Fin du produit de support|Bonne |Idéale|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (local)|SharePoint Online|
||SharePoint Server 2013 hybride avec SharePoint Online|SharePoint Server 2016 (local)|
|||Recherche hybride dans le cloud SharePoint|

Si vous choisissez une option à l’extrémité inférieure de l’échelle (bonne), vous devez commencer à planifier une autre mise à niveau peu après votre migration à partir de SharePoint Server 2010.

Voici les trois chemins que vous pouvez suivre pour éviter la fin de la prise en charge de SharePoint Server 2010.

![Chemins de mise à niveau SharePoint Server 2010.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> La fin du support pour SharePoint Server 2010 et SharePoint Foundation 2010 est prévue pour le 13 avril 2021. Mais veillez à vérifier le [site de cycle de vie des](https://support.microsoft.com/lifecycle) produits pour connaître les dates les plus récentes.

## <a name="whats-next"></a>Étape suivante

SharePoint Server 2013 et SharePoint Foundation 2013 peuvent être installés localement sur vos propres serveurs. Vous pouvez également utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft 365. Vous pouvez :

- Migrer vers SharePoint Online.

- Mettez à niveau SharePoint Server ou SharePoint Foundation en local.

- Effectuez les deux opérations ci-dessus.

- Implémentez une solution [hybride SharePoint](/sharepoint/hybrid/hybrid) .

Tenez compte des coûts cachés liés à la maintenance d’une batterie de serveurs, notamment la maintenance ou la migration des personnalisations et la mise à niveau du matériel. Si vous avez pris en compte ces facteurs, il sera plus facile de mettre à niveau localement. Si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités sans personnalisation intensive, vous pouvez bénéficier d’une migration planifiée vers SharePoint Online. Pour un environnement SharePoint Server local, vous pouvez également envisager de déplacer des données dans SharePoint Online pour réduire la surcharge de gestion matérielle.

> [!NOTE]
> Les administrateurs SharePoint peuvent créer un abonnement Microsoft 365, configurer de nouveaux sites SharePoint Online, puis supprimer sharePoint Server 2010 proprement, en prenant uniquement les documents essentiels aux nouveaux sites. Ensuite, toutes les données restantes peuvent être vidées du site SharePoint Server 2010 dans des archives locales.

|SharePoint Online|SharePoint Server local|
|---|---|
|Coût élevé dans le temps (plan/exécution/vérification)|Coût élevé dans le temps (plan/exécution/vérification)|
|Réduction du coût des fonds (aucun achat de matériel)|Coût plus élevé des fonds (achats de matériel)|
|Coût unique de la migration|Coût unique répété par migration future|
|Faible coût total de possession/maintenance|Coût total élevé de possession/maintenance|

Un passage unique à Microsoft 365 aura un coût plus élevé lorsque vous organisez les données et décidez de ce qu’il faut prendre dans le cloud et de ce qu’il faut laisser derrière vous. Toutefois, une fois vos données migrées, les mises à niveau futures seront automatiques, car vous n’aurez plus besoin de gérer les mises à jour matérielles et logicielles. Et le temps d’attente de votre batterie de serveurs sera soutenu par un [contrat de niveau de service (SLA) Microsoft](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement).

### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online offre toutes les fonctionnalités dont vous avez besoin. Consultez la [description du service SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

Vous ne pouvez pas migrer directement de SharePoint Server 2010 (ou SharePoint Foundation 2010) vers SharePoint Online. Une grande partie du travail de migration est manuelle. Mais cette étape vous donne la possibilité d’élaguer des données et des sites qui ne sont plus nécessaires avant le déplacement. Vous pouvez archiver d’autres données dans le stockage. 

N’oubliez pas que SharePoint Server 2010 et SharePoint Foundation 2010 ne cesseront pas de fonctionner à la fin du support. Ainsi, les administrateurs peuvent avoir une période pendant laquelle SharePoint est toujours en cours d’exécution si leurs clients oublient de déplacer certaines de leurs données.

Si vous effectuez une mise à niveau vers SharePoint Server 2013 ou SharePoint Server 2016 et décidez de placer des données dans SharePoint Online, vous pouvez utiliser [l’API de migration SharePoint](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) pour migrer des informations vers OneDrive Entreprise.

|Avantage SharePoint Online|Inconvénient de SharePoint Online|
|---|---|
|Microsoft fournit le matériel SPO et toute l’administration matérielle.|Les fonctionnalités disponibles peuvent différer entre SharePoint Server local et SPO.|
|Vous êtes l’administrateur SharePoint ou l’administrateur général de votre abonnement et pouvez affecter des administrateurs à des sites SPO.|Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server en local n’existent pas (ou ne sont pas nécessaires) dans le rôle Administrateur SharePoint dans Microsoft 365. Toutefois, l’administration SharePoint, l’administration de la collection de sites et la propriété du site sont locales pour votre organisation.|
|Microsoft applique des correctifs, des correctifs et des mises à jour au matériel et aux logiciels sous-jacents, y compris les serveurs SQL sur lesquels SharePoint Online s’exécute.|Étant donné qu’il n’existe aucun accès au système de fichiers sous-jacent dans le service, la personnalisation est limitée.|
|Microsoft publie des [contrats de niveau de service](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) et se déplace rapidement pour résoudre les incidents au niveau du service.|Les options de sauvegarde et de restauration et autres options de récupération sont automatisées par le service dans SharePoint Online. Les sauvegardes sont remplacées si non utilisées.|
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués en continu dans le service par Microsoft.|Les modifications apportées à l’interface utilisateur et aux autres fonctionnalités SharePoint sont installées par le service et doivent peut-être être activées ou désactivées.|
|Microsoft 365 répond à de nombreuses normes du secteur : [offres de conformité Microsoft](/compliance/regulatory/offering-home).|[L’assistance FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de route de [contenu de migration SharePoint Online et OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Support Microsoft les ingénieurs et les employés du centre de données n’ont pas d’accès administrateur illimité à votre abonnement.|Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version la plus récente de SharePoint ou si une batterie de serveurs secondaire est requise pour la mise à niveau.|
|Les fournisseurs de solutions peuvent vous aider dans la tâche unique de migration de vos données vers SharePoint Online.|Toutes les modifications apportées à SharePoint Online ne sont pas sous votre contrôle. Après la migration, les différences de conception dans les menus, les bibliothèques et d’autres fonctionnalités peuvent affecter temporairement l’utilisation.|
|Les produits en ligne sont mis à jour automatiquement sur l’ensemble du service. Les fonctionnalités peuvent être dépréciés, mais il n’existe pas de véritable fin de cycle de vie du support.|Il existe un cycle de vie de fin de support pour SharePoint Server ou SharePoint Foundation, ainsi que pour les serveurs SQL sous-jacents.|

Si vous avez décidé de créer un site Microsoft 365 et que vous y migrez manuellement des données en fonction des besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

À partir de SharePoint Server 2019, les mises à niveau doivent être effectuées *en série*. Il n’existe aucun moyen de mettre à niveau directement SharePoint Server 2010 vers SharePoint Server 2016 ou SharePoint 2019. Chemin de mise à niveau série :

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Il faudra du temps et de la planification pour suivre le chemin d’accès complet de SharePoint 2010 à SharePoint Server 2016. Les mises à niveau impliquent des coûts pour le matériel (les serveurs SQL doivent également être mis à niveau), les logiciels et l’administration. En outre, les personnalisations peuvent avoir besoin d’être mises à niveau ou même abandonnées. Veillez à documenter les personnalisations critiques avant de mettre à niveau votre batterie de serveurs SharePoint Server.

> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2010 de fin de prise en charge, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour télécharger et charger à nouveau du contenu, par exemple). Mais il existe des pièges potentiels à ces déplacements manuels, tels que les documents provenant de 2010 ayant un compte en cours de dernière modification avec l’alias du compte qui effectue le déplacement manuel. Et certains travaux doivent être effectués à l’avance, tels que la création de sites, de sous-sites, d’autorisations et de structures de liste. Veillez à nettoyer votre environnement avant la mise à niveau. Tenez compte des données que vous pouvez déplacer dans le stockage ou dont vous n’avez plus besoin. Cela peut réduire l’impact de la migration. Soyez certain que votre batterie de serveurs existante est fonctionnelle avant la mise à niveau, et (certainement) avant de mettre hors service !

N’oubliez pas de consulter les *chemins de mise à niveau pris en charge et non pris en charge* :

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Si vous avez *des personnalisations*, il est essentiel de planifier chaque étape du chemin de migration :

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Avantage local|Inconvénient local|
|---|---|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint (et de son SQL), à partir du matériel serveur.|Tous les arrêts et correctifs sont de la responsabilité de votre entreprise. Toutefois, vous pouvez engager des Support Microsoft payants si votre produit n’a pas dépassé la fin du support.|
|Ensemble complet de fonctionnalités de SharePoint Server en local avec la possibilité de connecter votre batterie de serveurs locale à un abonnement SharePoint Online via un abonnement hybride.|La mise à niveau, les correctifs de sécurité, les mises à niveau matérielles et toute la maintenance de SharePoint Server et de sa batterie SQL sont gérés localement.|
|Accès complet pour des options de personnalisation plus grandes qu’avec SharePoint Online.|Les [offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.|
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués localement sous votre contrôle.|Microsoft 365 peut mettre à la disposition de SharePoint Online des fonctionnalités qui n’interagissent pas avec SharePoint Server en local.|
|Les fournisseurs de solutions peuvent aider à migrer des données vers la prochaine version de SharePoint Server (et au-delà).|Vos sites SharePoint Server n’utilisent pas automatiquement les certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) , comme indiqué dans SharePoint Online.|
|Contrôle total des conventions d’affectation de noms et des options de sauvegarde et de restauration et autres options de récupération dans SharePoint Server en local.|SharePoint Server local est sensible aux cycles de vie des produits.|

### <a name="upgrade-resources"></a>Mettre à niveau des ressources

Commencez par comparer les exigences matérielles et logicielles. Si votre environnement actuel ne répond pas aux exigences de base, vous devrez peut-être d’abord mettre à niveau le matériel dans la batterie de serveurs ou les serveurs SQL. 

Vous pouvez décider de déplacer certains de vos sites vers le matériel « persistant » de SharePoint Online. Une fois que vous avez effectué votre évaluation, suivez les chemins et méthodes de mise à niveau pris en charge.

- *Configuration matérielle/logicielle requise pour :*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Limites et limites logicielles pour :*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)

- *Vue d’ensemble du processus de mise à niveau pour :*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>Créer une solution hybride avec SharePoint Online et SharePoint Server en local

Une configuration hybride offre le meilleur de l’environnement local et en ligne pour répondre à certains besoins de migration. Vous pouvez connecter des batteries de serveurs SharePoint Server 2013, 2016 ou 2019 à SharePoint Online pour créer un environnement hybride SharePoint : [Découvrez les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

Si une batterie de serveurs SharePoint Server hybride est votre objectif de migration, déterminez les sites et les utilisateurs à déplacer en ligne et qui doivent rester locaux. Le classement du contenu de votre batterie de serveurs SharePoint Server comme ayant un impact élevé, moyen ou faible sur votre entreprise peut vous aider à prendre cette décision. Vous devrez peut-être uniquement partager des comptes d’utilisateur pour la connexion et l’index de recherche SharePoint Server avec SharePoint Online. Mais ce facteur peut ne pas être clair tant que vous n’avez pas examiné la façon dont vos sites sont utilisés. Si votre entreprise décide ultérieurement de migrer tout votre contenu vers SharePoint Online, vous pouvez déplacer tous les comptes et données restants en ligne et désactiver votre batterie de serveurs locale. La gestion/l’administration de la batterie de serveurs SharePoint sera effectuée via les consoles Microsoft 365 à partir de ce stade.

Veillez à vous familiariser avec les types existants d’hybrides et à configurer la connexion entre votre batterie sharePoint locale et votre abonnement Microsoft 365.

|Option|Description|
|---|---|
|[Offres de conformité Microsoft](/compliance/regulatory/offering-home).|[L’assistance FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.<br/><br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de route de [contenu de migration SharePoint Online et OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Support Microsoft les ingénieurs et les employés du centre de données n’ont pas d’accès administrateur illimité à votre abonnement.|Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version la plus récente de SharePoint, ou si une batterie de serveurs secondaire est nécessaire.|
|Les partenaires peuvent vous aider dans la tâche unique de migration de vos données vers SharePoint Online.||
|Les produits en ligne sont mis à jour automatiquement sur l’ensemble du service. Les fonctionnalités peuvent être dépréciés, mais il n’y a pas de véritable fin de prise en charge.||

Si vous avez décidé de créer un site Microsoft 365 et d’y migrer manuellement les données en fonction des besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe aucun moyen d’ignorer les versions dans les mises à niveau SharePoint. Cela signifie que les mises à niveau s’exécutent en série :

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Prendre l’intégralité du chemin d’accès de SharePoint 2007 à SharePoint Server 2016 implique un investissement important de temps et implique du matériel (les serveurs SQL doivent également être mis à niveau), des logiciels et des coûts d’administration. Les personnalisations doivent être mises à niveau ou abandonnées, en fonction de la criticité de la fonctionnalité.

> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 en fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour télécharger et charger à nouveau du contenu, par exemple). Toutefois, ces déplacements manuels présentent certains inconvénients, tels que les déplacements de documents remplaçant le dernier compte modifié par l’alias du compte qui effectue le déplacement manuel. Et beaucoup de travail doit être effectué à l’avance, comme la recréer des sites, des sous-sites, des autorisations et des structures de liste. Dans tous les cas, tenez compte des données que vous pouvez déplacer dans le stockage ou n’avez plus besoin de réduire l’impact de la migration.

Veillez à nettoyer votre environnement avant la mise à niveau. Soyez certain que votre batterie de serveurs existante est fonctionnelle avant la mise à niveau, et certainement avant la mise hors service !

N’oubliez pas de consulter les *chemins de mise à niveau pris en charge et non pris en charge* :

- 
  [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Si vous avez *des personnalisations*, il est essentiel de planifier votre mise à niveau pour chaque étape du chemin de migration :

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Professionnel local|Local con|
|---|---|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, du matériel serveur vers le haut.|Tous les arrêts et correctifs sont de la responsabilité de votre entreprise. (Toutefois, vous pouvez engager des Support Microsoft payantes si votre produit n’a pas dépassé la fin du support.)|
|Ensemble complet de fonctionnalités de SharePoint Server en local avec la possibilité de connecter votre batterie de serveurs locale à un abonnement SharePoint Online via un abonnement hybride.|Mise à niveau, correctifs, correctifs de sécurité et toute maintenance de SharePoint Server géré localement.|
|Accès complet pour une personnalisation plus grande.|Les [offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.|
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués localement sous votre contrôle.|Microsoft 365 peut mettre à la disposition de SharePoint Online des fonctionnalités qui n’interagissent pas avec SharePoint Server en local.|
|Les partenaires peuvent aider à migrer des données vers la prochaine version de SharePoint Server (et au-delà).|Vos sites SharePoint Server n’utilisent pas automatiquement les certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) , comme indiqué dans SharePoint Online.|
|Contrôle total des conventions d’affectation de noms et des options de sauvegarde et de restauration et autres options de récupération dans SharePoint Server en local.|SharePoint Server local est sensible aux cycles de vie des produits.|

### <a name="upgrade-resources"></a>Mettre à niveau des ressources

Commencez par savoir que vous répondez aux exigences matérielles et logicielles, puis suivez les méthodes de mise à niveau prises en charge.

- *Configuration matérielle/logicielle requise pour* :

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Limites et limites logicielles pour* :

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)

- *Vue d’ensemble du processus de mise à niveau pour* :

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution hybride SharePoint entre SharePoint Online et un environnement local

Si la réponse à vos besoins de migration est quelque part entre le contrôle proposé par les batteries locales et le coût de possession inférieur offert par SharePoint Online, vous pouvez connecter les batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [En savoir plus sur les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Si vous décidez qu’une batterie de serveurs SharePoint hybride profitera à votre entreprise, familiarisez-vous avec les types existants d’hybrides et comment configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.

Vous pouvez créer un environnement de développement/test Microsoft 365, que vous pouvez configurer avec les [guides de laboratoire](m365-enterprise-test-lab-guides.md) de test. Après avoir obtenu une version d’évaluation ou acheté un abonnement Microsoft 365, vous pouvez créer les collections de sites, les sites web et les bibliothèques de documents dans SharePoint Online vers lesquels vous pouvez migrer des données. Vous pouvez migrer manuellement, à l’aide de l’API de migration, ou, si vous souhaitez migrer le contenu de Mon site vers OneDrive Entreprise, via l’Assistant hybride.

> [!NOTE]
> Pour utiliser l’option hybride, votre batterie de serveurs SharePoint Server 2010 doit d’abord être mise à niveau localement vers SharePoint Server 2013 ou 2016. SharePoint Foundation 2010 et SharePoint Foundation 2013 ne prennent pas en charge les connexions hybrides avec SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Récapitulatif des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Fin du support pour les clients et serveurs Office 2010 et l’affiche Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche illustre les différents chemins d’accès que vous pouvez prendre pour éviter les produits office 2010 client et serveur et la fin du support Windows 7, avec les chemins d’accès préférés et les options prises en charge dans Microsoft 365 Entreprise mis en surbrillance.

Vous pouvez également [télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="related-articles"></a>Articles connexes

[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007 ou 2010](upgrade-from-office-2010-servers-and-products.md)

[Vue d’ensemble du processus de mise à niveau de SharePoint 2010 vers SharePoint 2013](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[Meilleures pratiques pour la mise à niveau de SharePoint 2010 vers SharePoint 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Rechercher des fournisseurs de solutions Microsoft pour faciliter votre mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)

[Stratégie de maintenance de produit mise à jour pour SharePoint 2013](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[Stratégie de maintenance de produit mise à jour pour SharePoint Server 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
