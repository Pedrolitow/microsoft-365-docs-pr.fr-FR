---
title: 'Déploiement des règles de réduction de la surface d’attaque Phase 3 : implémenter'
description: Fournit des conseils pour implémenter le déploiement de vos règles de réduction de la surface d’attaque.
keywords: Déploiement des règles de réduction de la surface d’attaque, déploiement de la réduction de la surface d’attaque, activer les règles d’attaque, configurer la réduction de la surface d’attaque, système de prévention des intrusions hôte, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour le point de terminaison, configurer des règles de réduction de la surface d’attaque
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
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: 74eb07481358de99cd6f78563e1fb37266ebd1e3
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62329013"
---
# <a name="phase-3---implement"></a>Phase 3 : implémenter

La phase d’implémentation déplace l’anneau du test à l’état fonctionnel.

> [!div class="mx-imgBorder"]
> ![Étapes d’implémentation des règles asr](images/asr-rules-implementation-steps.png)

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Étape 1 : Transition des règles de la asr de l’audit au blocage

1. Une fois toutes les exclusions déterminées en mode audit, commencez à définir certaines règles asr en mode « bloquer », en commençant par la règle qui a le moins d’événements déclenchés. Voir « Activer [les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md).
2. Consultez la page de rapports dans le portail Microsoft 365 Defender' ; voir le rapport [sur la protection contre les menaces dans Microsoft Defender for Endpoint](threat-protection-reports.md). Examinez également les commentaires de vos champions de la asr.
3. Affinez les exclusions ou créez de nouvelles exclusions selon les besoins.
4. Revenir aux règles problématiques vers Audit.

  >[!Note]
  >Pour les règles problématiques (règles créant trop de bruit), il est préférable de créer des exclusions plutôt que de désactiver les règles ou de revenir à Audit. Vous devez déterminer ce qui est le mieux pour votre environnement.

  >[!Tip]
  >Lorsque ce paramètre est disponible, tirez parti du paramètre Du mode Avertissement dans les règles pour limiter les perturbations. L’activation des règles asr en mode Avertissement vous permet de capturer les événements déclenchés et d’afficher leurs perturbations potentielles, sans bloquer l’accès des utilisateurs finaux. En savoir plus : [mode d’avertissement pour les utilisateurs](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Comment fonctionne le mode Avertissement ?

Le mode Avertissement est en réalité une instruction bloquer, mais avec la possibilité pour l’utilisateur de « débloquer » les exécutions suivantes du flux ou de l’application donné. Le mode Avertissement se débloque sur une combinaison d’appareils, d’utilisateurs, de fichiers et de processus. Les informations du mode avertissement sont stockées localement et ont une durée de 24 heures.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Étape 2 : développer le déploiement pour sonner n + 1

Lorsque vous êtes certain d’avoir correctement configuré les règles asr pour l’anneau 1, vous pouvez élargir l’étendue de votre déploiement à l’anneau suivant (anneau n + 1).

Le processus de déploiement, étapes 1 à 3, est essentiellement le même pour chaque anneau suivant :

1. Règles de test dans Audit
2. Passer en revue les événements d’audit déclenchés par la asr dans le portail Microsoft 365 Defender de recherche
3. Créer des exclusions
4. Révision : affiner, ajouter ou supprimer des exclusions si nécessaire
5. Définir des règles sur « bloquer »
6. Examinez la page de rapports dans le portail Microsoft 365 Defender web.
7. Créez des exclusions.
8. Désactivez les règles problématiques ou revenir à Audit.

#### <a name="customize-attack-surface-reduction-rules"></a>Personnaliser les règles de réduction de la surface d’attaque

Lorsque vous continuez à développer le déploiement de vos règles de réduction de la surface d’attaque, il peut s’avérer nécessaire ou utile de personnaliser les règles de réduction de la surface d’attaque que vous avez activées.

##### <a name="exclude-files-and-folders"></a>Exclure des fichiers et des dossiers

Vous pouvez choisir d’exclure les fichiers et dossiers de l’évaluation par les règles de réduction de la surface d’attaque. Lorsqu’il est exclu, l’exécution du fichier n’est pas bloquée même si une règle de réduction de la surface d’attaque détecte que le fichier contient un comportement malveillant.

Par exemple, prenons la règle de ransomware :

La règle de ransomware est conçue pour aider les clients d’entreprise à réduire les risques d’attaques par ransomware tout en assurant la continuité de l’activité. Par défaut, les erreurs de règle de ransomware du côté de la prudence et la protection contre les fichiers qui n’ont pas encore atteint une réputation et une confiance suffisantes. Pour reéphaser, la règle de ransomware se déclenche uniquement sur les fichiers qui n’ont pas acquis une réputation et une prévalence positives suffisantes, en fonction des mesures d’utilisation de millions de nos clients. En règle générale, les blocs sont auto-résolus, car les valeurs « réputation et confiance » de chaque fichier sont mises à niveau de manière incrémentielle à mesure que l’utilisation non problématique augmente.

Dans les cas où les blocs ne sont pas résolus en temps voulu, les clients peuvent,  à leurs propres risques, utiliser le mécanisme en libre-service ou une fonctionnalité de « liste d’autoriser » basée sur l’indicateur de compromis (IOC) pour débloquer les fichiers eux-mêmes.

> [!WARNING]
> L’exclusion ou le déblocage de fichiers ou de dossiers pourrait potentiellement permettre à des fichiers non sécurisés de s’exécuter et d’infecter vos appareils. L’exclusion des fichiers ou dossiers peut considérablement réduire la protection fournie par les règles de réduction de la surface d’attaque. Les fichiers qui auraient été bloqués par une règle seront autorisés à s’exécuter et aucun rapport ou événement n’est enregistré.

Une exclusion s’applique à toutes les règles qui autorisent les exclusions. Vous pouvez spécifier un fichier, un chemin d’accès de dossier ou le nom de domaine complet d’une ressource. Toutefois, vous ne pouvez pas limiter une exclusion à une règle spécifique.

Une exclusion est appliquée uniquement au démarrage de l’application ou du service exclu. Par exemple, si vous ajoutez une exclusion pour un service de mise à jour déjà en cours d’exécution, le service de mise à jour continue à déclencher des événements jusqu’à ce que le service soit arrêté et redémarré.

La réduction de la surface d’attaque prend en charge les variables d’environnement et les caractères génériques. Pour plus d’informations sur l’utilisation de caractères génériques, voir les [caractères génériques dans les listes d’exclusions](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) de nom de fichier et de dossier ou d’extension.
Si vous rencontrez des problèmes avec les règles qui détectent des fichiers qui, selon vous, ne doivent pas être détectés, utilisez le [mode audit pour tester la règle](evaluate-attack-surface-reduction.md).

Consultez la rubrique [de référence des règles de réduction de la surface](attack-surface-reduction-rules-reference.md) d’attaque pour plus d’informations sur chaque règle.

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Utiliser une stratégie de groupe pour exclure des fichiers et des dossiers

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](https://technet.microsoft.com/library/cc731212.aspx), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. Dans **l’Éditeur de gestion des stratégies** de groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration**.

3. Développez l’arborescence **Windows composants Antivirus Microsoft Defender** \>  \> **Protection contre les attaques Microsoft Defender réduction de la surface** **d’attaque**\>.

4. Double-cliquez sur le **paramètre Exclure les fichiers et les** chemins d’accès du paramètre Règles de réduction de la surface d’attaque et définissez l’option **sur Activé**. **Sélectionnez Afficher** et entrez chaque fichier ou dossier dans la **colonne Nom de la** valeur. Entrez **0 dans** la colonne **Valeur** pour chaque élément.

> [!WARNING]
> N’utilisez pas de guillemets, car ils  ne sont pas pris en charge pour la colonne Nom de la valeur ou la **colonne** Valeur.

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Utiliser PowerShell pour exclure des fichiers et des dossiers

1. **Tapez powershell** dans le menu Démarrer, cliquez avec le **bouton droit sur Windows PowerShell** puis **sélectionnez Exécuter en tant qu’administrateur**.

2. Entrez l’cmdlet suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Continuez à l’utiliser `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` pour ajouter d’autres dossiers à la liste.

    > [!IMPORTANT]
    > Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste. L’utilisation `Set-MpPreference` de la cmdlet va supprimer la liste existante.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Utiliser des CSP mdm pour exclure des fichiers et des dossiers

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) (CSP) pour ajouter des exclusions.

##### <a name="customize-the-notification"></a>Personnaliser la notification

Vous pouvez personnaliser la notification lorsqu’une règle est déclenchée et bloque une application ou un fichier. Consultez l [Sécurité Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center) article.

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiements

[Vue d’ensemble du déploiement des règles ASR](attack-surface-reduction-rules-deployment.md)

[Phase 1 : Planifier](attack-surface-reduction-rules-deployment-plan.md)

[Phase 2 : Tester](attack-surface-reduction-rules-deployment-test.md)

[Phase 4 : Opérationnaliser](attack-surface-reduction-rules-deployment-operationalize.md)
