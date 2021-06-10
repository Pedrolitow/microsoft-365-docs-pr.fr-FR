---
title: Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centres de données allemandes
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 05/12/2021
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Récapitulatif : comprendre la migration de Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) vers les services Office 365 dans les nouvelles régions de centre de données allemandes.'
ms.openlocfilehash: 4162e51164120cecaa431ad6883d3ee112ad4880
ms.sourcegitcommit: bce733c1152dfbca782e716579074261e3c2ef65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2021
ms.locfileid: "52796005"
---
# <a name="migration-from-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centres de données allemandes

> [!NOTE]
> Cet article s’applique uniquement aux clients Microsoft Cloud Deutschland éligibles.

En août 2018, Microsoft a annoncé son intention de fournir le cloud Microsoft complet (Azure, Office 365, Dynamics 365 et Power Platform) à partir de nouvelles régions cloud en Allemagne afin de mieux activer la transformation numérique de nos clients. En août 2019, nous avons annoncé que nous sommes désormais en train d’ouvrir les nouvelles régions dans le Cloud en Allemagne. Nous avons depuis annoncé la disponibilité d’Azure, Office 365, Dynamics 365 et Power Platform.

Les nouvelles régions sont conçues pour répondre aux besoins en constante évolution des clients allemands avec plus de souplesse, les derniers services cloud intelligents et une connectivité complète à notre réseau cloud de services Microsoft 365, ainsi qu’à la résidence des données client en Allemagne.

## <a name="how-to-migrate-to-the-new-german-datacenter-regions"></a>Comment migrer vers les nouvelles régions de centres de données allemandes

Les clients Microsoft Cloud Deutschland existants peuvent maintenant commencer à migrer leurs clients Office 365, Dynamics 365 Customer Engagement et Power Platform. La première étape consiste à [opter pour une migration dirigée par Microsoft](./ms-cloud-germany-migration-opt-in.md) vers nos nouvelles régions de centre de données allemandes.

Pour les organisations qui optent pour l’approche pilotée par Microsoft, les migrations doivent commencer au début de l’année 2021 et se terminer le 29 octobre 2021. Suite à la migration, les données client principales et les abonnements sont transférés vers les nouvelles régions allemandes.

Cet article fournit une vue d’ensemble de l’approche pilotée par Microsoft pour la migration, de la clarté sur les expériences des utilisateurs et des administrateurs pendant et après la migration, et des actions qui peuvent être requises pour les clients en fonction des charges de travail que vous utilisez.

Les services suivants seront migrés dans le cadre de l’approche dirigée par Microsoft :

- Azure Active Directory (Azure AD)
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- OneDrive Entreprise
- Skype Entreprise En ligne\*\*
- Groupes Office 365
- Dynamics 365 / Power Platform\*\*\*

\*\*Pendant la migration de Microsoft Cloud Deutschland vers les régions de centres de données allemandes, les clients Skype Entreprise Online existants passeront à Microsoft Teams. Voir [Prise en main de votre mise à niveau de Microsoft Teams](/microsoftteams/upgrade-start-here) pour plus d’informations.

\*\*\*Les conditions préalables et l’impact de la migration pour ces services sont décrits dans l’article [Dynamics 365 Customer engagement.](/dynamics365/get-started/migrate-data-german-region)

Office 365 Video va être mise hors services le 1er mars 2021. Si vous décidez de migrer votre client Office 365 vers les nouvelles régions du centre de données allemand, Office 365 Video ne sera plus prise en charge une fois la migration SharePoint Online terminée. Pour plus d’informations, consultez [la chronologie Microsoft Cloud Deutschland.](/stream/migrate-from-office-365#microsoft-cloud-deutschland-timeline)

## <a name="how-is-the-migration-organized"></a>Comment la migration est-elle organisée ?

Cette figure montre les dix phases de migration vers les nouveaux centres de données allemands.

:::image type="content" alt-text="Les dix phases de migration vers les nouveaux centres de données allemands" source="../media/ms-cloud-germany-migration-opt-in/migration-organization.png" lightbox="../media/ms-cloud-germany-migration-opt-in/migration-organization.png":::

Ces phases démarrent lorsque [vous optez pour la migration.](./ms-cloud-germany-migration-opt-in.md) La plupart des phases de migration sont exécutées en tant qu’opérations de service back end avec une interaction client minimale requise et sont exécutées une phase après l’autre. Le début des tâches supplémentaires dirigées par le client et l’état de migration global seront communiqués via le centre de messages du Centre d’administration Microsoft 365 pendant le processus de migration. Les exemples de tâches peuvent inclure des mises à jour DNS gérées par le client, la reconfiguration de la configuration hybride pour Exchange clients hybrides ou la migration Azure.

La migration ne commence pas immédiatement lorsque l’option d’opt-in se produit. Votre organisation est ajoutée à la liste des locataires qui sont programmés pour une migration ultérieure. Vous pouvez commencer les phases préalables au travail dès maintenant, car elles sont essentielles pour garantir la réussite de la migration et de l’utilisation une fois l’opération terminée :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)

