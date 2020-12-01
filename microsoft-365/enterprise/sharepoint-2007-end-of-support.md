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
localization_priority: Normal
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
description: La prise en charge de SharePoint Server 2007 s’est terminée en octobre 2017. Dans cet article, Découvrez les options de mise à niveau, de migration et de support.
ms.openlocfilehash: aa09669d1c7b90f70e6c136a85d06ef2a516e4b5
ms.sourcegitcommit: d3ca8021f7da00a474ac14aac5f1358204a848f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "49519633"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour SharePoint Server 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Le **10 octobre 2017**, Microsoft Office SharePoint Server 2007 est parvenu à la fin du support. Si vous n’avez pas migré de SharePoint Server 2007 vers Microsoft 365 ou une version plus récente de SharePoint Server en local, il est maintenant temps de commencer la planification. Cet article fournit des ressources pour vous aider à migrer des données vers SharePoint Online ou à mettre à niveau votre serveur SharePoint Server local.
  
## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la *fin de la prise en charge* ?

SharePoint Server, comme la plupart des produits Microsoft, a un cycle de vie de la prise en charge, pendant lequel Microsoft fournit de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans après la publication initiale du produit. La fin de ce cycle de vie est appelée fin de la prise en charge du produit. Après la fin de l’assistance, Microsoft ne fournit plus :
  
- Support technique pour les problèmes susceptibles de se produire.
    
- Correctifs de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur.
    
- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre batterie de serveurs SharePoint Server 2007 sera toujours opérationnelle après le 10 octobre 2017, mais aucune mise à jour, correctif ou correctif supplémentaire ne sera publié pour le produit, y compris les correctifs de sécurité/correctifs. Le support Microsoft a entièrement déplacé ses efforts de prise en charge vers des versions plus récentes du produit. Étant donné que votre installation n’est plus prise en charge ou corrigée, vous devez mettre à niveau le produit ou migrer des données importantes.
  
> [!TIP]
> Si vous n’avez pas encore planifié de mise à niveau ou de migration, voir : [options de migration de SharePoint 2007 pour](sharepoint-2007-migration-options.md) obtenir des exemples d’emplacements de départ. Vous pouvez également rechercher des [partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) qui peuvent vous aider à effectuer une mise à niveau ou une migration Microsoft 365 (ou les deux).
  
