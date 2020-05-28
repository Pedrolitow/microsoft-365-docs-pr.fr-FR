---
title: Résolution des problèmes d’analyse de l’utilisation de Microsoft 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
description: Découvrez comment résoudre les problèmes liés à l’application de modèle d’analyse de l’utilisation de Microsoft 365.
ms.openlocfilehash: 4696dd0c5140cdc110781c226819fc64a90fae1b
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44402033"
---
# <a name="troubleshooting-microsoft-365-usage-analytics"></a>Résolution des problèmes d’analyse de l’utilisation de Microsoft 365

Explorez la liste de messages d’erreur suivante pour obtenir de l’aide sur les problèmes les plus courants liés à l’analyse de l’utilisation de Microsoft 365.
  
    
## <a name="we-are-unable-to-process-your-request-you-have-to-first-subscribe-to-this-data-from-the-microsoft-365-admin-center"></a>Nous ne sommes pas en mesure de traiter votre demande. Vous devez d’abord vous abonner à ces données à partir du centre d’administration Microsoft 365

 **Code d'erreur :** 422 
  
 **Où le message suivant s’affiche :** Dans Power BI lorsque vous vous connectez à l’application de modèle d’analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Avant de vous connecter à l’application, vous devez vous abonner aux données à partir du centre d’administration 365 de Microsoft. Si cette étape n’est pas réalisée en premier, vous ne pourrez pas vous connecter à l’application de modèle, même si vous fournissez votre ID de client Microsoft 365. 
  
 **Pour corriger cette erreur :** Pour vous abonner aux données, accédez à l’utilisation des rapports du centre d’administration \> **Reports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Usage</a> et recherchez la vignette Microsoft 365 utilisation analytique sur la page principale du tableau de bord. Sélectionnez le bouton **prise en main** , puis, dans le volet **rapports** qui s’ouvre, activez la case à cocher créer des **données disponibles pour l’analyse de l’utilisation de Microsoft 365 pour Power bi** sur et **Enregistrer**.
  
## <a name="we-are-processing-your-data"></a>Vos données sont en cours de traitement

 **Où le message suivant s’affiche :** Dans la vignette de l’analyse de l' **utilisation 365 de Microsoft** sur le tableau de bord d' **utilisation** dans le centre d’administration Microsoft 365. 
  
 **Cause :** Lorsque vous [Choisissez d’afficher les données dans l’application de modèle](enable-usage-analytics.md) à partir du centre d’administration Microsoft 365, le système Microsoft 365 commence à générer des données d’utilisation historiques pour votre organisation. En fonction de la taille de votre locataire, cette étape peut prendre 2 à 48 heures. 
  
 **Pour résoudre ce problème :** Il s’agit d’un patient, mais si le message ne change pas pour que **vos données soient prêtes** après 3 jours, [contactez Microsoft 365 pour obtenir de l’aide à](../contact-support-for-business-products.md)la décision.
  
## <a name="we-are-unable-to-process-your-request-at-this-time-we-are-still-preparing-the-data-for-your-organization"></a>Nous ne sommes pas en mesure de traiter votre demande pour le moment. Les données relatives à votre organisation sont en cours de préparation

 **Code d'erreur :** 423 
  
 **Où le message suivant s’affiche :** Dans Power BI lorsque vous vous connectez à l’application de modèle d’analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Lorsque vous [Choisissez d’afficher les données dans l’application de modèle](enable-usage-analytics.md) à partir du centre d’administration, le système Microsoft 365 commence à générer des données d’utilisation historiques pour votre organisation. En fonction de la taille de votre locataire, cette étape peut prendre 2 à 48 heures. 
  
 **Pour résoudre ce problème :** Il s’agit d’un patient, mais si le message ne change pas en fonction de **vos données, il est prêt** de 3 jours après l’initiation, [Contactez le support technique de Microsoft 365](../contact-support-for-business-products.md).
  
