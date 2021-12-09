---
title: Résolution des problèmes Microsoft 365'utilisation
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a73632a1-62c8-4a13-8115-913773b30f93
description: Découvrez comment résoudre les problèmes avec l’application Microsoft 365 d’analyse de l’utilisation.
ms.openlocfilehash: e9bb73eea33e882fb5c9b138610cdc0f8fe9a7c5
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61373751"
---
# <a name="troubleshooting-microsoft-365-usage-analytics"></a>Résolution des problèmes Microsoft 365'utilisation

Explorez la liste suivante des messages d’erreur pour obtenir de l’aide sur les problèmes les plus courants Microsoft 365'analyse de l’utilisation.
  
    
## <a name="we-are-unable-to-process-your-request-you-have-to-first-subscribe-to-this-data-from-the-microsoft-365-admin-center"></a>Nous ne sommes pas en mesure de traiter votre demande. Vous devez d’abord vous abonner à ces données à partir du Centre d'administration Microsoft 365

 **Code d’erreur :** 422 
  
 **Où vous verrez ce message :** Dans Power BI lorsque vous vous connectez à l’application Microsoft 365 Modèle d’analyse de l’utilisation ou lorsque vous appelez directement les API Microsoft 365 de rapports. 
  
 **Cause :** Avant de vous connecter à l’application, vous devez vous abonner aux données du Centre d'administration Microsoft 365. Si cette étape n’est pas effectuée en premier, vous ne pourrez pas vous connecter à l’application de modèle, même si vous fournissez votre ID Microsoft 365 client. 
  
 **Pour corriger cette erreur :** Pour vous abonner aux données, go to the admin center \> **Reports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Usage</a> and locate the Microsoft 365 usage analytics tile on the main dashboard page. Sélectionnez **le** bouton Commencer,  puis, dans le volet  Rapports qui s’ouvre, rendez les données disponibles pour Microsoft 365 l’analyse de l’utilisation Power BI sur et **Enregistrer.**
  
