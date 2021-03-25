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
ms.openlocfilehash: ecc549ca4d0bb8122de3bf092c004c919e958d5e
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165644"
---
# <a name="migration-phases-actions-and-impacts-for-the-migration-from-microsoft-cloud-deutschland-advanced"></a>Actions et impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland (avancé)

Les migrations de clients de Microsoft Cloud Deutschland vers la région Allemagne des services Office 365 de Microsoft sont exécutées en tant qu’ensemble de phases et leurs actions configurées pour chaque charge de travail. Cette figure montre les neuf phases de migration vers les nouveaux centres de données allemands.

![Les neuf phases de migration vers les nouveaux centres de données allemands](../media/ms-cloud-germany-migration-opt-in/migration-organization.png)

Les sections suivantes fournissent des informations supplémentaires sur les expériences client lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemande.

## <a name="office-365-portal-services-between-phase-2-and-phase-3"></a>Services portail Office 365 entre les phases 2 et 3

Entre les phases 2 et 3, le Portail partenaires n’est peut-être pas accessible. Pendant ce temps, il se peut que le partenaire ne puisse pas accéder aux informations du client sur le portail partenaire. Étant donné que chaque migration est différente, la durée de l’accessibilité peut être en heures.

### <a name="ediscovery-phase-4-to-the-end-of-phase-9"></a>eDiscovery phase 4 à la fin de la phase 9

