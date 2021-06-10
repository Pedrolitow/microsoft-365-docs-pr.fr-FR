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
localization_priority: Normal
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
ms.openlocfilehash: 9d61da5a12882bef3ffee715bffb37ec96a18fd1
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204379"
---
# <a name="threat-investigation-and-response"></a>Examen et réponse contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applicable aux**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)


Les fonctionnalités d’examen et de réponse aux menaces dans [Microsoft Defender](defender-for-office-365.md) pour Office 365 aident les analystes et les administrateurs de sécurité à protéger le Microsoft 365 de leur organisation pour les utilisateurs professionnels en :

- Faciliter l’identification, la surveillance et la compréhension des cyberattaques
- Aide à résoudre rapidement les menaces dans Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams
- Fournir des informations et des connaissances pour aider les opérations de sécurité à empêcher les cyberattaques contre leur organisation
- L’emploi [d’examens et de réponses automatisés Office 365](automated-investigation-response-office.md) pour les menaces critiques basées sur la messagerie

Les fonctionnalités d’examen et de réponse aux menaces fournissent des informations sur les menaces et les actions de réponse associées disponibles dans le Centre de sécurité & conformité. Ces informations peuvent aider l’équipe de sécurité de votre organisation à protéger les utilisateurs contre les attaques basées sur des e-mails ou des fichiers. Les fonctionnalités permettent de surveiller les signaux et de collecter des données provenant de plusieurs sources, telles que l’activité des utilisateurs, l’authentification, la messagerie, les PC compromis et les incidents de sécurité. Les décideurs d’entreprise et votre équipe en matière d’opérations de sécurité peuvent utiliser ces informations pour comprendre et répondre aux menaces contre votre organisation et protéger votre propriété intellectuelle.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>Se familiariser avec les outils d’examen et de réponse aux menaces

Les fonctionnalités d’examen et de réponse aux menaces sont disponibles dans le Centre de sécurité & conformité, sous la mesure d’un ensemble d’outils et de flux de travail de réponse, notamment :

