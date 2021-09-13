---
title: Activités préalables à la migration de Microsoft Cloud Deutschland
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
description: 'Résumé : Pré-travail lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers Office 365 services dans la nouvelle région de centres de données allemands.'
ms.openlocfilehash: 77e3dbd3f819aea15632a0ba069249a44a8663fb
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182159"
---
# <a name="pre-migration-activities-for-the-migration-from-microsoft-cloud-deutschland"></a>Activités préalables à la migration de Microsoft Cloud Deutschland

Utilisez ces liens pour obtenir les étapes préalables à la migration pertinentes pour votre organisation.

Si vous utilisez

- **Office 365 dans Microsoft Cloud Deutschland,** faites [ces étapes.](#general-tenant-migration-considerations)
- **Domaines personnalisés,** faites [cette étape.](#dns-entries-for-custom-domains)
- **Office applications, envisagez** [cette étape.](#office-apps)
- **SharePoint Online,** faites [cette étape.](#sharepoint-online)
- **Exchange Online** ou **Exchange hybride,** faites [cette étape.](#exchange-online)
- **Skype Entreprise Online,** faites [cette étape.](#skype-for-business-online)
- **Dynamics 365,** faites [cette étape.](#dynamics-365)
- **Power BI,** faites [cette étape.](#power-bi)
- **Active Directory Federation Services** for Azure AD Connecter, do [these steps](#active-directory-federation-services-ad-fs).
- **Les services tiers ou** les applications métier **qui** sont intégrées à Office 365, faites [cette étape.](#line-of-business-apps)
- Une solution de gestion des périphériques mobiles (MDM) tierce, faites [cette étape.](#mobile-device-management)
- **Services Azure** avec votre abonnement Office 365, faites [cette étape.](#microsoft-azure)

## <a name="general-tenant-migration-considerations"></a>Considérations générales sur la migration des locataires

**S’applique à :** Tous les clients qui utilisent Office 365 dans l’instance De Cloud Microsoft Deutschland

Office 365 les identificateurs de client et d’utilisateur sont conservés pendant la migration. Les appels de service Azure AD sont redirigés de Microsoft Cloud Deutschland vers Office 365 services globaux et sont transparents pour Office 365 services.

- Les demandes DSR (Data Subject Requests) du Règlement général sur la protection des données (R GDPR) sont exécutées à partir du portail d’administration Azure pour les demandes futures. Toutes les données de diagnostic héritées ou non client résidant dans Microsoft Cloud Deutschland sont supprimées au plus tard 30 jours après.

- Les demandes d’authentification multifacteur (MFA) qui utilisent Microsoft Authenticator s’affichent en tant qu’objectID utilisateur (GUID) pendant que le client est copié dans Office 365 services. Les demandes mfa s’exécuteront comme prévu malgré ce comportement d’affichage.  Microsoft Authenticator comptes qui ont été activés à l’aide Office 365 des points de terminaison des services afficheront le nom d’utilisateur principal (UPN).  Les comptes ajoutés à l’aide des points de terminaison Microsoft Cloud Deutschland afficheront l’objectID de l’utilisateur, mais fonctionneront avec les points de terminaison des services Microsoft Cloud Deutschland et Office 365 cloud.

<br>

****

|Étapes|Description|Impact|
|---|---|---|
|Préparez-vous à informer les utilisateurs du redémarrage et de la signature de leurs clients après la migration.|Office licences client passe de Microsoft Cloud Deutschland à Office 365 services de migration. Les clients sélectionnent une nouvelle licence valide après s’être dé sign s et se sont Office clients.|Les produits Office utilisateurs doivent actualiser les licences à partir Office 365 services. Si les licences ne sont pas actualisées, Office produits peuvent faire l’expérience d’erreurs de validation de licence.|
|Assurez-vous que la connectivité réseau [à Office 365 services d’URL et d’adresses IP](https://aka.ms/o365urls).|Tous les clients et services hébergés par le client qui sont utilisés pour accéder au service Office 365 doivent pouvoir accéder aux points de terminaison Office 365 services globaux. <p> Si vous ou vos partenaires de collaboration avez des règles de pare-feu en place qui empêcheraient l’accès aux URL et adresses IP répertoriées dans les URL et adresses IP des [services Office 365,](https://aka.ms/o365urls) vous devez modifier les règles de pare-feu pour autoriser l’accès aux points de terminaison du service global Office 365|Des défaillances du service ou du logiciel client peuvent se produire si cette étape n’est pas effectuée avant la phase 4|
|Annulez les abonnements à la version d’essai.|Les abonnements d’essai ne seront pas migrés et bloqueront le transfert des abonnements payants.|Les services d’essai ont expiré et ne fonctionnent pas si les utilisateurs y accèdent après l’annulation.|
|Analysez les différences de fonctionnalités de licence entre Microsoft Cloud Deutschland et les services Office 365 global.|Office 365 services incluent des fonctionnalités et des services supplémentaires qui ne sont pas disponibles dans Microsoft Cloud Deutschland actuel. Pendant le transfert d’abonnement, de nouvelles fonctionnalités seront disponibles pour les utilisateurs.|<ul><li>Analysez les différentes fonctionnalités fournies par les licences pour Microsoft Cloud Deutschland et Office 365 Global Services. Commencez par la [description Office 365 service de la plateforme.](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description)</li><li>Déterminez si les nouvelles fonctionnalités des services Office 365 doivent être initialement désactivées pour limiter les effets sur les utilisateurs ou sur la gestion des changements d’utilisateurs, et modifiez les attributions de licence utilisateur selon vos besoins.</li><li>Préparez les utilisateurs et le personnel du service d’aide aux nouveaux services et fonctionnalités fournis par Office 365 services.</li></ul>|
|Créer des stratégies de [rétention à l’échelle de](/microsoft-365/compliance/retention) l’organisation pour vous protéger contre la suppression accidentelle de contenu pendant la migration.|<ul><li>Pour s’assurer que le contenu n’est pas supprimé par inadvertance par les utilisateurs finaux pendant la migration, les clients peuvent choisir d’activer une stratégie de rétention à l’échelle de l’organisation.</li><li>Bien que la rétention ne soit pas requise, dans la mesure où les conservations placées à tout moment pendant la migration doivent fonctionner comme prévu, l’emploi d’une stratégie de rétention est un mécanisme de sécurité de protection de la protection. En même temps, une stratégie de rétention peut ne pas être utilisée par tous les clients, en particulier ceux qui sont préoccupés par la conservation.</li></ul>|Appliquez la stratégie de rétention comme décrit dans [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](/microsoft-365/compliance/retention-policies) Des défaillances du service ou du logiciel client peuvent se produire si cette étape n’est pas effectuée avant la phase 4 sur 9.|


## <a name="dns-entries-for-custom-domains"></a>Entrées DNS pour les domaines personnalisés

<!-- before phase 9 -->

**S’applique** à : Clients qui définissent un _cnaME msoid_ personnalisé dans leur propre domaine DNS ou qui utilisent un domaine pour Exchange Online

S’il est configuré, le _cname msoid_ affecte uniquement les clients utilisant le client de bureau Office (Microsoft 365 Apps, Office 365 ProPlus, Office 2019, 2016, ...)

Si vous avez définie un DNS CNAME appelé _msoid_ dans un ou plusieurs espaces de noms DNS que vous possédez, vous devez supprimer le CNAME jusqu’à la fin de la phase 8 au plus tard. Vous pouvez supprimer le _msoid_ CNAME à tout moment avant la fin de la phase 8.

Pour vérifier si vous avez définie un CNAME dans votre espace de noms DNS, suivez les étapes ci-dessous et remplacez _contoso.com_ par votre propre nom de domaine :

```console
nslookup -querytype=CNAME msoid.contoso.com
```

Si la ligne de commande renvoie un enregistrement DNS, supprimez _le cname msoid_ de votre domaine.

> [!NOTE]
> Si vous utilisez un domaine personnalisé pour Exchange Online, vous devez avoir accès à votre fournisseur d’hébergement DNS. Assurez-vous que vous pouvez accéder à vos paramètres DNS et les modifier, vous allez modifier les enregistrements DNS pendant la migration.

## <a name="office-apps"></a>Office Applications

**S’applique à**: Clients utilisant Office apps, en particulier sur Windows clients <br>
**Lorsqu’elle est** appliquée : tout moment avant le démarrage de la phase 9

Office 365 clients qui migrent vers la région « Allemagne » exigent que tous les utilisateurs se ferment, se connectent depuis Office 365 et se connectent à toutes les applications de bureau Office (Word, Excel, PowerPoint, Outlook, etc.) et au client OneDrive Entreprise une fois que la migration des clients a atteint la phase 9. La signature et la signature permettent aux services Office d’obtenir de nouveaux jetons d’authentification à partir du service Azure AD global.

Ceci est obligatoire pour tous les clients. Pour garantir une expérience de migration fluide, il est vivement recommandé d’informer et d’informer à l’avance et en amont tous les utilisateurs concernés de cette activité à venir.

Les clients ayant des clients Windows gérés peuvent préparer Windows ordinateurs à l’aide Office’outil de Office client [(OCCT).](https://github.com/microsoft/OCCT) L’OCCT est conçu pour s’exécuter régulièrement sur Windows clients jusqu’à ce que le client atteigne la phase 9 de la migration. Lorsque la phase 9 est atteinte, l’OCCT effectue automatiquement toutes les modifications nécessaires sur l’ordinateur sans intervention de l’utilisateur.

L’OCCT peut être déployé sur Windows clients à tout moment avant la phase 9. Si l’OCCT doit prendre en charge l’expérience de migration, nous vous recommandons de commencer le déploiement dès que possible pour obtenir un nombre maximal de clients.

## <a name="active-directory-federation-services-ad-fs"></a>Services AD FS (Active Directory Federation Services)

**S’applique** à : Clients utilisant AD FS sur site pour authentifier les utilisateurs se connectant à Microsoft Office 365<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 2

Lire et appliquer les [étapes de migration ADFS](ms-cloud-germany-transition-add-adfs.md)

## <a name="sharepoint-online"></a>SharePoint Online

**S’applique** à : Customers using SharePoint 2013 on-premises<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 4

<br>

****

|Étapes|Description|Impact|
|---|---|---|
|Limitez SharePoint flux de travail 2013, utilisés pendant la migration SharePoint Online.|Réduisez SharePoint flux de travail 2013 et terminez les flux de travail en cours avant les transitions.|L’inaction peut semer la confusion chez l’utilisateur et entraîner des appels au service d’aide.| 
Exportez SharePoint configuration de recherche si des modifications ont été appliquées. |La SharePoint de recherche ne sera pas migrée. Si des modifications dans SharePoint recherche ont été appliquées, veillez à prendre note des modifications et à exporter la configuration de la recherche. Les paramètres doivent être importés à nouveau une fois la transition SharePoint terminée.|Toutes les solutions personnalisées basées sur un schéma de recherche modifié ne seront pas disponibles tant que les modifications de recherche n’auront pas été appliquées à nouveau.|


## <a name="exchange-online"></a>Exchange Online

<!-- before phase 5 -->

**S’applique** à : Exchange Online clients<br>
**Appliqué :** Tout moment avant la fin de la phase 9

<br>

****

|Étapes|Description|Impact|
|---|---|---|
|Informez les partenaires externes de la transition à venir vers Office 365 services.|Les clients doivent informer leurs partenaires avec lesquels ils ont activé le partage du calendrier et de la configuration de l’espace d’adressace de disponibilité (autoriser le partage d’informations de disponibilité avec Office 365). La configuration de la disponibilité doit être effectuée pour utiliser les [points de terminaison Office 365](/microsoft-365/enterprise/urls-and-ip-address-ranges) dans le monde entier une fois Exchange Online migration est terminée.|Si vous ne le faites pas, le service ou le client échouera lors d’une phase ultérieure de la migration des clients.|
|Informez les utilisateurs des modifications de client IMAP4/POP3/SMTP requises.|Les utilisateurs qui ont des connexions d’appareil aux points de terminaison Microsoft Cloud Deutschland pour les protocoles clients IMAP4, POP3, SMTP sont tenus de mettre à jour manuellement leurs appareils clients pour basculer vers les noms de serveur [Exchange Online](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/pop3-and-imap4#settings-users-use-to-set-up-pop3-or-imap4-access-to-their-exchange-online-mailboxes).|Communiquez préalablement cette dépendance aux utilisateurs de ces protocoles et assurez-vous qu’ils basculent vers Outlook mobile ou Outlook sur le web lors de cette migration. L’échec de la mise à jour des points de terminaison clients entraîne des échecs de connexion client par rapport à Microsoft Cloud Deutschland lors de la migration des boîtes aux lettres utilisateur.|


### <a name="exchange-online-hybrid-customers"></a>Exchange Online Clients hybrides

**S’applique à :** Tous les clients utilisant une configuration hybride Exchange active avec Exchange serveurs locaux<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 5

Enterprise clients ayant un déploiement hybride de Exchange Online et un Exchange Server local exécutent l’Assistant Configuration hybride (HCW) et AAD Connecter pour maintenir et établir l’installation hybride.
Exchange Online Les administrateurs **hybrides doivent exécuter l’Assistant Configuration hybride (HCW)** plusieurs fois dans le cadre de cette transition.
Lors de la transition de Microsoft Cloud Deutschland vers la région Office 365 Germany, l’administrateur doit ré-exécuter la dernière version de HCW en mode « Office 365 Germany » avant le début de la migration Exchange (phase 5). Ensuite, exécutez de nouveau le HCW en mode « Office 365 Worldwide » à la fin de la phase 5 pour finaliser le déploiement local avec les paramètres de la région Office 365 Germany. L’exécution du HCW ne doit pas être exécutée pendant la phase 5, il est important d’exécuter le HCW jusqu’à la fin de la phase 5.
Les attributs d’annuaire sont synchronisés entre Office 365 et Azure AD avec le déploiement local via AAD Connecter.

<br>

**

|Étapes|Description|Impact|
|---|---|---|
|Ré-exécuter HCW à l’aide Office 365 Germany <p> _Vous pouvez démarrer cette activité immédiatement après avoir reçu la notification du centre de messages vous avertissant que la migration de votre client Office 365 a commencé (phase 1)._|La désinstallation et la ré-exécution du HCW (17.0.5378.0 ou une valeur supérieure) avant la phase 5 garantit que votre configuration sur site est prête à envoyer et recevoir des messages avec les utilisateurs de Microsoft Cloud Deutschland et les utilisateurs migrés vers la région <https://aka.ms/hybridwizard> Office 365 Germany. <p> Dans le HCW, pour la zone de liste sous Mon **Office 365 est** hébergée par , sélectionnez **Office 365 Germany.**|Si vous ne parvient pas à effectuer cette tâche avant le début de la phase 5 [migration Exchange], des messages d’échec de non-Exchange peuvent être acheminés entre votre déploiement local Office 365.|
|Conservation des paramètres de boîte aux lettres partagée|Certains clients hybrides ont converti des boîtes aux lettres utilisateur cloud en boîtes aux lettres « partagées » à l’aide Exchange Online commandes. Cette configuration de boîte aux lettres cloud est écrite dans la boîte aux lettres et le répertoire Exchange Online local, mais elle n’est pas synchronisée avec Active Directory du client via AAD Connecter. Le résultat est une différence entre la représentation Active Directory des valeurs de la boîte aux lettres RemoteRecipientType et RemoteDisplayType et celle dans Exchange Online définition de la boîte aux lettres comme partagée. <p> Le client est responsable de s’assurer que toutes les boîtes aux lettres partagées sont correctement mise en service à l’aide `New-RemoteMailbox -Shared` `Enable-RemoteMailbox -Shared` de , ou `Set-RemoteMailbox -Shared` . Consultez cette référence pour savoir comment convertir [la boîte aux lettres d’un utilisateur dans un environnement hybride.](/microsoft-365/admin/email/convert-user-mailbox-to-shared-mailbox)|Si vous ne parvient pas à effectuer cette tâche avant la phase 5 [migration de Exchange Online], il se peut que des NDR pour les boîtes aux lettres partagées se convertissent en boîtes aux lettres sans permis et que l’accès partagé des boîtes aux lettres concernées soit perdu. Les boîtes aux lettres partagées sont converties de manière inattendue en boîtes aux lettres utilisateur après l’installation de la synchronisation d’annuaires dans un déploiement hybride [Exchange](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes) décrit l’impact de ne pas résoudre ce problème avant la fin de la migration Exchange Online.|


## <a name="skype-for-business-online"></a>Skype Entreprise Online

<!-- before phase 7 -->

**S’applique** à : Skype pour les clients Business Online<br>
**Lorsqu’elle est** appliquée : à tout moment avant le début de la phase 7

<br>

****

|Étapes|Description|Impact|
|---|---|---|
|Déployez Teams client de bureau pour les utilisateurs qui accèdent Skype Entreprise en Allemagne.|La migration déplace Skype Entreprise utilisateurs vers Microsoft Teams pour la collaboration, les appels et la conversation. Déployez le client Microsoft Teams bureau ou assurez-vous qu’un navigateur pris en charge est disponible.|L’inaction entraîne l’indisponibilité des services Microsoft Teams collaboration.|
|Examiner et préparer les modifications DNS liées à la migration.|La zone DNS du client change pour Skype Entreprise Online.|<ul><li>Nous vous recommandons de mettre à jour la durée de vie (TTL) de tous les enregistrements DNS de domaine d’un client sur 5 minutes pour accélérer l’actualisation des enregistrements DNS. Toutefois, le cutover géré par Microsoft associé à cette modification DNS peut se produire à tout moment dans la fenêtre de modification de 24 heures fournie.</li><li>La perturbation du service est possible à l’avenir. Les utilisateurs ne pourront pas se connecter Skype Entreprise et seront redirigés vers l’expérience Teams migrée dans les services Office 365 client.</li></ul>|
|Préparez la formation et la préparation de l’utilisateur final et de l’administration pour la transition vers Microsoft Teams.|Pour réussir votre transition de Skype à Teams en planant la communication et la préparation des utilisateurs.|<ul><li>Les clients doivent connaître les nouveaux services et savoir comment les utiliser une fois leurs services Office 365 services.</li><li>Une fois que des modifications DNS ont été apportées pour les domaines de la première ligne et les domaines de la première ligne, les utilisateurs se connectent à Skype Entreprise et voient qu’ils sont désormais migrés vers Teams. Cela télécharge également le client de bureau pour Teams en arrière-plan.</li></ul>|


## <a name="mobile-device-management"></a>Gestion des appareils mobiles

<!-- before phase 5 -->
**S’applique à :** Clients utilisant une solution de gestion des périphériques mobiles (MDM) tierce<br>
**Lorsqu’elle est** appliquée : à tout moment avant le démarrage de la phase 5

<br>

****

|Étapes|Description|S’applique à|Impact|
|---|---|---|---|
|Préparez la formation des utilisateurs finaux et de l’administration sur la suppression et l’ajout de leur compte à Microsoft Outlook pour iOS et Android.|Les comptes Microsoft Outlook pour iOS et Android configurés avec des boîtes aux lettres dans Microsoft Cloud Deutschland peuvent être supprimés et ajoutés à nouveau à Outlook afin de synchroniser correctement la nouvelle configuration des services Office 365.|Microsoft Outlook pour les clients iOS et Android|Outlook boîtes aux lettres précédemment configurées pour Microsoft Cloud Deutschland peuvent ne pas prendre en compte la nouvelle configuration Office 365 Services, entraînant des erreurs et une dégradation des performances des autres expériences utilisateur. Les administrateurs informatiques sont invités à fournir une documentation qui demande aux utilisateurs de supprimer et de rajouter leurs comptes à Microsoft Outlook pour iOS et Android si des problèmes de signature ou de synchronisation de messages se produisent après la migration.|
|Déterminez si une reconfiguration est requise après la migration.|Les solutions de gestion des périphériques mobiles (MDM) peuvent cibler des `outlook.de` points de terminaison. Dans cette transition vers Office 365 Services, les profils clients doivent être mis à jour vers l’URL des services Office 365, `outlook.office365.com` .|Exchange Online clients et mdm|Les clients peuvent continuer à fonctionner tant que le point de terminaison est accessible, mais ils échoueront si les points de terminaison Microsoft Cloud Deutschland ne `outlook.de` sont plus disponibles.|


## <a name="line-of-business-apps"></a>Applications métier

**S’applique à :** Clients utilisant des applications métier avec des points de terminaison fournis par Microsoft Cloud Deutschland<br>
**Appliqué :** après la fin de la phase 2 et avant la fin de la phase 9

Si vous utilisez un service tiers ou des applications métier intégrées à Office 365, vous devez résoudre les dépendances envers les points de terminaison fournies par l’instance Microsoft Cloud Deutschland. Par exemple, si vos applications LOB se connectent, vous devez modifier `https://graph.microsoft.de/` le point de terminaison en `https://graph.microsoft.com/` . Les points de terminaison du service Microsoft Office 365 global deviennent disponibles pour votre client après la phase 2.

Pendant la migration, alors que votre organisation se trouve entre les phases 2 et 9, vous ne pouvez pas ajouter d’applications tierces multi-locataires (MTA) à votre organisation. Une fois la migration terminée la phase 9, vous pouvez reprendre l’ajout ou le consentement aux applications MTA pour votre organisation.


| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Déterminez si une reconfiguration est requise après la migration. | Les applications et services tiers qui s’intègrent Office 365 peuvent être codés pour s’attendre à des adresses IP et des URL Microsoft Cloud Deutschland. | Action requise. L’inaction peut entraîner des défaillances du service ou du logiciel client. |


|Étapes|Description|Impact|
|---|---|---|
|Déterminez si une reconfiguration est requise après la migration.|Les applications et services tiers qui s’intègrent Office 365 peuvent être codés pour s’attendre à des adresses IP et des URL Microsoft Cloud Deutschland.|Action requise. L’inaction peut entraîner des défaillances du service ou du logiciel client.|


## <a name="dynamics-365"></a>Dynamics 365

**S’applique à**: Clients utilisant Microsoft Dynamics 365

<br>

****

|Étapes|Description|Impact|
|---|---|---|
|Pour les abonnements en bac à sable Dynamics 365, n’oubliez pas de télécharger l’environnement de production de l’instance Dynamics SQL à partir de votre abonnement Dynamics 365 dans Microsoft Cloud Deutschland. La dernière sauvegarde de production doit être restaurée dans le bac à sable avant la migration en bac à sable.|Pour migrer Dynamics 365, les clients doivent s’assurer que l’environnement en bac à sable est actualisé avec la dernière base de données de production.|L FastTrack’équipe de l’utilisateur aidera les clients à effectuer des essais secs pour valider la mise à niveau de version de 8.x vers 9.1.x.|


## <a name="power-bi"></a>Power BI

**S’applique à**: Clients utilisant Power BI

<br>

****

|Étapes|Description|Impact|
|---|---|---|
|Suppression d’objets de Power BI abonnements qui ne seront pas migrés de Power BI Microsoft Cloud Deutschland vers Office 365 services.|La migration des services Power BI nécessite une action du client pour supprimer certains artefacts, tels que les jeux de données et les tableaux de bord.|Les administrateurs peuvent être dans l’devoir de supprimer les éléments suivants de leur abonnement : <ul><li>Real-Time de données (par exemple, les jeux de données push ou de diffusion en continu)</li><li>Power BI la configuration et la source de données de la passerelle de données sur site </li></ul>|


## <a name="microsoft-azure"></a>Microsoft Azure

Si vous utilisez la même partition d’identité Azure Active Directory pour Office 365 et Microsoft Azure dans l’instance Microsoft Cloud Deutschland, assurez-vous que vous préparez la migration pilotée par le client des services Microsoft Azure.

> [!NOTE]
> La migration de vos services Microsoft Azure risque de ne pas commencer avant que votre client Office 365 n’ait atteint la phase de migration 9 et doit être terminée avant le début de la phase 10.

Les clients qui utilisent Office 365 ressources Azure (par exemple, réseau, calcul et stockage) effectueront la migration des ressources vers l’instance Office 365 services. Cette migration est la responsabilité du client. Les publications du Centre de messages signalent le début. La migration doit être effectuée avant la finalisation de l’organisation Azure AD dans l’environnement Office 365 services. Pour les migrations Azure, consultez le manuel de migration Azure, vue d’ensemble des conseils de [migration pour Azure Germany.](/azure/germany/germany-migration-main)

<br>

****

|Étapes|Description|Impact|
|---|---|---|
|Déterminez les services Azure en cours d’utilisation et préparez la migration future de l’Allemagne vers le client Office 365 services en travaillant avec vos partenaires. Suivez les étapes décrites dans le [manuel de migration Azure.](/azure/germany/germany-migration-main)|<ul><li>La migration des ressources Azure est une responsabilité du client et nécessite un effort manuel en suivant les étapes prescrites. Il est essentiel de comprendre quels services sont utilisés dans l’organisation pour réussir la migration des services Azure.</li><li>Office 365 Les clients allemands qui ont des abonnements Azure sous la même partition d’identité (organisation) doivent respecter l’ordre prévu par Microsoft lorsqu’ils peuvent commencer la migration des abonnements et des services.</li></ul>|<ul><li>Les clients peuvent avoir plusieurs abonnements Azure, chacun contenant des composants d’infrastructure, de services et de plateforme.</li><li>Les administrateurs doivent identifier les abonnements et les parties prenantes pour s’assurer que la migration rapide et la validation sont possibles dans le cadre de cet événement de migration.</li><li>L’échec de la migration de ces abonnements et composants Azure dans la chronologie prescrite affecte la fin de la transition de Office et Azure AD vers les services Office 365 et peut entraîner une perte de données.</li><li>Une notification du centre de messages signale le point auquel la migration dirigée par le client peut commencer.</li></ul>|


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

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
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
