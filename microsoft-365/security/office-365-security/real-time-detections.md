---
title: Informations de base de l’Explorateur de menaces et des détections en temps réel dans Microsoft Defender Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Utilisez les détections de l’Explorateur ou en temps réel pour examiner les menaces et y répondre efficacement.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4d0a9ba7ee40c8ad97df745a20d6b5b3314bb3d8
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182999"
---
# <a name="explorer-and-real-time-detections-basics"></a>Informations de base sur les détections en temps réel et de l’Explorateur

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Contenu de cet article :

- [Différences entre les détections de l’Explorateur et en temps réel](#differences-between-explorer-and-real-time-detections)
- [Licences et autorisations requises](#required-licenses-and-permissions)

> [!NOTE]
> Cela fait partie d’une série de **3 articles** sur l’Explorateur (également appelé Explorateur de **menaces),** la sécurité du courrier électronique et les bases de détection en temps réel et de l’Explorateur **(telles** que les différences entre les outils et les autorisations nécessaires pour les utiliser). Les deux autres articles de cette série sont le recherche de menaces dans [l’Explorateur](threat-hunting-in-threat-explorer.md) et la [sécurité de messagerie avec l’Explorateur.](email-security-in-microsoft-defender.md)

Cet article explique la différence entre l’Explorateur et les rapports de détections en temps réel, ainsi que les licences et autorisations requises.

Si votre organisation dispose de [Microsoft Defender](defender-for-office-365.md)pour Office 365 et que vous disposez des [autorisations,](#required-licenses-and-permissions)vous pouvez utiliser **l’Explorateur** (également appelé Explorateur de menaces) ou les détections en temps réel pour détecter et corriger les **menaces.**

Dans le portail Microsoft 365 Defender ( ), go <https://security.microsoft.com> to **Email & collaboration,** and then choose **Explorer** _or_ **Real-time detections**.

Avec ces outils, vous pouvez :

- Consultez les programmes malveillants détectés Microsoft 365 fonctionnalités de sécurité.
- Afficher l’URL de hameçonnage et cliquer sur les données de verdict.
- Démarrez un processus d’examen et de réponse automatisé à partir d’un affichage dans l’Explorateur.
- Examinez les e-mails malveillants, et bien plus encore.

Pour plus d’informations, voir [Sécurité du courrier électronique avec l’Explorateur.](email-security-in-microsoft-defender.md)

## <a name="differences-between-explorer-and-real-time-detections"></a>Différences entre les détections de l’Explorateur et en temps réel

- *Les détections en temps réel* sont un outil de rapports disponible dans Defender pour Office 365 Plan 1. *L’Explorateur de* menaces est un outil de recherche et de correction des menaces disponible dans Defender Office 365 Plan 2.
- Le rapport de détections en temps réel vous permet d’afficher les détections en temps réel. L’Explorateur de menaces le fait également, mais fournit des détails supplémentaires pour une attaque donnée, comme la mise en surbrillance des campagnes d’attaque, et offre aux équipes des opérations de sécurité la possibilité de corriger les menaces (notamment le déclenchement d’une enquête automatisée et d’une enquête sur les [réponses).](automated-investigation-response-office.md)
- Un *affichage de courrier tout* est disponible dans l’Explorateur de menaces, mais n’est pas inclus dans le rapport de détections en temps réel.
- Des fonctionnalités de filtrage enrichies et des actions de correction sont incluses dans l’Explorateur de menaces. Pour plus d’informations, voir Microsoft Defender pour la description Office 365 service : disponibilité des fonctionnalités dans [Defender pour Office 365 plans.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender](defender-for-office-365.md) pour Office 365 utiliser l’explorateur ou les détections en temps réel :

- Explorer est inclus uniquement dans Defender pour Office 365 Plan 2.
- Le rapport détections en temps réel est inclus dans Defender pour Office 365 Plan 1.

Les équipes des opérations de sécurité doivent attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender pour Office 365 et sachent que les détections d’Explorateur et en temps réel montrent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser *les* détections de l’Explorateur ou en temps réel, vous avez besoin des autorisations suivantes :

- Dans Defender pour Office 365 :
  - Gestion de l’organisation
  - Administrateur de sécurité (peut être affecté dans le centre d’administration Azure Active Directory de sécurité ( <https://aad.portal.azure.com> )
  - Lecteur de sécurité
- Dans Exchange Online :
  - Gestion de l’organisation
  - Afficher uniquement la gestion de l’organisation
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les articles suivants :

- [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Autorisations dans Exchange Online](/e/exchange/permissions-exo/permissions-exo)

## <a name="more-information"></a>Plus d’informations

- [L’Explorateur de menaces collecte les détails des e-mails sur la page d’entité de messagerie](mdo-email-entity-page.md)
- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](automated-investigation-response-office.md)
