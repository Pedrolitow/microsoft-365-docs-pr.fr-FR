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
description: Cette rubrique vous propose une configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de votre environnement Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 99086bbe28135a3f504986a81cfd5cff303df95c
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50920311"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Configurer votre client Microsoft 365 pour une sécurité accrue

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Cette rubrique vous propose une configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de votre environnement Microsoft 365. Vos besoins en matière de sécurité peuvent nécessiter plus ou moins de sécurité. Utilisez ces recommandations comme point de départ.

## <a name="check-office-365-secure-score"></a>Vérifier le score de sécurité Office 365

Le niveau de sécurité Office 365 analyse la sécurité de votre organisation en fonction de vos activités régulières et de vos paramètres de sécurité et affecte un score. Commencez par prendre note de votre score actuel. L’ajustement de certains paramètres à l’échelle du client augmente votre score. L’objectif n’est pas d’atteindre le score maximum, mais de prendre en compte les opportunités de protection de votre environnement qui n’affectent pas la productivité de vos utilisateurs. Voir [Microsoft Secure Score](../mtp/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-security-center"></a>Régler les stratégies de gestion des menaces dans le Centre de sécurité Microsoft 365

Le Centre de sécurité Microsoft 365 inclut des fonctionnalités qui protègent votre environnement. Il inclut également des rapports et des tableaux de bord que vous pouvez utiliser pour surveiller et prendre des mesures. Certains domaines sont des configurations de stratégie par défaut. Certains domaines n’incluent pas de stratégies ou de règles par défaut. Consultez ces stratégies sous gestion des menaces pour régler les paramètres de gestion des menaces pour un environnement plus sécurisé.

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Anti-hameçonnage**|Oui|Si vous avez un domaine personnalisé, configurez la stratégie anti-hameçonnage par défaut pour protéger les comptes de messagerie de vos utilisateurs les plus précieux, tels que votre PDG, et pour protéger votre domaine. <p> Consultez les stratégies anti-hameçonnage dans [Office 365](set-up-anti-phishing-policies.md) et consultez Configurer des stratégies [anti-hameçonnage](configure-anti-phishing-policies-eop.md) dans EOP ou Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour [Office 365.](configure-atp-anti-phishing-policies.md)|
|**Moteur anti-programme malveillant**|Oui| Modifiez la stratégie par défaut : <ul><li>Filtre types de pièces jointes courants : sélectionner sur</li></ul> <p> Vous pouvez également créer des stratégies de filtrage des programmes malveillants personnalisées et les appliquer à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. <p> Plus d’informations : <ul><li>[Protection contre les programmes malveillants](anti-malware-protection.md)</li><li>[Configurer des stratégies anti-programme malveillant](configure-anti-malware-policies.md)</li></ul>|
|**Pièces jointes sécurisées dans Microsoft Defender pour Office 365**|Non|Dans la page principale des pièces jointes sécurisées, cliquez sur **Paramètres** globaux et activer ce paramètre : <ul><li>**Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams**</li></ul> <p> Créez une stratégie de pièces jointes sécurisées avec les paramètres ci-après : <ul><li> **Bloquer :** sélectionnez **Bloquer en** tant que réponse anti-programme malveillant inconnue.</li><li>**Activer la redirection**: cochez cette case et entrez une adresse de messagerie, telle qu’un compte d’administrateur ou de mise en quarantaine.</li><li>**Appliquez la sélection ci-dessus si** l’analyse des programmes malveillants pour les pièces jointes arrive à arriver à son arrivée ou si une erreur se produit : cochez cette case.</li><li>**_Appliqué à_*: **le domaine du destinataire est votre** \> domaine.</li></ul> <p> Plus d’informations : [Pièces jointes sécurisées pour SharePoint, OneDrive](atp-for-spo-odb-and-teams.md) et Microsoft Teams et [configurer des stratégies de pièces jointes sécurisées](set-up-atp-safe-attachments-policies.md)|
|**Liens sécurisés dans Microsoft Defender pour Office 365**|Oui|Dans la page principale de liens sécurisés, cliquez **sur Paramètres globaux**: <ul><li>**Utilisez la fonction Liens sécurisés dans : applications Office 365**: vérifiez que ce paramètre est allumé.</li><li>**Ne pas suivre le moment où les utilisateurs cliquent sur** Liens sécurisés : désactiver ce paramètre pour suivre les clics des utilisateurs.</li></ul> <p> Créez une stratégie de liens sécurisés avec les paramètres suivants : <ul><li>**Sélectionnez l’action pour les URL potentiellement malveillantes inconnues** dans les messages : Vérifiez que ce paramètre est **sur**.</li><li>**Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft Teams**: vérifiez que ce paramètre est **sur**.</li><li>**Appliquez l’analyse des URL en** temps réel pour les liens suspects et les liens pointant vers des fichiers : cochez cette case.</li><li>**Attendez que l’analyse des URL se termine avant de remettre le message**: cochez cette case.</li><li>**Appliquer des liens sûrs aux messages électroniques envoyés au sein** de l’organisation : cochez cette case</li><li>**N’autorisez pas les utilisateurs à cliquer sur l’URL d’origine**: cochez cette case.</li><li>**Appliqué à**: **le domaine du destinataire est votre** \> domaine.</li></ul> <p> Plus d’informations : [Configurer des stratégies de liens sécurisés.](set-up-atp-safe-links-policies.md)|
|**Anti-courrier indésirable (filtrage du courrier)**|Oui| Ce qu’il faut surveiller : <ul><li>Trop de courrier indésirable : choisissez les paramètres personnalisés et modifiez la stratégie de filtrage du courrier indésirable par défaut.</li><li>Veille contre l’usurpation d’adresse : examinez les expéditeurs qui usurpent votre domaine. Bloquez ou autorisez ces expéditeurs.</li></ul> <p> Plus d’informations : [Microsoft 365 Email Anti-Spam Protection](anti-spam-protection.md).|
|***Authentification de messagerie***|Oui|L’authentification de messagerie utilise un DNS (Domain Name System) pour ajouter des informations vérifiables aux messages électroniques concernant l’expéditeur d’un e-mail. Microsoft 365 définit l’authentification de messagerie pour son domaine par défaut (onmicrosoft.com), mais les administrateurs Microsoft 365 peuvent également utiliser l’authentification de messagerie pour les domaines personnalisés. Trois méthodes d’authentification sont utilisées : <ul><li>Sender Policy Framework (ou SPF).</li><ul><li>Pour la configuration, voir [Configurer SPF dans Microsoft 365 pour empêcher l’usurpation.](set-up-spf-in-office-365-to-help-prevent-spoofing.md)</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>Voir [Utiliser DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé.](use-dkim-to-validate-outbound-email.md)</li><li>Une fois que vous avez configuré DKIM, activez-le dans le centre de sécurité.</li></ul><li>DMARC (Domain-based Message Authentication, Reporting, and Conformance).</li><ul><li>Pour le programme d’installation [de DMARC, utilisez DMARC pour valider le courrier électronique dans Microsoft 365.](use-dmarc-to-validate-email.md)</li></ul></ul>|
|

> [!NOTE]
> Pour les déploiements non standard de SPF, les déploiements hybrides et la résolution des problèmes : comment [Microsoft 365 utilise SPF (Sender Policy Framework)](how-office-365-uses-spf-to-prevent-spoofing.md)pour empêcher l’usurpation.

## <a name="view-dashboards-and-reports-in-the-security-and-compliance-centers"></a>Afficher les tableaux de bord et les rapports dans les centres de sécurité et de conformité

Consultez ces rapports et tableaux de bord pour en savoir plus sur l’état de votre environnement. Les données de ces rapports s’enrichiront à mesure que votre organisation utilisera les services Office 365. Pour l’instant, familiarisez-vous avec ce que vous pouvez surveiller et prendre des mesures. Pour plus d’informations, voir : Rapports dans les centres de sécurité et [conformité Microsoft 365.](../../compliance/reports-in-security-and-compliance.md)

****

|Tableau de bord|Description|
|---|---|
|[Tableau de bord de gestion des menaces](security-dashboard.md)|Dans la **section** Gestion des menaces du Centre de sécurité, utilisez ce tableau de bord pour voir les menaces qui ont déjà été gérées et comme un outil pratique pour signaler aux décideurs d’entreprise ce que les fonctionnalités d’examen et de réponse aux menaces ont déjà fait pour sécuriser votre entreprise.|
|[Threat Explorer (et détections en temps réel)](threat-explorer.md)|Il se trouve également dans la section **Gestion des** menaces du centre de sécurité. Si vous examinez ou rencontrez une attaque contre votre client, utilisez l’Explorateur (ou les détections en temps réel) pour analyser les menaces. L’Explorateur (et le rapport de détections en temps réel) vous indique le volume d’attaques au fil du temps, et vous pouvez analyser ces données par familles de menaces, infrastructure d’attaquant, etc. Vous pouvez également marquer tout message suspect pour la liste Incidents.|
|Rapports — Tableau de bord|Dans la section **Rapports** du Centre de sécurité, affichez les rapports d’audit pour vos organisations SharePoint Online et Exchange Online. Vous pouvez également accéder aux rapports de connexion des utilisateurs Azure Active Directory (Azure AD), aux rapports d’activité des utilisateurs et au journal d’audit Azure AD à partir de la page Afficher les **rapports.**|
|

![Tableau de bord du Centre de sécurité](../../media/870ab776-36d2-49c7-b615-93b2bc42fce5.png)

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Configurer des paramètres supplémentaires à l’échelle du client Exchange Online

De nombreux contrôles de sécurité et de protection dans le Centre d’administration Exchange sont également inclus dans le centre de sécurité. Vous n’avez pas besoin de les configurer aux deux endroits. Voici quelques paramètres supplémentaires qui sont recommandés.

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Flux de messagerie** (règles de flux de messagerie, également appelées règles de transport)|Non|Ajoutez une règle de flux de messagerie pour vous protéger contre les ransomware en bloquant les types de fichiers exécutables et les types de fichiers Office qui contiennent des macros. Pour plus d’informations, voir [Utiliser des règles de flux de messagerie pour inspecter les pièces jointes des messages dans Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments) <p> Consultez les rubriques supplémentaires ci-après : <ul><li>[Se protéger contre les rançongiciels](../../admin/security-and-compliance/secure-your-business-data.md#5-protect-against-ransomware)</li><li>[Protection contre les programmes malveillants et les ransomware dans Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Récupérer d’une attaque par ransomware dans Office 365](recover-from-ransomware.md)</li></ul> <p> Créez une règle de flux de messagerie pour empêcher le forwarding automatique du courrier électronique vers des domaines externes. Pour plus d’informations, voir [Atténuation des règles de forwarding externe client avec le score de sécurisation.](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score) <p> Plus d’informations : [Règles de flux de messagerie (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Activer l’authentification moderne**|Non|L’authentification moderne est une condition préalable à l’utilisation de l’authentification multifacteur (MFA). L’mf est recommandée pour sécuriser l’accès aux ressources cloud, y compris la messagerie. <p> Consultez les rubriques ci-après : <ul><li>[Activation ou désactivation de l’authentification moderne dans Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype Entreprise Online : activer votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> L’authentification moderne est activée par défaut pour les clients Office 2016, SharePoint Online et OneDrive Entreprise. <p> Plus d’informations : Fonctionnement de l’authentification moderne pour les applications [clientes Office 2013 et Office 2016](../../enterprise/modern-auth-for-office-2013-and-2016.md)|
|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Configurer des stratégies de partage à l’échelle du client dans le Centre d’administration SharePoint

Recommandations de Microsoft pour la configuration des sites d’équipe SharePoint à des niveaux de protection croissants, en commençant par la protection de référence. Pour plus d’informations, voir [recommandations de stratégie pour la sécurisation des sites et des fichiers SharePoint.](sharepoint-file-access-policies.md)

Les sites d’équipe SharePoint configurés au niveau de référence autorisent le partage de fichiers avec des utilisateurs externes à l’aide de liens d’accès anonyme. Cette approche est recommandée au lieu d’envoyer des fichiers par courrier électronique.

Pour prendre en charge les objectifs de protection de référence, configurez les stratégies de partage à l’échelle du client comme recommandé ici. Les paramètres de partage pour des sites individuels peuvent être plus restrictifs que cette stratégie à l’échelle du client, mais pas plus permissifs.

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Partage** (SharePoint Online et OneDrive Entreprise)|Oui|Le partage externe est activé par défaut. Ces paramètres sont recommandés : <ul><li>Autoriser le partage à des utilisateurs externes authentifiés et l’utilisation de liens d’accès anonyme (paramètre par défaut).</li><li>Les liens d’accès anonyme expirent dans ce nombre de jours. Entrez un nombre, si vous le souhaitez, par exemple 30 jours.</li><li>Type de lien par défaut : sélectionnez Interne (personnes de l’organisation uniquement). Les utilisateurs qui souhaitent partager à l’aide de liens anonymes doivent choisir cette option dans le menu de partage.</li></ul> <p> Plus d’informations : [Vue d’ensemble du partage externe](/sharepoint/external-sharing-overview)|
|

Le Centre d’administration SharePoint et le Centre d’administration OneDrive Entreprise incluent les mêmes paramètres. Les paramètres de l’un ou l’autre centre d’administration s’appliquent aux deux.

## <a name="configure-settings-in-azure-active-directory"></a>Configurer les paramètres dans Azure Active Directory

N’oubliez pas de visiter ces deux zones dans Azure Active Directory pour terminer la configuration à l’échelle du client pour des environnements plus sécurisés.

### <a name="configure-named-locations-under-conditional-access"></a>Configurer des emplacements nommés (sous accès conditionnel)

Si votre organisation inclut des bureaux avec un accès réseau sécurisé, ajoutez les plages d’adresses IP de confiance à Azure Active Directory en tant qu’emplacements nommés. Cette fonctionnalité permet de réduire le nombre de faux positifs signalés pour les événements de risque de sign-in.

Voir : [Emplacements nommés dans Azure Active Directory](/azure/active-directory/active-directory-named-locations)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Bloquer les applications qui ne permettent pas l’authentification moderne

L’authentification multifacteur nécessite des applications qui la prise en charge de l’authentification moderne. Les applications qui ne permettent pas l’authentification moderne ne peuvent pas être bloquées à l’aide de règles d’accès conditionnel.

Pour les environnements sécurisés, assurez-vous de désactiver l’authentification pour les applications qui ne la prisent pas en charge de l’authentification moderne. Vous pouvez le faire dans Azure Active Directory avec un contrôle qui sera bientôt disponible.

En attendant, utilisez l’une des méthodes suivantes pour effectuer cette tâche pour SharePoint Online et OneDrive Entreprise :

- Utilisez PowerShell, voir [Bloquer les applications qui n’utilisent pas l’authentification moderne (ADAL).](/mem/intune/protect/app-modern-authentication-block)

- Configurez cette configuration dans le Centre d’administration SharePoint sur la page « Accès aux appareils » — « Contrôler l’accès à partir d’applications qui n’utilisent pas l’authentification moderne ». Sélectionnez Bloquer.

## <a name="get-started-with-cloud-app-security-or-office-365-cloud-app-security"></a>Prendre en charge Cloud App Security ou Office 365 Cloud App Security

Utilisez Office 365 Cloud App Security pour évaluer les risques, pour alerter sur les activités suspectes et pour prendre automatiquement des mesures. Nécessite une plan Office 365 E5.

Vous pouvez également utiliser Microsoft Cloud App Security pour obtenir une visibilité plus approfondie même une fois l’accès accordé, des contrôles complets et une protection améliorée pour toutes vos applications cloud, y compris Office 365.

Étant donné que cette solution recommande le plan EMS E5, nous vous recommandons de commencer par Cloud App Security afin de pouvoir l’utiliser avec d’autres applications SaaS dans votre environnement. Commencez par les stratégies et paramètres par défaut.

Plus d’informations :

- Rubrique relative au [déploiement de Cloud App Security](/cloud-app-security/getting-started-with-cloud-app-security)

- Rubrique relative aux [informations supplémentaires concernant Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security)

- [Qu’est-ce que Cloud App Security ?](/cloud-app-security/what-is-cloud-app-security)

![Tableau de bord Cloud App Security](../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png)

## <a name="additional-resources"></a>Ressources supplémentaires

Ces articles et guides fournissent des informations normatives supplémentaires pour la sécurisation de votre environnement Microsoft 365 :

- Conseils de sécurité Microsoft pour les [campagnes électorales,](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) les organisations à but non lucratif et d’autres organisations flexibles (vous pouvez utiliser ces recommandations dans n’importe quel environnement, en particulier les environnements cloud uniquement)

- [Stratégies et configurations de](microsoft-365-policies-configurations.md) sécurité recommandées pour les identités et les appareils (ces recommandations incluent de l’aide pour les environnements AD FS)