---
title: Créer un certificat APNs pour les appareils iOS
f1.keywords: NOCSH
ms.author: kwekua
author: kwekua
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
description: Gérer les appareils iOS dans la sécurité et la mobilité de base.
ms.openlocfilehash: 8b41c1c6c891a5d6cb98a6a381c65aa0310a1761
ms.sourcegitcommit: 2179abfe0b7a8bea917eb1c1057ed3795bdf91e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "47336871"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Créer un certificat APNs pour les appareils iOS

Pour gérer les appareils iOS tels que iPad et iPhone dans la sécurité et la mobilité de base, créez un certificat APNs.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.
    
2. Dans votre navigateur, tapez  [https://protection.office.com](https://protection.office.com/) .
    
3. Sélectionnez gestion des périphériques de  **protection contre la perte de données**   >  **Device management**, puis choisissez le **certificat APNs pour les appareils iOS**.    

4. Sur la page Paramètres du certificat de notification de type Apple, choisissez **suivant**.
    
5. Sélectionnez télécharger votre fichier CSR et enregistrez la demande de signature de certificat sur un emplacement de votre ordinateur dont vous vous souviendrez. Sélectionnez  **suivant**.
    
6. Sur la page créer un certificat APNs :  

    1. Sélectionnez Apple APNS Portal pour ouvrir le portail Appled Certificates.
    
    2. Sign in with an Apple ID.   

    >[!IMPORTANT]
    >Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

    3. Sélectionnez  **créer un certificat**   et accepter les conditions d’utilisation.
    
    4. Accédez à la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir de Microsoft 365, puis sélectionnez **Télécharger**.
    
        Téléchargez le certificat APNs créé par le portail de certificats poussés Apple sur votre ordinateur.
    
       >[!TIP]
       >If you're having trouble downloading the certificate, refresh your browser.

7. Revenez à Microsoft 365, puis sélectionnez **suivant**   pour accéder à la page  **Télécharger le certificat APNs**   .
    
8.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.
    
9. Sélectionnez  **Terminer**.
    
Pour terminer l’installation, revenez au centre de sécurité & conformité >gestion des périphériques de  **sécurité**   >  **Device management**   >  **gérer les paramètres**.
