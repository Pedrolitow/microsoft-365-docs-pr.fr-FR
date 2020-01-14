---
title: Applications dans le bureau géré Microsoft
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: ea6cc92fe84cc39502e3db97361ff9d294fdfca2
ms.sourcegitcommit: 39bd4be7e8846770f060b5dd7d895fc8040b18f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "41112658"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Applications dans le bureau géré Microsoft

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->
 
## <a name="apps-generally"></a>Applications généralement

Microsoft inclut certaines applications clés, ainsi que la licence Microsoft 365 E3 ou E5 requise pour participer au bureau géré Microsoft. Toutefois, même si nous fournissons ces applications, vous avez toujours certaines responsabilités et actions à effectuer.

Vous pouvez également déployer des applications supplémentaires non-Microsoft pour les utilisateurs finaux en libre-service via le portail de l’entreprise ou une installation en arrière-plan requise, tout en utilisant le pipeline de déploiement de Microsoft Intune. Si vous disposez de l’expertise, vous pouvez migrer les applications dont vous avez besoin. Si ni Microsoft Consulting Services (MCS) ni un fournisseur non-Microsoft ne seront heureux de vous aider dans un projet d’empaquetage et de migration. Pour plus d’informations sur l’utilisation de MCS, voir [Working with Microsoft Consulting Services](apps-MCS.md).


## <a name="apps-provided-by-microsoft"></a>Applications fournies par Microsoft

Les versions 64 bits des applications de la suite Office 365 ProPlus standard (Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype entreprise et OneNote) sont incluses dans votre licence de bureau géré Microsoft. Les versions « démarrer en un clic » de Microsoft Project et Visio *ne sont pas* incluses par défaut, mais vous pouvez les demander pour qu’elles soient ajoutées. Pour plus d’informations sur ces applications, voir [installer Microsoft Project ou Microsoft Visio sur des appareils de bureau gérés Microsoft](../get-started/project-visio.md).

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Éléments pris en charge par Microsoft pour prendre en charge les applications que nous fournissons

Microsoft fournira un service complet pour le déploiement, la mise à jour et la prise en charge des applications Office 365 ProPlus incluses. Les versions « démarrer en un clic » de Microsoft Project et Visio ne sont *pas* incluses par défaut, mais le bureau géré Microsoft fournit des groupes de déploiement qui permettent à votre administrateur informatique de gérer des licences et de déployer ces applications de manière appropriée pour votre organisation. Microsoft prend en charge les utilisateurs finaux de ces applications par le biais des canaux de support de bureau géré Microsoft.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Ce que vous devez faire pour prendre en charge les applications que nous fournissons

Il reste certaines choses que vous devez faire avec ces applications :

- **Attribuer des licences** : vous êtes responsable de l’obtention et de l’affectation des licences appropriées aux utilisateurs finaux pour Office 365 ProPlus.
- **Ajouter des utilisateurs à des groupes de sécurité** : Si vous utilisez Microsoft Project ou Visio, votre administrateur informatique doit ajouter ces utilisateurs aux groupes de déploiement appropriés. Les administrateurs informatiques sont également chargés de récupérer les licences de ces utilisateurs s’ils quittent la société.
- **Deploy office 365 addons** -si vous avez besoin d’addons pour l’une des applications Office 365 ProPlus, déployez-les de manière centralisée comme n’importe quelle autre application Windows 32. 

## <a name="apps-you-provide"></a>Applications que vous fournissez

Bien entendu, vous disposez probablement d’un certain nombre d’autres applications dont vous avez besoin pour vos opérations professionnelles. Ces éléments peuvent uniquement être déployés sur des appareils de bureau gérés par Microsoft à l’aide du pipeline de déploiement de Microsoft Intune. Si l’application en a besoin, vous pouvez les présenter à un fournisseur (qui peut être un fournisseur non-Microsoft ou un service MCS) ou, si vous le faites, vous pouvez les empaqueter vous-même. Ajoutez ensuite ces packages au portail de bureau géré Microsoft et affectez-les à des groupes Azure Active Directory pour déclencher le déploiement. 

Si vous déployez actuellement vos applications à l’aide du gestionnaire de configuration de point de terminaison Microsoft, Microsoft Managed Desktop peut vous fournir une requête pour évaluer vos applications et découvrir celles que vous êtes prêt à migrer vers Microsoft Intune et celles qui peuvent nécessiter des ajustement.


### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Préparation de vos propres applications pour l’inclusion dans le bureau géré Microsoft
Passez en revue vos applications, en vérifiant les éléments suivants :

- Aucune des applications n’est interdite ou a un comportement restreint, comme décrit dans [Microsoft Managed Desktop App Requirements](https://aka.ms/app-req).
- Les applications doivent être prêtes pour la gestion par Microsoft Intune. Pour plus d’informations à ce sujet, voir [Windows 10 App Deployment Using Microsoft Intune](https://docs.microsoft.com/intune/apps-windows-10-app-deploy) et [Add Apps to Microsoft Intune](https://docs.microsoft.com/intune/apps-add).
- Autres conditions préalables à l’empaquetage, telles que la fourniture de clés de licence, l’accord avec les termes de licence et la prédéfinition des connexions serveur.

### <a name="decide-how-to-package-apps"></a>Décider comment empaqueter les applications

Certains fournisseurs de logiciels indépendants peuvent exiger que vos applications soient empaquetées avant d’être déployées de manière centralisée. « Packaging » signifie que le programme d’installation de l’application est configuré avec des paramètres tels que des clés de licence, des emplacements de serveur distant ou des raccourcis de bureau, afin que l’application puisse être installée en arrière-plan.

Vous disposez de trois options pour obtenir le package de vos applications : 


- Vous pouvez empaqueter les applications vous-même
- Vous pouvez travailler avec un fournisseur non-Microsoft
- Vous pouvez vous engager avec MCS pour empaqueter vos applications. Travaillez avec votre responsable de compte Microsoft. Pour plus d’informations, consultez la rubrique [Working with Microsoft Consulting Services](apps-MCS.md).







## <a name="deploying-apps"></a>Déploiement d’applications

Quelle que soit la méthode que vous utilisez pour obtenir un package d’applications, une fois cette opération terminée, vous êtes prêt à suivre les étapes décrites dans [Deploy Apps to Microsoft Managed Desktop Devices](../get-started/deploy-apps.md).


