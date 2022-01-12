---
title: Examen des menaces & fonctionnalités de réponse - Microsoft Defender pour Office 365 Plan 2
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
description: Découvrez les fonctionnalités d’examen et de réponse aux menaces dans Microsoft Defender Office 365 Plan.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e14cda205405b90a73689bde59fcccf22095f2df
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61933826"
---
# <a name="threat-investigation-and-response"></a>Examen et réponse contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applicable aux**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)


Les fonctionnalités d’examen et de réponse aux menaces dans [Microsoft Defender](defender-for-office-365.md) pour Office 365 aident les analystes et les administrateurs de sécurité à protéger le Microsoft 365 de leur organisation pour les utilisateurs professionnels en :

- Faciliter l’identification, la surveillance et la compréhension des cyberattaques.
- Aide à résoudre rapidement les menaces dans Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams.
- Fournir des informations et des connaissances pour aider les opérations de sécurité à empêcher les cyberattaques contre leur organisation.
- L’emploi [d’examens et](automated-investigation-response-office.md) de réponses automatisés Office 365 les menaces critiques basées sur la messagerie.

Les fonctionnalités d’examen et de réponse aux menaces fournissent des informations sur les menaces et les actions de réponse associées qui sont disponibles dans Microsoft 365 Defender portail. Ces informations peuvent aider l’équipe de sécurité de votre organisation à protéger les utilisateurs contre les attaques par courrier électronique ou basées sur des fichiers. Les fonctionnalités permettent de surveiller les signaux et de collecter des données à partir de plusieurs sources, telles que l’activité des utilisateurs, l’authentification, la messagerie, les PC compromis et les incidents de sécurité. Les décideurs d’entreprise et votre équipe en matière de sécurité peuvent utiliser ces informations pour comprendre et répondre aux menaces contre votre organisation et protéger votre propriété intellectuelle.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>Se familiariser avec les outils d’examen et de réponse aux menaces

Les fonctionnalités d’examen et de réponse aux menaces dans le portail Microsoft 365 Defender sont un ensemble d’outils et de flux de travail de réponse qui <https://security.microsoft.com> incluent :

