---
title: Feuille de route pour la fin de l’assistance pour SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
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
ms.service: o365-solutions
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
description: La prise en charge SharePoint Server 2007 a pris fin en octobre 2017. Dans cet article, découvrez les options de mise à niveau, de migration et de support.
ms.openlocfilehash: d09e0cf58ef814a76cdac28f6029189eaf655efc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60197268"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour SharePoint Server 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Le **10 octobre 2017,** Microsoft Office SharePoint Server 2007 a atteint la fin du support. Si vous n’avez pas migré de SharePoint Server 2007 vers Microsoft 365 ou une version plus récente de SharePoint Server en local, il est temps de commencer la planification. Cet article fournit des ressources pour vous aider à migrer des données vers SharePoint Online ou à mettre à niveau SharePoint Server local.
  
## <a name="what-does-end-of-support-mean"></a>*Qu’est-ce que la fin du support* signifie ?

SharePoint Le serveur, comme la plupart des produits Microsoft, a un cycle de vie de support, au cours duquel Microsoft fournit de nouvelles fonctionnalités, des correctifs de bogue, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est appelée fin de support du produit. Après la fin du support, Microsoft ne fournit plus :
  
- Support technique pour les problèmes qui peuvent se produire.
    
- Résolutions de bogues pour les problèmes qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.
    
- Correctifs de sécurité pour les vulnérabilités qui peuvent rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre batterie de serveurs SharePoint Server 2007 sera toujours opérationnelle après le 10 octobre 2017, mais aucune mise à jour, correctifs ou correctifs supplémentaires ne sera publié pour le produit, y compris les correctifs/correctifs de sécurité. Le Support Microsoft a entièrement déplacé ses efforts de support vers des versions plus récentes du produit. Étant donné que votre installation n’est plus prise en charge ou corrigé, vous devez mettre à niveau le produit ou migrer des données importantes.
  