## <a name="the-tenant-id-you-provided-is-not-in-the-correct-format"></a>Le format de l'ID de locataire que vous avez fourni est incorrect

 **Code d'erreur :** 400 
  
 **Où le message suivant s’affiche :** Dans Power BI lorsque vous vous connectez à l’application de modèle d’analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** L'ID de locataire est un identificateur global unique (GUID) qui doit être au format xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx. Toute autre chaîne saisie dans la zone d'entrée du locataire générera cette erreur. 
  
 **Pour corriger cette erreur :** Accédez à l’utilisation des rapports du centre d’administration \> **Reports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Usage</a> et localisez la vignette de l’utilisation de Microsoft 365 sur la page principale du tableau de bord. L'ID de locataire est répertorié sur la vignette. Vous pouvez le copier à partir de cet emplacement et le coller dans la boîte de dialogue pour vous connecter à l’application de modèle. 
  
## <a name="the-tenant-id-you-provided-is-not-recognized-by-our-system"></a>Notre système ne reconnaît pas l'ID de locataire que vous avez fourni

 **Code d'erreur :** 404 
  
 **Où le message suivant s’affiche :** Dans Power BI lorsque vous vous connectez à l’application de modèle d’analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** L'ID de locataire que vous avez fourni n'est pas valide ou n'existe pas. 
  
 **Pour corriger cette erreur :** Accédez à l’utilisation des rapports du centre d’administration \> **Reports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Usage</a> et localisez la vignette de l’utilisation de Microsoft 365 sur la page principale du tableau de bord. L'ID de locataire est répertorié sur la vignette. Vous pouvez le copier à partir de cet emplacement et le coller dans la boîte de dialogue pour vous connecter à l’application de modèle. 
  
## <a name="please-re-enter-your-credentials-to-sign-in-to-power-bi-again"></a>Entrez à nouveau vos informations d'identification pour vous connecter à Power BI

Code d'erreur : 302
  
 **Où le message suivant s’affiche :** Dans Power BI lorsque vous vous connectez à l’application de modèle d’analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Le code d'autorisation a échoué. Vous risquez d'être invité à entrer à nouveau vos informations d'identification. 
  
 **Pour résoudre ce problème :** Déconnectez-vous de Power BI, puis reconnectez-vous. 
  
## <a name="you-do-not-have-the-right-authorization-to-access-to-this-data-to-be-able-to-gain-access-to-the-data-from-this-service-you-need-to-be-either-a-global-admin-or-any-one-of-the-product-admins"></a>Vous ne disposez pas de l'autorisation adéquate pour accéder à ces données. Pour accéder aux données à partir de ce service, vous devez être administrateur général ou administrateur de produit

 **Code d'erreur :** 403 
  
 **Où le message suivant s’affiche :** Dans Power BI lorsque vous vous connectez à l’application de modèle d’analyse de l’utilisation de Microsoft 365 ou lorsque vous appelez directement les API de création de rapports Microsoft 365. 
  
 **Cause :** Le code d’autorisation a échoué, car l’utilisateur qui a tenté de se connecter à l’application de modèle ne dispose pas du niveau d’autorisation approprié pour accéder à ces données. 
  
 **Pour corriger cette erreur :** Fournissez les informations d’identification d’un utilisateur qui est soit un administrateur **général**, un administrateur **Exchange**, un **administrateur Skype entreprise**, un **administrateur SharePoint**, un **lecteur global** ou un **lecteur de rapports** pour se connecter à l’application de modèle. Pour plus d’informations, consultez la rubrique [à propos des rôles d’administrateur](../add-users/about-admin-roles.md) . 
  
## <a name="refresh-failed"></a>L'actualisation a échoué

 **Où ce message s'affichera-t-il ?** E-mail de Power BI ou état d'échec dans l'historique d'actualisation. 
  
 **Cause :** Parfois, les informations d’identification de l’utilisateur qui s’est connecté à l’application de modèle sont réinitialisées, et elles ne sont pas mises à jour dans les paramètres de connexion de l’application de modèle, ce qui entraîne l’affichage des erreurs d’échec d’actualisation. 
  
 **Pour corriger cette erreur :** Dans Power BI, recherchez le jeu de données correspondant à l’application de modèle d’analyse de l’utilisation de Microsoft 365, sélectionnez **Schedule Refresh** et fournissez vos informations d’identification d’administrateur. 
  
Si cela ne fonctionne pas, effacez le cache et recréez l’application de modèle.
  
  