Une semaine avant le début de la migration des clients, vous recevrez un avertissement final dans le service du centre de messages vous avertissant que toutes les conditions préalables doivent être terminées.

La migration déplace votre client Azure AD du service Azure AD allemand souverain vers l’instance de services Office 365 d’Azure AD dans la région de l’UE.

La phase suivante consiste à migrer vos abonnements&#39;client et les licences utilisateur des produits propres à l’Allemagne vers des produits globaux.

Une fois toutes les étapes terminées, y compris la migration azure du client, votre client est finalisé dans le service de services Office 365 et la migration est marquée comme terminée. À ce stade, la mise à jour finale du centre de messages vous est fournie. Le client est désormais une organisation Office 365 globale.

Vous êtes informé de l’avancement de la migration avec les publications du Centre de messages. Les publications auront lieu à des jalons spécifiques et fourniront des conseils sur la progression d’une étape, ainsi que des informations importantes sur les clients sur la base des exigences de processus. Les notifications du centre de messages sont fournies aux jalons suivants :

- Début de la migration (5 jours ou jours ou moins avant le début de la migration d’Azure AD)
- Migration d’Azure AD terminée
- Migration des abonnements et des licences terminée
- SharePoint migration terminée
- Exchange migration terminée
- Skype Entreprise terminé
- Dynamics complete
- Power BI terminé
- Le cutover final des services est terminé

Après le dernier passage d’Azure AD au service mondial, tous les clients et applications devraient être entièrement en transition pour utiliser les points de terminaison corrects. Il existe une fenêtre de 30 jours après le dernier passage où il est possible de continuer à obtenir des jetons Azure AD à partir du service Microsoft Cloud Deutschland. À l’expiration de la fenêtre de 30 jours, les clients et les applications ne pourront plus accéder aux points de terminaison Azure AD de Microsoft Cloud Deutschland. À partir de ce stade, l’accès des applications ou des utilisateurs échouera. Vous devez vous assurer que tous les utilisateurs et applications sont migrés vers les points de terminaison corrects avant la fermeture de cette fenêtre de temps. 

## <a name="moving-to-the-new-german-datacenter-regions"></a>Déplacement vers les nouvelles régions de centres de données allemandes

Les clients Microsoft Cloud Deutschland existants peuvent désormais commencer à migrer leurs services Office 365, Dynamics 365 Customer Engagement et Power Platform. La première étape consiste à [opter pour une migration dirigée par Microsoft](./ms-cloud-germany-migration-opt-in.md) vers nos nouvelles régions de centre de données allemandes. Lorsque vous renouvelez votre abonnement, vous optez automatiquement pour une migration assisté par Microsoft. Microsoft avertit les administrateurs clients par courrier électronique et dans le centre de messages du centre d’administration Microsoft 365 client lorsque cela s’est produit. Toutefois, si vous préférez démarrer [](./ms-cloud-germany-migration-opt-in.md) le processus maintenant, vous pouvez l’opter directement dans Microsoft 365 centre d’administration dès aujourd’hui. Les migrations doivent commencer au début de 2021 et se terminer le 29 octobre 2021. 

Suite à la migration, les données client essentielles et les abonnements sont déplacés vers les nouvelles régions de centres de données allemandes.

> [!NOTE]
> Cet article contient des instructions pour la migration des services Office 365 uniquement. Si vous exécutez des charges de travail Azure supplémentaires dans Microsoft Cloud Deutschland, consultez les instructions de [migration pour Azure Germany.](/azure/germany/germany-migration-main)

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Comment préparer la migration vers les services Office 365 dans les nouvelles régions de centre de données allemandes

