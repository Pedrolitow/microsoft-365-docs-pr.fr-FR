---
title: Actions et impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland (avancé)
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
description: 'Résumé : Informations supplémentaires sur l’expérience client lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemande.'
ms.openlocfilehash: 3f9bc40d7551dfcdb65abcf8b150f98b8242d7d2
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921689"
---
# <a name="migration-phases-actions-and-impacts-for-the-migration-from-microsoft-cloud-deutschland-advanced"></a>Actions et impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland (avancé) 

Les migrations de clients de Microsoft Cloud Deutschland vers la région Allemagne des services Office 365 de Microsoft sont exécutées sous la forme d’un ensemble de phases et leurs actions configurées pour chaque charge de travail. Cette figure montre les neuf phases de migration vers les nouveaux centres de données allemands.

![Les neuf phases de migration vers les nouveaux centres de données allemands](../media/ms-cloud-germany-migration-opt-in/migration-organization.png)

Les sections suivantes fournissent des informations supplémentaires sur les expériences client lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemande.

## <a name="services"></a>Services

### <a name="azure-ad-phase-2-of-9"></a>Azure AD (phase 2 sur 9)

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Client Azure AD dans Microsoft Cloud Deutschland copié dans les services Office 365. | Azure AD copie le client dans les services Office 365. Les identificateurs de client et d’utilisateur sont conservés. Les appels de service Azure AD sont redirigés de Microsoft Cloud Deutschland vers les services Office 365 et sont transparents pour les services. | Tous les clients Office | - Les demandes des personnes soumises au règlement général sur la protection des données (R GDPR) sont exécutées à partir du portail d’administration Azure pour les demandes futures. Toutes les données de diagnostic héritées ou non client résidant dans Microsoft Cloud Deutschland sont supprimées au cours ou avant 30 jours. <br><br> - Les clients qui utilisent des authentifications fédérées avec les services AD FS (Active Directory Federation Services) ne doivent pas apporter de modifications aux AUTHENTIFICATION d’émetteur utilisées pour toutes les authentifications avec Active Directory local lors de la migration. La modification des URL d’émetteur entraîne des échecs d’authentification pour les utilisateurs du domaine. Les URIs d’émetteur peuvent être modifiés directement dans  AD  FS ou lorsqu’un domaine est converti de géré en fédéré et vice-versa. Nous recommandons aux clients de ne pas ajouter, supprimer ou convertir un domaine fédéré dans le client Azure AD qui a été migré. Les URL de l’émetteur peuvent être modifiées une fois la migration terminée. <br><br> - Les demandes d’authentification multifacteur (MFA) qui utilisent Microsoft Authenticator s’affichent en tant qu’objectid utilisateur (guid) pendant que le client est copié dans les services Office 365. Les demandes mfa s’exécutent comme prévu malgré ce comportement d’affichage.  Les comptes Microsoft Authenticator qui ont été activés à l’aide des points de terminaison des services Office 365 affichent le nom d’utilisateur principal (UPN).  Les comptes ajoutés à l’aide des points de terminaison Microsoft Cloud Deutschland afficheront l’objectid utilisateur, mais fonctionneront avec les points de terminaison des services Microsoft Cloud Deutschland et Office 365.  |
| Établir authServer local pointant vers le service STS global. | Cela garantit que les demandes des utilisateurs qui migrent vers Microsoft Cloud Deutschland pour les demandes de disponibilité Exchange qui ciblent l’environnement local hybride sont authentifiées pour accéder au service local. De même, cela garantit l’authentification des demandes provenant de l’local vers les points de terminaison des services Office 365. | Clients Exchange Online avec déploiements hybrides (locaux) | Une fois la migration d’Azure AD terminée, l’administrateur de la topologie Exchange (hybride) sur site doit ajouter un nouveau point de terminaison de service d’authentification pour les services Office 365. Avec cette commande à partir d’Exchange PowerShell, remplacez-la par l’ID de locataire de votre organisation (dans le portail `<TenantID>` Azure sur Azure Active **Directory).** <br><br> - `New-AuthServer GlobalMicrosoftSts -AuthMetadataUrl https://accounts.accesscontrol.windows.net/<TenantId>/metadata/json/1` <br> <br> Si vous ne parvient pas à effectuer cette tâche, les demandes de libre-service hybrides risquent de ne pas fournir d’informations aux utilisateurs de boîtes aux lettres qui ont été migrés de Microsoft Cloud Deutschland vers les services Office 365.  |
| Migration des ressources Azure. | Les clients qui utilisent des ressources Office 365 et Azure (par exemple, réseau, calcul et stockage) effectueront la migration des ressources vers l’instance des services Office 365. Cette migration est une responsabilité pour les clients. Les publications du Centre de messages signalent le début. La migration doit être effectuée avant la finalisation de l’organisation Azure AD dans l’environnement de services Office 365. | Clients Azure | Pour les migrations Azure, consultez le manuel de migration Azure, vue d’ensemble des conseils de [migration pour Azure Germany.](https://docs.microsoft.com/azure/germany/germany-migration-main) |
|||||

### <a name="exchange-online-phase-5-of-9"></a>Exchange Online (phase 5 sur 9)

Si vous utilisez **Set-UserPhoto**:

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| La nouvelle région d’Allemagne est ajoutée à une configuration d’organisation existante et les boîtes aux lettres sont déplacées vers les services Office 365. | La configuration d’Exchange Online ajoute la nouvelle région allemande locale à l’organisation en transition. Cette région de services Office 365 est définie par défaut, ce qui permet au service d’équilibrage de charge interne de redistribuer les boîtes aux lettres vers la région par défaut appropriée dans les services Office 365. Dans cette transition, les utilisateurs des deux côtés (services d’Allemagne ou d’Office 365) sont dans la même organisation et peuvent utiliser l’un ou l’autre point de terminaison d’URL. |  Exchange Online | Si une boîte aux lettres d’utilisateur a été miggrée, mais qu’une boîte aux lettres d’administrateur n’a pas été miggrée, ou inversement, les administrateurs ne pourront pas exécuter **Set-UserPhoto**, une cmdlet PowerShell. Dans ce cas, un administrateur doit transmettre une chaîne supplémentaire au cours de la connexion définie à l’aide `ConnectionUri` de la syntaxe suivante : <br><br> `https://outlook.office.de/PowerShell-LiveID?email=<user_email>` <br><br> où est l’espace réservé pour l’ID de messagerie de l’utilisateur dont la photo doit être modifiée à l’aide `<user_email>` **de Set-UserPhoto**. |
|||||

Si vous utilisez un déploiement hybride local :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
|Arrêtez ou supprimez les déplacements d’intégration ou de suppression de boîtes aux lettres.  | Cela garantit que les demandes de déplacement n’échouent pas avec une erreur. | Clients Exchange Online avec déploiements hybrides (locaux) | Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
|||||

### <a name="dynamics-phase-8-of-9"></a>Dynamics (phase 8 sur 9)

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Ressources Microsoft Dynamics | Les clients avec Microsoft Dynamics seront engagés par Engineering ou FastTrack pour la transition de Dynamics vers l’instance des services Office 365.* | Clients Microsoft Dynamics 365 | - Après la migration, l’administrateur valide l’organisation. <br><br> - L’administrateur modifie les flux de travail, si nécessaire. <br><br> - L’administrateur désessonne le mode AdminOnly selon le cas. <br><br> - L’administrateur modifie le type d’organisation à partir _du bac_ à sable , selon le cas <br><br> - Informer les utilisateurs finaux de la nouvelle URL pour accéder à l’instance (org). <br><br> - Mettez à jour les connexions entrantes vers la nouvelle URL de point de terminaison. <br><br> - Le service Dynamics n’est pas disponible pour les utilisateurs pendant la transition. <br><br> - Les utilisateurs doivent valider l’état et les fonctionnalités de l’organisation après la migration de chaque organisation.  |
|||||

\* (i) Les clients avec Microsoft Dynamics 365 doivent prendre des mesures dans ce scénario de migration, comme défini par le processus de migration fourni. (ii) Si le client ne parvient pas à prendre des mesures, Microsoft ne pourra pas terminer la migration. (iii) Lorsque Microsoft ne parvient pas à terminer la migration en raison de l’inaction du client, l’abonnement du client expirera le 29 octobre 2021. 


### <a name="power-bi-phase-8-of-9"></a>Power BI (phase 8 sur 9)

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration des ressources Power BI | Les clients avec Microsoft Power BI seront impliqués par Engineering ou FastTrack après avoir déclenché manuellement un outil de migration PBI existant pour la transition de Power BI vers l’instance des services Office 365.\*\* | Clients Microsoft Power BI | - Les éléments Power BI suivants _ne_ seront pas transitionn et devront être re-créés : <br><br> - Jeux de données en temps réel (par exemple, jeux de données push ou de diffusion en continu). <br> - Configuration et source de données de la passerelle de données power BI sur site. <br> - Les rapports créés en plus des jeux de données en temps réel ne seront pas disponibles après la migration et doivent être recréés. <br><br> - Les services Power BI ne seront pas disponibles pour les utilisateurs pendant la transition. L’indisponibilité du service ne doit pas être plus de 24 heures. <br><br> - Les utilisateurs doivent reconfigurer les sources de données et leurs passerelles de données locales avec le service Power BI après la migration.  Tant qu’ils ne le font pas, les utilisateurs ne pourront pas utiliser ces sources de données pour effectuer une actualisation programmée et/ou des requêtes directes sur ces sources de données. <br><br> - Les capacités et les espaces de travail premium ne peuvent pas être migrés. Les clients doivent supprimer toutes les capacités avant la migration et les re-créer après la migration. Déplacez les espaces de travail vers les capacités souhaitées.  |
|||||

\*\* (i) Les clients avec Microsoft Power BI doivent prendre des mesures dans ce scénario de migration, comme défini par le processus de migration fourni. (ii) Si le client ne parvient pas à prendre des mesures, Microsoft ne pourra pas terminer la migration. (iii) Lorsque Microsoft ne parvient pas à terminer la migration en raison de l’inaction du client, l’abonnement du client expirera le 29 octobre 2021. 


### <a name="office-apps-phase-9-of-9"></a>Applications Office (phase 9 sur 9)

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Clients, Office Online pendant le cutover client Office, Azure AD finalise l’étendue du client pour pointer vers les services Office 365. | Cette modification de configuration permet aux clients Office de mettre à jour et de pointer vers les points de terminaison des services Office 365. | Tous les clients Office | - Avertir les utilisateurs de fermer toutes les applications _Office,_ puis de se ré-inscrire (ou de forcer les clients à redémarrer et les utilisateurs à se connecter) pour permettre aux clients Office de récupérer la modification. <br><br> - Informez les utilisateurs  et le personnel du service d’aide que les utilisateurs peuvent voir une bannière Office qui les invite à réactiver les applications Office dans les 72 heures qui s’ernt après le passage à la ligne. <br><br> - Toutes les applications Office sur des ordinateurs personnels doivent être fermées, et les utilisateurs doivent se fermer, puis se connectent à nouveau. Dans la barre d’activation jaune, connectez-vous pour vous réactiver aux services Office 365. <br><br> - Les ordinateurs partagés nécessitent des actions similaires à des ordinateurs personnels et ne nécessitent pas de procédure spéciale. <br><br> - Sur les appareils mobiles, les utilisateurs doivent se fermer des applications, les fermer, puis se connecter à nouveau. |
|||||

## <a name="during-migration"></a>Pendant la migration

### <a name="sharepoint-online-phase-4-of-9"></a>SharePoint Online (Phase 4 sur 9)

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| SharePoint et OneDrive sont en transition. | SharePoint et OneDrive sont migrés de Microsoft Cloud Deutschland vers les services Office 365 au cours de cette phase. Les URL Microsoft Cloud Deutschland existantes sont conservées ( `contoso.sharepoint.de` ). Les jetons émis par les services Microsoft Cloud Deutschland ou Office 365 sont valides pendant la transition. | Clients SharePoint | Les flux de travail SharePoint 2013 inflight sont rompus lors de la migration et doivent être republiés après la migration. |
|||||


### <a name="exchange-online-phase-5-of-9"></a>Exchange Online (phase 5 sur 9)

Pour eDiscovery :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Pendant la migration, les recherches de découverte électronique échouent ou retournent 0 résultat pour les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online qui ont été migrés. | Pendant la migration, les clients peuvent continuer à créer des cas, des obligations, des recherches et des exportations dans le Centre de sécurité [&](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)conformité, y compris la recherche [de contenu.](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)  Toutefois, les recherches sur les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online qui ont été migrés retournent 0 résultat ou produisent une erreur. Pour la correction, consultez la _colonne Impact._ | Tous les clients utilisant eDiscovery |  Dans le cas où une recherche renvoie 0 résultat ou une erreur lors de la migration, veuillez effectuer l’action suivante pour SharePoint Online : <br><br>  Téléchargez les sites directement à partir du site SharePoint Online/OneDrive Entreprise en suivant les instructions dans Télécharger des fichiers et des dossiers à partir de [OneDrive ou SharePoint.](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05) Cette méthode nécessite des autorisations d’administrateur SharePoint Online ou des autorisations en lecture seule sur le site. <br><br> Si les limites sont dépassées, comme expliqué dans télécharger des fichiers et des dossiers à partir de OneDrive ou [SharePoint,](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05)les clients peuvent utiliser le client de synchronisation OneDrive Entreprise en suivant les instructions de synchronisation des fichiers [SharePoint](https://support.office.com/article/sync-sharepoint-files-with-the-new-onedrive-sync-app-6de9ede8-5b6e-4503-80b2-6190f3354a88)et Teams avec votre ordinateur. <br><br> - Exchange Online <br><br> - [Découverte électronique sur place dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/ediscovery/ediscovery) |
|||||


### <a name="skype-for-business-online-phase-7-of-9"></a>Skype Entreprise Online (phase 7 sur 9)

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration de Skype Entreprise vers Teams. | Les clients Skype Entreprise existants sont migrés vers les services Office 365 en Europe, puis migrés vers Microsoft Teams dans la région Allemagne des services Office 365. | Clients Skype Entreprise |  PowerShell vous permet d’administrer les paramètres et les stratégies de votre client et de vos utilisateurs. Lorsque vous vous connectez à une session PowerShell, ajoutez les valeurs suivantes : <br><br> `-OverridePowershellUri "https://admin4E.online.lync.com/OcsPowershellOAuth"` |
|||||


## <a name="post-migration"></a>Après la migration

### <a name="azure-ad-phase-9-of-9"></a>Azure AD (phase 9 sur 9)

Pour les hybrides :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Mettez à jour Azure AD Connect. | Une fois la connexion à Azure AD terminée, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit s’assurer que le processus de synchronisation delta a été finalisé et, après cela, modifier la valeur de chaîne de 3 (Microsoft Cloud Deutschland) à 0 dans le chemin d’accès du Registre `AzureInstance` `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Azure AD Connect` . | Organisations hybrides connectées à Azure AD | Modifiez la valeur `AzureInstance` de , la clé de Registre. Si vous ne le faites pas, les objets ne seront plus synchronisés une fois que les points de terminaison Microsoft Cloud Deutschland ne seront plus disponibles. |
|||||

Pour l’authentification fédérée :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Supprimez les confiances de partie de confiance de Microsoft Cloud Deutschland AD FS. | Une fois la connexion à Azure AD terminée, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit supprimer l’confiance de la partie de confiance vers les points de terminaison Microsoft Cloud Deutschland. Cette action ne peut être effectuée que lorsqu’aucune application du client ne pointe vers les points de terminaison Microsoft Cloud Deutschland lorsque Azure AD est mis à profit en tant que fournisseur d’identité (IdP). | Organisations d’authentification fédérée | Aucun. |
|||||

Pour Azure AD :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Les demandes de joindre un groupe Azure AD au cours des 30 derniers jours avant la migration doivent être demandées à nouveau si la demande d’origine n’a pas été approuvée. | Les clients des utilisateurs finals devront utiliser le panneau d’accès pour envoyer une demande de rejoindre à nouveau un groupe Azure AD si ces demandes n’ont pas été approuvées au cours des 30 derniers jours avant la migration. | Utilisateurs finaux dont les demandes d’approbation de groupe Azure AD n’ont pas été approuvées au cours des 30 derniers jours avant la migration |  En tant qu’utilisateur final : <ol><li>Accédez au [panneau d’accès.](https://account.activedirectory.windowsazure.com/r#/joinGroups)</li><li>Recherchez un groupe Azure AD pour lequel l’approbation de l’appartenance était en attente dans les 30 jours avant la migration.</li><li>Demande de rejoindre à nouveau le groupe Azure AD.</li></ol> Les demandes de participation à un groupe qui sont actives moins de 30 jours avant la migration ne peuvent pas être approuvées, sauf si elles sont demandées à nouveau après la migration. |
|||||

Pour DNS :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Mettre à jour les services DNS locaux pour les points de terminaison des services Office 365. | Les entrées DNS gérées par le client qui pointent vers Office 365 Germany doivent être mises à jour pour pointer vers les points de terminaison des services Office 365. | Tous les clients Office | Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
|||||

Pour les services tiers pour les points de terminaison des services Office 365 :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Mettez à jour les partenaires et les services tiers pour les points de terminaison des services Office 365. | - Les services et partenaires tiers qui pointent vers Office 365 Germany doivent être mis à jour pour pointer vers les points de terminaison des services Office 365. Exemple : ré-inscrire, en alignement avec vos fournisseurs et partenaires, la version d’application de la galerie d’applications, si disponible. <br><br> - Pointez toutes les applications personnalisées qui tirent parti de l’API Graph `graph.microsoft.de` vers `graph.microsoft.com` . Les autres API avec des points de terminaison modifiés doivent également être mises à jour, si elles sont mises à profit. <br><br> - Modifier toutes les applications d’entreprise tierces pour les rediriger vers les points de terminaison internationaux.  | Tous les clients Office | Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
|||||

### <a name="sharepoint-online-phase-4-of-9"></a>SharePoint Online (Phase 4 sur 9)

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Republier les flux de travail SharePoint 2013. | Dans le travail préalable à la migration, nous avons réduit le nombre de flux de travail SharePoint 2013. Une fois la migration terminée, le client peut republier les flux de travail. | Tous les clients Office | Il s’agit d’une action obligatoire. Si vous ne le faites pas, les utilisateurs risquent de semer la confusion et d’appeler le service d’aide. |
| Partager des éléments via Outlook | Le partage d’éléments via Outlook ne fonctionne plus après le passage à un client. | Sharepoint Online et OneDrive Entreprise | - Dans SharePoint Online et OneDrive Entreprise, vous pouvez partager des éléments via Outlook. Après avoir enfoncé le bouton Outlook, un lien partageable est créé et envoyé dans un nouveau message dans Outlook Web App. <br><br> - Après le passage à la location, cette méthode de partage ne fonctionne pas. Nous savons qu’il s’agit d’un problème connu. Toutefois, étant donné que cette fonctionnalité Outlook est dans le chemin de l’annulation, la résolution du problème n’est pas planifiée tant que l’annulation n’est pas déployée. |


### <a name="exchange-online-phase-5-of-9"></a>Exchange Online (phase 5 sur 9)

Si vous utilisez une configuration Exchange hybride :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Réexécutez l’Assistant Configuration hybride (HCW) sur les services Office 365. | La configuration HCW existante est destinée à prendre en charge Microsoft Cloud Deutschland. Une fois la migration des services Exchange terminée, nous dissocions la configuration sur site de Microsoft Cloud Deutschland. | Clients Exchange Online qui exécutent un déploiement hybride | - Action obligatoire. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. Avant le début de la migration des boîtes aux lettres Exchange (avec au moins 5 jours d’avis), informez les clients qu’ils doivent arrêter et supprimer les déplacements d’intégration ou de suppression de leurs boîtes aux lettres.  S’ils ne le font pas, ils voient des erreurs dans leurs demandes de déplacement. <br><br> - Une fois la migration des boîtes aux lettres Exchange terminée, informez les clients qu’ils peuvent reprendre les déplacements d’intégration et de hors-intégration. <br> L’exécution **de Test-MigrationServerAvailabiilty**, une cmdlet PowerShell, pendant la migration d’Exchange de Microsoft Cloud Deutschland vers les services Office 365 peut ne pas fonctionner. Toutefois, elle fonctionne correctement une fois la migration terminée. <br><br> Si des clients ont des problèmes avec les informations d’identification ou l’autorisation après la migration des boîtes aux lettres, les utilisateurs peuvent entrer à nouveau leurs informations d’identification d’administrateur local dans le point de terminaison de migration en exécutant ou en le déliérant à l’aide du Panneau de configuration `Set-MigrationEndpoint endpointName -Credential $(Get-Credential)` Exchange (ECP).  |

Pour eDiscovery :

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
|  Tous les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online ont été migrés avec le Centre de sécurité et conformité (SCC). | Toute l’activité eDiscovery doit être exécuté à partir du client international. Les recherches seront désormais réussies à 100 %.  Les défaillances ou erreurs doivent suivre les canaux de support normaux. | Tous les clients qui utilisent eDiscovery | Aucun. |
| Supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées pendant les étapes préalables à la migration | Les clients peuvent supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées pendant le travail préalable à la migration des clients. | Tous les clients qui ont appliqué une stratégie de rétention dans le cadre des étapes préalables à la migration. | Aucun. |
|||||



## <a name="next-step"></a>Étape suivante

[Comprendre les actions et les impacts des phases de migration](ms-cloud-germany-transition-phases.md)

## <a name="more-information"></a>Informations supplémentaires

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