**S’applique à :** Tous les clients utilisant eDiscovery

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Depuis le début de la phase 4 jusqu’à la fin de la phase 9, les recherches de découverte électronique échouent ou retournent 0 résultat pour les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online qui ont été migrés. | Pendant la migration, les clients peuvent continuer à créer des cas, des obligations, des recherches et des exportations dans le Centre de sécurité [&](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)conformité, y compris la recherche [de contenu.](https://docs.microsoft.com/microsoft-365/compliance/search-for-content) Toutefois, les recherches sur les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online qui ont été migrés retournent 0 résultat ou produisent une erreur. Pour la correction, consultez la _colonne Impact._ | Dans le cas où une recherche renvoie zéro résultat ou une erreur lors de la migration, veuillez effectuer l’action suivante pour SharePoint Online : <ul><li>Téléchargez les sites directement à partir du site SharePoint Online ou OneDrive Entreprise en suivant les instructions dans Télécharger des fichiers et des dossiers à partir de [OneDrive ou SharePoint.](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05) Cette méthode nécessite des autorisations d’administrateur SharePoint Online ou des autorisations en lecture seule sur le site.</li><li>Si les limites sont dépassées, comme expliqué dans télécharger des fichiers et des dossiers à partir de OneDrive ou [SharePoint,](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05)les clients peuvent utiliser le client de synchronisation OneDrive Entreprise en suivant les instructions de synchronisation des fichiers [SharePoint](https://support.office.com/article/sync-sharepoint-files-with-the-new-onedrive-sync-app-6de9ede8-5b6e-4503-80b2-6190f3354a88)et Teams avec votre ordinateur.</li><li>Pour plus d’informations, voir Découverte électronique sur  [place dans Exchange Server](https://docs.microsoft.com/Exchange/policy-and-compliance/ediscovery/ediscovery) |
||||

## <a name="exchange-online-set-userphoto-during-phase-5"></a>Exchange Online Set-UserPhoto phase 5

**S’applique à :** Tous les clients stockant des photos utilisateur dans Exchange Online et qui **utilisent Set-UserPhoto**:

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| La nouvelle région « Allemagne » est ajoutée à une configuration d’organisation Exchange Online existante et les boîtes aux lettres sont déplacées vers les services Office 365. | La configuration d’Exchange Online ajoute la nouvelle région allemande locale à l’organisation en transition. Cette région de services Office 365 est définie par défaut, ce qui permet au service d’équilibrage de charge interne de redistribuer les boîtes aux lettres vers la région par défaut appropriée dans les services Office 365. Dans cette transition, les utilisateurs des deux côtés (services d’Allemagne ou d’Office 365) sont dans la même organisation et peuvent utiliser l’un ou l’autre point de terminaison d’URL. | Si une boîte aux lettres d’utilisateur a été miggrée, mais qu’une boîte aux lettres d’administrateur n’a pas été migrée, ou inversement, les administrateurs ne pourront pas exécuter **Set-UserPhoto**, une cmdlet PowerShell. Dans ce cas, un administrateur doit transmettre une chaîne supplémentaire au cours de la connexion définie à l’aide `ConnectionUri` de la syntaxe suivante : <br> `https://outlook.office.de/PowerShell-LiveID?email=<user_email>` <br> où est l’espace réservé pour l’ID de messagerie de l’utilisateur dont la photo doit être modifiée à l’aide `<user_email>` **de Set-UserPhoto**. |
||||

## <a name="post-migration"></a>Après la migration

### <a name="azure-ad-phase-9"></a>Phase 9 d’Azure AD

**S’applique à :** Tous les clients synchronisant les identités avec Azure AD Connect

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Mettez à jour Azure AD Connect. | Une fois la connexion à Azure AD terminée, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit s’assurer que le processus de synchronisation delta a été finalisé et, après cela, modifier la valeur de chaîne de 3 (Microsoft Cloud Deutschland) à 0 dans le chemin d’accès du Registre `AzureInstance` `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Azure AD Connect` . | Modifiez la valeur `AzureInstance` de , la clé de Registre. Si vous ne le faites pas, les objets ne seront plus synchronisés une fois que les points de terminaison Microsoft Cloud Deutschland ne seront plus disponibles. |
|||||

**S’applique à :** Tous les clients utilisant l’authentification fédérée avec ADFS

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Supprimez les confiances de partie de confiance de Microsoft Cloud Deutschland AD FS. | Une fois le cut-over vers Azure AD terminé, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit supprimer l’confiance de la partie de confiance vers les points de terminaison Microsoft Cloud Deutschland. Cette action ne peut être effectuée que lorsqu’aucune des applications du client ne pointe vers les points de terminaison Microsoft Cloud Deutschland lorsque Azure AD est mis à profit en tant que fournisseur d’identité (IdP). | Organisations d’authentification fédérée | Aucun. |
||||

<!--
    Question from ckinder
    The following paragraph is not clear
-->
**S’applique à :** Utilisateurs finaux dont les demandes d’approbation de groupe Azure AD n’ont pas été approuvées au cours des 30 derniers jours avant la migration 

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Les demandes de joindre un groupe Azure AD au cours des 30 derniers jours avant la migration doivent être demandées à nouveau si la demande d’origine n’a pas été approuvée. | Les clients d’utilisateur final devront utiliser le panneau d’accès pour soumettre une demande de rejoindre à nouveau un groupe Azure AD si ces demandes n’ont pas été approuvées au cours des 30 derniers jours avant la migration. |  En tant qu’utilisateur final : <ol><li>Accédez au [panneau d’accès.](https://account.activedirectory.windowsazure.com/r#/joinGroups)</li><li>Recherchez un groupe Azure AD pour lequel l’approbation de l’appartenance était en attente pendant les 30 jours avant la migration.</li><li>Demandez à rejoindre à nouveau le groupe Azure AD.</li></ol> Les demandes de participation à un groupe actif moins de 30 jours avant la migration ne peuvent pas être approuvées, sauf si elles sont demandées à nouveau après la migration. |
||||

<!--
    Question from ckinder
    The following paragraph is not clear
-->
**S’applique à :**  Tous les clients gérant leurs propres zones DNS

| Étapes | Description | Impact |
|:------|:-------|:-------|
| Mettre à jour les services DNS locaux pour les points de terminaison des services Office 365. | Les entrées DNS gérées par le client qui pointent vers Microsoft Cloud Deutschland doivent être mises à jour pour pointer vers les points de terminaison des services globaux Office 365. | Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||

**S’applique à :** Clients utilisant des services tiers pour les points de terminaison des services Office 365

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Mettez à jour les partenaires et les services tiers pour les points de terminaison des services Office 365. | <ul><li>Les services et partenaires tiers qui pointent vers Office 365 Germany doivent être mis à jour pour pointer vers les points de terminaison des services Office 365. Exemple : ré-inscrire, en alignement avec vos fournisseurs et partenaires, la version d’application de la galerie d’applications, si disponible. </li><li>Pointez toutes les applications personnalisées qui tirent parti de l’API Graph `graph.microsoft.de` vers `graph.microsoft.com` . Les autres API avec des points de terminaison modifiés doivent également être mises à jour, si elles sont mises à profit. </li><li>Modifiez toutes les applications d’entreprise tierces pour les rediriger vers les points de terminaison internationaux. </li></ul>| Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||

### <a name="sharepoint-online-post-migration"></a>SharePoint Online après la migration

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Republier les flux de travail SharePoint 2013. | Dans le travail préalable à la migration, nous avons réduit le nombre de flux de travail SharePoint 2013. Une fois la migration terminée, le client peut republier les flux de travail. | Il s’agit d’une action obligatoire. Si vous ne le faites pas, les utilisateurs risquent de semer la confusion et d’appeler le service d’aide. |
| Partager des éléments via Outlook | Le partage d’éléments dans SharePoint Online et OneDrive Entreprise via Outlook ne fonctionne plus après le passage à un client. |<ul><li>Dans SharePoint Online et OneDrive Entreprise, vous pouvez partager des éléments via Outlook. Après avoir enfoncé le bouton Outlook, un lien partageable est créé et envoyé dans un nouveau message dans Outlook Web App.</li><li>Après le passage à la location, cette méthode de partage ne fonctionne pas. Nous savons qu’il s’agit d’un problème connu. Toutefois, étant donné que cette fonctionnalité Outlook est dans le chemin de l’annulation, la résolution du problème n’est pas planifiée tant que l’annulation n’est pas déployée. </li></ul>|
||||

### <a name="exchange-online-post-migration"></a>Exchange Online après la migration

Si vous utilisez une configuration Exchange hybride :

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Réexécutez l’Assistant Configuration hybride (HCW) sur les services Office 365. | La configuration HCW existante est destinée à prendre en charge Microsoft Cloud Deutschland. Une fois la migration des services Exchange terminée, nous dissocions la configuration sur site de Microsoft Cloud Deutschland. |<ul><li>Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. Avant le début de la migration des boîtes aux lettres Exchange (avec au moins 5 jours d’avis), informez les clients qu’ils doivent arrêter et supprimer les déplacements d’intégration ou de suppression de leurs boîtes aux lettres.  S’ils ne le font pas, ils voient des erreurs dans leurs demandes de déplacement. </li><li>Une fois la migration des boîtes aux lettres Exchange terminée, informez les clients qu’ils peuvent reprendre les déplacements d’intégration et de hors-intégration. <br> L’exécution **de Test-MigrationServerAvailabiilty**, une cmdlet PowerShell, pendant la migration d’Exchange de Microsoft Cloud Deutschland vers les services Office 365 peut ne pas fonctionner. Toutefois, elle fonctionne correctement une fois la migration terminée. </li><li>Si des clients ont des problèmes avec les informations d’identification ou l’autorisation après la migration des boîtes aux lettres, les utilisateurs peuvent entrer à nouveau leurs informations d’identification d’administrateur local dans le point de terminaison de migration en exécutant ou en le déliérant à l’aide du Panneau de configuration `Set-MigrationEndpoint endpointName -Credential $(Get-Credential)` Exchange (ECP). </li></ul>|

### <a name="ediscovery-post-migration"></a>eDiscovery après la migration

**S’applique à :** Tous les clients qui utilisent eDiscovery

| Étapes | Description | Impact |
|:-------|:-------|:-------|
|  Tous les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online ont été migrés avec le Centre de sécurité et conformité (SCC). | Toute l’activité eDiscovery doit être exécuté à partir du client international. Les recherches seront désormais réussies à 100 %.  Les défaillances ou erreurs doivent suivre les canaux de support normaux. | Aucune |
||||

**S’applique à :**  Tous les clients qui ont appliqué une stratégie de rétention dans le cadre des étapes préalables à la migration

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées pendant les étapes préalables à la migration | Les clients peuvent supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées pendant le travail préalable à la migration des clients. | Aucune |
||||

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

- [Informations sur le programme de migration Dynamics 365](/dynamics365/get-started/migrate-data-german-region)
- [Informations sur le programme de migration Power BI](/power-bi/admin/service-admin-migrate-data-germany)
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)