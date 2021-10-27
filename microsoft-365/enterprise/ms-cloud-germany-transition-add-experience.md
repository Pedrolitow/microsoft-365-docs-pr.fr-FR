---
title: Activités post-migration pour la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/11/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
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
ms.openlocfilehash: 349b9aa756a67d823e95ec2d999a04b12863d0fb
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586204"
---
# <a name="post-migration-activities-for-the-migration-from-microsoft-cloud-deutschland"></a>Activités post-migration pour la migration à partir de Microsoft Cloud Deutschland

Les sections suivantes fournissent des activités post-migration pour plusieurs services après le déplacement de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers Office 365 services dans la nouvelle région de centres de données allemande.

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

### <a name="azure-ad-federated-authentication-with-ad-fs"></a>Azure AD l’authentification fédérée avec AD FS
**S’applique à :** Tous les clients utilisant l’authentification fédérée avec AD FS

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Supprimez les confiances de partie de confiance de Microsoft Cloud Deutschland AD FS. | Une fois le Azure AD terminé, l’organisation utilise entièrement les services Office 365 et n’est plus connectée à Microsoft Cloud Deutschland. À ce stade, le client doit supprimer l’confiance de la partie de confiance vers les points de terminaison Microsoft Cloud Deutschland. Cette action ne peut être effectuée que lorsqu’aucune des applications du client ne pointe vers les points de terminaison Microsoft Cloud Deutschland lorsque Azure AD est exploite en tant que fournisseur d’identité (IdP). | Organisations d’authentification fédérée | 
||||

<!--
    Question from ckinder
    The following paragraph is not clear
-->
### <a name="group-approvals"></a>Approbations de groupe
**S’applique à :** Les utilisateurs finaux dont Azure AD d’approbation de groupe n’ont pas été approuvés au cours des 30 derniers jours avant la migration 

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Les demandes de rejoindre un groupe Azure AD au cours des 30 derniers jours avant la migration doivent être demandées à nouveau si la demande d’origine n’a pas été approuvée. | Les clients d’utilisateur final doivent utiliser le panneau d’accès pour soumettre une demande de rejoindre un groupe Azure AD à nouveau si ces demandes n’ont pas été approuvées au cours des 30 derniers jours avant la migration. |  En tant qu’utilisateur final : <ol><li>Accédez au [panneau d’accès.](https://account.activedirectory.windowsazure.com/r#/joinGroups)</li><li>Recherchez un Azure AD pour lequel l’approbation de l’appartenance était en attente pendant les 30 jours avant la migration.</li><li>Demandez à rejoindre le groupe Azure AD nouveau.</li></ol> Les demandes de participation à un groupe actif moins de 30 jours avant la migration ne peuvent pas être approuvées, sauf si elles sont demandées à nouveau après la migration. |
||||

## <a name="custom-dns-updates"></a>Mises à jour DNS personnalisées
**S’applique à :**  Tous les clients gérant leurs propres zones DNS

| Étapes | Description | Impact |
|:------|:-------|:-------|
| Mettez à jour les services DNS locaux pour les points Office 365 services locaux. | Les entrées DNS gérées par le client qui pointent vers Microsoft Cloud Deutschland doivent être mises à jour pour pointer vers les points de terminaison Office 365 services globaux. Reportez-vous [aux domaines dans le Centre d'administration Microsoft 365](https://admin.microsoft.com/Adminportal/Home#/Domains) et appliquez les modifications dans votre configuration DNS. | Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||
   > [!NOTE]
   > Le Centre d'administration Microsoft 365 demande aux clients en transition de mettre en service les enregistrements MX (Mail Exchange) pour les nouveaux domaines sous la zone outlook.de de messagerie. Exemple : consoto-com.mail.protection.outlook.de. Pour les nouveaux domaines, la valeur attendue/correcte pointant vers votre enregistrement MX personnalisé se trouve sous outlook.com zone. Dans le même exemple, l’entrée correcte est consoto-com.mail.protection.outlook.com. Un correctif est en cours pour corriger ce comportement pour les domaines des organisations en transition.
   
## <a name="third-party-services"></a>Services tiers
**S’applique à :** Clients utilisant des services tiers pour les points de terminaison Office 365 services

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Mettez à jour les partenaires et les services tiers pour les points Office 365 services. | <ul><li>Les services tiers et les partenaires qui pointent vers Office 365 Germany doivent être mis à jour pour pointer vers les points de terminaison Office 365 services. Exemple : ré-inscrire, en alignement avec vos fournisseurs et partenaires, la version d’application de la galerie d’applications, si disponible. </li><li>Pointez toutes les applications personnalisées qui utilisent Graph API `graph.microsoft.de` à partir de `graph.microsoft.com` . Les autres API avec des points de terminaison modifiés doivent également être mises à jour, si elles sont mises à profit. </li><li>Modifiez toutes les applications d’entreprise tierces pour les rediriger vers les points de terminaison internationaux. </li></ul>| Action requise. Si vous ne le faites pas, le service ou les clients logiciels risquent d’échouer. |
||||
