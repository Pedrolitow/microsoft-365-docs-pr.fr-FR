---
title: Afficher les résultats d’une enquête automatisée dans Microsoft 365
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, investigation, correction, actions
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Pendant et après une enquête automatisée dans Microsoft 365, vous pouvez afficher les résultats et les principales conclusions.
ms.date: 01/29/2021
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: dd9d192862e82a43453459a6fedbb8b38c71a2cd
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68060557"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Détails et résultats d’une enquête automatisée dans Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Lorsqu’une [enquête automatisée](office-365-air.md) se produit dans [Microsoft Defender pour Office 365](defender-for-office-365.md), des détails sur cette enquête sont disponibles pendant et après le processus d’enquête automatisé. Si vous disposez des autorisations nécessaires, vous pouvez afficher ces détails dans le portail Microsoft 365 Defender. Les détails de l’enquête vous fournissent un état à jour et la possibilité d’approuver les actions en attente.

> [!TIP]
> Consultez la nouvelle page d’investigation unifiée dans le portail Microsoft 365 Defender. Pour en savoir plus, consultez [(NOUVEAU!) Page d’investigation unifiée](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>État de l’enquête

L’état de l’enquête indique la progression de l’analyse et des actions. À mesure que l’enquête s’exécute, l’état change pour indiquer si des menaces ont été détectées et si des actions ont été approuvées.

|État|Description|
|---|---|
|**Démarrage**|L’enquête a été déclenchée et attend de commencer à s’exécuter.|
|**En cours d’exécution**|Le processus d’enquête a commencé et est en cours. Cet état se produit également lorsque les [actions en attente](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) sont approuvées.|
|**Aucune menace trouvée**|L’enquête est terminée et aucune menace (compte d’utilisateur, e-mail, URL ou fichier) n’a été identifiée. <p> **CONSEIL** : Si vous pensez que quelque chose a été manqué (par exemple, un faux négatif), vous pouvez prendre des mesures à l’aide de [l’Explorateur de menaces](threat-explorer.md).|
|**Partiellement examinée**|L’enquête automatisée a détecté des problèmes, mais il n’existe aucune action de correction spécifique pour résoudre ces problèmes. <p> L’état **partiellement examiné** peut se produire lorsqu’un type d’activité utilisateur a été identifié, mais qu’aucune action de nettoyage n’est disponible. Les activités utilisateur suivantes sont les suivantes : <ul><li>Événement [de protection contre la perte de données](../../compliance/dlp-learn-about-dlp.md)</li><li>Une anomalie d’envoi de courrier électronique</li><li>Programmes malveillants envoyés</li><li>Hameçonnage envoyé</li></ul> <p> **Remarque** : cet état **partiellement étudié** était auparavant étiqueté comme **menaces trouvées**. <p> L’enquête n’a détecté aucune URL, fichier ou e-mail malveillant à corriger, et aucune activité de boîte aux lettres à corriger, telle que la désactivation des règles de transfert ou de délégation. <p> **CONSEIL** : Si vous pensez que quelque chose a été manqué (par exemple, un faux négatif), vous pouvez examiner et prendre des mesures à l’aide de [l’Explorateur de menaces](threat-explorer.md)|
|**Arrêté par le système**|L’enquête s’est arrêtée. Une enquête peut s’arrêter pour plusieurs raisons : <ul><li>Les actions en attente de l’enquête ont expiré. Délai d’attente des actions en attente après l’approbation d’une semaine</li><li>Il y a trop d’actions. Par exemple, s’il y a trop d’utilisateurs qui cliquent sur des URL malveillantes, cela peut dépasser la capacité de l’enquête à exécuter tous les analyseurs, de sorte que l’investigation s’arrête</li></ul> <p> **CONSEIL** : Si une enquête s’arrête avant que des actions aient été effectuées, essayez d’utiliser [l’Explorateur](threat-explorer.md) de menaces pour rechercher et traiter les menaces.|
|**Action en attente**|L’enquête a détecté une menace, telle qu’un e-mail malveillant, une URL malveillante ou un paramètre de boîte aux lettres à risque, et une action pour corriger cette menace [est en attente d’approbation](air-review-approve-pending-completed-actions.md). <p> L’état **de l’action en attente** est déclenché lorsqu’une menace avec une action correspondante est trouvée. Toutefois, la liste des actions en attente peut augmenter à mesure qu’une enquête s’exécute. Affichez les détails de l’examen pour voir si d’autres éléments sont toujours en attente d’achèvement.|
|**Corrigé**|L’enquête s’est terminée et toutes les mesures correctives ont été approuvées (indiquées comme entièrement corrigées). <p> **REMARQUE** : Les actions de correction approuvées peuvent avoir des erreurs qui empêchent les actions d’être effectuées. Que les actions de correction soient terminées ou non, l’état de l’examen ne change pas. Afficher les détails de l’enquête.|
|**Partiellement corrigé**|L’enquête a donné lieu à des mesures correctives, et certaines ont été approuvées et terminées. D’autres actions sont toujours [en attente](air-review-approve-pending-completed-actions.md).|
|**Échec**|Au moins un analyseur d’investigation a rencontré un problème où il n’a pas pu se terminer correctement. <p> **NOTE** Si une enquête échoue après l’approbation des actions de correction, les actions de correction peuvent encore avoir réussi. Affichez les détails de l’enquête.|
|**Mise en file d’attente par limitation**|Une enquête est en cours dans une file d’attente. Une fois les autres enquêtes terminées, les enquêtes en file d’attente commencent. La limitation permet d’éviter des performances de service médiocres.  <p> **CONSEIL** : Les actions en attente peuvent limiter le nombre de nouvelles investigations pouvant s’exécuter. Veillez à [approuver (ou rejeter) les actions en attente](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions).|
|**Terminé par la limitation**|Si une enquête est trop longue dans la file d’attente, elle s’arrête. <p> **CONSEIL** : Vous pouvez [démarrer une enquête à partir de l’Explorateur de menaces](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|

## <a name="view-details-of-an-investigation"></a>Afficher les détails d’une enquête

1. Accédez au portail Microsoft 365 Defender (<https://security.microsoft.com>), puis connectez-vous.
2. Dans le volet de navigation, sélectionnez **Centre d’actions**.
3. Sous les onglets **En attente** ou **Historique** , sélectionnez une action. Son volet volant s’ouvre.
4. Dans le volet de menu volant, sélectionnez **Ouvrir la page d’investigation**. 
5. Utilisez les différents onglets pour en savoir plus sur l’enquête.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Afficher les détails d’une alerte liée à une enquête

Certains types d’alertes déclenchent une investigation automatisée dans Microsoft 365. Pour plus d’informations, consultez [les stratégies d’alerte qui déclenchent des investigations automatisées](office-365-air.md#which-alert-policies-trigger-automated-investigations).

1. Accédez au portail Microsoft 365 Defender (<https://security.microsoft.com>), puis connectez-vous.
2. Dans le volet de navigation, sélectionnez **Centre d’actions**.
3. Sous les onglets **En attente** ou **Historique** , sélectionnez une action. Son volet volant s’ouvre.
4. Dans le volet de menu volant, sélectionnez **Ouvrir la page d’investigation**.
5. Sélectionnez l’onglet **Alertes** pour afficher la liste de toutes les alertes associées à cette enquête.
6. Sélectionnez un élément dans la liste pour ouvrir son volet volant. Vous pouvez y afficher plus d’informations sur l’alerte.

## <a name="keep-the-following-points-in-mind"></a>Gardez à l’esprit les points suivants

- Email nombres sont calculés au moment de l’enquête, et certains comptes sont recalculés lorsque vous ouvrez des menus volants d’investigation (basés sur une requête sous-jacente).

- Les nombres de courriers affichés pour les clusters de messagerie sous l’onglet **Email** et la valeur de quantité d’e-mail affichée dans le menu volant du cluster sont calculés au moment de l’examen et ne changent pas.

- Le nombre d’e-mails affiché en bas de l’onglet **Email** du menu volant du cluster de messagerie et le nombre de messages électroniques affichés dans l’Explorateur reflètent les messages électroniques reçus après l’analyse initiale de l’enquête.

  Ainsi, un cluster de courrier qui affiche une quantité d’origine de 10 e-mails affiche une liste de courriers de 15 au total lorsque cinq messages électroniques supplémentaires arrivent entre la phase d’analyse de l’enquête et lorsque l’administrateur examine l’enquête. De même, les anciennes investigations peuvent commencer à afficher des nombres plus élevés que ne le montrent les requêtes de l’Explorateur, car les données de Microsoft Defender pour Office 365 Plan 2 expirent après sept jours pour les essais et après 30 jours pour les licences payantes.

  L’affichage des nombres historiques et actuels dans différentes vues est effectué pour indiquer l’impact de l’e-mail au moment de l’examen et l’impact actuel jusqu’au moment de l’exécution de la correction.

- Dans le contexte de l’e-mail, vous pouvez voir une surface de menace d’anomalie de volume dans le cadre de l’enquête. Une anomalie de volume indique un pic de messages électroniques similaires autour de l’heure de l’événement d’investigation par rapport aux périodes antérieures. Un pic du trafic de messagerie avec certaines caractéristiques (par exemple, domaine de l’objet et de l’expéditeur, similarité du corps et adresse IP de l’expéditeur) est typique du début des campagnes de messagerie ou des attaques. Toutefois, les campagnes de courrier en bloc, de courrier indésirable et légitimes partagent généralement ces caractéristiques.

- Les anomalies de volume représentent une menace potentielle et peuvent donc être moins graves que les programmes malveillants ou les menaces de hameçonnage identifiés à l’aide de moteurs antivirus, de détonation ou de réputation malveillante.

- Vous n’êtes pas obligé d’approuver chaque action. Si vous n’êtes pas d’accord avec l’action recommandée ou si votre organisation ne choisit pas certains types d’actions, vous pouvez choisir de **rejeter** les actions ou simplement de les ignorer et de ne prendre aucune action.

- L’approbation et/ou le rejet de toutes les actions permettent à l’enquête de se fermer complètement (l’état est corrigé), tout en laissant certaines actions incomplètes pour que l’état de l’enquête passe à un état partiellement corrigé.

## <a name="next-steps"></a>Prochaines étapes

- [Examiner et approuver les actions en attente](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
