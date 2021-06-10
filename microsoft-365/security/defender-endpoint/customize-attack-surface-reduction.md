---
title: Personnaliser les règles de réduction de la surface d’attaque
description: Définissez individuellement des règles dans les modes audit, blocage ou désactivé, et ajoutez des fichiers et des dossiers qui doivent être exclus des règles de réduction de la surface d’attaque
keywords: Réduction de la surface d’attaque, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, personnaliser, configurer, exclure
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: c03bc2a61ba2dae1b5db34c6b48d623c58c0c613
ms.sourcegitcommit: 3b9fab82d63aea41d5f544938868c5d2cbf52d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52782872"
---
# <a name="customize-attack-surface-reduction-rules"></a>Personnaliser les règles de réduction de la surface d’attaque

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

[Les règles de réduction de la surface](enable-attack-surface-reduction.md) d’attaque permettent d’éviter les comportements logiciels qui sont souvent mal pris en compte pour compromettre votre appareil ou votre réseau. Par exemple, un attaquant peut essayer d’exécuter un script non signé à partir d’un lecteur USB ou faire en sorte qu’une macro dans un document Office appelle directement l’API Win32. Les règles de réduction de la surface d’attaque peuvent limiter ces types de comportements risqués et améliorer la posture de défense de votre organisation.

