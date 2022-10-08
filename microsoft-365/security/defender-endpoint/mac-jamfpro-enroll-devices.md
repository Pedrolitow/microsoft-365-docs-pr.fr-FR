---
title: Inscrire Microsoft Defender pour point de terminaison sur des appareils macOS dans Jamf Pro
description: Inscrire Microsoft Defender pour point de terminaison sur des appareils macOS dans Jamf Pro
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: c4e10dc812b90d9e2eb025855617787cbf685957
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68225413"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>Inscrire Microsoft Defender pour point de terminaison sur des appareils macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="enroll-macos-devices"></a>Inscrire des appareils macOS

Il existe plusieurs méthodes d’inscription à JamF.

Cet article vous guidera sur deux méthodes :

- [Méthode 1 : Invitations d’inscription](#enrollment-method-1-enrollment-invitations)
- [Méthode 2 : Inscriptions préalables](#enrollment-method-2-prestage-enrollments)

Pour obtenir la liste complète, consultez [À propos de l’inscription de l’ordinateur](https://docs.jamf.com/9.9/casper-suite/administrator-guide/About_Computer_Enrollment.html).

## <a name="enrollment-method-1-enrollment-invitations"></a>Méthode d’inscription 1 : Invitations d’inscription

1. Dans le tableau de bord Jamf Pro, **accédez aux invitations d’inscription**.

   :::image type="content" source="images/a347307458d6a9bbfa88df7dbe15398f.png" alt-text="Paramètres de configuration1" lightbox="images/a347307458d6a9bbfa88df7dbe15398f.png":::

2. Sélectionnez **+ Nouveau**.

   :::image type="content" source="images/b6c7ad56d50f497c38fc14c1e315456c.png" alt-text="Gros plan d’une description de logo générée automatiquement" lightbox="images/b6c7ad56d50f497c38fc14c1e315456c.png":::

3. Dans **Spécifier les destinataires de la > d’invitation** sous **Email Adresses**, entrez les adresses e-mail des destinataires.

    :::image type="content" source="images/718b9d609f9f77c8b13ba88c4c0abe5d.png" alt-text="Paramètres de configuration2" lightbox="images/718b9d609f9f77c8b13ba88c4c0abe5d.png":::

    :::image type="content" source="images/ae3597247b6bc7c5347cf56ab1e820c0.png" alt-text="Paramètres de configuration3" lightbox="images/ae3597247b6bc7c5347cf56ab1e820c0.png":::

    Par exemple : janedoe@contoso.com

    :::image type="content" source="images/4922c0fcdde4c7f73242b13bf5e35c19.png" alt-text="Paramètres de configuration4" lightbox="images/4922c0fcdde4c7f73242b13bf5e35c19.png":::

4. Configurez le message pour l’invitation.

   :::image type="content" source="images/ce580aec080512d44a37ff8e82e5c2ac.png" alt-text="Paramètres de configuration5" lightbox="images/ce580aec080512d44a37ff8e82e5c2ac.png":::

   :::image type="content" source="images/5856b765a6ce677caacb130ca36b1a62.png" alt-text="Paramètres de configuration6" lightbox="images/5856b765a6ce677caacb130ca36b1a62.png":::

   :::image type="content" source="images/3ced5383a6be788486d89d407d042f28.png" alt-text="Paramètres de configuration7" lightbox="images/3ced5383a6be788486d89d407d042f28.png":::

   :::image type="content" source="images/54be9c6ed5b24cebe628dc3cd9ca4089.png" alt-text="Paramètres de configuration8" lightbox="images/54be9c6ed5b24cebe628dc3cd9ca4089.png":::

## <a name="enrollment-method-2-prestage-enrollments"></a>Méthode d’inscription 2 : Inscriptions préliminaires

1. Dans le tableau de bord Jamf Pro, accédez aux **inscriptions en préconfiguration**.

   :::image type="content" source="images/6fd0cb2bbb0e60a623829c91fd0826ab.png" alt-text="Paramètres de configuration9" lightbox="images/6fd0cb2bbb0e60a623829c91fd0826ab.png":::

2. Suivez les instructions des [inscriptions de prédéfinissement de l’ordinateur](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>Inscrire un appareil macOS

1. Sélectionnez **Continuer** et installez le certificat d’autorité de certification à partir d’une fenêtre **Préférences système** .

   :::image type="content" source="images/jamfpro-ca-certificate.png" alt-text="Inscription Jamf Pro1" lightbox="images/jamfpro-ca-certificate.png":::

2. Une fois le certificat d’autorité de certification installé, revenez à la fenêtre du navigateur, puis **sélectionnez Continuer** et installer le profil GPM.

   :::image type="content" source="images/jamfpro-install-mdm-profile.png" alt-text="L’inscription Jamf Pro2" lightbox="images/jamfpro-install-mdm-profile.png":::

3. Sélectionnez **Autoriser** les téléchargements à partir de JAMF.

   :::image type="content" source="images/jamfpro-download.png" alt-text="L’inscription Jamf Pro 3" lightbox="images/jamfpro-download.png":::

4. Sélectionnez **Continuer** pour poursuivre l’installation du profil MDM.

   :::image type="content" source="images/jamfpro-install-mdm.png" alt-text="Inscription Jamf Pro4" lightbox="images/jamfpro-install-mdm.png":::

5. Sélectionnez **Continuer** pour installer le profil GPM.

   :::image type="content" source="images/jamfpro-mdm-unverified.png" alt-text="L’inscription Jamf Pro5" lightbox="images/jamfpro-mdm-unverified.png":::

6. Sélectionnez **Continuer**  pour terminer la configuration.

   :::image type="content" source="images/jamfpro-mdm-profile.png" alt-text="L’inscription Jamf Pro6" lightbox="images/jamfpro-mdm-profile.png":::
