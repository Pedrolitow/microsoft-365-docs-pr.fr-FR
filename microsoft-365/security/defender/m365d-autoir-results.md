---
title: Détails et résultats d’une enquête automatisée
description: Afficher les résultats et les principales conclusions de l’enquête automatisée dans Microsoft 365 Defender
keywords: automatisé, examen, résultats, analyse, détails, correction, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 08/11/2022
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 591c7a8aca882c0674eaa3ba4b3eacc89817e859
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67388614"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Détails et résultats d’une enquête automatisée

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Avec Microsoft 365 Defender, lorsqu’une [enquête automatisée](m365d-autoir.md) s’exécute, des détails sur cette enquête sont disponibles pendant et après le processus d’investigation automatisé. Si vous disposez [des autorisations nécessaires](m365d-action-center.md#required-permissions-for-action-center-tasks), vous pouvez afficher ces détails dans une vue détails de l’enquête qui vous fournit un état à jour et la possibilité d’approuver les actions en attente. 

## <a name="new-unified-investigation-page"></a>(NOUVEAU) Page d’investigation unifiée

La page d’enquête a récemment été mise à jour pour inclure des informations sur vos appareils, vos e-mails et le contenu de collaboration. La nouvelle page d’investigation unifiée définit un langage commun et fournit une expérience unifiée pour les investigations automatiques dans [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) et [Microsoft Defender pour Office 365](../office-365-security/defender-for-office-365.md). Pour accéder à la page d’investigation unifiée, sélectionnez le lien dans la bannière jaune sur laquelle vous verrez :

- Toute page d’enquête dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">portail de conformité Microsoft Purview</a>
- Toute page d’investigation dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))
- Toute expérience de centre d’incidents ou d’actions dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>

## <a name="open-the-investigation-details-view"></a>Ouvrir la vue Détails de l’examen

Vous pouvez ouvrir une vue Détails de l’examen avant impression comme suit :