- [Explorer](#explorer)
- [Incidents](#incidents)
- [Formation à la simulation d'attaque](attack-simulation-training.md)
- [Examen et réponse automatisés](automated-investigation-response-office.md)

### <a name="explorer"></a>Explorer

Utilisez [l’Explorateur (et](threat-explorer.md) les détections en temps réel) pour analyser les menaces, voir le volume d’attaques au fil du temps et analyser les données par familles de menaces, infrastructure de l’attaquant, etc. L’Explorateur (également appelé Explorateur de menaces) est le point de départ du flux de travail d’investigation d’un analyste de sécurité.

![Explorateur de menaces.](../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png)

Pour afficher et utiliser ce rapport dans le portail Microsoft 365 Defender, consultez l’Explorateur de collaboration & <https://security.microsoft.com>  \> **courrier électronique.** Ou, pour aller directement à la page **De l’Explorateur,** utilisez <https://security.microsoft.com/threatexplorer> .

### <a name="incidents"></a>Incidents

Utilisez la liste Incidents (également appelée Investigations) pour voir la liste des incidents de sécurité des vols. Les incidents sont utilisés pour suivre les menaces telles que les messages électroniques suspects, et pour mener des enquêtes et des corrections supplémentaires.

![Liste des incidents de menace en cours dans Office 365.](../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png)

Pour afficher la liste des incidents actuels pour votre organisation dans le portail Microsoft 365 Defender, consultez <https://security.microsoft.com> **Incidents &** \> **alertes Incidents**. Ou, pour aller directement à la page **Incidents,** utilisez <https://security.microsoft.com/incidents> .

![Dans le Centre de sécurité & conformité, choisissez Révision de la gestion des \> menaces.](../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png)

### <a name="attack-simulation-training"></a>Formation à la simulation d'attaque

Utilisez une formation sur la simulation d’attaques pour configurer et exécuter des cyberattaques réalistes dans votre organisation et identifier les personnes vulnérables avant qu’une cyberattaque réelle affecte votre entreprise. Pour plus d’informations, voir [Simuler une attaque par hameçonnage.](attack-simulation-training.md)

Pour afficher et utiliser cette fonctionnalité dans le portail Microsoft 365 Defender, consultez la & formation sur la simulation d’attaques de <https://security.microsoft.com> **collaboration.**  >   Ou, pour aller directement à la page de formation sur la **simulation d’attaque,** utilisez <https://security.microsoft.com/attacksimulator?viewid=overview> .

### <a name="automated-investigation-and-response"></a>Enquêtes et réponses automatisées

Utilisez des fonctionnalités d’investigation et de réponse automatisées (AIR) pour gagner du temps et des efforts en corrélant le contenu, les appareils et les personnes à risque des menaces au niveau de votre organisation. Les processus AIR peuvent commencer chaque fois que certaines alertes sont déclenchées ou lorsqu’elles sont démarrées par votre équipe des opérations de sécurité. Pour en savoir plus, consultez [l’examen et la réponse automatisés dans Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>Widgets d’intelligence des menaces

Dans le cadre de l’offre Microsoft Defender pour Office 365 Plan 2, les analystes de sécurité peuvent examiner les détails d’une menace connue. Cela est utile pour déterminer s’il existe des mesures ou des mesures préventives supplémentaires qui peuvent être prises pour assurer la sécurité des utilisateurs.

![Tendances de sécurité affichant des informations sur les menaces récentes.](../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png)

## <a name="how-do-we-get-these-capabilities"></a>Comment obtenir ces fonctionnalités ?

Microsoft 365 fonctionnalités d’examen et de réponse aux menaces sont incluses dans Microsoft Defender pour Office 365 Plan 2, qui est inclus dans Enterprise E5 ou en tant que modules pour certains abonnements. Pour en savoir plus, [consultez Defender pour Office 365 Plan 1 et Plan 2.](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2)

## <a name="required-roles-and-permissions"></a>Rôles et des autorisations requis

Microsoft Defender pour Office 365 utilise le contrôle d’accès basé sur les rôles. Les autorisations sont attribuées par le biais de certains rôles dans Azure Active Directory, le Centre d'administration Microsoft 365 ou le portail Microsoft 365 Defender web.

> [!TIP]
> Bien que certains rôles, tels que l’administrateur de sécurité, peuvent être affectés dans le portail Microsoft 365 Defender, envisagez d’utiliser l’Centre d'administration Microsoft 365 ou Azure Active Directory à la place. Pour plus d’informations sur les rôles, les groupes de rôles et les autorisations, consultez les ressources suivantes :
>
> - [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
> - [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference)

<br>

****

|Activité|Rôles et autorisations|
|---|---|
|Utiliser le tableau de bord gestion & des menaces et des vulnérabilités (ou le nouveau tableau [de bord sécurité](security-dashboard.md) <p> Afficher des informations sur les menaces récentes ou actuelles|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory ( ) ou <https://portal.azure.com> dans le Centre d'administration Microsoft 365 ( <https://admin.microsoft.com> ).|
|Utiliser [l’Explorateur (et les détections en temps réel)](threat-explorer.md) pour analyser les menaces|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory ( ) ou <https://portal.azure.com> dans le Centre d'administration Microsoft 365 ( <https://admin.microsoft.com> ).|
|Afficher les incidents (également appelés investigations) <p> Ajouter des messages électroniques à un incident|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory ( ) ou <https://portal.azure.com> dans le Centre d'administration Microsoft 365 ( <https://admin.microsoft.com> ).|
|Déclencher des actions de messagerie dans un incident <p> Rechercher et supprimer des messages électroniques suspects|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité** plus le **rôle Recherche et purge**</li></ul> <p> Les **rôles Administrateur** général et **Administrateur** de la sécurité peuvent être attribués dans Azure Active Directory ( ) ou le rôle Centre d'administration Microsoft 365 <https://portal.azure.com> ( <https://admin.microsoft.com> ). <p> Le **rôle Recherche et purge** doit être attribué dans les rôles de **collaboration** & messagerie dans le portail Microsoft 36 Defender ( <https://security.microsoft.com> ).|
|Intégrer Microsoft Defender pour Office 365 Plan 2 à Microsoft Defender pour Endpoint <p> Intégrer Microsoft Defender pour Office 365 Plan 2 à un serveur SIEM|Soit le **rôle Administrateur général,** **soit** Administrateur de la sécurité attribué dans Azure Active Directory ( ) ou le rôle Centre d'administration Microsoft 365 <https://portal.azure.com> ( <https://admin.microsoft.com> ). <p> --- **plus** --- <p> Rôle approprié attribué dans des applications supplémentaires (par exemple, [Centre de sécurité Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/user-roles) ou votre serveur SIEM).|
|

## <a name="next-steps"></a>Prochaines étapes

- [En savoir plus sur les suivis des menaces : nouveautés et remarques](threat-trackers.md)
- [Rechercher et examiner les e-mails malveillants qui ont été remis (Office 365 et réponse aux menaces)](investigate-malicious-email-that-was-delivered.md)
- [Intégrer l Office 365 et la réponse aux menaces avec Microsoft Defender pour le point de terminaison](integrate-office-365-ti-with-mde.md)
- [Simuler une attaque par hameçonnage](attack-simulation-training.md)
