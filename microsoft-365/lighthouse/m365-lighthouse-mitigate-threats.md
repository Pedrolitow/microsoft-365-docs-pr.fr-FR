---
title: Atténuer les menaces avec Antivirus Microsoft Defender
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment atténuer les menaces avec Antivirus Microsoft Defender.
ms.openlocfilehash: 428370ce5e49bba0bc9489143864f9b88b2e8c3f
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824331"
---
# <a name="mitigate-threats-with-microsoft-defender-antivirus"></a>Atténuer les menaces avec Antivirus Microsoft Defender

Microsoft 365 Lighthouse permet aux partenaires d’examiner et d’atténuer les menaces sur tous vos locataires. Vous pouvez également lancer des analyses antivirus sur les appareils, vous assurer que les appareils reçoivent les dernières mises à jour pour Antivirus Microsoft Defender et passer en revue les actions en attente à la suite d’analyses antivirus. Lighthouse prend uniquement en charge les appareils exécutant Windows 10 ou version ultérieure.

## <a name="before-you-begin"></a>Avant de commencer

- Microsoft 365 Lighthouse est déployé dans le locataire partenaire uniquement, non pas dans les locataires clients, mais assurez-vous que vous et vos locataires client répondez aux exigences indiquées dans [Microsoft 365 Lighthouse exigences](m365-lighthouse-requirements.md).

- Les utilisateurs doivent exécuter Antivirus Microsoft Defender (inclus dans Windows). Lighthouse ne prend pas en charge les logiciels antivirus non Microsoft. Pour plus d’informations, consultez [Activer Antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows).

- Vous devez être administrateur général dans le locataire partenaire auquel vous vous connectez.

## <a name="investigate-active-threats"></a>Examiner les menaces actives

Pour examiner une menace spécifique :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces**.

2. Sélectionnez l’onglet **Menaces** .

3. Dans la liste des menaces, sélectionnez la menace à examiner.

Le volet détails des menaces fournit les informations suivantes :

| Catégorie                                      | Définition                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Appareil et locataire                             | Nom de l’appareil et locataire où la menace a été trouvée. Sélectionnez le nom de l’appareil pour afficher des informations supplémentaires. |
| État de la menace                                 | État de la menace.                                                                                    |
| Type de menace                                   | Type de menace.                                                                                              |
| Gravité des menaces                               | Gravité de la menace (grave, élevé, modéré, faible, inconnu)                                                    |
| Cas                                     | Nombre d’instances de cette menace présentes sur l’appareil.                                                    |
| Première détection                                | Quand la menace a été détectée pour la première fois sur cet appareil.                                                           |
| Documentation                                 | Lien vers des informations supplémentaires sur la menace.                                                             |
| Autres appareils sur ce locataire avec cette menace | Liste d’autres appareils dans le même locataire avec la même menace active.                                      |
| Autres locataires avec cette menace                | Liste d’autres locataires avec la même menace active.                                                         |

Pour examiner les menaces sur un appareil spécifique :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces**.

2. Sélectionnez l’onglet **Protection antivirus** .

3. Sélectionnez un appareil dans la liste.

4. Dans le volet détails de l’appareil, sélectionnez l’onglet **Menaces actuelles** .

Lighthouse affiche toutes les menaces détectées sur l’appareil. Pour afficher les détails, sélectionnez la menace.

## <a name="scan-for-threats-on-a-device"></a>Rechercher les menaces sur un appareil

Une analyse rapide recherche les emplacements courants où les programmes malveillants peuvent se trouver, tels que les clés de Registre et connaître les dossiers de démarrage. Une analyse complète recherche l’ensemble de l’appareil. Dans la plupart des cas, une analyse rapide est suffisante et est l’option recommandée pour les analyses planifiées.

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces**.

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **Exécuter l’analyse complète** ou **Exécuter l’analyse rapide**.

Vous pouvez également analyser plusieurs appareils en cochant la case en regard de chaque nom d’appareil dans la liste, puis en sélectionnant **Exécuter l’analyse complète** ou **Exécuter l’analyse rapide**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir des mises à jour pour Antivirus Microsoft Defender

Pour mettre à jour Antivirus Microsoft Defender sur un seul appareil :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces**.

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **Mettre à jour l’antivirus**.

Vous pouvez obtenir des mises à jour pour plusieurs appareils en cochant la case en regard de chaque nom d’appareil dans la liste, puis sélectionnez **Mettre à jour l’antivirus**.

Si vous devez créer une stratégie, sélectionnez **Mettre à jour** la stratégie dans le volet détails de l’appareil. Lighthouse vous redirige vers Microsoft Endpoint Manager (MEM). Pour plus d’informations sur la création d’une stratégie, consultez [Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Vérifier les actions antivirus en attente sur un appareil

Lorsque des actions consécutives sont appliquées à un appareil, vous recevez un message d’action en attente. Pour vérifier les actions en attente sur un appareil :

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces**.

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez l’onglet **État des actions** de l’appareil pour afficher les actions en attente.

## <a name="restart-a-device"></a>Redémarrer un appareil

Certaines mises à jour peuvent nécessiter le redémarrage d’un appareil pour s’installer correctement.

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Gestion des menaces**.

2. Sélectionnez l’onglet **Protection antivirus** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **Redémarrer l’appareil**.

Vous pouvez également redémarrer plusieurs appareils en cochant la case en regard de chaque nom d’appareil dans la liste, puis en sélectionnant **Redémarrer l’appareil**.

## <a name="related-content"></a>Contenu associé

[Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Vue d’ensemble de la page de gestion des menaces](m365-lighthouse-threat-management-page-overview.md) (article)\
[Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy) (article)\
[Activer Antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows) (article)\
[Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/threats) (page web)
