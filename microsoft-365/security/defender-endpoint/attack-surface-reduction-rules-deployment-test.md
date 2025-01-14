---
title: Tester des règles de réduction de la surface d’attaque (ASR)
description: Fournit des conseils pour tester le déploiement de vos règles de réduction de la surface d’attaque (ASR). Microsoft Defender pour point de terminaison (MDE) test ASR inclut, auditer les règles ASR defender, configurer des règles ASR à l’aide de MEM, rapports de règles Microsoft ASR, exclusions de règles ASR, observateur d’événements de règles ASR.
keywords: Microsoft Defender pour point de terminaison (MDE) Déploiement de règles de réduction de la surface d’attaque (ASR), guide de réduction de la surface d’attaque, déploiement ASR, règles asr de test, exclusions de règles ASR, Microsoft ASR, configurer des règles ASR, bonnes pratiques en matière de réduction de la surface d’attaque, réduction de la surface d’attaque intune, observateur d’événements de règles ASR, défenseur de la réduction de la surface d’attaque, powershell de règles asr, réduction de la surface d’attaque  bonne pratique, désactiver les règles ASR, le système de prévention des intrusions de l’hôte, les règles de protection, les règles de lutte contre l’exploitation, les règles d’exploitation, les règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer les règles ASR
search.product: eADQiWindows 10XVcnh
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.topic: conceptual
ms.collection:
- m365-security
- m365solution-asr-rules
- highpri
- tier1
ms.date: 09/18/2022
search.appverid: met150
ms.openlocfilehash: 697f8352cc23c1379d756ceda95b83bd299b0d52
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68632115"
---
# <a name="test-attack-surface-reduction-asr-rules"></a>Tester des règles de réduction de la surface d’attaque (ASR)

Le test des règles de réduction de la surface d’attaque (ASR) Microsoft Defender pour point de terminaison (MDE) vous permet de déterminer si les règles entravent les opérations métier avant d’activer une règle. En commençant par un petit groupe contrôlé, vous pouvez limiter les interruptions de travail potentielles à mesure que vous développez votre déploiement au sein de votre organisation.

Dans cette section du guide de déploiement des règles ASR, vous allez apprendre à :

- configurer des règles à l’aide de MEM
- utiliser Microsoft Defender pour point de terminaison rapports de règles ASR
- configurer des exclusions de règles ASR
- activer des règles ASR à l’aide de PowerShell
- utiliser observateur d'événements pour les événements de règles ASR

> [!NOTE]
> Avant de commencer à tester les règles ASR, il est recommandé de désactiver d’abord toutes les règles que vous avez précédemment définies pour **auditer** ou **activer** (le cas échéant). Consultez [les rapports de règles de réduction de la surface](attack-surface-reduction-rules-report.md) d’attaque pour plus d’informations sur l’utilisation du rapport de règles ASR pour désactiver les règles ASR.

Commencez le déploiement de vos règles de réduction de la surface d’attaque (ASR) avec l’anneau 1.

> :::image type="content" source="images/asr-rules-testing-steps.png" alt-text="Étapes de test de la réduction de la surface d’attaque (règles ASR) Microsoft Defender pour point de terminaison (MDE). Auditez les règles ASR, configurez les exclusions de règles ASR. Configurez les règles ASR MEM. Exclusions de règles ASR. Visionneuse d’événements des règles ASR." lightbox="images/asr-rules-testing-steps.png":::
  
## <a name="step-1-test-asr-rules-using-audit"></a>Étape 1 : Tester des règles ASR à l’aide de l’audit

Commencez la phase de test en activant les règles ASR avec les règles définies sur Audit, en commençant par vos utilisateurs ou appareils champions dans l’anneau 1. En règle générale, il est recommandé d’activer toutes les règles (dans Audit) afin de pouvoir déterminer les règles qui sont déclenchées pendant la phase de test. Notez que les règles définies sur Audit n’ont généralement pas d’impact sur les fonctionnalités de l’entité ou des entités auxquelles la règle est appliquée, mais génèrent des événements journalisés pour l’évaluation ; il n’y a aucun effet sur les utilisateurs finaux.

### <a name="configure-asr-rules-using-mem"></a>Configurer des règles ASR à l’aide de MEM

Vous pouvez utiliser Microsoft Endpoint Manager (MEM) Endpoint Security pour configurer des règles ASR personnalisées.

1. Ouvrez le [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home).
2. Accédez à **Endpoint Security** > **Attack Surface Reduction**.
3. Sélectionner **Créer une stratégie**.
4. Dans **Plateforme**, sélectionnez **Windows 10 et versions ultérieures**, puis, dans **Profil**, sélectionnez **Règles de réduction de la surface d’attaque**.
  
    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-create-profile.png" alt-text="Page de création de profil pour les règles ASR" lightbox="images/asr-mem-create-profile.png":::

