---
title: Gouvernance des applications dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: Implémentez les fonctionnalités de gouvernance des applications Microsoft pour régir vos applications.
ms.openlocfilehash: ca1a77c4f5a1543a000b563dde98238136b3115d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60189548"
---
# <a name="app-governance-add-on-to-microsoft-cloud-app-security-in-preview"></a>Module complémentaire de gouvernance des applications pour Microsoft Cloud App Security (en préversion)

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

> [!NOTE]
> Pour vous inscrire à la gouvernance des applications, consultez [Démarrage avec la gouvernance des applications (en préversion)](app-governance-get-started.md).

Les cyberattaques sont de plus en plus sophistiquées dans la façon dont elles exploitent les applications que vous avez déployées dans vos infrastructures locales et cloud, en établissant un point de départ pour l’escalade de privilèges, le déplacement latéral et l’exfiltration de vos données. Pour comprendre les risques potentiels et arrêter ces types d’attaques, vous devez obtenir une visibilité claire de la posture de conformité des applications de votre organisation afin d’identifier rapidement quand une application présente des comportements anormaux et de répondre quand ces comportements présentent des risques pour votre environnement, vos données et vos utilisateurs.

La fonctionnalité de module complémentaire de gouvernance des applications à Microsoft Cloud App Security est une fonctionnalité de gestion de la sécurité et des stratégies conçue pour les applications compatibles OAuth qui accèdent aux données Microsoft 365 via Microsoft Graph API. La gouvernance des applications offre une visibilité, une correction et une gouvernance complètes sur la façon dont ces applications et leurs utilisateurs accèdent, utilisent et partagent vos données sensibles stockées dans Microsoft 365 par le biais d’insights actionnables et d’alertes et d’actions de stratégie automatisées.

<!--
The scale of ongoing cybersecurity incidents affecting large enterprises and smaller businesses highlights the dangers of supply chain attacks and the need to strengthen the security and compliance posture of every organization. Accelerated cloud adoption with Microsoft 365 and its rich application ecosystem are constantly growing. Attackers are gaining organizational footholds through applications because:

- Users are typically unaware of the risks when consenting to the use of applications. 
- App developers and independent software vendors (ISVs) do not yet have Security Development Lifecycle (SDL) best practices in place to address attacker techniques.
-->

La gouvernance des applications vous offre des fonctionnalités complètes :

- **Insights**: consultez une vue de toutes les applications tierces pour la plateforme Microsoft 365 dans votre client sur un tableau de bord unique. Vous pouvez voir l’état et les activités d’alerte de toutes les applications, et y réagir ou y répondre.
- **Gouvernance**: créez des stratégies proactives ou réactives pour les modèles et comportements des applications et des utilisateurs, et protégez vos utilisateurs contre l’utilisation d’applications non conformes ou malveillantes et en limitant l’accès des applications à risque à vos données.
- **Détection**: être alerté et averti en cas d’anomalies dans l’activité de l’application et lorsque des applications non conformes, malveillantes ou à risque sont utilisées.
- **Correction**: en plus des fonctionnalités de correction automatique, utilisez les contrôles de correction en temps voulu pour répondre aux détections anormales d’activité d’application.

La gouvernance des applications est une solution basée sur une plateforme qui fait partie intégrante de l’écosystème d’applications Microsoft 365. La gouvernance des applications supervise et régit les applications compatibles OAuth qui sont inscrites auprès de Azure Active Directory (Azure AD) et accèdent aux données via l’API Microsoft Graph. La gouvernance des applications vous fournit des contrôles de comportement d’application pour renforcer la sécurité et la conformité de votre infrastructure informatique.

## <a name="a-first-glimpse-at-app-governance"></a>Un premier aperçu de la gouvernance des applications

Pour voir le tableau de bord de la gouvernance des applications, allez à [https://compliance.microsoft.com/appgovernance](https://compliance.microsoft.com/appgovernance). Notez que votre compte de connexion doit avoir l'un des [rôles d'administrateur](app-governance-get-started.md#administrator-roles) pour voir toutes les données de gouvernance des applications.

## <a name="app-governance-integration-with-azure-ad-and-microsoft-cloud-app-security"></a>Intégration de la gouvernance des applications à Azure AD et Microsoft Cloud App Security

La gouvernance des applications, Azure AD et Microsoft Cloud App Security collectent et fournissent différents jeux de données :

- La gouvernance des applications fournit des informations détaillées sur l’activité d’une application au niveau de l’API.
- Azure AD fournit des métadonnées d’application de base et des informations détaillées sur les connexions aux applications.
- Microsoft Cloud App Security fournit des informations sur les risques liés aux applications.

En partageant des informations sur la gouvernance des applications, les Azure AD et les Microsoft Cloud App Security, vous pouvez afficher des informations agrégées dans un portail et lier facilement à un autre portail pour plus d’informations. Voici quelques exemples :

- Informations de connexion d’application dans la gouvernance des applications :

  Dans le portail de gouvernance des applications, vous pouvez voir l’activité de connexion agrégée pour chaque application et créer un lien vers le centre d’administration Azure Active Directory pour obtenir les détails des événements de connexion.

<!--
- App API usage information in the Azure Active Directory admin center:

  From the Azure Active Directory admin center, you can see the aggregated app usage information and link to the app governance portal for the details of app usage.
-->
- Informations sur l’utilisation de l’API dans le portail Microsoft Cloud App Security :

  Dans le portail Microsoft Cloud App Security, vous pouvez voir le niveau d’utilisation de l’API et agréger le transfert de données et le lien vers le portail de gouvernance des applications pour plus d’informations.

Voici un résumé de l’intégration.

![Intégration de la gouvernance des applications avec Azure AD et Microsoft Cloud App Security.](..\media\manage-app-protection-governance\mapg-integration.png)

La gouvernance des applications envoie ses alertes à Microsoft Cloud App Security et Microsoft 365 Defender et reçoit des alertes de Microsoft Cloud App Security, pour permettre une analyse plus détaillée des incidents de sécurité basés sur les applications.
- Les alertes de gouvernance des applications s'affichent dans la liste des alertes Microsoft 365 Defender en tant qu'alertes avec le champ Source de détection défini sur « Gouvernance des applications »
- Les alertes de gouvernance des applications s'affichent dans la liste des alertes MCAS en tant qu'alertes avec le champ Stratégie défini sur l'un des éléments suivants :
  - Gouvernance des applications OAuth Microsoft 365
  - Détection de l'hameçonnage de OAuth Microsoft 365
  - Réputation de l’application OAuth Microsoft 365
- Les alertes MCAS apparaissent dans la liste des alertes de gouvernance d’application en tant qu’alertes avec la source définie sur MCAS.

> [!NOTE]
> L’état des alertes n’est actuellement pas synchronisé entre la gouvernance des applications et Microsoft Cloud App Security.