- [Sélectionnez un élément dans le centre de notifications](#select-an-item-in-the-action-center)
- [Sélectionnez un examen dans une page de détails d’incident](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Sélectionnez un élément dans le centre de notifications

Le [Centre d’actions](m365d-action-center.md) amélioré ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) regroupe les [actions de correction](m365d-remediation-actions.md) sur vos appareils, les e-mails & le contenu de collaboration et les identités. Les actions répertoriées incluent les actions de correction qui ont été effectuées automatiquement ou manuellement. Dans le centre de actions, vous pouvez afficher les actions en attente d’approbation et les actions qui ont déjà été approuvées ou terminées. Vous pouvez également accéder à plus de détails, tels qu’une page d’investigation.

> [!TIP]
> Vous devez disposer [de certaines autorisations](m365d-action-center.md#required-permissions-for-action-center-tasks) pour approuver, rejeter ou annuler des actions.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et connectez-vous. 

2. Dans le volet de navigation, choisissez **Centre de notifications**. 

3. Sous l’onglet **En attente** ou **Historique**, sélectionnez un élément. Son volet volant s’ouvre.

4. Passez en revue les informations contenues dans le volet volant, puis effectuez l’une des étapes suivantes :
   - Sélectionnez **Ouvrir la page d’enquête** pour afficher plus de détails sur l’enquête.
   - Sélectionnez **Approuver** pour lancer une action en attente.
   - Sélectionnez **Refuser** pour empêcher l’exécution d’une action en attente.
   - Sélectionnez **Go Hunt** pour passer à [la chasse avancée](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Ouvrez un examen dans une page de détails d’incident

La page Détails de l’incident permet d’afficher des informations détaillées sur un incident, notamment des alertes qui ont déclenché des informations sur les appareils, les comptes utilisateurs ou les boîtes aux lettres concernés.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et connectez-vous. 

2. Dans le volet de navigation, choisissez **Incidents & alertes** > **Incidents**. 

3. Sélectionnez un élément dans la liste, puis choisissez **Ouvrir la page d’incident**.

4. Sélectionnez l’onglet **Investigations** , puis sélectionnez une enquête dans la liste. Son volet volant s’ouvre.

5. Sélectionnez **Ouvrir la page d’investigation**. 

Voici un exemple.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="Page d’enquête dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>Détails de l’examen

Utilisez la vue Détails de l’examen pour afficher les activités passées, actuelles et en attente relatives à un examen. Voici un exemple.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="Page détails de l’enquête dans le portail Microsoft 365 Defender" lightbox="../../media/mtp-air-investdetails.png":::

Dans la vue Détails de l’examen, vous pouvez consulter des informations sur les onglets **Graphique de l'examen**, **Alertes**, **Appareils**, **Identités**, **Principales conclusions**, **Entités**, **Journal** et **Actions en attente**, comme décrit dans le tableau suivant.

> [!NOTE]
> Les onglets spécifiques que vous voyez dans une page de détails d’investigation dépendent de ce que votre abonnement inclut. Par exemple, si votre abonnement n’inclut pas Microsoft Defender pour Office 365 plan 2, vous ne verrez pas d’onglet **Boîtes aux lettres**.

| Tab | Description |
|:--------|:--------|
| **Graphique de l'examen** | Fournit une représentation visuelle de l’examen. Décrit les entités et répertorie de menaces détectées, ainsi que les alertes et l’attente d’une approbation.<br/>Vous pouvez sélectionner un élément sur le graphique pour afficher plus de détails. Par exemple, la sélection de l’icône **Preuve** vous amène à l’onglet **Preuve** , où vous pouvez voir les entités détectées et leurs verdicts. |
| **Alertes** | Répertorie les alertes associées à l’examen. Les alertes peuvent provenir de fonctionnalités de protection contre les menaces sur l’appareil d’un utilisateur, dans des applications Office, des Microsoft Defender for Cloud Apps et d’autres fonctionnalités Microsoft 365 Defender. <br> <br> Si vous voyez un *type d’alerte non pris en charge*, cela signifie que les fonctionnalités d’investigation automatisée ne peuvent pas récupérer cette alerte pour exécuter une investigation automatisée. Toutefois, vous pouvez [examiner ces alertes manuellement](investigate-incidents.md#alerts).
| **Appareils** | Répertorie les appareils inclus dans l’enquête, ainsi que leur niveau de correction. (Les niveaux de correction correspondent [au niveau d’automatisation pour les groupes d’appareils](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups).) |
| **Boîtes aux lettres** |Répertorie les boîtes aux lettres impactées par les menaces détectées.  |
| **Utilisateurs**  | Répertorie les comptes d’utilisateurs impactés par les menaces détectées. |
| **Preuve** | Répertorie les éléments de preuve déclenchés par des alertes ou des enquêtes. Inclut les verdicts (*malveillants*, *suspects*, *inconnus* ou *aucune menace trouvée*) et l’état de correction. |
| **Entities** | Fournit des détails sur chaque entité analysée, y compris un verdict pour chaque type d’entité (*malveillant*, *suspect* ou *aucune menace trouvée*).|
|**Log** | Fournit une vue chronologique et détaillée de toutes les actions d’enquête effectuées après le déclenchement d’une alerte.|
| **Historique des actions en attente** | Répertorie les éléments qui nécessitent une approbation pour continuer. Accédez au Centre d’actions ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) pour approuver les actions en attente. |


## <a name="investigation-states"></a>États d’investigation

Le tableau suivant répertorie les états d’investigation et ce qu’ils indiquent.


|État de l’enquête  |Définition  |
|---------|---------|
|Bénigne   | Des artefacts ont fait l’objet d’une enquête et on a déterminé qu’aucune menace n’avait été détectée.|
|PendingResource     | Une enquête automatisée est suspendue, car une action de correction est en attente d’approbation ou l’appareil sur lequel un artefact a été trouvé est temporairement indisponible.|
|UnsupportedAlertType     | Aucune investigation automatisée n’est disponible pour ce type d’alerte. Une investigation plus approfondie peut être effectuée manuellement, à l’aide de la chasse avancée. |
|Échec     | Au moins un analyseur d’investigation a rencontré un problème où il n’a pas pu terminer l’enquête. Si une enquête échoue après l’approbation des actions de correction, les actions de correction peuvent encore avoir réussi.|
|Correction réussie| Une enquête automatisée s’est terminée et toutes les actions de correction ont été terminées ou approuvées.|

Pour fournir plus de contexte sur la façon dont les états d’investigation s’affichent, le tableau suivant répertorie les alertes et leur état d’investigation automatisé correspondant. Ce tableau est inclus comme exemple de ce qu’une équipe des opérations de sécurité peut voir dans le portail Microsoft 365 Defender.

|Nom de l’alerte | Severity | État de l’enquête | État | Catégorie |
|-----------|----------|---------------------|--------|----------|
|Un programme malveillant a été détecté dans un fichier d’image de disque wim|Informatif|Bénigne|Résolu|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|UnsupportedAlertType|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|UnsupportedAlertType|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|UnsupportedAlertType|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive zip|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive zip|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive zip|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive zip|Informatif|PendingResource|Nouveau|Programme malveillant|
|Wpakill hacktool a été empêché|Faible|Échec|Nouveau|Programme malveillant|
|GendowsBatch hacktool a été empêché|Faible|Échec|Nouveau|Programme malveillant|
|Keygen hacktool a été empêché|Faible|Échec|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive zip|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive zip|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier d’archive rar|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier image de disque ISO|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier image de disque ISO|Informatif|PendingResource|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier de données Outlook pst|Informatif|UnsupportedAlertType|Nouveau|Programme malveillant|
|Un programme malveillant a été détecté dans un fichier de données Outlook pst|Informatif|UnsupportedAlertType|Nouveau|Programme malveillant|
|MediaGet détecté|Moyen|Partiellement investi|Nouveau|Programme malveillant|
|TrojanEmailFile|Moyen|SuccessfullyRemediated|Résolu|Programme malveillant|
|Le programme malveillant CustomEnterpriseBlock a été empêché|Informatif|SuccessfullyRemediated|Résolu|Programme malveillant|
|Un programme malveillant CustomEnterpriseBlock actif a été bloqué|Faible|SuccessfullyRemediated|Résolu|Programme malveillant|
|Un programme malveillant CustomEnterpriseBlock actif a été bloqué|Faible|SuccessfullyRemediated|Résolu|Programme malveillant|
|Un programme malveillant CustomEnterpriseBlock actif a été bloqué|Faible|SuccessfullyRemediated|Résolu|Programme malveillant|
|TrojanEmailFile|Moyen|Bénigne|Résolu|Programme malveillant|
|Le programme malveillant CustomEnterpriseBlock a été empêché|Informatif|UnsupportedAlertType|Nouveau|Programme malveillant|
|Le programme malveillant CustomEnterpriseBlock a été empêché|Informatif|SuccessfullyRemediated|Résolu|Programme malveillant|
|TrojanEmailFile|Moyen|SuccessfullyRemediated|Résolu|Programme malveillant|
|TrojanEmailFile|Moyen|Bénigne|Résolu|Programme malveillant|
|Un programme malveillant CustomEnterpriseBlock actif a été bloqué|Faible|PendingResource|Nouveau|Programme malveillant|

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les actions de correction](m365d-autoir-actions.md)
- [En savoir plus sur les actions de correction](m365d-remediation-actions.md)
