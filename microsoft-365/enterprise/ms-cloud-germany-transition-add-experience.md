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
description: 'Résumé : Activités post-migration après le passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers Office 365 services dans la nouvelle région de centres de données allemands.'
ms.openlocfilehash: ad696e1012d7b540017db29be7638d50ea2dbc5133411da7ba5e0d0145ada1e8
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53899042"
---
# <a name="post-migration-activities-for-the-migration-from-microsoft-cloud-deutschland"></a>Activités post-migration pour la migration à partir de Microsoft Cloud Deutschland

Les sections suivantes fournissent des activités post-migration pour plusieurs services après le passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers Office 365 services dans la nouvelle région de centres de données allemands.

## <a name="azure-ad"></a>Azure AD
<!-- This AAD Endpoints comparison table could be added to the documentation, not finally decided.
### Azure AD Endpoints
**Applies to:** All customers

After the cut over to Azure AD is complete, the organization is fully using Office 365 services and is no longer connected to Microsoft Cloud Deutschland and the endpoints cannot be used anymore. At this point, the customer needs to ensure that all applications are using the endpoints for the new German datacenter region.
The following table provides an overview about which endpoints will replace the previously used endpoints in Microsoft Cloud Germany (Microsoft Cloud Deutschland). 

|Endpoint in Microsoft Cloud Germany  |Endpoint in the new German datacenter region  |
|:---------|:---------|
|becws.microsoftonline.de<br>provisioningapi.microsoftonline.de |becws.microsoftonline.com<br>provisioningapi.microsoftonline.com |
|adminwebservice.microsoftonline.de |adminwebservice.microsoftonline.com |
|login.microsoftonline.de<br>logincert.microsoftonline.de<br>sts.microsoftonline.de |login.microsoftonline.com<br>login.windows.net<br>logincert.microsoftonline.com<br>accounts.accesscontrol.windows.net |
|enterpriseregistration.microsoftonline.de |enterpriseregistration.windows.net |
|graph.cloudapi.de |graph.windows.net |
|graph.microsoft.de |graph.microsoft.com |
|||
-->

### <a name="azure-ad-federated-authentication-with-ad-fs"></a>Authentification fédérée Azure AD avec AD FS
**S’applique à :** Tous les clients utilisant l’authentification fédérée avec AD FS

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Supprimez les confiances de partie de confiance de Microsoft Cloud Deutschland AD FS. | Une fois le cut-over vers Azure AD terminé, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit supprimer l’confiance de la partie de confiance vers les points de terminaison Microsoft Cloud Deutschland. Cette action ne peut être effectuée que lorsqu’aucune des applications du client ne pointe vers les points de terminaison Microsoft Cloud Deutschland lorsque Azure AD est mis à profit en tant que fournisseur d’identité (IdP). | Organisations d’authentification fédérée | 
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

## <a name="custom-dns-updates"></a>Mises à jour DNS personnalisées
**S’applique à :**  Tous les clients gérant leurs propres zones DNS

| Étapes | Description | Impact |
|:------|:-------|:-------|
| Mettez à jour les services DNS locaux pour les points Office 365 services locaux. | Les entrées DNS gérées par le client qui pointent vers Microsoft Cloud Deutschland doivent être mises à jour pour pointer vers les points de terminaison Office 365 services globaux. Reportez-vous [aux domaines dans le Centre d’administration Microsoft 365](https://admin.microsoft.com/Adminportal/Home#/Domains) et appliquez les modifications apportées à votre configuration DNS. | Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||

## <a name="third-party-services"></a>Services tiers
**S’applique à :** Clients utilisant des services tiers pour les points de terminaison Office 365 services

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Mettez à jour les partenaires et les services tiers pour les points Office 365 services. | <ul><li>Les services tiers et les partenaires qui pointent vers Office 365 Germany doivent être mis à jour pour pointer vers les points de terminaison Office 365 services de sécurité. Exemple : ré-inscrire, en alignement avec vos fournisseurs et partenaires, la version d’application de la galerie d’applications, si disponible. </li><li>Pointez toutes les applications personnalisées qui utilisent Graph API à `graph.microsoft.de` partir de `graph.microsoft.com` . Les autres API avec des points de terminaison modifiés doivent également être mises à jour, si elles sont mises à profit. </li><li>Modifiez toutes les applications d’entreprise tierces pour les rediriger vers les points de terminaison internationaux. </li></ul>| Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||