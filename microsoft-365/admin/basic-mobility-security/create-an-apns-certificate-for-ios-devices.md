---
title: Configurer un certificat APNs pour les appareils iOS
f1.keywords: NOCSH
ms.author: kwekua
author: kwekua
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
description: Gérez les appareils iOS dans mobilité et sécurité de base.
ms.openlocfilehash: 99aa909bf9adab1464ad3858cfac4a04cc541609
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781158"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Configurer un certificat APNs pour les appareils iOS

Pour gérer des appareils iOS tels que des iPad et des iPhone dans mobilité et sécurité de base, créez un certificat APNs.

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Dans votre navigateur, tapez <https://protection.office.com/>.

3. Sélectionnez **Gestion des** appareils de **protection contre la** \> perte de données, puis choisissez **Certificat APNs pour les appareils iOS**.

4. Dans la page Paramètres certificat de notification Push Apple, choisissez **Suivant**.

5. Sélectionnez Télécharger votre fichier CSR et enregistrez la demande de signature de certificat quelque part sur votre ordinateur dont vous vous souviendrez. Sélectionnez **Suivant**.

6. Dans la page Créer un certificat APNs :

    1. Select Apple APNS Portal to open the Apple Push Certificates Portal. 

    2. Sign in with an Apple ID.

       > [!IMPORTANT]
       > Use a company Apple ID associated with an email account that will remain with your organization even if the user who manages the account leaves. Save this ID because you'll need to use the same ID when it's time to renew the certificate.

    3. Sélectionnez **Créer un certificat** et acceptez les conditions d’utilisation.

    4. Accédez à la demande de signature de certificat que vous avez téléchargée sur votre ordinateur à partir de Microsoft 365, puis sélectionnez **Télécharger**.

       Téléchargez le certificat APNs créé par le portail de certificats Push Apple sur votre ordinateur.

       > [!TIP]
       > If you're having trouble downloading the certificate, refresh your browser.

7. Retour à Microsoft 365, puis sélectionnez **Suivant** pour accéder à la page de **certificat APNS Télécharger**.

8.  Browse to the APN certificate you downloaded from the Apple Push Certificates Portal.

9. Sélectionnez **Terminer**.

Pour terminer l’installation, revenez aux **paramètres** de gestion de la **gestion** \> des appareils des stratégies **de sécurité** \> du Centre \> de sécurité & conformité.
