---
title: Applications dans le Bureau géré Microsoft
description: Explique comment les applications sont gérées, notamment comment les packager, les déployer et les prendre en charge.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ce43080c284c4c15be5a8799f70a43de611ff9ba
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62520438"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Applications dans le Bureau géré Microsoft

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->

## <a name="apps-generally"></a>Applications généralement

Microsoft inclut certaines applications clés, ainsi que la licence Microsoft 365 E3 ou E5 nécessaire pour participer à Microsoft Manged Desktop. Toutefois, même si nous fournissons ces applications, vous avez encore certaines responsabilités et actions à effectuer.

Vous pouvez également déployer d’autres applications non Microsoft pour vos utilisateurs via le libre-service via le Portail d'entreprise ou une installation en arrière-plan requise à l’aide du pipeline de déploiement de Microsoft Intune.

## <a name="apps-provided-by-microsoft"></a>Applications fournies par Microsoft

Les versions 64 bits des applications de Microsoft 365 Apps pour Enterprise Standard Suite (Word, Excel, PowerPoint, Outlook, Publisher, sont incluses avec votre licence Microsoft Manged Desktop. Accès, Teams et OneNote.)

Les versions « Click-to-Run » de Microsoft Project et Visio ne sont pas  incluses par défaut, mais vous pouvez les demander à être ajoutées. Pour plus d’informations sur ces applications, voir [Install Microsoft Project ou Microsoft Visio sur Microsoft Manged Desktop appareils.](../get-started/project-visio.md)

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Ce que Microsoft fait pour prendre en charge les applications que nous fournissons

Microsoft fournit un service complet pour le déploiement, la mise à jour et la prise en charge des applications Applications Microsoft 365 pour les grandes entreprises incluses. Les versions « Exécuter en un clic » Microsoft Project et Visio *ne sont pas incluses* par défaut. Toutefois, Microsoft Manged Desktop des groupes de déploiement pour permettre à votre administrateur informatique de gérer les licences et de déployer ces applications de manière appropriée pour votre organisation. Microsoft prendra en charge les utilisateurs de ces applications via les canaux Microsoft Manged Desktop support technique.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Ce que vous devez faire pour prendre en charge les applications que nous fournissons

Il existe encore certaines choses que vous devez faire avec ces applications :

| Tâche | Description |
| ------ | ------ |
| Attribuer des licences | Vous êtes responsable de l’obtention et de l’attribution des licences appropriées aux utilisateurs pour Applications Microsoft 365 pour les grandes entreprises. |
| Ajouter des utilisateurs à des groupes de sécurité | Si vous utilisez Microsoft Project ou Visio, votre administrateur informatique doit ajouter ces utilisateurs aux groupes de déploiement appropriés. Les administrateurs informatiques sont également chargés de récupérer les licences de ces utilisateurs s’ils quittent l’entreprise. |
| Déployer Microsoft 365 de modules | Si vous avez besoin de modules Applications Microsoft 365 pour les grandes entreprises applications, déployez-les de manière centralisée comme n’importe quelle autre application Windows 32.

## <a name="apps-you-provide"></a>Applications que vous fournissez

Vous avez probablement d’autres applications dont vous avez besoin pour vos opérations professionnelles. Ces applications ne peuvent être déployées que sur Microsoft Manged Desktop à l’aide Microsoft Intune pipeline de déploiement de l’application. Pour plus d’informations sur le déploiement d’applications, suivez les étapes de [Déploiement d’applications Microsoft Manged Desktop appareils.](../get-started/deploy-apps.md)

### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Préparation de vos propres applications pour l’inclusion dans Microsoft Manged Desktop

Examinez vos applications, en vérifiant :

- Aucune des applications n’est interdite ou n’a un comportement restreint, comme décrit [Microsoft Manged Desktop les exigences de l’application](../service-description/mmd-app-requirements.md).
- Les applications doivent être prêtes à être Microsoft Intune. Pour plus d’informations, [voir Windows 10 déploiement d’applications](/intune/apps-windows-10-app-deploy) à l Microsoft Intune et [Ajouter des applications à Microsoft Intune](/intune/apps-add).
- Autres conditions préalables à l’empaquetage, telles que la fourniture de clés de licence, l’accord avec les termes du contrat de licence et la configuration préalable des connexions au serveur.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
1. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. Préparer les applications (cet article).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.
