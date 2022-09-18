---
title: Visitez le Centre d’actions pour voir les actions de correction
description: Utiliser le centre d’action pour afficher les détails et les résultats à la suite d’une investigation automatisée
keywords: action, centre, autoir, automatisé, investigation, réponse, correction
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.prod: m365-security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
search.appverid: met150
ms.openlocfilehash: cc947828d66ffd0e7220ddfddc2a366348b3c289
ms.sourcegitcommit: 2dedd0f594b817779e034afa6c4418def2382a22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2022
ms.locfileid: "67796739"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Visitez le Centre d’actions pour voir les actions de correction

Pendant et après une enquête automatisée, les actions de correction pour les détections de menaces sont identifiées. Selon la menace particulière et la façon dont [les fonctionnalités d’investigation et de correction automatisées sont configurées](configure-automated-investigations-remediation.md) pour votre organisation, certaines actions de correction sont effectuées automatiquement, et d’autres nécessitent une approbation. Si vous faites partie de l’équipe des opérations de sécurité de votre organisation, vous pouvez afficher les [actions de correction](manage-auto-investigation.md#remediation-actions) en attente et terminées dans le **Centre d’actions**.

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

## <a name="the-unified-action-center"></a>Centre d’action unifié

Récemment, le Centre d’action a été mis à jour. Vous disposez maintenant d’une expérience de centre d’actions unifiée. Pour accéder à votre centre d’actions, accédez à [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) et connectez-vous.

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Page Centre d’actions dans le portail Microsoft 365 Defender" lightbox="images/mde-action-center-unified.png":::

### <a name="whats-changed"></a>Qu’est-ce qui a changé ?

Le tableau suivant compare le nouveau centre d’action unifié au centre d’actions précédent.

|Le nouveau centre d’action unifié  |Centre d’actions précédent  |
|---------|---------|
|Répertorie les actions en attente et terminées pour les appareils et les e-mails dans un seul emplacement <br/>([Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) plus [Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/office-365-atp))|Répertorie les actions en attente et terminées pour les appareils <br/> ([Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) uniquement)   |
|Se trouve à :<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Se trouve à :<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, choisissez **Centre d’action**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Volet de navigation vers le Centre d’actions dans le portail Microsoft 365 Defender" lightbox="images/action-center-nav-new.png"::: | Dans le portail Microsoft 365 Defender, choisissez **Centre d’action** des  > **enquêtes automatisées**. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Version antérieure du volet de navigation vers le Centre d’actions dans le portail Microsoft 365 Defender" lightbox="images/action-center-nav-old.png":::  |

Le centre d’action unifié regroupe les actions de correction dans Defender pour point de terminaison et Defender pour Office 365. Il définit un langage commun pour toutes les actions de correction et fournit une expérience d’investigation unifiée.

Vous pouvez utiliser le Centre d’actions unifié si vous disposez des autorisations appropriées et d’un ou plusieurs des abonnements suivants :

- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)
- [Defender pour point de terminaison](microsoft-defender-endpoint.md)
- [Defender pour Office 365](/microsoft-365/security/office-365-security/office-365-atp)
- [Défenseur des affaires](../defender-business/mdb-overview.md)

## <a name="using-the-action-center"></a>Utilisation du centre d’actions

Pour accéder au centre d’action unifié dans le portail Microsoft 365 Defender amélioré :

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portail Microsoft 365 Defender</a> et connectez-vous.

2. Dans le volet de navigation, sélectionnez **Centre d’actions**.

3. Utilisez les onglets **Actions en attente** et **Historique** . Le tableau suivant récapitule ce que vous verrez sous chaque onglet :

   |Tab|Description|
   |---|---|
   |**Pending**|Affiche une liste des actions qui nécessitent une attention particulière. Vous pouvez approuver ou rejeter des actions une par une, ou sélectionner plusieurs actions si elles ont le même type d’action (par exemple, **fichier de mise en quarantaine**). <p> **CONSEIL** : Veillez à [examiner et approuver (ou rejeter) les actions en attente](manage-auto-investigation.md) dès que possible afin que vos enquêtes automatisées puissent se terminer en temps voulu.|
   |**Historique**|Sert de journal d’audit pour les actions qui ont été effectuées, par exemple : <ul><li>Mesures correctives prises à la suite d’enquêtes automatisées</li><li>Actions de correction approuvées par votre équipe des opérations de sécurité</li><li>Commandes exécutées et actions de correction appliquées pendant les sessions de réponse en direct</li><li>Actions de correction effectuées par les fonctionnalités de protection contre les menaces dans l’Antivirus Microsoft Defender</li></ul> <p> Fournit un moyen d’annuler certaines actions (voir [Annuler les actions terminées](manage-auto-investigation.md#undo-completed-actions)).|

4. Pour personnaliser, trier, filtrer et exporter des données dans le Centre d’actions, effectuez une ou plusieurs des étapes suivantes :

   :::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Centre d’actions avec colonnes et filtres" lightbox="images/new-action-center-columnsfilters.png":::

   - Sélectionnez un en-tête de colonne pour trier les éléments dans l’ordre croissant ou décroissant.
   - Utilisez le filtre de période pour afficher les données du dernier jour, semaine, 30 jours ou 6 mois.
   - Choisissez les colonnes que vous souhaitez afficher.
   - Spécifiez le nombre d’éléments à inclure sur chaque page de données.
   - Utilisez des filtres pour afficher uniquement les éléments que vous souhaitez voir.
   - Sélectionnez **Exporter** pour exporter les résultats vers un fichier .csv.

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et approuver des actions de correction](manage-auto-investigation.md)
- [Consultez le guide interactif : Examiner et corriger les menaces avec Microsoft Defender pour point de terminaison](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Voir aussi

- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)
- [Comparer les fonctionnalités de sécurité dans les plans Microsoft 365 pour les petites et moyennes entreprises](../defender-business/compare-mdb-m365-plans.md)
