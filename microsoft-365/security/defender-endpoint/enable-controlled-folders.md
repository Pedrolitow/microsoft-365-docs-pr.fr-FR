---
title: Activer l’accès contrôlé aux dossiers
keywords: Accès contrôlé aux dossiers, windows 10, windows 11, windows defender, ransomware, protéger, fichiers, dossiers, activer, activer, utiliser
description: Découvrez comment protéger vos fichiers importants en activant l’accès contrôlé aux dossiers
ms.service: microsoft-365-security
ms.topic: conceptual
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.subservice: mde
ms.collection:
- m365-security
- tier3
ms.date: ''
search.appverid: met150
ms.openlocfilehash: 88219eb48a81f092070b787acbd283cc3bf5fb37
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68630663"
---
# <a name="enable-controlled-folder-access"></a>Activer l’accès contrôlé aux dossiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[L’accès contrôlé aux dossiers](controlled-folders.md) vous permet de protéger les données précieuses contre les applications malveillantes et les menaces, telles que les ransomware. L’accès contrôlé aux dossiers est inclus avec Windows 10, Windows 11 et Windows Server 2019. L’accès contrôlé aux dossiers est également inclus dans la [solution unifiée moderne pour Windows Server 2012R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

Vous pouvez activer l’accès contrôlé aux dossiers à l’aide de l’une des méthodes suivantes :

