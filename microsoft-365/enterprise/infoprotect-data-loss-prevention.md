---
title: 'Étape 5 : configurer la prévention des pertes de données Office 365'
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/19/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre et déployer Prévention des pertes de données Office 365 dans Microsoft 365.
ms.openlocfilehash: 896670e9ae83324a1220d64f49a8ea48aee85169
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42067221"
---
# <a name="step-5-configure-office-365-data-loss-prevention"></a>Étape 5 : configurer la prévention des pertes de données Office 365

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![Phase 6 : Protection des informations](../media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

Les stratégies de protection contre la perte de données (DLP) disponibles dans le Centre de sécurité et conformité Office 365 vous permettent d’identifier, de surveiller et de protéger automatiquement des informations sensibles dans Microsoft 365. Avec les stratégies DLP, vous pouvez :

- Identifier les informations sensibles à de nombreux emplacements, comme Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams.
- Empêcher le partage accidentel d’informations sensibles en bloquant l’accès à un document ou le courrier qui le contient.
- Surveiller et protéger les informations sensibles dans les versions de bureau d’Excel, de PowerPoint et de Word.
- Aider les utilisateurs à respecter les règles de conformité sans interrompre leur flux de travail avec des notifications e-mail et conseils de stratégie. 
- Consulter les rapports DLP présentant le contenu qui correspond aux stratégies DLP de votre organisation.

Une stratégie DLP spécifie :

- **Où :** emplacements comme Exchange Online, SharePoint Online, sites OneDrive Entreprise et chats et canaux Microsoft Teams.
- **Quand :** conditions auxquelles le contenu doit correspondre au sein d’une règle de stratégie spécifique.
- **Comment :** actions dans cette règle de stratégie correspondante permettant d’adapter automatiquement les conditions correspondantes.

En d’autres termes :

- Pour un document dans cet emplacement (où), si le contenu remplit les conditions d’une règle (quand), alors automatiquement effectuer les actions spécifiées dans la règle (comment).

Pour déterminer l’ensemble de stratégies DLP dont vous avez besoin, vous devez analyser vos documents et les types de données y figurant nécessitant une protection contre la perte de données. Par exemple, si vous êtes une entreprise financière aux États-Unis, vous pouvez créer une stratégie DLP qui empêche le partage de documents avec des numéros de sécurité sociale en dehors de l’organisation ou envoyés dans un courrier électronique à des emplacements externes à l’organisation.

Ensuite, vous configurez et testez les stratégies avec des emplacements tests pour vous assurer que le comportement DLP est correct et pour réduire les faux positifs.

Enfin, vous le déployez dans votre organisation en informant les employés de nouvelles stratégies et leur comportement souhaité et vous élargissez l’étendue des emplacements.

Pour plus d’informations, voir [prise en main recommandations en matière de stratégie DLP](https://docs.microsoft.com/office365/securitycompliance/get-started-with-dlp-policy-recommendations).

Comme point de contrôle intermédiaire, consultez les [critères de sortie](infoprotect-exit-criteria.md#crit-infoprotect-step5) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![Étape 6](../media/stepnumbers/Step6.png)|[Configurer le chiffrement des e-mails](infoprotect-email-encryption.md)|


