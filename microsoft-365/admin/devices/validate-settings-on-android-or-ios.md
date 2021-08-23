---
title: Valider les paramètres de protection des applications sur les appareils Android ou iOS
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: f3433b6b-02f7-447f-9d62-306bf03638b0
description: Découvrez comment valider les paramètres Microsoft 365 Business Premium protection des applications sur vos appareils Android ou iOS.
ms.openlocfilehash: 37593e499e772b3f3ed29d8c966812f60e088d1d
ms.sourcegitcommit: 251551539b1532fdac7b7e3dd2733a75c62e8a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58360374"
---
# <a name="validate-app-protection-settings-on-android-or-ios-devices"></a>Valider les paramètres de protection des applications sur les appareils Android ou iOS

Suivez les instructions des sections suivantes pour valider les paramètres de protection des applications sur les appareils Android ou iOS.
  
## <a name="android"></a>Android
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Vérifier que les paramètres de protection des applications fonctionnent sur les appareils des utilisateurs

Une fois que vous avez [défini des configurations d'application pour les appareils Android](app-protection-settings-for-android-and-ios.md) afin de protéger les applications, vous pouvez suivre cette procédure pour confirmer que les paramètres sélectionnés fonctionnent correctement. 
  
Tout d’abord, assurez-vous que la stratégie s’applique à l’application dans laquelle vous allez la valider.
  
1. Dans le centre [Microsoft 365 Business Premium' administration,](https://admin.microsoft.com)allez à  \> **Stratégies modifier la stratégie.**
    
2. Choisissez **une stratégie** d’application pour Android pour les paramètres que vous avez créés lors de l’installation, ou une autre stratégie que vous avez créée, et vérifiez qu’elle est appliquée pour Outlook, par exemple. 
    
    ![Shows all the apps for which this policy protects files.](../../media/b3be3ddd-f683-4073-8d7a-9c639a636a2c.png)
  
### <a name="validate-require-a-pin-or-a-fingerprint-to-access-office-apps"></a>Confirmer le fonctionnement du paramètre Exiger un code confidentiel ou une empreinte pour accéder aux applications Office

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Contrôle de l'accès aux documents Office**, développez **Gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et assurez-vous que l'option **Exiger un code confidentiel ou une empreinte pour accéder aux applications Office** est **activée**.
  
![Assurez-vous que la fonction Exiger un code confidentiel ou une empreinte digitale pour accéder Office applications est définie sur On.](../../media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Sur l’appareil Android de l’utilisateur, Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur.
    
2. Vous serez également invité à entrer un code confidentiel ou à utiliser une empreinte digitale.
    
    ![Enter a PIN on your Android device to access Office apps.](../../media/9e8ecfee-8122-4a3a-8918-eece80344310.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Confirmer le fonctionnement du paramètre Réinitialiser le code confidentiel après un certain nombre d'échecs successifs

In the **Edit policy** pane, choose **Edit** next to Office documents **access control,** expand **Manage how users access Office files on mobile devices**, and make sure that **Reset PIN after number of failed attempts** is set to some number. Il s’agit de 5 par défaut. 
  
1. Sur l’appareil Android de l’utilisateur, Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur.
    
2. Entrez un code confidentiel incorrect autant de fois que le spécifie la stratégie. Vous verrez une invite qui indique que la limite de tentative de code confidentiel **est atteinte** pour réinitialiser le code confidentiel. 
    
    ![After too many incorrect PIN attempts, you need to reset your PIN.](../../media/fca6fcb4-bb5c-477f-af5e-5dc937e8b835.png)
  
3. Appuyez sur **Réinitialiser le code confidentiel**. Vous serez invité à vous inscrire avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis à définir un nouveau code confidentiel.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Confirmer le fonctionnement du paramètre Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **activée**.
  
![Verify that Force users to save all work files to OneDrive for Business is set to On.](../../media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Sur l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis entrez un code confidentiel si nécessaire.
    
2. Ouvrez un e-mail qui contient une pièce jointe et appuyez sur l'icône de flèche vers le bas en regard des informations de la pièce jointe.
    
    ![Tap the down arrow next to an attachment to try to save it.](../../media/b22573bb-91ce-455f-84fa-8feb2846b117.png)
  
    Vous verrez impossible **d’enregistrer sur l’appareil** en bas de l’écran. 
    
    ![Warning text that indicates cannot save a file locally to an Android.](../../media/52ca3f3d-7ed0-4a52-9621-4872da6ea9c5.png)
  
    > [!NOTE]
    > L'enregistrement dans OneDrive Entreprise n'est pas activé pour Android pour le moment. C'est pourquoi la seule chose affichée est le message indiquant que l'enregistrement local est bloqué. 
  
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Confirmer le fonctionnement du paramètre Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office

Dans  le volet Modifier  la stratégie, sélectionnez Modifier en plus du contrôle d’accès aux **documents Office,** développez Gérer la façon dont les utilisateurs accèdent aux fichiers **Office** sur les appareils mobiles et assurez-vous que demander aux utilisateurs de se connecter à nouveau une fois que les applications **Office** ont été inactives est définie sur un certain nombre de minutes. Cette valeur est de 30 minutes par défaut. 
  
1. Sur l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis entrez un code confidentiel si nécessaire.
    
2. Vous devez maintenant voir la boîte de réception d'Outlook. Ne touchez pas à l'appareil Android pendant au moins 30 minutes (ou toute autre durée supérieure à celle que vous avez spécifiée dans la stratégie). L'appareil va probablement se mettre en veille.
    
3. Accédez Outlook à nouveau sur l’appareil Android.
    
4. Vous serez invité à entrer votre code confidentiel avant de pouvoir Outlook à nouveau.
    
### <a name="validate-protect-work-files-with-encryption"></a>Confirmer le fonctionnement du paramètre Chiffrer les fichiers professionnels pour les protéger

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Chiffrer les fichiers professionnels pour les protéger** est **activée** et que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **désactivée**.
  
1. Sur l’appareil Android de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis entrez un code confidentiel si nécessaire.
    
2. Ouvrez un e-mail contenant quelques pièces jointes de fichier image.
    
3. Appuyez sur l'icône de flèche vers le bas en regard des informations de la pièce jointe pour enregistrer cette dernière.
    
    ![Tap the down arrow to save the figure file to the Android device.](../../media/08a9e21e-4022-45d5-acff-59cface651e7.png)
  
4. Il se peut que vous soyez invité à autoriser Outlook à accéder aux photos, éléments multimédia et fichiers enregistrés sur votre appareil. Appuyez sur **Autoriser**.
    
5. En bas de l'écran, sélectionnez **Enregistrer sur l'appareil**, puis ouvrez l'application **Galerie**. 
    
6. Vous devriez voir une photo chiffrée (ou plusieurs si vous avez enregistré plusieurs pièces jointes de fichiers images) dans la liste. Elle peut figurer dans la liste Photos sous la forme d'un carré gris avec un point d'exclamation blanc dans un cercle blanc au centre du carré gris.
    
    ![An encrypted image file in the Gallery app.](../../media/25936414-bd7e-421d-824e-6e59b877722d.png)
  
## <a name="ios"></a>iOS
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Vérifier que les paramètres de protection des applications fonctionnent sur les appareils de l'utilisateur

Une fois que vous avez [défini des configurations d'application pour les appareils iOS](app-protection-settings-for-android-and-ios.md) afin de protéger les applications, vous pouvez suivre cette procédure pour confirmer que les paramètres sélectionnés fonctionnent bien. 
  
Tout d’abord, assurez-vous que la stratégie s’applique à l’application dans laquelle vous allez la valider.
  
1. Dans le centre [Microsoft 365 Business Premium' administration,](https://admin.microsoft.com)allez à  \> **Stratégies modifier la stratégie.**
    
2. Choisissez **une stratégie d’application pour iOS** pour les paramètres que vous avez créés lors de l’installation, ou une autre stratégie que vous avez créée, et vérifiez qu’elle est appliquée pour Outlook par exemple. 
    
    ![Shows all the apps for which this policy protects files.](../../media/842441b8-e7b1-4b86-9edd-d94d1f77b6f4.png)
  
### <a name="validate-require-a-pin-to-access-office-apps"></a>Confirmer le fonctionnement du paramètre Exiger un code confidentiel pour accéder aux applications Office

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Contrôle de l'accès aux documents Office**, développez **Gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et assurez-vous que l'option **Exiger un code confidentiel ou une empreinte pour accéder aux applications Office** est **activée**.
  
![Assurez-vous que la fonction Exiger un code confidentiel ou une empreinte digitale pour accéder Office applications est définie sur On.](../../media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Sur l’appareil iOS de l’utilisateur, Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur.
    
2. Vous serez également invité à entrer un code confidentiel ou à utiliser une empreinte digitale.
    
    ![Enter a PIN on your IOS device to access Office apps.](../../media/06fc5cf3-9f19-4090-b23c-14bb59805b7a.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Confirmer le fonctionnement du paramètre Réinitialiser le code confidentiel après un certain nombre d'échecs successifs

In the **Edit policy** pane, choose **Edit** next to Office documents **access control,** expand **Manage how users access Office files on mobile devices**, and make sure that **Reset PIN after number of failed attempts** is set to some number. Il s’agit de 5 par défaut. 
  
1. Sur l’appareil iOS de l’utilisateur, Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur.
    
2. Entrez un code confidentiel incorrect autant de fois que le spécifie la stratégie. Vous verrez une invite qui indique que la limite de tentative de code confidentiel **est atteinte** pour réinitialiser le code confidentiel. 
    
    ![After too many incorrect PIN attempts, you need to reset your PIN.](../../media/fab5c089-a4a5-4e8d-8c95-b8eed1dfa262.png)
  
3. Appuyez sur **OK**. Vous serez invité à vous inscrire avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis à définir un nouveau code confidentiel.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Confirmer le fonctionnement du paramètre Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **activée**.
  
![Verify that Force users to save all work files to OneDrive for Business is set to On.](../../media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis entrez un code confidentiel si nécessaire.
    
2. Ouvrez un e-mail qui contient une pièce jointe, ouvrez la pièce jointe et sélectionnez **Enregistrer** au bas de l'écran. 
    
    ![Tap the Save option after you open an attachment to try to save it.](../../media/b419b070-1530-4f14-86a8-8d89933a2b25.png)
  
3. Seule une option pour OneDrive Entreprise devrait être affichée. Si ce n’est pas le cas, appuyez **sur** Ajouter un **OneDrive Entreprise** l’écran **Ajouter Stockage compte.** Fournissez la demande de l’utilisateur Microsoft 365 Business Premium se connecte lorsque vous y êtes invité. 
    
    Appuyez sur **Enregistrer** et sélectionnez **OneDrive Entreprise**.
    
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Confirmer le fonctionnement du paramètre Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office

Dans  le volet Modifier  la stratégie, sélectionnez Modifier en plus du contrôle d’accès aux **documents Office,** développez Gérer la façon dont les utilisateurs accèdent aux fichiers **Office** sur les appareils mobiles et assurez-vous que demander aux utilisateurs de se connecter à nouveau une fois que les applications **Office** ont été inactives est définie sur un certain nombre de minutes. Cette valeur est de 30 minutes par défaut. 
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis entrez un code confidentiel si nécessaire.
    
2. Vous devez maintenant voir la boîte de réception d'Outlook. Ne touchez pas à l'appareil iOS pendant au moins 30 minutes (ou toute autre durée supérieure à celle que vous avez spécifiée dans la stratégie). L'appareil va probablement se mettre en veille.
    
3. Accédez Outlook à nouveau sur l’appareil iOS.
    
4. Vous serez invité à entrer votre code confidentiel avant de pouvoir Outlook à nouveau.
    
### <a name="validate-protect-work-files-with-encryption"></a>Confirmer le fonctionnement du paramètre Chiffrer les fichiers professionnels pour les protéger

Dans le volet **Modifier une stratégie**, sélectionnez **Modifier** en regard de **Se prémunir contre la perte ou le vol d'appareils**, développez **Protéger les fichiers professionnels en cas de perte ou de vol des appareils** et vérifiez que l'option **Chiffrer les fichiers professionnels pour les protéger** est **activée** et que l'option **Obliger les utilisateurs à enregistrer tous les fichiers professionnels dans OneDrive Entreprise** est **désactivée**.
  
1. Sur l’appareil iOS de l’utilisateur, ouvrez Outlook et connectez-vous avec les informations d’identification Microsoft 365 Business Premium utilisateur, puis entrez un code confidentiel si nécessaire.
    
2. Ouvrez un e-mail contenant quelques pièces jointes de fichier image.
    
3. Appuyez sur la pièce jointe, puis sur l'option **Enregistrer** en dessous. 
    
4. Ouvrez l'application **Photos** à partir de l'écran d'accueil. Vous devriez voir une photo (ou plusieurs si vous avez enregistré plusieurs pièces jointes de fichiers images) enregistrée, mais chiffrée. 
    
---

