---
title: Surveillance des fuites de données personnelles
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 02/07/2018
audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
- m365-security
ms.localizationpriority: high
search.appverid:
- MET150
description: Découvrez trois outils qui permettent de surveiller les fuites de données personnelles.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: dd25ee58f219a18544b05969e2c0a51eb7788a13
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68069004"
---
# <a name="monitor-for-leaks-of-personal-data"></a>Surveillance des fuites de données personnelles

There are many tools that can be used to monitor the use and transport of personal data. This topic describes three tools that work well.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image1.png" alt-text="Outils permettant de surveiller l’utilisation et le transport des données personnelles" lightbox="../../media/Monitor-for-leaks-of-personal-data-image1.png":::

Dans cette illustration :

- Start with Microsoft Purview data loss prevention reports for monitoring personal data in SharePoint Online, OneDrive for Business, and email in transit. These reports provide the greatest level of detail for monitoring personal data. However, these reports don't include all services in Office 365.

- Next, use alert policies and the audit log to monitor activity across services. Set up ongoing monitoring or search the audit log to investigate an incident. The audit log works across services—Sway, Power BI, eDiscovery, Dynamics 365, Power Automate, Microsoft Teams, Admin activity, OneDrive for Business, SharePoint Online, mail in transit, and mailboxes at rest. Skype conversations are included in mailboxes at rest.

- Finally, Use Microsoft Defender for Cloud Apps to monitor files with sensitive data in other SaaS providers. Coming soon is the ability to use sensitive information types and unified labels across Azure Information Protection and Office with Defender for Cloud Apps. You can set up policies that apply to all of your SaaS apps or specific apps (like Box). Defender for Cloud Apps doesn't discover files in Exchange Online, including files attached to email.

## <a name="data-loss-prevention-reports"></a>Rapports de protection contre la perte de données

After you create your data loss prevention (DLP) policies, you'll want to verify that they're working as you intended and helping you to stay compliant. With the DLP reports in Office 365, you can quickly view the number of DLP policy matches, overrides, or false positives; see whether they're trending up or down over time; filter the report in different ways; and view more details by selecting a point on a line on the graph.

Vous pouvez utiliser les rapports DLP pour :

- Vous concentrer sur des périodes de temps spécifiques et comprendre les raisons des pics et des tendances.
- Découvrir les processus d’entreprise qui enfreignent les stratégies DLP de votre organisation.
- Comprendre l’incidence des stratégies DLP sur l’entreprise.
- Afficher les motifs présentés par les utilisateurs lorsqu'ils passent outre une stratégie ou signalent un faux positif.
- Vérifier la conformité avec une stratégie DLP spécifique en affichant les correspondances pour cette stratégie.
- Afficher la liste des fichiers avec des données sensibles qui correspondent à vos stratégies DLP dans le volet de détails.

En outre, vous pouvez utiliser les rapports DLP pour affiner vos stratégies DLP lorsque vous les exécutez en mode test.

DLP reports are in the Microsoft Purview compliance portal. Go to **Reports** \> **Organizational data** section to find the **DLP policy matches**, **DLP incidents**, and **DLP false positives and overrides** reports.

Pour plus d’informations, consultez la rubrique [Affichage des rapports de protection contre la perte de données](../../compliance/view-the-dlp-reports.md).

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image2.png" alt-text="Rapport montrant les correspondances de stratégie DLP" lightbox="../../media/Monitor-for-leaks-of-personal-data-image2.png":::

## <a name="audit-log-and-alert-policies"></a>Journal d’audit et stratégies d’alerte

Le journal d’audit contient les événements Exchange Online, SharePoint Online, OneDrive Entreprise, Azure Active Directory, Microsoft Teams, Power BI, Sway et d’autres services.

Le Portail Microsoft 365 Defender et le portail de conformité Microsoft Purview proposent deux méthodes pour surveiller et générer des rapports sur la base du journal d’audit :

