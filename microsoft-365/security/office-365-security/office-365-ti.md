---
title: Fonctionnalités de réponse & d’enquête sur les menaces - plan Microsoft Defender pour Office 365 2
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/09/2019
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 32405da5-bee1-4a4b-82e5-8399df94c512
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Découvrez les fonctionnalités d’investigation et de réponse aux menaces dans Microsoft Defender pour Office 365 Plan.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c972a42730f4d21b73227a8b8a9900223109d590
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972032"
---
# <a name="threat-investigation-and-response"></a>Examen et réponse contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applicable aux**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Les fonctionnalités d’investigation et de réponse aux menaces dans [Microsoft Defender pour Office 365](defender-for-office-365.md) aident les analystes de sécurité et les administrateurs à protéger les Microsoft 365 de leur organisation pour les utilisateurs professionnels en :

- Faciliter l’identification, la surveillance et la compréhension des cyberattaques.
- Aider à résoudre rapidement les menaces dans Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams.
- Fournir des insights et des connaissances pour aider les opérations de sécurité à prévenir les cyberattaques contre leur organisation.
- Utilisation [d’une investigation et d’une réponse automatisées dans Office 365](automated-investigation-response-office.md) pour les menaces critiques basées sur les e-mails.

Les fonctionnalités d’investigation et de réponse aux menaces fournissent des insights sur les menaces et les actions de réponse associées disponibles dans le portail Microsoft 365 Defender. Ces informations peuvent aider l’équipe de sécurité de votre organisation à protéger les utilisateurs contre les attaques par e-mail ou par fichier. Les fonctionnalités permettent de surveiller les signaux et de collecter des données à partir de plusieurs sources, telles que l’activité de l’utilisateur, l’authentification, la messagerie électronique, les PC compromis et les incidents de sécurité. Les décideurs commerciaux et votre équipe chargée des opérations de sécurité peuvent utiliser ces informations pour comprendre et répondre aux menaces pesant sur votre organisation et protéger votre propriété intellectuelle.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>Se familiariser avec les outils d’investigation et de réponse aux menaces

Les fonctionnalités d’investigation et de réponse aux <https://security.microsoft.com> menaces dans le portail Microsoft 365 Defender sont un ensemble d’outils et de flux de travail de réponse qui incluent :

