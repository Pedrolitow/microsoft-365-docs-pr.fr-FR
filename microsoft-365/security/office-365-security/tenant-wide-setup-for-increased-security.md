---
title: Configurer votre client Microsoft 365 pour une sécurité accrue
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 10/11/2018
audience: ITPro
ms.topic: article
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: 8d274fe3-db51-4107-ba64-865e7155b355
ms.custom:
- seo-marvel-apr2020
description: Cette rubrique vous dirige vers la configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de Microsoft 365 environnement.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8a449d9647ae5a8b892967116f28aa6203a5e815
ms.sourcegitcommit: a6fb731fdf726d7d9fe4232cf69510013f2b54ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "52684170"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Configurer votre client Microsoft 365 pour une sécurité accrue

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cette rubrique vous dirige vers la configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de Microsoft 365 environnement. Vos besoins en matière de sécurité peuvent nécessiter plus ou moins de sécurité. Utilisez ces recommandations comme point de départ.

## <a name="check-office-365-secure-score"></a>Vérifier Office 365 secure score

Office 365 Le score de sécurité analyse la sécurité de votre organisation en fonction de vos activités régulières et de vos paramètres de sécurité et affecte un score. Commencez par prendre note de votre score actuel. L’ajustement de certains paramètres à l’échelle du client augmente votre score. L’objectif n’est pas d’atteindre le score maximum, mais de prendre en compte les opportunités de protection de votre environnement qui n’affectent pas la productivité de vos utilisateurs. Voir [Microsoft Secure Score](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-security-center"></a>Régler les stratégies de gestion des menaces dans le centre Microsoft 365 de sécurité

Le centre Microsoft 365 de sécurité inclut des fonctionnalités qui protègent votre environnement. Il inclut également des rapports et des tableaux de bord que vous pouvez utiliser pour surveiller et prendre des mesures. Certains domaines sont des configurations de stratégie par défaut. Certains domaines n’incluent pas de stratégies ou de règles par défaut. Consultez ces stratégies sous gestion des menaces pour régler les paramètres de gestion des menaces pour un environnement plus sécurisé.

<br>

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Anti-hameçonnage**|Oui|<ul><li>Protection contre l’emprunt d’identité — Si vous avez Defender pour Office 365 et un domaine personnalisé, configurez les paramètres de protection contre l’emprunt d’identité dans la stratégie anti-hameçonnage par défaut pour protéger les comptes de messagerie de vos utilisateurs les plus précieux, tels que votre PDG, et pour protéger votre domaine. Plus d’informations : [Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) et informations [sur l’emprunt d’identité](impersonation-insight.md)</li><li>Veille contre l’usurpation d’adresse : examinez les expéditeurs qui usurpent votre domaine. Bloquez ou autorisez ces expéditeurs. Plus d’informations : [Informations sur l’usurpation d’informations](learn-about-spoof-intelligence.md) dans EOP et gérer la liste d’adresses client [autoriser/bloquer](tenant-allow-block-list.md).</li></ul>|
|**Moteur anti-programme malveillant**|Oui|Modifiez la stratégie par défaut : <ul><li>Select **Enable the common attachments filter**</li></ul> <p> Vous pouvez également créer des stratégies de filtrage des programmes malveillants personnalisées et les appliquer à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. <p> Plus d’informations : <ul><li>[Protection contre les programmes malveillants](anti-malware-protection.md)</li><li>[Configurer des stratégies anti-programme malveillant](configure-anti-malware-policies.md)</li></ul>|
|**Pièces jointes sécurisées dans Microsoft Defender pour Office 365**|Non|Dans la page principale des pièces jointes sécurisées, cliquez sur **Paramètres** globaux et activer ce paramètre : <ul><li>**Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams**</li></ul> <p> Créez une stratégie de pièces jointes sécurisées avec les paramètres ci-après : <ul><li> **Bloquer :** sélectionnez **Bloquer en** tant que réponse anti-programme malveillant inconnue.</li><li>**Activer la redirection**: cochez cette case et entrez une adresse de messagerie, telle qu’un compte d’administrateur ou de mise en quarantaine.</li><li>**Appliquez la sélection ci-dessus si l’analyse des** programmes malveillants pour les pièces jointes arrive à arriver à son arrivée ou si une erreur se produit : cochez cette case.</li><li>**_Appliqué à_*: **le domaine du destinataire est votre** \> domaine.</li></ul> <p> Plus d’informations : [Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md) stratégies de pièces jointes sécurisées et configurer des [stratégies de pièces jointes sécurisées](set-up-safe-attachments-policies.md)|
|**Liens sécurisés dans Microsoft Defender pour Office 365**|Oui|Dans la page principale de liens sécurisés, cliquez **sur Paramètres globaux**: <ul><li>**Utilisez la fonction Liens sécurisés dans : Office 365 applications :** vérifiez que ce paramètre est allumé.</li><li>**Ne pas suivre le moment où les utilisateurs cliquent sur** Liens sécurisés : désactiver ce paramètre pour suivre les clics des utilisateurs.</li></ul> <p> Créez une stratégie de liens sécurisés avec les paramètres suivants : <ul><li>**Sélectionnez l’action pour les URL potentiellement malveillantes inconnues** dans les messages : Vérifiez que ce paramètre est **sur**.</li><li>**Sélectionnez l’action pour les URL inconnues** ou potentiellement malveillantes dans Microsoft Teams : vérifiez que ce paramètre est **sur**.</li><li>**Appliquez l’analyse d’URL en** temps réel pour les liens suspects et les liens qui pointent vers des fichiers : cochez cette case.</li><li>**Attendez que l’analyse des URL se termine avant de remettre le message**: cochez cette case.</li><li>**Appliquer des liens sûrs aux messages électroniques envoyés au sein** de l’organisation : cochez cette case</li><li>**N’autorisez pas les utilisateurs à cliquer sur l’URL d’origine**: cochez cette case.</li><li>**Appliqué à**: **le domaine du destinataire est votre** \> domaine.</li></ul> <p> Plus d’informations : [Configurer des stratégies de liens sécurisés.](set-up-safe-links-policies.md)|
|**Anti-courrier indésirable (filtrage du courrier)**|Oui| Ce qu’il faut surveiller : trop de courrier indésirable — Choisissez les paramètres personnalisés et modifiez la stratégie de filtrage du courrier indésirable par défaut. Plus d’informations [: Microsoft 365 protection contre le courrier indésirable](anti-spam-protection.md).|
|***Authentification de messagerie***|Oui|L’authentification de messagerie utilise un DNS (Domain Name System) pour ajouter des informations vérifiables aux messages électroniques concernant l’expéditeur d’un e-mail. Microsoft 365 l’authentification de messagerie électronique pour son domaine par défaut (onmicrosoft.com), mais les administrateurs Microsoft 365 peuvent également utiliser l’authentification de messagerie pour les domaines personnalisés. Trois méthodes d’authentification sont utilisées : <ul><li>Sender Policy Framework (ou SPF).</li><ul><li>Pour l’installation, [voir Configurer SPF dans Microsoft 365 pour empêcher l’usurpation.](set-up-spf-in-office-365-to-help-prevent-spoofing.md)</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>Voir [Utiliser DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé.](use-dkim-to-validate-outbound-email.md)</li><li>Une fois que vous avez configuré DKIM, activez-le dans le centre de sécurité.</li></ul><li>DMARC (Domain-based Message Authentication, Reporting, and Conformance).</li><ul><li>Pour le programme d’installation [de DMARC, utilisez DMARC pour valider les messages Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|
|

> [!NOTE]
> Pour les déploiements non standard de SPF, les déploiements hybrides et la résolution des problèmes : comment Microsoft 365 utilise [SPF (Sender Policy Framework)](how-office-365-uses-spf-to-prevent-spoofing.md)pour empêcher l’usurpation.

## <a name="view-dashboards-and-reports-in-the-security--compliance-center"></a>Afficher les tableaux de bord et les rapports dans le Centre de sécurité & conformité

Consultez ces rapports et tableaux de bord pour en savoir plus sur l’état de votre environnement. Les données de ces rapports s’enrichiront à mesure que votre organisation utilisera Office 365 services. Pour l’instant, familiarisez-vous avec ce que vous pouvez surveiller et prendre des mesures. Pour plus d’informations, [voir Rapports dans le Centre de sécurité & conformité.](../../compliance/reports-in-security-and-compliance.md)

<br>

****

|Tableau de bord|Description|
|---|---|
|[Tableau de bord de gestion des menaces](security-dashboard.md)|Dans la **section** Gestion des menaces du Centre de sécurité, utilisez ce tableau de bord pour voir les menaces qui ont déjà été gérées et comme outil pratique pour signaler aux décideurs d’entreprise les fonctionnalités d’examen et de réponse aux menaces qui ont déjà été réalisées pour sécuriser votre entreprise.|
|[Threat Explorer (et détections en temps réel)](threat-explorer.md)|Il se trouve également dans la section **Gestion des** menaces du centre de sécurité. Si vous examinez ou rencontrez une attaque contre votre client, utilisez l’Explorateur (ou les détections en temps réel) pour analyser les menaces. L’Explorateur (et le rapport de détections en temps réel) vous indique le volume d’attaques au fil du temps, et vous pouvez analyser ces données par familles de menaces, infrastructure de l’attaquant, etc. Vous pouvez également marquer tout message suspect pour la liste Incidents.|
|Rapports — Tableau de bord|Dans la section **Rapports** du Centre de sécurité, affichez les rapports d’audit pour SharePoint online et Exchange Online organisations. Vous pouvez également accéder Azure Active Directory de connexion utilisateur (Azure AD), aux rapports d’activité des utilisateurs et au journal d’audit Azure AD à partir de la page Afficher les **rapports.**|
|

![Tableau de bord du Centre de sécurité](../../media/870ab776-36d2-49c7-b615-93b2bc42fce5.png)

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Configurer des paramètres Exchange Online à l’échelle du client

De nombreux contrôles de sécurité et de protection dans le centre Exchange’administration sont également inclus dans le centre de sécurité. Il n’est pas nécessaire de les configurer aux deux endroits. Voici quelques paramètres supplémentaires qui sont recommandés.

<br>

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Mail Flow** (règles de flux de messagerie, également appelées règles de transport)|Non|Ajoutez une règle de flux de messagerie pour vous protéger contre les ransomware en bloquant les types de fichiers exécutables Office types de fichiers contenant des macros. Pour plus d’informations, voir [Utiliser des règles de flux de messagerie pour inspecter les pièces jointes](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments)des messages Exchange Online . <p> Consultez les rubriques supplémentaires ci-après : <ul><li>[Se protéger contre les rançongiciels](../../admin/security-and-compliance/secure-your-business-data.md#5-protect-against-ransomware)</li><li>[Protection contre les programmes malveillants et ransomware dans Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Récupérer d’une attaque par ransomware dans Office 365](recover-from-ransomware.md)</li></ul> <p> Créez une règle de flux de messagerie pour empêcher le forwarding automatique du courrier électronique vers des domaines externes. Pour plus d’informations, voir [Atténuation des règles de forwarding externe client avec le score de sécurisation.](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score) <p> Plus d’informations [: Règles de flux de messagerie (règles](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) de transport) Exchange Online|
|**Activer l’authentification moderne**|Non|L’authentification moderne est une condition préalable à l’utilisation de l’authentification multifacteur (MFA). L’mf est recommandée pour sécuriser l’accès aux ressources cloud, y compris la messagerie. <p> Consultez les rubriques ci-après : <ul><li>[Activation ou désactivation de l’authentification moderne dans Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype Entreprise En ligne : activer votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> L’authentification moderne est activée par défaut pour Office clients 2016, SharePoint Online et OneDrive Entreprise. <p> Plus d’informations : Fonctionnement de l’authentification [moderne Office 2013 et Office applications clientes 2016](../../enterprise/modern-auth-for-office-2013-and-2016.md)|
|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Configurer des stratégies de partage à l’échelle du client dans SharePoint’administration centrale

Recommandations de Microsoft pour la configuration SharePoint sites d’équipe à des niveaux de protection croissants, en commençant par la protection de référence. Pour plus d’informations, voir [recommandations de stratégie pour la sécurisation SharePoint sites et fichiers.](sharepoint-file-access-policies.md)

SharePoint sites d’équipe configurés au niveau de référence autorisent le partage de fichiers avec des utilisateurs externes à l’aide de liens d’accès anonyme. Cette approche est recommandée au lieu d’envoyer des fichiers par courrier électronique.

Pour prendre en charge les objectifs de protection de base, configurez les stratégies de partage à l’échelle du client comme recommandé ici. Les paramètres de partage pour des sites individuels peuvent être plus restrictifs que cette stratégie à l’échelle du client, mais pas plus permissifs.

<br>

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Partage** (SharePoint Online et OneDrive Entreprise)|Oui|Le partage externe est activé par défaut. Ces paramètres sont recommandés : <ul><li>Autoriser le partage à des utilisateurs externes authentifiés et l’utilisation de liens d’accès anonyme (paramètre par défaut).</li><li>Les liens d’accès anonyme expirent dans ce nombre de jours. Entrez un nombre, si vous le souhaitez, par exemple 30 jours.</li><li>Type de lien par défaut : sélectionnez Interne (personnes de l’organisation uniquement). Les utilisateurs qui souhaitent partager à l’aide de liens anonymes doivent choisir cette option dans le menu de partage.</li></ul> <p> Plus d’informations : [Vue d’ensemble du partage externe](/sharepoint/external-sharing-overview)|
|

SharePoint centre d’administration et OneDrive Entreprise’administration centrale incluent les mêmes paramètres. Les paramètres de l’un ou l’autre centre d’administration s’appliquent aux deux.

## <a name="configure-settings-in-azure-active-directory"></a>Configurer les paramètres dans Azure Active Directory

N’oubliez pas de visiter ces deux zones dans Azure Active Directory pour terminer la configuration à l’échelle du client pour des environnements plus sécurisés.

### <a name="configure-named-locations-under-conditional-access"></a>Configurer des emplacements nommés (sous accès conditionnel)

Si votre organisation inclut des bureaux avec un accès réseau sécurisé, ajoutez les plages d’adresses IP Azure Active Directory en tant qu’emplacements nommés. Cette fonctionnalité permet de réduire le nombre de faux positifs signalés pour les événements de risque de sign-in.

Voir : [Emplacements nommés dans Azure Active Directory](/azure/active-directory/active-directory-named-locations)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Bloquer les applications qui ne permettent pas l’authentification moderne

L’authentification multifacteur nécessite des applications qui la prise en charge de l’authentification moderne. Les applications qui ne permettent pas l’authentification moderne ne peuvent pas être bloquées à l’aide de règles d’accès conditionnel.

Pour les environnements sécurisés, assurez-vous de désactiver l’authentification pour les applications qui ne la prisent pas en charge de l’authentification moderne. Vous pouvez le faire dans Azure Active Directory avec un contrôle qui sera bientôt disponible.

En attendant, utilisez l’une des méthodes suivantes pour effectuer cette tâche pour SharePoint Online et OneDrive Entreprise :

- Utilisez PowerShell, voir [Bloquer les applications qui n’utilisent pas l’authentification moderne (ADAL).](/mem/intune/protect/app-modern-authentication-block)

- Configurez cette configuration dans le Centre d’administration SharePoint sur la page « Accès aux appareils » — « Contrôler l’accès à partir d’applications qui n’utilisent pas l’authentification moderne ». Sélectionnez Bloquer.

## <a name="get-started-with-cloud-app-security-or-office-365-cloud-app-security"></a>Prendre en Sécurité des applications cloud ou Sécurité des applications cloud Office 365

Utilisez Sécurité des applications cloud Office 365 pour évaluer les risques, pour alerter sur une activité suspecte et pour prendre automatiquement des mesures. Nécessite Office 365 plan E5.

Vous pouvez également utiliser Microsoft Cloud App Security pour obtenir une visibilité plus approfondie même une fois l’accès accordé, des contrôles complets et une protection améliorée pour toutes vos applications cloud, y compris Office 365.

Étant donné que cette solution recommande le plan EMS E5, nous vous recommandons de commencer par Sécurité des applications cloud afin de pouvoir l’utiliser avec d’autres applications SaaS dans votre environnement. Commencez par les stratégies et paramètres par défaut.

Plus d’informations :

- Rubrique relative au [déploiement de Cloud App Security](/cloud-app-security/getting-started-with-cloud-app-security)
- Rubrique relative aux [informations supplémentaires concernant Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Qu’est-ce Sécurité des applications cloud ?](/cloud-app-security/what-is-cloud-app-security)

![Tableau de bord Cloud App Security](../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png)

## <a name="additional-resources"></a>Ressources supplémentaires

Ces articles et guides fournissent des informations normatives supplémentaires pour la sécurisation de Microsoft 365 environnement :

- Conseils de sécurité Microsoft pour les [campagnes électorales,](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) les organisations à but non lucratif et d’autres organisations flexibles (vous pouvez utiliser ces recommandations dans n’importe quel environnement, en particulier les environnements cloud uniquement)

- [Stratégies et configurations de](microsoft-365-policies-configurations.md) sécurité recommandées pour les identités et les appareils (ces recommandations incluent de l’aide pour les environnements AD FS)
