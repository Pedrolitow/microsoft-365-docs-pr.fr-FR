---
title: Intégrer des appareils à Microsoft Defender pour entreprises
description: Découvrez comment intégrer des appareils à Defender pour Les Entreprises afin de protéger vos appareils dès le premier jour.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 11/01/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365solution-mdb-setup
- highpri
- tier1
ms.openlocfilehash: 553dc3143d7cd01c48200097a3ba60b054ba5da8
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805033"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Intégrer des appareils à Microsoft Defender pour entreprises

Intégrez vos appareils professionnels pour les protéger immédiatement. Vous pouvez choisir parmi plusieurs options pour intégrer les appareils de votre entreprise. Cet article vous guide tout au long de vos options et décrit le fonctionnement de l’intégration.

## <a name="what-to-do"></a>Procédure

1. Sélectionnez un onglet : 
   - **Windows 10 et 11**
   - **Mac**
   - **Serveurs** (NOUVEAU ! Windows Server ou Linux Server)
   - **Mobile** (pour les appareils iOS/iPadOS ou Android)
2. Affichez vos options d’intégration et suivez les instructions de l’onglet sélectionné.
3. Passez aux étapes suivantes.

## <a name="windows-10-and-11"></a>[**Windows 10 et 11**](#tab/Windows10and11)

## <a name="windows-10-and-11"></a>Windows 10 et 11

Choisissez l'une des options suivantes pour intégrer des appareils clients Windows à Defender pour entreprises :

