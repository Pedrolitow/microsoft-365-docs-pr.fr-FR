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
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: 8d274fe3-db51-4107-ba64-865e7155b355
ms.custom:
- seo-marvel-apr2020
description: Cette rubrique décrit la configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de votre environnement Microsoft 365.
ms.openlocfilehash: cc1f69663badaa7ae6590bb1d389cb15f13da79d
ms.sourcegitcommit: 474bd6a86c3692d11fb2c454591c89029ac5bbd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49357538"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Configurer votre client Microsoft 365 pour une sécurité accrue

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Cette rubrique décrit la configuration recommandée pour les paramètres à l’échelle du client qui affectent la sécurité de votre environnement Microsoft 365. Vos besoins en matière de sécurité peuvent nécessiter plus ou moins de sécurité. Utilisez ces recommandations comme point de départ.

## <a name="check-office-365-secure-score"></a>Vérifier le score de sécurité d’Office 365

Le score de sécurité d’Office 365 analyse la sécurité de votre organisation en fonction de vos activités normales et des paramètres de sécurité et affecte un score. Commencez par prendre note de votre score actuel. L’ajustement de certains paramètres à l’échelle du client augmentera votre score. L’objectif est de ne pas atteindre le score maximal, mais de prendre conscience des possibilités de protection de votre environnement qui n’ont pas d’impact négatif sur la productivité de vos utilisateurs. Consultez la rubrique [Microsoft Secure score](../mtp/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-security-center"></a>Réglage des stratégies de gestion des menaces dans le centre de sécurité Microsoft 365

Le centre de sécurité Microsoft 365 inclut des fonctionnalités qui protègent votre environnement. Il inclut également des rapports et des tableaux de bord que vous pouvez utiliser pour surveiller et prendre des mesures. Certaines zones sont dotées de configurations de stratégie par défaut. Certaines zones n’incluent pas de stratégies ou de règles par défaut. Consultez ces stratégies sous gestion des menaces pour ajuster les paramètres de gestion des menaces à un environnement plus sécurisé.

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Anti-hameçonnage**|Oui|Si vous avez un domaine personnalisé, configurez la stratégie anti-hameçonnage par défaut pour protéger les comptes de messagerie de vos utilisateurs les plus précieux, tels que votre PDG, et pour protéger votre domaine. <p> Examinez les [stratégies anti-hameçonnage dans Office 365](set-up-anti-phishing-policies.md) et consultez la rubrique [configure anti-phishing Policies in EOP](configure-anti-phishing-policies-eop.md) or [configure anti-phishing Policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).|
|**Moteur anti-programme malveillant**|Oui| Modifiez la stratégie par défaut : <ul><li>Filtre de types de pièces jointes courantes : sélectionnez activé</li></ul> <p> Vous pouvez également créer des stratégies de filtrage des programmes malveillants personnalisées et les appliquer à des utilisateurs, des groupes ou des domaines spécifiés dans votre organisation. <p> Plus d’informations : <ul><li>[Protection contre les programmes malveillants](anti-malware-protection.md)</li><li>[Configurer des stratégies anti-programme malveillant](configure-anti-malware-policies.md)</li></ul>|
|**Pièces jointes fiables dans Microsoft Defender pour Office 365**|Non|Sur la page principale des pièces jointes fiables, cliquez sur **paramètres globaux** et activez ce paramètre : <ul><li>**Activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams**</li></ul> <p> Créez une stratégie de pièces jointes approuvées avec ces paramètres : <ul><li> **Bloquer**: sélectionnez **bloquer** comme réponse inconnue contre les programmes malveillants.</li><li>**Activer la redirection**: activez cette case à cocher et entrez une adresse de messagerie, telle qu’un compte d’administrateur ou de mise en quarantaine.</li><li>**Appliquer la sélection ci-dessus si l’analyse anti-programme malveillant pour les pièces jointes expire ou si une erreur se produit**: Cochez cette case.</li><li>**_Appliqué à_*: **le domaine du destinataire est** \> Sélectionnez votre domaine.</li></ul> <p> Pour plus d’informations : [ATP pour SharePoint, OneDrive et Microsoft teams](atp-for-spo-odb-and-teams.md) et [configurer des stratégies de pièces jointes fiables](set-up-atp-safe-attachments-policies.md)|
|**Liens fiables dans Microsoft Defender pour Office 365**|Oui|Sur la page principale des liens fiables, cliquez sur **paramètres globaux**: <ul><li>**Utiliser les liens fiables dans : applications Office 365**: Vérifiez que ce paramètre est activé.</li><li>**Ne pas effectuer le suivi lorsque les utilisateurs cliquent sur liens fiables**: désactivez ce paramètre pour effectuer le suivi des clics de l’utilisateur.</li></ul> <p> Créez une stratégie de liens fiables avec ces paramètres : <ul><li>**Sélectionnez l’action pour les URL potentiellement malveillantes dans les messages**: Vérifiez que ce paramètre est **activé**.</li><li>**Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft teams**: Vérifiez que ce paramètre est **activé**.</li><li>**Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers**: activez cette case à cocher.</li><li>**Patientez jusqu’à la fin de l’analyse des URL avant de remettre le message**: Cochez cette case.</li><li>**Appliquer des liens fiables aux messages électroniques envoyés au sein de l’organisation**: Cochez cette case</li><li>**Ne pas autoriser les utilisateurs à cliquer sur vers l’URL d’origine**: Cochez cette case.</li><li>**Appliqué à**: **le domaine du destinataire est** \> Sélectionnez votre domaine.</li></ul> <p> Informations supplémentaires : [configurer des stratégies de liens fiables](set-up-atp-safe-links-policies.md).|
|**Blocage du courrier indésirable (filtrage du courrier)**|Oui| Éléments à surveiller : <ul><li>Courrier indésirable trop nombreux : choisissez les paramètres personnalisés et modifiez la stratégie de filtrage du courrier indésirable par défaut.</li><li>Usurpation d’identité : Examinez les expéditeurs qui usurpent votre domaine. Bloquer ou autoriser ces expéditeurs.</li></ul> <p> Plus d’informations : [protection contre le courrier indésirable de Microsoft 365](anti-spam-protection.md).|
|**_Authentification de messagerie_* _|Oui|L’authentification de messagerie utilise un système DNS (Domain Name System) pour ajouter des informations vérifiables aux messages électroniques concernant l’expéditeur d’un message électronique. Microsoft 365 configure l’authentification de messagerie pour son domaine par défaut (onmicrosoft.com), mais les administrateurs Microsoft 365 peuvent également utiliser l’authentification de messagerie pour les domaines personnalisés. Trois méthodes d’authentification sont utilisées : <ul><li>Sender Policy Framework (SPF).</li><ul><li>Pour la configuration, consultez la rubrique [configurer SPF dans Microsoft 365 pour éviter l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Identified Identified Mail (DKIM).</li><ul><li>Consultez [la rubrique use DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).</li><li>Une fois que vous avez configuré DKIM, activez-le dans le centre de sécurité.</li></ul><li>Authentification de message basée sur un domaine, création de rapports et conformité (DMARC).</li><ul><li>Pour le programme d’installation d’DMARC [, utilisez DMARC pour valider le courrier électronique dans Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|
|

> [!NOTE]
> Pour les déploiements non standard de SPF, les déploiements hybrides et la résolution des problèmes : [Microsoft 365 utilise SPF (Sender Policy Framework) pour éviter l’usurpation](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-security-and-compliance-centers"></a>Afficher des tableaux de bord et des rapports dans les centres de sécurité et de conformité

Visitez ces rapports et tableaux de bord pour en savoir plus sur l’état de santé de votre environnement. Les données de ces rapports deviennent plus riches lorsque votre organisation utilise les services Office 365. Pour l’instant, familiarisez-vous avec les éléments que vous pouvez surveiller et prendre des mesures. Pour plus d’informations, consultez la rubrique relative aux [rapports dans les centres de sécurité et de conformité Microsoft 365](../../compliance/reports-in-security-and-compliance.md).

_***

|Tableau de bord|Description|
|---|---|
|[Tableau de bord de gestion des menaces](security-dashboard.md)|Dans la section **gestion des menaces** du centre de sécurité, utilisez ce tableau de bord pour voir les menaces qui ont déjà été gérées, et en tant qu’outil pratique pour le signalement aux décideurs d’entreprise sur les fonctionnalités d’enquête et de réponse de menace déjà effectuées pour sécuriser votre entreprise.|
|[Threat Explorer (et détections en temps réel)](threat-explorer.md)|Il s’agit également de la section **gestion des menaces** du centre de sécurité. Si vous recherchez ou rencontrez une attaque contre votre client, utilisez l’Explorateur (ou les détections en temps réel) pour analyser les menaces. L’Explorateur (et le rapport de détections en temps réel) vous montre le volume des attaques au fil du temps, et vous pouvez analyser ces données par familles de menaces, infrastructure d’agresseur, et bien plus encore. Vous pouvez également marquer tous les messages suspects pour la liste des incidents.|
|Rapports — tableau de bord|Dans la section **rapports** du centre de sécurité, affichez les rapports d’audit de vos organisations SharePoint Online et Exchange Online. Vous pouvez également accéder aux rapports de connexion utilisateur Azure Active Directory (Azure AD), aux rapports d’activité de l’utilisateur et au Journal d’audit Azure AD à partir de la page **afficher les rapports** .|
|

![Tableau de bord du centre de sécurité](../../media/870ab776-36d2-49c7-b615-93b2bc42fce5.png)

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Configurer des paramètres supplémentaires à l’échelle du client Exchange Online

De nombreux contrôles de sécurité et de protection dans le centre d’administration Exchange sont également inclus dans le centre de sécurité. Vous n’avez pas besoin de les configurer aux deux emplacements. Voici quelques paramètres supplémentaires qui sont recommandés.

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Flux de messagerie** (règles de flux de messagerie, également appelées règles de transport)|Non|Ajoutez une règle de flux de messagerie pour vous protéger contre les ransomware en bloquant les types de fichiers exécutables et les types de fichiers Office qui contiennent des macros. Pour plus d’informations, consultez la rubrique [utiliser des règles de flux de messagerie pour inspecter les pièces jointes dans Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Consultez les rubriques supplémentaires suivantes : <ul><li>[Se protéger contre les rançongiciels](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/secure-your-business-data#ransomware)</li><li>[Protection contre les programmes malveillants et les ransomware dans Office 365](https://docs.microsoft.com/Office365/Enterprise/office-365-malware-and-ransomware-protection)</li><li>[Récupération suite à une attaque de ransomware dans Office 365](recover-from-ransomware.md)</li></ul> <p> Créez une règle de flux de messagerie pour empêcher le transfert automatique des messages vers des domaines externes. Pour plus d’informations, consultez la rubrique [minimisation des règles de transfert externe des clients avec le score sécurisé](https://docs.microsoft.com/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> Plus d’informations : [règles de flux de messagerie (règles de transport) dans Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Activer l’authentification moderne**|Non|L’authentification moderne est une condition préalable à l’utilisation de l’authentification multifacteur (MFA). L’authentification multifacteur est recommandée pour sécuriser l’accès aux ressources Cloud, y compris la messagerie électronique. <p> Consultez les rubriques suivantes : <ul><li>[Activation ou désactivation de l’authentification moderne dans Exchange Online](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype entreprise Online : activation de votre client pour l’authentification moderne](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> L’authentification moderne est activée par défaut pour les clients Office 2016, SharePoint Online et OneDrive entreprise. <p> Plus d’informations : [fonctionnement de l’authentification moderne pour les applications clientes office 2013 et office 2016](https://docs.microsoft.com/microsoft-365/enterprise/modern-auth-for-office-2013-and-2016)|
|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Configurer des stratégies de partage à l’échelle du client dans le centre d’administration SharePoint

Recommandations de Microsoft relatives à la configuration des sites d’équipe SharePoint à des niveaux de protection croissants, à partir de la protection de base. Pour plus d’informations, consultez la rubrique [sécuriser des sites et des fichiers SharePoint Online](https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)

Les sites d’équipe SharePoint configurés au niveau de base autorisent le partage de fichiers avec des utilisateurs externes à l’aide de liens d’accès anonymes. Cette approche est recommandée au lieu d’envoyer des fichiers par courrier électronique.

Pour prendre en charge les objectifs de la protection de base, configurez les stratégies de partage à l’échelle du client comme il est recommandé ici. Les paramètres de partage de sites individuels peuvent être plus restrictifs que cette stratégie à l’échelle du client, mais pas plus permissif.

****

|Domaine|Inclut une stratégie par défaut|Recommandation|
|---|---|---|
|**Partage** (SharePoint Online et OneDrive entreprise)|Oui|Le partage externe est activé par défaut. Ces paramètres sont recommandés : <ul><li>Autoriser le partage à des utilisateurs externes authentifiés et à l’aide des liens d’accès anonyme (paramètre par défaut).</li><li>Les liens d’accès anonymes expirent dans ce nombre de jours. Entrez un nombre, si vous le souhaitez, par exemple 30 jours.</li><li>Type de lien par défaut — sélectionnez interne (personnes de l’organisation uniquement). Les utilisateurs qui souhaitent partager à l’aide de liens anonymes doivent choisir cette option dans le menu partage.</li></ul> <p> Plus d’informations : [vue d’ensemble du partage externe](https://docs.microsoft.com/sharepoint/external-sharing-overview)|
|

Le centre d’administration SharePoint et le centre d’administration OneDrive entreprise incluent les mêmes paramètres. Les paramètres dans le centre d’administration s’appliquent aux deux.

## <a name="configure-settings-in-azure-active-directory"></a>Configurer les paramètres dans Azure Active Directory

Veillez à visiter ces deux domaines dans Azure Active Directory pour effectuer une configuration à l’échelle du client pour des environnements plus sécurisés.

### <a name="configure-named-locations-under-conditional-access"></a>Configurer des emplacements nommés (sous accès conditionnel)

Si votre organisation comprend des bureaux disposant d’un accès réseau sécurisé, ajoutez les plages d’adresses IP approuvées à Azure Active Directory en tant qu’emplacements nommés. Cette fonctionnalité permet de réduire le nombre de faux positifs signalés pour les événements de risque de connexion.

Voir : [locations nommées dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-named-locations)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Bloquer les applications qui ne prennent pas en charge l’authentification moderne

L’authentification multifacteur nécessite des applications qui prennent en charge l’authentification moderne. Les applications qui ne prennent pas en charge l’authentification moderne ne peuvent pas être bloquées à l’aide des règles d’accès conditionnel.

Pour les environnements sécurisés, veillez à désactiver l’authentification pour les applications qui ne prennent pas en charge l’authentification moderne. Vous pouvez effectuer cette opération dans Azure Active Directory avec un contrôle bientôt disponible.

En attendant, utilisez l’une des méthodes suivantes pour effectuer cette commande pour SharePoint Online et OneDrive entreprise :

- Utiliser PowerShell, consultez la rubrique [bloquer les applications qui n’utilisent pas l’authentification moderne (Adal)](https://docs.microsoft.com/mem/intune/protect/app-modern-authentication-block).

- Configurez-le dans le centre d’administration SharePoint sur la page « accès au périphérique » — « contrôler l’accès à partir d’applications qui n’utilisent pas l’authentification moderne ». Choisissez bloquer.

## <a name="get-started-with-cloud-app-security-or-office-365-cloud-app-security"></a>Prise en main de la sécurité des applications Cloud ou de la sécurité des applications Cloud Office 365

Utilisez Office 365 Cloud App Security pour évaluer les risques, pour alerter les activités suspectes et pour agir automatiquement. Nécessite Office 365 E5 plan.

Vous pouvez également utiliser Microsoft Cloud App Security pour obtenir une visibilité plus poussée, même après avoir accordé un accès, des contrôles complets et une meilleure protection pour toutes vos applications Cloud, y compris Office 365.

Étant donné que cette solution recommande le plan EMS E5, nous vous recommandons de commencer par la sécurité des applications Cloud afin de pouvoir l’utiliser avec d’autres applications SaaS dans votre environnement. Démarrez avec les stratégies et les paramètres par défaut.

Plus d’informations :

- Rubrique relative au [déploiement de Cloud App Security](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security)

- Rubrique relative aux [informations supplémentaires concernant Microsoft Cloud App Security](https://www.microsoft.com/cloud-platform/cloud-app-security)

- [Qu’est-ce que la sécurité des applications Cloud ?](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)

![Tableau de bord Cloud App Security](../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png)

## <a name="additional-resources"></a>Ressources supplémentaires

Ces articles et guides fournissent des informations normatives supplémentaires pour la sécurisation de votre environnement Microsoft 365 :

- [Conseils de sécurité Microsoft pour les campagnes politiques, les organisations à but non lucratif et d’autres organisations agiles](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) (vous pouvez utiliser ces recommandations dans n’importe quel environnement, en particulier les environnements en nuage uniquement)

- [Stratégies de sécurité et configurations recommandées pour les identités et les appareils](microsoft-365-policies-configurations.md) (ces recommandations incluent de l’aide pour les environnements AD FS)
