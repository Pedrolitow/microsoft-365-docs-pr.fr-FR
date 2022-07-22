---
title: Activer des règles de réduction de la surface d’attaque (ASR)
description: Fournit des conseils pour implémenter votre déploiement de règles de réduction de la surface d’attaque.
keywords: Déploiement de règles de réduction de la surface d’attaque, déploiement ASR, activer des règles asr, configurer asr, système de prévention des intrusions de l’hôte, règles de protection, règles anti-exploitation, règles d’exploitation, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles ASR
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- M365-security-compliance
- m365solution-asr-rules
ms.date: 1/18/2022
ms.openlocfilehash: a1db97410de095314de6fb75acc5394ab18bc6c6
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969702"
---
# <a name="enable-attack-surface-reduction-asr-rules"></a>Activer des règles de réduction de la surface d’attaque (ASR)

L’implémentation de règles de réduction de la surface d’attaque (ASR) déplace le premier anneau de test dans un état fonctionnel activé.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-implementation-steps.png" alt-text="Procédure d’implémentation des règles ASR" lightbox="images/asr-rules-implementation-steps.png":::
  

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Étape 1 : Passer des règles ASR de l’audit au bloc

1. Une fois toutes les exclusions déterminées en mode audit, commencez à définir certaines règles ASR sur le mode « bloquer », en commençant par la règle qui a le moins d’événements déclenchés. Voir « [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md).
2. Consultez la page de création de rapports dans le portail Microsoft 365 Defender ; consultez le [rapport sur la protection contre les menaces dans Microsoft Defender pour point de terminaison](threat-protection-reports.md). Passez également en revue les commentaires de vos champions ASR.
3. Affinez les exclusions ou créez de nouvelles exclusions si nécessaire.
4. Rebasculez les règles problématiques vers Audit.

  >[!Note]
  >Pour les règles problématiques (règles créant trop de bruit), il est préférable de créer des exclusions plutôt que de désactiver les règles ou de revenir à Audit. Vous devrez déterminer ce qui convient le mieux à votre environnement.

  >[!Tip]
  >Lorsqu’il est disponible, tirez parti du paramètre de mode d’avertissement dans les règles pour limiter les interruptions. L’activation des règles ASR en mode Avertir vous permet de capturer les événements déclenchés et d’afficher leurs interruptions potentielles, sans bloquer réellement l’accès de l’utilisateur final. En savoir plus : [Mode d’avertissement pour les utilisateurs](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Comment fonctionne le mode Avertir ?

Le mode d’avertissement est en fait une instruction Block, mais avec l’option permettant à l’utilisateur de « débloquer » les exécutions suivantes du flux ou de l’application donné. Le mode Avertir se débloque sur une combinaison d’appareils, d’utilisateurs, de fichiers et de processus. Les informations du mode d’avertissement sont stockées localement et ont une durée de 24 heures.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Étape 2 : Développer le déploiement pour sonner n + 1

Lorsque vous êtes certain d’avoir correctement configuré les règles ASR pour l’anneau 1, vous pouvez étendre l’étendue de votre déploiement à l’anneau suivant (anneau n + 1).

Le processus de déploiement, étapes 1 à 3, est essentiellement le même pour chaque anneau suivant :

1. Règles de test dans Audit
2. Examiner les événements d’audit déclenchés par ASR dans le portail Microsoft 365 Defender
3. Créer des exclusions
4. Révision : affiner, ajouter ou supprimer des exclusions si nécessaire
5. Définir des règles sur « bloquer »
6. Passez en revue la page de création de rapports dans le portail Microsoft 365 Defender.
7. Créez des exclusions.
8. Désactivez les règles problématiques ou revenez à Audit.

#### <a name="customize-attack-surface-reduction-rules"></a>Personnaliser les règles de réduction de la surface d’attaque

Au fur et à mesure que vous développez votre déploiement de règles de réduction de la surface d’attaque, vous pouvez trouver nécessaire ou avantageux de personnaliser les règles de réduction de la surface d’attaque que vous avez activées.

##### <a name="exclude-files-and-folders"></a>Exclure des fichiers et des dossiers

Vous pouvez choisir d’exclure les fichiers et dossiers de l’évaluation par les règles de réduction de la surface d’attaque. En cas d’exclusion, l’exécution du fichier n’est pas bloquée même si une règle de réduction de la surface d’attaque détecte que le fichier contient un comportement malveillant.

Prenons l’exemple de la règle de ransomware :

La règle de ransomware est conçue pour aider les clients d’entreprise à réduire les risques d’attaques par ransomware tout en assurant la continuité de l’activité. Par défaut, les erreurs de règle de ransomware du côté de la prudence et se protègent contre les fichiers qui n’ont pas encore atteint la réputation et la confiance suffisantes. Pour réemphaser, la règle de ransomware se déclenche uniquement sur les fichiers qui n’ont pas acquis une réputation et une prévalence positives suffisantes, en fonction des métriques d’utilisation de millions de nos clients. En règle générale, les blocs sont auto-résolus, car les valeurs de « réputation et d’approbation » de chaque fichier sont mises à niveau de manière incrémentielle à mesure que l’utilisation non problématique augmente.

Dans les cas où les blocs ne sont pas auto-résolus en temps voulu, les clients peuvent, _à leurs risques et périls_ , utiliser le mécanisme en libre-service ou une fonctionnalité « liste verte » basée sur l’indicateur de compromission (IOC) pour débloquer eux-mêmes les fichiers.

> [!WARNING]
> L’exclusion ou le déblocage de fichiers ou de dossiers peut potentiellement permettre l’exécution et l’infection de fichiers non sécurisés sur vos appareils. L’exclusion des fichiers ou dossiers peut considérablement réduire la protection fournie par les règles de réduction de la surface d’attaque. Les fichiers qui auraient été bloqués par une règle seront autorisés à s’exécuter, et aucun rapport ou événement n’est enregistré.

Une exclusion s’applique à toutes les règles qui autorisent les exclusions. Vous pouvez spécifier un fichier individuel, un chemin d’accès de dossier ou le nom de domaine complet d’une ressource. Toutefois, vous ne pouvez pas limiter une exclusion à une règle spécifique.

Une exclusion n’est appliquée qu’au démarrage de l’application ou du service exclu. Par exemple, si vous ajoutez une exclusion pour un service de mise à jour qui est déjà en cours d’exécution, le service de mise à jour continue de déclencher des événements jusqu’à ce que le service soit arrêté et redémarré.

La réduction de la surface d’attaque prend en charge les variables d’environnement et les caractères génériques. Pour plus d’informations sur l’utilisation de caractères génériques, consultez [utiliser des caractères génériques dans les listes d’exclusions de nom de fichier et de dossier ou d’extension](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).
Si vous rencontrez des problèmes avec des règles qui détectent des fichiers qui ne doivent pas être détectés, [utilisez le mode audit pour tester la règle](evaluate-attack-surface-reduction.md).

Pour plus d’informations sur chaque règle, consultez la rubrique de référence sur les [règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md) .

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Utiliser stratégie de groupe pour exclure des fichiers et des dossiers

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](https://technet.microsoft.com/library/cc731212.aspx), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur**, puis cliquez sur **Modèles d’administration**.

3. Développez l’arborescence sur **les composants** \> Windows de **l’antivirus** \> **Microsoft Defender Microsoft Defender Exploit Guard** \> **Pour réduire la surface d’attaque**.

4. Double-cliquez sur le paramètre **Exclure les fichiers et les chemins d’accès du paramètre Règles de réduction de la surface d’attaque** et définissez l’option **sur Activé**. Sélectionnez **Afficher** et entrez chaque fichier ou dossier dans la colonne **Nom de** la valeur. Entrez **0** dans la colonne **Valeur** de chaque élément.

> [!WARNING]
> N’utilisez pas de guillemets, car ils ne sont pas pris en charge pour la colonne **Nom** de la valeur ou la colonne **Valeur** .

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Utiliser PowerShell pour exclure des fichiers et des dossiers

1. Tapez **powershell** dans le menu Démarrer, cliquez avec le bouton droit sur **Windows PowerShell** et sélectionnez **Exécuter en tant qu’administrateur**.

2. Entrez l’applet de commande suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Continuez à utiliser `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` pour ajouter d’autres dossiers à la liste.

    > [!IMPORTANT]
    > Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste. L’utilisation de l’applet `Set-MpPreference` de commande remplace la liste existante.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Utiliser des CSP GPM pour exclure des fichiers et des dossiers

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) (CSP) pour ajouter des exclusions.

##### <a name="customize-the-notification"></a>Personnaliser la notification

Vous pouvez personnaliser la notification lorsqu’une règle est déclenchée et bloque une application ou un fichier. Consultez l’article [Sécurité Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center).

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiement

[Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment.md)

[Planifier le déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Tester des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-test.md)

[Utiliser des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

[Référence des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-reference.md)