La première étape consiste à avertir Microsoft afin que nous ions votre autorisation de migrer votre abonnement et vos données de Microsoft Cloud Deutschland vers les services Office 365 dans les nouvelles régions de centres de données allemandes. Pour obtenir des [instructions, reportez-vous](./ms-cloud-germany-migration-opt-in.md) au processus d’opt-in et notez que :

- Tous les clients en migration doivent vérifier la connectivité aux URL et adresses IP Office 365 Services Office 365, qui incluent les nouvelles régions de centres de données [allemandes.](urls-and-ip-address-ranges.md) L’inaction peut entraîner une défaillance du service et du client.
- Examinez la liste des [activités](ms-cloud-germany-transition-add-pre-work.md) préalables au travail pour vous assurer que votre organisation est informée et préparée pour les modifications.
- Vous devez consulter la description Office 365 service de la plateforme pour comprendre les fonctionnalités et services qui seront disponibles pour votre organisation après la migration vers la région allemande.
- Les abonnements d’essai ne seront pas migrés et bloqueront la migration de tous les abonnements payants. Vous devez annuler les essais ou les convertir en abonnements payants avant le début de la migration.

## <a name="where-do-i-go-from-here"></a>Où puis-je aller à partir d’ici ?

Examinez la section Questions fréquemment posées ci-après.

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="is-migration-required"></a>La migration est-elle obligatoire ?

Microsoft offre Office 365 migration de client microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centres de données allemandes sans frais supplémentaires. Même si nous vous recommandons vivement d’opter pour la migration vers les nouvelles régions de centres de données allemandes, nous continuerons à fournir les mises à jour de sécurité nécessaires à la région Microsoft Cloud Deutschland.

Office 365 services dans les nouvelles régions de centres de données allemandes :

