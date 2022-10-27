---
title: Résolution des problèmes liés à l’analytique de l’utilisation de Microsoft 365
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
- Tier2
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
description: Découvrez comment résoudre les problèmes liés à l’application modèle Analyse de l’utilisation De Microsoft 365.
ms.openlocfilehash: 0aaeb559a27f75a60ca4966041b75ac694025e0f
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68733744"
---
# <a name="troubleshooting-microsoft-365-usage-analytics"></a>Résolution des problèmes liés à l’analytique de l’utilisation de Microsoft 365

Explorez la liste suivante de messages d’erreur pour obtenir de l’aide sur les problèmes les plus courants liés à l’analytique de l’utilisation de Microsoft 365.
  
    
## <a name="we-are-unable-to-process-your-request-you-have-to-first-subscribe-to-this-data-from-the-microsoft-365-admin-center"></a>Nous ne sommes pas en mesure de traiter votre demande. Vous devez d’abord vous abonner à ces données à partir du Centre d'administration Microsoft 365

 **Code d’erreur :** 422 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Avant de pouvoir vous connecter à l’application, vous devez vous abonner aux données du Centre d'administration Microsoft 365. Si cette étape n’est pas effectuée en premier, vous ne pourrez pas vous connecter à l’application modèle, même si vous fournissez votre ID de locataire Microsoft 365. 
  
 **Pour corriger cette erreur :** Pour vous abonner aux données, accédez au centre \> d’administration **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a> et recherchez la vignette Analyse de l’utilisation de Microsoft 365 sur la page principale du tableau de bord. Sélectionnez le bouton **Prise en main**, puis, dans le volet **Rapports** qui s’ouvre, activez et **enregistrez** le paramètre **Rendre les données disponibles pour l’analytique de l’utilisation de Microsoft 365 pour Power BI**.
  
## <a name="we-are-processing-your-data"></a>Vos données sont en cours de traitement

 **Où vous verrez ce message :** Dans la vignette **Analyse de l’utilisation de Microsoft 365** sur le tableau de bord **Utilisation** dans le Centre d'administration Microsoft 365. 
  
 **Cause :** Lorsque vous [choisissez d’afficher des données dans l’application modèle](enable-usage-analytics.md) à partir de l’Centre d'administration Microsoft 365, le système Microsoft 365 commence à générer des données d’historique d’utilisation pour votre organisation. En fonction de la taille de votre locataire, cette étape peut prendre 2 à 48 heures. 
  
 **Pour résoudre ce problème :** Soyez patient, mais si le message ne change pas **en Vos données sont prêtes** après 3 jours, [contactez le support microsoft 365 pour les entreprises](obtenir du support](.. /get-help-support.md).
  
## <a name="we-are-unable-to-process-your-request-at-this-time-we-are-still-preparing-the-data-for-your-organization"></a>Nous ne sommes pas en mesure de traiter votre demande pour le moment. Les données relatives à votre organisation sont en cours de préparation

 **Code d'erreur :** 423 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Lorsque vous [choisissez d’afficher des données dans l’application modèle à](enable-usage-analytics.md) partir du centre d’administration, le système Microsoft 365 commence à générer des données d’utilisation historiques pour votre organisation. Selon la taille de votre locataire, cette étape peut prendre entre deux heures et 48 heures. 
  
 **Pour résoudre ce problème :** Soyez patient, mais si le message ne change pas en **Vos données sont prêtes** , même 3 jours après le lancement, [contactez le support microsoft 365 pour les entreprises](../../business-video/get-help-support.md).
  
## <a name="the-tenant-id-you-provided-is-not-in-the-correct-format"></a>Le format de l'ID de locataire que vous avez fourni est incorrect

 **Code d'erreur :** 400 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Microsoft 365 Usage Analytics ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** L’ID de locataire est un GUID et doit être au format xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxxx. Si vous entrez une autre chaîne dans la zone d’entrée du locataire, vous obtenez cette erreur. 
  
 **Pour corriger cette erreur :** Accédez au centre \> d’administration **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">d’utilisation</a> et recherchez la vignette Analyse de l’utilisation de Microsoft 365 sur la page principale du tableau de bord. L’ID de locataire est répertorié sur la vignette. Vous pouvez le copier à partir d’ici et le coller dans la boîte de dialogue pour vous connecter à l’application modèle. 
  
## <a name="the-tenant-id-you-provided-is-not-recognized-by-our-system"></a>Notre système ne reconnaît pas l'ID de locataire que vous avez fourni

 **Code d'erreur :** 404 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** L’ID de locataire que vous avez fourni n’est pas valide ou n’existe pas. 
  
 **Pour corriger cette erreur :** Accédez au centre \> d’administration **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">d’utilisation</a> et recherchez la vignette Analyse de l’utilisation de Microsoft 365 sur la page principale du tableau de bord. L’ID de locataire est répertorié sur la vignette. Vous pouvez le copier à partir d’ici et le coller dans la boîte de dialogue pour vous connecter à l’application modèle. 
  
## <a name="please-re-enter-your-credentials-to-sign-in-to-power-bi-again"></a>Entrez à nouveau vos informations d'identification pour vous connecter à Power BI

Code d'erreur : 302
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Le code d'autorisation a échoué. Vous risquez d'être invité à entrer à nouveau vos informations d'identification. 
  
 **Pour résoudre ce problème :** Déconnectez-vous de Power BI, puis reconnectez-vous. 
  
## <a name="you-do-not-have-the-right-authorization-to-access-to-this-data-to-be-able-to-gain-access-to-the-data-from-this-service-you-need-to-be-either-a-global-admin-or-any-one-of-the-product-admins"></a>You do not have the right authorization to access to this data. To be able to gain access to the data from this service you need to be either a global admin or any one of the product admins

 **Code d'erreur :** 403 
  
 **Où vous verrez ce message :** Dans Power BI, lorsque vous vous connectez à l’application modèle Analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Le code d’autorisation a échoué, car l’utilisateur qui a essayé de se connecter à l’application modèle n’a pas le niveau d’autorisation approprié pour accéder à ces données. 
  
 **Pour corriger cette erreur :** Fournissez les informations d’identification d’un utilisateur qui est **administrateur général**, **administrateur Exchange**, **administrateur Skype Entreprise**, **administrateur SharePoint**, **lecteur général** ou **lecteur de rapport** pour se connecter à l’application modèle. Pour plus [d’informations, consultez À propos des rôles d’administrateur](../add-users/about-admin-roles.md) . 
  
## <a name="refresh-failed"></a>L'actualisation a échoué

 **Où ce message s'affichera-t-il ?** E-mail de Power BI ou état d'échec dans l'historique d'actualisation. 
  
 **Cause :** Parfois, les informations d’identification de l’utilisateur qui s’est connecté à l’application modèle sont réinitialisées et ne sont pas mises à jour dans les paramètres de connexion de l’application modèle, ce qui entraîne l’échec de l’actualisation de l’utilisateur. 
  
 **Pour corriger cette erreur :** Dans Power BI, recherchez le jeu de données correspondant à l’application modèle Microsoft 365 Usage Analytics, sélectionnez **Planifier l’actualisation** et fournissez vos informations d’identification d’administrateur. 
  
Si cela ne fonctionne pas, effacez le cache et recréez l’application modèle.
  
  
