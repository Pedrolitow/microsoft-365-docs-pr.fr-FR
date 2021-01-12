---
title: Application Guard pour Office 365 (prévisualisation publique) pour les administrateurs
keywords: protection de l’application, protection, isolation, conteneur isolé, isolation matérielle
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Obtenez la dernière version de l’isolation matérielle. Empêcher les attaques actuelles et émergentes telles que les attaques ou les liens malveillants de perturber la productivité des employés et la sécurité de l’entreprise.
ms.openlocfilehash: f5a5feb14db75c5baccecf0c6afafe0c42517224
ms.sourcegitcommit: 9833f95ab6ab95aea20d68a277246dca2223f93d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49794507"
---
# <a name="application-guard-for-office-public-preview-for-admins"></a>Application Guard pour Office (prévisualisation publique) pour les administrateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**S’applique à :** Word, Excel et PowerPoint pour Microsoft 365, Windows 10 Entreprise

> [!IMPORTANT]
> Certaines informations concernent un produit pré-publié qui peut être considérablement modifié avant sa commercialisation. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft Defender Application Guard pour Office (Application Guard pour Office) permet d’empêcher les fichiers non fiables d’accéder aux ressources de confiance, afin de préserver la sécurité de votre entreprise contre les attaques nouvelles et émergentes. Cet article présente aux administrateurs la configuration des appareils pour un aperçu d’Application Guard pour Office. Il fournit des informations sur la exigences système et les étapes d’installation pour activer Application Guard pour Office sur un appareil.

## <a name="prerequisites"></a>Configuration requise

### <a name="minimum-hardware-requirements"></a>Configuration matérielle minimale requise

* **Processeur**: 64 bits, 4 cœurs (physiques ou virtuels), extensions de virtualisation (Intel VT-x OR AMD-V), core i5 équivalent ou supérieur recommandé
* **Mémoire physique**: 8 Go de RAM
* **Disque dur**: 10 Go d’espace libre sur le lecteur système (SSD recommandé)

### <a name="minimum-software-requirements"></a>Configuration logicielle minimale requise

