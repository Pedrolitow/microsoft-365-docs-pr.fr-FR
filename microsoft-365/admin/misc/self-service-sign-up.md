---
title: Utilisation de l’inscription en libre-service dans votre organisation
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: seemg, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_signup
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
description: Découvrez l’inscription en libre-service Microsoft 365 et les programmes libre-service disponibles tels que Microsoft Power Apps, Microsoft Power Automate et Dynamics 365 for Finance.
ms.date: 03/17/2021
ms.openlocfilehash: aa2c926e380f07dd43e3c3da14cfb389b92a0765
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67323527"
---
# <a name="using-self-service-sign-up-in-your-organization"></a>Utilisation de l’inscription en libre-service dans votre organisation

L’inscription en libre-service permet aux utilisateurs de votre organisation de s’inscrire plus facilement à services en ligne auprès de Microsoft. Nous appelons ce processus d’inscription « inscription en libre-service », car vos utilisateurs peuvent s’inscrire pour utiliser les services payés par votre abonnement ou utiliser des services gratuits, sans vous demander d’agir en leur nom.

## <a name="how-self-service-sign-up-works"></a>Fonctionnement de l’inscription en libre-service

L’exemple suivant décrit le fonctionnement de l’auto-inscription pour une école. Le même processus fonctionne pour toute organisation dont les programmes en libre-service sont activés dans son locataire.