Découvrez comment personnaliser les règles de réduction de la surface d’attaque en excluant des fichiers et des [dossiers](#exclude-files-and-folders) ou en ajoutant du texte personnalisé à l’alerte de [notification](#customize-the-notification) qui apparaît sur l’ordinateur d’un utilisateur.

Vous pouvez définir des règles de réduction de la surface d’attaque pour les appareils exécutant l’une des éditions et versions suivantes de Windows :
- Windows 10 Professionnel, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows 10 Entreprise, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows Serveur, [version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19) Vous pouvez utiliser la stratégie de groupe, PowerShell et les fournisseurs de services de configuration (CSP) de gestion des périphériques mobiles (CSP) pour configurer ces paramètres.

## <a name="exclude-files-and-folders"></a>Exclure des fichiers et des dossiers

Vous pouvez choisir d’exclure les fichiers et dossiers de l’évaluation par les règles de réduction de la surface d’attaque. Une fois exclu, l’exécution du fichier ne sera pas bloquée même si une règle de réduction de la surface d’attaque détecte que le fichier contient un comportement malveillant.

Par exemple, prenons la règle de ransomware :

La règle de ransomware est conçue pour aider les clients d’entreprise à réduire les risques d’attaques par ransomware tout en assurant la continuité de l’activité. Par défaut, la règle de ransomware va faire l’erreur du côté de la prudence et se protéger contre les fichiers qui n’ont pas encore atteint une réputation et une confiance suffisantes. Pour reéphaser, la règle de ransomware se déclenche uniquement sur les fichiers qui n’ont pas acquis une réputation et une prévalence positives suffisantes, en fonction des mesures d’utilisation de millions de nos clients. En règle générale, les blocs sont auto-résolus, car les valeurs « réputation et confiance » de chaque fichier sont mises à niveau de manière incrémentielle à mesure que l’utilisation non problématique augmente.

Dans les cas où les blocs ne sont pas résolus en temps voulu, les clients peuvent, à leurs propres risques, utiliser le mécanisme en libre-service ou une fonctionnalité de « liste d’autoriser » basée sur l’indicateur de compromis (IOC) pour débloquer les fichiers eux-mêmes.   

> [!WARNING]
> L’exclusion ou le déblocage de fichiers ou de dossiers pourrait potentiellement permettre à des fichiers non sécurisés de s’exécuter et d’infecter vos appareils. L’exclusion des fichiers ou dossiers peut considérablement réduire la protection fournie par les règles de réduction de la surface d’attaque. Les fichiers qui auraient été bloqués par une règle seront autorisés à s’exécuter et aucun rapport ou événement n’est enregistré.

Une exclusion s’applique à toutes les règles qui autorisent les exclusions. Vous pouvez spécifier un fichier, un chemin d’accès de dossier ou le nom de domaine complet d’une ressource. Toutefois, vous ne pouvez pas limiter une exclusion à une règle spécifique.

Une exclusion est appliquée uniquement au démarrage de l’application ou du service exclu. Par exemple, si vous ajoutez une exclusion pour un service de mise à jour déjà en cours d’exécution, le service de mise à jour continue à déclencher des événements jusqu’à ce que le service soit arrêté et redémarré.

La réduction de la surface d’attaque prend en charge les variables d’environnement et les caractères génériques. Pour plus d’informations sur l’utilisation de caractères génériques, voir les caractères génériques dans le nom de fichier et le chemin d’accès du dossier ou les [listes d’exclusion d’extension.](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists)
Si vous rencontrez des problèmes avec des règles détectant des fichiers qui, selon vous, ne doivent pas être détectés, utilisez le [mode audit pour tester la règle.](evaluate-attack-surface-reduction.md)

| Description de la règle | GUID |
|:----|:----|
| Empêcher toutes les applications Office de créer des processus enfants | `D4F940AB-401B-4EFC-AADC-AD5F3C50688A` |
| Bloquer l’exécution de scripts potentiellement obscurcis | `5BEB7EFE-FD9A-4556-801D-275E5FFC04CC` |
| Bloquer les appels d’API Win32 à partir Office macro | `92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B` |
| Empêcher Office applications de créer du contenu exécutable | `3B576869-A4EC-4529-8536-B80A7769E899` |
| Empêcher Office applications d’injecter du code dans d’autres processus | `75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84` |
| Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé | `D3E037E1-3EB8-44C8-A917-57927947596D` |
| Bloquer le contenu exécutable du client de messagerie et de la messagerie web | `BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550` |
| Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de listes fiables | `01443614-cd74-433a-b99e-2ecdc07bfc25` |
| Utiliser la protection avancée contre les ransomware | `c1db55ab-c21a-4637-bb3f-a12568109d35` |
| Bloquer le vol d’informations d’identification Windows sous-système d’autorité de sécurité locale (lsass.exe) | `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2` |
| Bloquer les créations de processus provenant de commandes PSExec et WMI | `d1e49aac-8f56-4280-b9ba-993a6d77406c` |
| Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB | `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4` |
| Empêcher Office applications de communication de créer des processus enfants | `26190899-1602-49e8-8b27-eb1d0a1ce869` |
| Empêcher Adobe Reader de créer des processus enfants | `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c` |
| Bloquer la persistance via un abonnement à des événements WMI | `e6db77e5-3df2-4cf1-b95a-636979351e5b` |

Consultez la rubrique [réduction de la surface](attack-surface-reduction.md) d’attaque pour plus d’informations sur chaque règle.

### <a name="use-group-policy-to-exclude-files-and-folders"></a>Utiliser la stratégie de groupe pour exclure des fichiers et des dossiers

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](https://technet.microsoft.com/library/cc731212.aspx), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration** ordinateur et cliquez sur **Modèles d’administration.**

3. Développez l’arborescence **Windows composants Antivirus Microsoft Defender**  >    >  Windows Defender réduction de la surface **d’attaque Exploit Guard.**  >  

4. Double-cliquez sur le **paramètre Exclure les fichiers et** les chemins d’accès du paramètre Règles de réduction de la surface d’attaque et définissez l’option sur **Activé.** Sélectionnez **Afficher** et entrez chaque fichier ou dossier dans la **colonne Nom de la** valeur. Entrez **0 dans** la colonne **Valeur** pour chaque élément.

> [!WARNING]
> N’utilisez pas de guillemets, car ils ne sont pas pris en charge pour la colonne Nom de la valeur ou la **colonne** Valeur. 

### <a name="use-powershell-to-exclude-files-and-folders"></a>Utiliser PowerShell pour exclure des fichiers et des dossiers

1. Tapez **powershell** dans le menu Démarrer, cliquez avec le **bouton droit sur Windows PowerShell** puis **sélectionnez Exécuter en tant qu’administrateur**
2. Entrez l’cmdlet suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

Continuez à `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` utiliser pour ajouter d’autres dossiers à la liste.

> [!IMPORTANT]
> Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste. `Set-MpPreference`L’utilisation de la cmdlet va supprimer la liste existante.

### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Utiliser des CSP mdm pour exclure des fichiers et des dossiers

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) (CSP) pour ajouter des exclusions.

## <a name="customize-the-notification"></a>Personnaliser la notification

Vous pouvez personnaliser la notification pour le déclenchement d’une règle et bloquer une application ou un fichier. Consultez [l’article](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center) Sécurité Windows’article.

## <a name="related-topics"></a>Voir aussi

* [Réduire les surfaces d’attaque avec des règles de réduction de la surface d’attaque](attack-surface-reduction.md)
* [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
* [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
* [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction.md)
