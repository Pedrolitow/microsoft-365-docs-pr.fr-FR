---
title: Applications dans le Bureau géré Microsoft
description: Explique comment les applications sont gérées, notamment comment les packager, les déployer et les prendre en charge.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 20d68ec007ccda82816ad2288428016019f6d4b2
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49840692"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Applications dans le Bureau géré Microsoft

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->
 
## <a name="apps-generally"></a>Applications généralement

Microsoft inclut certaines applications clés, ainsi que la licence Microsoft 365 E3 ou E5 nécessaire pour participer au Bureau géré Microsoft. Toutefois, même si nous fournissons ces applications, vous avez encore certaines responsabilités et actions à effectuer.

Vous pouvez également déployer d’autres applications non Microsoft pour vos utilisateurs en libre-service via le portail d’entreprise ou une installation en arrière-plan requise, à l’aide du pipeline de déploiement de Microsoft Intune. Si vous avez l’expertise requise, vous pouvez migrer les applications dont vous avez besoin . En outre, microsoft Consulting Services (MCS) ou les fournisseurs non-Microsoft seront ravis de vous aider avec un projet d’empaquetage et de migration. Pour plus d’informations sur l’working with MCS, voir [Working with Microsoft Consulting Services](apps-MCS.md).


## <a name="apps-provided-by-microsoft"></a>Applications fournies par Microsoft

Les versions 64 bits des applications de la suite Microsoft 365 Apps for enterprise Standard Suite (Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype Entreprise et OneNote sont incluses dans votre licence Bureau géré Microsoft). Les versions « Exécuter en un clic  » de Microsoft Project et De Visio ne sont pas incluses par défaut, mais vous pouvez les demander à être ajoutées. Pour plus d’informations sur ces applications, voir Installer Microsoft Project ou [Microsoft Visio sur les appareils de bureau géré Microsoft.](../get-started/project-visio.md)

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Ce que Microsoft fait pour prendre en charge les applications que nous fournissons

Microsoft fournit un service complet pour le déploiement, la mise à jour et la prise en charge des applications Microsoft 365 pour les entreprises incluses. Les versions « Click-to-Run »  de Microsoft Project et Visio ne sont pas incluses par défaut, mais Bureau géré Microsoft fournit des groupes de déploiement permettant à votre administrateur informatique de gérer les licences et de déployer ces applications de manière appropriée pour votre organisation. Microsoft prendra en charge les utilisateurs de ces applications via les canaux de support Bureau géré Microsoft.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Ce que vous devez faire pour prendre en charge les applications que nous fournissons

Il existe encore certaines choses que vous devez faire avec ces applications :

- **Attribuer des licences** : vous êtes responsable de l’obtention et de l’attribution des licences appropriées aux utilisateurs pour Microsoft 365 Apps for enterprise.
- **Ajouter des utilisateurs** à des groupes de sécurité : si vous utilisez Microsoft Project ou Visio, votre administrateur informatique doit ajouter ces utilisateurs aux groupes de déploiement appropriés. Les administrateurs informatiques sont également chargés de récupérer les licences de ces utilisateurs s’ils quittent l’entreprise.
- Déployer des modules de développement microsoft **365** : si vous avez besoin de modules de développement pour l’une des applications Microsoft 365 Apps pour entreprise, déployez-les de manière centralisée comme n’importe quelle autre application Windows 32. 

## <a name="apps-you-provide"></a>Applications que vous fournissez

Vous avez probablement d’autres applications dont vous avez besoin pour vos opérations professionnelles. Ces applications peuvent uniquement être déployées sur des appareils bureau géré Microsoft à l’aide du pipeline de déploiement de Microsoft Intune. Si l’application en a besoin, vous pouvez les empaquetés par un fournisseur (qui peut être un fournisseur non Microsoft ou Microsoft Consulting Services (MCS)) ou si vous en avez les moyens, vous pouvez les empaquetér vous-même. Vous ajoutez ensuite ces packages au portail Bureau géré Microsoft et les affectez à des groupes Azure Active Directory pour déclencher le déploiement. 

Si vous déployez actuellement vos applications à l’aide de Microsoft Endpoint Configuration Manager, Bureau géré Microsoft peut vous fournir une requête pour évaluer vos applications et découvrir les applications prêtes à migrer vers Microsoft Intune et les applications qui peuvent nécessiter un ajustement.


### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Préparation de vos propres applications pour l’inclusion dans Le Bureau géré Microsoft
Examinez vos applications, en vérifiant :

- Aucune des applications n’est interdite ou n’a un comportement restreint, comme décrit dans les exigences de [l’application Bureau géré Microsoft.](https://aka.ms/app-req)
- Les applications doivent être prêtes pour la gestion par Microsoft Intune. Pour plus d’informations sur cette rubrique, voir Déploiement d’applications Windows 10 à l’aide [de Microsoft Intune](https://docs.microsoft.com/intune/apps-windows-10-app-deploy) et Ajouter des applications à Microsoft [Intune.](https://docs.microsoft.com/intune/apps-add)
- Autres conditions préalables à l’empaquetage, telles que la fourniture de clés de licence, l’accord avec les termes du contrat de licence et la configuration préalable des connexions au serveur.

### <a name="decide-how-to-package-apps"></a>Décider comment mettre en package des applications

Certains éditeurs de logiciels indépendants peuvent exiger que vos applications soient empaquetées avant d’être déployées de manière centralisée. « Empaquetage » signifie que le programme d’installation de l’application est configuré avec des paramètres tels que les clés de licence, les emplacements de serveurs distants ou les raccourcis de bureau afin que l’application puisse être installée en arrière-plan.

Il existe trois options pour empaquetér vos applications : 


- Vous pouvez packager des applications vous-même
- Vous pouvez travailler avec un fournisseur autre que Microsoft
- Vous pouvez utiliser MCS pour mettre en package vos applications. Travaillez avec votre représentant de compte Microsoft. Pour plus d’informations, [voir Working with Microsoft Consulting Services](apps-MCS.md).



## <a name="deploying-apps"></a>Déploiement d’applications

Quelle que soit la méthode que vous utilisez pour empaqueté des applications, une fois que vous avez terminé, vous êtes prêt à suivre les étapes de déploiement des applications sur les appareils de bureau géré [Microsoft.](../get-started/deploy-apps.md)