## <a name="we-are-processing-your-data"></a>Vos données sont en cours de traitement

 **Où vous verrez ce message :** Dans la vignette **Microsoft 365'analyse de l’utilisation** dans le **tableau** de bord Utilisation de la Centre d'administration Microsoft 365. 
  
 **Cause :** Lorsque vous [choisissez de](enable-usage-analytics.md) voir les données dans l’application modèle à partir du Centre d'administration Microsoft 365, le système Microsoft 365 commence à générer des données d’utilisation historiques pour votre organisation. En fonction de la taille de votre locataire, cette étape peut prendre 2 à 48 heures. 
  
 **Pour résoudre ce problème :** Soyez patient, mais si le message  n’est pas ajouté à Vos données, il est prêt après 3 jours, [contactez Microsoft 365 support technique pour les entreprises]( Obtenez un [support technique.](../get-help-support.md)
  
## <a name="we-are-unable-to-process-your-request-at-this-time-we-are-still-preparing-the-data-for-your-organization"></a>Nous ne sommes pas en mesure de traiter votre demande pour le moment. Les données relatives à votre organisation sont en cours de préparation

 **Code d'erreur :** 423 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application Microsoft 365 Modèle d’analyse de l’utilisation ou lorsque vous appelez directement les API Microsoft 365 de rapports. 
  
 **Cause :** Lorsque vous [choisissez de](enable-usage-analytics.md) voir les données dans l’application modèle à partir du Centre d’administration, le système Microsoft 365 commence à générer des données d’utilisation historiques pour votre organisation. Selon la taille de votre client, cette étape peut prendre entre deux et 48 heures. 
  
 **Pour résoudre ce problème :** Soyez patient, mais si le message  n’est pas ajouté à Vos données, même 3 jours après l’initiation, contactez Microsoft 365 pour le [support technique.](../../business-video/get-help-support.md)
  
## <a name="the-tenant-id-you-provided-is-not-in-the-correct-format"></a>Le format de l'ID de locataire que vous avez fourni est incorrect

 **Code d'erreur :** 400 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application Microsoft 365 Modèle d’analyse de l’utilisation ou lorsque vous appelez directement les API Microsoft 365 de rapports. 
  
 **Cause :** L’ID de client est un GUID qui doit être au format xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx. Si vous entrez une autre chaîne dans la zone d’entrée du client, vous obtenez cette erreur. 
  
 **Pour corriger cette erreur :** Go to the admin center \> **Reports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Usage</a> and locate the Microsoft 365 usage analytics tile on the main dashboard page. L’ID de client est répertorié sur la vignette. Vous pouvez le copier à partir d’ici et le coller dans la boîte de dialogue pour vous connecter à l’application de modèle. 
  
## <a name="the-tenant-id-you-provided-is-not-recognized-by-our-system"></a>Notre système ne reconnaît pas l'ID de locataire que vous avez fourni

 **Code d'erreur :** 404 
  
 **Où vous verrez ce message :** Dans Power BI lorsque vous vous connectez à l’application Microsoft 365 Modèle d’analyse de l’utilisation ou lorsque vous appelez directement les API Microsoft 365 de rapports. 
  
 **Cause :** L’ID de locataire que vous avez fourni n’est pas valide ou n’existe pas. 
  
 **Pour corriger cette erreur :** Go to the admin center \> **Reports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Usage</a> and locate the Microsoft 365 usage analytics tile on the main dashboard page. L’ID de client est répertorié sur la vignette. Vous pouvez le copier à partir d’ici et le coller dans la boîte de dialogue pour vous connecter à l’application de modèle. 
  
## <a name="please-re-enter-your-credentials-to-sign-in-to-power-bi-again"></a>Entrez à nouveau vos informations d'identification pour vous connecter à Power BI

Code d'erreur : 302
  
 **Où vous verrez ce message :** Dans Power BI lorsque vous vous connectez à l’application Microsoft 365 Modèle d’analyse de l’utilisation ou lorsque vous appelez directement les API Microsoft 365 de rapports. 
  
 **Cause :** Le code d'autorisation a échoué. Vous risquez d'être invité à entrer à nouveau vos informations d'identification. 
  
 **Pour résoudre ce problème :** Déconnectez-vous de Power BI, puis reconnectez-vous. 
  
## <a name="you-do-not-have-the-right-authorization-to-access-to-this-data-to-be-able-to-gain-access-to-the-data-from-this-service-you-need-to-be-either-a-global-admin-or-any-one-of-the-product-admins"></a>Vous ne disposez pas de l'autorisation adéquate pour accéder à ces données. Pour accéder aux données à partir de ce service, vous devez être administrateur général ou administrateur de produit

 **Code d'erreur :** 403 
  
 **Où vous verrez ce message :** Dans Power BI lorsque vous vous connectez à l’application Microsoft 365 Modèle d’analyse de l’utilisation ou lorsque vous appelez directement les API Microsoft 365 de rapports. 
  
 **Cause :** Le code d’autorisation a échoué car l’utilisateur qui a tenté de se connecter à l’application modèle ne peut pas accéder à ces données avec le niveau d’autorisation le plus élevé. 
  
 **Pour corriger cette erreur :** Fournissez les informations d’identification d’un utilisateur qui est un administrateur global, un administrateur  **Exchange,**  un administrateur **Skype Entreprise,** un administrateur  **SharePoint,** un lecteur global ou un lecteur de rapports pour se connecter à l’application de modèle. Pour plus [d’informations, voir](../add-users/about-admin-roles.md) à propos des rôles d’administrateur. 
  
## <a name="refresh-failed"></a>L'actualisation a échoué

 **Où ce message s'affichera-t-il ?** E-mail de Power BI ou état d'échec dans l'historique d'actualisation. 
  
 **Cause :** Parfois, les informations d’identification de l’utilisateur qui s’est connecté à l’application de modèle sont réinitialisées et ne sont pas mises à jour dans les paramètres de connexion de l’application de modèle, ce qui provoque des erreurs d’échec d’actualisation de l’utilisateur. 
  
 **Pour corriger cette erreur :** Dans Power BI, recherchez le jeu de données correspondant à l’application  Microsoft 365 Modèle d’analyse de l’utilisation, sélectionnez planifier l’actualisation et fournissez vos informations d’identification d’administrateur. 
  
Si cela ne fonctionne pas, effacer le cache et re-créer l’application de modèle.
  
  
