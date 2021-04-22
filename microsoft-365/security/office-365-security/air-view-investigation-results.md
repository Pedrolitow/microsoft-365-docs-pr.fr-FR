---
title: Afficher les résultats d'une enquête automatisée dans Microsoft 365
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, examen, correction, actions
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Pendant et après un examen automatisé dans Microsoft 365, vous pouvez afficher les résultats et les résultats clés.
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ebdd25e9bddf53682f747fff7477d49dd1c94755
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933492"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Détails et résultats d'une enquête automatisée dans Microsoft 365

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Lorsqu'une enquête automatisée](office-365-air.md) se produit dans Microsoft Defender pour [Office 365,](defender-for-office-365.md)des détails sur cette enquête sont disponibles pendant et après le processus d'examen automatisé. Si vous avez les autorisations nécessaires, vous pouvez afficher ces détails dans le Centre de sécurité Microsoft 365. Les détails de l'examen vous fournissent l'état à jour et la possibilité d'approuver les actions en attente.

> [!TIP]
> Consultez la nouvelle page d'enquête unifiée dans le Centre de sécurité Microsoft 365. Pour en savoir plus, [voir (NOUVEAU!) Page d'examen unifié](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>État de l'examen

L'état de l'examen indique la progression de l'analyse et des actions. Au cours de l'examen, l'état change pour indiquer si des menaces ont été trouvées et si des actions ont été approuvées.

|Statut|Description|
|:---|:---|
|**Démarrage**|L'enquête a été déclenchée et en attente de démarrage de l'exécution.|
|**En cours d’exécution**|Le processus d'examen a démarré et est en cours. Cet état se produit également lorsque les [actions en attente sont](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) approuvées.|
|**Aucune menace trouvée**|L'enquête est terminée et aucune menace (compte d'utilisateur, message électronique, URL ou fichier) n'a été identifiée. <p> **CONSEIL**: si vous pensez que quelque chose a été manqué (par exemple, un faux négatif), vous pouvez prendre des mesures à l'aide de [l'Explorateur de menaces.](threat-explorer.md)|
|**Menaces détectées**|L'examen automatisé a trouvé des problèmes, mais il n'existe aucune action de correction spécifique pour résoudre ces problèmes. <p> **L'état Menaces** trouvées peut se produire lorsqu'un type d'activité utilisateur a été identifié, mais qu'aucune action de nettoyage n'est disponible. Voici quelques exemples d'activités utilisateur : <br/>- Un [événement de protection contre la](../../compliance/data-loss-prevention-policies.md) perte de données (DLP)<br/>- Une anomalie d'envoi de courrier électronique<br/>- Programmes malveillants envoyés<br/>- Hameçonnage envoyé <p> L'examen n'a trouvé aucune URL, aucun fichier ou message électronique malveillant à corriger et aucune activité de boîte aux lettres à corriger, telle que la non-remise des règles de forwarding ou de la délégation. <p> **CONSEIL**: si vous pensez que quelque chose a été manqué (tel qu'un faux négatif), vous pouvez examiner et prendre des mesures à l'aide de [l'Explorateur de menaces.](threat-explorer.md)|
|**Terminated By System**|L'examen a été arrêté. Une enquête peut s'arrêter pour plusieurs raisons : <br/>- Les actions en attente de l'examen ont expiré. Le délai d'attente des actions en attente d'approbation est de 1 semaine.<br/>- Il y a trop d'actions. Par exemple, s'il y a trop d'utilisateurs qui cliquent sur des URL malveillantes, cela peut aller au-delà de la capacité de l'examen à exécuter tous les analyseurs, de sorte que l'enquête s'arrête.<p> **CONSEIL :** si un examen s'arrête avant que des mesures ne sont prises, essayez d'utiliser l'Explorateur de menaces [pour](threat-explorer.md) rechercher et résoudre les menaces.|
|**Action en attente**|L'enquête a trouvé une menace, telle qu'un e-mail malveillant, une URL malveillante ou un paramètre de boîte aux lettres à risque, et une action pour corriger cette menace est en attente [d'approbation.](air-review-approve-pending-completed-actions.md) <p> **L'état Action en attente** est déclenché lorsqu'une menace avec une action correspondante est trouvée. Toutefois, la liste des actions en attente peut augmenter au cours d'une enquête. Affichez les détails de l'examen pour voir si d'autres éléments sont en attente d'achèvement.|
|**Corrigé**|L'examen s'est terminé et toutes les actions de correction ont été approuvées (notées comme étant entièrement corrigés). <p> **REMARQUE**: les actions de correction approuvées peuvent avoir des erreurs qui empêchent les actions d'être prises. Que les actions de correction soient effectuées avec succès ou non, l'état de l'examen ne change pas. Afficher les détails de l'examen.|
|**Correction partielle**|L'examen a entraîné des actions de correction, dont certaines ont été approuvées et terminées. D'autres actions sont [toujours en attente.](air-review-approve-pending-completed-actions.md)|
|**Échec**|Au moins un analyseur d'examen a rencontré un problème dans lequel il n'a pas pu se terminer correctement. <p> **REMARQUE**: si un examen échoue après l'approbation des actions de correction, les actions de correction ont peut-être encore réussi. Afficher les détails de l'enquête. |
|**Mis en file d'attente par limitation**|Un examen est placé dans une file d'attente. Lorsque d'autres enquêtes sont terminées, les enquêtes en file d'attente commencent. La limitation permet d'éviter les performances médiocres du service.  <p> **CONSEIL**: les actions en attente peuvent limiter le nombre de nouvelles enquêtes qui peuvent s'exécuter. Veillez à [approuver (ou rejeter) les actions en attente.](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)|
|**Terminated By Throttling**|Si un examen est mis trop longtemps dans la file d'attente, il s'arrête. <p> **CONSEIL**: vous pouvez [démarrer une enquête à partir de l'Explorateur de menaces.](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)|
|

## <a name="view-details-of-an-investigation"></a>Afficher les détails d'une enquête

1. Go to the Microsoft 365 security center ( <https://security.microsoft.com> ) and sign in.
2. Dans le volet de navigation, sélectionnez **Centre de l'action.**
3. Sous les onglets **En attente** **ou** Historique, sélectionnez une action. Son volet volant s'ouvre.
4. Dans le volet volant, sélectionnez **Ouvrir la page Enquête.** 
5. Utilisez les différents onglets pour en savoir plus sur l'examen.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Afficher les détails d'une alerte liée à un examen

Certains types d'alerte déclenchent une enquête automatisée dans Microsoft 365. Pour en savoir plus, consultez les [stratégies d'alerte qui déclenchent des enquêtes automatisées.](office-365-air.md#which-alert-policies-trigger-automated-investigations)

1. Go to the Microsoft 365 security center ( <https://security.microsoft.com> ) and sign in.
2. Dans le volet de navigation, sélectionnez **Centre de l'action.**
3. Sous les onglets **En attente** **ou** Historique, sélectionnez une action. Son volet volant s'ouvre.
4. Dans le volet volant, sélectionnez **Ouvrir la page Enquête.** 
5. Sélectionnez **l'onglet Alertes** pour afficher la liste de toutes les alertes associées à cet examen.
6. Sélectionnez un élément dans la liste pour ouvrir son volet volant. Vous y pouvez afficher plus d'informations sur l'alerte.

## <a name="keep-the-following-points-in-mind"></a>Gardez les points suivants à l'esprit

- Le nombre d'e-mails est calculé au moment de l'enquête et certains sont recalculés lorsque vous ouvrez des volants d'enquête (sur la base d'une requête sous-jacente).

- Les nombres de messages affichés  pour les clusters de messagerie sous l'onglet Courrier électronique et la valeur de quantité de courrier indiquée dans le flyout de cluster sont calculés au moment de l'examen et ne changent pas.

- Le nombre de messages affichés en bas de l'onglet Courrier du flyout du cluster de messagerie et le nombre de messages affichés dans l'Explorateur reflètent les messages électroniques reçus après l'analyse initiale de l'enquête. 

  Par conséquent, un cluster de messagerie qui affiche une quantité d'origine de 10 messages électroniques affiche un total de 15 messages électroniques lorsque cinq autres messages électroniques arrivent entre la phase d'analyse de l'examen et lorsque l'administrateur examine l'examen. De même, les anciennes enquêtes peuvent commencer à afficher des nombres plus élevés que les requêtes De l'Explorateur, car les données dans Microsoft Defender pour Office 365 Plan 2 expirent après sept jours pour les essais et après 30 jours pour les licences payantes.

  L'affichage du nombre historique et du nombre actuel dans différents affichages est effectué pour indiquer l'impact de la messagerie au moment de l'examen et l'impact actuel jusqu'au moment où la correction est effectuée.

- Dans le contexte du courrier électronique, vous pouvez voir une surface de menace d'anomalie de volume dans le cadre de l'examen. Une anomalie de volume indique un pic du nombre de messages électroniques similaires au moment de l'événement d'investigation par rapport aux périodes antérieures. Un pic du trafic de messagerie ainsi que certaines caractéristiques (par exemple, le domaine de l'objet et de l'expéditeur, la similarité du corps et l'adresse IP de l'expéditeur) est caractéristique du début des campagnes ou des attaques par courrier électronique. Toutefois, les campagnes de courrier en masse, de courrier indésirable et légitimes partagent généralement ces caractéristiques.

- Les anomalies de volume représentent une menace potentielle et, par conséquent, peuvent être moins graves que les programmes malveillants ou les menaces de hameçonnage identifiés à l'aide de moteurs antivirus, de détonation ou de réputation malveillante.

- Vous n'avez pas besoin d'approuver chaque action. Si vous n'êtes pas d'accord avec l'action recommandée ou si  votre organisation ne choisit pas certains types d'actions, vous pouvez choisir de rejeter les actions ou simplement de les ignorer et de ne pas prendre d'action.

- L'approbation et/ou le rejet de toutes les actions permet à l'examen de se fermer complètement (l'état est corrigé), tout en laissant certaines actions incomplètes, l'état de l'examen passe à un état partiellement corrigé.

## <a name="next-steps"></a>Étapes suivantes

- [Examiner et approuver les actions en attente](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
