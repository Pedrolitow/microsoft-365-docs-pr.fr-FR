---
title: Utilisation de l’inscription en libre-service dans votre organisation
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: seemg, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_SMB
- commerce_signup
search.appverid: MET150
description: Découvrez les Microsoft 365 l’inscription en libre-service et les programmes libre-service disponibles tels que Microsoft Power Apps, Microsoft Flow et Dynamics 365 for Finance.
ms.date: 03/17/2021
ms.openlocfilehash: e03f82903b8aa81db2425769a23d7ec379120526
ms.sourcegitcommit: 9469d16c6bbd29442a6787beaf7d84fb7699c5e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2021
ms.locfileid: "58400210"
---
# <a name="using-self-service-sign-up-in-your-organization"></a>Utilisation de l’inscription en libre-service dans votre organisation

L’inscription en libre-service permet aux utilisateurs de votre organisation de s’inscrire plus facilement aux services en ligne de Microsoft. Nous appelons ce processus d’inscription « inscription en libre-service », car vos utilisateurs peuvent s’inscrire pour utiliser les services payés par votre abonnement ou utiliser des services gratuits, sans vous demander d’agir en leur nom.

## <a name="how-self-service-sign-up-works"></a>Fonctionnement de l’inscription en libre-service

L’exemple suivant décrit le fonctionnement de l’inscription autonome pour un établissement scolaire. Le même processus fonctionne pour toute organisation dont les programmes libre-service sont activés dans son client.

