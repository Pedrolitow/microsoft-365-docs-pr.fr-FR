---
title: Configurer votre locataire Microsoft 365 pour renforcer la sécurité
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 04/06/2022
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
description: Cette rubrique vous guide tout au long de la configuration recommandée pour les paramètres à l’échelle du locataire qui affectent la sécurité de votre environnement Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a3b4d0580a8807dd9801b082a8326e4a17b65f5f
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2022
ms.locfileid: "66773134"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Configurer votre locataire Microsoft 365 pour renforcer la sécurité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cette rubrique vous guide tout au long de la configuration recommandée pour les paramètres à l’échelle du locataire qui affectent la sécurité de votre environnement Microsoft 365. Vos besoins en matière de sécurité peuvent nécessiter une sécurité plus ou moins importante. Utilisez ces recommandations comme point de départ.

## <a name="check-office-365-secure-score"></a>Vérifier Office 365 degré de sécurisation

Office 365 degré de sécurisation analyse la sécurité de votre organisation en fonction de vos activités régulières et de vos paramètres de sécurité et attribue un score. Commencez par prendre note de votre score actuel. L’ajustement de certains paramètres à l’échelle du locataire augmente votre score. L’objectif n’est pas d’atteindre le score maximal, mais d’être conscient des opportunités de protéger votre environnement qui n’affectent pas négativement la productivité de vos utilisateurs. Voir [Microsoft Secure Score](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>Paramétrer les stratégies de gestion des menaces dans le portail Microsoft 365 Defender

Le portail Microsoft 365 Defender inclut des fonctionnalités qui protègent votre environnement. Il inclut également des rapports et des tableaux de bord que vous pouvez utiliser pour surveiller et prendre des mesures. Certaines zones sont associées à des configurations de stratégie par défaut. Certaines zones n’incluent pas de stratégies ou de règles par défaut. Consultez ces stratégies sous **Email &** stratégies de collaboration \> **& règles Stratégies** \> de menace pour paramétrer les paramètres de gestion des menaces pour un environnement plus sécurisé.

|Zone|Stratégie par défaut ?|Recommandation|
|---|---|---|
|**Anti-hameçonnage**|Oui|Configurez la stratégie anti-hameçonnage par défaut comme décrit ici : [Configurez les paramètres de protection anti-hameçonnage dans EOP et Defender pour Office 365](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365). <p> Plus d’informations : <ul><li>[Stratégies anti-hameçonnage dans Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[Paramètres de stratégie anti-hameçonnage recommandés dans Microsoft Defender pour Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [Perspicacité de l'usurpation d'identité](impersonation-insight.md)</li><li>[Informations sur l’intelligence d’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md)</li><li>[Gérer la liste d’autorisations/de blocs du locataire](tenant-allow-block-list.md).</li></ul>|
|**Moteur anti-programme malveillant**|Oui|Configurez la stratégie anti-programme malveillant par défaut comme décrit ici : [Configurez les paramètres de protection contre les programmes malveillants dans EOP](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> Plus d’informations : <ul><li>[Protection contre les programmes malveillants](anti-malware-protection.md)</li><li>[Paramètres de stratégie anti-programme malveillant recommandés](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[Configurer des stratégies anti-programme malveillant](configure-anti-malware-policies.md)</li></ul>|
|**Pièces jointes sécurisées dans Defender pour Office 365**|Non|Configurez les paramètres globaux pour les pièces jointes sécurisées et créez une stratégie de pièces jointes sécurisées comme décrit ici : [Configurer les paramètres des pièces jointes sécurisées dans Microsoft Defender pour Office 365](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> Plus d’informations : <ul><li>[Paramètres de pièces jointes fiables recommandés](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[Pièces jointes sécurisées dans Microsoft Defender pour Office 365](safe-attachments.md)</li><li>[Définir des stratégies de pièces jointes fiables](set-up-safe-attachments-policies.md)</li><li>[Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Documents sécurisés dans Microsoft 365 E5](safe-docs.md)</li></ul>|
|**Liens sécurisés dans Microsoft Defender pour Office 365**|Non|Créez une stratégie liens sécurisés comme décrit ici : [configurez les paramètres liens fiables dans Microsoft Defender pour Office 365](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> Plus d’informations : <ul><li>[Paramètres de liens fiables recommandés](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[Configuration des stratégies de liens fiables](set-up-safe-links-policies.md)</li><li>[Liens sécurisés dans Microsoft Defender pour Office 365](safe-links.md)</li></ul>|
|**Anti-courrier indésirable (filtrage de courrier)**|Oui|Configurer la stratégie anti-courrier indésirable par défaut comme décrit ici : [Configurer les paramètres de protection anti-courrier indésirable dans EOP](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> Plus d’informations : <ul><li>[Paramètres de stratégie anti-courrier indésirable recommandés](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[Protection anti-courrier indésirable dans EOP](anti-spam-protection.md)</li><li>[Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection](configure-your-spam-filter-policies.md)</li></ul>|
|***Authentification Email***|Oui|Email’authentification utilise des enregistrements DNS pour ajouter des informations vérifiables aux messages électroniques concernant la source et l’expéditeur du message. Microsoft 365 configure automatiquement l’authentification par e-mail pour son domaine par défaut (onmicrosoft.com), mais les administrateurs microsoft 365 peuvent également configurer l’authentification par e-mail pour les domaines personnalisés. Trois méthodes d’authentification sont utilisées : <ul><li>Framework de stratégie d’expéditeur (ou SPF).</li><ul><li>Pour l’installation, consultez [Configurer SPF dans Microsoft 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>Consultez [Utiliser DKIM pour valider les e-mails sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).</li><li>Une fois que vous avez configuré DKIM, activez-le dans le portail Microsoft 365 Defender.</li></ul><li>Authentification, création de rapports et conformité des messages basée sur le domaine (DMARC).</li><ul><li>Pour la configuration DMARC [, utilisez DMARC pour valider les e-mails dans Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|

> [!NOTE]
> Pour les déploiements non standard de SPF, les déploiements hybrides et la résolution des problèmes : [comment Microsoft 365 utilise Sender Policy Framework (SPF) pour empêcher l’usurpation d’identité](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>Afficher les tableaux de bord et les rapports dans le portail Microsoft 365 Defender

Consultez ces rapports et tableaux de bord pour en savoir plus sur l’intégrité de votre environnement. Les données contenues dans ces rapports s’enrichiront à mesure que votre organisation utilisera Office 365 services. Pour l’instant, familiarisez-vous avec ce que vous pouvez surveiller et prendre des mesures.

|Tableau de bord|Description|
|---|---|
|Email rapports de sécurité|Ces rapports sont disponibles dans Exchange Online Protection. Pour plus d’informations, consultez [Afficher les rapports de sécurité par e-mail dans le portail Microsoft 365 Defender](view-email-security-reports.md).|
|Rapports Defender pour Office 365|Les rapports sont disponibles uniquement dans Defender pour Office 365. Pour plus d’informations, consultez [Afficher les rapports Defender pour Office 365 dans le portail Microsoft 365 Defender](view-reports-for-mdo.md).|
|Rapports et insights de flux de courrier|Ces rapports et insights sont disponibles dans le Centre d’administration Exchange (EAC). Pour plus d’informations, consultez [les rapports de flux de courrier](/exchange/monitoring/mail-flow-reports/mail-flow-reports) et [les insights sur les flux de courrier](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[Threat Explorer (et détections en temps réel)](threat-explorer.md)|Si vous examinez ou rencontrez une attaque contre votre locataire, utilisez l’Explorateur (ou les détections en temps réel) pour analyser les menaces. L’Explorateur (et le rapport de détections en temps réel) vous indiquent le volume d’attaques au fil du temps, et vous pouvez analyser ces données par familles de menaces, infrastructure des attaquants, etc. Vous pouvez également marquer tout e-mail suspect pour la liste des incidents.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Configurer des paramètres supplémentaires Exchange Online à l’échelle du locataire

Voici quelques paramètres supplémentaires recommandés.

|Zone|Recommandation|
|---|---|
|**Règles de flux de messagerie** (également appelées règles de transport)|Ajoutez une règle de flux de messagerie pour vous protéger contre les ransomware en bloquant les types de fichiers exécutables et les types de fichiers Office qui contiennent des macros. Pour plus d’informations, consultez [Utiliser des règles de flux de courrier pour inspecter les pièces jointes des messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Consultez ces rubriques supplémentaires : <ul><li>[Se protéger contre les rançongiciels](../../admin/security-and-compliance/secure-your-business-data.md)</li><li>[Protection contre les programmes malveillants et les ransomwares dans Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Récupérer à la suite d’une attaque par ransomware dans Office 365](recover-from-ransomware.md)</li></ul> <p> Créez une règle de flux de messagerie pour empêcher le transfert automatique des e-mails vers des domaines externes. Pour plus d’informations, consultez [Atténuation des règles de transfert externe du client avec un score sécurisé](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> Plus d’informations : [Règles de flux de courrier (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Authentification moderne**|L’authentification moderne est un prérequis pour l’utilisation de l’authentification multifacteur (MFA). L’authentification multifacteur est recommandée pour sécuriser l’accès aux ressources cloud, y compris les e-mails. <p> Consultez les rubriques suivantes : <ul><li>[Activation ou désactivation de l’authentification moderne dans Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype Entreprise Online : Activer votre locataire pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> L’authentification moderne est activée par défaut pour les clients Office 2016, SharePoint Online et OneDrive Entreprise. <p> Informations supplémentaires : [Fonctionnement de l’authentification moderne pour les applications clientes Office 2013 et Office 2016](../../enterprise/modern-auth-for-office-2013-and-2016.md)|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Configurer des stratégies de partage à l’échelle du locataire dans le Centre d’administration SharePoint

Recommandations Microsoft pour la configuration des sites d’équipe SharePoint à des niveaux de protection croissants, en commençant par la protection de référence. Pour plus d’informations, consultez [les recommandations de stratégie pour la sécurisation des sites et fichiers SharePoint](sharepoint-file-access-policies.md).

Les sites d’équipe SharePoint configurés au niveau de la base de référence permettent de partager des fichiers avec des utilisateurs externes à l’aide de liens d’accès anonymes. Cette approche est recommandée au lieu d’envoyer des fichiers par e-mail.

Pour prendre en charge les objectifs de protection de base de référence, configurez les stratégies de partage à l’échelle du locataire, comme recommandé ici. Les paramètres de partage pour des sites individuels peuvent être plus restrictifs que cette stratégie à l’échelle du locataire, mais pas plus permissifs.

|Zone|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Partage** (SharePoint Online et OneDrive Entreprise)|Oui|Le partage externe est activé par défaut. Ces paramètres sont recommandés : <ul><li>Autoriser le partage aux utilisateurs externes authentifiés et l’utilisation de liens d’accès anonymes (paramètre par défaut).</li><li>Les liens d’accès anonyme expirent au bout de plusieurs jours. Entrez un nombre, si vous le souhaitez, par exemple 30 jours.</li><li>Type de lien par défaut : sélectionnez Interne (personnes de l’organisation uniquement). Les utilisateurs qui souhaitent partager à l’aide de liens anonymes doivent choisir cette option dans le menu de partage.</li></ul> <p> Plus d’informations : [Vue d’ensemble du partage externe](/sharepoint/external-sharing-overview)|

Le Centre d’administration SharePoint et OneDrive Entreprise centre d’administration incluent les mêmes paramètres. Les paramètres de l’un ou l’autre centre d’administration s’appliquent aux deux.

## <a name="configure-settings-in-azure-active-directory"></a>Configurer les paramètres dans Azure Active Directory

Veillez à visiter ces deux zones dans Azure Active Directory pour terminer la configuration à l’échelle du locataire pour des environnements plus sécurisés.

### <a name="configure-named-locations-under-conditional-access"></a>Configurer des emplacements nommés (sous accès conditionnel)

Si votre organisation inclut des bureaux disposant d’un accès réseau sécurisé, ajoutez les plages d’adresses IP approuvées à Azure Active Directory en tant qu’emplacements nommés. Cette fonctionnalité permet de réduire le nombre de faux positifs signalés pour les événements à risque de connexion.

Voir : [Emplacements nommés dans Azure Active Directory](/azure/active-directory/conditional-access/location-condition)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Bloquer les applications qui ne prennent pas en charge l’authentification moderne

L’authentification multifacteur nécessite des applications qui prennent en charge l’authentification moderne. Les applications qui ne prennent pas en charge l’authentification moderne ne peuvent pas être bloquées à l’aide de règles d’accès conditionnel.

Pour les environnements sécurisés, veillez à désactiver l’authentification pour les applications qui ne prennent pas en charge l’authentification moderne. Vous pouvez le faire dans Azure Active Directory avec un contrôle qui sera bientôt disponible.

En attendant, utilisez l’une des méthodes suivantes pour effectuer cette opération pour SharePoint Online et OneDrive Entreprise :

- Utilisez PowerShell, consultez [Bloquer les applications qui n’utilisent pas l’authentification moderne](/mem/intune/protect/app-modern-authentication-block).
- Configurez-le dans le <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a> sur la page « Accès des appareils » : « Contrôler l’accès à partir d’applications qui n’utilisent pas l’authentification moderne ». Choisissez Bloquer.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>Bien démarrer avec Defender pour Cloud Apps ou Sécurité des applications cloud Office 365

Utilisez Sécurité des applications cloud Office 365 pour évaluer les risques, pour alerter sur les activités suspectes et prendre automatiquement des mesures. Nécessite Office 365 E5 plan.

Vous pouvez également utiliser Microsoft Defender for Cloud Apps pour obtenir une visibilité plus approfondie même après l’octroi d’un accès, des contrôles complets et une protection améliorée pour toutes vos applications cloud, y compris Office 365.

Étant donné que cette solution recommande le plan EMS E5, nous vous recommandons de commencer par Defender pour Cloud Apps afin de pouvoir l’utiliser avec d’autres applications SaaS dans votre environnement. Commencez par les stratégies et les paramètres par défaut.

Plus d’informations :

- [Déployer Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Plus d’informations sur Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Qu’est-ce que Defender pour les applications cloud ?](/cloud-app-security/what-is-cloud-app-security)

:::image type="content" source="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png" alt-text="Tableau de bord Defender pour Cloud Apps" lightbox="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png":::

## <a name="additional-resources"></a>Ressources supplémentaires

Ces articles et guides fournissent des informations prescriptives supplémentaires pour sécuriser votre environnement Microsoft 365 :

- [Conseils de sécurité Microsoft pour les campagnes politiques, les organisations à but non lucratif et d’autres organisations agiles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) (vous pouvez utiliser ces recommandations dans n’importe quel environnement, en particulier dans les environnements cloud uniquement)

- [Stratégies et configurations de sécurité recommandées pour les identités et les appareils](microsoft-365-policies-configurations.md) (ces recommandations incluent de l’aide pour les environnements AD FS)
