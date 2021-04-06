---
title: Activités préalables à la migration de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 03/09/2021
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
description: 'Résumé : Pré-travail lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemands.'
ms.openlocfilehash: e04246626088d9fca653c98246fd4a5b81bc1d30
ms.sourcegitcommit: e0a96e08b7dc29e074065e69a2a86fc3cf0dad01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51591873"
---
# <a name="pre-migration-activities-for-the-migration-from-microsoft-cloud-deutschland"></a>Activités préalables à la migration de Microsoft Cloud Deutschland

Utilisez ces liens pour obtenir les étapes préalables à la migration pertinentes pour votre organisation.

Si vous utilisez

- **Office 365 dans Microsoft Cloud Deutschland**, faites ces [étapes.](#general-tenant-migration-considerations)
- **Domaines personnalisés,** faites [cette étape.](#dns-entries-for-custom-domains)

- **SharePoint Online**, faites [cette étape.](#sharepoint-online)
- **Exchange Online ou** **Exchange hybride**, faites [cette étape.](#exchange-online)
- **Skype Entreprise Online,** faites [cette étape.](#skype-for-business-online)
- **Dynamics 365**, faites [cette étape.](#dynamics365)
- **Power BI**, faites [cette étape.](#power-bi)

- **Active Directory Federation Services** pour Azure AD Connect, faites [ces étapes.](#active-directory-federation-services-ad-fs)
- **Les services tiers ou** les applications métier **qui** sont intégrées à Office 365, faites [cette étape.](#line-of-business-apps)
- Une solution de gestion des périphériques mobiles (MDM) tierce, faites [cette étape.](#mobile-device-management)
- **Services Azure** avec votre abonnement Office 365, faites [cette étape.](#microsoft-azure)

## <a name="general-tenant-migration-considerations"></a>Considérations générales sur la migration des locataires

**S’applique à :** Tous les clients qui utilisent Office 365 dans l’instance cloud De Microsoft Deutschland

Les identificateurs de client et d’utilisateur Office 365 sont conservés pendant la migration. Les appels de service Azure AD sont redirigés de Microsoft Cloud Deutschland vers les services globaux Office 365 et sont transparents pour les services Office 365.

- Les demandes DSR (Data Subject Requests) du Règlement général sur la protection des données (R GDPR) sont exécutées à partir du portail d’administration Azure pour les demandes futures. Toutes les données de diagnostic héritées ou non client résidant dans Microsoft Cloud Deutschland sont supprimées au plus tard 30 jours après.
- Les demandes d’authentification multifacteur (MFA) qui utilisent Microsoft Authenticator s’affichent en tant qu’objectid utilisateur (guid) pendant que le client est copié dans les services Office 365. Les demandes mfa s’exécuteront comme prévu malgré ce comportement d’affichage.  Les comptes Microsoft Authenticator qui ont été activés à l’aide des points de terminaison des services Office 365 affichent le nom d’utilisateur principal (UPN).  Les comptes ajoutés à l’aide des points de terminaison Microsoft Cloud Deutschland afficheront l’objectid utilisateur, mais fonctionneront avec les points de terminaison des services Microsoft Cloud Deutschland et Office 365.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Préparez-vous à informer les utilisateurs du redémarrage et de la signature de leurs clients après la migration. | Les licences client Office passeront de Microsoft Cloud Deutschland aux services Office 365 lors de la migration. Les clients sélectionnent une nouvelle licence valide après s’être désoyé et s’être mis en place avec les clients Office. | Les produits Office des utilisateurs doivent actualiser les licences à partir des services Office 365. Si les licences ne sont pas actualisées, les produits Office peuvent faire l’expérience d’erreurs de validation de licence. |
| Assurez-vous que la connectivité réseau aux URL et adresses IP des [services Office 365](https://aka.ms/o365urls). | Tous les clients et services hébergés par le client qui sont utilisés pour accéder au service Office 365 doivent pouvoir accéder aux points de terminaison des services globaux Office 365. <br>Si vous ou vos partenaires de collaboration avez des règles de pare-feu en place qui empêcheraient l’accès aux URL et adresses IP répertoriées dans les URL et adresses IP des [services Office 365,](https://aka.ms/o365urls) vous devez modifier les règles de pare-feu pour autoriser l’accès aux points de terminaison du service global Office 365| Des défaillances du service ou du logiciel client peuvent se produire si cette étape n’est pas effectuée avant la phase 4  |
| Annulez les abonnements à la version d’essai. | Les abonnements d’essai ne seront pas migrés et bloqueront le transfert des abonnements payants. | Les services d’essai ont expiré et ne fonctionnent pas si les utilisateurs y accèdent après l’annulation. |
| Analysez les différences de fonctionnalités de licence entre Microsoft Cloud Deutschland et les services globaux Office 365. | Les services Office 365 incluent des fonctionnalités et des services supplémentaires qui ne sont pas disponibles dans microsoft Cloud Deutschland actuel. Pendant le transfert d’abonnement, de nouvelles fonctionnalités seront disponibles pour les utilisateurs. | <ul><li> Analysez les différentes fonctionnalités fournies par les licences pour Microsoft Cloud Deutschland et les services globaux Office 365. Commencez par la description du service de la [plateforme Office 365.](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description) </li><li> Déterminez si les nouvelles fonctionnalités des services Office 365 doivent être initialement désactivées pour limiter les effets sur les utilisateurs ou sur la gestion des changements d’utilisateurs, et modifiez les attributions de licence utilisateur selon vos besoins. </li><li>Préparez les utilisateurs et le personnel du service d’aide aux nouveaux services et fonctionnalités fournis par les services Office 365. |
| Créer des stratégies de [rétention à l’échelle de](https://docs.microsoft.com/microsoft-365/compliance/retention) l’organisation pour vous protéger contre la suppression accidentelle de contenu pendant la migration.  |<ul><li>Pour s’assurer que le contenu n’est pas supprimé par inadvertance par les utilisateurs finaux pendant la migration, les clients peuvent choisir d’activer une stratégie de rétention à l’échelle de l’organisation. </li><li>Bien que la rétention ne soit pas requise, dans la mesure où les conservations placées à tout moment pendant la migration doivent fonctionner comme prévu, l’emploi d’une stratégie de rétention est un mécanisme de sécurité de protection de la protection. En même temps, une stratégie de rétention peut ne pas être utilisée par tous les clients, en particulier ceux qui sont préoccupés par la conservation.</li></ul>| Appliquez la stratégie de rétention comme décrit dans [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) Des défaillances du service ou du logiciel client peuvent se produire si cette étape n’est pas effectuée avant la phase 4 sur 9. </li></ul>|
|||||

## <a name="dns-entries-for-custom-domains"></a>Entrées DNS pour les domaines personnalisés

<!-- before phase 9 -->

**S’applique** à : Clients qui définissent un _cnaME msoid_ personnalisé dans leur propre domaine DNS

S’il est configuré, le _cname msoid_ affecte uniquement les clients utilisant le client de bureau Office (Microsoft 365 Apps, Office 365 ProPlus, Office 2019, 2016, ...)

Si vous avez définie un DNS CNAME appelé _msoid_ dans un ou plusieurs espaces de noms DNS que vous possédez, vous devez supprimer le CNAME jusqu’à la fin de la phase 8 au plus tard. Vous pouvez supprimer le _msoid_ CNAME à tout moment avant la fin de la phase 8.

Pour vérifier si vous avez définie un CNAME dans votre espace de noms DNS, suivez les étapes ci-dessous et remplacez _contoso.com_ par votre propre nom de domaine :

```console
nslookup -querytype=CNAME msoid.contoso.com
```

Si la ligne de commande renvoie un enregistrement DNS, supprimez _le cname msoid_ de votre domaine.

## <a name="active-directory-federation-services-ad-fs"></a>Services AD FS (Active Directory Federation Services)

<!-- before phase 4 -->

**S’applique** à : Clients utilisant AD FS sur site pour authentifier les utilisateurs se connectant Microsoft Office 365<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 4

Lire et appliquer les [étapes de migration ADFS](ms-cloud-germany-transition-add-adfs.md)

## <a name="sharepoint-online"></a>SharePoint Online

<!-- before phase 4 -->

**S’applique** à : Clients qui utilisent SharePoint 2013 en local<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 4

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Limitez les flux de travail SharePoint 2013, utilisés pendant la migration SharePoint Online. | Réduisez les flux de travail SharePoint 2013 et terminez les flux de travail en cours avant les transitions. | L’inaction peut semer la confusion chez l’utilisateur et entraîner des appels au service d’aide. |
||||

## <a name="exchange-online"></a>Exchange Online

<!-- before phase 5 -->

**S’applique à**: clients Exchange Online<br>
**Appliqué :** Tout moment avant la fin de la phase 9

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Informez les partenaires externes de la transition à venir vers les services Office 365. |  Les clients doivent informer leurs partenaires avec lesquels ils ont activé le partage de la configuration de l’espace d’adressace de disponibilité et du calendrier (autoriser le partage d’informations de disponibilité avec Office 365). La configuration de la disponibilité doit être effectuée pour utiliser les points de terminaison [Office 365 dans](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide) le monde une fois la migration d’Exchange Online terminée. | Si vous ne le faites pas, le service ou le client échouera lors d’une phase ultérieure de la migration des clients. |
| Informez les utilisateurs des modifications de client IMAP4/POP3/SMTP requises. | Les utilisateurs qui ont des connexions d’appareil aux points de terminaison Microsoft Cloud Deutschland pour les protocoles clients IMAP4, POP3, SMTP sont tenus de mettre à jour manuellement leurs appareils clients pour basculer vers les points de terminaison [office 365 dans](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide)le monde. | Communiquez préalablement cette dépendance aux utilisateurs de ces protocoles et assurez-vous qu’ils basculent vers Outlook Mobile ou Outlook sur le web pendant cette migration. L’échec de la mise à jour des points de terminaison clients entraîne des échecs de connexion client par rapport à Microsoft Cloud Deutschland lors de la migration des boîtes aux lettres utilisateur. |
||||

### <a name="exchange-online-hybrid-configuration"></a>Configuration hybride d’Exchange Online

**S’applique à :** Tous les clients utilisant une configuration exchange hybride active avec des serveurs Exchange locaux<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 5

Les clients d’entreprise qui ont un déploiement hybride d’Exchange Online et une Exchange Server exécutent l’Assistant Configuration hybride (HCW) pour maintenir et établir la configuration hybride. Lors de la transition de Microsoft Cloud Deutschland vers la région Office 365 Germany, l’administrateur doit ré-exécuter la dernière version de HCW en mode « Office 365 Germany » avant le début de la migration Exchange (phase 5). Ensuite, exécutez de nouveau le HCW en mode « Office 365 Dans le monde » à la fin de la phase 5 pour finaliser le déploiement local avec les paramètres de la région Office 365 Germany.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| (Pré-étape 5) : ré-exécuter HCW à l’aide des paramètres d’Office 365 Germany <br><br> <i>Vous pouvez démarrer cette activité immédiatement après avoir reçu la notification du centre de messages vous avertissant que la migration de votre client Office 365 a commencé (phase 1).</i>| La désinstallation et la ré-exécution du HCW (17.0.5378.0 ou une valeur supérieure) avant l’étape 5 garantissent que votre configuration sur site est prête à envoyer et recevoir des messages avec les utilisateurs de Microsoft Cloud Deutschland et les utilisateurs migrés vers la région [https://aka.ms/hybridwizard](https://aka.ms/hybridwizard) Office 365 Germany. <p><li> Dans le HCW, pour la zone de liste sous Mon organisation **Office 365** est hébergée par , sélectionnez **Office 365 Germany.** | Si vous ne parvient pas à effectuer cette tâche avant le début de l’étape 5 [migration Exchange], des messages d’échec de non-accès peuvent être acheminés entre votre déploiement Exchange local et Office 365.  
| (Post-Stage 5) - Ré-exécuter HCW à l’aide des paramètres Office 365 dans le monde <br><br> <i>Vous pouvez démarrer cette activité après avoir reçu la notification du centre de messages vous avertissant que votre migration Exchange est terminée (phase 5).</i>| La désinstallation et la ré-exécution du HCW après l’étape 5 réinitialiseront la configuration sur site pour la configuration hybride avec [https://aka.ms/hybridwizard](https://aka.ms/hybridwizard) uniquement Office 365 global. <p><li> Dans la zone de liste sous **Mon organisation Office 365** est hébergée par , sélectionnez **Office 365 dans le monde entier.** | Si vous ne parvient pas à effectuer cette tâche avant l’étape 9 [migration terminée], des NDR peuvent être envoyées pour le courrier acheminé entre votre déploiement Exchange local et Office 365.  
| Établir authServer local pointant vers le service d’jeton de sécurité global (STS) pour l’authentification | Cela garantit que les demandes d’authentification pour les demandes de disponibilité Exchange des utilisateurs en état de migration qui ciblent l’environnement local hybride sont authentifiées pour accéder au service local. De même, cela garantit l’authentification des demandes provenant de l’environnement local vers les points de terminaison des services globaux Office 365. | Une fois la migration Azure AD (phase 2) terminée, l’administrateur de la topologie Exchange (hybride) sur site doit ajouter un nouveau point de terminaison du service d’authentification pour les services globaux Office 365. Avec cette commande à partir d’Exchange PowerShell, remplacez l’ID de locataire de votre organisation dans le portail `<TenantID>` Azure sur Azure Active Directory.<br>`New-AuthServer GlobalMicrosoftSts -AuthMetadataUrl https://accounts.accesscontrol.windows.net/<TenantId>/metadata/json/1`<br> Si vous ne parvient pas à effectuer cette tâche, les demandes de libre-service hybride risquent de ne pas fournir d’informations aux utilisateurs de boîtes aux lettres qui ont été migrés de Microsoft Cloud Deutschland vers les services Office 365.  |
||||

## <a name="skype-for-business-online"></a>Skype Entreprise Online

<!-- before phase 7 -->

**S’applique** à : clients Skype Entreprise Online<br>
**Lorsqu’elle est** appliquée : à tout moment avant le début de la phase 7

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Déployez le client de bureau Teams pour les utilisateurs qui accèdent à Skype Entreprise en Allemagne. | La migration déplace les utilisateurs de Skype Entreprise vers Microsoft Teams pour la collaboration, l’appel et la conversation. Déployez le client de bureau Microsoft Teams ou assurez-vous qu’un navigateur pris en charge est disponible. | L’inaction entraîne l’indisponibilité des services de collaboration Microsoft Teams. |
| Examiner et préparer les modifications DNS liées à la migration. | La zone DNS du client change pour Skype Entreprise Online. |<ul><li>Nous vous recommandons de mettre à jour la durée de vie (TTL) de tous les enregistrements DNS de domaine d’un client sur 5 minutes pour accélérer l’actualisation des enregistrements DNS. Toutefois, le cutover géré par Microsoft associé à cette modification DNS peut se produire à tout moment dans la fenêtre de modification de 24 heures fournie. </li><li>La perturbation du service est possible à l’avenir. Les utilisateurs ne pourront pas se connecter à Skype Entreprise et seront redirigés vers l’expérience De Teams migrée dans les services Office 365. </li></ul>|
| Préparez la formation et la préparation de l’utilisateur final et de l’administration pour la transition vers Microsoft Teams. | Pour réussir votre transition de Skype vers Teams, planifiez la communication et la préparation des utilisateurs. | <ul><li>Les clients doivent connaître les nouveaux services et savoir comment les utiliser une fois que leurs services sont transitionn s vers les services Office 365. </li><li>Une fois que les modifications DNS ont été apportées à la fois pour les domaines professionnels du client et le domaine initial, les utilisateurs se connectent à Skype Entreprise et voient qu’ils sont désormais migrés vers Teams. Cela télécharge également le client de bureau pour Teams en arrière-plan. </li></ul>|
||||

## <a name="mobile-device-management"></a>Gestion des appareils mobiles

<!-- before phase 5 -->
**S’applique à :** Clients utilisant une solution de gestion des périphériques mobiles (MDM) tierce<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 5

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Préparez la formation des utilisateurs finaux et de l’administration sur la suppression et la nouvelle ajout de leur compte à Microsoft Outlook pour iOS et Android. | Il se peut que les comptes Microsoft Outlook pour iOS et Android configurés avec des boîtes aux lettres dans Microsoft Cloud Deutschland doivent être supprimés et ajoutés à Outlook pour synchroniser correctement la nouvelle configuration des services Office 365. | Clients Microsoft Outlook pour iOS et Android | Il se peut que les boîtes aux lettres Outlook précédemment configurées pour Microsoft Cloud Deutschland ne sélectionnent pas la nouvelle configuration des services Office 365, entraînant des erreurs et une dégradation des performances des autres expériences utilisateur. Les administrateurs informatiques sont invités à fournir une documentation qui demande aux utilisateurs de supprimer et de rajouter leurs comptes à Microsoft Outlook pour iOS et Android si des problèmes de signature ou de synchronisation des messages se produisent après la migration. |
| Déterminez si une reconfiguration est requise après la migration. | Les solutions de gestion des périphériques mobiles (MDM) peuvent cibler des `outlook.de` points de terminaison. Dans cette transition vers les services Office 365, les profils clients doivent être mis à jour vers l’URL des services Office 365, `outlook.office365.com` . | Clients Exchange Online et MDM | Les clients peuvent continuer à fonctionner tant que le point de terminaison est accessible, mais ils échoueront si les points de terminaison Microsoft Cloud Deutschland ne `outlook.de` sont plus disponibles. |
|||||

## <a name="line-of-business-apps"></a>Applications métier

**S’applique à :** Clients utilisant des applications métier avec des points de terminaison fournis par Microsoft Cloud Deutschland<br>
**Appliqué :** après la fin de la phase 2 et avant la fin de la phase 9

Si vous utilisez un service tiers ou des applications métier intégrées à Office 365, vous devez résoudre les dépendances envers les points de terminaison fournies par l’instance Microsoft Cloud Deutschland. Par exemple, si vos applications LOB se connectent, vous devez modifier `https://graph.microsoft.de/` le point de terminaison en `https://graph.microsoft.com/` . Les points de terminaison du service global Microsoft Office 365 deviennent disponibles pour votre client après la phase 2.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Déterminez si une reconfiguration est requise après la migration. | Les applications et services tiers qui s’intègrent à Office 365 peuvent être codés pour s’attendre à des adresses IP et des URL Microsoft Cloud Deutschland. | Action requise. L’inaction peut entraîner des défaillances du service ou du logiciel client. |
||||

## <a name="dynamics-365"></a>Dynamics 365

**S’applique à**: Clients utilisant Microsoft Dynamics 365

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Pour les abonnements en bac à sable Dynamics 365, n’oubliez pas de télécharger l’environnement de production de l’instance Dynamics SQL à partir de votre abonnement Dynamics 365 dans Microsoft Cloud Deutschland. La dernière sauvegarde de production doit être restaurée dans le bac à sable avant la migration en bac à sable. | Pour migrer Dynamics 365, les clients doivent s’assurer que l’environnement en bac à sable est actualisé avec la dernière base de données de production. | L’équipe FastTrack aidera les clients à effectuer des essais secs pour valider la mise à niveau de version de 8.x vers 9.1.x. |
||||

## <a name="power-bi"></a>Power BI

**S’applique à**: Clients utilisant Power BI

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Suppression des objets des abonnements Power BI qui ne seront pas migrés de Power BI Microsoft Cloud Deutschland vers les services Office 365. | La migration des services Power BI nécessite une action du client pour supprimer certains artefacts, tels que les jeux de données et les tableaux de bord. | <ul><li>Les administrateurs peuvent être dans l’devoir de supprimer les éléments suivants de leur abonnement : </li><li>Real-Time de données (par exemple, les jeux de données push ou de diffusion en continu) </li><li>Configuration et source de données de la passerelle de données power BI sur site </li></ul>|
||||

## <a name="microsoft-azure"></a>Microsoft Azure

Si vous utilisez la même partition d’identité Azure Active Directory pour Office 365 et Microsoft Azure dans l’instance Microsoft Cloud Deutschland, assurez-vous que vous préparez la migration pilotée par le client des services Microsoft Azure.

> [!NOTE]
> La migration de vos services Microsoft Azure ne doit pas être démarrée avant que votre client Office 365 n’ait atteint la phase de migration 3 et doit être terminée avant la fin de la phase 8.

Les clients qui utilisent des ressources Office 365 et Azure (par exemple, réseau, calcul et stockage) effectueront la migration des ressources vers l’instance des services Office 365. Cette migration est la responsabilité du client. Les publications du Centre de messages signalent le début. La migration doit être effectuée avant la finalisation de l’organisation Azure AD dans l’environnement de services Office 365. Pour les migrations Azure, consultez le manuel de migration Azure, vue d’ensemble des conseils de [migration pour Azure Germany.](https://docs.microsoft.com/azure/germany/germany-migration-main)

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Déterminez les services Azure en cours d’utilisation et préparez la migration future de l’Allemagne vers le client des services Office 365 en travaillant avec vos partenaires. Suivez les étapes décrites dans le [manuel de migration Azure.](/azure/germany/germany-migration-main) |<ul><li>La migration des ressources Azure est une responsabilité du client et nécessite un effort manuel en suivant les étapes prescrites. Il est essentiel de comprendre quels services sont utilisés dans l’organisation pour réussir la migration des services Azure. </li><li> Les clients Office 365 Germany qui ont des abonnements Azure sous la même partition d’identité (organisation) doivent respecter l’ordre prescrit par Microsoft lorsqu’ils peuvent commencer la migration des abonnements et des services.</li></ul>|<ul><li>Les clients peuvent avoir plusieurs abonnements Azure, chacun contenant des composants d’infrastructure, de services et de plateforme. </li><li> Les administrateurs doivent identifier les abonnements et les parties prenantes pour s’assurer que la migration rapide et la validation sont possibles dans le cadre de cet événement de migration. </li><li>L’échec de la migration de ces abonnements et composants Azure dans la chronologie prescrite affecte la fin de la transition d’Office et d’Azure AD vers les services Office 365 et peut entraîner une perte de données. </li><li> Une notification du centre de messages signale le point auquel la migration dirigée par le client peut commencer. </li></ul>|
||||

<!--
Reworked as text:

**Step:** Determine which Azure services are in use and prepare for future migration from Germany to the Office 365 services tenant by working with your partners. Follow the steps described in the [Azure migration playbook](/azure/germany/germany-migration-main).

**Description:** Migration of Azure resources is a customer responsibility and requires manual effort following prescribed steps. Understanding what services are in use in the organization is key to successful migration of Azure services. 

Office 365 Germany customers who have Azure subscriptions under the same identity partition (organization) must follow the Microsoft-prescribed order when they can begin subscription and services migration.

**Applies to:** Azure Customers

**Impact:** 

- Customers may have multiple Azure subscriptions, each subscription containing infrastructure, services, and platform components. 
- Administrators should identify subscriptions and stakeholders to ensure prompt migration and validation is possible as part of this migration event.

  Failing to successfully complete migration of these subscriptions and Azure components within the prescribed timeline will affect completion of the Office and Azure AD transition to Office 365 services and may result in data loss.
- A Message center notification will signal the point at which customer-led migration can begin.
-->

## <a name="more-information"></a>Plus d’informations

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers les services Office 365 dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
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
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)