1. Les étudiants et les membres du corps professoral ont des adresses e-mail scolaires qui indiquent qu’ils sont associés à votre établissement. Par exemple, l’adresse e-mail jakob@uw.edu peut indiquer un étudiant à l’Université de Washington.
2. Les étudiants et les enseignants se rendent sur [notre site web](https://go.microsoft.com/fwlink/p/?LinkId=536628) et utilisent leur adresse e-mail pour s’inscrire aux services offerts par votre organisation, tels que Applications Microsoft 365 pour les grandes entreprises. Ils peuvent également s’inscrire à d’autres services gratuits que nous offrons.
3. Nous validons leur adresse e-mail, puis ils peuvent commencer à utiliser Microsoft 365, Power BI ou d’autres services immédiatement.
4. En tant qu’administrateur de l’entreprise, vous pouvez voir qui s’est inscrit à un abonnement en sélectionnant l’abonnement dans la page **Licences** du Centre d'administration Microsoft 365. De cette façon, vous pouvez voir s’il existe des licences nouvelles ou non reconnues pour les services dans votre locataire. Pour contrôler si les utilisateurs peuvent s’inscrire à des abonnements en libre-service, utilisez l’applet de commande PowerShell [Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings) avec le paramètre **AllowAdHocSubscriptions** . Pour plus d’informations, consultez [Comment faire contrôler les paramètres en libre-service ?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="available-self-service-programs"></a>Programmes libre-service disponibles

Voici les programmes en libre-service actuellement disponibles. Cette liste sera mise à jour à mesure que de nouveaux programmes seront ajoutés.

| Programme <br/> | Description <br/> | Informations supplémentaires <br/> | Site web pour l’inscription en libre-service <br/> |
|:-----|:-----|:-----|:-----|
|Office 365 A1**** <br/> |Tout étudiant ou enseignant peut utiliser une adresse e-mail scolaire pour s’inscrire gratuitement Office 365 et obtenir des applications Office pour le web, 1 To de stockage cloud OneDrive et SharePoint Online pour les sites de classe, d’équipe et de projet.  <br/> |[FAQ technique Office 365 Éducation](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Éducation](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Office 365 A1 Plus** <br/> |Les étudiants et les enseignants éligibles peuvent s’inscrire à Office 365 A1 Plus, qui inclut tout ce qui est mentionné ci-dessus, ainsi que Applications Microsoft 365 pour les grandes entreprises. Applications Microsoft 365 pour les grandes entreprises est un logiciel de productivité, notamment Word, PowerPoint, Excel, Outlook, OneNote, Publisher, Access et Skype Entreprise, qui est installé sur votre ordinateur de bureau ou ordinateur portable.  <br/> |[FAQ technique Office 365 Éducation](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Éducation](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Power BI** <br/> |Power BI permet aux utilisateurs de visualiser des données, de partager des découvertes et de collaborer de nouvelles façons intuitives. <br/> Si votre organisation s’abonne déjà, vous pouvez également voir des licences pour « Power BI Pro essai utilisateur individuel », qui offrent aux utilisateurs un accès gratuit limité aux fonctionnalités avancées.  <br/> |[Power BI dans votre organisation](/power-bi/enterprise/service-admin-org-subscription) <br/> |[Microsoft Power BI](https://go.microsoft.com/fwlink/p/?LinkId=536629) <br/> |
|**Rights Management Services (RMS)** <br/> |RMS pour les particuliers est un abonnement libre-service gratuit pour les utilisateurs d’une organisation qui ont reçu des fichiers sensibles qui ont été protégés par Azure Rights Management (Azure RMS), mais leur service informatique n’a pas implémenté Azure Rights Management (Azure RMS) ou Active Directory Rights Management Services (AD RMS).  <br/> |[RMS pour les particuliers et les Azure Rights Management](/azure/information-protection/rms-for-individuals) <br/> |[Portail Microsoft Rights Management](https://portal.azure.com/) pour vous permettre de vérifier si vous pouvez ouvrir un document protégé par des droits donné.  <br/> |
|**Microsoft Power Apps** <br/> |Dans Power Apps, vous pouvez gérer les données organisationnelles en exécutant une application que vous avez créée ou que quelqu’un d’autre a créée et partagée avec vous. Les applications s’exécutent sur des appareils mobiles tels que des téléphones, ou vous pouvez les exécuter dans un navigateur en ouvrant Dynamics 365. Vous pouvez créer une variété infinie d’applications, le tout sans apprendre un langage de programmation tel que C#.  <br/> |[Inscription en libre-service à Power Apps](/powerapps/maker/signup-for-powerapps) <br/> |[Microsoft Power Apps](https://go.microsoft.com/fwlink/p/?linkid=841462) <br/> |
|**Dynamics 365 for Financials** <br/> |Obtenez une solution complète de gestion commerciale et financière pour les petites et moyennes entreprises. Dynamics 365 for Financials facilite la commande, la vente, la facturation et la création de rapports, à compter du premier jour.  <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |
|**Microsoft Dynamics 365 for Operations** <br/> |Augmentez votre vitesse de travail. Les outils ERP complets de Dynamics 365 for Operations fournissent une scalabilité globale et une intelligence numérique pour vous aider à croître à votre rythme.  <br/> |[Microsoft Dynamics 365 for Operations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |[Microsoft Dynamics 365 for Operations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |
|**Microsoft AppSource** <br/> |Microsoft AppSource est une destination pour les applications métier logicielles en tant que service basées sur la plateforme cloud Microsoft. AppSource propose des centaines d’applications, de modules complémentaires et de packs de contenu qui étendent les fonctionnalités des produits Microsoft tels qu’Azure, Dynamics 365, Office 365 et Power BI.  <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |
|**Primes incitatives pour les partenaires Microsoft** <br/> |Microsoft Partner Network fournit trois types d’appartenances. Chaque type offre un ensemble d’avantages pour aider votre entreprise à croître. Lorsque vous atteignez vos objectifs, participez au programme au niveau qui répond à vos besoins uniques pour accéder à davantage d’avantages et développer votre relation avec nous et d’autres partenaires du réseau.  <br/> |[Primes incitatives pour les partenaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |[Primes incitatives pour les partenaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |
|**Centre d’affaires Microsoft** <br/> |Le Centre d’affaires Microsoft est le portail pour les clients qui ont effectué des achats via le Contrat produits et services Microsoft (MPSA). <br/> |[Démarrage rapide : S’inscrire au Centre d’affaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841479) <br/> |[Centre d’affaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841470) <br/> |
|**Centre de services de licences en volume Microsoft** <br/> |Le Centre de gestion des licences en volume Microsoft affiche les licences achetées dans le cadre des contrats Enterprise, Select, Education (Campus ou School), Open Value, Open License et ISV Royalty.  <br/> |[Formation et ressources VLSC](https://www.microsoft.com/en-us/Licensing/existing-customer/vlsc-training-and-resources.aspx) <br/> |[Centre de service de licences en volume](https://www.microsoft.com/Licensing/servicecenter/default.aspx) <br/> |
|**Minecraft Education Edition** <br/> |En utilisant Minecraft comme plateforme pour l’apprentissage, les enseignants peuvent motiver et inspirer chaque étudiant à atteindre plus, et enflammer une passion pour l’apprentissage. Rejoignez une communauté d’enseignants qui apprennent à utiliser Minecraft pour libérer le potentiel des étudiants.  <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841480) <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841471) <br/> |
|**Microsoft Stream (basé sur SharePoint)** <br/> |Chargez et partagez des vidéos au sein de votre organisation pour améliorer la communication, la participation et l’apprentissage.  <br/> |[S’inscrire à l’expérience &amp; jour 0](https://go.microsoft.com/fwlink/p/?linkid=841472) <br/> |[Microsoft Stream (basé sur SharePoint)](https://go.microsoft.com/fwlink/p/?linkid=841473) <br/> |
|**Power Automate** <br/> |Power Automate est un produit qui vous aide à configurer des flux de travail automatisés entre vos applications et services favoris pour synchroniser des fichiers, obtenir des notifications, collecter des données, etc.  <br/> |[S’inscrire et se connecter à Power Automate](/power-automate/sign-up-sign-in) <br/> |[Power Automate](https://go.microsoft.com/fwlink/p/?linkid=841465) <br/> |
|**Power Virtual Agents** <br/> |Power Virtual Agents permet aux équipes de créer facilement des bots puissants à l’aide d’une interface graphique guidée sans code sans avoir besoin de scientifiques des données ou de développeurs. Power Virtual Agents résout de nombreux problèmes majeurs liés à la création de bots dans l’industrie d’aujourd’hui. Il élimine l’écart entre les experts en la matière et les équipes de développement qui créent les bots, ainsi que la longue latence entre les équipes qui reconnaissent un problème et mettent à jour le bot pour y remédier.  <br/> |[Détails des licences et de l’accès](/power-virtual-agents/requirements-licensing) <br/> |[S’inscrire à Power Virtual Agents](https://aka.ms/TryPVA) <br/> |
|**Azure AD B2B** <br/> |La collaboration B2B (Business-to-Business) Azure Active Directory (Azure AD) vous permet d’inviter des utilisateurs externes (ou « utilisateurs invités ») à utiliser vos services Azure AD payants. Certaines fonctionnalités sont gratuites, mais pour toutes les fonctionnalités Azure AD payantes, vous pouvez inviter jusqu’à cinq utilisateurs invités pour chaque licence d’édition Azure AD que vous possédez pour un employé ou un utilisateur non invité dans votre locataire. <br/> |[Inscription en libre-service pour Azure AD B2B Collaboration](/azure/active-directory/b2b/self-service-portal) <br/> |[Aide sur les licences Azure Active Directory B2B Collaboration](/azure/active-directory/b2b/licensing-guidance) <br/> |
