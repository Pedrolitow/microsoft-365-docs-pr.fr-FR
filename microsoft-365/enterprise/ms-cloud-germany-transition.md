---
title: Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 09/30/2020
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
ms.openlocfilehash: 23ccc30bab5d1045e4716cd637899e20362fc597
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48846939"
---
# <a name="migration-from-microsoft-cloud-deutschland-to-office-365-services-in-the-new-german-datacenter-regions"></a>Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand

> [!NOTE]
> Cet article s’applique uniquement aux clients Deutschland de Microsoft Cloud éligibles.

En août 2018, Microsoft a annoncé notre intention de livrer la gamme Microsoft Cloud – Azure, Office 365, Dynamics 365 et Power Platform, des nouvelles régions de Cloud en Allemagne afin de mieux activer la transformation numérique de nos clients. En août 2019, nous avons annoncé que nous sommes désormais en train d’ouvrir les nouvelles régions dans le Cloud en Allemagne. Depuis, nous avons annoncé la disponibilité d’Azure, Office 365, Dynamics 365 et Power Platform.

Les nouvelles régions sont conçues pour répondre aux besoins évolutifs des clients allemands avec une plus grande flexibilité, les services Cloud intelligents les plus récents et une connectivité complète à notre réseau Cloud des services Microsoft 365, ainsi qu’à la résidence des données du client en Allemagne.

## <a name="how-to-migrate-to-the-new-german-regions"></a>Procédure de migration vers les nouvelles régions allemandes