- Ils offrent des tarifs compétitifs pour [Azure](https://azure.microsoft.com/pricing/calculator/), [Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 Customer engagement](https://dynamics.microsoft.com/pricing/)et [Power BI](https://powerbi.microsoft.com/pricing/).
- Sont connectés au réseau global de Microsoft&#39;, offrant des centaines de sites edge réseau, d’emplacements d’homologue et de points de sortie pour offrir une expérience utilisateur robuste partout dans le monde.
- Ils vous aident à répondre aux exigences de résidence des données client en Allemagne.
- Proposez notre offre de cloud mondial complète avec les versions les plus récentes de nos services et de nouvelles fonctionnalités, notamment Microsoft Teams et Multi-Géo dans Office 365. Ils permettent de comparer les produits par région pour [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&amp;regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](o365-data-locations.md) et [Dynamics 365](/dynamics365/get-started/availability).
- Ils offrent toutes les fonctionnalités, une sécurité de qualité professionnelle et des fonctionnalités complètes pour aider les clients à respecter les exigences de conformité et de réglementation.
- Ils sont accessibles via les contrats de services en ligne existants.

### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>Quelle est la disponibilité du service entre les différentes offres de service Cloud d’Office 365 ?
<h2 id="serv-avail"></h2>

Les 15 services suivants sont disponibles dans l’offre de services cloud Microsoft Cloud Deutschland. Nous n’ajoutons pas de nouveaux services à Microsoft Cloud Deutschland.

1. Exchange Online
2. Customer Lockbox (Exchange Online)
3. Groupes (groupes modernes)
4. Profil Delve
5. Exchange Online Protection
6. Defender pour Office 365
7. Advanced eDiscovery
8. Gouvernance des données avancée
9. SharePoint Online
10. Customer Lockbox (SharePoint Online)
11. OneDrive Entreprise
12. Skype Entreprise Online
13. Word Online, Excel Online, PowerPoint, OneNote, Visio Online
14. Office 365 Pro Plus
15. Outlook Mobile

Il existe actuellement 39 services disponibles dans le cadre de Office 365 services dans les nouvelles régions de centres de données allemandes. De nouvelles fonctionnalités et de nouveaux services sont régulièrement disponibles avec les services Office 365 globaux.

1. Exchange Online
2. Customer Lockbox for Exchange Online
3. Groupes Microsoft 365
4. Profil Delve
5. MyAnalytics
6. Workplace Analytics
7. Exchange Online Protection
8. Defender pour Office 365
9. Advanced eDiscovery
10. Gestion de la sécurité avancée
11. Protection des informations pour Office 365 
12. Gouvernance des données avancée
13. SharePoint Online
14. Customer Lockbox pour SharePoint Online
15. OneDrive Entreprise
16. Microsoft Stream
17. Skype Entreprise (migre vers Microsoft Teams lors de la migration)
18. PBX cloud
19. Conférence sur réseau téléphonique commuté
20. Appel sur réseau téléphonique commuté
21. Microsoft Teams
22. Rapports d’administration/rapports d’utilisation
23. Office pour le web
24. Planificateur
25. Sway
26. Microsoft 365 Apps
27. Outlook Mobile
28. Enterprise Mobility + Security (EMS) E3 (Azure AD Premium P1, Intune et Rights Management Service)
29. Yammer Entreprise
30. Microsoft Forms
31. Power Automate pour Office 365
32. Power Virtual Agents pour Office 365
33. PowerApps pour Office 365
34. Microsoft Bookings
35. À faire
36. Tableau blanc collaboratif
37. Microsoft StuffHub
38. Microsoft Kaizala Pro
39. Listes

### <a name="when-will-migration-happen"></a>Quand la migration aura-t-elle lieu ?

**Azure**

Si vous êtes un client Azure [](/azure/germany/germany-migration-main) uniquement, vous pouvez commencer à migrer vos ressources Azure vers une autre région dès aujourd’hui. 

Si vous avez Azure avec Office 365, Dynamics 365 ou Power BI, vous devez d’abord suivre le processus de migration des services Office 365 pour garantir la réussite de la migration d’Azure AD avant de pouvoir commencer la migration Azure auto-dirigée. Vous devez effectuer la migration Azure avant de finaliser votre migration de client pour maintenir vos charges de travail Azure avec votre azure AD et Office 365 organisation. [Reportez-vous aux actions](ms-cloud-germany-transition-phases.md) et aux impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland pour plus d’informations.

**Office 365**

[Optez](./ms-cloud-germany-migration-opt-in.md) pour la migration dirigée par Microsoft aujourd’hui. Lorsque nous sommes prêts à commencer votre migration, nous vous en informons via le centre de messages du centre d Microsoft 365'administration.

**Dynamics 365 et Power BI**

Optez pour la migration pilotée par Microsoft pour [Dynamics 365 Customer Engagement](/dynamics365/get-started/migrate-data-german-region) et [Power BI](/power-bi/admin/service-admin-migrate-data-germany) aujourd’hui. Lorsque nous serons prêts à démarrer votre migration, nous vous informerons via le centre de messages dans le Centre d’administration Microsoft 365.

### <a name="will-the-price-change-for-the-office-365-services-that-i-use"></a>Le prix change-t-il pour les services Office 365 que j’utilise ?

Oui. Les tarifs dans les&#39;cloud mondial de Microsoft (y compris les nouvelles régions de centres de données) sont généralement plus bas.

### <a name="during-the-subscription-migration-what-skus-and-licenses-will-be-applied-to-my-organization-and-users"></a>Pendant la migration de l’abonnement, quelles sont les S SKUs et les licences qui seront appliquées à mon organisation et aux utilisateurs ?

Pendant la migration de Microsoft Cloud Deutschland vers les services Office 365, les références SKU propres au service allemand sont remplacées par des versions globales de la même référence SKU ou d’une référence similaire. Dans la plupart des cas, la référence (SKU) dans les services Office 365 est identique, mais il existe peu de remplacements où la référence (SKU) en Allemagne n’est plus disponible dans les services Office 365. Si vous souhaitez mettre à jour la référence (SKU) attribuée à votre organisation une fois la migration terminée, contactez votre vendeur pour ajouter ou modifier les services affectés.

| Microsoft Cloud Deutschland - Product SKU (DE) | Microsoft Cloud Global - Référence du produit (WW) |
| --- | --- |
| Customer Lockbox \_ DE (LOCKBOX \_ DE) | Customer Lockbox (LOCKBOX) |
| Dynamics 365 Êdition Entreprise - Base de données Stockage \_ DE (CRMSTORAGE \_ DE) | Dynamics 365 Êdition Entreprise - Base de données Stockage (CRMSTORAGE) |
| Dynamics 365 Êdition Entreprise - Instance de non-production \_ supplémentaire DE (CRMTESTINSTANCE \_ DE) | Dynamics 365 Êdition Entreprise - Instance de non-production supplémentaire (CRMTESTINSTANCE) |
| Dynamics 365 for Customer Service Êdition Entreprise \_ DE (DYN365 \_ ENTERPRISE CUSTOMER SERVICE \_ \_ \_ DE) | Dynamics 365 for Customer Service Êdition Entreprise (DYN365 \_ ENTERPRISE \_ CUSTOMER \_ SERVICE) |
| Dynamics 365 for Sales Êdition Entreprise \_ DE (DYN365 \_ ENTERPRISE SALES \_ \_ DE) | Dynamics 365 for Sales Êdition Entreprise (DYN365 \_ ENTERPRISE \_ SALES) |
| Dynamics 365 for Team Members Êdition Entreprise \_ DE (DYN365 \_ ENTERPRISE TEAM MEMBERS \_ \_ \_ DE) | Dynamics 365 for Team Members Êdition Entreprise (DYN365 \_ ENTERPRISE \_ TEAM \_ MEMBERS) |
| Dynamics 365 Plan 1 Êdition Entreprise \_ DE (DYN365 \_ ENTERPRISE \_ PLAN1 \_ DE) | Dynamics 365 Plan 1 Êdition Entreprise (DYN365 \_ ENTERPRISE \_ PLAN1) |
| \_Services ECAL (EOA, EOP, DLP) DE (ECAL \_ SERVICES \_ DE) | Services ECAL (EOA, EOP, DLP) (ECAL \_ SERVICES) |
| \_Enterprise Mobility + Security E3 DE (EMS \_ DE) | Enterprise Mobility + Security E3 (EMS) |
| \_Exchange Online (plan 1) DE (EXCHANGESTANDARD \_ DE) | Exchange Online (plan 1) (EXCHANGESTANDARD) |
| \_Exchange Online (plan 2) DE (EXCHANGEENTERPRISE \_ DE) | Exchange Online (plan 2) (EXCHANGEENTERPRISE) |
| \_Archivage Exchange Online pour Exchange Online DE (EXCHANGEARCHIVE \_ ADDON \_ DE) | Archivage Exchange Online pour Exchange Online (EXCHANGEARCHIVE \_ ADDON) |
| \_Archivage Exchange Online pour Exchange Server DE (EXCHANGEARCHIVE \_ DE) | Archivage Exchange Online pour Exchange Server (EXCHANGEARCHIVE) |
| \_Exchange Online Essentials DE (EXCHANGE \_ S \_ ESSENTIALS \_ DE) | Exchange Online Essentials (EXCHANGE \_ S \_ ESSENTIALS) |
| \_Exchange Online Kiosk DE (EXCHANGEDESKLESS \_ DE) | Exchange Online Kiosk (EXCHANGEDESKLESS) |
| \_Exchange Online Protection DE (EOP \_ ENTERPRISE \_ DE) | Exchange Online Protection (EOP \_ ENTERPRISE) |
| Microsoft 365 Business Standard (O365 \_ BUSINESS \_ PREMIUM) | Microsoft 365 Business Standard (O365 \_ BUSINESS \_ PREMIUM) |
| Microsoft Dynamics CRM Online Instance \_ DE (CRMINSTANCE \_ DE) | Microsoft Dynamics CRM Online Instance (CRMINSTANCE) |
| Office 365 A1 pour le corps enseignant \_ DE (STANDARDWOFFPACK \_ FACULTY \_ DE) | Office 365 A1 pour les enseignants (STANDARDWOFFPACK \_ FACULTY) |
| Office 365 A1 pour les étudiants \_ DE (STANDARDWOFFPACK \_ STUDENT \_ DE) | Office 365 A1 pour les étudiants (STANDARDWOFFPACK \_ STUDENT) |
| \_Conformité avancée Office 365 DE (EQUIVIO \_ ANALYTICS \_ DE) | Microsoft 365 E5 Conformité (CONFORMITÉ \_ DE LA PROTECTION DES \_ INFORMATIONS) |
|Microsoft Defender pour Office 365 (Plan 1) \_ DE (ATP \_ ENTERPRISE \_ DE) |Microsoft Defender pour Office 365 (Plan 1) (ATP \_ ENTREPRISE) |
| \_Office 365 Business Essentials DE (O365 \_ BUSINESS \_ ESSENTIALS \_ DE) | Microsoft 365 Business Basic (O365 \_ BUSINESS \_ ESSENTIALS) |
| \_Office 365 Business Premium DE (O365 \_ BUSINESS \_ PREMIUM \_ DE) | Microsoft 365 Business Standard (O365 \_ BUSINESS \_ PREMIUM) |
| \_Office 365 Business DE (O365 \_ BUSINESS \_ DE) | Applications Microsoft 365 pour les PME (O365 \_ BUSINESS) |
| Office 365 E1 \_ DE (STANDARDPACK \_ DE) | Office 365 E1 (STANDARDPACK) |
| Office 365 E3 sans ProPlus \_ DE (ENTERPRISEPACKWITHOUTPROPLUS \_ DE) | Office 365 E3 sans ProPlus (ENTERPRISEPACKWITHOUTPROPLUS) |
| Office 365 E3 \_ DE (ENTERPRISEPACK \_ DE) | Office 365 E3 (ENTERPRISEPACK) |
| Office 365 Entreprise E1 \_ DE (STANDARDPACK \_ DE) | Office 365 Entreprise E1 (STANDARDPACK) |
| Office 365 Entreprise E3 \_ DE (ENTERPRISEPACK \_ DE) | Office 365 Entreprise E3 (ENTERPRISEPACK) |
| \_Stockage de fichiers supplémentaire Office 365 DE (SHAREPOINTSTORAGE \_ DE) | Stockage de fichiers supplémentaire Office 365 (SHAREPOINTSTORAGE) |
| \_Office 365 F1 DE (DESKLESSPACK \_ DE) | Office 365 F1 (DESKLESSPACK) |
| Office 365 ProPlus pour faculty \_ DE (OFFICESUBSCRIPTION \_ FACULTY \_ DE) | Office 365 ProPlus pour les enseignants (OFFICESUBSCRIPTION \_ FACULTY) |
| Office 365 ProPlus pour étudiants \_ DE (OFFICESUBSCRIPTION \_ STUDENT \_ DE) | Office 365 ProPlus pour les étudiants (OFFICESUBSCRIPTION \_ STUDENT) |
| \_Office 365 ProPlus DE (OFFICESUBSCRIPTION \_ DE) | Office 365 ProPlus (OFFICESUBSCRIPTION) |
| \_OneDrive Entreprise (plan 1) DE (WACONEDRIVESTANDARD \_ DE) | OneDrive Entreprise (plan 1) (WACONEDRIVESTANDARD) |
| \_OneDrive Entreprise (plan 2) DE (WACONEDRIVEENTERPRISE \_ DE) | OneDrive Entreprise (plan 2) (WACONEDRIVEENTERPRISE) |
| Power BI Pro pour les enseignants \_ DE (POWER \_ BI PRO \_ \_ FACULTY \_ DE) | Power BI Pro pour les enseignants (POWER \_ BI \_ PRO \_ FACULTY) |
| \_Power BI Pro DE (POWER \_ BI \_ PRO \_ DE) | Power BI Pro (POWER \_ BI \_ PRO) |
| \_Project Online Essentials DE (PROJECTESSENTIALS \_ DE) | Project Online Essentials (PROJECTESSENTIALS) |
| \_Project Online Premium DE (PROJECTPREMIUM \_ DE) | Project Online Premium (PROJECTPREMIUM) |
| \_Project Online Professionnel DE (PROJECTPROFESSIONAL \_ DE) | Project Online Professionnel (PROJECTPROFESSIONAL) |
| \_Project (plan 3) DE (PROJECTPROFESSIONAL \_ DE) | Project (plan 3) (PROJECTPROFESSIONAL) |
| Office 365 E4 \_ DE (ENTERPRISEWITHSCAL \_ DE) | Office 365 E3 (ENTERPRISEPACK) |
| \_SharePoint Online (plan 1) DE (SHAREPOINTSTANDARD \_ DE) | SharePoint Online (plan 1) (SHAREPOINTSTANDARD) |
| \_SharePoint Online (plan 2) DE (SHAREPOINTENTERPRISE \_ DE) | SharePoint Online (plan 2) (SHAREPOINTENTERPRISE) |
| Skype Entreprise Online (Plan 1) \_ DE (MCOIMP \_ DE) | Office 365 E1 (STANDARDPACK) |
| Skype Entreprise Online (Plan 1) \_ DE (MCOIMP \_ DE) | Skype Entreprise Online (Plan 1) (MCOIMP) |
| Skype Entreprise Online (Plan 2) \_ DE (MCOSTANDARD \_ DE) | Skype Entreprise Online (Plan 2) (MCOSTANDARD) |
| Skype Entreprise Plus CAL \_ DE (MCOPLUSCAL \_ DE) | Skype Entreprise Plus CAL (MCOPLUSCAL) |
| Visio Online Plan 1 for faculty \_ DE (VISIOONLINE \_ PLAN1 \_ FAC \_ DE) | Visio Plan en ligne 1 pour les enseignants (VISIOONLINE \_ PLAN1 \_ FAC) |
| Visio Online Plan 1 \_ DE (VISIOONLINE \_ PLAN1 \_ DE) | Visio Plan en ligne 1 (VISIOONLINE \_ PLAN1) |
| Visio Online Plan 2 for faculty \_ DE (VISIOCLIENT \_ FACULTY \_ DE) | Visio Plan en ligne 2 pour les enseignants (VISIOCLIENT \_ FACULTY) |
| Visio Online Plan 2 \_ DE (VISIOCLIENT \_ DE) | Visio Plan en ligne 2 (VISIOCLIENT) |
| \_Visio (plan 1) DE (VISIOONLINE \_ PLAN1 \_ DE) | Visio (plan 1) (VISIOONLINE \_ PLAN1) |
| \_Visio (plan 2) DE (VISIOCLIENT \_ DE) | Visio (plan 2) (VISIOCLIENT) |
|||

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>Comment obtenir de l’aide de la part de Microsoft pour effectuer la migration vers une nouvelle région ou répondre à des questions de support ?

Si vous avez des questions, vous pouvez nous contacter ou contacter votre partenaire :

- Pour Azure, vous pouvez envoyer de [nouvelles demandes de support](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) dans le portail Azure.
- Par Office 365, vous pouvez soumettre des questions à l’aide du lien Besoin d’aide du &quot; &quot; Centre [d’administration Microsoft 365.](https://portal.office.de/)
- Si vous êtes un client Dynamics 365 Customer Engagement et Power BI et que vous avez également des Office 365, vous pouvez soumettre des questions à l’aide du lien Besoin d’aide ? du Centre d’administration &quot; &quot; [Microsoft 365.](https://portal.office.de/) Les options de support de Dynamics 365 Customer Engagement se trouvent [ici](/dynamics365/get-started/support/). Les options de support de Power BI se trouvent [ici](https://powerbi.microsoft.com/support/).

### <a name="my-customer-already-has-a-m365-tenant-in-the-global-microsoft-cloud-in-addition-to-a-microsoft-cloud-deutschland-tenant-can-these-two-tenants-be-merged-into-one-as-part-of-the-migration"></a>Mon client dispose déjà d’un client M365 dans le cloud Microsoft global en plus d’un client Microsoft Cloud Deutschland. Ces deux locataires peuvent-ils être fusionnés en un dans le cadre de la migration ?

Non, il n’existe aucune fonctionnalité de fusion de client. Les locataires restent distincts et uniques, car chaque client possède son propre espace de noms et son ID unique. Microsoft migre un client Microsoft Cloud Deutschland vers le cloud global si vous le souhaitez, sinon le client peut l’annuler et l’abandonner.


### <a name="what-actions-are-required-to-be-done-by-most-end-users-as-part-of-the-migration"></a>Quelles actions sont requises par la plupart des utilisateurs finaux dans le cadre de la migration ?
La migration est conçue pour avoir un impact minimal sur les utilisateurs finaux/clients.
- Assurez-vous que Office applications exécutent les dernières versions disponibles. 
- Les clients utilisant Skype Entreprise passeront à Teams dans le cadre de la migration et devront peut-être télécharger et installer Teams [sur](/deployoffice/teams-install) les appareils.
- Les utilisateurs finaux devront peut-être se déconnecter des applications Office et se connecter une fois la migration terminée. 
- Les clients qui exécutent le client OneDrive Sync doivent se déconnecter de leur station de travail et se connecter à nouveau pour permettre au client OneDrive Sync de se connecter au service Azure Active Directory global.
- Prenons en compte les nouvelles URL globales une fois la migration terminée, notamment Outlook Web Access (exemple : utiliser outlook.office365.com). SharePoint Les clients en ligne continueront à se connecter correctement à l’espace de noms MCD à l’aide de l’URL existante (exemple : contoso.sharepoint.de).


### <a name="which-customers-are-affected-by-the-azure-active-directory-migration"></a>Quels clients sont concernés par la migration Azure Active Directory migration ? 

Tous les clients de Office 365 comptent sur Azure Active Directory authentifier et stocker les composants de service critiques nécessaires au fonctionnement des services hébergés par Microsoft. 


### <a name="what-are-the-impacts-of-the-azure-active-directory-migration"></a>Quels sont les impacts de la migration Azure Active Directory migration ?

La migration initiale de Azure Active Directory en phase préliminaire n’a aucun impact sur l’expérience client. Après l’étape de migration finale, tous les services du client sont entièrement dans le service global. Après cette étape finale, le service Azure Active Directory Microsoft Cloud Deutschland peut ne plus accepter de demandes d’autorisation ou fournir des jetons d’accès Office services.


### <a name="what-does-it-mean-to-ensure-network-connectivity-to-office-365-services-urls-and-ip-addresses"></a>Qu’est-ce que cela signifie de garantir la connectivité réseau aux URL Office 365 services et [aux adresses IP](./urls-and-ip-address-ranges.md)?

Cet article décrit les URL et adresses IP nécessaires pour une bonne fonction du service global afin de garantir une bonne expérience client. Dans des cas relativement rares, certains clients tentent de configurer la sécurité du périmètre réseau de manière à minimiser les flux de trafic et ont un accès restreint aux services à ceux-ci uniquement dans le cadre des plages d’adresses IP du service Microsoft Cloud Deutschland.


### <a name="how-do-i-manage-the-dns-changes-for-exchange-online-so-mail-will-continue-to-flow"></a>Comment puis-je gérer les modifications DNS pour Exchange Online pour que le courrier continue de circuler ?

Les plages IP gérées par Microsoft et les zones DNS sont transitionn es pendant et dans le cadre de la migration vers le service global. 

Les zones DNS gérées par le client telles que les enregistrements MX de domaine personnalisé sont la responsabilité du client. Toutefois, pour simplifier cette migration, l’enregistrement MX géré par le client pointe vers un point de terminaison de service Office 365 dans la zone office.de et Microsoft gère automatiquement la migration de ce point de terminaison de service.


### <a name="how-do-i-manage-the-dns-changes-for-skype-for-business"></a>Comment gérer les modifications DNS pour les Skype Entreprise ? 
 
Tous les Skype pour les entreprises passeront à la Microsoft Teams. La transition des zones DNS Skype client n’est pas requise lors de la migration vers Teams. Les clients pourront se Teams immédiatement avec toutes les fonctionnalités après la migration.
 

### <a name="will-outlook-for-ios-and-android-work-after-the-migration"></a>Les Outlook pour iOS et Android fonctionneront-ils après la migration ? 

Oui. La recommandation de Microsoft est que tous les clients exécutent les dernières versions disponibles de Office clients, y compris Outlook clients iOS et Android. À la fin de la migration vers le service global Office 365, tous les clients Office doivent se déconnecter et se connecter pour obtenir un nouveau jeton d’accès Azure Active Directory auprès du service global. 



## <a name="next-step"></a>Étape suivante

[Opter pour une migration](ms-cloud-germany-migration-opt-in.md)

## <a name="more-information"></a>Plus d’informations

Mise en place :

- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client pendant la migration](ms-cloud-germany-transition-experience.md)

Transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [les appareils,](ms-cloud-germany-transition-add-devices.md) [les expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications cloud :

- [Informations sur le programme de migration Dynamics 365](/dynamics365/get-started/migrate-data-german-region)
- [Informations sur le programme de migration Power BI](/power-bi/admin/service-admin-migrate-data-germany)
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)
