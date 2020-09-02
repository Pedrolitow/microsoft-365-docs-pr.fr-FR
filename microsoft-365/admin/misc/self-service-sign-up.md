---
title: Utilisation de l’inscription en libre-service au sein de votre organisation
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- okr_SMB
search.appverid:
- MET150
ms.assetid: 4f8712ff-9346-4c6c-bb63-a21ad7a62cbd
description: Découvrez les programmes libre-service de Microsoft 365 self-service, tels que Microsoft Power Apps, Microsoft Flow et Dynamics 365 for finance.
ms.openlocfilehash: 8e8ed80cc24e3c6ec0a4a9d408d202495de52adb
ms.sourcegitcommit: 25afc0c34edc7f8a5eb389d8c701175256c58ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "47324479"
---
# <a name="using-self-service-sign-up-in-your-organization"></a>Utilisation de l’inscription en libre-service au sein de votre organisation

En libre-service, les utilisateurs de votre organisation peuvent facilement s’inscrire aux services en ligne de Microsoft. Nous appelons ce processus de connexion en libre-service, car vos utilisateurs peuvent s’inscrire pour utiliser les services payés par votre abonnement ou utiliser des services gratuits, sans vous demander de prendre des mesures pour leur compte.
  
## <a name="how-self-service-sign-up-works"></a>Fonctionnement de l’inscription en libre-service

L’exemple suivant décrit le fonctionnement de l’auto-inscription pour un établissement scolaire. Le même processus fonctionne pour toutes les organisations qui ont des programmes en libre-service activés dans leur client.
  
