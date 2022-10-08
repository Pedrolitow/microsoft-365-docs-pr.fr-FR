---
title: Configurer un certificat APNs pour les appareils iOS
f1.keywords: NOCSH
ms.author: kwekua
author: kwekua
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
description: Pour gérer des appareils iOS tels que des iPad et des iPhone dans mobilité et sécurité de base, commencez par créer un certificat APNs.
ms.openlocfilehash: b85976c2c6f07672635b6474e036accd2b3789d7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68166854"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Configurer un certificat APNs pour les appareils iOS

Pour gérer des appareils iOS tels que des iPad et des iPhone dans mobilité et sécurité de base, créez un certificat APNs.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

1. Accédez à la [Centre d'administration Microsoft 365](https://portal.office.com/adminportal/home?#/MifoDevices), puis choisissez **Certificat APNs pour iOS**.

1. Dans la page Paramètres du certificat de notification Push Apple, choisissez **Suivant**.

1. Sélectionnez Télécharger votre fichier CSR et enregistrez la demande de signature de certificat quelque part sur votre ordinateur dont vous vous souviendrez. Sélectionnez **Suivant**.

1. Dans la page Créer un certificat APNs :

    1. Select Apple APNS Portal to open the Apple Push Certificates Portal. 

    2. Sign in with an Apple ID.

       > [!IMPORTANT]
       > Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

    3. Sélectionnez **Créer un certificat** et acceptez les conditions d’utilisation.

    4. Accédez à la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir de Microsoft 365, puis **sélectionnez Charger**.

       Téléchargez le certificat APNs créé par le portail de certificats Push Apple sur votre ordinateur.

       > [!TIP]
       > If you're having trouble downloading the certificate, refresh your browser.

1. Retour à Microsoft 365, puis sélectionnez **Suivant** pour accéder à la page Charger le **certificat APNS**.

1.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.

1. Sélectionnez **Terminer**.

Pour terminer l’installation, revenez aux **paramètres** de gestion de la **gestion** \> des appareils des stratégies **de sécurité** \> du Centre \> de sécurité & conformité.
