---
title: Personnaliser les règles de réduction de la surface d’attaque
description: Définir individuellement des règles dans les modes audit, bloquer ou désactivé, et ajouter des fichiers et des dossiers qui doivent être exclus des règles de réduction de la surface d’attaque
keywords: Réduction de la surface d’attaque, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, personnaliser, configurer, exclure
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 992c8802f3a4f44b1558004e2ee27ddbedf70a1a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531170"
---
# <a name="customize-attack-surface-reduction-rules"></a>Personnaliser les règles de réduction de la surface d’attaque

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

[Les règles de réduction de la surface](enable-attack-surface-reduction.md) d’attaque permettent d’éviter les comportements logiciels qui sont souvent mal pris en charge pour compromettre votre appareil ou votre réseau. Par exemple, un attaquant peut essayer d’exécuter un script non signé à partir d’un lecteur USB ou faire en sorte qu’une macro dans un document Office appelle directement l’API Win32. Les règles de réduction de la surface d’attaque peuvent limiter ces types de comportements risqués et améliorer la posture de défense de votre organisation.

Découvrez comment personnaliser les règles de réduction de la surface d’attaque en excluant des fichiers et des [dossiers](#exclude-files-and-folders) ou en ajoutant du texte personnalisé à l’alerte de [notification](#customize-the-notification) qui apparaît sur l’ordinateur d’un utilisateur.

Vous pouvez définir des règles de réduction de la surface d’attaque pour les appareils exécutant l’une des éditions et versions de Windows :

- Windows 10 Professionnel, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows 10 Entreprise, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows Server, [version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
-  [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2) 
- Windows Server 2022

Vous pouvez utiliser la stratégie de groupe, PowerShell et les fournisseurs de services de configuration (CSP) de gestion des périphériques mobiles (CSP) pour configurer ces paramètres.

Pour plus [d’informations](enable-attack-surface-reduction.md#requirements) sur les systèmes d’exploitation pris en charge et d’autres informations sur les conditions requises, voir La procédure requise dans l’article « Activer les règles de réduction de la surface d’attaque ».

## <a name="exclude-files-and-folders"></a>Exclure des fichiers et des dossiers

Vous pouvez choisir d’exclure les fichiers et dossiers de l’évaluation par les règles de réduction de la surface d’attaque. Lorsqu’il est exclu, l’exécution du fichier n’est pas bloquée même si une règle de réduction de la surface d’attaque détecte que le fichier contient un comportement malveillant.

Par exemple, prenons la règle de ransomware :

La règle de ransomware est conçue pour aider les clients d’entreprise à réduire les risques d’attaques par ransomware tout en assurant la continuité de l’activité. Par défaut, les erreurs de règle de ransomware du côté de la prudence et la protection contre les fichiers qui n’ont pas encore atteint une réputation et une confiance suffisantes. Pour reéphaser, la règle de ransomware se déclenche uniquement sur les fichiers qui n’ont pas acquis une réputation et une prévalence positives suffisantes, en fonction des mesures d’utilisation de millions de nos clients. En règle générale, les blocs sont auto-résolus, car les valeurs « réputation et confiance » de chaque fichier sont mises à niveau de manière incrémentielle à mesure que l’utilisation non problématique augmente.

Dans les cas où les blocs ne sont pas résolus en temps voulu, les clients peuvent, à leurs propres risques, utiliser le mécanisme en libre-service ou une fonctionnalité de « liste d’autoriser » basée sur l’indicateur de compromis (IOC) pour débloquer les fichiers eux-mêmes. 

> [!WARNING]
> L’exclusion ou le déblocage de fichiers ou de dossiers pourrait potentiellement permettre à des fichiers non sécurisés de s’exécuter et d’infecter vos appareils. L’exclusion des fichiers ou dossiers peut considérablement réduire la protection fournie par les règles de réduction de la surface d’attaque. Les fichiers qui auraient été bloqués par une règle seront autorisés à s’exécuter et aucun rapport ou événement n’est enregistré.

Une exclusion s’applique à toutes les règles qui autorisent les exclusions. Vous pouvez spécifier un fichier, un chemin d’accès de dossier ou le nom de domaine complet d’une ressource. Toutefois, vous ne pouvez pas limiter une exclusion à une règle spécifique.

Une exclusion est appliquée uniquement au démarrage de l’application ou du service exclu. Par exemple, si vous ajoutez une exclusion pour un service de mise à jour déjà en cours d’exécution, le service de mise à jour continue à déclencher des événements jusqu’à ce que le service soit arrêté et redémarré.

La réduction de la surface d’attaque prend en charge les variables d’environnement et les caractères génériques. Pour plus d’informations sur l’utilisation de caractères génériques, voir les caractères génériques dans le nom de fichier et le chemin d’accès du dossier ou les [listes d’exclusion d’extension.](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists)
Si vous rencontrez des problèmes avec des règles détectant des fichiers qui, selon vous, ne doivent pas être détectés, utilisez le [mode audit pour tester la règle.](evaluate-attack-surface-reduction.md)

Consultez la rubrique [de référence des règles](attack-surface-reduction-rules-reference.md) de réduction de la surface d’attaque pour plus d’informations sur chaque règle.

### <a name="use-group-policy-to-exclude-files-and-folders"></a>Utiliser une stratégie de groupe pour exclure des fichiers et des dossiers

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](https://technet.microsoft.com/library/cc731212.aspx), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

3. Développez l’arborescence **Windows composants Antivirus Microsoft Defender** \>  \> Protection contre les attaques Microsoft Defender réduction de la surface  \> **d’attaque.**

4. Double-cliquez sur le **paramètre Exclure les fichiers et** les chemins d’accès du paramètre Règles de réduction de la surface d’attaque et définissez l’option sur **Activé.** Sélectionnez **Afficher** et entrez chaque fichier ou dossier dans la **colonne Nom de la** valeur. Entrez **0 dans** la colonne **Valeur** pour chaque élément.

> [!WARNING]
> N’utilisez pas de guillemets, car ils ne sont pas pris en charge pour la colonne Nom de la valeur ou la **colonne** Valeur. 

### <a name="use-powershell-to-exclude-files-and-folders"></a>Utiliser PowerShell pour exclure des fichiers et des dossiers

1. Tapez **powershell** dans le menu Démarrer, cliquez avec le **bouton droit** sur Windows PowerShell puis **sélectionnez Exécuter en tant qu’administrateur.**

2. Entrez l’cmdlet suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Continuez à `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` l’utiliser pour ajouter d’autres dossiers à la liste.
    
    > [!IMPORTANT]
    > Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste. `Set-MpPreference`L’utilisation de la cmdlet va supprimer la liste existante.

### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Utiliser des CSP mdm pour exclure des fichiers et des dossiers

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) (CSP) pour ajouter des exclusions.

## <a name="customize-the-notification"></a>Personnaliser la notification

Vous pouvez personnaliser la notification lorsqu’une règle est déclenchée et bloque une application ou un fichier. Consultez [l’article](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center) Sécurité Windows’article.

## <a name="related-topics"></a>Voir aussi

- [Réduire les surfaces d’attaque avec des règles de réduction de la surface d’attaque](attack-surface-reduction.md)
- [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
- [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
- [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction.md)