1. Les étudiants et les membres du corps enseignant ont des adresses de messagerie scolaires qui indiquent qu’elles sont associées à votre institution. Par exemple, l’adresse de messagerie jakob@uw.edu peut indiquer un étudiant à l’Université de Washington.
2. Les étudiants et les enseignants accèdent à [notre site Web](https://go.microsoft.com/fwlink/p/?LinkId=536628)et utilisent leur adresse de messagerie pour s’inscrire aux services offerts par votre organisation, tels que les applications Microsoft 365 pour les entreprises. Ils peuvent également s’inscrire aux autres services gratuits que nous proposons.
3. Nous validerons leur adresse de messagerie, puis nous pouvons commencer à utiliser Microsoft 365, Power BI ou d’autres services immédiatement.
4. En tant qu’administrateur d’entreprise, vous pouvez voir qui a souscrit un abonnement en sélectionnant l’abonnement sur la page gestion des **licences** dans le centre d’administration 365 de Microsoft. De cette façon, vous pouvez voir quand des licences de services nouvelles ou non reconnues sont répertoriées dans votre client. Pour contrôler si les utilisateurs peuvent s’inscrire aux abonnements en libre-service, utilisez l’applet de commande PowerShell [Set-MsolCompanySettings](https://docs.microsoft.com/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0) avec le paramètre **AllowAdHocSubscriptions** . Pour plus d’informations, voir [Comment puis-je contrôler les paramètres en libre-service ?](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="available-self-service-programs"></a>Programmes libre-service disponibles

Vous trouverez ci-dessous les programmes libre-service actuellement disponibles. Cette liste sera mise à jour au fur et à mesure que de nouveaux programmes seront ajoutés.
  
|||||
|:-----|:-----|:-----|:-----|
|**Programme** <br/> |**Description** <br/> |**Informations supplémentaires** <br/> |Site Web pour l’inscription en libre-service * * * * <br/> |
|Office 365 a1 * * * <br/> |Tout étudiant ou enseignant peut utiliser une adresse de messagerie scolaire pour s’inscrire gratuitement à Office 365 et obtenir des applications Office pour le Web, 1 to d’espace de stockage OneDrive sur le Cloud et SharePoint Online pour les sites de cours, d’équipe et de projet.  <br/> |[FAQ technique sur l’éducation Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536625) <br/> |[Office 365 Éducation](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Office 365 a1 plus** <br/> |Les étudiants et enseignants éligibles peuvent s’inscrire à Office 365 a1 plus, ce qui inclut tous les éléments mentionnés ci-dessus, ainsi que les applications Microsoft 365 pour les entreprises. Les applications Microsoft 365 pour Enterprise sont des logiciels de productivité, notamment Word, PowerPoint, Excel, Outlook, OneNote, Publisher, Access et Skype entreprise, qui est installé sur votre ordinateur de bureau ou portable.  <br/> |[FAQ technique sur l’éducation Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536625) <br/> |[Office 365 Éducation](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Power BI** <br/> |Power BI permet aux utilisateurs de visualiser des données, de partager des découvertes et de collaborer de façon intuitive. <br/> Si votre organisation vous abonne déjà, vous pouvez également consulter la rubrique « Power BI Pro Individual User Trial », qui offre aux utilisateurs un accès limité et gratuit à des fonctionnalités avancées.  <br/> |[Power BI dans votre organisation](https://go.microsoft.com/fwlink/p/?LinkId=536626) <br/> |[Microsoft Power BI](https://go.microsoft.com/fwlink/p/?LinkId=536629) <br/> |
|**Rights Management Services (RMS)** <br/> |RMS pour les personnes est un abonnement gratuit en libre-service pour les utilisateurs d’une organisation qui ont reçu des fichiers sensibles protégés par Azure Rights Management (Azure RMS), mais leur service informatique n’a pas implémenté Azure Rights Management (Azure RMS) ou Active Directory Rights Management Services (AD RMS).  <br/> |[RMS pour les particuliers et Azure Rights Management](https://go.microsoft.com/fwlink/p/?LinkId=536627) <br/> |[Microsoft Rights Management Portal](https://portal.azure.com/) pour vérifier si vous pouvez ouvrir un document donné protégé par des droits.  <br/> |
|**Microsoft Power Apps** <br/> |Dans les PowerApps, vous pouvez gérer les données de l’organisation en exécutant une application que vous avez créée ou qu’une autre personne a créée et partagée avec vous. Les applications s’exécutent sur des appareils mobiles tels que des téléphones ou vous pouvez les exécuter dans un navigateur en ouvrant Dynamics 365. Vous pouvez créer une variété infinie d’applications, tout en n’apprenant pas de langage de programmation tel que C#.  <br/> |[Inscription en libre-service pour les PowerApp](https://go.microsoft.com/fwlink/p/?linkid=841461) <br/> |[Microsoft Power Apps](https://go.microsoft.com/fwlink/p/?linkid=841462) <br/> |
|**Dynamics 365 pour les finances** <br/> |Obtenir une solution de gestion commerciale et financière complète pour les petites et moyennes entreprises. La fonctionnalité Dynamics 365 pour les finances facilite les opérations de tri, de vente, de facturation et de création de rapports, à partir du jour 1.  <br/> |[Microsoft Dynamics 365 pour les finances](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |[Microsoft Dynamics 365 pour les finances](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |
|**Microsoft Dynamics 365 pour les opérations** <br/> |Augmentez votre vitesse d’activité. Les outils ERP complets de Dynamics 365 pour les opérations offrent une évolutivité globale et une intelligence numérique pour vous aider à évoluer à votre rythme.  <br/> |[Microsoft Dynamics 365 pour les opérations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |[Microsoft Dynamics 365 pour les opérations](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |
|**Microsoft AppSource** <br/> |Microsoft AppSource est une destination pour les applications métiers logicielles en tant que service basées sur la plateforme Cloud de Microsoft. AppSource comprend des centaines d’applications, de modules complémentaires et de packs de contenu qui étendent les fonctionnalités des produits Microsoft tels que Azure, Dynamics 365, Office 365 et Power BI.  <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |
|**Microsoft Partner Incentive** <br/> |Le réseau partenaire de Microsoft fournit trois types d’appartenances. Chaque type offre un ensemble de prestations pour aider votre entreprise à croître. À mesure que vous atteignez vos objectifs, participez au programme au niveau qui répond à vos besoins uniques et développez votre relation avec nous et d’autres partenaires sur le réseau.  <br/> |[Microsoft Partner Incentive](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |[Microsoft Partner Incentive](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |
|**Centre d’affaires Microsoft** <br/> |Microsoft Business Center est le portail pour les clients qui ont effectué des achats via le contrat de services et de produits Microsoft (MPSA). <br/> |[Démarrage rapide : Inscrivez-vous au centre d’affaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841479) <br/> |[Centre d’affaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841470) <br/> |
|**Centre de service de licences en volume Microsoft** <br/> |Le centre de service de licences en volume Microsoft affiche les licences achetées sous entreprise, Select, Education (campus ou scolaires), Open Value, Open License et les accords de droits ISV.  <br/> |[Formation et ressources VLSC](https://www.microsoft.com/en-us/Licensing/existing-customer/vlsc-training-and-resources.aspx) <br/> |[Centre de service de licence en volume](https://www.microsoft.com/Licensing/servicecenter/default.aspx) <br/> |
|**Minecraft éducation** <br/> |En utilisant Minecraft comme plate-forme d’apprentissage, les enseignants peuvent motiver et inspirer chaque étudiant pour y parvenir plus et s’enflammer une passion pour l’apprentissage. Participez à une communauté d’enseignants qui apprennent à utiliser Minecraft pour déverrouiller le potentiel des étudiants.  <br/> |[Minecraft éducation](https://go.microsoft.com/fwlink/p/?linkid=841480) <br/> |[Minecraft éducation](https://go.microsoft.com/fwlink/p/?linkid=841471) <br/> |
|**Microsoft Stream** <br/> |Téléchargez et partagez des vidéos au sein de votre organisation pour améliorer la communication, la participation et l’apprentissage.  <br/> |[Expérience de la journée de connexion &amp; 0](https://go.microsoft.com/fwlink/p/?linkid=841472) <br/> |[Microsoft Stream](https://go.microsoft.com/fwlink/p/?linkid=841473) <br/> |
|**Power Automate** <br/> |Power automate est un produit qui vous permet de configurer des flux de travail automatisés entre vos applications et services préférés pour synchroniser des fichiers, obtenir des notifications, collecter des données et bien plus encore.  <br/> |[S’inscrire et se connecter pour une mise à l’arrêt automatique](https://docs.microsoft.com/power-automate/sign-up-sign-in) <br/> |[Power Automate](https://go.microsoft.com/fwlink/p/?linkid=841465) <br/> |
|**Power Virtual Agents** <br/> |Les agents virtuels de puissance permettent aux équipes de créer facilement des robots puissants à l’aide d’une interface graphique interactive sans code sans avoir besoin de recourir à des scientifiques de données ou à des développeurs. Les agents virtuels de puissance abordent la plupart des problèmes majeurs liés au développement de robots dans le secteur d’aujourd’hui. Elle élimine le fossé entre les experts techniques et les équipes de développement qui créent les robots, ainsi que la latence longue entre les équipes qui reconnaissent un problème et mettent à jour le bot pour l’adresser.  <br/> |[Licences et informations d’accès](https://go.microsoft.com/fwlink/?linkid=2113708) <br/> |[S’inscrire aux agents virtuels de l’alimentation](https://aka.ms/TryPVA) <br/> |
|**B2B Azure AD** <br/> |Azure Active Directory (Azure AD) collaboration B2B (Business-to-Business) vous permet d’inviter des utilisateurs externes (ou des « utilisateurs invités ») à utiliser vos services Azure AD sponsorisés. Certaines fonctionnalités sont gratuites, mais pour les fonctionnalités Azure AD payantes, vous pouvez inviter jusqu’à cinq utilisateurs invités pour chaque licence Azure AD Edition que vous possédez pour un employé ou un utilisateur non invité de votre client. <br/> |[Libre-service pour l’inscription à la collaboration B2B Azure AD](https://docs.microsoft.com/azure/active-directory/b2b/self-service-portal) <br/> |[Guide des licences pour la collaboration B2B Azure Active Directory](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance) <br/> |