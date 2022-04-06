---
title: Tester les règles de réduction de la surface d’attaque (ASR)
description: Fournit des conseils pour tester le déploiement de règles de réduction de la surface d’attaque (ASR).
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
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 2f3a97da3eff16a639df995d88b9ceda91497f11
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475408"
---
# <a name="step-2-test-asr-rules"></a>Étape 2 : Tester les règles ASR

Le test des règles de réduction de la surface d’attaque (ASR) vous permet de déterminer si les règles empêcheront les opérations d’entreprise avant d’activer une règle. En commençant par un petit groupe contrôlé, vous pouvez limiter les interruptions de travail potentielles à mesure que vous développez votre déploiement au sein de votre organisation.

Commencez le déploiement des règles de réduction de la surface d’attaque (ASR) avec l’anneau 1.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-testing-steps.png" alt-text="Étapes de test des règles asr" lightbox="images/asr-rules-testing-steps.png":::
  

## <a name="step-1-test-asr-rules-using-audit"></a>Étape 1 : Tester les règles de la asr à l’aide de l’audit

Commencez la phase de test en 2013 en 2013, en 2013, en 2013, en 2013. En règle générale, il est recommandé d’activer toutes les règles (dans Audit) afin de pouvoir déterminer les règles déclenchées au cours de la phase de test. Notez que les règles définies sur Audit n’ont généralement pas d’impact sur les fonctionnalités de l’entité ou des entités à laquelle la règle est appliquée, mais génèrent des événements consignés pour l’évaluation ; n’a aucun effet sur les utilisateurs finaux.

### <a name="configure-asr-rules-using-mem"></a>Configurer des règles asr à l’aide de MEM

Vous pouvez utiliser Microsoft Endpoint Manager de point de terminaison (MEM) pour configurer des règles asr personnalisées.

