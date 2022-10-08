---
title: Protection d'application pour Office pour les administrateurs
keywords: application guard, protection, isolation, conteneur isolé, isolation matérielle
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: m365-security
description: Obtenez la dernière version de l’isolation basée sur le matériel. Empêchez les attaques actuelles et émergentes telles que les attaques ou les liens malveillants de perturber la productivité des employés et la sécurité de l’entreprise.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 75404b9b58fe51fa76a1699b6db0eff7354930c2
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68082612"
---
# <a name="application-guard-for-office-for-admins"></a>Protection d'application pour Office pour les administrateurs

**S’applique à :** Applications Word, Excel et PowerPoint pour Microsoft 365, Windows 10 Entreprise, Windows 11 Entreprise

Protection d'application Microsoft Defender pour Office (Protection d'application pour Office) permet d’empêcher les fichiers non approuvés d’accéder aux ressources approuvées, ce qui protège votre entreprise contre les attaques nouvelles et émergentes. Cet article guide les administrateurs dans la configuration des appareils pour un aperçu de Protection d'application pour Office. Il fournit des informations sur la configuration système requise et les étapes d’installation pour activer Protection d'application pour Office sur un appareil.

## <a name="prerequisites"></a>Configuration requise

### <a name="minimum-hardware-requirements"></a>Configuration matérielle minimum requise

* **Processeur** : 64 bits, 4 cœurs (physiques ou virtuels), extensions de virtualisation (Intel VT-x OR AMD-V), core i5 équivalent ou supérieur recommandé
* **Mémoire physique** : 8 Go de RAM
* **Disque dur** : 10 Go d’espace libre sur le lecteur système (disque SSD recommandé)

### <a name="minimum-software-requirements"></a>Configuration logicielle minimale requise