- Configurer des stratégies d’alerte, afficher des alertes et surveiller les tendances : utilisez les nouveaux outils de tableau de bord d’alertes et de stratégie d’alerte dans le Portail Microsoft 365 Defender ou le portail de conformité Microsoft Purview.
- Search the audit log directly: Search for all events in a specified date rage. Or you can filter the results based on specific criteria, such as the user who performed the action, the action, or the target object.

Information compliance and security teams can use these tools to proactively review activities performed by both end users and administrators across services. Automatic alerts can be configured to send email notifications when certain activities occur on specific site collections - for example when content is shared from sites known to contain GDPR-related information. This allows those teams to follow up with users to ensure that corporate security policies are followed, or to provide additional training.

Information security teams can also search the audit log to investigate suspected data breaches and determine both root cause and the extent of the breach. This built-in capability facilitates compliance with article 33 and 34 of the GDPR, which require notifications be provided to the GDPR supervisory authority and to the data subjects themselves of a data breach within a specific time period. Audit log entries are only retained for 90 days within the service - it is often recommended and many organizations required that these logs be retained for longer periods of time.

Solutions are available that subscribe to the Unified Audit Logs through the Microsoft Management Activity API and can both store log entries as needed, and provide advanced dashboards and alerts. One example is [Microsoft Operations Management Suite (OMS)](/azure/operations-management-suite/oms-solution-office-365).

Plus d’informations sur les stratégies d’alerte et l’exécution d’une recherche dans le journal d’audit :

- [Stratégies d’alerte dans Microsoft 365](../../compliance/alert-policies.md)
- [Effectuer des recherches dans le journal d’audit dans le Centre de sécurité et de conformité Office 365](../../compliance/search-the-audit-log-in-security-and-compliance.md) (introduction)
- [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md)
- [Rechercher le journal d’audit](../../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) (cmdlet)
- [Propriétés détaillées dans le journal d’audit](../../compliance/detailed-properties-in-the-office-365-audit-log.md)

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Cloud App Security vous permet de découvrir d’autres applications SaaS utilisées dans vos réseaux et les données sensibles qui sont envoyées vers et depuis ces applications.

Microsoft Defender for Cloud Apps is a comprehensive service providing deep visibility, granular controls, and enhanced threat protection for your cloud apps. It identifies more than 15,000 cloud applications in your network-from all devices-and provides risk scoring and ongoing risk assessment and analytics. No agents required: information is collected from your firewalls and proxies to give you complete visibility and context for cloud usage and shadow IT.

To better understand your cloud environment, the Defender for Cloud Apps investigate feature provides deep visibility into all activities, files, and accounts for sanctioned and managed apps. You can gain detailed information on a file level and discover where data travels in the cloud apps.

Par exemple, l’illustration suivante présente deux stratégies Defender for Cloud Apps qui peuvent vous aider avec le RGPD.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image3.png" alt-text="Exemples de stratégies Defender for Cloud Apps." lightbox="../../media/Monitor-for-leaks-of-personal-data-image3.png":::

La première stratégie signale lorsque des fichiers avec un attribut PII prédéfini ou une expression personnalisée que vous choisissez sont partagés en dehors de l’organisation à partir des applications SaaS que vous choisissez.

The second policy blocks downloads of files to any unmanaged device. You choose the attributes within the files to look for and the SaaS apps you want the policy to apply to.

Ces types d’attributs seront bientôt disponibles dans Defender for Cloud Apps :

- Types d’informations sensibles
- Étiquettes unifiées dans Microsoft 365 et Azure information protection

### <a name="defender-for-cloud-apps-dashboard"></a>Tableau de bord Microsoft Defender for Cloud Apps

If you haven't yet started to use Defender for Cloud Apps, begin by starting it up. To access Defender for Cloud Apps: <https://portal.cloudappsecurity.com>.

> [!NOTE]
> Be sure to enable 'Automatically scan files for Azure Information Protection classification labels' (in General settings) when getting started with Defender for Cloud Apps or before you assign labels. After setup, Defender for Cloud Apps does not scan existing files again until they are modified.

:::image type="content" source="../../media/Monitor-for-leaks-of-personal-data-image4.png" alt-text="Tableau de bord affichant des informations sur les alertes" lightbox="../../media/Monitor-for-leaks-of-personal-data-image4.png":::