5. Cliquez sur **Créer**.
6. Sous l’onglet **De base** du volet **Créer un profil** , dans **Nom** , ajoutez un nom pour votre stratégie. Dans **Description** , ajoutez une description de votre stratégie de règles ASR.
7. Sous l’onglet **Paramètres de configuration** , sous **Règles de réduction de la surface d’attaque**, définissez toutes les règles en **mode Audit**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-configuration-settings.png" alt-text="Configuration des règles ASR en mode Audit" lightbox="images/asr-mem-configuration-settings.png":::

    >[!Note]
    >Il existe des variantes dans certaines listes de mode de règles ASR ; _Les fonctionnalités bloquées_ et _activées_ fournissent les mêmes fonctionnalités.

8. [Facultatif] Dans le volet **Balises d’étendue** , vous pouvez ajouter des informations de balise à des appareils spécifiques. Vous pouvez également utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour vous assurer que les administrateurs appropriés disposent de l’accès et de la visibilité appropriés aux objets Intune appropriés. En savoir plus : [Utilisez le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué dans Intune](/mem/intune/fundamentals/scope-tags).
9. Dans le volet **Affectations** , vous pouvez déployer ou « affecter » le profil à vos groupes d’utilisateurs ou d’appareils. En savoir plus : [Affecter des profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
   
    >[!Note]
    > La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.

1. Passez en revue vos paramètres dans le volet **Vérifier + créer** . Cliquez sur **Créer** pour appliquer les règles.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-review-create.png" alt-text="Page Créer un profil" lightbox="images/asr-mem-review-create.png":::

Votre nouvelle stratégie de réduction de la surface d’attaque pour les règles ASR est répertoriée dans **| Réduction de la surface d’attaque**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-my-asr-rules.png" alt-text=" Page Réduction de la surface d’attaque" lightbox="images/asr-mem-my-asr-rules.png":::

## <a name="step-2-understand-the-asr-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Étape 2 : Comprendre la page de création de rapports de règles ASR dans le portail Microsoft 365 Defender

La page de création de rapports de règles ASR se trouve dans **Microsoft 365 Defender portail** > **signale les** > **règles de réduction de la surface d’attaque**. Cette page comporte trois onglets :

- Detections
- Configuration
- Ajouter des exclusions

### <a name="detections-tab"></a>Onglet Détections

Fournit une chronologie de 30 jours des événements d’audit détectés et bloqués.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01.png" alt-text="Onglet Détections des règles de réduction de la surface d’attaque" lightbox="images/asr-defender365-01.png":::

Le volet règles de réduction de la surface d’attaque fournit une vue d’ensemble des événements détectés par règle.

>[!Note]
>Il existe certaines variantes dans les rapports de règles ASR. Microsoft est en train de mettre à jour le comportement des rapports de règles ASR pour fournir une expérience cohérente.

> :::image type="content" source="images/asr-defender365-01b.png" alt-text="Page Règles de réduction de la surface d’attaque" lightbox="images/asr-defender365-01b.png":::

Cliquez sur **Afficher les détections** pour ouvrir l’onglet **Détections** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Détections des règles de réduction de la surface d’attaque" lightbox="images/asr-defender365-reports-detections.png":::

Les **volets GroupBy** et **Filter** fournissent les options suivantes :

**GroupBy** retourne les résultats définis sur les groupes suivants :

- Aucun regroupement
- Fichier détecté
- Auditer ou bloquer
- Rule
- Application source
- Device
- Utilisateur
- Éditeur

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Les règles de réduction de la surface d’attaque détectent le filtre GroupBy" lightbox="images/asr-defender365-reports-detections.png":::

**Le filtre** ouvre la page **Filtrer sur les règles** , ce qui vous permet d’étendre les résultats aux seules règles ASR sélectionnées :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-filter.png" alt-text="Filtre des règles de réduction de la surface d’attaque sur les règles" lightbox="images/asr-defender365-filter.png":::

>[!Note]
>Si vous disposez d’une licence Microsoft Microsoft 365 Security E5 ou A5, Windows E5 ou A5, le lien suivant ouvre l’onglet Microsoft Defender rapports 365 > [réductions de la surface d’attaque](https://security.microsoft.com/asr?viewid=detections) > l’onglet Détections.

### <a name="configuration-tab"></a>Onglet Configuration

Répertorie, par ordinateur, l’état agrégé des règles ASR : Désactivé, Audit, Bloquer.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.png" alt-text="Onglet Configuration des règles de réduction de la surface d’attaque et entrée dans sa page" lightbox="images/asr-defender365-configurations.png":::

Sous l’onglet Configurations, vous pouvez vérifier, par appareil, quelles règles ASR sont activées et dans quel mode, en sélectionnant l’appareil pour lequel vous souhaitez passer en revue les règles ASR.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.settings.png" alt-text="Règles de réduction de la surface d’attaque activées et mode" lightbox="images/asr-defender365-configurations.settings.png":::

Le lien **Prise en main** ouvre le Centre d’administration Microsoft Endpoint Manager, où vous pouvez créer ou modifier une stratégie de protection des points de terminaison pour ASR :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem1.png" alt-text="Élément de menu sécurité *Point de terminaison sur la page Vue d’ensemble" lightbox="images/asr-defender365-05b-mem1.png":::

Dans | de sécurité de point de terminaison Vue d’ensemble, sélectionnez **Réduction de la surface d’attaque** :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem2.png" alt-text="Réduction de la surface d’attaque dans MEM" lightbox="images/asr-defender365-05b-mem2.png":::

| de sécurité du point de terminaison Le volet réduction de la surface d’attaque s’ouvre :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem3.png" alt-text="Volet Réduction de la surface d’attaque de sécurité du point de terminaison" lightbox="images/asr-defender365-05b-mem3.png":::

>[!Note]
>Si vous disposez d’une licence Microsoft Defender 365 E5 (ou Windows E5?), ce lien ouvre l’onglet Microsoft Defender 365 Rapports > Réductions de la surface d’attaque > [l’onglet Configurations](https://security.microsoft.com/asr?viewid=configuration).

### <a name="add-exclusions"></a>Ajouter des exclusions

Cet onglet fournit une méthode permettant de sélectionner les entités détectées (par exemple, les faux positifs) à exclure. Lorsque des exclusions sont ajoutées, le rapport fournit un résumé de l’impact attendu.

>[!Note]
> Microsoft Defender les exclusions d’antivirus av sont respectées par les règles ASR.  Consultez [Configurer et valider les exclusions en fonction de l’extension, du nom ou de l’emplacement](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="Images/asr-defender365-06d.png" alt-text="Volet d’exclusion du fichier détecté" lightbox="Images/asr-defender365-06d.png":::

> [!Note]
>Si vous disposez d’une licence Microsoft Defender 365 E5 (ou Windows E5?), ce lien ouvre l’onglet Microsoft Defender 365 Rapports > Réductions de la surface d’attaque [>'onglet Exclusions](https://security.microsoft.com/asr?viewid=exclusions).

Pour plus d’informations sur l’utilisation du rapport de règles ASR pour gérer les règles ASR, consultez [les rapports sur les règles de réduction de la surface d’attaque](attack-surface-reduction-rules-report.md).

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>Utiliser PowerShell comme méthode alternative pour activer les règles ASR

Vous pouvez utiliser PowerShell - comme alternative à MEM - pour activer les règles ASR en mode audit afin d’afficher un enregistrement des applications qui auraient été bloquées si la fonctionnalité était entièrement activée. Vous pouvez également avoir une idée de la fréquence à laquelle les règles seront déclenchées lors d’une utilisation normale.

Pour activer une règle de réduction de la surface d’attaque en mode audit, utilisez l’applet de commande PowerShell suivante :

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Où `<rule ID>` est une [valeur GUID de la règle de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md).

Pour activer toutes les règles de réduction de la surface d’attaque ajoutées en mode audit, utilisez l’applet de commande PowerShell suivante :

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Si vous souhaitez auditer entièrement le fonctionnement des règles de réduction de la surface d’attaque dans votre organisation, vous devez utiliser un outil de gestion pour déployer ce paramètre sur les appareils de votre réseau.

Vous pouvez également utiliser stratégie de groupe, Intune ou des fournisseurs de services de configuration de gestion des appareils mobiles (MDM) pour configurer et déployer le paramètre. Pour en savoir plus, consultez l’article principal [sur les règles de réduction de la surface d’attaque](attack-surface-reduction.md) .

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Utilisez Windows observateur d'événements Review comme alternative à la page de création de rapports sur les règles de réduction de la surface d’attaque dans le portail Microsoft 365 Defender

Pour examiner les applications qui auraient été bloquées, ouvrez observateur d'événements et filtrez l’ID d’événement 1121 dans le journal Microsoft-Windows-Windows Defender/Operational. Le tableau suivant répertorie tous les événements de protection réseau.

ID d’événement | Description
-|-
 5007 | Événement lorsque les paramètres sont modifiés
 1121 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode bloc
 1122 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode audit

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiement

[Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment.md)

[Planifier le déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Activer des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-implement.md)

[Utiliser des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

[Référence des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-reference.md)
