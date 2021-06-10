---
title: Application Guard pour les Office 365 administrateurs
keywords: protection de l’application, protection, isolation, conteneur isolé, isolation matérielle
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Obtenez la dernière version de l’isolation matérielle. Empêcher les attaques actuelles et émergentes telles que les attaques ou les liens malveillants de perturber la productivité des employés et la sécurité de l’entreprise.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d0fa6ad884c6b21457c8359cf82e32e4b8c100ba
ms.sourcegitcommit: 7ebed5810480d7c49f8ca03207b5ea84993d253f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51488310"
---
# <a name="application-guard-for-office-for-admins"></a>Application Guard pour les Office administrateurs

**S’applique à :** Word, Excel et PowerPoint pour Microsoft 365, Windows 10 Entreprise

Protection d’application Microsoft Defender for Office (Application Guard pour Office) permet d’empêcher les fichiers non fiables d’accéder aux ressources de confiance, afin de préserver la sécurité de votre entreprise contre les attaques nouvelles et émergentes. Cet article présente aux administrateurs la configuration des appareils pour un aperçu d’Application Guard pour Office. Il fournit des informations sur la demande système et les étapes d’installation pour activer Application Guard Office sur un appareil.

## <a name="prerequisites"></a>Configuration requise

### <a name="minimum-hardware-requirements"></a>Configuration matérielle minimum requise

* **Processeur**: 64 bits, 4 cœurs (physiques ou virtuels), extensions de virtualisation (Intel VT-x OR AMD-V), core i5 équivalent ou supérieur recommandé
* **Mémoire physique**: 8 Go de RAM
* **Disque dur**: 10 Go d’espace libre sur le lecteur système (SSD recommandé)

### <a name="minimum-software-requirements"></a>Configuration logicielle minimale requise

