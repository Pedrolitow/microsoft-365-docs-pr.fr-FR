---
title: Valider les paramètres de protection des applications sur les appareils Android ou iOS
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: medium
ms.date: 07/19/2022
ms.custom:
- MSB365
search.appverid:
- BCS160
- MET150
description: Découvrez comment valider les paramètres de protection des applications Microsoft 365 Business Premium sur vos appareils Android ou iOS. Il est essentiel de définir des paramètres de sécurité pour vos applications afin de protéger les fichiers de vos applications et appareils mobiles contre tout type de menaces de sécurité.
ms.openlocfilehash: 36a67f999cb9b4476f3757daa6033e6409b49c1a
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893812"
---
# <a name="validate-app-protection-settings-on-android-or-ios-devices"></a>Valider les paramètres de protection des applications sur les appareils Android ou iOS


Suivez les instructions des sections suivantes pour valider les paramètres de protection des applications sur les appareils Android ou iOS.
  
## <a name="android"></a>[Android](#tab/Android)  

### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Vérifier que les paramètres de protection des applications fonctionnent sur les appareils utilisateur

Après avoir [défini les paramètres de protection des applications pour les appareils Android ou iOS](../business-premium/m365bp-app-protection-settings-for-android-and-ios.md) afin de protéger les applications, vous pouvez suivre ces étapes pour valider les paramètres que vous avez choisis.
  
Tout d’abord, assurez-vous que la stratégie s’applique à l’application dans laquelle vous allez la valider.
  
