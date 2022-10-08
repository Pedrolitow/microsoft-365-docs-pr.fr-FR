---
title: Résolution des problèmes d’analyse de l’utilisation de Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a73632a1-62c8-4a13-8115-913773b30f93
description: Découvrez comment résoudre les problèmes liés à l’application modèle Analyse de l’utilisation de Microsoft 365.
ms.openlocfilehash: 6b6a293d1627ca4fc91836c0ae9a503903186330
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68165842"
---
# <a name="troubleshooting-microsoft-365-usage-analytics"></a>Résolution des problèmes d’analyse de l’utilisation de Microsoft 365

Explorez la liste suivante des messages d’erreur pour obtenir de l’aide sur les problèmes les plus courants liés à l’analyse de l’utilisation de Microsoft 365.
  
    
## <a name="we-are-unable-to-process-your-request-you-have-to-first-subscribe-to-this-data-from-the-microsoft-365-admin-center"></a>Nous ne sommes pas en mesure de traiter votre demande. Vous devez d’abord vous abonner à ces données à partir de la Centre d'administration Microsoft 365

 **Code d’erreur :** 422 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Avant de pouvoir vous connecter à l’application, vous devez vous abonner aux données du Centre d'administration Microsoft 365. Si cette étape n’est pas effectuée en premier, vous ne pourrez pas vous connecter à l’application modèle, même si vous fournissez votre ID de locataire Microsoft 365. 
  
 **Pour corriger cette erreur :** Pour vous abonner aux données, accédez au centre \> d’administration **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">d’utilisation</a> et recherchez la vignette Analyse de l’utilisation de Microsoft 365 sur la page du tableau de bord principal. Sélectionnez le bouton **Prise en main**, puis, dans le volet **Rapports** qui s’ouvre, **activez et enregistrez les données disponibles pour l’analyse de l’utilisation de Microsoft 365 pour le paramètre Power BI**.
  
## <a name="we-are-processing-your-data"></a>Vos données sont en cours de traitement

 **Où vous verrez ce message :** Dans la vignette **Analyse de l’utilisation de Microsoft 365** sur le tableau de bord **Utilisation** dans le Centre d'administration Microsoft 365. 
  
 **Cause :** Lorsque vous [choisissez de voir des données dans l’application modèle](enable-usage-analytics.md) à partir du Centre d'administration Microsoft 365, le système Microsoft 365 commence à générer des données d’utilisation historiques pour votre organisation. En fonction de la taille de votre locataire, cette étape peut prendre 2 à 48 heures. 
  
 **Pour résoudre ce problème :** Soyez patient, mais si le message ne change pas **à Vos données est prêt** après 3 jours, [contactez le support Microsoft 365 pour les entreprises](Obtenir un support](.. /get-help-support.md).
  
## <a name="we-are-unable-to-process-your-request-at-this-time-we-are-still-preparing-the-data-for-your-organization"></a>Nous ne sommes pas en mesure de traiter votre demande pour le moment. Les données relatives à votre organisation sont en cours de préparation

 **Code d'erreur :** 423 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Lorsque vous [choisissez d’afficher des données dans l’application modèle](enable-usage-analytics.md) à partir du centre d’administration, le système Microsoft 365 commence à générer des données d’utilisation historiques pour votre organisation. Selon la taille de votre locataire, cette étape peut prendre entre deux heures et 48 heures. 
  
 **Pour résoudre ce problème :** Soyez patient, mais si le message ne change pas pour **vos données,** même 3 jours après le lancement, contactez le [support Microsoft 365 pour les entreprises](../../business-video/get-help-support.md).
  
## <a name="the-tenant-id-you-provided-is-not-in-the-correct-format"></a>Le format de l'ID de locataire que vous avez fourni est incorrect

 **Code d'erreur :** 400 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** L’ID de locataire est un guid et doit être au format xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx. Si vous entrez une autre chaîne dans la zone d’entrée du locataire, vous obtiendrez cette erreur. 
  
 **Pour corriger cette erreur :** Accédez au centre \> d’administration **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">d’utilisation</a> et recherchez la vignette Analyse de l’utilisation de Microsoft 365 sur la page du tableau de bord principal. L’ID de locataire est répertorié sur la vignette. Vous pouvez le copier à partir d’ici et le coller dans la boîte de dialogue pour vous connecter à l’application modèle. 
  
## <a name="the-tenant-id-you-provided-is-not-recognized-by-our-system"></a>Notre système ne reconnaît pas l'ID de locataire que vous avez fourni

 **Code d'erreur :** 404 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** L’ID de locataire que vous avez fourni n’est pas valide ou n’existe pas. 
  
 **Pour corriger cette erreur :** Accédez au centre \> d’administration **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">d’utilisation</a> et recherchez la vignette Analyse de l’utilisation de Microsoft 365 sur la page du tableau de bord principal. L’ID de locataire est répertorié sur la vignette. Vous pouvez le copier à partir d’ici et le coller dans la boîte de dialogue pour vous connecter à l’application modèle. 
  
## <a name="please-re-enter-your-credentials-to-sign-in-to-power-bi-again"></a>Entrez à nouveau vos informations d'identification pour vous connecter à Power BI

Code d'erreur : 302
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Le code d'autorisation a échoué. Vous risquez d'être invité à entrer à nouveau vos informations d'identification. 
  
 **Pour résoudre ce problème :** Déconnectez-vous de Power BI, puis reconnectez-vous. 
  
## <a name="you-do-not-have-the-right-authorization-to-access-to-this-data-to-be-able-to-gain-access-to-the-data-from-this-service-you-need-to-be-either-a-global-admin-or-any-one-of-the-product-admins"></a>You do not have the right authorization to access to this data. To be able to gain access to the data from this service you need to be either a global admin or any one of the product admins

 **Code d'erreur :** 403 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Le code d’autorisation a échoué, car l’utilisateur qui a essayé de se connecter à l’application modèle n’a pas le niveau d’autorisation approprié pour accéder à ces données. 
  
 **Pour corriger cette erreur :** Fournissez les informations d’identification d’un utilisateur qui est **administrateur général**, **administrateur Exchange**, **administrateur Skype Entreprise**, **administrateur SharePoint**, **lecteur général** ou **lecteur de rapport** pour se connecter à l’application modèle. [Pour plus d’informations, consultez À propos des rôles d’administrateur](../add-users/about-admin-roles.md). 
  
## <a name="refresh-failed"></a>L'actualisation a échoué

 **Où ce message s'affichera-t-il ?** E-mail de Power BI ou état d'échec dans l'historique d'actualisation. 
  
 **Cause :** Parfois, les informations d’identification de l’utilisateur qui s’est connecté à l’application modèle sont réinitialisées et non mises à jour dans les paramètres de connexion de l’application modèle, ce qui entraîne l’affichage d’erreurs d’échec d’actualisation. 
  
 **Pour corriger cette erreur :** Dans Power BI, recherchez le jeu de données correspondant à l’application modèle Microsoft 365 Usage Analytics, sélectionnez **Planifier l’actualisation** et fournissez vos informations d’identification d’administrateur. 
  
Si cela ne fonctionne pas, effacez le cache et recréez l’application modèle.
  
  