> [!TIP]
> Si vous n’avez pas encore planifié la mise à niveau ou la migration, voir : [SharePoint 2007 migration options to consider](sharepoint-2007-migration-options.md) for some examples of where to begin. Vous pouvez également rechercher des [partenaires Microsoft qui](https://go.microsoft.com/fwlink/?linkid=841249) peuvent vous aider avec la mise à niveau ou Microsoft 365 migration (ou les deux).
  
Pour plus d’informations sur Office serveurs 2007 et la fin de la prise en charge, voir Ressources pour vous aider à mettre à niveau des serveurs et [des clients Office 2007.](upgrade-from-office-2007-servers-and-products.md)
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Votre premier arrêt doit être le [site cycle de vie du produit.](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007) Si vous avez un produit Microsoft local qui est en cours d’âge, vérifiez sa date de fin de support pour avoir un an ou deux pour planifier une mise à niveau ou une migration. Lorsque vous choisissez l’étape suivante, réfléchissez aux fonctionnalités de produit qui seraient suffisamment bonnes, meilleures et meilleures. Voici un exemple : 
  
|**Good**|**Meilleure**|**Idéale**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Environnement hybride Microsoft Office SharePoint Online  <br/> |SharePoint Server 2016  <br/> |
| | |Environnement hybride Microsoft Office SharePoint Online  <br/> |
   
Si vous choisissez une option « suffisamment bonne », vous devrez bientôt commencer la planification d’une autre mise à niveau une fois la migration à partir de SharePoint Server 2007 terminée. 

>[!NOTE] 
>Les dates de fin de prise en charge sont sujettes à modification. Vérifiez le [site Cycle de vie du produit.](https://support.microsoft.com/lifecycle)
  
## <a name="where-can-i-go-next"></a>Que faire ensuite ?

SharePoint Le serveur peut être installé en local sur vos propres serveurs. Vous pouvez également utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft 365. Voici les différents choix possibles :
  
- Migrez vers SharePoint Online.
    
- Mettre à SharePoint serveur local.
    
- Faites les deux choses ci-dessus.
    
- Implémenter [SharePoint solution hybride](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) hybride.
    
Tenez compte des coûts masqués associés à la maintenance d’une batterie de serveurs, à la maintenance ou à la migration des personnalisations et à la mise à niveau du matériel dont SharePoint Server a besoin. Disposer d’une batterie de serveurs SharePoint serveur local est une récompense si nécessaire. Toutefois, si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités sans personnalisation importante, vous pouvez bénéficier de la migration vers SharePoint Online.
  
> [!IMPORTANT]
> Il existe une autre option si le contenu de SharePoint 2007 est rarement utilisé. Certains administrateurs SharePoint choisissent de créer un abonnement Microsoft 365, de configurer un nouveau site SharePoint Online, puis de supprimer proprement SharePoint 2007, en prenant uniquement les documents essentiels vers les nouveaux sites SharePoint Online. Les données peuvent ensuite être drainées du site SharePoint 2007 dans des archives. Réfléchissez à la façon dont vos utilisateurs utilisent les données de votre installation SharePoint 2007. Il peut y avoir des moyens créatifs de gérer vos besoins.
  
|**SharePoint Online (SPO)**|**SharePoint Serveur local**|
|:-----|:-----|
|Coût élevé en temps (plan/ exécution/vérification)  <br/> |Coût élevé en temps (plan/ exécution/vérification)  <br/> |
|Moindre coût en fonds (aucun achat de matériel)  <br/> |Coût plus élevé des fonds (matériel + devs/administrateurs)  <br/> |
|Coût one-time lors de la migration  <br/> |Coût à durée de vie répété par migration future  <br/> |
|Faible coût total de possession/maintenance  <br/> |Coût total élevé de possession/maintenance  <br/> |
   
Lorsque vous migrez vers Microsoft 365, le déplacement à une seule heure aura un coût plus élevé à l’avance, pendant que vous organisez les données et décidez de ce qu’il faut faire dans le cloud et de ce qu’il faut laisser. Toutefois, les mises à niveau futures seront automatiques et vous n’aurez plus besoin de gérer les mises à jour matérielles et logicielles. En outre, la durée de vie de votre batterie de serveurs est également fonction d’un contrat de niveau de service[(SLA)](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online dispose de toutes les fonctionnalités dont vous avez besoin. Voir [Microsoft 365 et les descriptions Office 365 service.](/office365/servicedescriptions/office-365-service-descriptions-technet-library)
  
Vous ne pouvez pas migrer directement de SharePoint 2007 vers SharePoint Online. Votre déplacement vers SharePoint Online serait effectué manuellement. Si vous faites une mise à niveau vers SharePoint Server 2013 ou SharePoint Server 2016, vous pouvez utiliser l’API de migration SharePoint (pour migrer des informations vers OneDrive Entreprise, par exemple).
  
|**Professionnel en ligne**|**Con en ligne**|
|:-----|:-----|
|Microsoft fournit le matériel SPO et l’administration de tout le matériel.  <br/> |Les fonctionnalités disponibles peuvent différer entre SharePoint Server local et SPO.  <br/> |
|Vous êtes l’administrateur SharePoint ou l’administrateur général de votre abonnement et pouvez affecter des administrateurs à des sites SPO.  <br/> |Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server local n’existent pas ou ne sont pas nécessairement incluses dans le rôle administrateur SharePoint dans Microsoft 365.  <br/> |
|Microsoft applique des correctifs, des correctifs et des mises à jour au matériel et aux logiciels sous-jacents. <br/> |Étant donné qu’il n’y a pas d’accès au système de fichiers sous-jacent dans le service, la personnalisation est limitée.  <br/> |
|Microsoft publie des [contrats de niveau de](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) service et se déplace rapidement pour résoudre les incidents au niveau du service. <br/> |Les options de sauvegarde et de restauration et d’autres options de récupération sont automatisées par le service dans SharePoint Online. Les sauvegardes sont écrasées si elles ne sont pas utilisées. <br/> |
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués régulièrement dans le service par Microsoft. <br/> |Les modifications apportées à l’interface utilisateur et aux autres fonctionnalités SharePoint sont installées par le service et peuvent avoir besoin d’être togged ou off. <br/> |
|Microsoft 365 répond à de nombreuses normes du secteur : [offres de conformité Microsoft](/compliance/regulatory/offering-home).  <br/> |[FastTrack’aide](https://www.microsoft.com/fasttrack/microsoft-365) à la migration est limitée.  <br/> La majeure partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans SharePoint Online et OneDrive feuille de route [du contenu de migration.](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets)  <br/> |
|Les ingénieurs du support Microsoft et les employés du centre de données n’auront pas un accès administrateur illimité à votre abonnement. <br/> |Il peut y avoir des coûts supplémentaires si le matériel doit être mis à niveau pour prendre en charge la nouvelle version de SharePoint, ou si une batterie secondaire est requise pour la mise à niveau.  <br/> |
|Les partenaires peuvent vous aider à migrer vos données vers SharePoint Online.  <br/> ||
|Les produits en ligne sont mis à jour automatiquement. Bien que les fonctionnalités peuvent se déprécier, il n’existe pas de véritable fin de prise en charge. <br/> ||
   
Si vous avez décidé de créer un site Microsoft 365 et migrez manuellement les données vers ce site selon vos besoins, vérifiez vos [options Microsoft 365 de migration.](https://www.microsoft.com/microsoft-365/)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à SharePoint serveur local

Il n’existe aucun moyen d’ignorer les versions SharePoint mises à niveau. Les mises à niveau sont mises à niveau en série :
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Passer de SharePoint 2007 à SharePoint Server 2016 représente un investissement important en temps et implique des coûts en matériel (les serveurs SQL doivent également être mis à niveau), les logiciels et l’administration. Les personnalisations doivent être mises à niveau ou abandonnées.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 en fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle du contenu (pour télécharger et télécharger à nouveau du contenu, par exemple). Mais attention à certains des pièges des déplacements manuels, tels que les déplacements de documents remplaçant le compte de dernière modification par l’alias du compte qui a fait le déplacement manuel. Prenez également en compte le travail à faire à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de liste. Envisagez à l’avance les données que vous pouvez déplacer dans le stockage ou la suppression pour réduire l’impact de la migration.
  
Il est important de nettoyer votre environnement avant de mettre à niveau. Veillez à ce que votre batterie de serveurs existante soit fonctionnelle avant la mise à niveau et avant de la désaffecter .
  
N’oubliez pas de passer en revue les *chemins de* mise à niveau pris en charge et non pris en charge : 
  
- 
  [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Si vous avez des personnalisations, il est essentiel d’avoir un plan pour chaque étape du chemin de migration : 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Professionnel local**|**Con local**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de SharePoint, à partir du matériel du serveur.  <br/> |Toutes les interruptions et correctifs sont la responsabilité de votre entreprise (vous pouvez engager le Support Microsoft payant si votre produit n’a pas fini de prendre en charge).  <br/> |
|Ensemble complet de fonctionnalités SharePoint Server local avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un abonnement hybride.  <br/> |Mise à niveau, correctifs, correctifs de sécurité et maintenance SharePoint Server géré en local.  <br/> |
|Accès complet pour une personnalisation plus importante.  <br/> |[Les offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur sont effectués sur votre site (sous votre contrôle).  <br/> |Microsoft 365 pouvez mettre à la disposition de SharePoint Online qui n’interaront pas avec SharePoint Server local.  <br/> |
|Les partenaires peuvent vous aider à migrer des données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) comme le permet SharePoint Online.  <br/> |
|Contrôle total des conventions d’attribution de noms, de la back up et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server local.  <br/> |SharePoint Le serveur local est sensible aux cycles de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Assurez-vous que votre environnement répond à la configuration matérielle et logicielle requise, puis suivez les méthodes de mise à niveau prise en charge.
  
- **Configuration matérielle/logicielle requise pour**: 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0)  |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Limites et frontières logicielles pour**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits)  |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Vue d’ensemble du processus de mise à niveau pour**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14))  |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)  |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et en local

Si la réponse à vos besoins de migration se situe quelque part entre le contrôle autonome proposé en local et le coût de possession inférieur proposé par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [En savoir plus sur SharePoint solutions hybrides.](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si vous décidez qu’une batterie de serveurs SharePoint hybride bénéficiera à votre entreprise, familiarisez-vous avec les types d’hybrides existants et comment configurer la connexion entre votre batterie de serveurs SharePoint sur site et votre abonnement Microsoft 365.
  
| Option | Description |
|:-----|:-----|
[Offres pour la conformité Microsoft](/compliance/regulatory/offering-home)  <br/> |[FastTrack’aide](https://www.microsoft.com/fasttrack/microsoft-365) à la migration est limitée.  <br/> La majeure partie de la mise à niveau sera manuelle, ou via l’API de migration SPO décrite dans la feuille de route de contenu de migration SharePoint Online et [OneDrive migration.](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets)  <br/> |
|Les ingénieurs du support Microsoft et les employés du centre de données n’ont pas un accès administrateur illimité à votre abonnement.<br/> |Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la nouvelle version de SharePoint ou si une batterie secondaire est requise pour la mise à niveau.  <br/> |
|Les partenaires peuvent vous aider à migrer vos données vers SharePoint Online.  <br/> ||
|Les produits en ligne sont mis à jour automatiquement dans l’ensemble du service. Bien que les fonctionnalités peuvent être dépréciables, il n’existe pas de véritable fin de prise en charge.<br/> ||
   
Si vous avez décidé de créer un site Microsoft 365 et migrez manuellement les données vers ce site si nécessaire, vérifiez vos [options Microsoft 365 de migration.](https://www.microsoft.com/microsoft-365/)
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à SharePoint serveur local

Il n’existe aucun moyen d’ignorer les versions SharePoint mises à niveau. Les mises à niveau sont mises à niveau en série :
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Passer de SharePoint 2007 à SharePoint Server 2016 implique un investissement important en temps et implique des coûts pour le matériel (les serveurs SQL doivent également être mis à niveau), les logiciels et l’administration. Les personnalisations doivent être mises à niveau ou abandonnées.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 en fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur un nouveau matériel (de sorte que les batteries de serveurs distinctes s’exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle du contenu (pour télécharger et télécharger à nouveau du contenu, par exemple). Mais attention aux risques potentiels de déplacements manuels, tels que les déplacements de documents remplaçant le compte de dernière modification par l’alias du compte qui a effectué le déplacement manuel, et le travail à faire à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de listes. Réfléchissez aux données que vous pouvez déplacer dans le stockage ou la suppression pour réduire l’impact de la migration.
  
Nettoyez votre environnement avant la mise à niveau. Veillez à ce que votre batterie de serveurs existante soit fonctionnelle avant de mettre à niveau et avant de la désaffecter ! 
  
N’oubliez pas de passer en revue les *chemins de* mise à niveau pris en charge et non pris en charge : 
  
- 
  [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Si vous avez *des personnalisations,* il est essentiel de planifier votre mise à niveau pour chaque étape du chemin de migration : 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Local Pro**|**Con local**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de SharePoint, à partir du matériel du serveur.  <br/> |Toutes les interruptions et correctifs sont la responsabilité de votre entreprise. (Vous pouvez engager le Support Microsoft payant si votre produit n’a pas passé la fin du support.)  <br/> |
|Ensemble complet de fonctionnalités SharePoint Server local avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un abonnement hybride.  <br/> |Mise à niveau, correctifs, correctifs de sécurité et maintenance SharePoint Server géré en local.  <br/> |
|Accès complet pour une personnalisation plus importante.  <br/> |[Les offres de conformité Microsoft](/compliance/regulatory/offering-home) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et l’optimisation des performances du serveur sont effectués sur votre site sous votre contrôle.  <br/> |Microsoft 365 mettre à la disposition de SharePoint Online qui ne fonctionnent pas avec SharePoint Server local  <br/> |
|Les partenaires peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) comme le permet SharePoint Online.  <br/> |
|Contrôle total des conventions d’attribution de noms, de la back up et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server local.  <br/> |SharePoint Le serveur local est sensible aux cycles de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Assurez-vous que votre environnement répond à la configuration matérielle et logicielle requise. Suivez ensuite les méthodes de mise à niveau prise en charge.
  
- **Configuration matérielle/logicielle requise pour :** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0)  |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Limites et frontières logicielles pour :** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14))  |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits)  |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Vue d’ensemble du processus de mise à niveau pour :** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12))  |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14))  |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)  |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et en local