1. Dans le [centre d’administration](https://admin.microsoft.com) Microsoft 365 Business Premium, accédez **à La** **stratégie de modification** des \> stratégies.

2. Choisissez **la stratégie d’application pour Android** pour les paramètres que vous avez créés lors de l’installation, ou une autre stratégie que vous avez créée, et vérifiez qu’elle est appliquée pour Outlook, par exemple. 

    ![Capture d’écran montrant toutes les applications pour lesquelles cette stratégie protège les fichiers.](../business-premium/media/b3be3ddd-f683-4073-8d7a-9c639a636a2c.png)
  
### <a name="validate-require-a-pin-or-a-fingerprint-to-access-office-apps"></a>Confirmer le fonctionnement du paramètre Exiger un code confidentiel ou une empreinte pour accéder aux applications Office

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Contrôle de l'accès aux documents Office**, développez **Gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et assurez-vous que l'option **Exiger un code confidentiel ou une empreinte pour accéder aux applications Office** est **activée**.
  
![Assurez-vous que l’option Exiger un code confidentiel ou une empreinte digitale pour accéder aux applications Office est activée.](../business-premium/media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Sur l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur.

2. Vous serez également invité à entrer un code confidentiel ou à utiliser une empreinte digitale.

    ![Enter a PIN on your Android device to access Office apps.](../business-premium/media/9e8ecfee-8122-4a3a-8918-eece80344310.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Confirmer le fonctionnement du paramètre Réinitialiser le code confidentiel après un certain nombre d'échecs successifs

Dans le volet **Modifier** la stratégie, choisissez **Modifier** en regard du **contrôle d’accès aux documents Office**, **développez Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et assurez-vous que **la réinitialisation du code confidentiel après le nombre de tentatives ayant échoué** est définie sur un certain nombre. Il s’agit de 5 par défaut. 
  
1. Sur l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur.

2. Entrez un code confidentiel incorrect autant de fois que le spécifie la stratégie. Vous verrez une invite indiquant la **limite de tentative de code confidentiel atteinte** pour réinitialiser le code confidentiel. 

    ![Capture d’écran indiquant qu’après trop de tentatives de code confidentiel incorrectes, vous devez réinitialiser votre code confidentiel.](../business-premium/media/fca6fcb4-bb5c-477f-af5e-5dc937e8b835.png)
  
3. Appuyez sur **Réinitialiser le code confidentiel**. Vous serez invité à vous connecter avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis à définir un nouveau code confidentiel.

### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Confirmer le fonctionnement du paramètre Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **activée**.
  
![Verify that Force users to save all work files to OneDrive for Business is set to On.](../business-premium/media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Dans l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis entrez un code confidentiel si nécessaire.

2. Ouvrez un e-mail qui contient une pièce jointe et appuyez sur l'icône de flèche vers le bas en regard des informations de la pièce jointe.

    ![Tap the down arrow next to an attachment to try to save it.](../business-premium/media/b22573bb-91ce-455f-84fa-8feb2846b117.png)
  
    Vous verrez **Impossible d’enregistrer sur l’appareil** en bas de l’écran. 

    ![Warning text that indicates cannot save a file locally to an Android.](../business-premium/media/52ca3f3d-7ed0-4a52-9621-4872da6ea9c5.png)
  
    > [!NOTE]
    > L'enregistrement dans OneDrive Entreprise n'est pas activé pour Android pour le moment. C'est pourquoi la seule chose affichée est le message indiquant que l'enregistrement local est bloqué. 
  
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Confirmer le fonctionnement du paramètre Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office

Dans le volet **Modifier** la stratégie, choisissez **Modifier** en regard du **contrôle d’accès aux documents Office**, **développez Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et **assurez-vous que l’option Exiger que les utilisateurs se reconnectent une fois que les applications Office ont été inactives** est définie sur un certain nombre de minutes. Il s’agit de 30 minutes par défaut. 
  
1. Dans l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis entrez un code confidentiel si nécessaire.

1. Vous devez maintenant voir la boîte de réception d'Outlook. Ne touchez pas à l'appareil Android pendant au moins 30 minutes (ou toute autre durée supérieure à celle que vous avez spécifiée dans la stratégie). L'appareil va probablement se mettre en veille.

1. Accédez à nouveau à Outlook sur l’appareil Android.

1. Vous serez invité à entrer votre code confidentiel avant de pouvoir accéder à Nouveau à Outlook.

### <a name="validate-protect-work-files-with-encryption"></a>Confirmer le fonctionnement du paramètre Chiffrer les fichiers professionnels pour les protéger

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Chiffrer les fichiers professionnels pour les protéger** est **activée** et que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **désactivée**.
  
1. Dans l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis entrez un code confidentiel si nécessaire.

1. Ouvrez un e-mail contenant quelques pièces jointes de fichier image.

1. Appuyez sur l'icône de flèche vers le bas en regard des informations de la pièce jointe pour enregistrer cette dernière.

    ![Tap the down arrow to save the figure file to the Android device.](../business-premium/media/08a9e21e-4022-45d5-acff-59cface651e7.png)
  
1. Il se peut que vous soyez invité à autoriser Outlook à accéder aux photos, éléments multimédia et fichiers enregistrés sur votre appareil. Appuyez sur **Autoriser**.

1. En bas de l'écran, sélectionnez **Enregistrer sur l'appareil**, puis ouvrez l'application **Galerie**.

1. Vous devriez voir une photo chiffrée (ou plusieurs si vous avez enregistré plusieurs pièces jointes de fichiers images) dans la liste. Elle peut figurer dans la liste Photos sous la forme d'un carré gris avec un point d'exclamation blanc dans un cercle blanc au centre du carré gris.

    ![An encrypted image file in the Gallery app.](../business-premium/media/25936414-bd7e-421d-824e-6e59b877722d.png)
  
### <a name="ios"></a>[iOS](#tab/iOS)

## <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Vérifier que les paramètres de protection des applications fonctionnent sur les appareils de l'utilisateur

Une fois que vous avez [défini des configurations d'application pour les appareils iOS](../business-premium/m365bp-protection-settings-for-windows-10-devices.md) afin de protéger les applications, vous pouvez suivre cette procédure pour confirmer que les paramètres sélectionnés fonctionnent bien. 
  
Tout d’abord, assurez-vous que la stratégie s’applique à l’application dans laquelle vous allez la valider.
  
1. Dans le [centre d’administration](https://admin.microsoft.com) Microsoft 365 Business Premium, accédez **à La** **stratégie de modification** des \> stratégies.

1. Choisissez **la stratégie d’application pour iOS pour** les paramètres que vous avez créés lors de l’installation, ou une autre stratégie que vous avez créée, et vérifiez qu’elle est appliquée pour Outlook, par exemple. 

    ![Capture d’écran montrant toutes les applications pour lesquelles cette stratégie protège les fichiers.](../business-premium/media/842441b8-e7b1-4b86-9edd-d94d1f77b6f4.png)
  
### <a name="validate-require-a-pin-to-access-office-apps"></a>Confirmer le fonctionnement du paramètre Exiger un code confidentiel pour accéder aux applications Office

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Contrôle de l'accès aux documents Office**, développez **Gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et assurez-vous que l'option **Exiger un code confidentiel ou une empreinte pour accéder aux applications Office** est **activée**.
  
![Assurez-vous que l’option Exiger un code confidentiel ou une empreinte digitale pour accéder aux applications Office est activée.](../business-premium/media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur.

1. Vous serez également invité à entrer un code confidentiel ou à utiliser une empreinte digitale.

    ![Enter a PIN on your IOS device to access Office apps.](../business-premium/media/06fc5cf3-9f19-4090-b23c-14bb59805b7a.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Confirmer le fonctionnement du paramètre Réinitialiser le code confidentiel après un certain nombre d'échecs successifs

Dans le volet **Modifier** la stratégie, choisissez **Modifier** en regard du **contrôle d’accès aux documents Office**, **développez Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et assurez-vous que **la réinitialisation du code confidentiel après le nombre de tentatives ayant échoué** est définie sur un certain nombre. Il s’agit de 5 par défaut.
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur.

1. Entrez un code confidentiel incorrect autant de fois que le spécifie la stratégie. Vous verrez une invite indiquant la **limite de tentative de code confidentiel atteinte** pour réinitialiser le code confidentiel.

    ![Capture d’écran d’avertissement de réinitialisation du code confidentiel après trop de tentatives incorrectes.](../business-premium/media/fab5c089-a4a5-4e8d-8c95-b8eed1dfa262.png)
  
1. Appuyez sur **OK**. Vous serez invité à vous connecter avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis à définir un nouveau code confidentiel.

### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Confirmer le fonctionnement du paramètre Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **activée**.
  
![Verify that Force users to save all work files to OneDrive for Business is set to On.](../business-premium/media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis entrez un code confidentiel si nécessaire.

1. Ouvrez un e-mail qui contient une pièce jointe, ouvrez la pièce jointe et sélectionnez **Enregistrer** au bas de l'écran. 

    ![Tap the Save option after you open an attachment to try to save it.](../business-premium/media/b419b070-1530-4f14-86a8-8d89933a2b25.png)
  
1. Seule une option pour OneDrive Entreprise devrait être affichée. Si ce n’est pas le cas, appuyez sur **Ajouter un compte** et sélectionnez **OneDrive Entreprise** dans l’écran **Ajouter un compte de stockage**. Indiquez l’Microsoft 365 Business Premium de l’utilisateur final pour se connecter lorsque vous y êtes invité.

    Appuyez sur **Enregistrer** et sélectionnez **OneDrive Entreprise**.

### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Confirmer le fonctionnement du paramètre Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office

Dans le volet **Modifier** la stratégie, choisissez **Modifier** en regard du **contrôle d’accès aux documents Office**, **développez Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et **assurez-vous que l’option Exiger que les utilisateurs se reconnectent une fois que les applications Office ont été inactives** est définie sur un certain nombre de minutes. Il s’agit de 30 minutes par défaut.
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis entrez un code confidentiel si nécessaire.

1. Vous devez maintenant voir la boîte de réception d'Outlook. Ne touchez pas à l'appareil iOS pendant au moins 30 minutes (ou toute autre durée supérieure à celle que vous avez spécifiée dans la stratégie). L'appareil va probablement se mettre en veille.

1. Accédez à nouveau à Outlook sur l’appareil iOS.

1. Vous serez invité à entrer votre code confidentiel avant de pouvoir accéder à Nouveau à Outlook.

### <a name="validate-protect-work-files-with-encryption"></a>Confirmer le fonctionnement du paramètre Chiffrer les fichiers professionnels pour les protéger

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Chiffrer les fichiers professionnels pour les protéger** est **activée** et que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **désactivée**.
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium de l’utilisateur, puis entrez un code confidentiel si nécessaire.

1. Ouvrez un e-mail contenant quelques pièces jointes de fichier image.

1. Appuyez sur la pièce jointe, puis sur l'option **Enregistrer** en dessous. 

1. Ouvrez l'application **Photos** à partir de l'écran d'accueil. Vous devriez voir une photo (ou plusieurs si vous avez enregistré plusieurs pièces jointes de fichiers images) enregistrée, mais chiffrée. 

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)