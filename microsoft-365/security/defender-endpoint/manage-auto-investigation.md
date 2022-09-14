---
title: Passer en revue les actions de correction à la suite d’investigations automatisées
description: Passez en revue et approuvez (ou rejetez) les actions de correction à la suite d’une enquête automatisée.
keywords: autoir, automatisé, investigation, détection, correction, action, en attente, approuvé
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
ms.date: 07/20/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 4bad45f7ed9e6c5e82f1bbc52603deeb6c104af1
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67689894"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Passer en revue les actions de correction à la suite d’une investigation automatisée

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

## <a name="remediation-actions"></a>Actions de correction

Lorsqu’une [enquête automatisée](automated-investigations.md) s’exécute, un verdict est généré pour chaque élément de preuve faisant l’objet d’une enquête. Les verdicts peuvent être *malveillants*, *suspects* ou *introuvables*.

Selon

- le type de menace,
- le verdict qui en résulte, et
- comment les [groupes d’appareils](/microsoft-365/security/defender-endpoint/machine-groups) de votre organisation sont configurés,

les actions de correction peuvent se produire automatiquement ou uniquement après approbation par l’équipe des opérations de sécurité de votre organisation.

Voici quelques exemples :

- **Exemple 1** : Les groupes d’appareils de Fabrikam sont définis sur **Full : corrigez automatiquement les menaces** (paramètre recommandé). Dans ce cas, les actions de correction sont effectuées automatiquement pour les artefacts considérés comme malveillants à la suite d’une enquête automatisée (voir [Examiner les actions terminées](#review-completed-actions)).

- **Exemple 2** : Les appareils de Contoso sont inclus dans un groupe d’appareils défini pour **Semi - nécessitent une approbation pour toute correction**. Dans ce cas, l’équipe des opérations de sécurité de Contoso doit examiner et approuver toutes les actions de correction à la suite d’une enquête automatisée (voir [Examiner les actions en attente](#review-pending-actions)).

- **Exemple 3** : Les groupes d’appareils de Tailspin Toys sont définis sur **Aucune réponse automatisée** (non recommandé). Dans ce cas, les investigations automatisées ne se produisent pas. Aucune action de correction n’est effectuée ou en attente, et aucune action n’est journalisée dans le [Centre d’actions](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center) pour leurs appareils (voir [Gérer les groupes d’appareils](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)).

Qu’elle soit effectuée automatiquement ou après approbation, une enquête automatisée peut entraîner une ou plusieurs des actions de correction :

- Mettre en quarantaine un fichier
- Supprimer une clé de Registre
- Tuer un processus
- Arrêter un service
- Désactiver un pilote
- Supprimer une tâche planifiée

## <a name="review-pending-actions"></a>Examiner les actions en attente

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portail Microsoft 365 Defender</a> et connectez-vous.

2. Dans le volet de navigation, choisissez **Centre de notifications**.

3. Passez en revue les éléments sous l’onglet **En attente** .

4. Sélectionnez une action pour ouvrir son volet volant.

5. Dans le volet volant, passez en revue les informations, puis effectuez l’une des étapes suivantes :

   - Sélectionnez **Ouvrir la page d’enquête** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Refuser** pour empêcher l’exécution d’une action en attente.
   - Sélectionnez **Go Hunt** pour passer à [la chasse avancée](advanced-hunting-overview.md).

## <a name="review-completed-actions"></a>Passer en revue les actions terminées

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portail Microsoft 365 Defender</a> et connectez-vous.

2. Dans le volet de navigation, choisissez **Centre de notifications**.

3. Passez en revue les éléments de l’onglet **Historique** .

4. Sélectionnez un élément pour afficher plus de détails sur cette action de correction.

## <a name="undo-completed-actions"></a>Annuler les actions terminées

Si vous avez déterminé qu’un appareil ou un fichier n’est pas une menace, vous pouvez annuler les actions de correction qui ont été effectuées, que ces actions aient été effectuées automatiquement ou manuellement. Dans le centre d’actions, sous l’onglet **Historique** , vous pouvez annuler l’une des actions suivantes :

|Source de l’action|Actions prises en charge|
|---|---|
|<ul><li>Investigation automatisée</li><li>Actions de réponse manuelles (voir la note ci-dessous)</li><li>Antivirus Microsoft Defender</li></ul>|<ul><li>Désactiver un pilote</li><li>Isoler l’appareil</li><li>Mettre en quarantaine un fichier</li><li>Supprimer une clé de Registre</li><li>Supprimer une tâche planifiée</li><li>Restreindre l'exécution de code</li><li>Arrêter un service</li></ul>|

> [!NOTE]
> [Defender pour point de terminaison Plan 1](defender-endpoint-plan-1.md) et [Microsoft Defender pour entreprises](../defender-business/mdb-overview.md) inclure uniquement les actions de réponse manuelle suivantes :
>
> - Exécuter une analyse antivirus
> - Isoler l’appareil
> - Arrêter et mettre en quarantaine un fichier
> - Ajouter un indicateur pour bloquer ou autoriser un fichier
>
> Pour plus d’informations, consultez [Comparer Microsoft Defender pour point de terminaison plans](defender-endpoint-plan-1-2.md) et [Comparer les fonctionnalités de sécurité dans les plans Microsoft 365 pour les petites et moyennes entreprises](../defender-business/compare-mdb-m365-plans.md).

### <a name="to-undo-multiple-actions-at-one-time"></a>Pour annuler plusieurs actions à la fois

1. Accédez au centre d’action ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) et connectez-vous.

2. Sous l’onglet **Historique** , sélectionnez les actions que vous souhaitez annuler. Veillez à sélectionner les éléments qui ont le même type d’action. Un volet volant s’ouvre.

3. Dans le volet de menu volant, sélectionnez **Annuler**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Pour supprimer un fichier de la quarantaine sur plusieurs appareils

1. Accédez au centre d’action ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) et connectez-vous.

2. Sous l’onglet **Historique** , sélectionnez un élément contenant le **fichier de mise en quarantaine** de type Action.

3. Dans le volet de menu volant, **sélectionnez Appliquer à X autres instances de ce fichier**, puis sélectionnez **Annuler**.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Niveaux d’automatisation, résultats d’investigation automatisés et actions résultantes

Les niveaux d’automatisation déterminent si certaines actions de correction sont effectuées automatiquement ou uniquement après approbation. Parfois, votre équipe des opérations de sécurité a plus de mesures à prendre, en fonction des résultats d’une enquête automatisée. Le tableau suivant récapitule les niveaux d’automatisation, les résultats des investigations automatisées et ce qu’il faut faire dans chaque cas.

|Paramètre de groupe d’appareils|Résultats des investigations automatisées|Procédure|
|---|---|---|
|**Complet : corriger automatiquement les menaces**<br/>(recommandé)|Un verdict de *malveillance* est rendu pour un élément de preuve. <p> Les actions de correction appropriées sont effectuées automatiquement.|[Passer en revue les actions terminées](#review-completed-actions) |
|**Semi - exiger l’approbation de toute correction**|Un verdict de *malveillance* ou *de suspect* est rendu pour un élément de preuve. <p> Les actions de correction sont en attente d’approbation pour continuer.|[Approuver (ou rejeter) les actions en attente](#review-pending-actions)|
|**Semi - Exiger l’approbation pour la correction des dossiers principaux**|Un verdict de *malveillance* est rendu pour un élément de preuve. <p> Si l’artefact est un fichier ou un exécutable et qu’il se trouve dans un répertoire de système d’exploitation, tel que le dossier Windows ou le dossier Program Files, les actions de correction sont en attente d’approbation. <p> Si l’artefact *ne* se trouve pas dans un répertoire de système d’exploitation, des actions de correction sont effectuées automatiquement.|<ol><li>[Approuver (ou rejeter) les actions en attente](#review-pending-actions)</li><li>[Passer en revue les actions terminées](#review-completed-actions)</li></ol>|
|**Semi - Exiger l’approbation pour la correction des dossiers principaux**|Un verdict de *suspect* est rendu pour un élément de preuve. <p> Les actions de correction sont en attente d’approbation.|[Approuver (ou rejeter) les actions en attente](#review-pending-actions).|
|**Semi - Exiger l’approbation pour la correction des dossiers non temporaires**|Un verdict de *malveillance* est rendu pour un élément de preuve. <p> Si l’artefact est un fichier ou un exécutable qui ne se trouve pas dans un dossier temporaire, tel que le dossier de téléchargements ou le dossier temporaire de l’utilisateur, les actions de correction sont en attente d’approbation. <p> Si l’artefact est un fichier ou un exécutable qui *se trouve* dans un dossier temporaire, des actions de correction sont effectuées automatiquement.|<ol><li>[Approuver (ou rejeter) les actions en attente](#review-pending-actions)</li><li>[Passer en revue les actions terminées](#review-completed-actions)</li></ol>|
|**Semi - Exiger l’approbation pour la correction des dossiers non temporaires**|Un verdict de *suspect* est rendu pour un élément de preuve. <p> Les actions de correction sont en attente d’approbation.|[Approuver (ou rejeter) les actions en attente](#review-pending-actions)|
|N’importe quel niveau **d’automatisation complète** ou **semi-automatique**|Un verdict *d’absence de menaces trouvées* est rendu pour un élément de preuve. <p> Aucune action de correction n’est effectuée et aucune action n’est en attente d’approbation.|[Consulter les détails et les résultats des examens automatisés](/microsoft-365/security/defender-endpoint/auto-investigation-action-center)|
|**Aucune réponse automatisée** (non recommandée)|Aucune enquête automatisée n’est exécutée, aucun verdict n’est rendu et aucune mesure corrective n’est prise ou n’attend l’approbation.|[Envisagez de configurer ou de modifier vos groupes d’appareils pour utiliser **l’automatisation complète** ou **semi-automatique**](/microsoft-365/security/defender-endpoint/machine-groups)|

Tous les verdicts sont suivis dans le [Centre d’action](auto-investigation-action-center.md#the-unified-action-center).

> [!NOTE]
> Dans [Defender entreprise](../defender-business/mdb-overview.md), les fonctionnalités d’investigation et de correction automatisées sont prédéfinies pour utiliser **les menaces complètes et de correction automatique**. Ces fonctionnalités sont appliquées à tous les appareils par défaut.

## <a name="next-steps"></a>Prochaines étapes

- [En savoir plus sur les fonctionnalités de réponse en direct](live-response.md)
- [Chasse proactive pour les menaces avec repérage avancé](advanced-hunting-overview.md)
- [Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des enquêtes automatisées](automated-investigations.md)
