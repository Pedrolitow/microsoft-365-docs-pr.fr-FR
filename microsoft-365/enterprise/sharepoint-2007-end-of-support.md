---
title: Feuille de route pour la fin de l’assistance pour SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1.keywords:
- CSH
ms.custom:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
- seo-marvel-apr2020
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: La prise en charge de SharePoint Server 2007 a pris fin en octobre 2017. Dans cet article, découvrez vos options de mise à niveau, de migration et de support.
ms.openlocfilehash: 889f166c7f1b6aac9110a34f2cc5ae0e069d6b7f
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67670672"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour SharePoint Server 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Le **10 octobre 2017**, Microsoft Office SharePoint Server 2007 a atteint la fin du support. Si vous n’avez pas migré de SharePoint Server 2007 vers Microsoft 365 ou une version plus récente de SharePoint Server localement, il est temps de commencer à planifier. Cet article fournit des ressources pour vous aider à migrer des données vers SharePoint Online ou à mettre à niveau votre serveur SharePoint server en local.
  
## <a name="what-does-end-of-support-mean"></a>Que signifie *la fin du support* ?

SharePoint Server, comme la plupart des produits Microsoft, a un cycle de vie de support, au cours duquel Microsoft fournit de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, et ainsi de suite. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est connue sous le nom de fin de support du produit. Après la fin du support, Microsoft ne fournit plus les éléments suivants :
  
- Support technique pour les problèmes qui peuvent se produire.
    
- Résolutions de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.
    
- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre batterie de serveurs SharePoint Server 2007 sera toujours opérationnelle après le 10 octobre 2017, mais aucune autre mise à jour, correctifs ou correctifs ne sera publié pour le produit, y compris les correctifs/correctifs de sécurité. Support Microsoft a entièrement déplacé ses efforts de support vers des versions plus récentes du produit. Étant donné que votre installation n’est plus prise en charge ou mise à jour corrective, vous devez mettre à niveau le produit ou migrer des données importantes.
  
> [!TIP]
> Si vous n’avez pas encore planifié la mise à niveau ou la migration, consultez : [Options de migration SharePoint 2007 à prendre en compte](sharepoint-2007-migration-options.md) pour obtenir des exemples d’emplacement de démarrage. Vous pouvez également rechercher des [partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) qui peuvent vous aider dans la mise à niveau ou la migration de Microsoft 365 (ou les deux).
  
