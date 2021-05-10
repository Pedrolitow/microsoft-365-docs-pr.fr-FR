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
ms.openlocfilehash: 7ab7b5731d121106d930868b03330d4ac7befd77
ms.sourcegitcommit: de5fce90de22ba588e75e1a1d2e87e03b9e25ec7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52300154"
---
# <a name="threat-explorer-and-real-time-detections-basics"></a>Informations de base sur l’Explorateur de menaces et les détections en temps réel

Contenu de cet article :

- [Différences entre l’Explorateur de menaces et les détections en temps réel](#differences-between-threat-explorer-and-real-time-detections)<br/>
- [Licences et autorisations requises](#required-licenses-and-permissions)

> [!NOTE]
> Cela fait partie d’une série de **3** articles sur l’Explorateur de menaces **,** la sécurité du courrier électronique et les bases de détection **en** temps réel et de l’Explorateur (telles que les différences entre les outils et les autorisations nécessaires pour les utiliser). Les deux autres articles de cette série sont le recherche de menaces dans [l’Explorateur](threat-hunting-in-threat-explorer.md) de menaces et la sécurité du [courrier électronique avec l’Explorateur de menaces.](email-security-in-microsoft-defender.md)

Cet article explique la différence entre l’exploration des menaces et les rapports de détections en temps réel, ainsi que les licences et autorisations requises.

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si votre organisation dispose de [Microsoft Defender](defender-for-office-365.md)pour Office 365 et que vous disposez des [autorisations,](#required-licenses-and-permissions)vous pouvez utiliser l’Explorateur de menaces **(appelé** **Explorateur)** ou les détections en temps réel pour détecter et corriger les **menaces.**

Dans le Centre de sécurité &  **conformité,** sélectionnez Gestion des menaces, puis sélectionnez **Explorer** _ou_ **Détections en temps réel.**

<br>

****

|Avec Microsoft Defender pour Office 365 Plan 2, vous pouvez voir :|Avec Microsoft Defender pour Office 365 Plan 1, vous pouvez voir :|
|---|---|
|![Explorateur de menaces](../../media/threatmgmt-explorer.png)|![Détections en temps réel](../../media/threatmgmt-realtimedetections.png)|
|

Avec ces outils, vous pouvez :

- Consultez les programmes malveillants détectés Microsoft 365 fonctionnalités de sécurité.
- Afficher l’URL de hameçonnage et cliquer sur les données de verdict.
- Démarrez un processus d’examen et de réponse automatisé à partir d’un affichage dans l’Explorateur.
- Examinez les e-mails malveillants, et bien plus encore.

Pour plus d’informations, [voir Sécurité du courrier électronique avec l’Explorateur de menaces.](email-security-in-microsoft-defender.md)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Différences entre l’Explorateur de menaces et les détections en temps réel

- *Les détections en temps réel* sont un outil de rapports disponible dans Defender pour Office 365 Plan 1. *L’Explorateur de* menaces est un outil de recherche et de correction des menaces disponible dans Defender Office 365 Plan 2.
- Le rapport de détections en temps réel vous permet d’afficher les détections en temps réel. L’Explorateur de menaces le fait également, mais fournit des détails supplémentaires pour une attaque donnée, comme la mise en surbrillance des campagnes d’attaque, et offre aux équipes des opérations de sécurité la possibilité de corriger les menaces (notamment le déclenchement d’une enquête automatisée et d’une enquête sur les [réponses).](automated-investigation-response-office.md)
- Un *affichage de courrier tout* est disponible dans l’Explorateur de menaces, mais n’est pas inclus dans le rapport de détections en temps réel.
- Des fonctionnalités de filtrage enrichies et des actions de correction sont incluses dans l’Explorateur de menaces. Pour plus d’informations, voir Microsoft Defender pour la description Office 365 service : disponibilité des fonctionnalités dans [Defender pour Office 365 plans.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender](defender-for-office-365.md) pour Office 365 utiliser l’explorateur ou les détections en temps réel :

- Toutefois, Explorer est uniquement inclus dans Defender pour Office 365 Plan 2.
- Le rapport détections en temps réel est inclus dans Defender pour Office 365 Plan 1.

Les équipes des opérations de sécurité doivent attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender pour Office 365 et sachent que les détections d’Explorateur et en temps réel montrent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser *les* détections de l’Explorateur ou en temps réel, vous devez avoir les valeurs suivantes :

- Pour le Centre de sécurité & conformité :

  - Gestion de l’organisation
  - Administrateur de sécurité (peut être affecté dans le centre d’administration Azure Active Directory de sécurité ( <https://aad.portal.azure.com> )
  - Lecteur de sécurité

- Pour Exchange Online :

  - Gestion de l’organisation
  - Afficher uniquement la gestion de l’organisation
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les ressources suivantes :

- [Autorisations dans le centre de conformité et de sécurité](permissions-in-the-security-and-compliance-center.md)
- [Autorisations des fonctionnalités dans Exchange Online](/exchange/permissions-exo/feature-permissions)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Plus d’informations
- [L’Explorateur de menaces collecte les détails des e-mails sur la page d’entité de messagerie](mdo-email-entity-page.md)
- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](automated-investigation-response-office.md)