* **Windows** : édition Windows 10 Entreprise, build client version 2004 (20H1) build 19041 ou ultérieure. Toutes les versions de Windows 11 sont prises en charge.
* **Office** : Microsoft 365 Apps avec la build 16.0.13530.10000 ou ultérieure. Pour les installations de canal actuel et de canal d’entreprise mensuel, cela équivaut à la version 2011. Pour Semi-Annual Enterprise Channel et Semi-Annual Enterprise Channel (préversion), la version minimale est 2108 ou ultérieure. Les versions 32 bits et 64 bits sont prises en charge.
* **Package de mise à jour** : Windows 10 mise à jour de sécurité mensuelle cumulative [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Pour obtenir une configuration système détaillée, reportez-vous à [la configuration requise pour Protection d'application Microsoft Defender](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). En outre, reportez-vous aux guides du fabricant de votre ordinateur sur la façon d’activer la technologie de virtualisation.
Pour en savoir plus sur Microsoft 365 Apps canaux de mise à jour, consultez [Vue d’ensemble des canaux de mise à jour pour Microsoft 365 Apps](/deployoffice/overview-update-channels).

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

* Microsoft 365 E5 Sécurité
* Microsoft 365 A5 pour les enseignants
* Microsoft 365 A5 pour les étudiants

> [!NOTE]
> Applications Microsoft 365 pour les grandes entreprises avec activation d’ordinateur partagé ou licences basées sur les appareils n’ont pas accès à Protection d'application pour Office.
>
> Les plans de licence documents sécurisés permettent d’accéder à Protection d'application pour Office. Pour plus d’informations, consultez [Documents sécurisés dans Microsoft 365 E5/A5](/microsoft-365/security/office-365-security/safe-docs).

## <a name="deploy-application-guard-for-office"></a>Déployer Protection d'application pour Office

### <a name="enable-application-guard-for-office"></a>Activer Protection d'application pour Office

1. Téléchargez et installez **Windows 10 mises à jour de sécurité mensuelles cumulatives KB4571756**.

2. Sélectionnez **Protection d'application Microsoft Defender** sous Fonctionnalités Windows, puis **sélectionnez OK**. L’activation de la fonctionnalité Protection d'application invite un redémarrage du système. Vous pouvez choisir de redémarrer maintenant ou après l’étape 3.

   :::image type="content" source="../../media/ag03-deploy.png" alt-text="Boîte de dialogue Fonctionnalités Windows affichant le groupe de disponibilité" lightbox="../../media/ag03-deploy.png":::

   La fonctionnalité peut également être activée en exécutant la commande PowerShell suivante en tant qu’administrateur :

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Recherchez **Protection d'application Microsoft Defender en mode managé**, une stratégie de groupe dans **les composants\\ Windows des\\modèles d’administration de configuration\\par ordinateur Protection d'application Microsoft Defender**. Activez cette stratégie en définissant la valeur sous Options **sur 2** ou **3**, puis en sélectionnant **OK** ou **Appliquer**.

   :::image type="content" source="../../media/ag04-deploy.png" alt-text="Option permettant d’activer le groupe de disponibilité en mode managé" lightbox="../../media/ag04-deploy.png":::

   Au lieu de cela, vous pouvez définir la stratégie CSP correspondante :

   > OMA-URI : **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Settings/AllowWindowsDefenderApplicationGuard** <br> Type de données : **Entier** <br> Valeur : **2**

4. Redémarrez le système.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Définir diagnostics & commentaires pour envoyer des données complètes

> [!NOTE]
> Toutefois, cela n’est pas obligatoire. Toutefois, la configuration des données de diagnostic facultatives permet de diagnostiquer les problèmes signalés.

Cette étape garantit que les données nécessaires pour identifier et résoudre les problèmes atteignent Microsoft. Procédez comme suit pour activer les diagnostics sur votre appareil Windows :

1. Ouvrez **Paramètres** dans le menu Démarrer.

   :::image type="content" source="../../media/ag05-diagnostic.png" alt-text="Menu Démarrer" lightbox="../../media/ag05-diagnostic.png":::

2. Dans **Paramètres Windows**, sélectionnez **Confidentialité**.

   :::image type="content" source="../../media/ag06-diagnostic.png" alt-text="Menu Paramètres Windows" lightbox="../../media/ag06-diagnostic.png":::

3. Sous Confidentialité, sélectionnez **Diagnostics & commentaires** et sélectionnez **Données de diagnostic facultatives**.

   :::image type="content" source="../../media/ag07a-diagnostic.png" alt-text="Menu Diagnostics et commentaires" lightbox="../../media/ag07a-diagnostic.png":::

Pour plus d’informations sur la configuration des paramètres de diagnostic Windows, reportez-vous à [La configuration des données de diagnostic Windows dans votre organisation](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Vérifier que Protection d'application pour Office est activé et fonctionne

Avant de confirmer que Protection d'application pour Office est activé, lancez Word, Excel ou PowerPoint sur un appareil sur lequel les stratégies ont été déployées. Vérifiez qu’Office est activé. Vous devrez peut-être d’abord utiliser votre identité professionnelle pour activer le produit Office.

Pour confirmer que Protection d'application pour Office est activé, lancez Word, Excel ou PowerPoint, puis ouvrez un document non approuvé. Par exemple, vous pouvez ouvrir un document téléchargé à partir d’Internet ou une pièce jointe d’une personne externe à votre organisation.

Lorsque vous ouvrez pour la première fois un fichier non approuvé, vous pouvez voir un écran de démarrage Office comme dans l’exemple suivant. Il peut s’afficher pendant un certain temps pendant que Protection d'application pour Office est en cours d’activation et que le fichier est ouvert. Les ouvertures suivantes de fichiers non approuvés doivent être plus rapides.

:::image type="content" source="../../media/ag08-confirm.png" alt-text="Page de démarrage de l’application Office" lightbox="../../media/ag08-confirm.png":::

Une fois ouvert, le fichier doit afficher quelques indicateurs visuels indiquant que le fichier a été ouvert dans Protection d'application pour Office :

* Légende dans le ruban

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Fichier doc montrant une petite note App Guard" lightbox="../../media/ag09-confirm.png":::

* Icône d’application avec un bouclier dans la barre des tâches

  ![Icône dans la barre des tâches.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Configurer Protection d'application pour Office

Office prend en charge les stratégies suivantes pour vous permettre de configurer les fonctionnalités de Protection d'application pour Office. Ces stratégies peuvent être configurées via des stratégies de groupe ou via le [service de stratégie cloud Office](/DeployOffice/overview-office-cloud-policy-service).

> [!NOTE]
> La configuration de ces stratégies peut désactiver certaines fonctionnalités pour les fichiers ouverts dans Protection d'application pour Office.

|Stratégie|Description|
|---|---|
|N’utilisez pas Protection d'application pour Office|L’activation de cette stratégie force Word, Excel et PowerPoint à utiliser le conteneur d’isolation en mode protégé au lieu de Protection d'application pour Office. Cette stratégie peut être utilisée pour désactiver temporairement Protection d'application pour Office en cas de problèmes lors de son activation pour Microsoft Edge.|
|Configurer Protection d'application pour la pré-création du conteneur Office|Cette stratégie détermine si le Protection d'application pour le conteneur Office, pour isoler les fichiers non approuvés, est précréé pour améliorer les performances d’exécution. Si vous activez ce paramètre, vous pouvez spécifier le nombre de jours pendant lesquels continuer la précréation d’un conteneur ou laisser le conteneur précréé intégré à Office créer le conteneur.
|N’autorisez pas le copier-coller pour les documents Office ouverts dans Protection d'application pour Office|L’activation de cette stratégie empêche un utilisateur de copier et coller du contenu d’un document ouvert dans Protection d'application pour Office vers un document ouvert en dehors de celui-ci.|
|Désactiver l’accélération matérielle dans Protection d'application pour Office|Cette stratégie contrôle si Protection d'application pour Office utilise l’accélération matérielle pour afficher des graphiques. Si vous activez ce paramètre, Protection d'application pour Office utilise le rendu basé sur les logiciels (UC) et ne charge pas de pilotes graphiques tiers ni n’interagit avec un matériel graphique connecté.
|Désactiver la protection des types de fichiers non pris en charge dans Protection d'application pour Office|Cette stratégie détermine si Protection d'application pour Office empêche l’ouverture des types de fichiers non pris en charge ou si elle active la redirection vers la vue protégée.
|Désactiver l’accès à la caméra et au microphone pour les documents ouverts dans Protection d'application pour Office|L’activation de cette stratégie supprimera l’accès Office à la caméra et au microphone à l’intérieur Protection d'application pour Office.|
|Restreindre l’impression à partir de documents ouverts dans Protection d'application pour Office|L’activation de cette stratégie limite les imprimantes auxquelles un utilisateur peut imprimer à partir d’un fichier ouvert dans Protection d'application pour Office. Par exemple, vous pouvez utiliser cette stratégie pour restreindre les utilisateurs à imprimer uniquement au format PDF.|
|Empêcher les utilisateurs de supprimer Protection d'application pour la protection Office sur les fichiers|L’activation de cette stratégie supprime l’option (dans l’expérience d’application Office) de désactiver Protection d'application pour la protection Office ou d’ouvrir un fichier en dehors de Protection d'application pour Office. <p> **Note:** Les utilisateurs peuvent toujours contourner cette stratégie en supprimant manuellement la propriété mark-of-the-web du fichier ou en déplaçant un document vers un emplacement approuvé.|

> [!NOTE]
> Les stratégies suivantes obligeront l’utilisateur à se déconnecter et à se reconnecter à Windows pour prendre effet :
>
> * Désactiver le copier-coller pour les documents ouverts dans Protection d'application pour Office
> * Restreindre l’impression des documents ouverts dans Protection d'application pour Office
> * Désactiver l’accès caméra et micro aux documents ouverts dans Protection d'application pour Office

## <a name="submit-feedback"></a>Envoyer les commentaires

### <a name="submit-feedback-via-feedback-hub"></a>Envoyer des commentaires via le Hub de commentaires

Si vous rencontrez des problèmes lors du lancement de Protection d'application pour Office, vous êtes invité à envoyer vos commentaires via le Hub de commentaires :

1. Ouvrez **l’application Hub de commentaires** et connectez-vous.

2. Si vous obtenez une boîte de dialogue d’erreur lors du lancement de Protection d'application, sélectionnez **Signaler à Microsoft** dans la boîte de dialogue d’erreur pour démarrer une nouvelle soumission de commentaires. Sinon, accédez à <https://aka.ms/mdagoffice-fb> la catégorie appropriée pour Protection d'application, puis sélectionnez **+&nbsp;Ajouter de nouveaux commentaires** en haut à droite.

3. Entrez un résumé dans la zone **Résumer vos commentaires** s’il n’est pas déjà renseigné pour vous.

4. Entrez une description détaillée du problème que vous avez rencontré et les étapes que vous avez effectuées dans la zone **Expliquer plus en détail** , puis sélectionnez **Suivant**.

5. Sélectionnez la bulle en regard de **Problème**. Vérifiez que la catégorie sélectionnée est **Sécurité et confidentialité \> Protection d'application Microsoft Defender – Office**, puis sélectionnez **Suivant**.

6. Sélectionnez **Nouveau commentaire**, puis **Suivant**.

7. Collectez des traces sur le problème :

   1. Développez la vignette **Recréer mon problème** .

   2. Si le problème que vous rencontrez se produit pendant que Protection d'application est en cours d’exécution, ouvrez une instance Protection d'application. L’ouverture d’une instance permet de collecter des traces supplémentaires à partir du conteneur Protection d'application.

   3. Sélectionnez **Démarrer l’enregistrement**, puis attendez que la vignette cesse de tourner et dites *Arrêter l’enregistrement*.

   4. Reproduisez entièrement le problème avec Protection d'application. La reproduction peut inclure la tentative de lancement d’une instance Protection d'application et l’attente jusqu’à ce qu’elle échoue, ou la reproduction d’un problème dans une instance de Protection d'application en cours d’exécution.

   5. Sélectionnez la vignette **Arrêter l’enregistrement** .

   6. Laissez les instances Protection d'application en cours d’exécution ouvertes, même quelques minutes après l’envoi, afin que les diagnostics de conteneur puissent également être collectés.

8. Joignez les captures d’écran ou fichiers pertinents liés au problème.

9. Sélectionnez **Envoyer**.

### <a name="submit-feedback-via-office-customer-voice"></a>Envoyer des commentaires via Office Customer Voice

Vous pouvez également envoyer des commentaires à partir d’Office si le problème se produit lorsque des documents Office sont ouverts dans Protection d'application. Reportez-vous au [Manuel Office Insider](https://insider.office.com/handbook) pour envoyer des commentaires.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Intégration avec Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365

Protection d'application pour Office est intégré à Microsoft Defender pour point de terminaison pour fournir une surveillance et des alertes sur les activités malveillantes qui se produisent dans l’environnement isolé.

[Documents sécurisés dans Microsoft E365 E5](/microsoft-365/security/office-365-security/safe-docs) est une fonctionnalité qui utilise Microsoft Defender pour point de terminaison pour analyser les documents ouverts dans Protection d'application pour Office. Pour une couche supplémentaire de protection, les utilisateurs ne peuvent pas quitter Protection d'application pour Office tant que les résultats de l’analyse n’ont pas été déterminés.

Microsoft Defender pour point de terminaison est une plateforme de sécurité conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Pour plus d’informations sur cette plateforme, consultez [Microsoft Defender pour point de terminaison](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). Pour en savoir plus sur l’intégration d’appareils à cette plateforme, consultez [Intégrer des appareils au service Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure).

Vous pouvez également configurer Microsoft Defender pour Office 365 pour qu’ils fonctionnent avec Defender pour point de terminaison. Pour plus d’informations, reportez-vous à [Intégrer Defender pour Office 365 à Microsoft Defender pour point de terminaison](integrate-office-365-ti-with-mde.md).

## <a name="limitations-and-considerations"></a>Limitations et considérations

* Protection d'application pour Office est un mode protégé qui isole les documents non approuvés afin qu’ils ne puissent pas accéder aux ressources d’entreprise approuvées, à un intranet, à l’identité de l’utilisateur et aux fichiers arbitraires sur l’ordinateur. Par conséquent, si un utilisateur tente d’accéder à une fonctionnalité qui a une dépendance vis-à-vis de cet accès, telle que l’insertion d’une image à partir d’un fichier local sur le disque, l’accès échoue et produit une invite qui ressemble à l’exemple suivant. Pour permettre à un document non approuvé d’accéder aux ressources approuvées, les utilisateurs doivent supprimer Protection d'application protection du document.

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Boîte de dialogue indiquant le message de sécurité et l’état de la fonctionnalité" lightbox="../../media/ag09-confirm.png":::

  > [!NOTE]
  > Conseillez aux utilisateurs de supprimer la protection uniquement s’ils approuvent le fichier et sa source ou l’endroit d’où il provient.

* Lorsqu’un document non approuvé est stocké dans un emplacement approuvé, l’approbation de l’emplacement est héritée par le document. En règle générale, le stockage cloud d’une organisation est identifié comme un emplacement approuvé.

* Le contenu actif dans les documents tels que les macros et les contrôles ActiveX est désactivé dans Protection d'application pour Office. Les utilisateurs doivent supprimer Protection d'application protection pour activer le contenu actif.

* Les fichiers non approuvés provenant de partages réseau ou de fichiers partagés à partir de OneDrive, OneDrive Entreprise ou SharePoint Online d’une autre organisation s’ouvrent en lecture seule dans Protection d'application. Les utilisateurs peuvent enregistrer une copie locale de ces fichiers pour continuer à travailler dans le conteneur ou supprimer la protection pour travailler directement avec le fichier d’origine.

* Les fichiers protégés par la Gestion des droits relatifs à l’information (IRM) sont bloqués par défaut. Si les utilisateurs souhaitent ouvrir ces fichiers en mode protégé, un administrateur doit configurer les paramètres de stratégie pour les types de fichiers non pris en charge pour l’organisation.

* Les personnalisations apportées aux applications Office dans Protection d'application pour Office ne sont pas conservées après qu’un utilisateur s’est déconnecté et s’est reconnecté ou après le redémarrage de l’appareil.

* Seuls les outils d’accessibilité qui utilisent l’infrastructure UIA peuvent fournir une expérience accessible pour les fichiers ouverts dans Protection d'application pour Office.

* La connectivité réseau est requise pour le premier lancement de Protection d'application après l’installation. La connectivité est requise pour que Protection d'application valide la licence.

* Dans la section d’informations du document, la propriété *Last Modified By* peut afficher **WDAGUtilityAccount** en tant qu’utilisateur. WDAGUtilityAccount est l’utilisateur anonyme configuré dans Protection d'application. L’identité de l’utilisateur de bureau n’est pas partagée dans le conteneur Protection d'application.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Optimisations des performances pour Protection d'application pour Office

Cette section fournit une vue d’ensemble des optimisations de performances utilisées dans Protection d'application pour Office. Ces informations peuvent aider les administrateurs à diagnostiquer les rapports des utilisateurs liés aux performances d’Office ou du système global lorsque Protection d'application est activé.

Protection d'application utilise un conteneur virtualisé pour isoler les documents non approuvés du système. Le processus de création d’un conteneur et de configuration du conteneur Protection d'application pour ouvrir des documents Office a une surcharge de performances qui peut affecter négativement l’expérience utilisateur lorsque les utilisateurs ouvrent un document non approuvé.

Pour fournir aux utilisateurs l’expérience d’ouverture de fichier attendue, Protection d'application utilise la logique pour précréer un conteneur lorsque l’heuristique suivante est remplie sur un système : un utilisateur a ouvert un fichier en mode protégé ou Protection d'application au cours des 28 derniers jours.

Lorsque cette heuristique est remplie, Office crée au préalable un conteneur Protection d'application pour l’utilisateur une fois qu’il se connecte à Windows. Pendant que cette opération de précréage est en cours, le système peut rencontrer des performances lentes, mais l’effet sera résolu dès que l’opération se termine.

> [!NOTE]
> Les indicateurs nécessaires à l’heuristique pour précréer le conteneur sont générés par les applications Office quand un utilisateur les utilise. Si un utilisateur installe Office sur un nouveau système sur lequel Protection d'application est activé, Office ne crée pas le conteneur avant la première ouverture d’un document non approuvé sur le système. L’utilisateur remarque que l’ouverture de ce premier fichier prend plus de temps dans Protection d'application.

## <a name="known-issues"></a>Problèmes connus

* La sélection de liens web (`http` ou `https`) n’ouvre pas le navigateur.
* Le paramètre par défaut de la stratégie de protection copier-coller consiste à activer l’accès du Presse-papiers au texte uniquement.
* Le paramètre par défaut pour la stratégie de protection des types de fichiers non pris en charge consiste à bloquer l’ouverture de types de fichiers non pris en charge non approuvés chiffrés ou dont la gestion des droits relatifs à l’information (IRM) est définie. Cela inclut les fichiers chiffrés à l’aide d’étiquettes de confidentialité de Protection des données Microsoft Purview.
* Les fichiers CSV et HTML ne sont pas pris en charge pour l’instant.
* Protection d'application pour Office ne fonctionne actuellement pas avec les volumes compressés NTFS. Si vous voyez une erreur « ERROR_VIRTUAL_DISK_LIMITATION », essayez de décompresser le volume.
* Mises à jour à .NET peut entraîner l’échec de l’ouverture des fichiers dans Protection d'application. En guise de solution de contournement, les utilisateurs peuvent redémarrer leur appareil lorsqu’ils rencontrent cet échec. En savoir plus sur le problème lors de la [réception d’un message d’erreur lors de la tentative d’ouverture de Windows Defender Protection d'application ou de Bac à sable Windows](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* Pour [plus d’informations, consultez Forum aux questions - Protection d'application Microsoft Defender.](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard)
