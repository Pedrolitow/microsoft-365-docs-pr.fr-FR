---
title: En savoir plus sur la détection et la correction des menaces d’application
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: m365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: En savoir plus sur la détection et la correction des menaces d’application.
ms.openlocfilehash: 574688e67b7562c8df6aec7d2242e68485239479
ms.sourcegitcommit: 2fd60871975d61e60d4827b36cd689021fd2a4c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53438047"
---
# <a name="learn-about-app-threat-detection-and-remediation"></a>En savoir plus sur la détection et la correction des menaces d’application

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Avec la gouvernance des applications Microsoft, vous pouvez :

- Surveillez facilement les alertes de menace générées par les méthodes intégrées de détection de la gouvernance des applications pour les activités malveillantes des applications et les alertes basées sur des stratégies générées par des stratégies d’application actives que vous créez. Ces alertes peuvent indiquer des anomalies dans l’activité des applications et quand des applications non conformes, malveillantes ou à risque sont utilisées.  Vous pouvez également utiliser des modèles dans les alertes pour créer des stratégies d’application ou modifier les paramètres des stratégies existantes pour des actions plus restrictives.
- Corrigez facilement les alertes manuellement après examen ou automatiquement via les paramètres d’action sur les stratégies d’application actives.


>[!Note]
>Les activités anormales provenant d’applications Azure uniquement qui ne sont pas autorisées à accéder aux ressources Microsoft 365 ne sont pas incluses dans la détection et les alertes de gouvernance des applications.
>

Consultez les [rôles d’administrateur](app-governance-get-started.md#administrator-roles) pour savoir quels les rôles peuvent accéder aux pages de gouvernance des applications.


## <a name="app-governance-integration-with-azure-active-directory-and-microsoft-cloud-app-security"></a>Intégration de la gouvernance des applications à Azure Active Directory et Microsoft Cloud App Security

La gouvernance des applications, Azure Active Directory (Azure AD) et Microsoft Cloud App Security peuvent collecter et fournir différents jeux de données :

- La gouvernance des applications fournit des informations détaillées sur l’activité d’une application au niveau de l’API.
- Azure AD fournit des métadonnées d’application de base et des informations détaillées sur les connexions aux applications.
- Microsoft Cloud App Security fournit des informations sur les risques liés aux applications.

En partageant des informations sur la gouvernance des applications, les Azure AD et les Microsoft Cloud App Security, vous pouvez afficher des informations agrégées dans un portail et lier facilement à un autre portail pour plus d’informations. Voici quelques exemples :

- Informations de connexion d’application dans la gouvernance des applications :

  Dans le portail de gouvernance des applications, vous pouvez voir l’activité de connexion agrégée pour chaque application et créer un lien vers le centre d’administration Azure Active Directory pour obtenir les détails des événements de connexion.

- Informations sur l’utilisation de l’API d’application dans le centre d’administration Azure Active Directory :

  Dans le centre d’administration Azure Active Directory, vous pouvez voir les informations agrégées sur l’utilisation des applications et le lien vers le portail de gouvernance des applications pour plus d’informations sur l’utilisation des applications.

- Informations sur l’utilisation de l’API dans le portail Microsoft Cloud App Security : 

  Dans le portail Microsoft Cloud App Security, vous pouvez voir le niveau d’utilisation de l’API et agréger le transfert de données et le lien vers le portail de gouvernance des applications pour plus d’informations.

Voici un résumé de l’intégration.

![Intégration de la gouvernance des applications à Azure AD et Microsoft Cloud App Security](..\media\manage-app-protection-governance\mapg-integration.png)

En outre, la gouvernance des applications envoie ses alertes en tant que signaux à Microsoft Cloud App Security et Microsoft 365 Defender pour une analyse plus détaillée des incidents de sécurité basés sur les applications.

<!--

CFA #3 Scenario 1:  As an admin, I can investigate alerts associated to my M365 apps through MAPG.
CFA #3 Scenario 2: As an admin, I can manually remediate 
CFA #3 Scenario 3: As an admin, I can configure policies to perform automatic 
--> 

## <a name="next-step"></a>Étape suivante

[Démarrage avec la détection et la correction des menaces d’application.](app-governance-detect-remediate-get-started.md)
