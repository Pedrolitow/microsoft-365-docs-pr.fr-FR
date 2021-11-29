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
ms.openlocfilehash: 3965b02e4bf4e4b6bce35a6abaf368dc4f47be83
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61218285"
---
# <a name="customize-attack-surface-reduction-rules"></a>Personnaliser les règles de réduction de la surface d’attaque

**S’applique à :**

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

<br>

****

|Description de la règle|GUID|
|---|---|
|Bloquer l’utilisation abusive des pilotes signés vulnérables exploités|`56a863a9-875e-4185-98a7-b882c64b5ce5`|
|Empêcher Adobe Reader de créer des processus enfants|`7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`|
|Empêcher toutes les applications Office de créer des processus enfants|`d4f940ab-401b-4efc-aadc-ad5f3c50688a`|
|Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe)|`9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`|
|Bloquer le contenu exécutable du client de messagerie et de la messagerie web|`be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`|
|Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de listes fiables|`01443614-cd74-433a-b99e-2ecdc07bfc25`|
|Bloquer l’exécution de scripts potentiellement obscurcis|`5beb7efe-fd9a-4556-801d-275e5ffc04cc`|
|Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé|`d3e037e1-3eb8-44c8-a917-57927947596d`|
|Empêcher Office applications de créer du contenu exécutable|`3b576869-a4ec-4529-8536-b80a7769e899`|
|Empêcher Office applications d’injecter du code dans d’autres processus|`75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`|
|Empêcher Office applications de communication de créer des processus enfants|`26190899-1602-49e8-8b27-eb1d0a1ce869`|
|Bloquer la persistance via un abonnement à des événements WMI|`e6db77e5-3df2-4cf1-b95a-636979351e5b`|
|Bloquer les créations de processus provenant de commandes PSExec et WMI|`d1e49aac-8f56-4280-b9ba-993a6d77406c`|
|Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB|`b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`|
|Bloquer les appels d’API Win32 à partir Office macro|`92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`|
|Utiliser la protection avancée contre les ransomware|`c1db55ab-c21a-4637-bb3f-a12568109d35`|
|

Consultez la rubrique [réduction de la surface](attack-surface-reduction.md) d’attaque pour plus d’informations sur chaque règle.

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

## <a name="related-topics"></a>Rubriques connexes

- [Réduire les surfaces d’attaque avec des règles de réduction de la surface d’attaque](attack-surface-reduction.md)
- [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
- [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
- [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction.md)