Les clients de Microsoft Cloud Deutschland existants peuvent désormais migrer leur engagement client Office 365, Dynamics 365 et les clients Power Platform. La première étape consiste à [opter pour une migration dirigée par Microsoft](https://aka.ms/office365germanymoveoptin) vers nos nouvelles régions de centre de données allemandes.

Pour les organisations qui optent pour l’approche basée sur Microsoft, les migrations sont censées commencer en début de 2021 et seront effectuées au plus tard le 29 octobre 2021. Suite à la migration, les données client principales et les abonnements sont transférés vers les nouvelles régions allemandes.

Cet article fournit une vue d’ensemble de l’approche basée sur Microsoft pour la migration, de la clarté sur les expériences pour les utilisateurs et les administrateurs pendant et après la migration, ainsi que les actions qui peuvent être requises pour les clients en fonction des charges de travail que vous utilisez.

Les services suivants seront migrés dans le cadre de l’approche dirigée par Microsoft :

- Azure Active Directory (Azure AD)
- Exchange Online
- Exchange Online Protection
- SharePoint Online
- OneDrive Entreprise

- Skype entreprise Online\*\*
- Groupes Office 365
- Dynamics 365/Power Platform\*\*\*

\*\*Lors de la migration de Microsoft Cloud Deutschland vers les régions de centre de développement allemand, les clients Skype entreprise Online sont transférés vers Microsoft Teams. Voir [Prise en main de votre mise à niveau de Microsoft Teams](https://aka.ms/SkypeToTeams-Home) pour plus d’informations.

\*\*\*Les conditions préalables et l’impact de la migration de ces services sont décrits dans l’article de l' [engagement client Dynamics 365](https://aka.ms/d365ceoptin) .

Office 365 Video va être mise hors services le 1er mars 2021. Si vous décidez de migrer votre client Office 365 vers les nouvelles régions du centre de données allemand, Office 365 Video ne sera plus prise en charge une fois la migration SharePoint Online terminée. Cliquez [ici](https://docs.microsoft.com/stream/migrate-from-office-365#microsoft-cloud-deutschland-timeline) pour en savoir plus.

## <a name="how-is-the-migration-organized"></a>Comment la migration est-elle organisée ?

Cette illustration représente les différents composants d’Office 365 et Dynamics 365 lors de la migration vers les nouveaux centres de calcul allemands.

![Composants d’Office 365 et Dynamics 365 lors de la migration vers les nouveaux centres de centre d’Allemagne](../media/ms-cloud-germany-migration-opt-in/migration-organization.png)

La migration est exécutée dans les phases qui commencent lorsque vous [optez pour la migration](https://aka.ms/office365germanymoveoptin). La plupart des phases de migration sont exécutées en tant qu’opérations de service principal avec une interaction client minimale requise et sont exécutées une phase après l’autre. Le centre de messages du centre d’administration 365 de Microsoft pour le processus de migration indique le début des tâches supplémentaires dirigées par le client et l’état de la migration globale. Exemple de tâches : mises à jour DNS gérées par le client, reconfiguration de l’installation hybride pour les clients hybrides Exchange ou migration Azure.

La migration ne commence pas immédiatement lorsque l’abonnement est exécuté. Votre organisation est ajoutée à la liste des clients qui sont planifiés pour une migration ultérieure. Vous pouvez commencer les phases de pré-travail dès que celles-ci sont essentielles pour garantir la réussite de la migration et de l’utilisation.

Une semaine avant le début de la migration client, vous recevrez une notification dans le service du centre de messages comme un avertissement final indiquant que tous les éléments prérequis doivent être terminés.

La migration va déplacer votre client Azure AD du service d’Office Azure Allemagne vers l’instance de services Office 365 d’Azure AD dans la région de l’UE.

La phase suivante est la migration de vos abonnements et licences utilisateur&#39;s de client à partir de produits spécifiques en Allemagne.

Une fois toutes les étapes terminées, y compris la migration Azure client, votre client est finalisé dans le service Office 365 services et la migration est marquée comme étant terminée. À ce stade, la mise à jour finale du centre de messages vous est fournie. Le client n’est désormais pas une organisation Office 365 complète.

Vous êtes informé de la progression de la migration avec les publications du centre de messages. Les publications se produisent à des échéances spécifiques et fournissent des instructions sur la progression d’une étape ainsi que des informations importantes que les clients peuvent utiliser en fonction des exigences de processus. Les notifications du centre de messages sont fournies aux étapes suivantes :

- Début de la migration (5 jours ouvrés avant le début de la migration Azure AD)
- Migration Azure AD terminée
- Migration des abonnements et des licences terminée
- Migration SharePoint terminée
- Migration Exchange terminée
- Skype entreprise achevé
- Dynamics terminée
- Power BI terminé
- Le basculement final des services est terminé.

## <a name="moving-to-the-new-german-regions"></a>Transition vers les nouvelles régions allemandes

Les clients Microsoft Cloud Germany (Microsoft Cloud Deutschland) existants peuvent désormais migrer leur engagement client Office 365, Dynamics 365 et les clients Power Platform. La première étape consiste à [opter pour une migration dirigée par Microsoft](https://aka.ms/office365germanymoveoptin) vers nos nouvelles régions de centre de données allemandes. Lorsque vous renouvelez votre abonnement, vous vous abonnez automatiquement à une migration assistée par Microsoft. Lorsque cela s’est produit, Microsoft communique aux administrateurs clients client les courriers électroniques et le centre de messages du centre d’administration Microsoft 365. Toutefois, si vous préférez démarrer le processus maintenant, vous pouvez vous [inscrire](https://aka.ms/office365germanymoveoptin) directement dans le centre d’administration Microsoft 365 dès aujourd’hui. Les migrations sont censées commencer en début de 2021 et seront effectuées au plus tard le 29 octobre 2021. 

Suite à la migration, les données client principales et les abonnements sont transférés vers les nouvelles régions allemandes.

## <a name="how-to-prepare-for-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Comment préparer la migration vers les services Office 365 dans les nouvelles régions de centre de données allemandes

La première étape consiste à informer Microsoft afin de pouvoir migrer votre abonnement et vos données à partir de Microsoft Cloud Deutschland vers les services Office 365 dans les nouvelles régions de centre de données allemand. Consultez le processus d' [abonnement](https://aka.ms/office365germanymoveoptin) pour obtenir des instructions et notez les éléments suivants :

- Tous les clients qui migrent doivent vérifier la connectivité aux [URL et aux adresses IP office 365](urls-and-ip-address-ranges.md)des Services Office 365, qui incluent les nouvelles régions de centre de l’Allemagne. Inaction peut entraîner une défaillance du service et du client.
- Vous devez passer en revue la description du service de plateforme Office 365 afin de comprendre les fonctionnalités et services qui seront mis à la disposition de votre organisation suite à la migration vers la région allemande.
- Les abonnements à la version d’évaluation ne seront pas migrés et bloqueront la migration de tous les abonnements payants. Avant de commencer la migration, vous devez annuler tous les essais ou les convertir en abonnements payants.

## <a name="where-do-i-go-from-here"></a>Où puis-je aller ?

Consultez la section questions fréquemment posées ci-dessous.

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="is-migration-required"></a>La migration est-elle obligatoire ?

Microsoft propose la migration client Office 365 de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand sans frais supplémentaires. Bien que nous vous recommandons vivement d’opter pour une migration vers les nouvelles régions de centre de contenu allemand, nous continuerons à fournir les mises à jour de sécurité nécessaires à la région Deutschland du Cloud Microsoft.

Services Office 365 dans les nouvelles régions de centre de connaissances allemand :

- Ils offrent des tarifs compétitifs pour [Azure](https://azure.microsoft.com/pricing/calculator/), [Office 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans), [Dynamics 365 Customer engagement](https://dynamics.microsoft.com/pricing/)et [Power BI](https://powerbi.microsoft.com/pricing/).
- Sont connectés au réseau mondial de Microsoft&#39;, qui offrent des centaines de sites Edge réseau, des emplacements d’homologation et des points de sortie pour offrir une expérience utilisateur robuste n’importe où dans le monde.
- Ils vous aident à répondre aux exigences de résidence des données client en Allemagne.
- Offrir notre offre de Cloud internationale complète avec les versions les plus récentes de nos services et de nouvelles fonctionnalités, notamment Microsoft teams et multi-géo dans Office 365. Ils permettent de comparer les produits par région pour [Azure](https://azure.microsoft.com/global-infrastructure/services/?products=all&amp;regions=germany-non-regional,germany-central,germany-north,germany-northeast,germany-west-central), [Office 365](o365-data-locations.md) et [Dynamics 365](https://docs.microsoft.com/dynamics365/get-started/availability).
- Ils offrent toutes les fonctionnalités, une sécurité de qualité professionnelle et des fonctionnalités complètes pour aider les clients à respecter les exigences de conformité et de réglementation.
- Ils sont accessibles via les contrats de services en ligne existants.

### <a name="what-is-the-service-availability-between-the-different-office-365-cloud-service-offerings"></a>Quelle est la disponibilité du service entre les différentes offres de service Cloud d’Office 365 ?

Les 15 services suivants sont disponibles dans l’offre de service Cloud Deutschland Cloud de Microsoft Cloud. Nous n’ajoutons pas de nouveaux services à Microsoft Cloud Deutschland.

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

Nous avons actuellement 29 services dans le cadre des services Office 365 dans les nouvelles régions de centres de données allemands. De nouvelles fonctionnalités et de nouveaux services sont régulièrement disponibles avec les services Office 365 globaux.

1. Exchange Online
2. Référentiel sécurisé du client pour Exchange Online
3. Groupes Microsoft 365
4. Profil Delve
5. MyAnalytics
6. Workplace Analytics
7. Exchange Online Protection
8. Defender pour Office 365
9. Advanced eDiscovery
10. Gestion de la sécurité avancée
11. Gestion des droits relatifs à l’information
12. Gouvernance des données avancée
13. SharePoint Online
14. Référentiel sécurisé du client pour SharePoint Online
15. OneDrive Entreprise
16. Microsoft Stream
17. Skype entreprise (migration vers Microsoft teams pendant la migration)
18. PBX cloud
19. Conférence sur réseau téléphonique commuté
20. Appel sur réseau téléphonique commuté
21. Microsoft Teams
22. Rapports d’administration/rapports d’utilisation
23. Word Online, Excel Online, PowerPoint, OneNote et Visio Online
24. Planificateur
25. Sway
26. Microsoft 365 Apps
27. Outlook Mobile
28. Enterprise Mobility + Security (EMS) E3 (Azure AD Premium P1, Intune et le service RMS)
29. Yammer Online

### <a name="when-will-migration-happen"></a>Quand la migration aura-t-elle lieu ?

**Azure**

Si vous êtes un client Azure uniquement, vous pouvez commencer à [migrer](https://docs.microsoft.com/azure/germany/germany-migration-main) vos ressources Azure vers une autre région dès aujourd’hui. Si vous disposez d’Azure avec Office 365, Dynamics 365 ou Power BI, suivez les étapes ci-dessous.

**Office 365**

[Optez](https://aka.ms/office365germanymoveoptin) pour la migration dirigée par Microsoft aujourd’hui. Lorsque nous sommes prêts à démarrer votre migration, nous vous informerons via le centre de messages dans le centre d’administration 365 de Microsoft.

**Dynamics 365 et Power BI**

Abonnez-vous à la migration orientée Microsoft pour l' [engagement client de Dynamics 365](https://aka.ms/D365ceOptIn) et [Power bi](https://aka.ms/PBIOptIn) dès aujourd’hui. Lorsque nous serons prêts à démarrer votre migration, nous vous informerons via le centre de messages dans le Centre d’administration Microsoft 365.

### <a name="will-the-price-change-for-the-office-365-services-that-i-use"></a>Le tarif sera-t-il modifié pour les services Office 365 que j’utilise ?

Oui. Les tarifs dans les régions de nuage globales de Microsoft&#39;(y compris les nouvelles régions de centres de informations) sont généralement moins élevés.

### <a name="during-the-subscription-migration-what-skus-and-licenses-will-be-applied-to-my-organization-and-users"></a>Lors de la migration des abonnements, quelles références et licences seront appliquées à mon organisation et à ses utilisateurs ?

Lors de la migration de Microsoft Cloud Deutschland vers les services Office 365, les références SKU propres au service d’Allemagne sont remplacées par des versions globales du même SKU ou similaires. Dans la plupart des cas, le SKU dans Office 365 services est le même, cependant, il n’y a pas assez de remplacements lorsque le SKU en Allemagne n’est plus disponible dans les services Office 365. Si vous souhaitez mettre à jour le SKU affecté à votre organisation une fois la migration terminée, contactez votre vendeur pour ajouter ou modifier les services affectés.

| Microsoft Cloud Deutschland-SKU du produit (DE) | Microsoft Cloud global-produit SKU (WW) |
| --- | --- |
| Client Lockbox \_ de (Lockbox \_ de) | Référentiel sécurisé (LOCKBOX) |
| Dynamics 365 Enterprise Edition-stockage de base de données supplémentaire \_ (CRMSTORAGE \_ de) | Dynamics 365 Enterprise Edition-stockage de base de données supplémentaire (CRMSTORAGE) |
| Dynamics 365 Enterprise Edition-instance de non-production supplémentaire \_ de (CRMTESTINSTANCE \_ de) | Dynamics 365 Enterprise Edition-instance de non-production supplémentaire (CRMTESTINSTANCE) |
| Dynamics 365 pour le service clientèle Enterprise Edition \_ de (DYN365 \_ Enterprise \_ client \_ service \_ de) | Dynamics 365 pour le service clientèle Enterprise Edition ( \_ \_ service client entreprise DYN365 \_ ) |
| Dynamics 365 pour Sales Enterprise Edition \_ de (DYN365 \_ Enterprise \_ Sales \_ de) | Dynamics 365 pour Sales Enterprise Edition (DYN365 \_ Enterprise \_ Sales) |
| Dynamics 365 pour les membres de l’équipe Enterprise Edition \_ de (DYN365 \_ entreprise \_ \_ membres de l’équipe \_ de) | Dynamics 365 pour les membres de l’équipe Enterprise Edition (membres de l' \_ équipe DYN365 entreprise \_ \_ ) |
| Dynamics 365 plan 1 Enterprise Edition \_ de (DYN365 \_ Enterprise \_ PLAN1 \_ de) | Dynamics 365 plan 1 Enterprise Edition (DYN365 \_ Enterprise \_ PLAN1) |
| Services ECAL (EOA, EOP, DLP) \_ de (ECAL \_ services \_ de) | Services ECAL (EOA, EOP, DLP) (ECAL \_ Services) |
| Enterprise Mobility + Security E3 \_ de (EMS \_ de) | Enterprise Mobility + Security E3 (EMS) |
| Exchange Online (plan 1) \_ de (EXCHANGESTANDARD \_ de) | Exchange Online (plan 1) (EXCHANGESTANDARD) |
| Exchange Online (plan 2) \_ de (EXCHANGEENTERPRISE \_ de) | Exchange Online (plan 2) (EXCHANGEENTERPRISE) |
| Archivage Exchange Online pour Exchange Online \_ de (EXCHANGEARCHIVE \_ addon \_ de) | Archivage Exchange Online pour Exchange Online (EXCHANGEARCHIVE \_ addon) |
| Archivage Exchange Online pour Exchange Server \_ de (EXCHANGEARCHIVE \_ de) | Archivage Exchange Online pour Exchange Server (EXCHANGEARCHIVE) |
| Exchange Online Essentials \_ de (Exchange \_ S \_ Essentials \_ de) | Exchange Online Essentials (EXCHANGE \_ S \_ Essentials) |
| Exchange Online Kiosk \_ de (EXCHANGEDESKLESS \_ de) | Borne Exchange Online (EXCHANGEDESKLESS) |
| Exchange Online Protection \_ de (EOP \_ entreprise \_ de) | Exchange Online Protection (EOP \_ Enterprise) |
| Microsoft 365 Business standard (Office 365 \_ Business \_ Premium) | Microsoft 365 Business standard (Office 365 \_ Business \_ Premium) |
| Instance de Microsoft Dynamics CRM Online \_ de (CRMINSTANCE \_ de) | Instance de Microsoft Dynamics CRM Online (CRMINSTANCE) |
| Office 365 a1 pour Université \_ de (STANDARDWOFFPACK \_ universitaire \_ de) | Office 365 a1 pour facultés (STANDARDWOFFPACK \_ universitaire) |
| Office 365 a1 pour étudiants \_ de (STANDARDWOFFPACK \_ Student \_ de) | Office 365 a1 pour étudiants (STANDARDWOFFPACK \_ Student) |
| Office 365 Advanced Compliance \_ de (EQUIVIO \_ Analytics \_ de) | Microsoft 365 E5 conformité ( \_ conformité de la protection des informations \_ ) |
|Microsoft Defender pour Office 365 (plan 1) \_ de (ATP \_ Enterprise \_ de) |Microsoft Defender pour Office 365 (plan 1) (ATP \_ ) |
| Office 365 Business Essentials \_ de (O365 \_ Business \_ Essentials \_ de) | Microsoft 365 Business Basic (O365 \_ Business \_ Essentials) |
| Office 365 Business Premium \_ de (O365 \_ Business \_ Premium \_ de) | Microsoft 365 Business standard (Office 365 \_ Business \_ Premium) |
| Office 365 Business \_ de (O365 \_ Business \_ de) | Microsoft 365 apps pour les entreprises (Office 365 \_ entreprise) |
| Office 365 E1 \_ de (STANDARDPACK \_ de) | Office 365 E1 (STANDARDPACK) |
| Office 365 E3 sans ProPlus \_ de (ENTERPRISEPACKWITHOUTPROPLUS \_ de) | Office 365 E3 sans ProPlus (ENTERPRISEPACKWITHOUTPROPLUS) |
| Office 365 E3 \_ de (ENTERPRISEPACK \_ de) | Office 365 E3 (ENTERPRISEPACK) |
| Office 365 entreprise E1 \_ de (STANDARDPACK \_ de) | Office 365 entreprise E1 (STANDARDPACK) |
| Office 365 entreprise E3 \_ de (ENTERPRISEPACK \_ de) | Office 365 entreprise E3 (ENTERPRISEPACK) |
| Office 365 extra File Storage of \_ (SHAREPOINTSTORAGE \_ de) | Stockage de fichiers supplémentaire Office 365 (SHAREPOINTSTORAGE) |
| Office 365 F1 \_ de (DESKLESSPACK \_ de) | Office 365 F1 (DESKLESSPACK) |
| Office 365 ProPlus pour Université \_ de (OFFICESUBSCRIPTION \_ universitaire \_ de) | Office 365 ProPlus pour les enseignants (OFFICESUBSCRIPTION \_ universitaire) |
| Office 365 ProPlus pour étudiants \_ de (OFFICESUBSCRIPTION \_ Student \_ de) | Office 365 ProPlus pour étudiants (OFFICESUBSCRIPTION \_ Student) |
| Office 365 ProPlus \_ de (OFFICESUBSCRIPTION \_ de) | Office 365 ProPlus (OFFICESUBSCRIPTION) |
| OneDrive entreprise (plan 1) \_ de (WACONEDRIVESTANDARD \_ de) | OneDrive entreprise (plan 1) (WACONEDRIVESTANDARD) |
| OneDrive entreprise (plan 2) \_ de (WACONEDRIVEENTERPRISE \_ de) | OneDrive entreprise (plan 2) (WACONEDRIVEENTERPRISE) |
| Power BI Pro for Université \_ de (Power \_ bi \_ Pro \_ Faculté \_ de) | Power BI Pro for Université (Université de POWER \_ bi \_ Pro \_ ) |
| Power BI Pro \_ de (Power \_ bi \_ Pro \_ de) | Power BI Pro (POWER \_ bi \_ Pro) |
| Project Online Essentials \_ de (PROJECTESSENTIALS \_ de) | Project Online Essentials (PROJECTESSENTIALS) |
| Project Online Premium \_ de (PROJECTPREMIUM \_ de) | Project Online Premium (PROJECTPREMIUM) |
| Project Online professionnel \_ de (PROJECTPROFESSIONAL \_ de) | Project Online professionnel (PROJECTPROFESSIONAL) |
| Plan de projet 3 \_ de (PROJECTPROFESSIONAL \_ de) | Plan de projet 3 (PROJECTPROFESSIONAL) |
| Office 365 E4 \_ de (ENTERPRISEWITHSCAL \_ de) | Office 365 E3 (ENTERPRISEPACK) |
| SharePoint Online (plan 1) \_ de (SHAREPOINTSTANDARD \_ de) | SharePoint Online (plan 1) (SHAREPOINTSTANDARD) |
| SharePoint Online (plan 2) \_ de (SHAREPOINTENTERPRISE \_ de) | SharePoint Online (plan 2) (SHAREPOINTENTERPRISE) |
| Skype entreprise Online (plan 1) \_ de (MCOIMP \_ de) | Office 365 E1 (STANDARDPACK) |
| Skype entreprise Online (plan 1) \_ de (MCOIMP \_ de) | Skype entreprise Online (plan 1) (MCOIMP) |
| Skype entreprise Online (plan 2) \_ de (MCOSTANDARD \_ de) | Skype entreprise Online (plan 2) (MCOSTANDARD) |
| Skype entreprise plus licence d’accès client \_ de (MCOPLUSCAL \_ de) | Skype entreprise plus CAL (MCOPLUSCAL) |
| Visio Online plan 1 pour Université \_ de (VISIOONLINE \_ PLAN1 \_ FAC \_ de) | Visio Online plan 1 pour facultés (VISIOONLINE \_ PLAN1 \_ FAC) |
| Visio Online plan 1 \_ de (VISIOONLINE \_ PLAN1 \_ de) | Visio Online plan 1 (VISIOONLINE \_ PLAN1) |
| Visio Online plan 2 pour Université \_ de (VISIOCLIENT \_ universitaire \_ de) | Visio Online plan 2 pour les enseignants (VISIOCLIENT \_ universitaire) |
| Visio Online plan 2 \_ de (VISIOCLIENT \_ de) | Visio Online plan 2 (VISIOCLIENT) |
| Visio plan 1 \_ de (VISIOONLINE \_ PLAN1 \_ de) | Visio plan 1 (VISIOONLINE \_ PLAN1) |
| Visio plan 2 \_ de (VISIOCLIENT \_ de) | Visio plan 2 (VISIOCLIENT) |
|||

### <a name="how-do-i-get-help-from-microsoft-to-migrate-to-a-new-region-or-answer-support-questions"></a>Comment obtenir de l’aide de la part de Microsoft pour effectuer la migration vers une nouvelle région ou répondre à des questions de support ?

Si vous avez des questions, vous pouvez nous contacter ou votre partenaire :

- Pour Azure, vous pouvez envoyer de [nouvelles demandes de support](https://portal.microsoftazure.de/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest) dans le portail Azure.
- Pour Office 365, vous pouvez envoyer des questions à l’aide du &quot; lien besoin d’aide ? &quot; du [Centre d’administration Microsoft 365](https://portal.office.de/).
- Si vous êtes un client Dynamics 365 engagement client et Power BI et que vous avez également Office 365, vous pouvez soumettre des questions à l’aide du &quot; lien vous avez besoin d’aide ? &quot; du [Centre d’administration Microsoft 365](https://portal.office.de/). Les options de support de Dynamics 365 Customer Engagement se trouvent [ici](https://docs.microsoft.com/dynamics365/get-started/support/). Les options de support de Power BI se trouvent [ici](https://powerbi.microsoft.com/support/).

## <a name="more-information"></a>Plus d’informations

Des informations supplémentaires sur la migration vers les nouvelles régions de centre de données allemand sont à venir. Ajoutez cette page aux favoris afin de pouvoir archiver et conserver à jour.

- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](https://aka.ms/office365germanymoveoptin)
- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [URL et plages d’adresses IP Office 365](https://aka.ms/o365endpoints)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
