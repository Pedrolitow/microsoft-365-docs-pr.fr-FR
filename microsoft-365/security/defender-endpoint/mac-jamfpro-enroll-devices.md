---
title: Inscrire Microsoft Defender pour endpoint sur les appareils macOS dans Jamf Pro
description: Inscrire Microsoft Defender pour endpoint sur les appareils macOS dans Jamf Pro
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, mac, installation, déployer, désinstallation, intune, jamfpro, macos, magasin, mojave, high sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 207c1334f91ecd22385ce281b3f10763afe57810
ms.sourcegitcommit: 6a73f0f0c0360fc015d9c0d0af26fb6926d9477d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2021
ms.locfileid: "58747374"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>Inscrire Microsoft Defender pour endpoint sur les appareils macOS dans Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="enroll-macos-devices"></a>Inscrire des appareils macOS

Il existe plusieurs méthodes pour être inscrit à JamF.

Cet article vous guide sur deux méthodes :

- [Méthode 1 : Invitations à l’inscription](#enrollment-method-1-enrollment-invitations)
- [Méthode 2 : Pré-étape des inscriptions](#enrollment-method-2-prestage-enrollments)

Pour obtenir la liste complète, voir [à propos de l’inscription de l’ordinateur.](https://docs.jamf.com/9.9/casper-suite/administrator-guide/About_Computer_Enrollment.html)

## <a name="enrollment-method-1-enrollment-invitations"></a>Méthode d’inscription 1 : invitations à l’inscription

1. Dans le tableau de bord Pro Jamf, accédez aux **invitations d’inscription.**

    ![Image des paramètres de configuration1.](images/a347307458d6a9bbfa88df7dbe15398f.png)

2. Sélectionnez **+ Nouveau**.

    ![Close up of a logo Description automatically generated.](images/b6c7ad56d50f497c38fc14c1e315456c.png)

3. Dans **Spécifier les destinataires de l'>** sous **Adresses** de messagerie, entrez l’adresse de messagerie des destinataires.

    ![Image des paramètres de configuration2.](images/718b9d609f9f77c8b13ba88c4c0abe5d.png)

    ![Image des paramètres de configuration3.](images/ae3597247b6bc7c5347cf56ab1e820c0.png)

    Par exemple : janedoe@contoso.com

    ![Image des paramètres de configuration4.](images/4922c0fcdde4c7f73242b13bf5e35c19.png)

4. Configurez le message pour l’invitation.

    ![Image des paramètres de configuration5.](images/ce580aec080512d44a37ff8e82e5c2ac.png)

    ![Image des paramètres de configuration6.](images/5856b765a6ce677caacb130ca36b1a62.png)

    ![Image des paramètres de configuration7.](images/3ced5383a6be788486d89d407d042f28.png)

    ![Image des paramètres de configuration8.](images/54be9c6ed5b24cebe628dc3cd9ca4089.png)

## <a name="enrollment-method-2-prestage-enrollments"></a>Enrollment Method 2: Prestage Enrollments

1. Dans le tableau de bord Pro Jamf, accédez à **Pré-étapes d’inscription.**

    ![Image des paramètres de configuration9.](images/6fd0cb2bbb0e60a623829c91fd0826ab.png)

2. Suivez les instructions dans [Computer PreStage Enrollments](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>Inscrire un appareil macOS

1. Sélectionnez **Continuer** et installez le certificat d’ac à partir d’une **fenêtre Préférences système.**

    ![Image de Jamf Pro enrollment1.](images/jamfpro-ca-certificate.png)

2. Une fois le certificat d’ac installé, revenir à la fenêtre du navigateur, puis **sélectionnez Continuer** et installer le profil MDM.

    ![Image de Jamf Pro enrollment2.](images/jamfpro-install-mdm-profile.png)

3. Sélectionnez **Autoriser** les téléchargements à partir de JAMF.

    ![Image de Jamf Pro enrollment3.](images/jamfpro-download.png)

4. Sélectionnez **Continuer** pour poursuivre l’installation du profil MDM.

    ![Image de Jamf Pro enrollment4.](images/jamfpro-install-mdm.png)

5. Sélectionnez **Continuer** à installer le profil MDM.

    ![Image de Jamf Pro enrollment5.](images/jamfpro-mdm-unverified.png)

6. Sélectionnez **Continuer**  pour terminer la configuration.

    ![Image de Jamf Pro enrollment6.](images/jamfpro-mdm-profile.png)
