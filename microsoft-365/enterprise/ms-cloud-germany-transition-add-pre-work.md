---
title: Pré-travail pour la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/11/2020
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
description: 'Résumé : Soyez opérationnel lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers les services Office 365 dans la nouvelle région de centre de connaissances allemande.'
ms.openlocfilehash: 1bb6a1b80da462da2218f32fbbc2899ae651a3ec
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688454"
---
# <a name="pre-work-for-the-migration-from-microsoft-cloud-deutschland"></a>Pré-travail pour la migration à partir de Microsoft Cloud Deutschland

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Assurer la connectivité réseau aux [URL et adresses IP des services Office 365](https://aka.ms/o365urls). | Tous les clients et services hébergés par le client qui sont utilisés pour accéder au service Office 365 doivent être en mesure d’accéder aux points de terminaison des services Office 365. | Tous les clients de transition et les clients disposant d’un accès réseau restreint à Microsoft Cloud Deutschland. | Action requise. Inaction peut entraîner des défaillances du service ou du logiciel client. |
| Passez en revue et préparez les modifications DNS liées à la migration. | Le client prépare les entrées DNS pour Exchange Online et Exchange Online Protection (enregistrement MX, etc.). | Clients Exchange Online | Il s’agit d’une action recommandée. Aucune action signifie que le courrier électronique des clients migrés peut être acheminé via Microsoft Cloud Deutschland jusqu’à ce que les services Microsoft Cloud Deutschland soient désactivés. |
| Passez en revue et préparez les modifications DNS liées à la migration. | Modification de la zone DNS appartenant au client pour Skype entreprise online. | Clients Skype entreprise Online | -Nous vous recommandons de mettre à jour la durée de vie (TTL) de tous les enregistrements DNS de domaine appartenant au client à 5 minutes pour accélérer l’actualisation des enregistrements DNS. Toutefois, le basculement géré par Microsoft associé à cette modification DNS peut se produire à tout moment dans la fenêtre de modification 24 heures fournie. <br><br> -Une interruption du service est possible à l’avenir. Les utilisateurs ne pourront pas se connecter à Skype entreprise et seront redirigés vers l’expérience de teams migrée dans les services Office 365. |
| Préparer l’utilisateur final et la formation et la préparation de la transition à Microsoft Teams. | Réussir votre transition de Skype vers teams en planifiant la communication et la disponibilité des utilisateurs. | Clients Skype entreprise Online | -Les clients doivent connaître les nouveaux services et utiliser une fois leurs services transférés vers les services Office 365. <br><br> -Après que des modifications DNS ont été apportées pour les domaines personnel client et le domaine initial, les utilisateurs se connectent à Skype entreprise et voient qu’ils sont désormais migrés vers Teams. Cela télécharge également le client de bureau pour teams en arrière-plan. |
| Préparer la formation de l’utilisateur final et de l’administration à propos des utilisateurs qui suppriment et rajoutent leur compte à Microsoft Outlook pour iOS et Android. | Microsoft Outlook pour iOS et Android les comptes configurés avec des boîtes aux lettres dans Microsoft Cloud Deutschland devront peut-être être supprimés et ajoutés à Outlook afin de synchroniser correctement la nouvelle configuration des services Office 365. | Microsoft Outlook pour les clients iOS et Android | Les boîtes aux lettres Outlook précédemment configurées pour Microsoft Cloud Deutschland ne peuvent pas récupérer la nouvelle configuration des services Office 365, ce qui entraîne des erreurs et dégradation des performances d’autres expériences utilisateur. Les administrateurs informatiques sont encouragés à fournir une documentation qui indique de manière proactive aux utilisateurs de supprimer et de rajouter leurs comptes à Microsoft Outlook pour iOS et Android si des problèmes liés à la connexion ou à la synchronisation des messages se produisent après la migration. |
| Préparez-vous à avertir les utilisateurs du redémarrage et de la connexion et de l’extraction de leurs clients après la migration. | La gestion des licences client Office passe de Microsoft Cloud Deutschland aux services Office 365 dans la migration. Les clients récupèrent une nouvelle licence valide après avoir effectué la déconnexion de et de vers les clients Office. | Clients Microsoft 365 apps |  Les produits Office des utilisateurs doivent actualiser les licences à partir des services Office 365. Si les licences ne sont pas actualisées, les produits Office peuvent subir des erreurs de validation de licence. |
| Annulez les abonnements d’essai. | Les abonnements à la version d’évaluation ne seront pas migrés et bloqueront le transfert des abonnements payants. | Tous les clients | Les services d’évaluation sont expirés et ne fonctionnent pas si les utilisateurs y accèdent après l’annulation. |
| Déployer le client de bureau teams pour les utilisateurs qui accèdent à Skype entreprise en Allemagne. | La migration déplace les utilisateurs vers teams pour la collaboration, l’appel et la conversation. Déployez le client teams de bureau ou assurez-vous qu’un navigateur pris en charge est disponible. | Clients Skype entreprise | L’inaction entraînera l’indisponibilité des services de collaboration de teams. |
| Analysez les différences de fonctionnalités de licence entre Microsoft Cloud Deutschland et les services Office 365. | Les services Office 365 incluent des fonctionnalités et des services supplémentaires qui ne sont pas disponibles dans le Cloud Deutschland actuel. Lors du transfert d’abonnement, de nouvelles fonctionnalités seront disponibles pour les utilisateurs. | Tous les clients | -Analysez les différentes fonctionnalités fournies par les licences pour Microsoft Cloud Deutschland et les services Office 365. Commencez par la [Description du service de plateforme Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description). <br><br> -Déterminez si les nouvelles fonctionnalités des services Office 365 doivent être initialement désactivées pour limiter les effets sur les utilisateurs ou la gestion des modifications de l’utilisateur, et modifier les attributions de licence si nécessaire. <br><br> -Préparez les utilisateurs et le personnel du support technique pour les nouveaux services et fonctionnalités fournis par les services Office 365. |
| Créez des stratégies de [rétention](https://docs.microsoft.com/microsoft-365/compliance/retention) à l’échelle de l’organisation à protéger contre la suppression involontaire du contenu lors de la migration.  | -Pour vous assurer que le contenu n’est pas supprimé par inadvertance par les utilisateurs finaux pendant la migration, les clients peuvent choisir d’activer une stratégie de rétention à l’échelle de l’organisation. <br><br> -Bien que la rétention ne soit pas requise, étant donné que les conservations placées à tout moment pendant la migration devraient fonctionner comme prévu, une stratégie de rétention est un mécanisme de sécurité de sauvegarde. En même temps, une stratégie de rétention peut ne pas être utilisée par tous les clients, en particulier les personnes concernées par la conservation. | Clients Office | Appliquez la stratégie de rétention comme décrit dans [Découvrez les stratégies de rétention et les étiquettes de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies). |
| [Sauvegarde de la batterie de serveurs AD FS (Active Directory Federation Services)](ms-cloud-germany-transition-add-adfs.md#backup) pour les scénarios de récupération d’urgence. | Les clients doivent sauvegarder la batterie AD FS de manière appropriée afin de garantir que les approbations de la partie de confiance pour les points de terminaison & Germany peuvent être restaurées sans toucher à l’URI de l’émetteur des domaines. Microsoft recommande d’utiliser la restauration rapide AD FS pour une sauvegarde de la batterie de serveurs et la restauration correspondante, si nécessaire. | Organisations d’authentification fédérée | Action requise. L’inaction entraînera un impact sur le service pendant la migration si la batterie de serveurs AD FS du client échoue. |


## <a name="exchange-online"></a>Exchange Online

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Informez les partenaires externes de la transition à venir vers les services Office 365. | Les configurations d’espace d’adressage de disponibilité permettent le partage d’informations de disponibilité avec Office 365. | Les clients Exchange Online ayant activé l’espace d’adressage calendrier et disponibilité. | Action requise.  Si vous ne le faites pas, vous risquez de provoquer une défaillance du service ou du client lors d’une phase ultérieure de la migration client. |
|||||

Si vous disposez d’un environnement Exchange hybride :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Désinstallez les versions précédentes de l’Assistant de configuration hybride (HCW), puis installez et exécutez la dernière version, 17.0.5378.0, de [https://aka.ms/hybridwizard](https://aka.ms/hybridwizard) . | La dernière version du HCW inclut les mises à jour nécessaires pour prendre en charge les clients qui passent de Microsoft Cloud Deutschland aux services Office 365. <br><br> Les mises à jour incluent les modifications apportées aux paramètres de certificat local pour le connecteur d’envoi et le connecteur de réception. | Clients Exchange Online exécutant un déploiement hybride | Action requise. Si vous ne le faites pas, vous risquez de provoquer une défaillance du service ou du client. |
|||||

## <a name="sharepoint-online"></a>SharePoint Online

Si vous disposez de SharePoint 2013 :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Limitez les flux de travail SharePoint 2013 à utiliser lors de la migration SharePoint Online. | Réduire les flux de travail SharePoint 2013 et effectuer les flux de travail en cours avant les transitions. | Clients SharePoint Online | L’inaction peut entraîner une confusion des utilisateurs et des appels au support technique. |
|||||

## <a name="mobile"></a>Mobile

Si vous utilisez une solution MDM (Mobile Device Management) tierce :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Déterminez si une reconfiguration est nécessaire après la migration. | Les solutions MDM peuvent cibler des `outlook.de` points de terminaison. Dans cette transition vers les services Office 365, les profils clients doivent être mis à jour vers l’URL des services Office 365, `outlook.office365.com` . | Clients Exchange Online et MDM | Les clients peuvent continuer à fonctionner pendant que le `outlook.de` point de terminaison est accessible, mais ils échoueront si les points de terminaison Deutschland Cloud de Microsoft ne sont plus disponibles. |
|||||

## <a name="line-of-business-apps"></a>Applications métiers

Si vous utilisez un service tiers ou des applications métier (LOB) qui sont intégrées à Office 365 : 

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Déterminez si une reconfiguration est nécessaire après la migration. | Les services et applications tiers qui s’intègrent à Office 365 peuvent être codés de manière à s’attendre aux adresses IP et URL de Microsoft Cloud Deutschland. | Tous les clients | Action requise. Inaction peut entraîner des défaillances du service ou du logiciel client. |
|||||

## <a name="azure"></a>Azure 

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Déterminez quels services Azure sont en cours d’utilisation et préparez-vous à la migration future d’Allemagne vers le client des services Office 365 en collaborant avec vos partenaires. Suivez les étapes décrites dans le [Manuel de migration Azure](https://docs.microsoft.com/azure/germany/germany-migration-main). | La migration des ressources Azure est une responsabilité client et nécessite des efforts manuels suivant les étapes prescrites. La compréhension des services utilisés dans l’organisation est essentielle pour réussir la migration des services Azure. <br><br> Office 365 Germany les clients disposant d’abonnements Azure sous la même partition d’identité (Organisation) doivent respecter l’ordre indiqué par Microsoft lorsqu’ils peuvent commencer la migration des abonnements et des services. | Clients Azure | -Les clients peuvent avoir plusieurs abonnements Azure, chaque abonnement contenant des composants d’infrastructure, de services et de plateforme. <br><br> -Les administrateurs doivent identifier les abonnements et les parties prenantes pour s’assurer que la migration et la validation des messages sont possibles dans le cadre de cet événement de migration. <br><br> Le fait de ne pas réussir la migration de ces abonnements et des composants Azure dans la chronologie prescrite a une incidence sur la transition d’Office et Azure AD vers les services Office 365 et peut entraîner une perte de données.  <br><br> -Une notification de centre de messages signale le point de départ de la migration orientée client. |
|||||

## <a name="dynamics-365"></a>Dynamics 365

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Pour les abonnements à Dynamics 365 sandbox, veillez à télécharger l’environnement de production de l’instance SQL Dynamics à partir de votre abonnement Dynamics 365 dans Microsoft Cloud Deutschland. La dernière sauvegarde de production doit être restaurée dans le bac à sable avant la migration bac à sable. | La migration de Dynamics 365 nécessite que les clients s’assurent que l’environnement de bac à sable est actualisé avec la dernière base de données de production. | Clients Microsoft Dynamics | L’équipe FastTrack aidera les clients à effectuer des exécutions sèches pour valider la mise à niveau de la version de 8. x vers la version 9.1. x. |
|||||

## <a name="power-bi"></a>Power BI

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Suppression des objets des abonnements Power BI qui ne seront pas migrés de Power BI Microsoft Cloud Deutschland vers Office 365 services. | La migration des services Power BI nécessite l’intervention du client pour supprimer certains artefacts, tels que des jeux de données et des tableaux de bord. | Clients Power BI | Les administrateurs devront peut-être supprimer les éléments suivants de leur abonnement : <br> -Real-Time des jeux de données (par exemple, des jeux de données en continu ou par émission) <br> -Configuration de passerelle de données locale et source de données Power BI |
|||||

## <a name="dns"></a>DNS

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Vérifiez et préparez la modification du DNS si le DNS actuel comporte une entrée CNAME MSOID. | Modifications de la zone DNS appartenant au client | Clients des services client Office | Mettez à jour la durée de vie (TTL) des enregistrements DNS appartenant au client à 5 minutes s’il existe un CNAME MSOID. |
|||||

## <a name="federated-identity"></a>Identité fédérée

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Générez une approbation de partie de confiance pour les points de terminaison Azure AD globaux. | Les clients doivent créer manuellement une approbation de partie de confiance (RPT) sur des points de terminaison [globaux](https://nexus.microsoftonline-p.com/federationmetadata/2007-06/federationmetadata.xml) . Pour ce faire, vous devez ajouter une nouvelle arborescence RPT via l’interface utilisateur en tirant parti de l’URL des métadonnées de Fédération globale, puis en utilisant les [règles de revendication RPT](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator#:~:text=%20Azure%20AD%20RPT%20Claim%20Rules%20%201,Azure%20AD.%20This%20will%20be%20what...%20More%20) (dans l’aide d’AD FS) pour générer les règles de revendication et les importer dans l’arborescence RPT. | Organisations d’authentification fédérée | Action requise. L’inaction entraînera un impact sur le service pendant la migration. |
|||||

## <a name="more-information"></a>Informations supplémentaires

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client lors de la migration](ms-cloud-germany-transition-experience.md)

Navigation par le biais de la transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure ad](ms-cloud-germany-transition-azure-ad.md), [appareils](ms-cloud-germany-transition-add-devices.md), [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