Si la réponse à vos besoins de migration se situe quelque part entre le contrôle autonome proposé en local et le coût de possession inférieur proposé par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [En savoir plus sur SharePoint solutions hybrides](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si vous décidez qu’une batterie de serveurs SharePoint hybride bénéficiera à votre entreprise, familiarisez-vous avec les types d’hybrides existants et comment configurer la connexion entre votre batterie de serveurs SharePoint sur site et votre abonnement Microsoft 365.
  
Un bon moyen de voir comment cela fonctionne consiste à créer un environnement de Microsoft 365/test, que vous pouvez configurer à l’aide des Guides de [laboratoire de test.](m365-enterprise-test-lab-guides.md) Après avoir acheté un abonnement d’essai ou Microsoft 365, vous pouvez créer les collections de sites, les sites web et les bibliothèques de documents dans SharePoint Online vers lesquels vous pouvez migrer des données. Vous pouvez migrer manuellement, à l’aide de l’API de migration, ou, si vous souhaitez migrer le contenu du Site Mon site vers OneDrive Entreprise, via l’Assistant hybride.
  
> [!NOTE]
> N’oubliez pas que pour utiliser l’option hybride, votre batterie de serveurs SharePoint 2007 devra être mise à niveau, en local, vers SharePoint Server 2013 ou SharePoint Server 2016.
  
## <a name="related-topics"></a>Rubriques connexes

[Résoudre les problèmes et reprendre la mise à niveau (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[Résoudre les problèmes de mise à niveau (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[Rechercher des partenaires Microsoft pour vous aider avec la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressources pour vous aider à mettre à niveau Office serveurs et clients 2007](upgrade-from-office-2007-servers-and-products.md)