Pour plus d’informations sur les serveurs Office 2007 et la fin de la prise en charge, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Votre première étape doit être le [site du cycle de vie du produit](https://go.microsoft.com/fwlink/?linkid=843148). Si vous disposez d’un produit Microsoft sur site qui est âgé, vérifiez sa fin de prise en charge afin de planifier une mise à niveau ou une migration. Lorsque vous choisissez l’étape suivante, vous devez tenir compte des fonctionnalités du produit qui seraient suffisantes, meilleures et les plus efficaces. Voici un exemple : 
  
|**Good**|**Parfaite**|**Idéale**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||Environnement hybride SharePoint  <br/> |SharePoint Server 2016  <br/> |
| | |Environnement hybride SharePoint  <br/> |
   
Si vous choisissez une option « suffisante », vous devrez bientôt commencer à planifier une autre mise à niveau après la migration de SharePoint Server 2007. 

>[!NOTE] 
>Les dates de fin de prise en charge peuvent faire l’objet de modifications. Vérifiez le [site du cycle de vie du produit](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>Que faire ensuite ?

SharePoint Server peut être installé en local sur vos propres serveurs. Ou vous pouvez utiliser SharePoint Online, qui est un service en ligne qui fait partie de Microsoft 365. Voici les différents choix possibles :
  
- Migrer vers SharePoint Online.
    
- Mettre à niveau SharePoint Server en local.
    
- Effectuez les deux opérations ci-dessus.
    
- Implémentez une solution [SharePoint hybride](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) .
    
Tenez compte des coûts cachés associés à la maintenance d’une batterie de serveurs, à la maintenance ou à la migration des personnalisations, ainsi qu’à la mise à niveau du matériel dont SharePoint Server a besoin. Disposer d’une batterie de serveurs SharePoint Server locale est gratifiant si nécessaire. Toutefois, si vous exécutez votre batterie de serveurs sur des serveurs SharePoint hérités sans personnalisation élevée, vous pouvez tirer parti de la migration vers SharePoint Online.
  
> [!IMPORTANT]
> Il existe une autre option si le contenu dans SharePoint 2007 n’est pas fréquemment utilisé. Certains administrateurs SharePoint choisissent de créer un abonnement Microsoft 365, de configurer un nouveau site SharePoint Online, puis de se découper de SharePoint 2007 proprement, en prenant uniquement les documents essentiels sur les sites SharePoint Online récents. Les données peuvent ensuite être vidées du site SharePoint 2007 en archives. Réfléchissez à la façon dont vos utilisateurs travaillent avec les données de votre installation SharePoint 2007. Il peut y avoir des moyens créatifs de gérer vos besoins.
  
|**SharePoint Online (SPO)**|**SharePoint Server en local**|
|:-----|:-----|
|Coût élevé dans le temps (planification/exécution/vérification)  <br/> |Coût élevé dans le temps (planification/exécution/vérification)  <br/> |
|Coût réduit des fonds (sans achat de matériel)  <br/> |Coût plus élevé des fonds (matériel + développeurs/administrateurs)  <br/> |
|Coût unique lors de la migration  <br/> |Coût unique répété par migration future  <br/> |
|Faible coût total de possession/maintenance  <br/> |Coût total de propriété/maintenance élevé  <br/> |
   
Lorsque vous procédez à une migration vers Microsoft 365, le déplacement unique aura un coût plus lourd, tout en organisant les données et en décidant des opérations à effectuer sur le Cloud et les éléments à laisser derrière. Toutefois, les mises à jour futures seront automatiques, et vous n’aurez plus besoin de gérer les mises à jour matérielles et logicielles. De plus, le temps de mise à niveau de votre batterie de serveurs sera sauvegardé par un contrat de niveau de service ([SLA](https://go.microsoft.com/fwlink/?linkid=843153)) Microsoft.
  
### <a name="migrate-to-sharepoint-online"></a>Migrer vers SharePoint Online

Assurez-vous que SharePoint Online dispose de toutes les fonctionnalités dont vous avez besoin. Consultez [les descriptions de service Microsoft 365 et Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
Vous ne pouvez pas migrer directement de SharePoint 2007 vers SharePoint Online. Votre déplacement vers SharePoint Online s’effectuera manuellement. Si vous effectuez une mise à niveau vers SharePoint Server 2013 ou SharePoint Server 2016, vous pouvez utiliser l’API de migration SharePoint (pour migrer des informations vers OneDrive entreprise, par exemple).
  
|**Online Pro**|**Con en ligne**|
|:-----|:-----|
|Microsoft fournit le matériel SPO et l’administration de toutes les ressources matérielles.  <br/> |Les fonctionnalités disponibles peuvent varier entre SharePoint Server sur site et SPO.  <br/> |
|Vous êtes l’administrateur général de votre abonnement et pouvez affecter des administrateurs aux sites SPO.  <br/> |Certaines actions disponibles pour un administrateur de batterie de serveurs dans SharePoint Server local n’existent pas ou ne sont pas nécessairement incluses dans le rôle d’administrateur SharePoint dans Microsoft 365.  <br/> |
|Microsoft applique les correctifs, les correctifs et les mises à jour sur le matériel et les logiciels sous-jacents. <br/> |Étant donné qu’il n’y a pas accès au système de fichiers sous-jacent dans le service, la personnalisation est limitée.  <br/> |
|Microsoft publie des [contrats de niveau de service](https://go.microsoft.com/fwlink/?linkid=843153) et se déplace rapidement pour résoudre les incidents de niveau de service. <br/> |La sauvegarde et la restauration, ainsi que d’autres options de récupération, sont automatisées par le service dans SharePoint Online. Les sauvegardes sont remplacées si elles ne sont pas utilisées. <br/> |
|Les tests de sécurité et le réglage des performances du serveur sont effectués en continu dans le service par Microsoft. <br/> |Les modifications apportées à l’interface utilisateur et à d’autres fonctionnalités SharePoint sont installées par le service et doivent être activées ou désactivées. <br/> |
|Microsoft 365 répond à de nombreuses normes industrielles : [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165).  <br/> |L’assistance [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de [route de contenu de migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Les ingénieurs du support technique Microsoft et les employés du centre de connaissances ne disposent pas d’un accès administrateur illimité à votre abonnement. <br/> |Il peut y avoir des coûts supplémentaires si le matériel doit être mis à niveau pour prendre en charge la version plus récente de SharePoint, ou si une batterie de serveurs secondaire est nécessaire pour la mise à niveau.  <br/> |
|Les partenaires peuvent vous aider lors du travail unique de migration de vos données vers SharePoint Online.  <br/> ||
|Les produits en ligne sont mis à jour automatiquement. Bien que les fonctionnalités puissent être déconseillées, il n’y a pas de terminaison de prise en charge réelle. <br/> ||
   
Si vous avez décidé de créer un nouveau site Microsoft 365 et de migrer manuellement les données vers ce dernier en fonction de vos besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe aucun moyen d’ignorer les versions des mises à niveau de SharePoint. Les mises à niveau sont en série :
  
- SharePoint 2007 \> SharePoint server 2010 SharePoint server \> 2013 \> SharePoint Server 2016
   
Pour passer de SharePoint 2007 à SharePoint Server 2016, il s’agit d’un investissement considérable en termes de temps et de coûts de matériel (les serveurs SQL doivent également être mis à niveau), de logiciels et d’administration. Les personnalisations doivent être mises à niveau ou abandonnées.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 de fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur le nouveau matériel (de sorte que les batteries de serveurs distinctes exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour le téléchargement et la rechargement de contenu, par exemple). Mais méfiez-vous des pièges de déplacement manuel, tels que les déplacements de documents qui remplacent le dernier compte modifié par l’alias du compte effectuant le déplacement manuel. Tenez également compte du travail qui doit être réalisé à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de liste. Examinez à l’avance les données que vous pouvez déplacer dans le stockage ou la supprimer pour réduire l’impact de la migration.
  
Il est important de nettoyer votre environnement avant de procéder à la mise à niveau. Assurez-vous que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau, et certainement avant la désaffectation.
  
N’oubliez pas de vérifier les *chemins de mise à niveau pris en charge et non pris en charge*: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si vous avez des personnalisations, il est essentiel d’avoir un plan pour chaque étape dans le chemin de migration : 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro local**|**Con local**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, depuis le serveur.  <br/> |Tous les sauts et correctifs sont la responsabilité de votre société (vous pouvez contacter le support Microsoft payant si votre produit n’est pas au-delà de la fin du support).  <br/> |
|Ensemble complet de fonctionnalités de SharePoint Server sur site avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un environnement hybride.  <br/> |La mise à niveau, les correctifs, les correctifs de sécurité et la maintenance de SharePoint Server sur site.  <br/> |
|Accès total pour une personnalisation accrue.  <br/> |Les [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur sont effectués sur votre site (sous votre contrôle).  <br/> |Microsoft 365 peut mettre à disposition des fonctionnalités de SharePoint Online qui ne fonctionnent pas avec SharePoint Server en local.  <br/> |
|Les partenaires peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) , comme dans SharePoint Online.  <br/> |
|Contrôle total des conventions d’affectation de noms, de la sauvegarde et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.  <br/> |SharePoint Server local est sensible au cycle de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Assurez-vous que votre environnement répond à la configuration matérielle et logicielle requise, puis suivez les méthodes de mise à niveau prises en charge.
  
- **Configuration matérielle/logicielle requise pour**: 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- Limites **et frontières logicielles pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Vue d’ensemble du processus de mise à niveau pour**: 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et l’environnement local

Si la réponse à vos besoins en matière de migration se situe entre l’auto-contrôle offert par le service local et le coût de possession inférieur offert par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [Découvrez les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Si vous décidez qu’une batterie de serveurs SharePoint Server hybride bénéficiera de votre entreprise, vous devez vous familiariser avec les types d’hybrides existants et configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.
  
| Option | Description |
|:-----|:-----|
[Offres pour la conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165)  <br/> |L’assistance [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) pour la migration est limitée.  <br/> Une grande partie de la mise à niveau sera manuelle ou via l’API de migration SPO décrite dans la feuille de [route de contenu de migration SharePoint Online et OneDrive](https://go.microsoft.com/fwlink/?linkid=843184).  <br/> |
|Les techniciens du support technique Microsoft et les employés du centre de données ne disposent pas d’un accès administrateur illimité à votre abonnement.<br/> |Il peut y avoir des coûts supplémentaires si l’infrastructure matérielle doit être mise à niveau pour prendre en charge la version plus récente de SharePoint, ou si une batterie de serveurs secondaire est nécessaire pour la mise à niveau.  <br/> |
|Les partenaires peuvent vous aider lors du travail unique de migration de vos données vers SharePoint Online.  <br/> ||
|Les produits en ligne sont mis à jour automatiquement à travers le service. Bien que les fonctionnalités puissent être déconseillées, il n’y a pas de terminaison de prise en charge.<br/> ||
   
Si vous avez décidé de créer un nouveau site Microsoft 365 et de migrer manuellement les données vers ce dernier en fonction de vos besoins, vérifiez vos [options Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Mettre à niveau SharePoint Server en local

Il n’existe aucun moyen d’ignorer les versions des mises à niveau de SharePoint. Les mises à niveau sont en série :
  
- SharePoint 2007 \> SharePoint server 2010 SharePoint server \> 2013 \> SharePoint Server 2016
   
Pour passer de SharePoint 2007 à SharePoint Server 2016, il s’agit d’un investissement considérable en termes de temps et de coûts liés au matériel (les serveurs SQL doivent également être mis à niveau), les logiciels et l’administration. Les personnalisations doivent être mises à niveau ou abandonnées.
  
> [!NOTE]
> Il est possible de maintenir votre batterie de serveurs SharePoint 2007 de fin de vie, d’installer une batterie de serveurs SharePoint Server 2016 sur le nouveau matériel (de sorte que les batteries de serveurs distinctes exécutent côte à côte), puis de planifier et d’exécuter une migration manuelle de contenu (pour le téléchargement et la rechargement de contenu, par exemple). Mais méfiez-vous des pièges potentiels des déplacements manuels, tels que les déplacements de documents qui remplacent le dernier compte modifié par l’alias du compte effectuant le déplacement manuel, et le travail qui doit être réalisé à l’avance, comme la recréation de sites, de sous-sites, d’autorisations et de structures de listes. Déterminez les données que vous pouvez déplacer dans le stockage ou la suppression pour réduire l’impact de la migration.
  
Nettoyez votre environnement avant la mise à niveau. Assurez-vous que votre batterie de serveurs existante est fonctionnelle avant de procéder à la mise à niveau avant de procéder à la mise hors service. 
  
N’oubliez pas de vérifier les *chemins de mise à niveau pris en charge et non pris en charge*: 
  
- 
  [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843156)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843157)
    
Si vous avez des *personnalisations*, nous vous recommandons de planifier votre mise à niveau pour chaque étape dans le chemin de migration : 
  
- [SharePoint 2007](https://go.microsoft.com/fwlink/?linkid=843158)
    
- [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843160)
    
- [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843162)
    
|**Pro local**|**Con local**|
|:-----|:-----|
|Contrôle total de tous les aspects de votre batterie de serveurs SharePoint, depuis le serveur.  <br/> |Tous les sauts et correctifs sont la responsabilité de votre entreprise. (Vous pouvez contacter le support Microsoft payant si votre produit n’est pas au-delà de la fin du support.)  <br/> |
|Ensemble complet de fonctionnalités de SharePoint Server sur site avec la possibilité de connecter votre batterie de serveurs sur site à un abonnement SharePoint Online via un environnement hybride.  <br/> |La mise à niveau, les correctifs, les correctifs de sécurité et la maintenance de SharePoint Server sur site.  <br/> |
|Accès total pour une personnalisation accrue.  <br/> |Les [offres de conformité Microsoft](https://go.microsoft.com/fwlink/?linkid=843165) doivent être configurées manuellement en local.  <br/> |
|Les tests de sécurité et le réglage des performances du serveur sont effectués sur votre site sous votre contrôle.  <br/> |Microsoft 365 peut mettre à disposition des fonctionnalités de SharePoint Online qui ne fonctionnent pas avec SharePoint Server en local  <br/> |
|Les partenaires peuvent vous aider à migrer les données vers la prochaine version de SharePoint Server (et au-delà).  <br/> |Vos sites SharePoint Server n’utiliseront pas automatiquement les certificats [SSL/TLS](https://go.microsoft.com/fwlink/?linkid=843167) comme indiqué dans SharePoint Online.  <br/> |
|Contrôle total des conventions d’affectation de noms, de la sauvegarde et de la restauration, ainsi que d’autres options de récupération dans SharePoint Server en local.  <br/> |SharePoint Server local est sensible au cycle de vie des produits.  <br/> |
   
### <a name="upgrade-resources"></a>Mettre à niveau les ressources

Assurez-vous que votre environnement répond à la configuration matérielle et logicielle requise. Ensuite, suivez les méthodes de mise à niveau prises en charge.
  
- **Configuration matérielle/logicielle requise pour :** 
    
    [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843204)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843206)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843207)
    
- **Limites et frontières logicielles pour :** 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843245)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843247)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843248)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843249)
    
- **Vue d’ensemble du processus de mise à niveau pour :** 
    
    [SharePoint Server 2007](https://go.microsoft.com/fwlink/?linkid=843250)  |  [SharePoint Server 2010](https://go.microsoft.com/fwlink/?linkid=843251)  |  [SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=843252)  |  [SharePoint Server 2016](https://go.microsoft.com/fwlink/?linkid=843359)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Créer une solution SharePoint hybride entre SharePoint Online et l’environnement local

Si la réponse à vos besoins en matière de migration se situe entre l’auto-contrôle offert par le service local et le coût de possession inférieur offert par SharePoint Online, vous pouvez connecter des batteries de serveurs SharePoint Server 2013 ou 2016 à SharePoint Online via des hybrides. [En savoir plus sur les solutions hybrides SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Si vous décidez qu’une batterie de serveurs SharePoint Server hybride bénéficiera de votre entreprise, vous devez vous familiariser avec les types d’hybrides existants et configurer la connexion entre votre batterie de serveurs SharePoint locale et votre abonnement Microsoft 365.
  
Pour voir comment cela fonctionne, il est recommandé de créer un environnement de développement/test Microsoft 365, que vous pouvez configurer avec des [guides de laboratoire de test](m365-enterprise-test-lab-guides.md). Une fois que vous avez obtenu une version d’évaluation ou un abonnement à Microsoft 365, vous pouvez créer les collections de sites, les sites Web et les bibliothèques de documents dans SharePoint Online vers lesquels vous pouvez migrer des données. Vous pouvez migrer manuellement, à l’aide de l’API de migration, ou si vous souhaitez migrer le contenu de mon site vers OneDrive entreprise, via l’Assistant hybride.
  
> [!NOTE]
> N’oubliez pas que pour utiliser l’option hybride, votre batterie de serveurs SharePoint 2007 doit être mise à niveau, localement, vers SharePoint Server 2013 ou SharePoint Server 2016.
  
## <a name="related-topics"></a>Voir aussi

[Résolution des problèmes et reprise de la mise à niveau (Office SharePoint Server 2007)](https://go.microsoft.com/fwlink/?linkid=843192)
  
[Résoudre les problèmes de mise à niveau (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?linkid=843194)
  
[Résoudre les problèmes de mise à niveau des bases de données dans SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=843195)
  
[Rechercher des partenaires Microsoft pour faciliter la mise à niveau](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
