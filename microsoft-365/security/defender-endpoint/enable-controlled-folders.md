---
title: Activer l’accès contrôlé aux dossiers
keywords: Accès contrôlé aux dossiers, windows 10, windows defender, ransomware, protéger, fichiers, dossiers, activer, utiliser
description: Découvrez comment protéger vos fichiers importants en activant l’accès contrôlé aux dossiers
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: levinec
ms.author: ellevin
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 6d07e2a21bb01794990160cf02837fc524008098
ms.sourcegitcommit: 8685b0f7d53c99577fa65144ab60295dfa60f46f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51218759"
---
# <a name="enable-controlled-folder-access"></a>Activer l’accès contrôlé aux dossiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

[L’accès contrôlé aux dossiers](controlled-folders.md) vous permet de protéger les données précieuses contre les applications malveillantes et les menaces, telles que les ransomware. L’accès contrôlé aux dossiers est inclus dans Windows 10 et Windows Server 2019.

Vous pouvez activer l’accès contrôlé aux dossiers à l’aide de l’une des méthodes ci-après :

* [Application sécurité Windows](#windows-security-app)
* [Microsoft Intune](#intune)
* [Gestion des périphériques mobiles (MDM)](#mobile-device-management-mdm)
* [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
* [Stratégie de groupe](#group-policy)
* [PowerShell](#powershell)

[Le mode audit](evaluate-controlled-folder-access.md) vous permet de tester le fonctionnement de la fonctionnalité (et de passer en revue les événements) sans impact sur l’utilisation normale de l’appareil.

Les paramètres de stratégie de groupe qui désactivent la fusion de listes d’administrateurs locaux remplacent les paramètres d’accès contrôlé aux dossiers. Ils remplacent également les dossiers protégés et les applications autorisées définies par l’administrateur local par le biais d’un accès contrôlé aux dossiers. Ces stratégies sont les suivantes :

* Antivirus Microsoft Defender **Configurer le comportement de fusion de l’administrateur local pour les listes**
* System Center Endpoint Protection **Autoriser les utilisateurs à ajouter des exclusions et des remplacements**

Pour plus d’informations sur la désactivation de la fusion de listes locales, voir Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie de [Microsoft Defender AV.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus#configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged)

## <a name="windows-security-app"></a>Application sécurité Windows

1. Ouvrez l’application Sécurité Windows en sélectionnant l’icône de bouclier dans la barre des tâches. Vous pouvez également rechercher Defender dans le menu **Démarrer.**

2. Sélectionnez la **vignette & protection** contre les virus contre les menaces (ou l’icône de bouclier dans la barre de menus de gauche), puis sélectionnez Protection contre les **ransomware.**

3. Définissez le commutateur pour **l’accès contrôlé aux** dossiers sur **On**.

> [!NOTE]
> Si l’accès contrôlé aux dossiers est configuré avec la stratégie de groupe, PowerShell ou les CSP MDM, l’état change dans l’application Sécurité Windows après un redémarrage de l’appareil.
> Si la fonctionnalité est définie sur **le mode Audit** avec l’un de ces outils, l’application sécurité Windows affiche l’état « Hors **».**
> Si vous protégez les données de profil utilisateur, nous vous recommandons de le faire sur le lecteur d’installation Windows par défaut.

## <a name="intune"></a>Intune

1. Connectez-vous au [portail Azure et](https://portal.azure.com) ouvrez Intune.

2. Go to **Device configuration**  >  **Profiles**  >  **Create profile**.

3. Nommez le profil, choisissez **Windows 10 et les ultérieures** et **Endpoint Protection**. <br/> ![Créer un profil de protection des points de terminaison](/microsoft-365/security/defender-endpoint/images/create-endpoint-protection-profile) <br/>

4. Go to **Configure**  >  **Windows Defender Exploit Guard**  >  **Controlled folder access**  >  **Enable**.

5. Tapez le chemin d’accès à chaque application qui a accès aux dossiers protégés et le chemin d’accès à tout dossier supplémentaire qui nécessite une protection. Sélectionnez **Ajouter**.<br/> ![Activer l’accès contrôlé aux dossiers dans Intune](/microsoft-365/security/defender-endpoint/images/enable-cfa-intune)<br/>

   > [!NOTE]
   > Wilcard est pris en charge pour les applications, mais pas pour les dossiers. Les sous-foldeurs ne sont pas protégés. Les applications autorisées continueront à déclencher des événements jusqu’à leur redémarrage.

6. Sélectionnez **OK** pour enregistrer chaque lame ouvert et **créer.**

7. Sélectionnez les **affectations de profil,** affectez à tous les utilisateurs **& tous** les appareils et **enregistrez**.

## <a name="mobile-device-management-mdm"></a>Gestion des périphériques mobiles (MDM)

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) (CSP) pour permettre aux applications d’apporter des modifications aux dossiers protégés.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Dans Microsoft Endpoint Configuration Manager, sélectionnez **Assets and Compliance**  >  **Endpoint Protection** Windows Defender Exploit  >  **Guard**.

2. Sélectionnez **Home**  >  **Create Exploit Guard Policy**.

3. Entrez un nom et une description, sélectionnez **Accès contrôlé aux** dossiers, puis sélectionnez **Suivant**.

4. Choisissez si bloquer ou auditer les modifications, autoriser d’autres applications ou ajouter d’autres dossiers, puis sélectionnez **Suivant**.
   > [!NOTE]
   > Wilcard est pris en charge pour les applications, mais pas pour les dossiers. Les sous-foldeurs ne sont pas protégés. Les applications autorisées continueront à déclencher des événements jusqu’à leur redémarrage.

5. Examinez les paramètres et **sélectionnez Suivant** pour créer la stratégie.

6. Une fois la stratégie créée, **fermez**.

## <a name="group-policy"></a>Stratégie de groupe

1. Sur votre appareil de gestion des stratégies de groupe, ouvrez la [Console](https://technet.microsoft.com/library/cc731212.aspx)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer et sélectionnez **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur et sélectionnez **Modèles d’administration.**

3. Développez l’arborescence **des composants Windows > Antivirus Microsoft Defender > Windows Defender Exploit Guard > accès contrôlé aux dossiers.**

4. Double-cliquez sur **le paramètre Configurer l’accès contrôlé aux** dossiers et définissez l’option sur **Activé.** Dans la section Options, vous devez spécifier l’une des options suivantes :
    * **Activer** : les applications malveillantes et suspectes ne seront pas autorisées à apporter des modifications aux fichiers des dossiers protégés. Une notification sera fournie dans le journal des événements Windows.
    * **Désactiver (par défaut)** : la fonctionnalité Accès contrôlé aux dossiers ne fonctionne pas. Toutes les applications peuvent apporter des modifications aux fichiers dans les dossiers protégés.
    * **Mode audit** : les modifications sont autorisées si une application malveillante ou suspecte tente d’apporter une modification à un fichier dans un dossier protégé. Toutefois, il sera enregistré dans le journal des événements Windows où vous pourrez évaluer l’impact sur votre organisation.
    * **Bloquer la modification du disque uniquement** : les tentatives d’écriture dans les secteurs de disque par des applications nontrues seront enregistrées dans le journal des événements Windows. Ces journaux se trouvent dans les Journaux des applications et des **services** > Microsoft > Windows > Windows Defender > Operational > ID 1123.
    * **Auditer** la modification du disque uniquement : seules les tentatives d’écriture dans les secteurs de disque protégés seront **enregistrées** dans le journal des événements Windows (sous Journaux des applications et des services  >  **Microsoft**  >  **Windows**  >  **Windows Defender**  >  **Operational**  >  **ID 1124**). Les tentatives de modification ou de suppression de fichiers dans des dossiers protégés ne sont pas enregistrées.

      ![Capture d’écran de l’option de stratégie de groupe Activée et mode Audit sélectionnée dans la baisse](/microsoft-365/security/defender-endpoint/images/cfa-gp-enable)

> [!IMPORTANT]
> Pour activer entièrement l’accès contrôlé aux dossiers, vous  devez définir l’option de stratégie de groupe sur Activé et sélectionner Bloquer dans le menu déroulant Options. 

## <a name="powershell"></a>PowerShell

1. Tapez **powershell** dans le menu Démarrer, cliquez avec **le bouton droit sur Windows PowerShell** puis **sélectionnez Exécuter en tant qu’administrateur.**

2. Entrez l’cmdlet suivante :

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

Vous pouvez activer la fonctionnalité en mode audit en spécifiant `AuditMode` au lieu de `Enabled` .

Permet `Disabled` de désactiver la fonctionnalité.

## <a name="see-also"></a>Voir aussi

* [Protéger les dossiers importants avec un accès contrôlé aux dossiers](controlled-folders.md)
* [Personnaliser l’accès contrôlé aux dossiers](customize-controlled-folders.md)
* [Évaluer Microsoft Defender pour le point de terminaison](evaluate-mde.md)