1. Les étudiants et les membres du corps enseignant ont des adresses de messagerie qui indiquent qu’ils sont associés à votre établissement. Par exemple, l’adresse de jakob@uw.edu peut indiquer un étudiant de l’Université de Washington.
2. Les étudiants et les enseignants se connectent à notre [site web](https://go.microsoft.com/fwlink/p/?LinkId=536628)et utilisent leur adresse de messagerie pour s’inscrire aux services que votre organisation propose, tels Applications Microsoft 365 pour les grandes entreprises. Ils peuvent également s’inscrire à d’autres services gratuits que nous proposons.
3. Nous validons leur adresse e-mail, puis ils peuvent commencer à utiliser Microsoft 365, Power BI ou d’autres services immédiatement.
4. En tant qu’administrateur commercial, vous pouvez voir qui s’est inscrit à un abonnement en sélectionnant l’abonnement sur la **page** Gestion des licences dans la Centre d’administration Microsoft 365. Ainsi, vous pouvez voir s’il existe des licences nouvelles ou non reconnues pour les services dans votre client. Pour contrôler si les utilisateurs peuvent s’inscrire à des abonnements en libre-service, utilisez l’cmdlet [PowerShell Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings) avec le paramètre **AllowAdHocSubscriptions.** Pour plus d’informations, [voir Comment contrôler les paramètres libre-service ?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="available-self-service-programs"></a>Programmes libre-service disponibles

Voici les programmes en libre-service actuellement disponibles. Cette liste sera mise à jour à mesure que de nouveaux programmes seront ajoutés.

| Programme <br/> | Description <br/> | Informations supplémentaires <br/> | Site web pour l’inscription en libre-service <br/> |
|:-----|:-----|:-----|:-----|
|Office 365 A1**** <br/> |Tout étudiant ou enseignant peut utiliser une adresse de messagerie scolaire pour s’inscrire à des Office 365 gratuites et obtenir des applications Office pour le web, 1 To de stockage cloud OneDrive et SharePoint Online pour les sites de cours, d’équipe et de projet.  <br/> |[Office 365 Éducation FAQ technique](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Éducation](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Office 365 A1 Plus** <br/> |Les étudiants et enseignants éligibles peuvent s’inscrire à Office 365 A1 Plus, qui inclut tout ce qui est mentionné plus Applications Microsoft 365 pour les grandes entreprises. Applications Microsoft 365 pour les grandes entreprises logiciels de productivité, notamment Word, PowerPoint, Excel, Outlook, OneNote, Publisher, Access et Skype Entreprise, installés sur votre ordinateur de bureau ou ordinateur portable.  <br/> |[Office 365 Éducation FAQ technique](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Éducation](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Power BI** <br/> |Power BI permet aux utilisateurs de visualiser des données, de partager des découvertes et de collaborer de façon intuitive. <br/> Si votre organisation s’abonne déjà, vous pouvez également voir des licences pour « Power BI Pro Version d’essai de l’utilisateur individuel », qui offrent aux utilisateurs un accès limité et gratuit aux fonctionnalités avancées.  <br/> |[Power BI dans votre organisation](./power-bi-in-your-organization.md) <br/> |[Microsoft Power BI](https://go.microsoft.com/fwlink/p/?LinkId=536629) <br/> |
|**Rights Management Services (RMS)** <br/> |RMS pour les individus est un abonnement libre-service pour les utilisateurs d’une organisation qui ont reçu des fichiers sensibles qui ont été protégés par Azure Rights Management (Azure RMS), mais leur service informatique n’a pas implémenté Azure Rights Management (Azure RMS) ou services AD RMS (Active Directory Rights Management Services) (AD RMS).  <br/> |[RMS pour les individus et les Azure Rights Management](/azure/information-protection/rms-for-individuals) <br/> |[Portail Microsoft Rights Management pour](https://portal.azure.com/) vérifier si vous pouvez ouvrir un document protégé par des droits donné.  <br/> |
|**Microsoft Power Apps** <br/> |Dans Power Apps, vous pouvez gérer les données organisationnelles en exécutant une application que vous avez créée ou que quelqu’un d’autre a créée et partagée avec vous. Les applications s’exécutent sur des appareils mobiles tels que des téléphones, ou vous pouvez les exécuter dans un navigateur en ouvrant Dynamics 365. Vous pouvez créer une variété infinie d’applications, le tout sans apprendre un langage de programmation tel que C#.  <br/> |[Inscription en libre-service à Power Apps](/powerapps/maker/signup-for-powerapps) <br/> |[Microsoft Power Apps](https://go.microsoft.com/fwlink/p/?linkid=841462) <br/> |
|**Dynamics 365 for Financials** <br/> |Obtenez une solution complète de gestion financière et d’entreprise pour les petites et moyennes entreprises. Dynamics 365 for Financials facilite la commande, la vente, la facturation et les rapports, à partir du premier jour.  <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |
|**Microsoft Dynamics 365 for Operations** <br/> |Augmentez votre vitesse d’activité. Les outils ERP complets de Dynamics 365 for Operations fournissent une évolutivité et une intelligence numérique globales pour vous aider à développer à votre rythme.  <br/> |[Microsoft Dynamics 365 for Operations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |[Microsoft Dynamics 365 for Operations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |
|**Microsoft AppSource** <br/> |Microsoft AppSource est une destination pour les applications professionnelles logicielles en tant que service conçues sur la plateforme cloud de Microsoft. AppSource propose des centaines d’applications, d’extensions et de packs de contenu qui étendent les fonctionnalités des produits Microsoft tels qu’Azure, Dynamics 365, Office 365 et Power BI.  <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |
|**Primes incitatives des partenaires Microsoft** <br/> |Microsoft Partner Network fournit trois types d’appartenances. Chaque type offre un ensemble d’avantages pour aider votre entreprise à croître. À mesure que vous atteignez vos objectifs, participez au programme au niveau qui répond à vos besoins uniques pour accéder à d’autres avantages et développer votre relation avec nous et d’autres partenaires dans le réseau.  <br/> |[Primes incitatives des partenaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |[Primes incitatives des partenaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |
|**Microsoft Business Center** <br/> |Le Microsoft Business Center est le portail pour les clients qui ont effectué des achats via le Contrat de produits et services Microsoft (MPSA). <br/> |[Démarrage rapide : s’inscrire au Microsoft Business Center](https://go.microsoft.com/fwlink/p/?linkid=841479) <br/> |[Microsoft Business Center](https://go.microsoft.com/fwlink/p/?linkid=841470) <br/> |
|**Centre de service de licence en volume Microsoft** <br/> |Le Centre de service de licence en volume Microsoft affiche les licences achetées dans le cadre des contrats Enterprise, Sélection, Éducation (Campus ou École), Open Value, Open License et ISV.  <br/> |[Formation et ressources vlsc](https://www.microsoft.com/en-us/Licensing/existing-customer/vlsc-training-and-resources.aspx) <br/> |[Centre de service de licence en volume](https://www.microsoft.com/Licensing/servicecenter/default.aspx) <br/> |
|**Minecraft Education Edition** <br/> |En utilisant Minecraft en tant que plateforme pour l’apprentissage, les enseignants peuvent encourager et encourager chaque étudiant à atteindre d’autres objectifs et à susciter une envie d’apprentissage. Rejoignez une communauté d’enseignants qui apprennent à utiliser Minecraft pour déverrouiller le potentiel des étudiants.  <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841480) <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841471) <br/> |
|**Microsoft Stream (basé sur SharePoint)** <br/> |Télécharger et partagez des vidéos au sein de votre organisation pour améliorer la communication, la participation et l’apprentissage.  <br/> |[Expérience &amp; d’inscription au jour 0](https://go.microsoft.com/fwlink/p/?linkid=841472) <br/> |[Microsoft Stream (basé sur SharePoint)](https://go.microsoft.com/fwlink/p/?linkid=841473) <br/> |
|**Power Automate** <br/> |Power Automate est un produit qui vous aide à configurer des flux de travail automatisés entre vos applications et services favoris pour synchroniser des fichiers, recevoir des notifications, collecter des données, etc.  <br/> |[Inscrivez-vous et connectez-vous Power Automate](/power-automate/sign-up-sign-in) <br/> |[Power Automate](https://go.microsoft.com/fwlink/p/?linkid=841465) <br/> |
|**Power Virtual Agents** <br/> |Power Virtual Agents permet aux équipes de créer facilement des bots puissants à l’aide d’une interface graphique sans code guidée sans avoir besoin de données ou de développeurs. Power Virtual Agents de nombreux problèmes majeurs avec la création de bots dans le secteur aujourd’hui. Cela élimine l’écart entre les experts techniques et les équipes de développement qui construisent les bots, ainsi que la latence longue entre les équipes qui reconnaissent un problème et mettent à jour le bot pour le résoudre.  <br/> |[Détails sur la gestion des licences et l’accès](/power-virtual-agents/requirements-licensing) <br/> |[S’inscrire à Power Virtual Agents](https://aka.ms/TryPVA) <br/> |
|**Azure AD B2B** <br/> |Azure Active Directory collaboration entreprise-entreprise (B2B) (Azure AD) vous permet d’inviter des utilisateurs externes (ou des « utilisateurs invités ») à utiliser vos services Azure AD payants. Certaines fonctionnalités sont gratuites, mais pour toutes les fonctionnalités Azure AD payantes, vous pouvez inviter jusqu’à cinq utilisateurs invités pour chaque licence d’édition Azure AD que vous possédez pour un employé ou un utilisateur non invité dans votre client. <br/> |[Inscription en libre-service pour la collaboration Azure AD B2B](/azure/active-directory/b2b/self-service-portal) <br/> |[Azure Active Directory Conseils sur les licences de collaboration B2B](/azure/active-directory/b2b/licensing-guidance) <br/> |