- [application Sécurité Windows *](#windows-security-app)
- [Microsoft Endpoint Manager](#endpoint-manager)
- [Gestion des périphériques mobiles (GPM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Stratégie de groupe](#group-policy)
- [PowerShell](#powershell)

Le [mode Audit](evaluate-controlled-folder-access.md) vous permet de tester le fonctionnement de la fonctionnalité (et d’examiner les événements) sans affecter l’utilisation normale de l’appareil.

stratégie de groupe paramètres qui désactivent la fusion de listes d’administrateurs locaux remplacent les paramètres d’accès contrôlé aux dossiers. Ils remplacent également les dossiers protégés et les applications autorisées définies par l’administrateur local via un accès contrôlé aux dossiers. Ces stratégies sont les suivantes :

- Microsoft Defender Antivirus **Configurez le comportement de fusion de l’administrateur local pour les listes**
- System Center Endpoint Protection **Autoriser les utilisateurs à ajouter des exclusions et des remplacements**

Pour plus d’informations sur la désactivation de la fusion de listes locales, consultez [Empêcher ou autoriser les utilisateurs à modifier localement Microsoft Defender paramètres de stratégie antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>Ouvrez l’application Sécurité Windows.

1. Ouvrez l’application Sécurité Windows en sélectionnant l’icône de bouclier dans la barre des tâches. Vous pouvez également rechercher Sécurité Windows dans le menu **Démarrer**.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche), puis sélectionnez **Protection contre les ransomware**.

3. Définissez le commutateur pour **l’accès contrôlé aux dossiers** **sur Activé**.

> [!NOTE]
> *Cette méthode n’est pas disponible sur Windows Server 2012R2 ou 2016.
> 
> Si l’accès contrôlé aux dossiers est configuré avec stratégie de groupe, PowerShell ou MDM CSP, l’état change dans l’application Sécurité Windows après un redémarrage de l’appareil.
> Si la fonctionnalité est définie sur **le mode Audit** avec l’un de ces outils, l’application Sécurité Windows affiche l’état **Désactivé**.
> Si vous protégez les données de profil utilisateur, nous vous recommandons d’utiliser le profil utilisateur sur le lecteur d’installation Windows par défaut.

## <a name="endpoint-manager"></a>Gestionnaire de points de terminaison

1. Connectez-vous au [Endpoint Manager](https://endpoint.microsoft.com) et **ouvrez Endpoint Security**.

2. Accédez à la **stratégie de réduction de la surface d’attaque** \> **.**

3. Sélectionnez **Plateforme**, choisissez **Windows 10 et versions ultérieures**, puis sélectionnez les règles \> de **réduction de la surface d’attaque** de profil **créer**.

4. Nommez la stratégie et ajoutez une description. Sélectionnez **Suivant**.

5. Faites défiler vers le bas, sélectionnez la liste **déroulante Activer la protection des dossiers** , puis choisissez **Activer**.

6. Sélectionnez **Liste des dossiers supplémentaires qui doivent être protégés** et ajoutez les dossiers qui doivent être protégés.

7. Sélectionnez **Liste des applications qui ont accès à des dossiers protégés** et ajoutez les applications qui ont accès à des dossiers protégés.

8. Sélectionnez **Exclure les fichiers et les chemins des règles de réduction de la surface d’attaque** et ajoutez les fichiers et les chemins qui doivent être exclus des règles de réduction de la surface d’attaque.

9. Sélectionnez les **affectations** de profil, affectez-les à **tous les utilisateurs & tous les appareils**, puis **sélectionnez Enregistrer**.

10. Sélectionnez **Suivant** pour enregistrer chaque panneau ouvert, puis **Créer**.

    > [!NOTE]
    > Les caractères génériques sont pris en charge pour les applications, mais pas pour les dossiers. Les sous-dossiers ne sont pas protégés. Les applications autorisées continueront de déclencher des événements jusqu’à leur redémarrage.

## <a name="mobile-device-management-mdm"></a>Gestion des périphériques mobiles (GPM)

Utilisez le fournisseur de services de configuration (CSP) [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) pour permettre aux applications d’apporter des modifications aux dossiers protégés.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Dans Microsoft Endpoint Configuration Manager, accédez à **Ressources et conformité**\>**Endpoint Protection**\>**Windows Defender Exploit Guard**.

2. Sélectionnez **Accueil**\>**Créer une stratégie Exploit Guard**.

3. Entrez un nom et une description, sélectionnez **Accès contrôlé aux dossiers**, puis **Suivant**.

4. Choisissez si vous bloquez ou auditez les modifications, autorisez d’autres applications ou ajoutez d’autres dossiers, puis sélectionnez **Suivant**.

   > [!NOTE]
   > Le caractère générique est pris en charge pour les applications, mais pas pour les dossiers. Les sous-dossiers ne sont pas protégés. Les applications autorisées continueront de déclencher des événements jusqu’à leur redémarrage.

5. Passez en revue les paramètres et sélectionnez **Suivant** pour créer la stratégie.

6. Une fois la stratégie créée, **fermez**.

## <a name="group-policy"></a>Stratégie de groupe

1. Sur votre appareil de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](https://technet.microsoft.com/library/cc731212.aspx), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans l’**Éditeur de gestion des stratégies de groupe**, accédez à **Configuration ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence sur **les composants Windows > Microsoft Defender Antivirus > Windows Defender Exploit Guard > l’accès contrôlé aux dossiers**.

4. Double-cliquez sur le paramètre **Configurer l’accès contrôlé aux dossiers** et définissez l’option **sur Activé**. Dans la section Options, vous devez spécifier l’une des options suivantes :
   - **Activer** : les applications malveillantes et suspectes ne seront pas autorisées à apporter des modifications aux fichiers dans les dossiers protégés. Une notification est fournie dans le journal des événements Windows.
   - **Désactiver (valeur par défaut)** : la fonctionnalité d’accès contrôlé aux dossiers ne fonctionnera pas. Toutes les applications peuvent apporter des modifications aux fichiers dans des dossiers protégés.
   - **Mode Audit** : les modifications sont autorisées si une application malveillante ou suspecte tente d’apporter une modification à un fichier dans un dossier protégé. Toutefois, il est enregistré dans le journal des événements Windows, où vous pouvez évaluer l’impact sur votre organisation.
   - **Bloquer la modification du disque uniquement** : les tentatives d’écriture dans les secteurs de disque par des applications non approuvées sont consignées dans le journal des événements Windows. Ces journaux se trouvent dans les journaux **d’activité Applications et Services** \> Microsoft \> Windows \> Windows Defender \> L’ID opérationnel \> 1123.
   - **Auditer uniquement la modification du disque** : seules les tentatives d’écriture dans les secteurs de disque protégés sont enregistrées dans le journal des événements Windows (sous **Journaux des applications et des** \> services **Microsoft** \> **Windows** \> **Windows Defender** \> **L’ID** **opérationnel** \> 1124). Les tentatives de modification ou de suppression de fichiers dans des dossiers protégés ne seront pas enregistrées.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="Option de stratégie de groupe activée et mode d’audit sélectionnée" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> Pour activer entièrement l’accès contrôlé aux dossiers, vous devez définir l’option stratégie de groupe **sur Activé** et sélectionner **Bloquer** dans le menu déroulant options.

## <a name="powershell"></a>PowerShell

1. Tapez **powershell** dans le menu Démarrer, cliquez avec le bouton droit sur **Windows PowerShell** et sélectionnez **Exécuter en tant qu’administrateur**.

2. Entrez l’applet de commande suivante :

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

Vous pouvez activer la fonctionnalité en mode audit en spécifiant au `AuditMode` lieu de `Enabled`.

Permet `Disabled` de désactiver la fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Protéger les dossiers importants avec accès contrôlé aux dossiers](controlled-folders.md)
- [Personnaliser l’accès contrôlé aux dossiers](customize-controlled-folders.md)
- [Évaluer Microsoft Defender pour point de terminaison](evaluate-mde.md)
