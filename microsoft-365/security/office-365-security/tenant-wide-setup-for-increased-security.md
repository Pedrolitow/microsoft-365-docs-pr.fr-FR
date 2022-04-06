---
title: Configurer votre locataire Microsoft 365 pour renforcer la sécurité
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 10/11/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: 8d274fe3-db51-4107-ba64-865e7155b355
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: Cette rubrique vous dirige vers la configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de Microsoft 365 environnement.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 94da7316c5e749cf6dcc5e038c185bea4790765f
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682876"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Configurer votre locataire Microsoft 365 pour renforcer la sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cette rubrique vous dirige vers la configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de Microsoft 365 environnement. Vos besoins en matière de sécurité peuvent nécessiter plus ou moins de sécurité. Utilisez ces recommandations comme point de départ.

## <a name="check-office-365-secure-score"></a>Vérifier Office 365 secure score

Office 365 Secure Score analyse la sécurité de votre organisation en fonction de vos activités et paramètres de sécurité habituels et affecte un score. Commencez par prendre note de votre score actuel. L’ajustement de certains paramètres à l’échelle du client augmente votre score. L’objectif n’est pas d’atteindre le score maximum, mais de prendre en compte les opportunités de protection de votre environnement qui n’affectent pas la productivité de vos utilisateurs. Voir [Score de sécurité Microsoft](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>Régler les stratégies de gestion des menaces dans Microsoft 365 Defender web

Le portail Microsoft 365 Defender inclut des fonctionnalités qui protègent votre environnement. Il inclut également des rapports et des tableaux de bord que vous pouvez utiliser pour surveiller et prendre des mesures. Certains domaines sont des configurations de stratégie par défaut. Certains domaines n’incluent pas de stratégies ou de règles par défaut. Consultez ces stratégies sous **Stratégies de collaboration** \> & courrier électronique **&** \> stratégies de menace pour régler les paramètres de gestion des menaces pour un environnement plus sécurisé.

|Zone|Stratégie par défaut ?|Recommandation|
|---|---|---|
|**Anti-hameçonnage**|Oui|Configurez la stratégie anti-hameçonnage par défaut comme décrit ici : [Configurez les paramètres de protection anti-hameçonnage dans EOP et Defender pour Office 365](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365). <p> Plus d’informations : <ul><li>[Stratégies anti-hameçonnage dans Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[Paramètres de stratégie anti-hameçonnage recommandés dans Microsoft Defender pour Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [Perspicacité de l'usurpation d'identité](impersonation-insight.md)</li><li>[Informations sur l’intelligence contre l’usurpation d’adresse dans EOP](learn-about-spoof-intelligence.md)</li><li>[Gérez la liste d’accès au client autoriser/bloquer](tenant-allow-block-list.md).</li></ul>|
|**Moteur anti-programme malveillant**|Oui|Configurez la stratégie anti-programme malveillant par défaut comme décrit ici : [Configurer les paramètres de protection anti-programme malveillant dans EOP](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> Plus d’informations : <ul><li>[Protection contre les programmes malveillants](anti-malware-protection.md)</li><li>[Paramètres de stratégie anti-programme malveillant recommandés](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[Configurer des stratégies anti-programme malveillant](configure-anti-malware-policies.md)</li></ul>|
|**Pièces jointes sécurisées dans Defender pour Office 365**|Non|Configurez les paramètres globaux des pièces jointes Coffre et créez une stratégie de pièces jointes Coffre comme décrit ici : [Configurer les paramètres de pièces jointes Coffre dans Microsoft Defender pour Office 365](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> Plus d’informations : <ul><li>[Paramètres recommandés Coffre pièces jointes](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[Coffre pièces jointes dans Microsoft Defender pour Office 365](safe-attachments.md)</li><li>[Définir des stratégies de pièces jointes fiables](set-up-safe-attachments-policies.md)</li><li>[Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Documents sécurisés dans Microsoft 365 E5](safe-docs.md)</li></ul>|
|**Coffre liens dans Microsoft Defender pour Office 365**|Non|Configurez les paramètres globaux des liens Coffre et créez une stratégie de liens Coffre comme décrit ici : Configurer les paramètres de liens Coffre dans [Microsoft Defender pour Office 365](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> Plus d’informations : <ul><li>[Paramètres Coffre liens recommandés](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[Configuration des stratégies de liens fiables](set-up-safe-links-policies.md)</li><li>[Coffre liens dans Microsoft Defender pour Office 365](safe-links.md)</li><li>[Configurer les paramètres globaux pour Coffre liens vers Microsoft Defender pour Office 365](configure-global-settings-for-safe-links.md)</li></ul>|
|**Anti-courrier indésirable (filtrage du courrier)**|Oui|Configurez la stratégie anti-courrier indésirable par défaut comme décrit ici : [Configurer les paramètres de protection anti-courrier indésirable dans EOP](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> Plus d’informations : <ul><li>[Paramètres de stratégie anti-courrier indésirable recommandés](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[Protection contre le courrier indésirable dans EOP](anti-spam-protection.md)</li><li>[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)</li></ul>|
|***Authentification de messagerie***|Oui|L’authentification de messagerie utilise des enregistrements DNS pour ajouter des informations vérifiables aux messages électroniques concernant la source et l’expéditeur du message. Microsoft 365 configure automatiquement l’authentification de messagerie électronique pour son domaine par défaut (onmicrosoft.com), mais les administrateurs Microsoft 365 peuvent également configurer l’authentification de messagerie pour les domaines personnalisés. Trois méthodes d’authentification sont utilisées : <ul><li>Sender Policy Framework (ou SPF).</li><ul><li>Pour l’installation, [voir Configurer SPF dans Microsoft 365 pour empêcher l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>Voir [Utiliser DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).</li><li>Une fois que vous avez configuré DKIM, activez-le dans le Microsoft 365 Defender web.</li></ul><li>DMARC (Domain-based Message Authentication, Reporting, and Conformance).</li><ul><li>Pour le programme d’installation [de DMARC, utilisez DMARC pour valider les messages Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|

> [!NOTE]
> Pour les déploiements non standard de SPF, les déploiements hybrides et la résolution des problèmes : comment [Microsoft 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>Afficher les tableaux de bord et les rapports dans le portail Microsoft 365 Defender web

Consultez ces rapports et tableaux de bord pour en savoir plus sur l’état de votre environnement. Les données de ces rapports s’enrichiront à mesure que votre organisation utilisera Office 365 services. Pour l’instant, familiarisez-vous avec ce que vous pouvez surveiller et prendre des mesures.

|Tableau de bord|Description|
|---|---|
|Rapports de sécurité de messagerie|Ces rapports sont disponibles dans Exchange Online Protection. Pour plus d’informations, [consultez les rapports de sécurité de messagerie dans le portail Microsoft 365 Defender messagerie](view-email-security-reports.md).|
|Rapports Defender for Office 365|Les rapports sont disponibles uniquement dans Defender pour Office 365. Pour plus d’informations, [voir View Defender pour Office 365 rapports dans le portail Microsoft 365 Defender web](view-reports-for-mdo.md).|
|Rapports et informations sur le flux de messagerie|Ces rapports et informations sont disponibles dans le Centre d’administration Exchange(EAC). Pour plus d’informations, voir [Rapports de flux de messagerie](/exchange/monitoring/mail-flow-reports/mail-flow-reports) et [Informations sur le flux de messagerie](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[Threat Explorer (et détections en temps réel)](threat-explorer.md)|Si vous examinez ou rencontrez une attaque contre votre client, utilisez l’Explorateur (ou les détections en temps réel) pour analyser les menaces. L’Explorateur (et le rapport de détections en temps réel) vous indique le volume d’attaques au fil du temps, et vous pouvez analyser ces données par familles de menaces, infrastructure d’attaquant, etc. Vous pouvez également marquer tout message suspect pour la liste Incidents.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Configurer des paramètres Exchange Online à l’échelle du client

Voici quelques paramètres supplémentaires qui sont recommandés.

|Zone|Recommandation|
|---|---|
|**Règles de flux de messagerie** (également appelées règles de transport)|Ajoutez une règle de flux de messagerie pour vous protéger contre les ransomware en bloquant les types de fichiers exécutables Office types de fichiers contenant des macros. Pour plus d’informations, voir [Utiliser des règles de flux de messagerie pour inspecter les pièces jointes des messages Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Consultez les rubriques supplémentaires ci-après : <ul><li>[Se protéger contre les rançongiciels](../../admin/security-and-compliance/secure-your-business-data.md#5-protect-against-ransomware)</li><li>[Protection contre les programmes malveillants et ransomware dans Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Récupérer d’une attaque par ransomware dans Office 365](recover-from-ransomware.md)</li></ul> <p> Créez une règle de flux de messagerie pour empêcher le forwarding automatique du courrier électronique vers des domaines externes. Pour plus d’informations, voir [Atténuation des règles de forwarding externe client avec le score de sécurisation](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> Plus d’informations : [Règles de flux de messagerie (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Authentification moderne**|L’authentification moderne est une condition préalable à l’utilisation de l’authentification multifacteur (MFA). L’mf est recommandée pour sécuriser l’accès aux ressources cloud, y compris la messagerie. <p> Consultez les rubriques ci-après : <ul><li>[Activation ou désactivation de l’authentification moderne dans Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype Entreprise Online : activer votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> L’authentification moderne est activée par défaut pour Office clients 2016, SharePoint Online et OneDrive Entreprise. <p> Plus d’informations : Fonctionnement de l’authentification [moderne Office applications clientes 2013 Office 2016](../../enterprise/modern-auth-for-office-2013-and-2016.md)|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Configurer des stratégies de partage à l’échelle du client dans SharePoint’administration centrale

Recommandations de Microsoft pour la configuration SharePoint sites d’équipe à des niveaux de protection croissants, en commençant par la protection de référence. Pour plus d’informations, voir [Recommandations de stratégie pour sécuriser SharePoint sites et fichiers.](sharepoint-file-access-policies.md)

SharePoint sites d’équipe configurés au niveau de référence autorisent le partage de fichiers avec des utilisateurs externes à l’aide de liens d’accès anonyme. Cette approche est recommandée au lieu d’envoyer des fichiers par courrier électronique.

Pour prendre en charge les objectifs de protection de référence, configurez les stratégies de partage à l’échelle du client comme recommandé ici. Les paramètres de partage pour des sites individuels peuvent être plus restrictifs que cette stratégie à l’échelle du client, mais pas plus permissifs.

|Zone|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Partage** (SharePoint Online et OneDrive Entreprise)|Oui|Le partage externe est activé par défaut. Ces paramètres sont recommandés : <ul><li>Autoriser le partage à des utilisateurs externes authentifiés et l’utilisation de liens d’accès anonyme (paramètre par défaut).</li><li>Les liens d’accès anonyme expirent dans ce nombre de jours. Entrez un nombre, si vous le souhaitez, par exemple 30 jours.</li><li>Type de lien par défaut : sélectionnez Interne (personnes de l’organisation uniquement). Les utilisateurs qui souhaitent partager à l’aide de liens anonymes doivent choisir cette option dans le menu de partage.</li></ul> <p> Plus d’informations : [Vue d’ensemble du partage externe](/sharepoint/external-sharing-overview)|

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

- Utilisez PowerShell, voir [Bloquer les applications qui n’utilisent pas l’authentification moderne](/mem/intune/protect/app-modern-authentication-block).
- Configurez cette configuration dans le <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a> sur la page « Accès aux appareils » — « Contrôler l’accès à partir d’applications qui n’utilisent pas l’authentification moderne ». Sélectionnez Bloquer.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>Mise en place de Defender pour les applications cloud Sécurité des applications cloud Office 365

Utilisez Sécurité des applications cloud Office 365 pour évaluer les risques, pour alerter sur une activité suspecte et pour prendre automatiquement des mesures. Nécessite Office 365 E5 plan.

Vous pouvez également utiliser Microsoft Defender pour les applications cloud pour obtenir une visibilité plus approfondie même après l’octroi d’un accès, des contrôles complets et une protection améliorée pour toutes vos applications cloud, y compris Office 365.

Étant donné que cette solution recommande le plan EMS E5, nous vous recommandons de commencer par Defender pour les applications cloud afin de pouvoir l’utiliser avec d’autres applications SaaS dans votre environnement. Commencez par les stratégies et paramètres par défaut.

Plus d’informations :

- [Déployer Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Plus d’informations sur Microsoft Defender pour les applications cloud](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Qu’est-ce que Defender pour les applications cloud ?](/cloud-app-security/what-is-cloud-app-security)

![Tableau de bord Defender pour les applications cloud.](../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png)

## <a name="additional-resources"></a>Ressources supplémentaires

Ces articles et guides fournissent des informations normatives supplémentaires pour la sécurisation de Microsoft 365 environnement :

- [Conseils de sécurité Microsoft pour les campagnes électorales,](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) les organisations à but non lucratif et d’autres organisations flexibles (vous pouvez utiliser ces recommandations dans n’importe quel environnement, en particulier les environnements cloud uniquement)

- [Stratégies et configurations de sécurité recommandées pour les identités](microsoft-365-policies-configurations.md) et les appareils (ces recommandations incluent de l’aide pour les environnements AD FS)