Plus d’informations :

- [Déployer Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Plus d’informations sur Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Bloquer les téléchargements d’informations sensibles à l’aide du proxy Microsoft Defender for Cloud Apps](/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>Exemple de stratégies d’activité et de fichier pour détecter le partage de données personnelles

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>Détection du partage de fichiers contenant des informations PII : numéro de carte de crédit

Alerte lorsqu’un fichier contenant un numéro de carte de crédit est partagé à partir d’une application cloud approuvée.

|Contrôle|Paramètres|
|---|---|
|Type de stratégie|Stratégie de fichier|
|Modèle de stratégie|Aucun modèle|
|Gravité de la stratégie|Importante|
|Catégorie|DLP|
|Paramètres de filtre|Niveau d’accès = Public (Internet), Public, Externe <p> Application = \<select apps\> (utiliser ce paramètre pour limiter la surveillance à des applications SaaS spécifiques)|
|Appliquer à|Tous les fichiers, tous les propriétaires|
|Inspection du contenu|Inclut les fichiers qui correspondent à une expression présente : Tous les pays: Finance: Numéro de carte de crédit <p> N’exige pas de contexte approprié : désactivé (ce paramètre correspondra aux mots-clés et aux expressions régulières) <p> Inclut les fichiers avec au moins 1 correspondance <p> Annuler le masquage des 4 derniers caractères de la violation : activé|
|Alertes|Crée une alerte pour chaque fichier correspondant : activé <p> Limite quotidienne d’alertes : 1 000 <p> Sélectionner une alerte en tant qu’e-mail : activé <p> À : infosec@contoso.com|
|Gouvernance|Microsoft OneDrive Entreprise <p> Donner un caractère privé : sélectionner Supprimer les utilisateurs externes <p> Tous les autres paramètres : désactivé <p> Microsoft SharePoint Online <p> Donner un caractère privé : sélectionner Supprimer les utilisateurs externes <p> Tous les autres paramètres : désactivé|

Stratégies similaires :

- Détection du partage de fichiers contenant des informations PII : adresse e-mail
- Détection du partage de fichiers contenant des informations PII : numéro de passeport

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Détection des données client ou RH dans Box ou OneDrive Entreprise

Alerte lorsqu’un fichier étiqueté en tant que Données client ou Données RH est chargé dans OneDrive Entreprise ou Box.

Remarques :

- La surveillance de Box requiert un connecteur configuré à l’aide du kit de développement logiciel (SDK) du connecteur de l’API.
- Cette stratégie exige des fonctionnalités qui sont actuellement en Private Preview.

|Contrôle|Paramètres|
|---|---|
|Type de stratégie|Stratégie d’activité|
|Modèle de stratégie|Aucun modèle|
|Gravité de la stratégie|Importante|
|Catégorie|Contrôle partagé|
|Agir sur|Activité unique|
|Paramètres de filtre|Type d’activité = Charger un fichier <p> Application = Microsoft OneDrive Entreprise et Box <p> Étiquette de classification (actuellement en Private Preview) : Azure Information Protection = données sur les clients, ressources humaines - données sur le salaire, ressources humaines - données sur les employés|
|Alertes|Créer une alerte : activé <p> Limite quotidienne d’alertes : 1 000 <p> Sélectionner une alerte en tant qu’e-mail : activé <p> À : infosec@contoso.com|
|Gouvernance|Toutes les applications <p> Mettre l’utilisateur en quarantaine : activé <p> Tous les autres paramètres : désactivé <p> Office 365 <p> Mettre l’utilisateur en quarantaine : activé <p> Tous les autres paramètres : désactivé|

Stratégies similaires :

- Détection de téléchargements volumineux de données client ou de données RH : alerte lorsqu’un grand nombre de fichiers contenant des données client ou des données RH ont été téléchargés par un utilisateur unique dans un court délai.
- Détection du partage de données clients et de données RH : alerte lorsque des fichiers contenant des données clients ou des données RH sont partagés.