Pour plus d’informations sur les serveurs Office 2007 et la fin du support, consultez [Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Votre premier arrêt doit être le [site product lifecycle](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007). Si vous avez un produit Microsoft local qui vieillit, vérifiez sa date de fin de support afin d’avoir un an ou plus pour planifier une mise à niveau ou une migration. Lorsque vous choisissez l’étape suivante, tenez compte des fonctionnalités de produit qui seraient suffisantes, meilleures et optimales. Voici un exemple : 
  
|**Good**|**Mieux**|**Idéale**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Environnement hybride Microsoft Office SharePoint Online  <br/> |SharePoint Server 2016  <br/> |
| | |Environnement hybride Microsoft Office SharePoint Online  <br/> |
   
Si vous choisissez une option « suffisamment bonne », vous devrez bientôt commencer à planifier une autre mise à niveau une fois la migration de SharePoint Server 2007 terminée. 

>[!NOTE] 
>Les dates de fin de support sont susceptibles d’être modifiées. Consultez le [site Product Lifecycle](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>Que faire ensuite ?

SharePoint Server peut être installé localement sur vos propres serveurs. Vous pouvez également utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft 365. Voici les différents choix possibles :
  
- Migrer vers SharePoint Online.
    
- Mettez à niveau SharePoint Server en local.
    
- Effectuez les deux opérations ci-dessus.
    
- Implémentez une solution [hybride SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) .
    
Tenez compte des coûts cachés associés à la maintenance d’une batterie de serveurs, à la maintenance ou à la migration des personnalisations et à la mise à niveau du matériel dont SharePoint Server a besoin. Le fait d’avoir une batterie de serveurs SharePoint Server locale est gratifiant si nécessaire. Toutefois, si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités sans personnalisation intensive, vous pouvez tirer parti de la migration vers SharePoint Online.
  
> [!IMPORTANT]
> Il existe une autre option si le contenu dans SharePoint 2007 est rarement utilisé. Certains administrateurs SharePoint choisissent de créer un abonnement Microsoft 365, de configurer un nouveau site SharePoint Online, puis de supprimer sharePoint 2007 proprement, en prenant uniquement les documents essentiels aux nouveaux sites SharePoint Online. Les données peuvent ensuite être vidées du site SharePoint 2007 dans des archives. Réfléchissez à la façon dont vos utilisateurs travaillent avec les données de votre installation SharePoint 2007. Il peut y avoir des façons créatives de gérer vos besoins.
  
|**SharePoint Online (SPO)**|**SharePoint Server local**|
|:-----|:-----|
|Coût élevé dans le temps (plan/ exécution/vérification)  <br/> |Coût élevé dans le temps (plan/ exécution/vérification)  <br/> |
|Réduction du coût des fonds (aucun achat de matériel)  <br/> |Coût plus élevé des fonds (matériel + développeurs/administrateurs)  <br/> |
|Coût unique de la migration  <br/> |Coût unique répété par migration future  <br/> |
|Faible coût total de possession/maintenance  <br/> |Coût total élevé de possession/maintenance  <br/> |
   
Lorsque vous migrez vers Microsoft 365, le déplacement à usage unique aura un coût plus élevé à l’avance, tandis que vous organisez les données et décidez ce qu’il faut prendre dans le cloud et ce qu’il faut laisser derrière vous. Mais les mises à niveau futures seront automatiques et vous n’aurez plus besoin de gérer les mises à jour matérielles et logicielles. En outre, le temps d’attente de votre batterie de serveurs sera soutenu par un contrat de niveau de service ([SLA](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online dispose de toutes les fonctionnalités dont vous avez besoin. Consultez [les descriptions des services Microsoft 365 et Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
Vous ne pouvez pas migrer directement de SharePoint 2007 vers SharePoint Online. Votre déplacement vers SharePoint Online est effectué manuellement. Si vous effectuez une mise à niveau vers SharePoint Server 2013 ou SharePoint Server 2016, vous pouvez utiliser l’API de migration SharePoint (pour migrer des informations vers OneDrive Entreprise, par exemple).
  
|**Professionnel en ligne**|**Con en ligne**|
|:-----|:-----|
|Microsoft fournit le matériel SPO et toute l’administration matérielle.  <br/> |Les fonctionnalités disponibles peuvent différer entre SharePoint Server local et SPO.  <br/> |
|Vous êtes l’administrateur SharePoint ou l’administrateur général de votre abonnement et pouvez affecter des administrateurs à des sites SPO.  <br/> |Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server en local n’existent pas ou ne sont pas nécessairement incluses dans le rôle Administrateur SharePoint dans Microsoft 365.  <br/> |
|Microsoft applique des correctifs, des correctifs et des mises à jour au matériel et aux logiciels sous-jacents. <br/> |Étant donné qu’il n’existe aucun accès au système de fichiers sous-jacent dans le service, la personnalisation est limitée.  <br/> |
|Microsoft publie des [contrats de niveau de service](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) et se déplace rapidement pour résoudre les incidents au niveau du service. <br/> |Les options de sauvegarde et de restauration et autres options de récupération sont automatisées par le service dans SharePoint Online. Les sauvegardes sont remplacées si non utilisées. <br/> |
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués de façon continue dans le service par Microsoft. <br/> |Les modifications apportées à l’interface utilisateur et aux autres fonctionnalités SharePoint sont installées par le service et doivent peut-être être activées ou désactivées. <br/> |
|Microsoft 365 répond à de nombreuses normes du secteur : [offres de conformité Microsoft](/compliance/regulatory/offering-home).  <br/> |[L’assistance FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de route de [contenu de migration SharePoint Online et OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Support Microsoft ingénieurs et les employés du centre de données n’auront pas d’accès administrateur illimité à votre abonnement. <br/> |Il peut y avoir des coûts supplémentaires si le matériel doit être mis à niveau pour prendre en charge la version la plus récente de SharePoint, ou si une batterie de serveurs secondaire est requise pour la mise à niveau.  <br/> |
|Les partenaires peuvent vous aider dans la tâche unique de migration de vos données vers SharePoint Online.  <br/> ||
|Les produits en ligne sont mis à jour automatiquement. Bien que les fonctionnalités puissent être dépréciés, il n’existe pas de véritable fin de prise en charge. <br/> ||
   
Si vous avez décidé de créer un site Microsoft 365 et que vous y migrez manuellement des données en fonction des besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe aucun moyen d’ignorer les versions dans les mises à niveau SharePoint. Les mises à niveau s’exécutent en série :
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Passer de SharePoint 2007 à SharePoint Server 2016 implique un investissement important de temps et implique des coûts en matériel (les serveurs SQL doivent également être mis à niveau), les logiciels et l’administration. Les personnalisations doivent être mises à niveau ou abandonnées.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 en fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour télécharger et charger à nouveau du contenu, par exemple). Mais méfiez-vous de certains des pièges des déplacements manuels, tels que les déplacements de documents remplaçant le compte modifié par l’alias du compte effectuant le déplacement manuel. Prenez également en compte le travail qui doit être effectué à l’avance, comme la recréer des sites, des sous-sites, des autorisations et des structures de liste. Réfléchissez à l’avance aux données que vous pouvez déplacer dans le stockage ou supprimer pour réduire l’impact de la migration.
  
Il est important de nettoyer votre environnement avant de procéder à la mise à niveau. Soyez certain que votre batterie de serveurs existante est fonctionnelle avant la mise à niveau, et certainement avant la mise hors service !
  
N’oubliez pas de consulter les *chemins de mise à niveau pris en charge et non pris en charge* : 
  
- 
  [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Si vous avez des personnalisations, il est essentiel d’avoir un plan pour chaque étape du chemin de migration : 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Professionnel local**|**Local con**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, du matériel serveur vers le haut.  <br/> |Tous les arrêts et correctifs sont de la responsabilité de votre entreprise (vous pouvez engager des Support Microsoft payants si votre produit n’est pas au-delà de la fin du support).  <br/> |
|Ensemble complet de fonctionnalités de SharePoint Server en local avec la possibilité de connecter votre batterie de serveurs locale à un abonnement SharePoint Online via un abonnement hybride.  <br/> |Mise à niveau, correctifs, correctifs de sécurité et toute maintenance de SharePoint Server géré localement.  <br/> |
|Accès complet pour une personnalisation plus grande.  <br/> |Les [offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur sont effectués localement (sous votre contrôle).  <br/> |Microsoft 365 peut mettre à la disposition de SharePoint Online des fonctionnalités qui n’interagissent pas avec SharePoint Server en local.  <br/> |
|Les partenaires peuvent vous aider à migrer des données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utilisent pas automatiquement des certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) , comme indiqué dans SharePoint Online.  <br/> |
|Contrôle total des conventions de nommage, de la sauvegarde et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.  <br/> |SharePoint Server local est sensible aux cycles de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau des ressources

Assurez-vous que votre environnement répond aux exigences matérielles et logicielles, puis suivez les méthodes de mise à niveau prises en charge.
  
- **Configuration matérielle/logicielle requise pour** : 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Limites et limites logicielles pour** : 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)
    
- **Vue d’ensemble du processus de mise à niveau pour** : 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution hybride SharePoint entre SharePoint Online et un environnement local

Si la réponse à vos besoins de migration est quelque part entre l’autocontrait offert par l’environnement local et le coût de possession inférieur offert par SharePoint Online, vous pouvez connecter les batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [Découvrez les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Si vous décidez qu’une batterie de serveurs SharePoint hybride profitera à votre entreprise, familiarisez-vous avec les types existants d’hybrides et comment configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.
  
| Option | Description |
|:-----|:-----|
[Offres pour la conformité Microsoft](/compliance/regulatory/offering-home)  <br/> |[L’assistance FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la [feuille de route de contenu de migration SharePoint Online et OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Support Microsoft les ingénieurs et les employés du centre de données n’ont pas d’accès administrateur illimité à votre abonnement.<br/> |Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version la plus récente de SharePoint, ou si une batterie de serveurs secondaire est requise pour la mise à niveau.  <br/> |
|Les partenaires peuvent vous aider dans la tâche unique de migration de vos données vers SharePoint Online.  <br/> ||
|Les produits en ligne sont mis à jour automatiquement sur l’ensemble du service. Bien que les fonctionnalités puissent être dépréciés, il n’y a pas de véritable fin de prise en charge.<br/> ||
   
Si vous avez décidé de créer un site Microsoft 365 et que vous y migrez manuellement des données en fonction des besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe aucun moyen d’ignorer les versions dans les mises à niveau SharePoint. Les mises à niveau s’exécutent en série :
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Passer de SharePoint 2007 à SharePoint Server 2016 implique un investissement important de temps et implique des coûts pour le matériel (les serveurs SQL doivent également être mis à niveau), les logiciels et l’administration. Les personnalisations doivent être mises à niveau ou abandonnées.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 en fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour télécharger et charger à nouveau du contenu, par exemple). Mais méfiez-vous des pièges potentiels des déplacements manuels, tels que les déplacements de documents remplaçant le compte modifié par l’alias du compte effectuant le déplacement manuel, et le travail qui doit être effectué à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de liste. Réfléchissez aux données que vous pouvez déplacer dans le stockage ou supprimer pour réduire l’impact de la migration.
  
Nettoyez votre environnement avant la mise à niveau. Soyez certain que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau et certainement avant de mettre hors service ! 
  
N’oubliez pas de consulter les *chemins de mise à niveau pris en charge et non pris en charge* : 
  
- 
  [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Si vous avez *des personnalisations*, il est essentiel que vous ayez un plan de mise à niveau pour chaque étape du chemin de migration : 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Professionnel local**|**Con local**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, du matériel serveur vers le haut.  <br/> |Tous les arrêts et correctifs sont de la responsabilité de votre entreprise. (Vous pouvez engager des Support Microsoft payants si votre produit n’a pas dépassé la fin du support.)  <br/> |
|Ensemble complet de fonctionnalités de SharePoint Server en local avec la possibilité de connecter votre batterie de serveurs locale à un abonnement SharePoint Online via un abonnement hybride.  <br/> |Mise à niveau, correctifs, correctifs de sécurité et toute maintenance de SharePoint Server géré localement.  <br/> |
|Accès complet pour une personnalisation plus grande.  <br/> |Les [offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués localement sous votre contrôle.  <br/> |Microsoft 365 peut mettre à la disposition de SharePoint Online des fonctionnalités qui n’interagissent pas avec SharePoint Server en local  <br/> |
|Les partenaires peuvent aider à migrer des données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utilisent pas automatiquement les certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) , comme indiqué dans SharePoint Online.  <br/> |
|Contrôle total des conventions de nommage, de la sauvegarde et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.  <br/> |SharePoint Server local est sensible aux cycles de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau des ressources

Assurez-vous que votre environnement répond aux exigences matérielles et logicielles. Suivez ensuite les méthodes de mise à niveau prises en charge.
  
- **Configuration matérielle/logicielle requise pour :** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Limites et limites logicielles pour :** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)
    
- **Vue d’ensemble du processus de mise à niveau pour :** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution hybride SharePoint entre SharePoint Online et un environnement local

Si la réponse à vos besoins de migration est quelque part entre l’autocontrait offert par l’environnement local et le coût de possession inférieur offert par SharePoint Online, vous pouvez connecter les batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [En savoir plus sur les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si vous décidez qu’une batterie de serveurs SharePoint hybride profitera à votre entreprise, familiarisez-vous avec les types existants d’hybrides et comment configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.
  
Une bonne façon de voir comment cela fonctionne consiste à créer un environnement de développement/test Microsoft 365, que vous pouvez configurer avec les [guides de laboratoire](m365-enterprise-test-lab-guides.md) de test. Après avoir obtenu une version d’évaluation ou acheté un abonnement Microsoft 365, vous pouvez créer les collections de sites, les sites web et les bibliothèques de documents dans SharePoint Online vers lesquels vous pouvez migrer des données. Vous pouvez migrer manuellement, à l’aide de l’API de migration, ou, si vous souhaitez migrer le contenu de Mon site vers OneDrive Entreprise, via l’Assistant hybride.
  
> [!NOTE]
> N’oubliez pas que pour utiliser l’option hybride, votre batterie de serveurs SharePoint 2007 doit être mise à niveau localement vers SharePoint Server 2013 ou SharePoint Server 2016.
  
## <a name="related-topics"></a>Voir aussi

[Résoudre les problèmes et reprendre la mise à niveau (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[Résoudre les problèmes de mise à niveau (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[Rechercher des partenaires Microsoft pour obtenir de l’aide sur la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
