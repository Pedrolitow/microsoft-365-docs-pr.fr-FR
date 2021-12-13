---
title: Atténuer les menaces à l’Antivirus Microsoft Defender
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
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez les menaces à l’aide Antivirus Microsoft Defender.
ms.openlocfilehash: 3d7eeb54c6f11e73bca71271faa7c09b30627ec2
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61424037"
---
# <a name="mitigate-threats-with-microsoft-defender-antivirus"></a>Atténuer les menaces à l’Antivirus Microsoft Defender

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse permet aux partenaires d’examiner et d’atténuer les menaces sur tous vos clients. Vous pouvez également lancer des analyses antivirus sur les appareils, vous assurer que les appareils sont en train d’obtenir les dernières mises à jour pour Antivirus Microsoft Defender et passer en revue les actions en attente suite aux analyses antivirus. Le pied de gamme prend uniquement en charge les Windows 10 ou ultérieurs.

## <a name="before-you-begin"></a>Avant de commencer

- Microsoft 365 Lighthouse est déployé uniquement dans le client partenaire, et non dans les locataires du client, mais assurez-vous que vous et vos clients respectez les exigences répertoriées dans les Microsoft 365 Lighthouse [client.](m365-lighthouse-requirements.md)

- Les utilisateurs doivent être en Antivirus Microsoft Defender (inclus dans Windows). Le navigateur ne prend pas en charge les logiciels antivirus non Microsoft. Pour plus d’informations, [voir Activer Antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows).

- Vous devez être administrateur général dans le client partenaire que vous êtes en train de vous inscrire.

## <a name="investigate-active-threats"></a>Examiner les menaces actives

Pour examiner une menace spécifique :

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Gestion des menaces.**

2. Sélectionnez **l’onglet Menaces.**

3. Dans la liste des menaces, sélectionnez la menace que vous souhaitez examiner.

Le volet d’informations sur les menaces fournit les informations suivantes :

| Catégorie                                      | Définition                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Appareil et client                             | Nom de l’appareil et client où la menace a été trouvée. Sélectionnez le nom de l’appareil pour voir des informations supplémentaires. |
| État de la menace                                 | État de la menace.                                                                                    |
| Type de menace                                   | Type de menace.                                                                                              |
| Gravité des menaces                               | Gravité de la menace (grave, élevé, modéré, faible, inconnu)                                                    |
| Instances                                     | Nombre d’instances de cette menace présentes sur l’appareil.                                                    |
| Première détection                                | Lorsque la menace a été détectée pour la première fois sur cet appareil.                                                           |
| Documentation                                 | Lien vers des informations supplémentaires sur la menace.                                                             |
| Autres appareils sur ce client avec cette menace | Liste des autres appareils dans le même client avec la même menace active.                                      |
| Autres locataires avec cette menace                | Liste des autres locataires avec la même menace active.                                                         |

Pour examiner les menaces sur un appareil spécifique :

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Gestion des menaces.**

2. Sélectionnez **l’onglet Protection antivirus.**

3. Sélectionnez un appareil dans la liste.

4. Dans le volet d’informations de l’appareil, sélectionnez **l’onglet Menaces** actuelles.

Le périphérique affiche toutes les menaces trouvées sur l’appareil. Pour voir les détails, sélectionnez la menace.

## <a name="scan-for-threats-on-a-device"></a>Analyse des menaces sur un appareil

Une analyse rapide recherche les emplacements courants où les programmes malveillants peuvent se trouver, tels que les clés de Registre et connaître les dossiers de démarrage. Une analyse complète recherche l’intégralité de l’appareil. Dans la plupart des cas, une analyse rapide est suffisante et constitue l’option recommandée pour les analyses programmées.

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Gestion des menaces.**

2. Sélectionnez **l’onglet Protection antivirus.**

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, **sélectionnez Exécuter une analyse complète** ou exécuter une analyse **rapide.**

Vous pouvez également analyser plusieurs appareils en cochez la case en  regard de chaque nom d’appareil dans la liste, puis sélectionnez Exécuter une analyse complète ou **exécuter une analyse rapide.**

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Obtenir les mises à jour de Antivirus Microsoft Defender

Pour mettre à jour Antivirus Microsoft Defender sur un seul appareil :

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Gestion des menaces.**

2. Sélectionnez **l’onglet Protection antivirus.**

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **Mettre à jour l’antivirus.**

Vous pouvez obtenir des mises à jour pour plusieurs appareils en élecntant la case à cocher en regard de chaque nom d’appareil dans la liste, puis sélectionnez Mettre à jour **l’antivirus.**

Si vous devez créer une stratégie, **sélectionnez** Stratégie de mise à jour dans le volet d’informations de l’appareil. Le réacheminer vous redirige vers Microsoft Endpoint Manager (MEM). Pour plus d’informations sur la création d’une stratégie, voir Créer une stratégie de conformité [dans Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Vérifier les actions antivirus en attente sur un appareil

Lorsque des actions consécutives sont appliquées à un appareil, vous recevez un message d’action en attente. Pour vérifier les actions en attente sur un appareil :

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Gestion des menaces.**

2. Sélectionnez **l’onglet Protection antivirus.**

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **l’onglet** État des actions de l’appareil pour afficher les actions en attente.

## <a name="restart-a-device"></a>Redémarrer un appareil

Certaines mises à jour peuvent nécessiter le redémarrage d’un appareil pour s’installer correctement.

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Gestion des menaces.**

2. Sélectionnez **l’onglet Protection antivirus.**

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez **Appareil de redémarrage.**

Vous pouvez également redémarrer plusieurs appareils en cochez la case en regard de chaque nom d’appareil dans la liste, puis sélectionnez **Appareil de redémarrage.**

## <a name="related-content"></a>Contenu associé

[Conditions requises pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Vue d’ensemble de la page gestion des menaces ](m365-lighthouse-threat-management-page-overview.md) (article)\
[Créer une stratégie de conformité dans Microsoft Intune](/mem/intune/protect/create-compliance-policy) (article)\
[Activer Antivirus Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows) (article)\
[Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/threats)
