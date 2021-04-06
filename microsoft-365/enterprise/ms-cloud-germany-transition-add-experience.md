---
title: Activités post-migration pour la migration à partir de Microsoft Cloud Deutschland
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
description: 'Résumé : Activités post-migration après le passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemande.'
ms.openlocfilehash: 745589c1c997540094fc4a770e437de89015f88a
ms.sourcegitcommit: e0a96e08b7dc29e074065e69a2a86fc3cf0dad01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51591755"
---
# <a name="post-migration-activities-for-the-migration-from-microsoft-cloud-deutschland"></a>Activités post-migration pour la migration à partir de Microsoft Cloud Deutschland

Les sections suivantes fournissent des activités post-migration pour plusieurs services après le passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemands.

## <a name="azure-ad"></a>Azure AD

### <a name="azure-ad-connect"></a>Azure AD Connect
**S’applique à :** Tous les clients synchronisant les identités avec Azure AD Connect

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Mettez à jour Azure AD Connect. | Une fois la connexion à Azure AD terminée, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit s’assurer que le processus de synchronisation delta a été finalisé et, après cela, modifier la valeur de chaîne de 3 (Microsoft Cloud Deutschland) à 0 dans le chemin d’accès du Registre `AzureInstance` `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Azure AD Connect` . | Modifiez la valeur `AzureInstance` de , la clé de Registre. Si vous ne le faites pas, les objets ne seront plus synchronisés une fois que les points de terminaison Microsoft Cloud Deutschland ne seront plus disponibles. |
|||||

### <a name="azure-ad-federated-authentication-with-ad-fs"></a>Authentification fédérée Azure AD avec AD FS
**S’applique à :** Tous les clients utilisant l’authentification fédérée avec AD FS

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Supprimez les confiances de partie de confiance de Microsoft Cloud Deutschland AD FS. | Une fois le cut-over vers Azure AD terminé, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit supprimer l’confiance de la partie de confiance vers les points de terminaison Microsoft Cloud Deutschland. Cette action ne peut être effectuée que lorsqu’aucune des applications du client ne pointe vers les points de terminaison Microsoft Cloud Deutschland lorsque Azure AD est mis à profit en tant que fournisseur d’identité (IdP). | Organisations d’authentification fédérée | Aucun. |
||||

<!--
    Question from ckinder
    The following paragraph is not clear