1. Ouvrez [Microsoft Endpoint Manager centre d’administration.](https://endpoint.microsoft.com/#home)
2. Go to **Endpoint SecurityAttack** >  **surface reduction**.
3. Sélectionner **Créer une stratégie**.
4. Dans **Plateforme**, sélectionnez **Windows 10 et ultérieures**, puis dans **Profil**, sélectionnez Règles de réduction **de la surface d’attaque**.
  
    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-create-profile.png" alt-text="Page de création de profil pour les règles de la asr." lightbox="images/asr-mem-create-profile.png":::

5. Cliquez sur **Créer**.
6. Dans **l’onglet De** base **du volet Créer** un profil, dans  Nom, ajoutez un nom pour votre stratégie. Dans **description** , ajoutez une description pour votre stratégie de règles de asr.
7. Dans **l’onglet Paramètres de configuration** , sous Règles de réduction de **la surface** d’attaque, définissez toutes les règles en **mode Audit**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-configuration-settings.png" alt-text="Configuration des règles asr en mode Audit" lightbox="images/asr-mem-configuration-settings.png":::

    >[!Note]
    >Il existe des variantes dans certaines listes en mode de règles de récupération automatique ; _Bloqués_ _et activés_ fournissent les mêmes fonctionnalités.

8. [Facultatif] Dans le volet **Balises d’étendue** , vous pouvez ajouter des informations de balise à des appareils spécifiques. Vous pouvez également utiliser des balises de contrôle d’accès et d’étendue basées sur les rôles pour vous assurer que les administrateurs qui ont les droits d’accès et de visibilité sur les objets Intune de droite. En savoir plus : [utilisez le contrôle d’accès basé sur un rôle (RBAC) et les balises d’étendue pour le service it distribué dans Intune](/mem/intune/fundamentals/scope-tags).
9. Dans le **volet Affectations** , vous pouvez déployer ou « affecter » le profil à vos groupes d’utilisateurs ou d’appareils. En savoir plus : [attribuer des profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. Examinez vos paramètres dans le **volet Révision +** Créer. Cliquez **sur Créer** pour appliquer les règles.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-review-create.png" alt-text="Page Créer un profil" lightbox="images/asr-mem-review-create.png":::

Votre nouvelle stratégie de réduction de la surface d’attaque pour les règles de réduction de la surface d’attaque est répertoriée dans **endpoint security | Réduction de la surface d’attaque**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-my-asr-rules.png" alt-text=" Page Réduction de la surface d’attaque" lightbox="images/asr-mem-my-asr-rules.png":::

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Étape 2 : Comprendre la page rapports des règles de réduction de la surface d’attaque dans le portail Microsoft 365 Defender attaque

La page de rapport des règles de réduction de la surface d’attaque **se trouve Microsoft 365 Defender règles** de réduction de **la surface** **portalReportsAttack** >  > . Cette page possède trois onglets :

- Detections
- Configuration
- Ajouter des exclusions

### <a name="detections-tab"></a>Onglet Détections

Fournit une chronologie de 30 jours des événements d’audit et bloqués détectés.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01.png" alt-text="Onglet Détections des règles de réduction de la surface d’attaque" lightbox="images/asr-defender365-01.png":::

Le volet Règles de réduction de la surface d’attaque fournit une vue d’ensemble des événements détectés par règle.

>[!Note]
>Il existe certaines variantes dans les rapports de règles de la asr. Microsoft est en train de mettre à jour le comportement des rapports de règles de la asr afin de fournir une expérience cohérente.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01b.png" alt-text="Page Règles de réduction de la surface d’attaque" lightbox="images/asr-defender365-01b.png"::: 

Cliquez **sur Afficher les détections** pour ouvrir **l’onglet Détections** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Détections des règles de réduction de la surface d’attaque" lightbox="images/asr-defender365-reports-detections.png":::

Le **volet GroupBy** et **Filter** offre les options suivantes :

**GroupBy renvoie** le jeu de résultats aux groupes suivants :

- Aucun regroupement
- Fichier détecté
- Auditer ou bloquer
- Rule
- Application source
- Device
- Utilisateur
- Éditeur

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Filtre GroupBy des règles de réduction de la surface d’attaque" lightbox="images/asr-defender365-reports-detections.png":::

**Le** filtre ouvre la page **Filtrer sur les** règles, qui vous permet d’étenduer les résultats uniquement aux règles asr sélectionnées :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-filter.png" alt-text="Filtre des règles de réduction de la surface d’attaque sur les règles" lightbox="images/asr-defender365-filter.png":::

>[!Note]
>Si vous avez une licence Microsoft Microsoft 365 Security E5 ou A5, Windows E5 ou A5, le lien suivant ouvre l’onglet Microsoft Defender 365 Reports > [Attack surface reductions](https://security.microsoft.com/asr?viewid=detections) > Detections.

### <a name="configuration-tab"></a>Onglet Configuration

Répertorie, par ordinateur, l’état d’agrégation des règles de la asr : Hors, Audit, Bloquer.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.png" alt-text="Onglet Configuration des règles de réduction de la surface d’attaque et entrée dans sa page" lightbox="images/asr-defender365-configurations.png":::

Sous l’onglet Configurations, vous pouvez vérifier, par appareil, quelles règles de récupération automatique sont activées et dans quel mode, en sélectionnant l’appareil pour lequel vous souhaitez passer en revue les règles de la asr.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.settings.png" alt-text="Règles de réduction de la surface d’attaque activées et mode" lightbox="images/asr-defender365-configurations.settings.png":::

Le **lien De mise** en Microsoft Endpoint Manager ouvre le Centre d’administration Microsoft Endpoint Manager, où vous pouvez créer ou modifier une stratégie de protection de point de terminaison pour la asr.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem1.png" alt-text="Élément de menu de sécurité *Point de terminaison dans la page Vue d’ensemble" lightbox="images/asr-defender365-05b-mem1.png":::

Dans endpoint security | Vue d’ensemble, sélectionnez **Réduction de la surface d’attaque** :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem2.png" alt-text="Réduction de la surface d’attaque dans mem" lightbox="images/asr-defender365-05b-mem2.png":::

Le point de terminaison de sécurité | Le volet Réduction de la surface d’attaque s’ouvre :

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem3.png" alt-text="Volet Réduction de la surface d’attaque du point de terminaison" lightbox="images/asr-defender365-05b-mem3.png":::

>[!Note]
>Si vous avez une licence Microsoft Defender 365 E5 (ou Windows E5 ?), ce lien ouvre l’onglet [Configurations](https://security.microsoft.com/asr?viewid=configuration) des rapports Microsoft Defender 365 > réductions de la surface d'>.

### <a name="add-exclusions"></a>Ajouter des exclusions

Cet onglet fournit une méthode pour sélectionner les entités détectées (par exemple, les faux positifs) pour l’exclusion. Lorsque des exclusions sont ajoutées, le rapport fournit un résumé de l’impact attendu.

>[!Note]
> Antivirus Microsoft Defender exclusions av sont honorées par les règles de la asr.  Voir [Configurer et valider les exclusions en fonction de l’extension, du nom ou de l’emplacement](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="Images/asr-defender365-06d.png" alt-text="Volet d’exclusion du fichier détecté" lightbox="Images/asr-defender365-06d.png":::

> [!Note]
>Si vous avez une licence Microsoft Defender 365 E5 (ou Windows E5 ?), ce lien ouvre l’onglet Réductions de la surface d’attaque de Microsoft Defender 365 > > [Exclusions](https://security.microsoft.com/asr?viewid=exclusions).

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>Utiliser PowerShell comme méthode alternative pour activer les règles de la asr

Vous pouvez utiliser PowerShell , comme alternative à MEM, pour activer les règles asr en mode audit afin d’afficher un enregistrement des applications qui auraient été bloquées si la fonctionnalité était entièrement activée. Vous pouvez également avoir une idée de la fréquence de tir des règles lors d’une utilisation normale.

Pour activer une règle de réduction de la surface d’attaque en mode audit, utilisez l’cmdlet PowerShell suivante :

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Où se `<rule ID>` trouve une valeur [GUID de la règle de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md).

Pour activer toutes les règles de réduction de la surface d’attaque ajoutées en mode audit, utilisez l’cmdlet PowerShell suivante :

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Si vous souhaitez auditer entièrement le fonctionnement des règles de réduction de la surface d’attaque dans votre organisation, vous devez utiliser un outil de gestion pour déployer ce paramètre sur les appareils de votre réseau.

Vous pouvez également utiliser une stratégie de groupe, Intune ou des fournisseurs de services de configuration (CSP) de gestion des périphériques mobiles (CSP) pour configurer et déployer le paramètre. En savoir plus dans l’article principal des règles de [réduction de la surface d’attaque](attack-surface-reduction.md) .

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Utiliser la Windows de l’Observateur d’événements comme alternative à la page de rapport des règles de réduction de la surface d’attaque dans Microsoft 365 Defender portail d’événements

Pour passer en revue les applications qui auraient été bloquées, ouvrez l’Observateur d’événements et filtrez l’ID d’événement 1121 dans le journal microsoft-Windows-Windows Defender/opérationnel. Le tableau suivant répertorie tous les événements de protection réseau.

ID d’événement | Description
-|-
 5007 | Événement lorsque les paramètres sont modifiés
 1121 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode blocage
 1122 | Événement lorsqu’une règle de réduction de la surface d’attaque se déclenche en mode audit

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiements

[Prérequis pour le déploiement des règles ASR](attack-surface-reduction-rules-deployment.md)

[Étape 1 : Planifier le déploiement des règles ASR](attack-surface-reduction-rules-deployment-plan.md)

[Étape 3 : Mettre en œuvre les règles ASR](attack-surface-reduction-rules-deployment-implement.md)

[Étape 4 : Opérationnaliser les règles ASR](attack-surface-reduction-rules-deployment-operationalize.md)