* **Windows 10**: édition Windows 10 Entreprise, version 2004 (20H1) build 19041
* **Office**: version 2008 de la version bêta du canal Office 16.0.13212 ou version ultérieure
* **Package de mise à** jour : Mises à jour de sécurité mensuelles cumulatives Windows 10 [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Pour obtenir des informations détaillées sur la requise, reportez-vous à [la procédure système requise pour Microsoft Defender Application Guard.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard) Pour en savoir plus sur les builds Office Insider Preview, reportez-vous à La mise en place du déploiement [des builds Office Insider.](https://insider.office.com/business/deploy)

### <a name="licensing-requirements"></a>Critères de licence

* Sécurité Microsoft 365 E5 ou Microsoft 365 E5

## <a name="deploy-application-guard-for-office"></a>Déployer Application Guard pour Office

### <a name="enable-application-guard-for-office"></a>Activer Application Guard pour Office

1. Téléchargez et installez les mises à jour de **sécurité mensuelles cumulatives Windows 10 KB4571756.**

2. Sélectionnez **Microsoft Defender Application Guard sous** Fonctionnalités Windows et **sélectionnez OK.** L’activation de la fonctionnalité Application Guard demande un redémarrage du système. Vous pouvez choisir de redémarrer maintenant ou après l’étape 3.

   ![Boîte de dialogue Fonctionnalités Windows affichant AG](../../media/ag03-deploy.png)

   La fonctionnalité peut également être activée en exécutant la commande PowerShell suivante en tant qu’administrateur :

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Recherchez la stratégie de groupe Microsoft Defender Application Guard en mode géré située dans les modèles d’administration de configuration ordinateur **\\ \\ composants \\ Microsoft Defender Application Guard.** Pour activer cette stratégie, vous pouvez définir la valeur sous Options sur **2** ou **3,** puis sélectionner **OK** ou **Appliquer.**

   ![Activer la gestion des ag en mode géré](../../media/ag04-deploy.png)

   Vous pouvez également définir la stratégie CSP correspondante :

   > OMA-URI : **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Settings/AllowWindowsDefenderApplicationGuard** <br> Type de données : **Integer** <br> Valeur : **2**

4. Redémarrez le système.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Définir les diagnostics & commentaires pour envoyer des données complètes

Cette étape garantit que les données nécessaires pour identifier et résoudre les problèmes atteignent Microsoft. Suivez ces étapes pour activer les diagnostics sur votre appareil Windows :

1. Ouvrez **Paramètres** à partir du menu Démarrer.

   ![Menu Démarrer](../../media/ag05-diagnostic.png)

2. Dans **Paramètres Windows,** sélectionnez **Confidentialité.**

   ![Menu Paramètres Windows](../../media/ag06-diagnostic.png)

3. Sous Confidentialité, sélectionnez **Diagnostics & commentaires** et **sélectionnez Données de diagnostic facultatives.**

   ![Menu Diagnostics et commentaires](../../media/ag07a-diagnostic.png)

Pour plus d’informations sur la configuration des paramètres de diagnostic Windows, reportez-vous à La configuration des données [de diagnostic Windows dans votre organisation.](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management)

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Vérifier qu’Application Guard pour Office est activé et fonctionne

Avant de confirmer que Application Guard pour Office est activé, lancez Word, Excel ou PowerPoint sur un appareil sur lequel les stratégies ont été déployées. Assurez-vous qu’Office est activé. Vous devrez peut-être utiliser votre identité de travail pour activer d’abord le produit Office.

Pour confirmer qu’Application Guard pour Office est désormais activé, lancez Word, Excel ou PowerPoint et ouvrez un document nontrus. Par exemple, vous pouvez ouvrir un document téléchargé à partir d’Internet ou une pièce jointe provenant d’une personne extérieure à votre organisation.

Lors du premier lancement d’un fichier nontrus, vous pouvez voir un écran de lancement Office comme celui ci-dessous. Il peut s’afficher pendant un certain temps pendant l’activation d’Application Guard pour Office et l’ouverture du fichier. Les lancements ultérieurs de fichiers nontrus doivent être plus rapides.

![Écran de splash de l’application Office](../../media/ag08-confirm.png)

Lors de l’ouverture, le fichier doit afficher quelques indicateurs visuels pour l’ouverture du fichier dans Application Guard pour Office :

* Une callout dans le ruban

  ![Fichier de document affichant une note App Guard de petite taille](../../media/ag09-confirm.png)

* Icône d’application avec un bouclier dans la barre des tâches

  ![Icône dans la barre des tâches](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Configurer Application Guard pour Office

Office prend en charge les stratégies suivantes pour vous permettre de configurer les fonctionnalités d’Application Guard pour Office. Ces stratégies peuvent être configurées via des stratégies de groupe ou via le service de stratégie cloud Office.

> [!NOTE]
> Ces stratégies seront bientôt disponibles.
> En outre, la configuration de ces stratégies peut désactiver certaines fonctionnalités pour les fichiers ouverts dans Application Guard pour Office.

|Stratégie|Description|
|---|---|
|Désactiver Application Guard pour Office|L’activation de cette stratégie force Word, Excel et PowerPoint à utiliser le conteneur d’isolation du affichage protégé au lieu d’Application Guard pour Office. Cette stratégie peut être utilisée pour désactiver temporairement Application Guard pour Office lorsqu’il existe des problèmes pour le laisser activé pour Edge.|
|Désactiver la copie/coller pour les documents ouverts dans Application Guard|L’activation de cette stratégie empêche un utilisateur de copier et coller du contenu d’un document ouvert dans Application Guard pour Office vers un document ouvert en dehors de celui-ci.|
|Empêcher les utilisateurs de supprimer la protection Application Guard sur les fichiers|L’activation de cette stratégie supprime l’option (dans l’expérience d’application Office) permettant de désactiver la protection Application Guard ou d’ouvrir un fichier en dehors d’Application Guard. <p> **Remarque :** Les utilisateurs peuvent toujours contourner cette stratégie en supprimant manuellement la propriété mark-of-the-web du fichier ou en déplaçant un document vers un emplacement approuvé.|
|Restreindre l’impression à partir de documents ouverts dans Application Guard|L’activation de cette stratégie limite les imprimantes sur les imprimantes sur des utilisateurs à partir d’un fichier ouvert dans Application Guard pour Office. Par exemple, vous pouvez utiliser cette stratégie pour restreindre les utilisateurs à imprimer uniquement au format PDF.|
|Désactiver l’accès à la caméra et au microphone pour les documents ouverts dans Application Guard|L’activation de cette stratégie supprime l’accès d’Office à la caméra et au microphone dans Application Guard pour Office.|
|

> [!NOTE]
> Les stratégies suivantes exigent que l’utilisateur se déconnecte et se connecte de nouveau à Windows pour prendre effet :
>
> * Désactiver la copie/coller pour les documents ouverts dans Application Guard
> * Restreindre l’impression pour les documents ouverts dans Application Guard
> * Désactiver l’accès à la caméra et au micro pour les documents ouverts dans Application Guard

## <a name="submit-feedback"></a>Envoyer les commentaires

### <a name="submit-feedback-via-feedback-hub"></a>Envoyer des commentaires via le Hub de commentaires

Si vous rencontrez des problèmes lors du lancement d’Application Guard pour Office, nous vous encourageons à envoyer vos commentaires via le Hub de commentaires :

1. Ouvrez **l’application Hub de commentaires** et connectez-vous.

2. Si vous obtenez une boîte de dialogue d’erreur lors du lancement d’Application Guard, sélectionnez Signaler à **Microsoft** dans la boîte de dialogue d’erreur pour démarrer une nouvelle soumission de commentaires. Dans le cas contraire, accédez à la catégorie correcte pour Application Guard, puis <https://aka.ms/mdagoffice-fb> **sélectionnez + Ajouter de nouveaux commentaires** en haut à droite.

3. Remplissez la **zone Résumé de vos** commentaires si elle n’est pas déjà remplie pour vous.

4. Remplissez la **zone Expliquer plus en** détail avec une description détaillée du problème que vous avez connu et des étapes que vous avez prises, puis sélectionnez **Suivant**.

5. Sélectionnez la bulle en de côté du problème. Assurez-vous que la catégorie sélectionnée est Sécurité et confidentialité **Microsoft Defender Application Guard – \> Office,** puis sélectionnez **Suivant**.

6. Sélectionnez **Nouveau commentaire,** puis **Suivant**.

7. Collectez des suivis sur le problème :

   1. Développez la **vignette Recréer mon** problème.

   2. Si le problème que vous rencontrez se produit pendant l’exécution d’Application Guard, ouvrez une instance d’Application Guard. Cela permet de collecter des suivis supplémentaires à partir du conteneur Application Guard.

   3. Sélectionnez **Démarrer l’enregistrement** et attendez que la vignette cesse de tourner et dites *Arrêter l’enregistrement.*

   4. Reproduisez entièrement le problème avec Application Guard. Cela peut inclure une tentative de lancement d’une instance d’Application Guard et l’attente d’un échec, ou la reproduction d’un problème dans une instance d’Application Guard en cours d’exécution.

   5. Sélectionnez la **vignette Arrêter l’enregistrement.**

   6. Gardez toutes les instances d’Application Guard en cours d’exécution ouvertes, même jusqu’à quelques minutes après l’envoi, afin que les diagnostics de conteneur soient également collectés.

8. Joignez les captures d’écran pertinentes ou les fichiers associés au problème.

9. Sélectionnez **Envoyer**.

### <a name="submit-feedback-via-office-customer-voice"></a>Envoyer des commentaires via Office Customer Voice

Vous pouvez également envoyer des commentaires à partir d’Office si le problème survient lorsque des documents Office sont ouverts dans Application Guard. Reportez-vous au manuel [Office Insider pour](https://insider.office.com/handbook) envoyer vos commentaires.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Intégration à Microsoft Defender pour Endpoint et Microsoft Defender pour Office 365

Application Guard pour Office est intégré à Microsoft Defender for Endpoint pour fournir une surveillance et une alerte sur les activités malveillantes qui se produisent dans l’environnement isolé.

Microsoft Defender pour point de terminaison est une plateforme de sécurité conçue pour aider les réseaux d’entreprise à prévenir, détecter, examiner et répondre aux menaces avancées. Pour plus d’informations sur cette plateforme, visitez la page [Microsoft Defender pour le point de terminaison.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp) Pour en savoir plus sur l’intégration d’appareils à cette plateforme, voir Appareils intégrés [au service Microsoft Defender for Endpoint.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/onboard-configure)

Vous pouvez également configurer Microsoft Defender pour Office 365 afin qu’il fonctionne avec Defender pour Endpoint. [Reportez-vous à Intégrer Defender pour Office 365 à Microsoft Defender pour le point de terminaison.](integrate-office-365-ti-with-wdatp.md)

## <a name="limitations-and-considerations"></a>Limitations et considérations

* Application Guard pour Office est un mode restreint qui isole les documents non fiables de l’accès aux ressources d’entreprise, à l’intranet, à l’identité de l’utilisateur et aux fichiers arbitraires présents sur l’ordinateur. Par conséquent, si un utilisateur tente d’accéder à une fonctionnalité qui dépend de cet accès, par exemple l’insertion d’une image à partir d’un fichier local sur le disque, il échoue et produit une invite comme celle ci-dessous. Pour permettre à un document non approuvé d’accéder à des ressources fiables, les utilisateurs doivent supprimer la protection Application Guard du document.

  ![Boîte de dialogue qui vous aide à assurer la sécurité, cette fonctionnalité n’est pas disponible](../../media/ag10-limitations.png)

  > [!NOTE]
  > Conseillez aux utilisateurs de supprimer la protection uniquement s’ils font confiance au fichier et à sa source ou à leur origine.

* Le contenu actif dans les documents tels que les macros et ActiveX contrôles de contenu sont désactivés dans Application Guard pour Office. Les utilisateurs doivent supprimer la protection Application Guard pour activer le contenu actif.

* Les fichiers nontrus ouverts à partir de partages réseau ou de fichiers partagés à partir de OneDrive, OneDrive Entreprise ou SharePoint Online d’une autre organisation s’ouvrent en lecture seule dans Application Guard. Les utilisateurs peuvent enregistrer une copie locale de ces fichiers pour continuer à travailler dans le conteneur ou supprimer la protection pour travailler directement avec le fichier d’origine.

* Les fichiers protégés par la Gestion des droits de l’information (IRM) continuent de s’ouvrir en affichage protégé.

* Les personnalisations des applications Office dans Application Guard pour Office ne sont pas persistantes après qu’un utilisateur se déconnecte et se connecte à nouveau ou redémarre l’appareil.

* Seuls les outils d’accessibilité qui utilisent l’infrastructure UIA peuvent fournir une expérience accessible pour les fichiers ouverts dans Application Guard pour Office.

* La connectivité réseau est requise pour le premier lancement d’Application Guard après l’installation. Cette procédure est requise pour qu’Application Guard valide la licence.

* Dans la section d’informations du document, la propriété *Last Modified By* peut afficher WDAGUtilityAccount en tant qu’utilisateur. Il s’agit de l’utilisateur anonyme configuré dans Application Guard, étant donné que l’identité de l’utilisateur de bureau n’est pas partagée à l’intérieur du conteneur Application Guard.

## <a name="performance-optimizations-for-application-guard"></a>Optimisation des performances pour Application Guard

Cette section fournit une vue d’ensemble des optimisations des performances utilisées dans Application Guard pour Office. Ces informations peuvent aider les administrateurs à diagnostiquer les rapports provenant d’utilisateurs liés aux performances d’Office ou au système global lorsque Application Guard est activé.

Application Guard utilise un conteneur virtualisé pour isoler les documents nontrus du système. Le processus de création d’un conteneur et de configuration du conteneur Application Guard pour ouvrir des documents Office a une surcharge de performances qui peut avoir un impact négatif sur l’expérience utilisateur lorsque les utilisateurs ouvrent un document nontrus.

Pour fournir aux utilisateurs l’expérience d’ouverture de fichier attendue, Application Guard utilise la logique pour pré-créer un conteneur lorsque l’heuristique suivante est rencontrée sur un système : un utilisateur a ouvert un fichier en affichage protégé ou en application Guard au cours des 28 derniers jours.

Lorsque cette heuristique est remplie, Office pré-crée un conteneur Application Guard pour l’utilisateur une fois qu’il se connecte à Windows. Lorsque cette opération de pré-création est en cours, les performances du système peuvent être lentes. Cette opération est résolue dès que l’opération est terminée.

> [!NOTE]
> Les conseils nécessaires pour l’heuristique utilisée pour pré-créer le conteneur sont générés par les applications Office en tant qu’utilisateurs. Si un utilisateur installe Office sur un nouveau système où Application Guard est activé, Office ne pré-crée pas le conteneur avant la première ouverture d’un document nontrus sur le système. L’utilisateur observe que l’ouverture de ce premier fichier dans Application Guard est plus longue.

## <a name="known-issues-in-preview"></a>Problèmes connus dans la prévisualisation

* Le fait de cliquer sur des liens web `http` (ou `https` ) n’ouvre pas le navigateur.
* Les mises à jour .NET entraînent l’échec de l’ouverture des fichiers dans Application Guard. Pour contourner ce problème, les utilisateurs peuvent redémarrer leur appareil lorsque ce problème se produit. En savoir plus sur le problème lors de la réception d’un message d’erreur lors de la tentative [d’ouverture Windows Defender Application Guard ou bac à sable Windows](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
