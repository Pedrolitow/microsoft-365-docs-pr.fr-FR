---
title: Atténuer les menaces dans Microsoft 365 Lighthouse avec Microsoft Defender Antivirus
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: algreer
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment atténuer les menaces avec Microsoft Defender Antivirus.
ms.openlocfilehash: cb324adcb9f463da48937f65d260354232355e1b
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662552"
---
# <a name="mitigate-threats-in-microsoft-365-lighthouse-with-microsoft-defender-antivirus"></a>Atténuer les menaces dans Microsoft 365 Lighthouse avec Microsoft Defender Antivirus

Microsoft 365 Lighthouse permet aux partenaires d’examiner et d’atténuer les menaces sur tous vos locataires. Vous pouvez également lancer des analyses antivirus sur les appareils, vérifier que les appareils reçoivent les dernières mises à jour pour Microsoft Defender Antivirus et passer en revue les actions en attente après les analyses antivirus. Lighthouse prend uniquement en charge les appareils exécutant Windows 10 ou une version ultérieure.

## <a name="before-you-begin"></a>Avant de commencer

- Microsoft 365 Lighthouse est déployé uniquement dans le locataire partenaire, et non dans les locataires du client, mais assurez-vous que vous et vos locataires clients répondez aux exigences répertoriées dans [Microsoft 365 Lighthouse exigences](m365-lighthouse-requirements.md).

- Les utilisateurs doivent exécuter Microsoft Defender Antivirus (inclus avec Windows). Lighthouse ne prend pas en charge les logiciels antivirus non-Microsoft. Pour plus d’informations, consultez [Activer Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows).

- Vous devez être administrateur général dans le locataire partenaire auquel vous vous connectez.

## <a name="investigate-active-threats"></a>Examiner les menaces actives

Pour examiner une menace spécifique :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces des appareils** > .

2. Sélectionnez l’onglet **Menaces** .

3. Dans la liste des menaces, sélectionnez la menace que vous souhaitez examiner.

Le volet d’informations sur les menaces fournit les informations suivantes :

| Catégorie                                      | Définition                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Appareil et locataire                             | Nom de l’appareil et locataire où la menace a été trouvée. Sélectionnez le nom de l’appareil pour afficher des informations supplémentaires. |
| État des menaces                                 | État de la menace.                                                                                    |
| Type de menace                                   | Type de menace.                                                                                              |
| Gravité des menaces                               | Gravité de la menace (Grave, Élevé, Modéré, Faible, Inconnu)                                                    |
| Cas                                     | Nombre d’instances de cette menace présentes sur l’appareil.                                                    |
| Première détection                                | Lorsque la menace a été détectée pour la première fois sur cet appareil.                                                           |
| Documentation                                 | Lien vers des informations supplémentaires sur la menace.                                                             |
| Autres appareils sur ce locataire avec cette menace | Liste des autres appareils du même locataire avec la même menace active.                                      |
| Autres locataires avec cette menace                | Liste d’autres locataires avec la même menace active.                                                         |

Pour examiner les menaces sur un appareil spécifique :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces des appareils** > .

2. Sélectionnez l’onglet **Protection antivirus** .

3. Sélectionnez un appareil dans la liste.

4. Dans le volet d’informations de l’appareil, sélectionnez l’onglet **Menaces actuelles** .

Lighthouse affiche toutes les menaces détectées sur l’appareil. Pour afficher les détails, sélectionnez la menace.

## <a name="scan-for-threats-on-a-device"></a>Rechercher les menaces sur un appareil

Une analyse rapide recherche les emplacements courants où les programmes malveillants peuvent se trouver, tels que les clés de Registre et les dossiers de démarrage de connaissances. Une analyse complète recherche l’ensemble de l’appareil. Dans la plupart des cas, une analyse rapide est suffisante et est l’option recommandée pour les analyses planifiées.

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces des appareils** > .

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **Exécuter l’analyse complète** ou **Exécuter l’analyse rapide**.

Vous pouvez également analyser plusieurs appareils en cochant la case en regard de chaque nom d’appareil dans la liste, puis en **sélectionnant Exécuter l’analyse complète** ou **Exécuter l’analyse rapide**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir les mises à jour de Microsoft Defender Antivirus

Pour mettre à jour Microsoft Defender Antivirus sur un seul appareil :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces des appareils** > .

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet détails de l’appareil, sélectionnez **Mettre à jour l’antivirus**.

Vous pouvez obtenir des mises à jour pour plusieurs appareils en cochant la case en regard de chaque nom d’appareil dans la liste, puis en sélectionnant **Mettre à jour l’antivirus**.

Si vous devez créer une stratégie, sélectionnez **Mettre à jour la stratégie** dans le volet d’informations de l’appareil. Lighthouse vous redirige vers Microsoft Endpoint Manager (MEM). Pour plus d’informations sur la création d’une stratégie, consultez [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Vérifier les actions antivirus en attente sur un appareil

Lorsque des actions consécutives sont appliquées à un appareil, vous recevez un message d’action en attente. Pour vérifier les actions en attente sur un appareil :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces des appareils** > .

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet Détails de l’appareil, sélectionnez l’onglet **État des actions** de l’appareil pour afficher les actions en attente.

## <a name="restart-a-device"></a>Redémarrer un appareil

Certaines mises à jour peuvent nécessiter un redémarrage d’un appareil pour s’installer correctement.

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces des appareils** > .

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **Redémarrer l’appareil**.

Vous pouvez également redémarrer plusieurs appareils en cochant la case en regard de chaque nom d’appareil dans la liste, puis en **sélectionnant Redémarrer l’appareil**.

## <a name="related-content"></a>Contenu associé

[Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Vue d’ensemble de la page Gestion des menaces dans Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (article)\
[Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy) (article)\
[Activer Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows) (article)\
[Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/threats) (page web)