* **Windows 10**: Windows 10 Entreprise, build client version 2004 (20H1) build 19041 ou ultérieure
* **Office**: Office Canal actuel et Canal Enterprise mensuel, build version 2011 16.0.13530.10000 ou ultérieure. Les versions 32 bits et 64 bits de Office sont toutes deux pris en charge.
* **Package de mise à** jour : Windows 10 de sécurité mensuelle cumulative [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Pour obtenir des informations détaillées sur la demande système requise, [reportez-vous à la](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard)Protection d’application Microsoft Defender . Consultez également les guides du fabricant de votre ordinateur sur la façon d’activer la technologie de virtualisation.
Pour en savoir plus sur Office canaux de mise à jour, voir [Vue d’ensemble](/deployoffice/overview-update-channels)des canaux de mise à jour Microsoft 365 .

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

* Microsoft 365 E5 ou Microsoft 365 E5 Sécurité

## <a name="deploy-application-guard-for-office"></a>Déployer Application Guard pour Office

### <a name="enable-application-guard-for-office"></a>Activer Application Guard pour Office

1. Téléchargez et installez Windows 10 mises à jour de sécurité **mensuelles cumulatives KB4571756**.

2. Sélectionnez **Protection d’application Microsoft Defender** sous Windows fonctionnalités et sélectionnez **OK.** L’activation de la fonctionnalité Application Guard demande un redémarrage du système. Vous pouvez choisir de redémarrer maintenant ou après l’étape 3.

   ![Windows Boîte de dialogue Fonctionnalités affichant AG](../../media/ag03-deploy.png)

   La fonctionnalité peut également être activée en exécutant la commande PowerShell suivante en tant qu’administrateur :

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Recherchez **Protection d’application Microsoft Defender en mode** géré , une stratégie de groupe dans les modèles d’administration de configuration ordinateur Windows **\\ \\ composants \\ Protection d’application Microsoft Defender**. Pour activer cette stratégie, vous pouvez définir la valeur sous Options **sur 2** ou **3,** puis sélectionner **OK** ou **Appliquer.**

   ![Activer la gestion des ag en mode géré](../../media/ag04-deploy.png)

   Au lieu de cela, vous pouvez définir la stratégie CSP correspondante :

   > OMA-URI : **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Paramètres/AllowWindowsDefenderApplicationGuard** <br> Type de données : **Integer** <br> Valeur : **2**

4. Redémarrez le système.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Définir les diagnostics & commentaires pour envoyer des données complètes

> [!NOTE]
> Toutefois, cela n’est pas obligatoire, la configuration des données de diagnostic facultatives permet de diagnostiquer les problèmes signalés.

Cette étape garantit que les données nécessaires pour identifier et résoudre les problèmes atteignent Microsoft. Pour activer les diagnostics sur votre appareil Windows, suivez les étapes ci-après :

1. Ouvrez **Paramètres** à partir du menu Démarrer.

   ![Menu Démarrer](../../media/ag05-diagnostic.png)

2. Sur **Windows Paramètres,** sélectionnez **Confidentialité.**

   ![Windows Paramètres menu](../../media/ag06-diagnostic.png)

3. Sous Confidentialité, sélectionnez **Diagnostics & commentaires** et **sélectionnez Données de diagnostic facultatives.**

   ![Menu Diagnostics et commentaires](../../media/ag07a-diagnostic.png)

Pour plus d’informations sur la Windows paramètres de diagnostic, reportez-vous à [La Windows données de diagnostic dans votre organisation.](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Vérifier qu’Application Guard pour Office est activé et fonctionne

Avant de confirmer qu’Application Guard pour Office est activé, lancez Word, Excel ou PowerPoint sur un appareil sur lequel les stratégies ont été déployées. Assurez-vous Office est activé. Vous devrez peut-être utiliser votre identité de travail pour activer le Office produit.

Pour confirmer qu’Application Guard pour Office est activé, lancez Word, Excel ou PowerPoint, puis ouvrez un document nontrus. Par exemple, vous pouvez ouvrir un document téléchargé à partir d’Internet ou une pièce jointe provenant d’une personne extérieure à votre organisation.

Lorsque vous ouvrez un fichier nontrus pour la première fois, vous pouvez voir un écran de Office comme dans l’exemple suivant. Il peut s’afficher pendant un certain temps pendant qu’Application Guard Office est activé et que le fichier est ouvert. Les ouvertures suivantes de fichiers nontrus doivent être plus rapides.

![application Office écran de splash](../../media/ag08-confirm.png)

À l’ouverture, le fichier doit afficher quelques indicateurs visuels qui ont montré que le fichier a été ouvert à l’intérieur d’Application Guard pour Office :

* Une callout dans le ruban

  ![Fichier de document affichant une note App Guard de petite taille](../../media/ag09-confirm.png)

* Icône d’application avec un bouclier dans la barre des tâches

  ![Icône dans la barre des tâches](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Configurer Application Guard pour Office

Office prend en charge les stratégies suivantes pour vous permettre de configurer les fonctionnalités d’Application Guard pour Office. Ces stratégies peuvent être configurées par le biais de stratégies de groupe ou via [Office service de stratégie cloud.](/DeployOffice/overview-office-cloud-policy-service)
Pour voir la configuration définie par votre administrateur, consultez les paramètres de stratégie de groupe dans modèles d’administration de configuration utilisateur **\\ Microsoft Office \\ 2016 \\ Security Paramètres Trust Center Application \\ \\ Guard**.


> [!NOTE]
> La configuration de ces stratégies peut désactiver certaines fonctionnalités pour les fichiers ouverts dans Application Guard Office.

|Stratégie|Description|
|---|---|
|N’utilisez pas Application Guard pour Office|L’activation de cette stratégie force Word, Excel et PowerPoint à utiliser le conteneur d’isolation en affichage protégé au lieu d’Application Guard pour Office. Cette stratégie peut être utilisée pour désactiver temporairement Application Guard pour les Office en cas de problèmes de laisser ce dernier activé pour Microsoft Edge.|
|Configurer Application Guard pour la pré Office pré-création d’un conteneur|Cette stratégie détermine si le conteneur Application Guard pour Office, pour isoler les fichiers nontrus, est pré-créé pour améliorer les performances d’exécution. Si vous activez ce paramètre, vous pouvez spécifier le nombre de jours pour continuer la pré-création d’un conteneur ou permettre au Office pré-créer le conteneur heuristique intégré.
|N’autorisez pas le copier-coller pour Office documents ouverts dans Application Guard Office|L’activation de cette stratégie empêche un utilisateur de copier et coller du contenu à partir d’un document ouvert dans Application Guard pour Office vers un document ouvert en dehors de celui-ci.|
|Désactiver l’accélération matérielle dans Application Guard pour Office|Cette stratégie contrôle si Application Guard pour Office utilise l’accélération matérielle pour restituer les graphiques. Si vous activez ce paramètre, Application Guard pour Office utilise le rendu logiciel (CPU) et ne charge aucun pilote graphique tiers ni n’interagit avec du matériel graphique connecté.
|Désactiver la protection des types de fichiers non pris en Office|Cette stratégie contrôle si Application Guard pour Office bloquera l’ouverture des types de fichiers non pris en Office ou s’il activera la redirection vers le affichage protégé.
|Désactiver l’accès à la caméra et au microphone pour les documents ouverts dans Application Guard Office|L’activation de cette stratégie Office accès à la caméra et au microphone à l’intérieur d’Application Guard Office.|
|Restreindre l’impression à partir de documents ouverts dans Application Guard Office|L’activation de cette stratégie limite les imprimantes sur qui un utilisateur peut imprimer à partir d’un fichier ouvert dans Application Guard Office. Par exemple, vous pouvez utiliser cette stratégie pour restreindre les utilisateurs à imprimer uniquement au format PDF.|
|Empêcher les utilisateurs de supprimer Application Guard pour Office protection contre les fichiers|L’activation de cette stratégie supprime l’option (dans l’expérience d’application Office) de désactiver Application Guard pour la protection Office ou d’ouvrir un fichier en dehors d’Application Guard pour Office. <p> **Remarque :** Les utilisateurs peuvent toujours contourner cette stratégie en supprimant manuellement la propriété mark-of-the-web du fichier ou en déplaçant un document vers un emplacement approuvé.|
|

> [!NOTE]
> Les stratégies suivantes exigent que l’utilisateur se connecte et se connecte à nouveau Windows pour prendre effet :
>
> * Désactiver la copie/coller pour les documents ouverts dans Application Guard Office
> * Restreindre l’impression des documents ouverts dans Application Guard Office
> * Désactiver l’accès à la caméra et au micro pour les documents ouverts dans Application Guard Office

## <a name="submit-feedback"></a>Envoyer les commentaires

### <a name="submit-feedback-via-feedback-hub"></a>Envoyer des commentaires via le Hub de commentaires

Si vous rencontrez des problèmes lors du lancement d’Application Guard pour Office, nous vous encourageons à envoyer vos commentaires via le Hub de commentaires :

1. Ouvrez **l’application Hub de commentaires** et connectez-vous.

2. Si vous obtenez une boîte de dialogue d’erreur lors du lancement d’Application Guard, sélectionnez Rapport à **Microsoft** dans la boîte de dialogue d’erreur pour démarrer une nouvelle soumission de commentaires. Dans le cas contraire, accédez à la catégorie correcte pour Application Guard, puis sélectionnez Ajouter un nouveau <https://aka.ms/mdagoffice-fb> **+ &nbsp; commentaire** en haut à droite.

3. Entrez un résumé dans la **zone Récapitulatif de vos** commentaires s’il n’est pas déjà rempli pour vous.

4. Entrez une description détaillée du problème que vous avez connu  et les étapes que vous avez prises dans la zone Expliquer plus en détail, puis sélectionnez **Suivant**.

5. Sélectionnez la bulle en de côté du **problème.** Assurez-vous que la catégorie sélectionnée est Sécurité et confidentialité **\> Protection d’application Microsoft Defender - Office**, puis sélectionnez **Suivant**.

6. Sélectionnez **Nouveau commentaire,** puis **Suivant**.

7. Collectez des suivis sur le problème :

   1. Développez la **vignette Recréer mon** problème.

   2. Si le problème que vous rencontrez se produit pendant l’exécution d’Application Guard, ouvrez une instance d’Application Guard. L’ouverture d’une instance permet de collecter des traces supplémentaires à partir du conteneur Application Guard.

   3. Sélectionnez **Démarrer l’enregistrement** et attendez que la vignette cesse de tourner et dites *Arrêter l’enregistrement.*

   4. Reproduisez entièrement le problème avec Application Guard. La reproduction peut inclure la tentative de lancement d’une instance d’Application Guard et l’attente de son échec, ou la reproduction d’un problème dans une instance d’Application Guard en cours d’exécution.

   5. Sélectionnez la **vignette Arrêter l’enregistrement.**

   6. Gardez toutes les instances Application Guard en cours d’exécution ouvertes, même pendant quelques minutes après l’envoi, afin que les diagnostics de conteneur soient également collectés.

8. Joignez les captures d’écran pertinentes ou les fichiers associés au problème.

9. Sélectionnez **Envoyer**.

### <a name="submit-feedback-via-office-customer-voice"></a>Envoyer des commentaires via Office Customer Voice

Vous pouvez également envoyer des commentaires à partir de Office si le problème survient lorsque Office documents sont ouverts dans Application Guard. Reportez-vous [au manuel Office Insider pour](https://insider.office.com/handbook) envoyer vos commentaires.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Intégration à Microsoft Defender pour Point de terminaison et Microsoft Defender pour Office 365

Application Guard pour Office est intégré à Microsoft Defender for Endpoint pour fournir une surveillance et une alerte sur les activités malveillantes qui se produisent dans l’environnement isolé.

[La fonctionnalité Documents sécurisés dans Microsoft E365 E5](/microsoft-365/security/office-365-security/safe-docs) utilise Microsoft Defender pour point de terminaison pour analyser les documents ouverts dans Application Guard Office. Pour une couche de protection supplémentaire, les utilisateurs ne peuvent pas quitter Application Guard Office tant que les résultats de l’analyse n’ont pas été déterminés.

Microsoft Defender pour point de terminaison est une plateforme de sécurité conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Pour plus d’informations sur cette plateforme, voir [Microsoft Defender pour Endpoint.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp) Pour en savoir plus sur l’intégration d’appareils à cette plateforme, voir Appareils intégrés au [service Microsoft Defender for Endpoint.](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure)

Vous pouvez également configurer Microsoft Defender pour que Office 365 fonctionne avec Defender for Endpoint. Pour plus d’informations, reportez-vous à [Intégrer Defender pour Office 365 avec Microsoft Defender pour endpoint.](integrate-office-365-ti-with-mde.md)

## <a name="limitations-and-considerations"></a>Limitations et considérations

* Application Guard pour Office est un mode protégé qui isole les documents non fiables afin qu’ils ne peuvent pas accéder aux ressources d’entreprise, à un intranet, à l’identité de l’utilisateur et aux fichiers arbitraires sur l’ordinateur. Par conséquent, si un utilisateur tente d’accéder à une fonctionnalité qui dépend de cet accès (par exemple, l’insertion d’une image à partir d’un fichier local sur le disque), l’accès échoue et produit une invite comme dans l’exemple suivant. Pour permettre à un document non approuvé d’accéder à des ressources fiables, les utilisateurs doivent supprimer la protection Application Guard du document.

  ![Boîte de dialogue qui vous aide à assurer la sécurité, cette fonctionnalité n’est pas disponible](../../media/ag10-limitations.png)

  > [!NOTE]
  > Conseillez aux utilisateurs de supprimer la protection uniquement s’ils font confiance au fichier et à sa source ou à leur origine.

* Le contenu actif dans les documents tels que les macros et ActiveX contrôles de contenu sont désactivés dans Application Guard pour Office. Les utilisateurs doivent supprimer la protection Application Guard pour activer le contenu actif.

* Les fichiers nontrus provenant de partages réseau ou les fichiers partagés à partir de OneDrive, OneDrive Entreprise ou SharePoint Online d’une autre organisation s’ouvrent en lecture seule dans Application Guard. Les utilisateurs peuvent enregistrer une copie locale de ces fichiers pour continuer à travailler dans le conteneur ou supprimer la protection pour travailler directement avec le fichier d’origine.

* Les fichiers protégés par la Gestion des droits numériques (IRM) sont bloqués par défaut. Si les utilisateurs souhaitent ouvrir ces fichiers en affichage protégé, un administrateur doit configurer les paramètres de stratégie pour les types de fichiers non pris en compte pour l’organisation.

* Toutes les personnalisations Office applications dans Application Guard pour Office ne sont pas persistantes une fois qu’un utilisateur s’est démarré et qu’il s’est connecté à nouveau ou après le redémarrage de l’appareil.

* Seuls les outils d’accessibilité qui utilisent l’infrastructure UIA peuvent fournir une expérience accessible pour les fichiers ouverts dans Application Guard Office.

* La connectivité réseau est requise pour le premier lancement d’Application Guard après l’installation. La connectivité est requise pour qu’Application Guard valide la licence.

* Dans la section d’informations du document, la propriété *Last Modified By* peut afficher **WDAGUtilityAccount** en tant qu’utilisateur. WDAGUtilityAccount est l’utilisateur anonyme configuré dans Application Guard. L’identité de l’utilisateur de bureau n’est pas partagée dans le conteneur Application Guard.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Optimisation des performances pour Application Guard pour Office

Cette section fournit une vue d’ensemble des optimisations des performances utilisées dans Application Guard pour Office. Ces informations peuvent aider les administrateurs à diagnostiquer les rapports des utilisateurs liés aux performances de Office ou du système global lorsque Application Guard est activé.

Application Guard utilise un conteneur virtualisé pour isoler les documents nontrus du système. Le processus de création d’un conteneur et de configuration du conteneur Application Guard pour ouvrir des documents Office a une surcharge de performances qui peut avoir une incidence négative sur l’expérience utilisateur lorsque les utilisateurs ouvrent un document nontrus.

Pour fournir aux utilisateurs l’expérience d’ouverture de fichier attendue, Application Guard utilise la logique pour pré-créer un conteneur lorsque l’heuristique suivante est rencontrée sur un système : un utilisateur a ouvert un fichier en affichage protégé ou en application Guard au cours des 28 derniers jours.

Lorsque cette heuristique est remplie, Office pré-crée un conteneur Application Guard pour l’utilisateur une fois qu’il s’est Windows. Alors que cette opération de pré-création est en cours, le système peut connaître des performances lentes, mais l’effet est résolu dès que l’opération se termine.

> [!NOTE]
> Les conseils nécessaires à l’heuristique pour pré-créer le conteneur sont générés par les applications Office qu’un utilisateur les utilise. Si un utilisateur installe Office sur un nouveau système où Application Guard est activé, Office ne pré-crée pas le conteneur avant la première ouverture d’un document nontrus sur le système. L’utilisateur observe que l’ouverture de ce premier fichier dans Application Guard est plus longue.

## <a name="known-issues"></a>Problèmes connus

* La sélection de liens web `http` (ou `https` ) n’ouvre pas le navigateur.
* Le contenu rtf (Rich Text Format) ou les images dans Office documents ouverts avec Application Guard ne sont pas pris en charge pour le moment.
* Le paramètre par défaut de la stratégie de protection des types de fichiers non pris en charge consiste à bloquer l’ouverture des types de fichiers non pris en charge non pris en charge par la Gestion des droits de l’information (IRM), CSV ou HTML.
* Les mises à jour de .NET peuvent entraîner l’échec de l’ouverture des fichiers dans Application Guard. Pour contourner ce cas de défaillance, les utilisateurs peuvent redémarrer leur appareil. En savoir plus sur le problème lors de la réception d’un message d’erreur lors de la tentative d’ouverture Protection d’application Windows Defender [ou Windows bac à sable](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
