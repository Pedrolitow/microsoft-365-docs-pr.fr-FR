---
title: Gouvernance des applications dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Implémentez les fonctionnalités de gouvernance des applications Microsoft pour régir vos applications.
ms.openlocfilehash: 63bd6684bc041c3c82ba6b8ddcc28c2600182b26
ms.sourcegitcommit: 997a21b83795789cda0a6b4a77f9985a3233d0c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2021
ms.locfileid: "53430695"
---
# <a name="app-governance-add-on-to-microsoft-cloud-app-security-in-preview"></a>Module complémentaire de gouvernance des applications pour Microsoft Cloud App Security (en préversion)

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

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

<!--
Unlike other application governance products in the marketplace, MAPG is a platform-based solution that is an integral part of the Microsoft 365 application ecosystem. MAPG's initial focus is on OAuth-enabled apps published to the Microsoft 365 platform that are registered with Azure AD and access data through the Graph API. For the initial release, MAPG does not support other, non-OAuth-enabled M365 apps, add-ins (such as PowerBI), or other app vendor ecosystems such as Google, Facebook, Amazon Web Services, Workplace, and Salesforce. MAPG’s focus is on third-party published apps for the Microsoft 365 application platform.

Microsoft allows developers to build cloud applications using Azure Active Directory (Azure AD), Microsoft’s cloud identity platform, and other resources and access to tenant data through the Microsoft Graph. Because of MAPG's visibility, insights, and control capabilities, app developers have the incentive to comply with publisher verification, self-attestation, and Microsoft certification, and can build high-quality productivity apps that are secure and compliant.
-->

## <a name="a-first-glimpse-at-app-governance"></a>Un premier aperçu de la gouvernance des applications

Pour afficher le tableau de bord de gouvernance des applications, accédez à [https://aka.ms/appgovernance](https://aka.ms/appgovernance). Notez que votre compte de connexion doit avoir l’un des [rôles d’administrateur](app-governance-get-started.md#administrator-roles) pour afficher les données de gouvernance des applications.

## <a name="app-governance-integration-with-azure-ad-and-microsoft-cloud-app-security"></a>Intégration de la gouvernance des applications à Azure AD et Microsoft Cloud App Security

La gouvernance des applications, Azure AD et Microsoft Cloud App Security collectent et fournissent différents jeux de données :

- La gouvernance des applications fournit des informations détaillées sur l’activité d’une application au niveau de l’API.
- Azure AD fournit des métadonnées d’application de base et des informations détaillées sur les connexions aux applications.
- Microsoft Cloud App Security fournit des informations sur les risques liés aux applications.

En partageant des informations sur la gouvernance des applications, Azure AD et Microsoft Cloud App Security, vous pouvez afficher des informations agrégées dans un portail et lier facilement à un autre portail pour plus d’informations. Voici quelques exemples :

- Informations de connexion d’application dans la gouvernance des applications :

  Dans le portail de gouvernance des applications, vous pouvez voir l’activité de connexion agrégée pour chaque application et créer un lien vers le centre d’administration Azure Active Directory pour obtenir les détails des événements de connexion.

<!--
- App API usage information in the Azure Active Directory admin center:

  From the Azure Active Directory admin center, you can see the aggregated app usage information and link to the app governance portal for the details of app usage.
-->
- Informations sur l’utilisation de l’API dans le portail Microsoft Cloud App Security :

  Dans le portail Microsoft Cloud App Security, vous pouvez voir le niveau d’utilisation de l’API et agréger le transfert de données et le lien vers le portail de gouvernance des applications pour plus d’informations.

Voici un résumé de l’intégration.

![Intégration de la gouvernance des applications à Azure AD et Microsoft Cloud App Security](..\media\manage-app-protection-governance\mapg-integration.png)

En outre, la gouvernance des applications envoie ses alertes en tant que signaux à Microsoft Cloud App Security et Microsoft 365 Defender, et la gouvernance des applications reçoit des alertes de Microsoft Cloud App Security, pour permettre une analyse plus détaillée des incidents de sécurité basés sur les applications.

<!--
Integration of alerts with MCAS and M365 Defender
Azure AD IP detections in progress to surface in M365 Defender

## Integration with Azure AD

**Feedback from Anand:** We should add some details on how MAPG works with M365 Defender (previously MTP). Also, we should highlight the integration with MCAS and AAD.

Key cross-reference resources:

- [What is application management in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-application-management)
- [Common application management scenarios for Azure Active Directory (especially scenarios 3-4)](https://docs.microsoft.com/cloud-app-security/monitor-alerts)
- [Azure Active Directory Identity Governance documentation](https://docs.microsoft.com/azure/active-directory/governance/)
- [Managing access to apps using Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management)

## Integration with Microsoft Cloud App Security

Key cross-reference resources:

- [Cloud App Security anomaly detection alerts investigation guide](https://docs.microsoft.com/cloud-app-security/investigate-anomaly-alerts#unusual-addition-of-credentials-to-an-oauth-app)
- [Monitor alerts raised in Cloud App Security](https://docs.microsoft.com/cloud-app-security/monitor-alerts)
- [Control which third-party cloud OAuth apps get permissions](https://docs.microsoft.com/cloud-app-security/manage-app-permissions)

-->

## <a name="using-app-governance"></a>Utilisation de la gouvernance des applications

L’utilisation de la gouvernance des applications pour protéger votre client et ses données contre les applications potentiellement malveillantes ou incorrectes s’inscrit dans ces trois fonctionnalités principales :

| Fonctionnalité | Description |
|:-------|:-----|
| [Visibilité et insights des applications](app-governance-visibility-insights-overview.md) | Obtenez une vue à 360° du trafic et de l’activité des applications Microsoft 365 dans votre client. |
| [Stratégies d’application pour une gouvernance renforcée](app-governance-app-policies-overview.md) | Créez des stratégies d’application proactives ou réactives, qui vous permettront d’appliquer la gouvernance pour vos applications Microsoft 3635. |
| [Détection et correction](app-governance-detect-remediate-overview.md) | En fonction des alertes de détection de plateforme ou des alertes de détection générées par la stratégie, surveillez le comportement anormal de vos applications et corrigez-le, automatiquement en fonction des paramètres de stratégie d’application ou manuellement. |
|||