- [Tableau de bord des menaces](#threat-dashboard)
- [Explorer](#threat-explorer)
- [Incidents](#incidents)
- [Simulateur d’attaques](#attack-simulator)
- [Examen et réponse automatisés](automated-investigation-response-office.md)

### <a name="threat-dashboard"></a>Tableau de bord des menaces

Utilisez le tableau de bord contre les menaces (également appelé tableau de bord de [sécurité)](security-dashboard.md)pour voir rapidement quelles menaces ont été traitées, et comme moyen visuel de signaler aux décideurs d’entreprise comment les services Microsoft 365 sécurisent votre entreprise.

![Tableau de bord des menaces](../../media/ce013a31-3f80-4d09-bb95-bfb7623b8bc4.png)

Pour afficher et utiliser ce tableau de bord, dans le Centre de sécurité & conformité, consultez le Tableau de bord **de gestion des** \> **menaces.**

### <a name="threat-explorer"></a>Threat Explorer

Utilisez [l’Explorateur de menaces (et](threat-explorer.md) les détections en temps réel) pour analyser les menaces, voir le volume d’attaques au fil du temps et analyser les données par familles de menaces, infrastructure des attaquants, etc. L’Explorateur de menaces (également appelé Explorateur) est le point de départ du flux de travail d’investigation d’un analyste de sécurité.

![Explorateur de menaces](../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png)

Pour afficher et utiliser ce rapport, dans le Centre de sécurité & conformité, allez dans l’Explorateur **de gestion des** \> **menaces.**

### <a name="incidents"></a>Incidents

Utilisez la liste Incidents (également appelée Investigations) pour voir la liste des incidents de sécurité de la flight. Les incidents sont utilisés pour suivre les menaces telles que les messages électroniques suspects, et pour mener des enquêtes et des corrections supplémentaires.

![Liste des incidents de menace actuels dans Office 365](../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png)

Pour afficher la liste des incidents actuels pour votre organisation, dans  le Centre de sécurité & conformité, allez à Incidents de révision de la gestion \>  \> **des menaces.**

![Dans le Centre de sécurité & conformité, choisissez Révision de la gestion des \> menaces](../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png)

### <a name="attack-simulator"></a>Simulateur d’attaques

Utilisez le Simulateur d’attaques pour configurer et exécuter des cyberattaques réalistes dans votre organisation et identifier les personnes vulnérables avant qu’une cyberattaque réelle affecte votre entreprise. Pour plus d’informations, [voir Simulateur d’attaques dans Office 365](attack-simulator.md).

### <a name="automated-investigation-and-response"></a>Enquêtes et réponses automatisées

Utilisez des fonctionnalités d’investigation et de réponse automatisées (AIR) pour gagner du temps et des efforts en corrélant le contenu, les appareils et les personnes à risque des menaces au niveau de votre organisation. Les processus AIR peuvent commencer chaque fois que certaines alertes sont déclenchées ou lorsqu’elles sont démarrées par votre équipe des opérations de sécurité. Pour en savoir plus, consultez [l’examen et la réponse automatisés dans Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>Widgets d’intelligence des menaces

Dans le cadre de l’offre Microsoft Defender pour Office 365 Plan 2, les analystes de sécurité peuvent examiner les détails d’une menace connue. Cela est utile pour déterminer s’il existe des mesures ou des mesures préventives supplémentaires qui peuvent être prises pour assurer la sécurité des utilisateurs.

![Tendances de sécurité affichant des informations sur les menaces récentes](../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png)

## <a name="how-do-we-get-these-capabilities"></a>Comment obtenir ces fonctionnalités ?

Microsoft 365 fonctionnalités d’examen et de réponse aux menaces sont incluses dans Microsoft Defender pour Office 365 Plan 2, qui est inclus dans Enterprise E5 ou en tant que modules pour certains abonnements. Pour en savoir plus, [consultez Defender pour Office 365 Plan 1 et Plan 2.](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2)

## <a name="required-roles-and-permissions"></a>Rôles et des autorisations requis

Microsoft Defender pour Office 365 utilise le contrôle d’accès basé sur les rôles. Les autorisations sont attribuées par le biais de certains rôles dans Azure Active Directory, le centre d’administration Microsoft 365 ou le Centre de sécurité & conformité.

> [!TIP]
> Bien que certains rôles, tels que l’administrateur de la sécurité, peuvent être affectés dans le Centre de sécurité & conformité, envisagez d’utiliser le Centre d’administration Microsoft 365 ou Azure Active Directory à la place. Pour plus d’informations sur les rôles, les groupes de rôles et les autorisations, consultez les ressources suivantes :
>
> - [Autorisations dans le centre de conformité et de sécurité](permissions-in-the-security-and-compliance-center.md)
>
> - [Autorisations des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)

****

|Activité|Rôles et autorisations|
|---|---|
|Utiliser le tableau de bord des menaces (ou le nouveau tableau [de bord de sécurité)](security-dashboard.md) <p> Afficher des informations sur les menaces récentes ou actuelles|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory ( ) ou dans <https://portal.azure.com> Microsoft 365'administration centrale ( <https://admin.microsoft.com> ).|
|Utiliser [l’Explorateur de menaces (et les détections en temps réel)](threat-explorer.md) pour analyser les menaces|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory ( ) ou dans <https://portal.azure.com> Microsoft 365'administration centrale ( <https://admin.microsoft.com> ).|
|Afficher les incidents (également appelés enquêtes) <p> Ajouter des messages électroniques à un incident|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité**</li><li>**Lecteur de sécurité**</li></ul> <p> Ces rôles peuvent être attribués dans Azure Active Directory ( ) ou dans <https://portal.azure.com> Microsoft 365'administration centrale ( <https://admin.microsoft.com> ).|
|Déclencher des actions de messagerie dans un incident <p> Rechercher et supprimer des messages électroniques suspects|Un des éléments suivants : <ul><li>**Administrateur général**</li><li>**Administrateur de sécurité** plus le **rôle Recherche et purge**</li></ul> <p> Les **rôles Administrateur** général et **Administrateur** de sécurité peuvent être attribués dans Azure Active Directory ( ) ou dans le centre <https://portal.azure.com> d’administration Microsoft 365 ( <https://admin.microsoft.com> ). <p> Le **rôle Recherche et purge** doit être attribué dans le Centre de sécurité & conformité ( <https://protection.office.com> ).|
|Intégrer Microsoft Defender pour Office 365 Plan 2 à Microsoft Defender pour endpoint  <p> Intégrer Microsoft Defender pour Office 365 Plan 2 à un serveur SIEM|Soit le **rôle Administrateur général,** **soit** Administrateur de la sécurité attribué dans Azure Active Directory ( ) ou dans le centre <https://portal.azure.com> d Microsoft 365'administration ( <https://admin.microsoft.com> ). <p> --- **plus** --- <p> Rôle approprié attribué dans des applications supplémentaires (par exemple, [Centre de sécurité Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/user-roles) ou votre serveur SIEM).|
|

## <a name="next-steps"></a>Prochaines étapes

- [En savoir plus sur les suivis des menaces : nouveautés et remarques](threat-trackers.md)

- [Rechercher et examiner les e-mails malveillants qui ont été remis (Office 365 et réponse aux menaces)](investigate-malicious-email-that-was-delivered.md)

- [Intégrer l Office 365 et la réponse aux menaces avec Microsoft Defender pour le point de terminaison](integrate-office-365-ti-with-mde.md)

- [En savoir plus sur le Simulateur d’attaques](attack-simulator.md)