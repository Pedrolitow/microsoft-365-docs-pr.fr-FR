---
title: Configurer un certificat APNs pour les appareils iOS
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
description: Gérer les appareils iOS dans Basic Mobility and Security.
ms.openlocfilehash: 84f3589593ef26325397f5b6e90d5b21662d2352
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176899"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Configurer un certificat APNs pour les appareils iOS

Pour gérer les appareils iOS tels que les iPad et les iPhone dans Basic Mobility and Security, créez un certificat APNs.

1. Connectez-vous Microsoft 365 avec votre compte d’administrateur global.

2. Dans votre navigateur, tapez  <https://protection.office.com/> .

3. Sélectionnez  **Gestion des appareils de protection contre** la perte de   >  **** données, puis sélectionnez **Certificat APNs pour les appareils iOS.**

4. Dans la page Certificat de notification Push Apple Paramètres, choisissez **Suivant**.

5. Sélectionnez Télécharger votre fichier CSR et enregistrez la demande de signature de certificat dans un endroit de votre ordinateur que vous mémoriserez. Sélectionnez  **Suivant**.

6. Dans la page Créer un certificat APNs :

    1. Sélectionnez Le portail Apple APNS pour ouvrir le portail de certificats Push Apple.

    2. Sign in with an Apple ID.

       > [!IMPORTANT]
       > Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

    3. Sélectionnez  **Créer un certificat et**   acceptez les conditions d’utilisation.

    4. Accédez à la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir Microsoft 365, puis sélectionnez **Télécharger**.

       Téléchargez le certificat APNs créé par le portail de certificats Push Apple sur votre ordinateur.

       > [!TIP]
       > If you're having trouble downloading the certificate, refresh your browser.

7. Revenir à Microsoft 365, puis sélectionnez **Suivant** pour obtenir la   page Télécharger certificat   **APNS.**  

8.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.

9. Sélectionnez  **Terminer.**

Pour terminer l’installation, revenir au Centre de sécurité  **** et conformité & stratégies de sécurité >Gestion des paramètres de gestion   >  ****   >  **des périphériques.**