- [Script local](#local-script-for-windows-10-and-11) (pour l’intégration manuelle des appareils dans le portail Microsoft 365 Defender)
- [stratégie de groupe](#group-policy-for-windows-10-and-11) (si vous utilisez déjà stratégie de groupe dans votre organisation)
- [Microsoft Intune](#intune-for-windows-10-and-11) (si vous utilisez déjà Intune)

### <a name="local-script-for-windows-10-and-11"></a>Script local pour Windows 10 et 11

Vous pouvez utiliser un script local pour intégrer des appareils clients Windows. Lorsque vous exécutez le script d’intégration sur un appareil, il crée une approbation avec Azure Active Directory, si cette approbation n’existe pas déjà . inscrit l’appareil dans Microsoft Intune, s’il n’est pas déjà inscrit, puis l’intègre à Defender pour les entreprises. Si vous n’utilisez pas actuellement Intune, la méthode de script local est la méthode d’intégration recommandée pour les clients Defender entreprise.

> [!TIP]
> Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois lorsque vous utilisez la méthode de script local.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez **Windows 10 et 11**, puis, dans la section **Méthode de déploiement**, choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

5. Sur un appareil Windows, extrayez le contenu du package de configuration vers un emplacement, tel que le dossier Desktop. Vous devez avoir un fichier nommé `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. Ouvrez une invite de commandes en tant qu’administrateur.

7. Tapez l’emplacement du fichier de script. Par exemple, si vous avez copié le fichier dans le dossier Desktop, tapez `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`, puis appuyez sur la touche Entrée (ou sélectionnez **OK**).

8. Une fois le script exécuté, [exécutez un test de détection](#run-a-detection-test-on-a-windows-10-or-11-device).

### <a name="group-policy-for-windows-10-and-11"></a>stratégie de groupe pour Windows 10 et 11

Si vous préférez utiliser stratégie de groupe pour intégrer des clients Windows, suivez les instructions fournies dans [Intégrer des appareils Windows à l’aide de stratégie de groupe](../defender-endpoint/configure-endpoints-gp.md). Cet article décrit les étapes d’intégration à Microsoft Defender pour point de terminaison. Les étapes d’intégration à Defender for Business sont similaires.

### <a name="intune-for-windows-10-and-11"></a>Intune pour Windows 10 et 11

Vous pouvez intégrer des clients Windows et d’autres appareils dans Intune à l’aide du Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Plusieurs méthodes sont disponibles pour inscrire des appareils dans Intune. Nous vous recommandons d’utiliser l’une des méthodes suivantes :

- [Activer l’inscription automatique Windows pour les appareils appartenant à l’entreprise ou gérés par l’entreprise](#enable-automatic-enrollment-for-windows-10-and-11)
- [Demandez aux utilisateurs d’inscrire leurs propres appareils Windows 10/11 dans Intune](#ask-users-to-enroll-their-windows-10-and-11-devices)

#### <a name="enable-automatic-enrollment-for-windows-10-and-11"></a>Activer l’inscription automatique pour Windows 10 et 11

Lorsque vous configurez l’inscription automatique, les utilisateurs ajoutent leur compte professionnel à l’appareil. En arrière-plan, l’appareil s’inscrit et rejoint Azure Active Directory (Azure AD) et est inscrit dans Intune.

1. Accédez à la Portail Azure ([https://portal.azure.com/](https://portal.azure.com/)) et connectez-vous.

2. Sélectionnez **Azure Active Directory** > **Mobility (MDM et GAM)** >  **Microsoft Intune**.

3. Configurez **l’étendue utilisateur MDM** et **l’étendue utilisateur GAM**.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="Capture d’écran de la définition de l’étendue utilisateur MDM et de l’étendue utilisateur GAM dans Intune.":::

   - Pour l’étendue utilisateur MDM, nous vous recommandons de sélectionner **Tout** afin que tous les utilisateurs puissent inscrire automatiquement leurs appareils Windows.
   - Dans la section Étendue de l’utilisateur GAM, nous vous recommandons les valeurs par défaut suivantes pour les URL :

       - **URL des conditions d’utilisation de la gestion des données de référence**
       - **URL de détection MDM**
       - **URL de conformité GAM**

4. Sélectionnez **Enregistrer**.

5. Une fois qu’un appareil est inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils dans Defender entreprise. [En savoir plus sur les groupes d’appareils dans Defender pour les entreprises](mdb-create-edit-device-groups.md).

> [!TIP]
> Pour plus d’informations, consultez [Activer l’inscription automatique Windows](/mem/intune/enrollment/windows-enroll).

#### <a name="ask-users-to-enroll-their-windows-10-and-11-devices"></a>Demander aux utilisateurs d’inscrire leurs Windows 10 et 11 appareils

1. Regardez la vidéo suivante pour voir le fonctionnement de l’inscription :<br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. Partagez cet article avec les utilisateurs de votre organisation : [Inscrire des appareils Windows 10/11 dans Intune](/mem/intune/user-help/enroll-windows-10-device).

3. Une fois qu’un appareil est inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils dans Defender entreprise. [En savoir plus sur les groupes d’appareils dans Defender pour les entreprises](mdb-create-edit-device-groups.md).

### <a name="run-a-detection-test-on-a-windows-10-or-11-device"></a>Exécuter un test de détection sur un appareil Windows 10 ou 11

Une fois que vous avez intégré des appareils Windows à Defender entreprise, vous pouvez exécuter un test de détection sur l’appareil pour vous assurer que tout fonctionne correctement.

1. Sur l’appareil Windows, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre d’invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécutée, la fenêtre d’invite de commandes se ferme automatiquement. En cas de réussite, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour l’appareil nouvellement intégré dans environ 10 minutes.

## <a name="view-the-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender pour les entreprises, accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Dans le volet de navigation, accédez à **Ressources** > **Appareils**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet correspondant à ces appareils ([Windows 10 et 11, Mac, Serveurs ou Appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration des appareils, passez à [l’Étape 5 : Configurer vos paramètres et stratégies de sécurité dans Defender pour les entreprises](mdb-configure-security-settings.md)
- Consultez [Prise en main de Defender pour les entreprises](mdb-get-started.md).

## <a name="mac"></a>[**Mac**](#tab/mac)

## <a name="mac"></a>Mac

> [!NOTE]
> Nous vous recommandons d’utiliser un [script local pour intégrer Mac](#local-script-for-mac). Bien que vous puissiez [configurer l’inscription pour Mac à l’aide de Intune](/mem/intune/enrollment/macos-enroll), le script local est la méthode la plus simple pour intégrer Mac à Defender pour Les Entreprises. 

Choisissez l'une des options suivantes pour le Mac embarqué :

- [Script local pour Mac](#local-script-for-mac) (*recommandé*)
- [Intune pour Mac](#intune-for-mac) (si vous utilisez déjà Intune)

### <a name="local-script-for-mac"></a>Script local pour Mac

Lorsque vous exécutez le script local sur Mac : 

- Il crée une approbation avec Azure Active Directory si cette approbation n’existe pas déjà.
- Il inscrit le Mac dans Microsoft Intune s’il n’est pas déjà inscrit, puis intègre le Mac à Defender entreprise. 
- Nous vous recommandons d’intégrer jusqu’à 10 appareils à la fois à l’aide de cette méthode.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez **macOS**. Dans la section **Méthode de déploiement** , choisissez **Script local**. 

4. Sélectionnez **Télécharger le package d’intégration** et enregistrez-le sur un lecteur amovible. Sélectionnez également **Télécharger le package d’installation** et enregistrez-le sur votre appareil amovible.

5. Sur Mac, enregistrez le package d’installation sous dans `wdav.pkg` un répertoire local.

6. Enregistrez le package d’intégration dans `WindowsDefenderATPOnboardingPackage.zip` le répertoire que vous avez utilisé pour le package d’installation.

7. Utilisez finder pour accéder à `wdav.pkg` votre enregistrement, puis ouvrez-le.

8. Sélectionnez **Continuer**, acceptez les termes du contrat de licence, puis entrez votre mot de passe lorsque vous y êtes invité.

9. Vous serez invité à autoriser l’installation d’un pilote à partir de Microsoft (soit « L’extension système est bloquée », soit « L’installation est en attente », ou les deux). Vous devez autoriser l’installation du pilote : sélectionnez **Ouvrir les préférences de sécurité** ou **Ouvrir les préférences** >  système **Sécurité & Confidentialité**, puis sélectionnez **Autoriser**.

10. Utilisez la commande Python suivante dans Bash pour exécuter le package d’intégration : `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.sh`

Une fois que Mac est inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Defender pour les entreprises](mdb-create-edit-device-groups.md).

### <a name="intune-for-mac"></a>Intune pour Mac

Si vous avez déjà Intune, vous pouvez inscrire des ordinateurs Mac à l’aide du Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Plusieurs méthodes sont disponibles pour inscrire Mac dans Intune. Nous vous recommandons l’une des méthodes suivantes :

- [Choisir une option pour mac appartenant à l’entreprise](#options-for-company-owned-mac)
- [Demander aux utilisateurs d’inscrire leur propre Mac dans Intune](#ask-users-to-enroll-their-own-mac-in-intune)

#### <a name="options-for-company-owned-mac"></a>Options pour Mac appartenant à l’entreprise

Choisissez l’une des options suivantes pour inscrire des appareils Mac gérés par l’entreprise dans Intune :

| Option  | Description  |
|---------|---------|
| Inscription d’appareils automatisée Apple |  Utilisez cette méthode pour automatiser l’inscription sur les appareils achetés via Apple Business Manager ou Apple School Manager. L’inscription automatisée des appareils déploie le profil d’inscription « over the air », de sorte que vous n’avez pas besoin d’avoir un accès physique aux appareils. <br/><br/>Consultez [Inscrire automatiquement un Mac avec Apple Business Manager ou Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| Gestionnaire d’inscription d’appareil (DEM)  |  Utilisez cette méthode pour les déploiements à grande échelle et lorsque plusieurs personnes de votre organisation peuvent vous aider à configurer l’inscription. Une personne disposant des droits de gestionnaire d'inscription de l'appareil (DEM) peut inscrire jusqu'à 1 000 appareils avec un seul compte Azure Active Directory. Cette méthode utilise l'application Company Portal ou l'application Microsoft Intune pour inscrire les appareils. Vous ne pouvez pas utiliser un compte DEM pour inscrire des appareils via l'inscription automatique des appareils.<br/><br/> Consultez [Inscrire des appareils dans Intune à l’aide d’un compte de gestionnaire d’inscription d’appareil](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| Inscription directe  | L’inscription directe inscrit les appareils sans affinité utilisateur. Cette méthode est donc idéale pour les appareils qui ne sont pas associés à un seul utilisateur. Cette méthode exige que vous ayez un accès physique aux Macs que vous inscrivez. <br/><br/>Consultez [Utiliser l’inscription directe pour Mac](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-mac-in-intune"></a>Demander aux utilisateurs d’inscrire leur propre Mac dans Intune

Si votre entreprise préfère que les utilisateurs inscrivent leurs propres appareils dans Intune, indiquez aux utilisateurs de suivre ces étapes :

1. Accédez au site web Portail d'entreprise ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)) et connectez-vous.

2. Suivez les instructions du site web Portail d'entreprise pour ajouter leur appareil.

3. Installez l’application Portail d'entreprise à l’adresse [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac), puis suivez les instructions de l’application.

### <a name="confirm-that-a-mac-is-onboarded"></a>Vérifier qu’un Mac est intégré

1. Pour vérifier que l’appareil est associé à votre entreprise, utilisez la commande Python suivante dans Bash :

   `mdatp health --field org_id`.

2. Si vous utilisez macOS 10.15 (Catalina) ou une version ultérieure, accordez à Defender pour entreprise le consentement pour protéger votre appareil. Accédez à **Préférences** >  système **Sécurité & Confidentialité** >  >  Confidentialité **Accès complet au disque**. Sélectionnez l’icône de verrou en bas de la boîte de dialogue pour apporter des modifications, puis sélectionnez **Microsoft Defender pour entreprises** (ou **Defender pour point de terminaison**, si c’est ce que vous voyez).

3. Pour vérifier que l’appareil est intégré, utilisez la commande suivante dans Bash :

   `mdatp health --field real_time_protection_enabled`

Une fois qu’un appareil est inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Defender pour les entreprises](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender pour les entreprises, accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Dans le volet de navigation, accédez à **Ressources** > **Appareils**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet correspondant à ces appareils ([Windows 10 et 11, Mac, Serveurs ou Appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration des appareils, passez à [l’Étape 5 : Configurer vos paramètres et stratégies de sécurité dans Defender pour les entreprises](mdb-configure-security-settings.md).
- Consultez [Prise en main de Defender pour les entreprises](mdb-get-started.md).

## <a name="servers"></a>[**Servers**](#tab/Servers)

## <a name="servers"></a>Serveurs

> [!NOTE]
> Si vous envisagez d’intégrer une instance de Windows Server ou Linux Server, vous aurez besoin d’une licence supplémentaire, par exemple [Microsoft Defender pour entreprises serveurs](get-defender-business-servers.md). Vous pouvez également utiliser [Microsoft Defender pour les serveurs](/azure/defender-for-cloud/defender-for-servers-introduction). Toutefois, votre expérience Defender entreprise peut changer lorsque vous ajoutez un plan d’entreprise, tel que Defender pour les serveurs Plan 1 ou Plan 2. Pour en savoir plus, consultez [Que se passe-t-il si j’ai une combinaison d’abonnements de sécurité de point de terminaison Microsoft ?](mdb-faq.yml#what-happens-if-i-have-a-mix-of-microsoft-endpoint-security-subscriptions).

Choisissez le système d’exploitation pour votre serveur :

- [Windows Server](#windows-server)
- [Serveur Linux](#linux-server)

## <a name="windows-server"></a>Windows Server

> [!IMPORTANT]
> Veillez à respecter les exigences suivantes avant d’intégrer un point de terminaison Windows Server :
> - Vous disposez d’une licence de serveurs Microsoft Defender pour entreprises. (Voir [Comment obtenir des serveurs Microsoft Defender pour entreprises](get-defender-business-servers.md).)
> - L’étendue de mise en œuvre de Windows Server est activée. Accédez à **Paramètres** > **points de terminaison** > **la gestion de la configuration** > **l’étendue application**. Sélectionnez **Utiliser MDE pour appliquer les paramètres de configuration de sécurité à partir de MEM**, sélectionnez  **Windows Server**, puis **sélectionnez Enregistrer**.

Vous pouvez intégrer une instance de Windows Server à Defender pour les entreprises à l’aide d’un script local.

### <a name="local-script-for-windows-server"></a>Script local pour Windows Server

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** >  **Endpoints**, puis, sous **Gestion des appareils**, choisissez **Intégration**.

3. Sélectionnez un système d’exploitation, tel que **Windows Server 1803, 2019 et 2022**, puis, dans la section **Méthode de déploiement** , choisissez **Script local**. 

   Si vous sélectionnez **Windows Server 2012 R2 et 2016**, vous avez deux packages à télécharger et à exécuter : un package d’installation et un package d’intégration. Le package d’installation contient un fichier MSI qui installe l’agent Defender for Business. Le package d’intégration contient le script permettant d’intégrer votre point de terminaison Windows Server à Defender entreprise.

4. Sélectionnez **Télécharger le package d’intégration**. Nous vous recommandons d’enregistrer le package d’intégration sur un lecteur amovible.

   Si vous avez sélectionné **Windows Server 2012 R2 et 2016**, sélectionnez également **Télécharger le package d’installation**, puis enregistrez le package sur un lecteur amovible.

5. Sur votre point de terminaison Windows Server, extrayez le contenu du package d’installation/intégration à un emplacement tel que le dossier Desktop. Vous devez avoir un fichier nommé `WindowsDefenderATPLocalOnboardingScript.cmd`. 

   Si vous intégrez Windows Server 2012 R2 ou Windows Server 2016, extrayez d’abord le package d’installation.

6. Ouvrez une invite de commandes en tant qu’administrateur.

7. Si vous intégrez Windows Server 2012R2 ou Windows Server 2016, exécutez la commande suivante :

   `Msiexec /i md4ws.msi /quiet` 

   Si vous intégrez Windows Server 1803, 2019 ou 2022, ignorez cette étape et passez à l’étape 8.

8. Tapez l’emplacement du fichier de script. Par exemple, si vous avez copié le fichier dans le dossier Desktop, tapez `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`, puis appuyez sur Entrée (ou sélectionnez **OK**).

9. Accédez à [Exécuter un test de détection sur Windows Server](#run-a-detection-test-on-windows-server).

### <a name="run-a-detection-test-on-windows-server"></a>Exécuter un test de détection sur Windows Server

Après avoir intégré votre point de terminaison Windows Server à Defender pour Entreprises, vous pouvez exécuter un test de détection pour vous assurer que tout fonctionne correctement :

1. Sur l’appareil Windows Server, créez un dossier : `C:\test-MDATP-test`.

2. Ouvrez une fenêtre d’invite de commandes en tant qu’administrateur.

3. Dans la fenêtre d’invite de commandes, exécutez la commande PowerShell suivante :

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Une fois la commande exécutée, la fenêtre d’invite de commandes se ferme automatiquement. En cas de réussite, le test de détection est marqué comme terminé et une nouvelle alerte s’affiche dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) pour l’appareil nouvellement intégré dans environ 10 minutes.

## <a name="linux-server"></a>Serveur Linux

> [!IMPORTANT]
> Veillez à respecter les exigences suivantes avant d’intégrer un point de terminaison de serveur Linux :
> - Vous disposez d’une licence de serveurs Microsoft Defender pour entreprises. (Voir [Comment obtenir des serveurs Microsoft Defender pour entreprises](get-defender-business-servers.md).)
> - Vous remplissez les [conditions préalables pour Microsoft Defender pour point de terminaison sur Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).

### <a name="onboard-linux-server-endpoints"></a>Intégrer des points de terminaison de serveur Linux

Vous pouvez utiliser les méthodes suivantes pour intégrer une instance de Linux Server à Defender for Business :

- **Script local :** Consultez [Déployer manuellement Microsoft Defender pour point de terminaison sur Linux](../defender-endpoint/linux-install-manually.md).
- **Ansible:** Consultez [Déployer Microsoft Defender pour point de terminaison sur Linux avec Ansible](../defender-endpoint/linux-install-with-ansible.md).
- **Chef :** Consultez [Déployer Defender pour point de terminaison sur Linux avec Chef](../defender-endpoint/linux-deploy-defender-for-endpoint-with-chef.md).
- **Marionnette:** Consultez [Déployer Microsoft Defender pour point de terminaison sur Linux avec Puppet](../defender-endpoint/linux-install-with-puppet.md).

> [!NOTE]
> L’intégration d’une instance de Linux Server à Defender for Business est identique à l’intégration à [Microsoft Defender pour point de terminaison sur Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md).

## <a name="view-a-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender pour les entreprises, accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Dans le volet de navigation, accédez à **Ressources** > **Appareils**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet correspondant à ces appareils ([Windows 10 et 11, Mac, Serveurs ou Appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration des appareils, passez à [l’Étape 5 : Configurer vos paramètres et stratégies de sécurité dans Defender pour les entreprises](mdb-configure-security-settings.md).
- Consultez [Prise en main de Defender pour les entreprises](mdb-get-started.md).

## <a name="mobile-devices"></a>[**Appareils mobiles**](#tab/mobiles)

## <a name="mobile-devices"></a>Appareils mobiles

Utilisez Microsoft Intune pour intégrer des appareils mobiles, tels que des appareils Android et iOS/iPadOS. Voir les ressources suivantes pour obtenir de l'aide pour inscrire ces appareils dans Intune :

- [Inscrire des appareils Android](/mem/intune/enrollment/android-enroll)
- [Inscrire les appareils iOS ou iPadOS](/mem/intune/enrollment/ios-enroll)

Une fois qu’un appareil est inscrit dans Intune, vous pouvez l’ajouter à un groupe d’appareils. [En savoir plus sur les groupes d’appareils dans Defender pour les entreprises](mdb-create-edit-device-groups.md).

> [!NOTE]
> La version autonome de Defender for Business n’inclut pas la licence Intune requise pour intégrer des appareils iOS et Android. Vous pouvez ajouter Intune à votre abonnement Defender entreprise pour intégrer des appareils mobiles. Intune est inclus dans Microsoft 365 Business Premium.

## <a name="view-a-list-of-onboarded-devices"></a>Afficher la liste des appareils intégrés

Pour afficher la liste des appareils intégrés à Defender pour les entreprises, accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Dans le volet de navigation, accédez à **Ressources** > **Appareils**.

## <a name="next-steps"></a>Prochaines étapes

- Si vous avez d’autres appareils à intégrer, sélectionnez l’onglet correspondant à ces appareils ([Windows 10 et 11, Mac, Serveurs ou Appareils mobiles](#what-to-do)), puis suivez les instructions de cet onglet.
- Si vous avez terminé l’intégration des appareils, passez à [l’Étape 5 : Configurer vos paramètres et stratégies de sécurité dans Defender pour les entreprises](mdb-configure-security-settings.md).
- Consultez [Prise en main de Defender pour les entreprises](mdb-get-started.md).
