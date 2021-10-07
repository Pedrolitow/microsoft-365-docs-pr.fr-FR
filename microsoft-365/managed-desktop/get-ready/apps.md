---
title: Applications dans le Bureau géré Microsoft
description: Explique comment les applications sont gérées, notamment comment les packager, les déployer et les prendre en charge.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: e3ac937a4ff98d853ad16ef4ae5854da70fa4d99
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60213960"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Applications dans le Bureau géré Microsoft

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->
 
## <a name="apps-generally"></a>Applications généralement

Microsoft inclut certaines applications clés, ainsi que la licence Microsoft 365 E3 ou E5 nécessaire pour participer à Microsoft Manged Desktop. Toutefois, même si nous fournissons ces applications, vous avez encore certaines responsabilités et actions à effectuer.

Vous pouvez également déployer d’autres applications non Microsoft pour vos utilisateurs en libre-service via le Portail d'entreprise ou une installation en arrière-plan requise, le tout à l’aide du pipeline de déploiement de Microsoft Intune. 

## <a name="apps-provided-by-microsoft"></a>Applications fournies par Microsoft

Les versions 64 bits des applications de Applications Microsoft 365 pour les grandes entreprises Standard Suite (Word, Excel, PowerPoint, Outlook, sont incluses dans votre licence Microsoft Manged Desktop. Publisher, Access, Teams et OneNote.) Les versions « Click-to-Run » de Microsoft Project  et Visio ne sont pas incluses par défaut, mais vous pouvez les demander à être ajoutées. Pour plus d’informations sur ces applications, voir [Installer Microsoft Project ou Microsoft Visio sur Microsoft Manged Desktop appareils.](../get-started/project-visio.md)

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Ce que Microsoft fait pour prendre en charge les applications que nous fournissons

Microsoft fournit un service complet pour le déploiement, la mise à jour et la prise en charge des applications Applications Microsoft 365 pour les grandes entreprises incluses. Les versions « Click-to-Run » de  Microsoft Project et Visio ne sont pas incluses par défaut, mais Microsoft Manged Desktop fournira des groupes de déploiement permettant à votre administrateur informatique de gérer les licences et de déployer ces applications de manière appropriée pour votre organisation. Microsoft prendra en charge les utilisateurs de ces applications via les canaux Microsoft Manged Desktop support technique.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Ce que vous devez faire pour prendre en charge les applications que nous fournissons

Il existe encore certaines choses que vous devez faire avec ces applications :

- **Attribuer des licences** : vous êtes responsable de l’obtention et de l’attribution des licences appropriées aux utilisateurs pour Applications Microsoft 365 pour les grandes entreprises.
- **Ajouter des utilisateurs** à des groupes de sécurité : si vous utilisez Microsoft Project ou Visio, votre administrateur informatique doit ajouter ces utilisateurs aux groupes de déploiement appropriés. Les administrateurs informatiques sont également chargés de récupérer les licences de ces utilisateurs s’ils quittent l’entreprise.
- **Déployer Microsoft 365-ons** : si vous avez besoin d’autres modules pour l’une des applications Applications Microsoft 365 pour les grandes entreprises, déployez-les de manière centralisée comme n’importe quelle autre application Windows 32. 

## <a name="apps-you-provide"></a>Applications que vous fournissez

Vous avez probablement d’autres applications dont vous avez besoin pour vos opérations professionnelles. Ces applications ne peuvent être déployées que sur Microsoft Manged Desktop à l’aide Microsoft Intune pipeline de déploiement de l’application. Pour plus d’informations sur le déploiement d’applications, suivez les étapes de [Déploiement d’applications Microsoft Manged Desktop appareils.](../get-started/deploy-apps.md)

### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Préparation de vos propres applications pour l’inclusion dans Microsoft Manged Desktop
Examinez vos applications, en vérifiant :

- Aucune des applications n’est interdite ou n’a un comportement restreint, comme décrit [dans Microsoft Manged Desktop’application requise.](../service-description/mmd-app-requirements.md)
- Les applications doivent être prêtes à être Microsoft Intune. Pour plus d’informations sur cette rubrique, [voir Windows 10 déploiement d’applications](/intune/apps-windows-10-app-deploy) à l’aide Microsoft Intune et Ajouter des applications à [Microsoft Intune](/intune/apps-add).
- Autres conditions préalables à l’empaquetage, telles que la fourniture de clés de licence, l’accord avec les termes du contrat de licence et la configuration préalable des connexions au serveur.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
2. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. Préparer les applications (cet article).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.