- [Explorer](#explorer)
- [Incidents](#incidents)
- [Formation à la simulation d'attaque](attack-simulation-training.md)
- [Examen et réponse automatisés](automated-investigation-response-office.md)

### <a name="explorer"></a>Explorer

Utilisez [l’Explorateur (et les détections en temps réel) pour analyser les menaces](threat-explorer.md) , voir le volume d’attaques au fil du temps et analyser les données par familles de menaces, l’infrastructure des attaquants, etc. L’Explorateur (également appelé Explorateur de menaces) est le point de départ du flux de travail d’investigation d’un analyste de sécurité.

:::image type="content" source="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png" alt-text="Page Explorateur de menaces" lightbox="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png":::

Pour afficher et utiliser ce rapport dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Email & Collaboration** \> **Explorer**. Ou, pour accéder directement à la page **Explorateur** , utilisez <https://security.microsoft.com/threatexplorer>.

## <a name="office-365-threat-intelligence-connection"></a>connexion Office 365 Threat Intelligence

Cette fonctionnalité n’est disponible que si vous disposez d’un abonnement Office 365 E5 actif ou du module complémentaire Threat Intelligence. Pour plus d’informations, consultez la page du produit Office 365 Entreprise E5.

Lorsque vous activez cette fonctionnalité, vous pouvez incorporer des données de Microsoft Defender pour Office 365 dans Microsoft 365 Defender afin d’effectuer une enquête de sécurité complète sur les boîtes aux lettres Office 365 et les appareils Windows.

> [!NOTE]
> Vous devez disposer de la licence appropriée pour activer cette fonctionnalité.

Pour recevoir l’intégration contextuelle des appareils dans Office 365 Threat Intelligence, vous devez activer les paramètres Defender pour point de terminaison dans le tableau de bord Sécurité & Conformité.

### <a name="incidents"></a>Incidents

Utilisez la liste des incidents (également appelée Investigations) pour afficher la liste des incidents de sécurité en vol. Les incidents sont utilisés pour suivre les menaces, telles que les messages électroniques suspects, et pour effectuer des investigations et des corrections plus approfondies.

:::image type="content" source="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png" alt-text="Liste des incidents de menace actuels dans Office 365" lightbox="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png":::

Pour afficher la liste des incidents actuels pour votre organisation dans le portail <https://security.microsoft.com>Microsoft 365 Defender, accédez à **Incidents & alertes** \> **Incidents**. Ou, pour accéder directement à la page **Incidents** , utilisez <https://security.microsoft.com/incidents>.

:::image type="content" source="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png" alt-text="Page Révision dans le Centre de sécurité & conformité" lightbox="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png":::

### <a name="attack-simulation-training"></a>Formation à la simulation d'attaque

Utilisez la formation de simulation d’attaque pour configurer et exécuter des cyberattaques réalistes dans votre organisation, et identifier les personnes vulnérables avant qu’une cyberattaque réelle n’affecte votre entreprise. Pour plus d’informations, consultez [Simuler une attaque par hameçonnage](attack-simulation-training.md).

Pour afficher et utiliser cette fonctionnalité dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**l’e-mail &** formation à la **simulation collaborationAttack** > . Ou, pour accéder directement à la page **d’entraînement de simulation d’attaque** , utilisez <https://security.microsoft.com/attacksimulator?viewid=overview>.

### <a name="automated-investigation-and-response"></a>Enquêtes et réponses automatisées

Utilisez des fonctionnalités d’investigation et de réponse automatisées (AIR) pour gagner du temps et des efforts pour mettre en corrélation le contenu, les appareils et les personnes à risque en cas de menaces au sein de votre organisation. Les processus AIR peuvent commencer chaque fois que certaines alertes sont déclenchées ou lorsqu’elles sont démarrées par votre équipe des opérations de sécurité. Pour en savoir plus, consultez [l’examen automatisé et la réponse dans Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>Widgets d’intelligence contre les menaces

Dans le cadre de l’offre Microsoft Defender pour Office 365 Plan 2, les analystes de sécurité peuvent examiner des détails sur une menace connue. Cela est utile pour déterminer s’il existe des mesures/étapes préventives supplémentaires qui peuvent être prises pour assurer la sécurité des utilisateurs.

:::image type="content" source="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png" alt-text="Le volet Tendances de sécurité affichant des informations sur les menaces récentes" lightbox="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png":::

## <a name="how-do-we-get-these-capabilities"></a>Comment obtenir ces fonctionnalités ?

Microsoft 365 fonctionnalités d’investigation et de réponse aux menaces sont incluses dans Microsoft Defender pour Office 365 plan 2, qui est inclus dans Enterprise E5 ou en tant que module complémentaire à certains abonnements. Pour en savoir plus, consultez [Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="required-roles-and-permissions"></a>Rôles et des autorisations requis

Microsoft Defender pour Office 365 utilise le contrôle d’accès en fonction du rôle. Les autorisations sont attribuées par le biais de certains rôles dans Azure Active Directory, le Centre d'administration Microsoft 365 ou le portail Microsoft 365 Defender.

> [!TIP]
> Bien que certains rôles, tels que l’administrateur de sécurité, puissent être attribués dans le portail Microsoft 365 Defender, envisagez plutôt d’utiliser le Centre d'administration Microsoft 365 ou Azure Active Directory. Pour plus d’informations sur les rôles, les groupes de rôles et les autorisations, consultez les ressources suivantes :
>
> - [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
> - [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference)

|Activité|Rôles et autorisations|
|---|---|
|Utiliser le tableau de bord Threat & Vulnerability Management (ou le nouveau [tableau de bord Sécurité](security-dashboard.md)) <p> Afficher des informations sur les menaces récentes ou actuelles|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory (<https://portal.azure.com>) ou dans le Centre d'administration Microsoft 365 (<https://admin.microsoft.com>).|
|Utiliser [l’Explorateur (et les détections en temps réel)](threat-explorer.md) pour analyser les menaces|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory (<https://portal.azure.com>) ou dans le Centre d'administration Microsoft 365 (<https://admin.microsoft.com>).|
|Afficher les incidents (également appelés enquêtes) <p> Ajouter des messages électroniques à un incident|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory (<https://portal.azure.com>) ou dans le Centre d'administration Microsoft 365 (<https://admin.microsoft.com>).|
|Déclencher des actions de messagerie dans un incident <p> Rechercher et supprimer des messages électroniques suspects|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité** plus le rôle **De recherche et de vidage**</li></ul> <p> Les rôles **Administrateur général** et **Administrateur de sécurité** peuvent être attribués dans Azure Active Directory (<https://portal.azure.com>) ou dans le Centre d'administration Microsoft 365 (<https://admin.microsoft.com>). <p> Le rôle **De recherche et de vidage** doit être attribué dans les **rôles e-mail & collaboration** dans le portail Microsoft 36 Defender (<https://security.microsoft.com>).|
|Intégrer Microsoft Defender pour Office 365 Plan 2 à Microsoft Defender pour point de terminaison <p> Intégrer Microsoft Defender pour Office 365 Plan 2 à un serveur SIEM|Le rôle **Administrateur général** ou **Administrateur de sécurité** attribué dans Azure Active Directory (<https://portal.azure.com>) ou le Centre d'administration Microsoft 365 (<https://admin.microsoft.com>). <p> --- **plus** --- <p> Rôle approprié attribué dans des applications supplémentaires (par exemple[, Centre de sécurité Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/user-roles) ou votre serveur SIEM).|

## <a name="next-steps"></a>Prochaines étapes

- [En savoir plus sur les suivis de menaces - Nouveaux et remarquables](threat-trackers.md)
- [Rechercher et examiner les e-mails malveillants qui ont été remis (Office 365 investigation et réponse aux menaces)](investigate-malicious-email-that-was-delivered.md)
- [Intégrer Office 365 Threat Investigation and Response à Microsoft Defender pour point de terminaison](integrate-office-365-ti-with-mde.md)
- [Simuler une attaque par hameçonnage](attack-simulation-training.md)
