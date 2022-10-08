---
title: Déploiement manuel pour Microsoft Defender pour point de terminaison sur macOS
description: Installez Microsoft Defender pour point de terminaison manuellement sur macOS à partir de la ligne de commande.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 55325d10fd444d34664ed11c63effd7b4e8b6aff
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233747"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Déploiement manuel pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour un essai gratuit](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink).

Cette rubrique explique comment déployer manuellement Microsoft Defender pour point de terminaison sur macOS. Un déploiement réussi nécessite l’achèvement de toutes les étapes suivantes :

- [Télécharger les packages d’installation et d’intégration](#download-installation-and-onboarding-packages)
- [Installation de l’application (macOS 10.15)](#application-installation-macos-1015)
- [Installation de l’application (macOS 11 et versions ultérieures)](#application-installation-macos-11-and-newer-versions)
- [Configuration du client](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Prérequis et configuration requise

Avant de commencer, consultez [la page principale Microsoft Defender pour point de terminaison sur macOS](microsoft-defender-endpoint-mac.md) pour obtenir une description des prérequis et de la configuration système requise pour la version actuelle du logiciel.

## <a name="download-installation-and-onboarding-packages"></a>Télécharger les packages d’installation et d’intégration

Téléchargez les packages d’installation et d’intégration à partir du portail Microsoft 365 Defender :

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>, accédez à **Paramètres > Points de terminaison > Gestion des appareils > Intégration**.
2. Dans la section 1 de la page, définissez le système d’exploitation sur **macOS** et la méthode de déploiement sur **le script local**.
3. Dans la section 2 de la page, **sélectionnez Télécharger le package d’installation**. Enregistrez-le sous la forme wdav.pkg dans un répertoire local.
4. Dans la section 2 de la page, **sélectionnez Télécharger le package d’intégration**. Enregistrez-le en tant que WindowsDefenderATPOnboardingPackage.zip dans le même répertoire.

   :::image type="content" source="images/portal-onboarding-macos.png" alt-text="Options de téléchargement des packages d’installation et d’intégration" lightbox="images/portal-onboarding-macos.png":::

5. À partir d’une invite de commandes, vérifiez que vous disposez des deux fichiers.

## <a name="application-installation-macos-1015"></a>Installation de l’application (macOS 10.15)

Pour effectuer ce processus, vous devez disposer de privilèges d’administrateur sur l’appareil.

1. Accédez au fichier wdav.pkg téléchargé dans Finder et ouvrez-le.

   :::image type="content" source="images/mdatp-28-appinstall.png" alt-text="Installation de l’application" lightbox="images/mdatp-28-appinstall.png":::

2. Sélectionnez **Continuer**, acceptez les termes du contrat de licence et entrez le mot de passe lorsque vous y êtes invité.

   :::image type="content" source="images/mdatp-29-appinstalllogin.png" alt-text="Installation de l’application" lightbox="images/mdatp-29-appinstalllogin.png":::

   > [!IMPORTANT]
   > Vous serez invité à autoriser l’installation d’un pilote de Microsoft (« Extension système bloquée » ou « L’installation est en attente » ou les deux. Le pilote doit être autorisé à être installé.

     :::image type="content" source="images/mdatp-30-systemextension.png" alt-text="Installation de l’application" lightbox="images/mdatp-30-systemextension.png":::

3. Sélectionnez **Ouvrir les préférences de sécurité** ou **ouvrir les préférences système > sécurité & confidentialité**. Sélectionnez **Autoriser** :

   :::image type="content" source="images/mdatp-31-securityprivacysettings.png" alt-text="Fenêtre Sécurité et confidentialité" lightbox="images/mdatp-31-securityprivacysettings.png":::

   L’installation se poursuit.

   > [!CAUTION]
   > Si vous ne sélectionnez pas **Autoriser**, l’installation se poursuit au bout de 5 minutes. Microsoft Defender pour point de terminaison seront chargées, mais certaines fonctionnalités, telles que la protection en temps réel, seront désactivées. Pour plus d’informations sur la façon de résoudre ce problème, consultez [Résolution des problèmes d’extension de noyau](mac-support-kext.md) .

> [!NOTE]
> macOS peut demander le redémarrage de l’appareil lors de la première installation de Microsoft Defender pour point de terminaison. La protection en temps réel ne sera pas disponible tant que l’appareil n’est pas redémarré.

## <a name="application-installation-macos-11-and-newer-versions"></a>Installation de l’application (macOS 11 et versions ultérieures)

Pour effectuer ce processus, vous devez disposer de privilèges d’administrateur sur l’appareil.

1. Accédez au fichier wdav.pkg téléchargé dans Finder et ouvrez-le.

   :::image type="content" source="images/monterey-install-1.png" alt-text="Processus d’installation de l’application" lightbox="images/monterey-install-1.png":::

2. Sélectionnez **Continuer**, acceptez les termes du contrat de licence et entrez le mot de passe lorsque vous y êtes invité.

3. À la fin du processus d’installation, vous serez promu pour approuver les extensions système utilisées par le produit. Sélectionnez **Ouvrir les préférences de sécurité**.

   :::image type="content" source="images/monterey-install-2.png" alt-text="Approbation de l’extension système" lightbox="images/monterey-install-2.png":::

4. Dans la fenêtre **Sécurité & Confidentialité** , sélectionnez **Autoriser**.

   :::image type="content" source="images/monterey-install-3.png" alt-text="Préférences de sécurité des extensions système1" lightbox="images/monterey-install-3.png":::

5. Répétez les étapes 3 & 4 pour toutes les extensions système distribuées avec Microsoft Defender pour point de terminaison sur Mac.

6. Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender pour point de terminaison sur Mac inspecte le trafic de socket et signale ces informations au portail Microsoft 365 Defender. Lorsque vous êtes invité à accorder Microsoft Defender pour point de terminaison autorisations pour filtrer le trafic réseau, sélectionnez **Autoriser**.

   :::image type="content" source="images/monterey-install-4.png" alt-text="Préférences de sécurité des extensions système2" lightbox="images/monterey-install-4.png":::

7. Ouvrez La sécurité **des préférences** \> système **& la confidentialité** et accédez à l’onglet **Confidentialité**. Accordez l’autorisation d’accès au **disque complet** à **Microsoft Defender** et **à l’extension de sécurité du point de terminaison Microsoft Defenders**.

   :::image type="content" source="images/monterey-install-5.png" alt-text="Accès au disque complet" lightbox="images/monterey-install-5.png":::

## <a name="client-configuration"></a>Configuration du client

1. Copiez wdav.pkg et MicrosoftDefenderATPOnboardingMacOs.sh sur l’appareil sur lequel vous déployez Microsoft Defender pour point de terminaison sur macOS.

    L’appareil client n’est pas associé à org_id. Notez que l’attribut *org_id* est vide.

    ```bash
    mdatp health --field org_id
    ```

2. Exécutez le script Bash pour installer le fichier de configuration :

    ```bash
    Sudo bash -x MicrosoftDefenderATPOnboardingMacOs.sh
    ```

3. Vérifiez que l’appareil est maintenant associé à votre organisation et indique un ID d’organisation valide :

    ```bash
    mdatp health --field org_id
    ```

    Après l’installation, vous verrez l’icône Microsoft Defender dans la barre d’état macOS en haut à droite.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Icône Microsoft Defender dans la barre d’état" lightbox="images/mdatp-icon-bar.png":::

## <a name="how-to-allow-full-disk-access"></a>Comment autoriser l’accès au disque complet

> [!CAUTION]
> macOS 10.15 (Catalina) contient de nouvelles améliorations en matière de sécurité et de confidentialité. À compter de cette version, par défaut, les applications ne peuvent pas accéder à certains emplacements sur le disque (tels que Documents, Téléchargements, Bureau, etc.) sans consentement explicite. En l’absence de ce consentement, Microsoft Defender pour point de terminaison ne peut pas protéger entièrement votre appareil.

1. Pour accorder le consentement, ouvrez La sécurité **des préférences** \> système & **l’accès complet au disque** de **confidentialité de la confidentialité** \>  \>. Cliquez sur l’icône de verrouillage pour apporter des modifications (en bas de la boîte de dialogue). Sélectionnez Microsoft Defender pour point de terminaison.

2. Exécutez un test de détection AV pour vérifier que l’appareil est correctement intégré et signaler au service. Effectuez les étapes suivantes sur l’appareil nouvellement intégré :

    1. Assurez-vous que la protection en temps réel est activée (indiquée par le résultat 1 de l’exécution de la commande suivante) :

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. Ouvrez une fenêtre Terminal. Copiez et exécutez la commande suivante :

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. Le fichier doit avoir été mis en quarantaine par Defender pour point de terminaison sur Mac. Utilisez la commande suivante pour répertorier toutes les menaces détectées :

        ```bash
        mdatp threat list
        ```

3. Exécutez un test de détection EDR pour vérifier que l’appareil est correctement intégré et signaler au service. Effectuez les étapes suivantes sur l’appareil nouvellement intégré :

   1. Dans votre navigateur, tel que Microsoft Edge pour Mac ou Safari.

   1. Téléchargez les DIY.zip MacOS MDATP à partir de https://aka.ms/mdatpmacosdiy et extrayez-les.

      Vous pouvez être invité à :

      > Voulez-vous autoriser les téléchargements sur « mdatpclientanalyzer.blob.core.windows.net » ?<br/>
      > Vous pouvez modifier les sites web qui peuvent télécharger des fichiers dans Les préférences des sites web.

4. Cliquez sur **Autoriser**.

5. Ouvrez **Téléchargements**.

6. Vous devriez voir **MDATP MacOS DIY**.

   > [!TIP]
   > Si vous double-cliquez, le message suivant s’affiche :
   >
   > > **« MDATP MacOS DIY » ne peut pas être ouvert, car le développeur ne peut pas être vérificateur.**<br/>
   > > macOS ne peut pas vérifier que cette application est exempte de programmes malveillants.<br/>
   > > **\[Passer à l’annulation de la corbeille\]** **\[\]**

7. Cliquez sur **Annuler**.

8. Cliquez avec le bouton droit sur **MDATP MacOS DIY**, puis cliquez sur **Ouvrir**.

    Le système doit afficher le message suivant :

    > **macOS ne peut pas vérifier le développeur de MDATP MacOS DIY. Êtes-vous sûr de vouloir l’ouvrir ?**<br/>
    > En ouvrant cette application, vous remplacerez la sécurité système qui peut exposer votre ordinateur et vos informations personnelles à des programmes malveillants susceptibles de nuire à votre Mac ou de compromettre votre confidentialité.

9. Cliquez sur **Ouvrir**. 

    Le système doit afficher le message suivant :

    > Microsoft Defender pour point de terminaison - fichier de test macOS EDR DIY<br/>
    > L’alerte correspondante sera disponible dans le portail MDATP.

10. Cliquez sur **Ouvrir**. 

    Dans quelques minutes, une alerte nommée « macOS EDR Test Alert » doit être déclenchée.

11. Accédez au portail Microsoft 365 Defender (https://security.microsoft.com/).

12. Accédez à la file d’attente des alertes.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="Alerte de test EDR macOS qui affiche la gravité, la catégorie, la source de détection et un menu réduit d’actions" lightbox="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png":::

    Examinez les détails de l’alerte et la chronologie de l’appareil, puis effectuez les étapes d’investigation régulières.

## <a name="logging-installation-issues"></a>Problèmes d’installation de la journalisation

Consultez [les problèmes d’installation](mac-resources.md#logging-installation-issues) de journalisation pour plus d’informations sur la façon de trouver le journal généré automatiquement qui est créé par le programme d’installation lorsqu’une erreur se produit.

## <a name="uninstallation"></a>Désinstallation

Pour plus d’informations sur la suppression de Microsoft Defender pour point de terminaison sur macOS sur les appareils clients, consultez [Désinstallation](mac-resources.md#uninstalling).
