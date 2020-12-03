---
title: Informations supplémentaires sur l’expérience de la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
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
description: 'Résumé : informations supplémentaires sur l’expérience client lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers les services Office 365 dans la nouvelle région de centre de données allemande.'
ms.openlocfilehash: 1eef8be624a92bf2dcaba8f0df2147697202be3a
ms.sourcegitcommit: ff1f0a97e9d43bc786f04d2ea7e01695531b9f28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49560837"
---
# <a name="additional-experience-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations supplémentaires sur l’expérience de la migration à partir de Microsoft Cloud Deutschland 

Les sections suivantes fournissent des informations supplémentaires sur les expériences des clients.

## <a name="services"></a>Services

### <a name="azure-ad"></a>Azure AD

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Client Azure AD dans Microsoft Cloud Deutschland copié vers les services Office 365. | Azure AD copie le client vers les services Office 365. Les identificateurs de client et d’utilisateur sont conservés. Les appels au service Azure AD sont redirigés de Microsoft Cloud Deutschland vers les services Office 365 et sont transparents pour les services. | Tous les clients Office | -Le règlement général sur la protection des données (RGPD) les demandes des personnes concernées (DSR) sont exécutées à partir du portail d’administration Azure pour les demandes ultérieures. Toute donnée de diagnostic héritée ou non client résidente dans Microsoft Cloud Deutschland est supprimée au moins 30 jours. <br><br> -Les clients qui utilisent des authentifications fédérées avec Active Directory Federation Services (AD FS) ne doivent pas modifier les URI d’émetteur utilisés pour toutes les authentifications avec Active Directory local lors de la migration. La modification des URI de l’émetteur entraîne des échecs d’authentification pour les utilisateurs du domaine. Les URI d’émetteur peuvent être modifiés directement dans AD FS ou lorsqu’un domaine est converti d’un domaine _géré_ à un domaine _fédéré_ , et inversement. Nous recommandons aux clients d’ajouter, de supprimer ou de convertir un domaine fédéré dans le client Azure AD qui a été migré. Les URI de l’émetteur peuvent être modifiés une fois la migration entièrement terminée. <br><br> -Requêtes Multi-Factor Authentication (MFA) qui utilisent l’afficheur Microsoft authentificateur en tant qu’ObjectID (GUID) de l’utilisateur, tandis que le client est copié vers les services Office 365. Les requêtes MFA s’exécuteront comme prévu malgré ce comportement d’affichage.  Les comptes d’authentificateur Microsoft qui ont été activés à l’aide des points de terminaison des services Office 365 afficheront le nom d’utilisateur principal (UPN).  Les comptes ajoutés à l’aide de points de terminaison de Microsoft Cloud Deutschland affichent l’ID de l’utilisateur, mais fonctionne avec les points de terminaison des services Microsoft Cloud Deutschland et Office 365.  |
| Établir AuthServer en local pointant vers le service STS global. | Cela garantit que les demandes des utilisateurs qui migrent vers Microsoft Cloud Deutschland pour les demandes de disponibilité Exchange ciblant l’environnement local hybride sont authentifiées pour accéder au service local. De même, cela garantit l’authentification des demandes en provenance des points de terminaison locaux des services Office 365. | Clients Exchange Online avec déploiements hybrides (sur site) | Une fois la migration Azure AD terminée, l’administrateur de la topologie Exchange locale (hybride) doit ajouter un nouveau point de terminaison de service d’authentification pour les services Office 365. À l’aide de cette commande de Microsoft Exchange PowerShell, remplacez `<TenantID>` par l’ID de client de votre organisation (dans le portail Azure sur **Azure Active Directory**). <br><br> - `New-AuthServer GlobalMicrosoftSts -AuthMetadataUrl https://accounts.accesscontrol.windows.net/<TenantId>/metadata/json/1` <br> <br> Si vous ne parvenez pas à effectuer cette tâche, il se peut que des demandes de disponibilité hybride ne fournissent pas d’informations pour les utilisateurs de boîtes aux lettres qui ont été migrés à partir de Microsoft Cloud Deutschland vers les services Office 365.  |
| Migration des ressources Azure. | Les clients qui utilisent Office 365 et les ressources Azure (par exemple, mise en réseau, calcul et stockage) effectueront la migration des ressources vers l’instance des services Office 365. Cette migration est une responsabilité pour les clients. Les publications du centre de messages signalent le démarrage. La migration doit être effectuée avant la finalisation de l’organisation Azure AD dans l’environnement des services Office 365. | Clients Azure | Pour les migrations Azure, voir le manuel de migration Azure, [Overview of migration Guidance for Azure Germany](https://docs.microsoft.com/azure/germany/germany-migration-main). |
|||||

<!--
[Reference: Experience][Data Protection] Experience][
[Reference: Experience][Federation] 
[Reference: Experience][MFA]  


[Reference: Experience – Post Migration][Hybrid]    
        

[Reference: Experience – During Migration] [Azure] 
-->

### <a name="exchange-online"></a>Exchange Online

Si vous utilisez **Set-applet userphoto**:

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| La nouvelle région Germany est ajoutée à une configuration existante de l’organisation et les boîtes aux lettres sont déplacées vers les services Office 365. | La configuration d’Exchange Online ajoute la nouvelle région locale allemande à l’organisation de transition. Cette région des services Office 365 est définie par défaut, ce qui permet au service d’équilibrage de charge interne de redistribuer des boîtes aux lettres à la région par défaut appropriée dans les services Office 365. Dans cette transition, les utilisateurs des deux côtés (Allemagne ou services Office 365) se trouvent dans la même organisation et peuvent utiliser le point de terminaison de l’URL. |  Exchange Online | Si une boîte aux lettres utilisateur a été migrée mais qu’une boîte aux lettres d’administrateur n’a pas été migrée, ou inversement, les administrateurs ne pourront pas exécuter **Set-applet userphoto**, une cmdlet PowerShell. Dans ce cas, un administrateur doit transmettre une chaîne supplémentaire dans `ConnectionUri` lors de la configuration de la connexion à l’aide de la syntaxe suivante : <br><br> `https://outlook.office.de/PowerShell-LiveID?email=<user_email>` <br><br> où `<user_email>` est l’espace réservé pour l’ID de messagerie de l’utilisateur dont la photo doit être modifiée à l’aide de **Set-applet userphoto**. |
|||||

<!--
[Reference: Experience][Exchange Online]  [if using Set-UserPhoto] 
-->  

Si vous utilisez un déploiement hybride sur site :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
|Arrêtez ou supprimez tous les déplacements de boîtes aux lettres d’intégration ou de par débarquement.  | Cela permet de s’assurer que les demandes de déplacement n’échouent pas avec une erreur. | Clients Exchange Online avec déploiements hybrides (sur site) | Action requise. Si ce n’est pas le cas, il se peut que le service ou les clients logiciels échouent. |
|||||

<!--
[Reference: Experience][Hybrid] 
--> 


### <a name="dynamics"></a>Dynamics

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Ressources Microsoft Dynamics | Les clients disposant de Microsoft Dynamics seront engagés par ingénierie ou FastTrack pour effectuer la transition vers l’instance des services Office 365. * | Clients Microsoft Dynamics 365 | -Après la migration, l’administrateur valide l’organisation. <br><br> -L’administrateur modifie les flux de travail, le cas échéant. <br><br> -L’administrateur efface le mode AdminOnly selon vos besoins. <br><br> -L’administrateur modifie le type d’organisation à partir du _bac à sable_, selon le cas. <br><br> -Avertir les utilisateurs finaux de la nouvelle URL pour accéder à l’instance (org). <br><br> -Mettez à jour toutes les connexions entrantes vers la nouvelle URL de point de terminaison. <br><br> -Le service Dynamics ne sera pas disponible pour les utilisateurs pendant la transition. <br><br> -Les utilisateurs doivent valider l’intégrité et les fonctionnalités de l’Organisation après la migration de chaque organisation.  |
|||||

\* (i) les clients disposant de Microsoft Dynamics 365 doivent effectuer des actions dans ce scénario de migration, comme défini par le processus de migration fourni. (II) si le client ne parvient pas à effectuer une action, Microsoft ne pourra pas terminer la migration. (III) lorsque Microsoft ne parvient pas à effectuer la migration en raison de l’inaction du client, l’abonnement du client expire le 29 octobre 2021. 


### <a name="power-bi"></a>Power BI

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration des ressources Power BI | Les clients avec Microsoft Power BI seront engagés par ingénierie ou FastTrack après le déclenchement manuel d’un outil de migration PBI existant pour effectuer une transition Power BI vers l’instance des services Office 365.\*\* | Clients Microsoft Power BI | -Les éléments Power BI suivants ne seront _pas_ migrés et doivent être recréés : <br><br> -Des jeux de données en temps réel (par exemple, des jeux de données en continu ou par émission). <br> -Configuration de passerelle de données sur site et source de données. <br> -Les rapports créés en plus des jeux de données en temps réel ne sont pas disponibles après la migration et doivent être recréés. <br><br> -Les services Power BI ne seront pas disponibles pour les utilisateurs pendant la transition. L’indisponibilité du service ne doit pas être supérieure à 24 heures. <br><br> -Les utilisateurs doivent reconfigurer les sources de données et leurs passerelles de données sur site avec le service Power BI après la migration.  En attendant, les utilisateurs ne pourront pas utiliser ces sources de données pour effectuer une actualisation planifiée et/ou des requêtes directes sur ces sources de données. <br><br> -Les capacités et les espaces de travail Premium ne peuvent pas être migrés. Les clients doivent supprimer toutes les capacités avant la migration et les recréer après la migration. Déplacez les espaces de travail vers les capacités comme vous le souhaitez.  |
|||||

\*\* (i) les clients avec Microsoft Power BI doivent prendre des mesures dans ce scénario de migration, comme défini par le processus de migration fourni. (II) si le client ne parvient pas à effectuer une action, Microsoft ne pourra pas terminer la migration. (III) lorsque Microsoft ne parvient pas à effectuer la migration en raison de l’inaction du client, l’abonnement du client expire le 29 octobre 2021. 


### <a name="office-apps"></a>Applications Office

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Clients, Office Online pendant le basculement du client Office, Azure AD finalise l’étendue du client pour pointer vers les services Office 365. | Ce changement de configuration permet aux clients Office de mettre à jour et de pointer vers les points de terminaison des services Office 365. | Tous les clients Office | -Supprimez MSOID CNAME du DNS appartenant au client, le cas échéant. <br><br> -Avertir les utilisateurs de fermer _toutes les_ applications Office, puis de se reconnecter (ou forcer les clients à redémarrer et aux utilisateurs de se connecter) pour permettre aux clients Office de prendre les modifications. <br><br> -Avertir les utilisateurs et le personnel du support technique que les utilisateurs *peuvent* voir apparaître une bannière Office pour les inviter à réactiver les applications Office dans les 72 heures du basculement. <br><br> -Toutes les applications Office sur les ordinateurs personnels doivent être fermées, et les utilisateurs doivent se déconnecter, puis se reconnecter. Dans la barre d’activation jaune, connectez-vous pour réactiver les services Office 365. <br><br> -Les machines partagées nécessitent des actions similaires aux machines personnelles et ne nécessitent pas de procédure spéciale. <br><br> -Sur les appareils mobiles, les utilisateurs doivent se déconnecter des applications, les fermer, puis se reconnecter. |
|||||

<!--
[Reference: Experience][Office Apps]
--> 

## <a name="during-migration"></a>Pendant la migration


### <a name="exchange-online"></a>Exchange Online

Pour eDiscovery :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Lors de la migration, les recherches de découverte électronique échouent ou renvoient 0 résultats pour SharePoint Online, OneDrive entreprise et les emplacements Exchange Online qui ont été migrés. | Lors de la migration, les clients peuvent continuer à créer des cas, des suspensions, des recherches et des exportations dans le [Centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations), notamment la [recherche de contenu](https://docs.microsoft.com/microsoft-365/compliance/search-for-content).  Toutefois, les recherches sur SharePoint Online, OneDrive entreprise et les emplacements Exchange Online qui ont été migrés renvoient 0 résultat, sinon une erreur est générée. Pour la correction, reportez-vous à la colonne _impact_ . | Tous les clients utilisant eDiscovery |  Si une recherche renvoie 0 résultat ou une erreur lors de la migration, effectuez l’action suivante pour SharePoint Online : <br><br>  Téléchargez des sites directement à partir du site SharePoint Online/OneDrive entreprise en suivant les instructions de la procédure de [téléchargement des fichiers et des dossiers à partir de OneDrive ou de SharePoint](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05). Cette méthode nécessite des autorisations d’administrateur SharePoint Online ou des autorisations en lecture seule sur le site. <br><br> Si les limites sont dépassées, comme expliqué dans [Télécharger des fichiers et des dossiers à partir de OneDrive ou de SharePoint](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05), les clients peuvent utiliser le client de synchronisation OneDrive entreprise en suivant les instructions de la rubrique [synchroniser des fichiers SharePoint et teams avec votre ordinateur](https://support.office.com/article/sync-sharepoint-files-with-the-new-onedrive-sync-app-6de9ede8-5b6e-4503-80b2-6190f3354a88). <br><br> -Exchange Online <br><br> - [Découverte électronique inaltérable dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/ediscovery/ediscovery) |
|||||

<!--
[Reference: Experience – During Migration][ [eDiscovery]
-->          


### <a name="sharepoint-online"></a>SharePoint Online

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| SharePoint et OneDrive sont en transition. | SharePoint et OneDrive sont migrés de Microsoft Cloud Deutschland vers les services Office 365 dans cette phase. Les URL de Microsoft Cloud Deutschland existantes sont préservées ( `contoso.sharepoint.de` ). Les jetons émis par les services Microsoft Cloud Deutschland ou Office 365 sont valides pendant la transition. | Clients SharePoint | Les flux de travail SharePoint 2013 Inflight seront rompus lors de la migration et doivent être republiés après la migration. |
|||||

<!--
[Reference: Experience – During Migration][ [SPO]
-->  

### <a name="skype-for-business-online"></a>Skype Entreprise Online

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration de Skype entreprise vers Teams. | Les clients Skype entreprise existants sont migrés vers les services Office 365 en Europe, puis transférés vers Microsoft teams dans la région d’Allemagne des services Office 365. | Clients Skype entreprise |  PowerShell utilisera pour administrer les paramètres et les stratégies de votre client et de vos utilisateurs. Lors de la connexion à une session PowerShell, ajoutez les éléments suivants : <br><br> `-OverridePowershellUri "https://admin4E.online.lync.com/OcsPowershellOAuth"` |
|||||

<!--
[Reference: Experience – During Migration][ [SfBO]
-->  


## <a name="post-migration"></a>Après la migration

### <a name="azure-ad"></a>Azure AD

Pour les hybrides :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Mettez à jour Azure AD Connect. | Une fois le passage à Azure AD terminé, l’organisation utilise pleinement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit s’assurer que le processus de synchronisation Delta a été finalisé, et ensuite, modifiez la valeur de chaîne de `AzureInstance` 3 (Microsoft Cloud Deutschland) à 0 dans le chemin d’accès du Registre `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Azure AD Connect` . | Organisations Azure AD hybrides : sociétés connectées | Modifiez la valeur de `AzureInstance` la clé de registre. Si ce n’est pas le cas, les objets ne seront pas synchronisés une fois que les points de terminaison Deutschland Cloud de Microsoft ne seront plus disponibles. |
|||||

<!--
[Reference: Experience – Post Migration][Hybrid]
--> 

Pour l’authentification fédérée :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Supprimer les approbations de partie de confiance de Microsoft Cloud Deutschland AD FS. | Une fois le passage à Azure AD terminé, l’organisation utilise pleinement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit supprimer l’approbation de partie de confiance pour les points de terminaison Deutschland Cloud de Microsoft. Cette opération n’est possible que si aucune application du client ne pointe vers des points de terminaison Cloud Deutschland lorsque Azure AD est exploité en tant que fournisseur d’identité (IdP). | Organisations d’authentification fédérée | Aucun. |
|||||

<!--
[Reference: Experience – Post Migration][Federated]
-->             

Pour Azure AD :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Les demandes de participation à un groupe Azure AD au cours des 30 derniers jours avant la migration devront être de nouveau demandées si la demande d’origine n’a pas été approuvée. | Les clients de l’utilisateur final devront utiliser le panneau d’accès pour soumettre une demande de participation à un groupe Azure AD si ces demandes n’ont pas été approuvées au cours des 30 derniers jours précédant la migration. | Les utilisateurs finaux dont les demandes d’approbation de groupe Azure AD n’ont pas été approuvées au cours des 30 derniers jours avant la migration |  En tant qu’utilisateur final : <ol><li>Accédez au [panneau accès](https://account.activedirectory.windowsazure.com/r#/joinGroups).</li><li>Recherchez un groupe Azure AD dont l’approbation d’appartenance était en attente dans 30 jours avant la migration.</li><li>Demande de rejoindre le groupe Azure AD.</li></ol> Les demandes de participation à un groupe qui sont actives moins de 30 jours avant la migration ne peuvent pas être approuvées, sauf si elles sont redemandées après la migration. |
|||||

<!--
[Reference: Experience – Post Migration][Azure AD]
--> 

Pour DNS :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Mettre à jour les services DNS locaux pour les points de terminaison des services Office 365. | Les entrées DNS gérées par le client qui pointent vers Office 365 Germany doivent être mises à jour pour pointer vers les points de terminaison des services Office 365. | Tous les clients Office | Action requise. Si ce n’est pas le cas, il se peut que le service ou les clients logiciels échouent. |
|||||

<!--
 [Reference: Experience – Post Migration][DNS]
-->

Pour les services tiers pour les points de terminaison des services Office 365 :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Mettre à jour les partenaires et les services tiers pour les points de terminaison des services Office 365. | -Les services tiers et les partenaires qui pointent vers Office 365 Germany doivent être mis à jour pour pointer vers les points de terminaison des services Office 365. Exemple : ré-enregistrer, en fonction de vos fournisseurs et partenaires, la version d’application de la Galerie d’applications, si disponible. <br><br> -Pointez toutes les applications personnalisées qui utilisent l’API Graph de `graph.microsoft.de` vers `graph.microsoft.com` . Les autres API avec des points de terminaison modifiés doivent également être mises à jour, si elles sont exploitées. <br><br> -Modifiez toutes les applications d’entreprise non tierces pour rediriger vers les points de terminaison internationaux.  | Tous les clients Office | Action requise. Si ce n’est pas le cas, il se peut que le service ou les clients logiciels échouent. |
|||||

<!--
 [Reference: Experience – Post Migration][]
--> 

### <a name="exchange-online"></a>Exchange Online

Si vous utilisez une configuration Exchange hybride :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Réexécutez l’Assistant Configuration hybride (HCW) sur les services Office 365. | La configuration HCW existante est conçue pour prendre en charge Microsoft Cloud Deutschland. Une fois la migration des services Exchange terminée, nous découples la configuration locale de Microsoft Cloud Deutschland. | Clients Exchange Online qui exécutent un déploiement hybride | -Action requise. Si ce n’est pas le cas, il se peut que le service ou les clients logiciels échouent. Avant le début de la migration de boîtes aux lettres Exchange (avec au moins 5 jours de notification), informez les clients qu’ils doivent arrêter et supprimer tous les déplacements ou par débarquement de leurs boîtes aux lettres.  Si ce n’est pas le cas, ils verront des erreurs dans leurs demandes de déplacement. <br><br> -Une fois la migration des boîtes aux lettres Exchange terminée, informez les clients qu’ils peuvent reprendre l’intégration et par débarquement. <br> L’exécution de **test-MigrationServerAvailabiilty**, une cmdlet PowerShell, lors de la migration d’Exchange à partir de Microsoft Cloud Deutschland vers Office 365 services peut ne pas fonctionner. Toutefois, elle fonctionne correctement une fois la migration terminée. <br><br> Si les clients ont des problèmes d’informations d’identification ou d’autorisation après la migration des boîtes aux lettres, les utilisateurs peuvent entrer de nouveau leurs informations d’identification d’administrateur local dans le point de terminaison de migration en exécutant `Set-MigrationEndpoint endpointName -Credential $(Get-Credential)` ou en définissant les mêmes à l’aide du panneau de configuration Exchange (ECP).  |

<!--
[Reference: Experience – Post Migration][Hybrid]  
[Reference: Experience – Post Migration][Exchange Online]
--> 

Pour eDiscovery :

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
|  Tous les emplacements SharePoint Online, OneDrive entreprise et Exchange Online ont été migrés avec le centre de sécurité et de conformité (SCC). | Toutes les activités eDiscovery doivent être exécutées à partir du client dans le monde entier. Les recherches seront désormais effectuées à 100%.  Les échecs ou les erreurs doivent suivre les canaux de support habituels. | Tous les clients qui utilisent eDiscovery | Aucun. |
| Supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées lors des étapes préalables à la migration | Les clients peuvent supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées pendant le travail de pré-migration des clients. | Tous les clients qui ont appliqué une stratégie de rétention dans le cadre des étapes préalables à la migration. | Aucun. |
|||||

<!--
 [Reference: Experience – Post Migration][ [eDiscovery]             

[Reference: Experience – Post Migration][ [eDiscovery]
-->             

### <a name="sharepoint-online"></a>SharePoint Online

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Republiez les flux de travail SharePoint 2013. | Dans le travail de pré-migration, nous avons réduit le nombre de flux de travail SharePoint 2013. Une fois la migration terminée, le client peut republier les flux de travail. | Tous les clients Office | Il s’agit d’une action obligatoire. Si vous ne le faites pas, vous risquez de confondre les utilisateurs et d’obtenir des appels au support technique. |
| Partager des éléments via Outlook | Le partage d’éléments via Outlook ne fonctionne plus après le basculement du client. | Sharepoint Online et OneDrive Entreprise | -Dans SharePoint Online et OneDrive entreprise, vous pouvez partager des éléments via Outlook. Après avoir appuyé sur le bouton Outlook, un lien partageable est créé et envoyé dans un nouveau message dans Outlook Web App. <br><br> -Après le basculement du client, cette méthode de partage ne fonctionnera pas. Nous reconnaissons qu’il s’agit d’un problème connu. Toutefois, étant donné que cette fonctionnalité Outlook se trouve dans le chemin d’accès de désapprobation, la résolution du problème n’est planifiée qu’une fois la désapprobation déployée. |

<!--
 [Reference: Experience – Post Migration][ [SPO]
-->

## <a name="next-step"></a>Étape suivante

[Comprendre les actions et les impacts des phases de migration](ms-cloud-germany-transition-phases.md)

## <a name="more-information"></a>Plus d’informations

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client lors de la migration](ms-cloud-germany-transition-experience.md)

Navigation par le biais de la transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour les [services](ms-cloud-germany-transition-add-general.md), les [appareils](ms-cloud-germany-transition-add-devices.md), les [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
