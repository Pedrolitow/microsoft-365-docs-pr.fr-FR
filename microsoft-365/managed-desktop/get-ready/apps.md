---
title: Applications dans le Bureau géré Microsoft
description: Explique comment les applications sont gérées, notamment comment les packager, les déployer et les prendre en charge.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 571acc9c240fc0243998050ac3013258a2f85a3e
ms.sourcegitcommit: e02cf5702af178ddd2968877a808874ecb49ed2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52028943"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Applications dans le Bureau géré Microsoft

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->
 
## <a name="apps-generally"></a>Applications généralement

Microsoft inclut certaines applications clés, ainsi que la licence Microsoft 365 E3 ou E5 nécessaire pour participer au Bureau géré Microsoft. Toutefois, même si nous fournissons ces applications, vous avez encore certaines responsabilités et actions à effectuer.

Vous pouvez également déployer d'autres applications non Microsoft pour vos utilisateurs en libre-service via le portail d'entreprise ou une installation en arrière-plan requise, à l'aide du pipeline de déploiement de Microsoft Intune. 

## <a name="apps-provided-by-microsoft"></a>Applications fournies par Microsoft

Les versions 64 bits des applications de la suite Microsoft 365 Apps for enterprise Standard Suite (Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype Entreprise et OneNote) sont incluses dans votre licence Bureau géré Microsoft. Les versions « Exécuter en un clic  » de Microsoft Project et De Visio ne sont pas incluses par défaut, mais vous pouvez les demander à être ajoutées. Pour plus d'informations sur ces applications, voir Installer Microsoft Project ou [Microsoft Visio sur les appareils de bureau géré Microsoft.](../get-started/project-visio.md)

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Ce que Microsoft fait pour prendre en charge les applications que nous fournissons

Microsoft fournit un service complet pour le déploiement, la mise à jour et la prise en charge des applications Microsoft 365 pour les entreprises incluses. Les versions « Click-to-Run »  de Microsoft Project et Visio ne sont pas incluses par défaut, mais Bureau géré Microsoft fournit des groupes de déploiement permettant à votre administrateur informatique de gérer les licences et de déployer ces applications de manière appropriée pour votre organisation. Microsoft prendra en charge les utilisateurs de ces applications via les canaux de support Bureau géré Microsoft.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Ce que vous devez faire pour prendre en charge les applications que nous fournissons

Il existe encore certaines choses que vous devez faire avec ces applications :

- **Attribuer des licences** : vous êtes responsable de l'obtention et de l'attribution des licences appropriées aux utilisateurs de Microsoft 365 Apps for enterprise.
- **Ajouter des utilisateurs** à des groupes de sécurité : si vous utilisez Microsoft Project ou Visio, votre administrateur informatique doit ajouter ces utilisateurs aux groupes de déploiement appropriés. Les administrateurs informatiques sont également chargés de récupérer les licences de ces utilisateurs s'ils quittent l'entreprise.
- **Déployez les modules** de développement microsoft 365 : si vous avez besoin de modules pour l'une des applications Microsoft 365 Apps pour entreprise, déployez-les de manière centralisée comme n'importe quelle autre application Windows 32. 

## <a name="apps-you-provide"></a>Applications que vous fournissez

Vous avez probablement d'autres applications dont vous avez besoin pour vos opérations professionnelles. Ces applications peuvent uniquement être déployées sur des appareils bureau géré Microsoft à l'aide du pipeline de déploiement de Microsoft Intune. Pour plus d'informations sur le déploiement d'applications, suivez les étapes de [déploiement d'applications sur des appareils de bureau géré Microsoft.](../get-started/deploy-apps.md)

### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Préparation de vos propres applications pour l'inclusion dans Le Bureau géré Microsoft
Examinez vos applications, en vérifiant :

- Aucune des applications n'est interdite ou n'a un comportement restreint, comme décrit dans les exigences de [l'application Bureau géré Microsoft.](../service-description/mmd-app-requirements.md)
- Les applications doivent être prêtes pour la gestion par Microsoft Intune. Pour plus d'informations sur cette rubrique, voir Déploiement d'applications Windows 10 à l'aide [de Microsoft Intune](/intune/apps-windows-10-app-deploy) et Ajouter des applications à Microsoft [Intune.](/intune/apps-add)
- Autres conditions préalables à l'empaquetage, telles que la fourniture de clés de licence, l'accord avec les termes du contrat de licence et la configuration préalable des connexions au serveur.

## <a name="steps-to-get-ready"></a>Étapes de préparation

1. Passer en [revue les conditions préalables pour le Bureau géré Microsoft.](prerequisites.md)
2. Utiliser [les outils d'évaluation de la préparation.](readiness-assessment-tool.md)
3. [Conditions préalables pour les comptes invité](guest-accounts.md)
4. [Configuration du réseau pour Bureau géré Microsoft](network.md)
5. [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft](certs-wifi-lan.md)
6. [Préparer l’accès aux ressources locales pour le Bureau géré Microsoft](authentication.md)
7. [Applications dans bureau géré Microsoft](apps.md) (cet article)
8. [Préparer les lecteurs mappés pour le Bureau géré Microsoft](mapped-drives.md)
9. [Préparer des ressources d’impression pour le Bureau géré Microsoft](printing.md)