-->
### <a name="group-approvals"></a>Approbations de groupe
**S’applique à :** Utilisateurs finaux dont les demandes d’approbation de groupe Azure AD n’ont pas été approuvées au cours des 30 derniers jours avant la migration 

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Les demandes de joindre un groupe Azure AD au cours des 30 derniers jours avant la migration doivent être demandées à nouveau si la demande d’origine n’a pas été approuvée. | Les clients d’utilisateur final devront utiliser le panneau d’accès pour soumettre une demande de rejoindre à nouveau un groupe Azure AD si ces demandes n’ont pas été approuvées au cours des 30 derniers jours avant la migration. |  En tant qu’utilisateur final : <ol><li>Accédez au [panneau d’accès.](https://account.activedirectory.windowsazure.com/r#/joinGroups)</li><li>Recherchez un groupe Azure AD pour lequel l’approbation de l’appartenance était en attente pendant les 30 jours avant la migration.</li><li>Demandez à rejoindre à nouveau le groupe Azure AD.</li></ol> Les demandes de participation à un groupe actif moins de 30 jours avant la migration ne peuvent pas être approuvées, sauf si elles sont demandées à nouveau après la migration. |
||||

<!--
    Question from ckinder
    The following paragraph is not clear
-->
## <a name="custom-dns-updates"></a>Mises à jour DNS personnalisées
**S’applique à :**  Tous les clients gérant leurs propres zones DNS

| Étapes | Description | Impact |
|:------|:-------|:-------|
| Mettez à jour les services DNS locaux pour les points de terminaison des services Office 365. | Les entrées DNS gérées par le client qui pointent vers Microsoft Cloud Deutschland doivent être mises à jour pour pointer vers les points de terminaison des services globaux Office 365. | Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||

## <a name="third-party-services"></a>Services tiers
**S’applique à :** Clients utilisant des services tiers pour les points de terminaison des services Office 365

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Mettez à jour les partenaires et les services tiers pour les points de terminaison des services Office 365. | <ul><li>Les services et partenaires tiers qui pointent vers Office 365 Germany doivent être mis à jour pour pointer vers les points de terminaison des services Office 365. Exemple : ré-inscrire, en alignement avec vos fournisseurs et partenaires, la version d’application de la galerie d’applications, si disponible. </li><li>Pointez toutes les applications personnalisées qui tirent parti de l’API Graph `graph.microsoft.de` vers `graph.microsoft.com` . Les autres API avec des points de terminaison modifiés doivent également être mises à jour, si elles sont mises à profit. </li><li>Modifiez toutes les applications d’entreprise tierces pour les rediriger vers les points de terminaison internationaux. </li></ul>| Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||

## <a name="sharepoint-online"></a>SharePoint Online
**S’applique** à : Clients utilisant des flux de travail SharePoint 2013

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Republier les flux de travail SharePoint 2013. | Dans le travail préalable à la migration, nous avons réduit le nombre de flux de travail SharePoint 2013. Une fois la migration terminée, le client peut republier les flux de travail. | Il s’agit d’une action obligatoire. Si vous ne le faites pas, les utilisateurs risquent de semer la confusion et d’appeler le service d’aide. |
| Partager des éléments via Outlook | Le partage d’éléments dans SharePoint Online et OneDrive Entreprise via Outlook ne fonctionne plus après le passage à un client. |<ul><li>Dans SharePoint Online et OneDrive Entreprise, vous pouvez partager des éléments via Outlook. Après avoir enfoncé le bouton Outlook, un lien partageable est créé et envoyé dans un nouveau message dans Outlook Web App.</li><li>Après le passage à la location, cette méthode de partage ne fonctionne pas. Nous savons qu’il s’agit d’un problème connu. Toutefois, étant donné que cette fonctionnalité Outlook est dans le chemin de l’annulation, la résolution du problème n’est pas planifiée tant que l’annulation n’est pas déployée. </li></ul>|
||||

## <a name="exchange-online"></a>Exchange Online
**S’applique à**: Clients utilisant une configuration Exchange hybride

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Réexécutez l’Assistant Configuration hybride (HCW) sur les services Office 365. | La configuration HCW existante est destinée à prendre en charge Microsoft Cloud Deutschland. Une fois la migration des services Exchange terminée, nous dissocions la configuration sur site de Microsoft Cloud Deutschland. |<ul><li>Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. Avant le début de la migration des boîtes aux lettres Exchange (avec au moins 5 jours d’avis), informez les clients qu’ils doivent arrêter et supprimer les déplacements d’intégration ou de suppression de leurs boîtes aux lettres.  S’ils ne le font pas, ils voient des erreurs dans leurs demandes de déplacement. </li><li>Une fois la migration des boîtes aux lettres Exchange terminée, informez les clients qu’ils peuvent reprendre les déplacements d’intégration et de hors-intégration. <br> L’exécution **de Test-MigrationServerAvailabiilty**, une cmdlet PowerShell, pendant la migration d’Exchange de Microsoft Cloud Deutschland vers les services Office 365 risque de ne pas fonctionner. Toutefois, elle fonctionne correctement une fois la migration terminée. </li><li>Si des clients ont des problèmes avec les informations d’identification ou l’autorisation après la migration des boîtes aux lettres, les utilisateurs peuvent entrer à nouveau leurs informations d’identification d’administrateur local dans le point de terminaison de migration en exécutant ou en le déliérant à l’aide du Panneau de configuration `Set-MigrationEndpoint endpointName -Credential $(Get-Credential)` Exchange (ECP). </li></ul>|
