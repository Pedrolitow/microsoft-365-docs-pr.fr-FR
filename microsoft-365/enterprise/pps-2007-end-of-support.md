---
title: Feuille de route pour la fin de l’assistance pour PerformancePoint Server 2007
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
f1.keywords:
- NOCSH
description: PerformancePoint Server 2007, ProClarity et SharePoint Server 2007 ont atteint la fin du support. Lisez cet article pour planifier la mise à niveau de votre solution BI.
ms.openlocfilehash: b36d050222ceecf3b52f790a41d26cee4b05ff1c
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67671982"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour PerformancePoint Server 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les serveurs et applications Office 2007 ont atteint leur fin de support, y compris les serveurs et les applications que vous pouvez utiliser dans le cadre de vos solutions décisionnels. Le tableau suivant répertorie les applications bi affectées :
  
|**Applications Microsoft BI**|**Date de fin du support**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 Service Pack 3  <br/> ProClarity Desktop Professional 6.3  <br/> ProClarity SharePoint Viewer 6.3  <br/> |11 juillet 2017  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |10 octobre 2017  <br/> |
|PerformancePoint Server Service Pack 3 2007  <br/> |9 janvier 2018  <br/> |
   
Pour plus d’informations, consultez [Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Que signifie *la fin du support* ?

Comme la plupart des produits Microsoft, PerformancePoint Server 2007 SP3, les logiciels ProClarity et SharePoint Server 2007 SP3 ont un cycle de vie de support, au cours duquel Microsoft fournit de nouvelles fonctionnalités, des correctifs de bogues et des mises à jour de sécurité. Le cycle de vie d’un produit dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est connue sous le nom de fin de support du produit. Étant donné que ProClarity, PerformancePoint Server et SharePoint Server 2007 ont atteint leur fin de support, Microsoft ne fournit plus :
  
- Support technique pour les problèmes qui peuvent se produire.
    
- Correctifs de bogues pour les problèmes détectés et susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation des serveurs.
    
- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre les serveurs ou les applications vulnérables aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre installation de ProClarity, SharePoint Server 2007 SP3 et PerformancePoint Server 2007 SP3 continuera de s’exécuter même si la prise en charge est terminée. Toutefois, nous vous recommandons vivement de migrer à partir de ces applications dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

De nombreuses modifications ont été apportées aux applications Microsoft BI depuis 2007, et vous avez plusieurs options à prendre en compte, comme résumé dans le tableau suivant.
  
|**Si vous utilisiez ce ...**|**Explorez ces options ...**|**Et gardez cela à l’esprit ...**|
|:-----|:-----|:-----|
| surveillance &amp; PerformancePoint Server 2007 Fonctionnalités d’analytique, notamment :<br/>- Serveur d’analyse PerformancePoint <br/>- Concepteur de tableau de bord PerformancePoint<br/>- Visionneuse de tableaux de bord pour SharePoint Services (utilisé pour le rendu des tableaux de bord PerformancePoint, des cartes de performance et des rapports)<br/> |**Excel avec Excel dans un navigateur** (dans le cloud ou en local). Pour une vue d’ensemble, consultez [les fonctionnalités bi dans Excel et Microsoft 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx).<br/><br/> **Power BI** (dans le cloud ou en local). Pour obtenir une vue d’ensemble, consultez [Qu’est-ce que Power BI ?](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** (local). Pour obtenir une vue d’ensemble, consultez [SQL Server Reporting Services (SSRS) : créer, déployer et gérer des rapports mobiles et paginés](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports). <br/><br/> **PerformancePoint Services** (local). Pour obtenir une vue [d’ensemble, consultez Les nouveautés de PerformancePoint Services (SharePoint Server 2010).](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14)) <br/> |Excel est disponible en tant que solution en ligne (basée sur le cloud) ou locale. De nombreux besoins en matière de création de rapports et de tableau de bord peuvent être satisfaits avec Excel.  <br/><br/> Power BI est disponible en tant que solution en ligne ou locale. Power BI n’est pas inclus dans Microsoft 365. Toutefois, vous pouvez commencer à utiliser Power BI gratuitement. Plus tard, en fonction de l’utilisation des données et des besoins de votre entreprise, vous pouvez effectuer une mise à niveau vers Power BI Pro avec Microsoft 365 E5.<br/> <br/> Reporting Services et PerformancePoint Services sont des solutions locales. <br/><br/> PerformancePoint Services est disponible dans SharePoint Server 2010, SharePoint Server 2013 et SharePoint Server 2016. <br/> <br/> Certaines fonctionnalités et types de rapports qui étaient disponibles dans PerformancePoint Server 2007 ne sont pas disponibles dans Excel, Power BI, Reporting Services ou PerformancePoint Services. Passez en revue les fonctionnalités disponibles pour déterminer la meilleure solution pour vos besoins métier. <br/> |
| Logiciel ProClarity, notamment :<br/>- ProClarity Desktop Professional<br/> - ProClarity Analytics Server<br/>- Visionneuse SharePoint ProClarity<br/> |**Collaborez avec un partenaire Microsoft** pour identifier une solution qui répond le mieux à vos besoins. Visitez [l’Espace partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249). <br/><br/> Vous pouvez également envisager d’utiliser Excel avec Excel dans un navigateur, Power BI, SQL Server Reporting Services ou PerformancePoint Services.  <br/> |Plusieurs fonctionnalités du logiciel ProClarity, mais pas toutes, sont disponibles dans d’autres offres Microsoft, notamment Excel, Power BI, Reporting Services et PerformancePoint Services.  <br/> |
|Indicateurs de performance clés SharePoint Server 2007 (également appelés indicateurs de performance clés MOSS)  <br/> |**Excel avec Excel Services**. Pour une vue d’ensemble, consultez [Business Intelligence dans Excel et Excel Services (SharePoint Server 2013).](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |Les indicateurs de performance clés MOSS créés à l’aide de SharePoint Server 2007 peuvent être utilisés dans SharePoint Server 2010, SharePoint Server 2013 et SharePoint Server 2016. Toutefois, vous ne pouvez pas créer de KPI MOSS.  <br/> |
|Excel 2007  <br/> |**Excel** (dans le cloud ou en local). Pour une vue d’ensemble, consultez [les fonctionnalités bi dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/><br/> **Power BI** (dans le cloud ou en local). Pour obtenir une vue d’ensemble, consultez [Qu’est-ce que Power BI ?](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Excel et Power BI offrent à votre organisation des solutions cloud et locales, avec prise en charge d’une grande variété de sources de données.  <br/> |
   
### <a name="help-selecting-a-solution"></a>Aide sur la sélection d’une solution

Avec autant de choix décisionnels disponibles, il peut sembler difficile de déterminer quelle option est la meilleure. Nous avons un guide en ligne disponible pour vous aider. Consultez [Choisir les outils Décisionnel (BI) Microsoft pour l’analyse et la création de rapports](/sql/reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting).
  
### <a name="what-if-i-dont-upgrade-now"></a>Que se passe-t-il si je n’effectue pas de mise à niveau maintenant ?

Vous pouvez choisir de ne pas mettre à niveau immédiatement. Vos serveurs et applications existants continueront à s’exécuter. Toutefois, vous ne recevrez aucune autre mise à jour, y compris les mises à jour de sécurité, car la prise en charge est terminée. En cas de problème avec vos applications serveur, vous ne pourrez pas obtenir de l’aide du support technique Microsoft.
  
## <a name="how-do-i-plan-my-upgrade"></a>Comment faire planifier ma mise à niveau ?

Après avoir explorer vos options de mise à niveau, l’étape suivante consiste à préparer un plan de mise à niveau. Les sections suivantes incluent des informations et des ressources supplémentaires pour vous aider. Vous disposez de quatre options principales, dont deux qui fonctionnent à la fois dans le cloud ou localement, et deux qui sont en local uniquement :
  
|**Option**|**Dans le cloud ou en local ?**|
|:-----|:-----|
|[Excel avec SharePoint Server (local)](#excel-with-sharepoint-server-on-premises) <br/> |Les deux  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or-on-premises)<br/> |Les deux  <br/> |
|[Reporting Services](#use-reporting-services-on-premises) <br/> |En local uniquement  <br/> |
|[PerformancePoint Services](#use-performancepoint-services-on-premises) <br/> |En local uniquement  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>Utiliser Excel (dans le cloud ou en local)

Avec Excel, également appelé *Excel Services* dans SharePoint Server, vous pouvez afficher et utiliser des classeurs dans une fenêtre de navigateur, même si Excel n’est pas installé sur l’ordinateur. Vous pouvez utiliser Excel pour créer des rapports, des cartes de performance et des tableaux de bord. Ensuite, partagez vos classeurs avec d’autres personnes, qui peuvent utiliser Excel dans un navigateur, qu’ils utilisent SharePoint Online dans le cadre de Microsoft 365 ou SharePoint Server en local. Vous pouvez utiliser des données stockées localement ou dans le cloud, ce qui vous permet d’utiliser une grande variété de sources de données.
  
Le tableau suivant compare les principaux avantages de l’utilisation d’Excel avec Microsoft 365 à l’utilisation d’Excel avec SharePoint Server. Plus d’informations suivent.
  
|**Excel avec Microsoft 365 (dans le cloud)**|**Excel avec SharePoint Server (local)**|
|:-----|:-----|
|**Vous obtenez la version la plus récente et la plus récente d’Excel**. Avec Microsoft 365, vous obtenez la dernière version d’Excel, qui inclut de nouveaux types de graphiques puissants, la possibilité de créer des graphiques et des tables rapidement et facilement, ainsi que la prise en charge d’autres sources de données. <br/> <br/> **Le programme d’installation est beaucoup plus simple**. Excel est inclus dans Microsoft 365 pour les entreprises, il n’y a donc pas de gros travaux de votre part. Inscrivez-vous et connectez-vous, et vous serez opérationnel plus rapidement et plus efficacement que si vous mettez à niveau vos serveurs locaux. <br/> <br/> **Personnes ont partout accès à leurs classeurs**. Personnes pouvez afficher en toute sécurité les classeurs où qu’ils se trouvent, à l’aide de leur ordinateur, de leur smartphone et de leur tablette. <br/> <br/> **Il y a plus!** Consultez [les fonctionnalités bi dans Excel et Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/> |**Vous gérez vos paramètres globaux**. En tant qu’administrateur SharePoint, vous pouvez spécifier des paramètres globaux, tels que la sécurité, l’équilibrage de charge, la gestion des sessions, la mise en cache de classeur et les connexions de données externes. <br/> <br/> **Vous pouvez utiliser Excel Services avec PerformancePoint Services**. Vous pouvez configurer Excel Services et PerformancePoint Services dans le cadre de l’installation de SharePoint Server et inclure Excel Services rapports dans vos tableaux de bord PerformancePoint. <br/> <br/> **Il y a plus!** Consultez [Business Intelligence dans Excel et Excel Services (SharePoint Server 2013).](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |
   
#### <a name="excel-with-microsoft-365-in-the-cloud"></a>Excel avec Microsoft 365 (dans le cloud)

Si vous passez à Microsoft 365, vous disposerez des services et applications les plus à jour, y compris Excel 2016. PerformancePoint Services n’étant pas disponible dans Microsoft 365, vous allez remplacer le contenu de votre tableau de bord PerformancePoint par des classeurs Excel ou d’autres rapports. La bonne nouvelle est que Excel 2016 a un grand nombre de nouveaux types de graphiques et qu’il est plus facile que jamais de créer des tableaux de bord impressionnants dans Excel. De nouvelles fonctionnalités sont ajoutées régulièrement. Pour en savoir plus, consultez [Les nouveautés de Excel 2016 pour Windows](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx).
  
En outre, si vous achetez 50 sièges ou plus de Microsoft 365, l’équipe Microsoft FastTrack peut vous aider à vous configurer. Pour en savoir plus, visitez [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365).
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel avec SharePoint Server (local)

Si vous effectuez une mise à niveau vers une version plus récente de SharePoint, vous pouvez utiliser Excel avec Excel Services ou dans un navigateur, comme suit :
  
- Excel Services dans SharePoint Server 2010
    
- Excel Services dans SharePoint Server 2013
    
- Excel, qui fait partie de Office Online Server, installé séparément de SharePoint Server 2016
    
Vous pouvez également configurer PerformancePoint Services dans votre nouvelle version de SharePoint Server et l’utiliser avec Excel.
  
Pour en savoir plus sur vos options de mise à niveau SharePoint, consultez la [feuille de route de fin de support sharePoint Server 2007](sharepoint-2007-end-of-support.md).
  
Pour en savoir plus sur Excel Services, consultez [Excel Services vue d’ensemble (SharePoint Server 2010).](/previous-versions/office/sharepoint-server-2010/ee424405(v=office.14))
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>Utiliser Power BI (dans le cloud ou en local)

Power BI est une suite d’outils d’analytique métier permettant d’analyser les données et de partager des insights. Avec Power BI, vous pouvez utiliser des sources de données locales ou en ligne pour créer des rapports et des tableaux de bord interactifs. Personnes pouvez afficher et utiliser vos rapports et tableaux de bord sur leurs ordinateurs ou appareils mobiles.
  
Power BI ne fait pas partie de Microsoft 365 ou SharePoint Server. Il s’agit d’une offre distincte qui inclut des Power BI Desktop, des passerelles Power BI et des service Power BI. Power BI s’intègre également à SharePoint Online. Vous pouvez commencer à utiliser Power BI gratuitement. En fonction de l’utilisation des données et des besoins de votre entreprise, vous pouvez effectuer une mise à niveau ultérieure vers Power BI Pro avec Microsoft 365 E5. Pour en savoir plus, consultez [Qu’est-ce que Power BI ?](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>Utiliser Reporting Services (local)

SQL Server Reporting Services fournit une solution de création de rapports robuste. Vous pouvez configurer Reporting Services en mode natif ou en mode intégré SharePoint. Vous pouvez utiliser plusieurs outils différents pour créer des rapports, notamment Concepteur de rapports, Report Builder et Power View. Avec la dernière version de SQL Server, vous pouvez également utiliser SQL Server Éditeur de rapports mobiles pour fournir des rapports qui s’adapte à n’importe quelle taille d’écran. Cela permet aux visionneuses de consommer des rapports sur leurs appareils mobiles. Pour en savoir plus, consultez [SQL Server Reporting Services (SSRS) : créer, déployer et gérer des rapports mobiles et paginés](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports).
  
### <a name="use-performancepoint-services-on-premises"></a>Utiliser PerformancePoint Services (local)

PerformancePoint Server 2007 a été vendu séparément de SharePoint Server 2007. À compter de SharePoint Server 2010, PerformancePoint Services est une application de service dans SharePoint Server. Par conséquent, vous n’avez pas besoin d’acheter des licences de serveur ou du matériel distincts pour utiliser PerformancePoint Services.
  
Pour passer de PerformancePoint Server 2007 à PerformancePoint Services, vous accédez à une version plus récente de SharePoint Server et configurez PerformancePoint Services. La version de SharePoint Server que vous déplacez détermine si vous pouvez importer le contenu de votre tableau de bord existant de PerformancePoint Server 2007 à PerformancePoint Services.
  
- Si vous effectuez une mise à niveau vers SharePoint Server 2010, vous pouvez importer le contenu de votre tableau de bord PerformancePoint de PerformancePoint Server 2007 à PerformancePoint Services dans SharePoint Server 2010. Pour en savoir plus, consultez [l’Assistant Importation : PerformancePoint Server contenu 2007 vers SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/ee681485(v=office.14)).
    
- Si vous passez à SharePoint Server 2013 ou SharePoint Server 2016, vous devrez probablement créer du contenu de tableau de bord (sources de données, rapports, cartes de performance et pages de tableau de bord).
    
Pour commencer votre plan de mise à niveau PerformancePoint Services, consultez les ressources suivantes :
  
- [Feuille de route de fin du support SharePoint Server 2007](sharepoint-2007-end-of-support.md)
    
- Lorsque vous savez vers quelle version de SharePoint vous vous déplacez, consultez l’article correspondant pour PerformancePoint Services :
    
  - [Planifier PerformancePoint Services (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee681486(v=office.14))
    
  - [vue d’ensemble de PerformancePoint Services dans SharePoint Server 2013](/sharepoint/administration/performancepoint-services-overview)
    
  - [Vue d’ensemble de PerformancePoint Services dans SharePoint Server 2016](/sharepoint/administration/performancepoint-services-overview)
    
Lorsque vous effectuez une mise à niveau vers PerformancePoint Services, vous obtenez plusieurs nouvelles fonctionnalités et améliorations. PerformancePoint Services offre des cartes de performance améliorées; de nouvelles visualisations, telles que le rapport Détails de l’arborescence de décomposition et de l’indicateur de performance clé, davantage de types de graphiques, de meilleures fonctionnalités de filtrage Time Intelligence et une meilleure conformité de l’accessibilité. Pour plus [d’informations, consultez les nouveautés de PerformancePoint Services (SharePoint Server 2010).](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14))
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>Où puis-je obtenir de l’aide sur ma mise à niveau ?

Que vous procédiez à une mise à niveau locale ou à une migration vers Microsoft 365, nous vous recommandons de travailler avec un partenaire Microsoft. Un partenaire qualifié peut vous aider à identifier la solution qui répond le mieux aux besoins de votre entreprise et à faciliter votre déploiement. Visitez [l’Espace partenaires Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) et utilisez les filtres de recherche pour trouver un fournisseur de solutions.
  
## <a name="related-topics"></a>Voir aussi

[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)