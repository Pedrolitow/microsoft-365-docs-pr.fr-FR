---
title: Pré-travail pour la migration à partir de Microsoft Cloud Deutschland
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
ms.openlocfilehash: 94b3758bbf24133c0d01a0db9e17f9451cf2d8d2
ms.sourcegitcommit: 9adb89206daa075af34a73bcb7e8fb86d7c2919a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2021
ms.locfileid: "50603863"
---
# <a name="pre-work-for-the-migration-from-microsoft-cloud-deutschland"></a>Pré-travail pour la migration à partir de Microsoft Cloud Deutschland

Utilisez ces liens pour obtenir les étapes préalables au travail pertinentes pour votre organisation :

- Pour tous les clients qui utilisent Office 365 dans Microsoft Cloud Deutschland, faites [ces étapes.](#applies-to-everyone)
- Si vous utilisez Exchange Online ou Exchange hybride, faites [cette étape.](#exchange-online)
- Si vous utilisez SharePoint Online, faites [cette étape.](#sharepoint-online)
- Si vous utilisez une solution de gestion des périphériques mobiles (MDM) tierce, faites [cette étape.](#mobile)
- Si vous utilisez des applications de service ou métier tierces intégrées à Office 365, faites [cette étape.](#line-of-business-apps)
- Si vous utilisez également des services Azure au-delà de ceux inclus dans votre abonnement Office 365, faites [cette étape.](#microsoft-azure)
- Si vous utilisez également Dynamics 365, faites [cette étape.](#dynamics365)
- Si vous utilisez également Power BI, faites [cette étape.](#power-bi)
- Pour les modifications DNS, faites [cette étape.](#dns)
- Si vous utilisez l’identité fédérée, faites [ces étapes.](#federated-identity)

## <a name="applies-to-everyone"></a>S’applique à tout le monde

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Préparez-vous à informer les utilisateurs du redémarrage et de la signature de leurs clients après la migration. | Les licences client Office passeront de Microsoft Cloud Deutschland aux services Office 365 lors de la migration. Les clients sélectionnent une nouvelle licence valide après s’être désoyé et s’être mis en place avec les clients Office. | Les produits Office des utilisateurs doivent actualiser les licences à partir des services Office 365. Si les licences ne sont pas actualisées, les produits Office peuvent faire l’expérience d’erreurs de validation de licence. |
| Assurez-vous que la connectivité réseau aux URL et adresses IP des [services Office 365](https://aka.ms/o365urls). | Tous les clients et services hébergés par le client qui sont utilisés pour accéder au service Office 365 doivent pouvoir accéder aux points de terminaison des services globaux Office 365. <br>Dans le cas où, vous ou vos partenaires de collaboration avez des règles de pare-feu en place qui empêchent l’accès aux URL et adresses IP répertoriées dans les URL et adresses IP des [services Office 365](https://aka.ms/o365urls) doivent modifier les règles de pare-feu pour autoriser l’accès aux points de terminaison du service global Office 365| Des défaillances du service ou du logiciel client peuvent se produire si cette étape n’est pas effectuée avant la phase 4  |
| Annulez les abonnements à la version d’essai. | Les abonnements d’essai ne seront pas migrés et bloqueront le transfert des abonnements payants. | Les services d’essai ont expiré et ne fonctionnent pas si les utilisateurs y accèdent après l’annulation. |
| Analysez les différences de fonctionnalités de licence entre Microsoft Cloud Deutschland et les services Office 365. | Les services Office 365 incluent des fonctionnalités et des services supplémentaires qui ne sont pas disponibles dans microsoft Cloud Deutschland actuel. Pendant le transfert d’abonnement, de nouvelles fonctionnalités seront disponibles pour les utilisateurs. | <ul><li> Analysez les différentes fonctionnalités fournies par les licences pour Microsoft Cloud Deutschland et les services Office 365. Commencez par la description du service de la [plateforme Office 365.](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description) </li><li> Déterminez si les nouvelles fonctionnalités des services Office 365 doivent être initialement désactivées pour limiter les effets sur les utilisateurs ou sur la gestion des changements d’utilisateurs, et modifiez les attributions de licence utilisateur selon vos besoins. </li><li>Préparez les utilisateurs et le personnel du service d’aide aux nouveaux services et fonctionnalités fournis par les services Office 365. |
| Créer des stratégies de [rétention à l’échelle de](https://docs.microsoft.com/microsoft-365/compliance/retention) l’organisation pour vous protéger contre la suppression accidentelle de contenu pendant la migration.  |<ul><li>Pour s’assurer que le contenu n’est pas supprimé par inadvertance par les utilisateurs finaux pendant la migration, les clients peuvent choisir d’activer une stratégie de rétention à l’échelle de l’organisation. </li><li>Bien que la rétention ne soit pas requise, dans la mesure où les conservations placées à tout moment pendant la migration doivent fonctionner comme prévu, la mise en place d’une stratégie de rétention est un mécanisme de sécurité de la protection. En même temps, une stratégie de rétention peut ne pas être utilisée par tous les clients, en particulier ceux qui sont préoccupés par la conservation.</li></ul>| Appliquez la stratégie de rétention comme décrit dans [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) Des défaillances du service ou du logiciel client peuvent se produire si cette étape n’est pas effectuée avant la phase 4 sur 9. </li></ul>|
|||||

## <a name="active-directory-federation-services-ad-fs"></a>Services AD FS (Active Directory Federation Services)

**S’applique** à : Clients utilisant AD FS sur site pour authentifier les utilisateurs se connectant Microsoft Office 365

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| [Sauvegarde de la batterie de serveurs AD FS (Active Directory Federation Services)](ms-cloud-germany-transition-add-adfs.md#backup) pour les scénarios de récupération d’urgence. | Les clients doivent back up the AD FS farm appropriately to ensure the relying party trusts to global & Germany endpoints can be restored without touch the issuer URI of the domains. Microsoft recommande d’utiliser la restauration rapide AD FS pour une sauvegarde de la batterie de serveurs et de la restauration respective, si nécessaire. | Action requise. L’inaction aura un impact sur le service pendant la migration si la batterie de serveurs AD FS du client échoue. Pour plus d’informations, reportez-vous aux [étapes de migration ADFS](https://docs.microsoft.com/microsoft-365/enterprise/ms-cloud-germany-transition-add-adfs) |
||||

## <a name="exchange-online"></a>Exchange Online

**S’applique à**: clients Exchange Online qui ont activé le partage du calendrier et de l’espace d’adressal de disponibilité.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Informez les partenaires externes de la transition à venir vers les services Office 365. | Les configurations d’espace d’adressare de disponibilité permettent le partage d’informations de disponibilité avec Office 365. | Si vous ne le faites pas, le service ou le client échouera lors d’une phase ultérieure de la migration des clients. |
|||||

### <a name="exchange-online-hybrid-configuration"></a>Configuration hybride d’Exchange Online

**S’applique à**: Clients Exchange Online avec une configuration Exchange hybride active

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Mettez à jour la dernière version de l’Assistant Configuration hybride (HCW) à tout moment avant que votre client n’entre dans l’étape de migration 5. Vous pouvez démarrer cette activité de manière incommensommable après avoir reçu le centre de messages pour vous notifier que la migration de votre client Office 365 a commencé.<br><br> Les clients Exchange Online hybrides Microsoft Cloud Deutschland doivent désinstaller les versions précédentes de HCW, puis installer et exécuter la dernière version (17.0.5378.0 ou version ultérieure) à partir de [https://aka.ms/hybridwizard](https://aka.ms/hybridwizard) . |<ul><li>La dernière version du HCW inclut les mises à jour nécessaires pour prendre en charge les clients qui sont en transition de Microsoft Cloud Deutschland vers les services Office 365.</li><li> Les mises à jour incluent les modifications apportées aux paramètres de certificat local pour le connecteur d’envoi et le connecteur de réception.</li><li> Les administrateurs Exchange doivent réinstaller le HCW à tout moment avant le début de la phase 5 sur 9 (migration Exchange).<br>Lors de l’exécution du HCW avant la phase 5, sélectionnez « Office 365 Germany » sur la deuxième page du HCW sous _Office 365 Exchange Online_ dans la boîte de liste sous Mon organisation Office _365_ est hébergée par</li><li>**REMARQUE**: à la fin de votre migration de client Office 365, vous allez supprimer et réinstaller le HCW, cette fois à l’aide des paramètres « Office 365 Dans le monde » sur le deuxième volet du HCW pour terminer votre configuration hybride avec le service global Exchange Online.</li></ul>|L’échec de l’exécuter avant la phase 5 (migration Exchange) peut entraîner une défaillance du service ou du client. |
||||

## <a name="sharepoint-online"></a>SharePoint Online

**S’applique** à : Clients qui utilisent SharePoint 2013 en local


| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Limitez les flux de travail SharePoint 2013, utilisés pendant la migration SharePoint Online. | Réduisez les flux de travail SharePoint 2013 et terminez les flux de travail en cours avant les transitions. | L’inaction peut semer la confusion chez l’utilisateur et entraîner des appels au service d’aide. |
||||

## <a name="skype-for-business-online"></a>Skype Entreprise Online

**S’applique** à : clients Skype Entreprise Online

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Déployez le client de bureau Teams pour les utilisateurs qui accèdent à Skype Entreprise en Allemagne. | La migration déplace les utilisateurs de Skype Entreprise vers Microsoft Teams pour la collaboration, l’appel et la conversation. Déployez le client de bureau Microsoft Teams ou assurez-vous qu’un navigateur pris en charge est disponible. | L’inaction entraîne l’indisponibilité des services de collaboration Microsoft Teams. |
| Examiner et préparer les modifications DNS liées à la migration. | La zone DNS du client change pour Skype Entreprise Online. |<ul><li>Nous vous recommandons de mettre à jour la durée de vie (TTL) de tous les enregistrements DNS de domaine d’un client sur 5 minutes pour accélérer l’actualisation des enregistrements DNS. Toutefois, le cutover géré par Microsoft associé à cette modification DNS peut se produire à tout moment dans la fenêtre de modification de 24 heures fournie. </li><li>La perturbation du service est possible à l’avenir. Les utilisateurs ne pourront pas se connecter à Skype Entreprise et seront redirigés vers l’expérience De Teams migrée dans les services Office 365. </li></ul>|
| Préparez la formation et la préparation de l’utilisateur final et de l’administration pour la transition vers Microsoft Teams. | Pour réussir votre transition de Skype vers Teams, planifiez la communication et la préparation des utilisateurs. | <ul><li>Les clients doivent connaître les nouveaux services et savoir comment les utiliser une fois que leurs services sont transitionn s vers les services Office 365. </li><li>Une fois que les modifications DNS ont été apportées à la fois pour les domaines professionnels du client et le domaine initial, les utilisateurs se connectent à Skype Entreprise et voient qu’ils sont désormais migrés vers Teams. Cela télécharge également le client de bureau pour Teams en arrière-plan. </li></ul>|
||||

## <a name="mobile"></a>Mobile

Si vous utilisez une solution de gestion des périphériques mobiles (MDM) tierce :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Préparez la formation des utilisateurs finaux et de l’administration sur la suppression et la nouvelle ajout de leur compte à Microsoft Outlook pour iOS et Android. | Il se peut que les comptes Microsoft Outlook pour iOS et Android configurés avec des boîtes aux lettres dans Microsoft Cloud Deutschland doivent être supprimés et ajoutés à Outlook pour synchroniser correctement la nouvelle configuration des services Office 365. | Clients Microsoft Outlook pour iOS et Android | Il se peut que les boîtes aux lettres Outlook précédemment configurées pour Microsoft Cloud Deutschland ne sélectionnent pas la nouvelle configuration des services Office 365, entraînant des erreurs et une dégradation des performances des autres expériences utilisateur. Les administrateurs informatiques sont invités à fournir une documentation qui demande aux utilisateurs de supprimer et de rajouter leurs comptes à Microsoft Outlook pour iOS et Android si des problèmes de signature ou de synchronisation des messages se produisent après la migration. |
| Déterminez si une reconfiguration est requise après la migration. | Les solutions de gestion des périphériques mobiles (MDM) peuvent cibler des `outlook.de` points de terminaison. Dans cette transition vers les services Office 365, les profils clients doivent être mis à jour vers l’URL des services Office 365, `outlook.office365.com` . | Clients Exchange Online et MDM | Les clients peuvent continuer à fonctionner tant que le point de terminaison est accessible, mais ils échoueront si les points de terminaison Microsoft Cloud Deutschland ne `outlook.de` sont plus disponibles. |
|||||

## <a name="line-of-business-apps"></a>Applications métier

Si vous utilisez un service tiers ou des applications métier intégrées à Office 365 : 

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Déterminez si une reconfiguration est requise après la migration. | Les applications et services tiers qui s’intègrent à Office 365 peuvent être codés pour s’attendre à des adresses IP et des URL Microsoft Cloud Deutschland. | Action requise. L’inaction peut entraîner des défaillances du service ou du logiciel client. |
||||

## <a name="dynamics-365"></a>Dynamics 365

**S’applique à**: Clients utilisant Microsoft Dynamics

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Pour les abonnements en bac à sable Dynamics 365, n’oubliez pas de télécharger l’environnement de production de l’instance Dynamics SQL à partir de votre abonnement Dynamics 365 dans Microsoft Cloud Deutschland. La dernière sauvegarde de production doit être restaurée dans le bac à sable avant la migration en bac à sable. | Pour migrer Dynamics 365, les clients doivent s’assurer que l’environnement en bac à sable est actualisé avec la dernière base de données de production. | L’équipe FastTrack aidera les clients à effectuer des essais secs pour valider la mise à niveau de version de 8.x vers 9.1.x. |
||||

## <a name="power-bi"></a>Power BI

**S’applique** à : Clients Power BI 

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Suppression des objets des abonnements Power BI qui ne seront pas migrés de Power BI Microsoft Cloud Deutschland vers les services Office 365. | La migration des services Power BI nécessite une action du client pour supprimer certains artefacts, tels que les jeux de données et les tableaux de bord. | <ul><li>Les administrateurs peuvent être dans l’devoir de supprimer les éléments suivants de leur abonnement : </li><li>Real-Time de données (par exemple, les jeux de données push ou de diffusion en continu) </li><li>Configuration et source de données de la passerelle de données power BI sur site </li></ul>|
||||

## <a name="dns"></a>DNS

**S’applique** à : Clients utilisant le client de bureau Office (Applications Microsoft 365, Office 365 ProPlus, Office 2019, 2016, ...)<br>
Supprimez MSOID, CName du DNS propriétaire du client s’il existe à tout moment avant le cut-over Azure Active Directory (Azure AD). Une TTL de 5 minutes peut être définie pour que la modification puisse prendre effet rapidement.

## <a name="federated-identity"></a>Identité fédérée

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Ajoutez un identificateur pour l' sign-on unique (SSO) à une confiance de partie de confiance existante et désactivez les mises à jour automatiques des métadonnées AD FS. | Un ID doit être ajouté à l’confiance de la partie de confiance AD FS avant de commencer la migration. Pour éviter la suppression accidentelle de l’identificateur de partie de confiance, désactivez la mise à jour automatique pour les mises à jour des métadonnées. <br><br> Exécutez cette commande en tant que ligne de commande unique sur le serveur AD FS : <br>`Set-AdfsRelyingPartyTrust -TargetIdentifier urn:federation:microsoftonline.de -Identifier @('urn:federation:microsoftonline.de', 'https://login.microsoftonline.de/extSTS.srf', 'https://login.microsoftonline.de') -AutoUpdate $False`
| Organisations d’authentification fédérée | Action requise. Inaction before Phase 4 of 9 (SharePoint) will result in service impact during the migration.  |
| Générer une confiance de partie de confiance pour les points de terminaison Azure AD globaux. | Les clients doivent créer manuellement une relation d’confiance (RPT) vers les [points de](https://nexus.microsoftonline-p.com/federationmetadata/2007-06/federationmetadata.xml) terminaison globaux. Pour ce faire, vous ajoutez une nouvelle rpt via l’interface graphique en tirant parti de l’URL de métadonnées de fédération globale, puis en utilisant les règles de revendication [rpt Azure AD](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator#:~:text=%20Azure%20AD%20RPT%20Claim%20Rules%20%201,Azure%20AD.%20This%20will%20be%20what...%20More%20) (dans l’aide AD FS) pour générer les règles de revendication et les importer dans la rpt. | Organisations d’authentification fédérée | Action requise. L’inaction aura un impact sur le service pendant la migration. |
|||||

## <a name="microsoft-azure"></a>Microsoft Azure

Si vous utilisez la même partition d’identité Azure Active Directory pour Office 365 et Microsoft Azure dans l’instance Microsoft Cloud Deutschland, assurez-vous que vous préparez la migration pilotée par le client des services Microsoft Azure.
La migration de vos services Microsoft Azure ne doit pas être démarrée avant que votre client Office 365 n’ait atteint la phase de migration 3 et doit être terminée avant la fin de la phase 8.
| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Déterminez les services Azure en cours d’utilisation et préparez la migration future de l’Allemagne vers le client des services Office 365 en travaillant avec vos partenaires. Suivez les étapes décrites dans le [manuel de migration Azure.](https://docs.microsoft.com/azure/germany/germany-migration-main) |<ul><li>La migration des ressources Azure est une responsabilité du client et nécessite un effort manuel en suivant les étapes prescrites. Il est essentiel de comprendre quels services sont utilisés dans l’organisation pour réussir la migration des services Azure. </li><li> Les clients Office 365 Germany qui ont des abonnements Azure sous la même partition d’identité (organisation) doivent respecter l’ordre prescrit par Microsoft lorsqu’ils peuvent commencer la migration des abonnements et des services.</li></ul>|<ul><li>Les clients peuvent avoir plusieurs abonnements Azure, chacun contenant des composants d’infrastructure, de services et de plateforme. </li><li> Les administrateurs doivent identifier les abonnements et les parties prenantes pour s’assurer que la migration rapide et la validation sont possibles dans le cadre de cet événement de migration. </li><li>L’échec de la migration de ces abonnements et composants Azure dans la chronologie prescrite affecte la fin de la transition d’Office et d’Azure AD vers les services Office 365 et peut entraîner une perte de données. </li><li> Une notification du centre de messages signale le point auquel la migration dirigée par le client peut commencer. </li></ul>|
||||

<!--
Reworked as text:

**Step:** Determine which Azure services are in use and prepare for future migration from Germany to the Office 365 services tenant by working with your partners. Follow the steps described in the [Azure migration playbook](https://docs.microsoft.com/azure/germany/germany-migration-main).

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

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
