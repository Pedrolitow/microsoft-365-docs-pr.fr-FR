---
title: Correction du courrier électronique malveillant remis dans Office 365
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.service: Microsoft Threat Protection
audience: admin
f1.keywords:
- NOCSH
localization_priority: Normal
MS.collection: ''
search.appverid: MET150
description: Correction des menaces
appliesto:
- Microsoft Threat Protection
ms.openlocfilehash: 6c05eac80c6de546a30f9abe29360178bcbcfcf8
ms.sourcegitcommit: dc5de2064706137256307f100b8dc61e9797bd1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "45068185"
---
# <a name="remediate-malicious-email-that-was-delivered-in-office-365"></a>Correction du courrier électronique malveillant remis dans Office 365

La correction consiste à prendre une mesure apposée contre une menace. Les courriers électroniques malveillants envoyés dans votre organisation peuvent être nettoyés par le système, via la fonction ZAP (vidage automatique des heures zéro) ou par les équipes de sécurité par le biais d’actions correctives telles que déplacer vers la boîte de réception, se déplacer vers le dossier courrier indésirable, déplacer vers le dossier éléments supprimés, suppression récupérable ou suppression définitive. Office Advanced Threat Protection (ATP) P2/E5 offre aux équipes des opérations de sécurité la possibilité de contourner les menaces dans les e-mails et les problèmes de collaboration grâce à la chasse manuelle et à des enquêtes automatiques.

> [!NOTE]
> Pour que les équipes de sécurité puissent corriger les courriers électroniques, elles doivent disposer d’un rôle de recherche et de purge affecté. L’attribution de rôle s’effectue via les autorisations dans le centre de sécurité et de conformité. <p>

## <a name="what-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Pour effectuer certaines actions, telles que l’affichage des en-têtes de message ou le téléchargement du contenu d’un message électronique, vous devez disposer d’un nouveau rôle appelé *Aperçu* ajouté à un autre groupe de rôles approprié. Le tableau suivant clarifie les rôles et les autorisations requis.

|Activité  |Groupe de rôles |Prévisualiser le rôle nécessaire ?  |
|---------|---------|---------|
|Utilisation de l’Explorateur de menaces (et des détections en temps réel) pour analyser les menaces     |Administrateur général <br> Administrateur de sécurité <br> Lecteur de sécurité     | Non   |
|Utiliser l’Explorateur de menaces (et les détections en temps réel) pour afficher les en-têtes des messages électroniques, ainsi que pour afficher un aperçu et télécharger des messages électroniques mis en quarantaine    |Administrateur général <br> Administrateur de sécurité <br>Lecteur de sécurité   |       Non  |
|Utiliser l’Explorateur de menaces pour afficher les en-têtes et télécharger les messages électroniques remis aux boîtes aux lettres     |Administrateur général <br>Administrateur de sécurité <br> Lecteur de sécurité <br> Preview   |   Oui      |

> [!NOTE]
> L' *Aperçu* est un rôle et non un groupe de rôles ; le rôle aperçu doit être ajouté à un groupe de rôles existant pour Office 365. Le rôle administrateur général est affecté au centre d’administration Microsoft 365 ( [https://admin.microsoft.com](https://admin.microsoft.com) ), et les rôles Administrateur de sécurité et lecteur de sécurité sont affectés dans le centre de sécurité & conformité ( [https://protection.office.com](https://protection.office.com) ). Pour en savoir plus sur les rôles et les autorisations, consultez [la rubrique autorisations dans le centre de sécurité & conformité.](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center?view=o365-worldwide)

> [!NOTE]
> Les administrateurs peuvent effectuer des actions requises sur les courriers électroniques, mais leur action doit être affectée au rôle « recherche et purge » via le centre de sécurité et de conformité > autorisations.

## <a name="manual-and-automated-remediation"></a>Correction manuelle et automatique

Une recherche **manuelle** a lieu lorsque les équipes de sécurité identifient les menaces manuellement à l’aide des fonctionnalités de recherche et de filtrage dans l’Explorateur de menaces. La correction manuelle des e-mails peut être déclenchée via n’importe quelle vue e-mail (programme malveillant, hameçon ou tout le courrier électronique) après avoir trouvé un ensemble de courriers électroniques qui doivent être résolus.

![Chasse manuelle dans Office 365 Threat Explorer par date.](../../../media/tp-RemediationArticle1.png "Threat Explorer")

La sélection des courriers électroniques peut être effectuée de plusieurs façons via l’Explorateur de menaces :

1. Sélection de courriers électroniques à la main : cela signifie que les équipes des opérations de sécurité peuvent utiliser des filtres dans les vues respectives et sélectionner quelques messages électroniques provenant de l’Explorateur de menaces qui doivent être résolus. La limite supérieure de sélection des courriers électroniques est de 100 (100). Les équipes d’opérations de sécurité ne peuvent pas sélectionner plus de centaines de courriers électroniques, manuellement.

2. Sélection de requête : les équipes d’opérations de sécurité peuvent sélectionner une requête entière à l’aide du bouton « Sélectionner tout ». La même requête apparaît également dans les détails de l’envoi de messages du centre d’action.

3. Sélection de requête avec exclusion : il peut arriver que des équipes d’opérations de sécurité décident de corriger les courriers électroniques en sélectionnant une requête entière et en excluant manuellement quelques messages électroniques de la requête. Pour ce faire, un administrateur peut utiliser la case à cocher « Sélectionner tout » et faire défiler vers le bas pour exclure quelques courriers électroniques, manuellement. Le nombre maximal de messages électroniques que la requête peut contenir est 1000 (1 000) et le nombre maximal d’exclusions est de 100 (100), dans ce cas.

Une fois que les courriers électroniques sont sélectionnés dans l’Explorateur de menaces, la création de la correction peut commencer par une action directe ou par la mise en file d’attente de messages électroniques pour une action :

1. Approbation directe : lorsque des actions telles que « déplacer vers la boîte de réception », « déplacer vers le courrier indésirable », « déplacer vers les éléments supprimés », « supprimer définitivement », « supprimer définitivement » sont sélectionnées par le personnel de sécurité avec des autorisations appropriées, et que les étapes suivantes sont suivies jusqu’à la création des corrections. Un lanceur temporaire affiche la correction en cours.

2. Approbation en deux étapes : l’action Ajouter à la correction peut être effectuée par un administrateur qui ne dispose pas des autorisations appropriées ou qui doit attendre plus longtemps pour exécuter l’action. Dans ce cas, l’action de correction n’est pas exécutée directement. Au lieu de cela, les messages électroniques sont ajoutés à un conteneur de correction qui doit être approuvé pour s’exécuter. Tant que la correction n’est pas approuvée, le courrier électronique ne sera pas résolu. Une fois les corrections approuvées, les actions seront effectuées dans le courrier électronique.

Les actions d' **enquête et de réponse automatiques** sont déclenchées par des alertes ou par des équipes d’opérations de sécurité dans l’Explorateur de menaces. Elles peuvent inclure certaines médiations recommandées qui doivent être approuvées par les équipes des opérations de sécurité. Ces actions de correction sont incluses dans l’onglet action au sein de l’enquête automatisée.  

:::image type="content" source="../../../media/tp-RemediationArticle3.png" alt-text="Le courrier électronique avec des programmes malveillants est une page zapped indiquant le moment de l’exécution de l’opération zap.":::

Toute la médiation (approbation directe ou approbation en deux étapes) créée via l’Explorateur de menaces, ainsi que les actions approuvées provenant d’analyses automatisées, s’affichent dans le centre de maintenance, accessible via le volet de navigation de gauche sous *examiner*le >  **Centre de maintenance**.

:::image type="content" source="../../../media/tp-RemediationArticle4.png" alt-text="Centre de notifications avec une liste des menaces par date et gravité.":::

Le centre de maintenance affiche toutes les actions de correction au cours des 30 derniers jours. Les actions effectuées via l’Explorateur s’affichent avec le même nom fourni par les équipes des opérations de sécurité lorsque la correction a été créée. Les actions réalisées par le biais d’enquêtes automatisées sont exposées aux titres qui commencent par l’alerte qui a déclenché l’enquête, par exemple « zap mail cluster... ».

Chaque élément de correction peut être ouvert pour en afficher les détails. Lorsqu’un élément de correction est ouvert, il affiche les détails de la correction de base, le nom de la correction, la date de création, la description, la gravité des menaces et l’État. Il présente également deux onglets. 

1. **Onglet envoi de courrier**: Voici le nombre de messages électroniques envoyés par le biais de l’Explorateur de menaces ou des investigations automatiques à résoudre. Ces messages électroniques peuvent être les suivants :

:::image type="content" source="../../../media/tp-RemediationArticle5.png" alt-text="Le centre de notifications avec des menaces actionnables et non exploitables.":::

Fonction **exploitable**: les courriers électroniques dans les emplacements de boîtes aux lettres Cloud suivants peuvent être traités et déplacés par exemple : tout courrier électronique appartenant à la catégorie pouvant être résolue peut être déplacé d’un emplacement à un autre :
  - Boîte de réception 
  - Filtre  
  - Dossier supprimé
  - Dossier supprimé (récupérable)

>[!NOTE]
> Actuellement, seul un utilisateur final ayant accès à la boîte aux lettres peut récupérer des éléments à partir d’un dossier de suppression récupérable.

**Non actionnable**: les courriers électroniques aux emplacements suivants ne peuvent pas être traités ou déplacés dans le cadre des actions de messagerie (par exemple, les courriers électroniques dans une catégorie non réutilisable ne peuvent pas être déplacés dans la catégorie non réutilisable, ni dans un délai résolu). Les emplacements non réessayez sont les suivants :

  - Quarantaine
  - Dossier supprimé définitivement
  - Local/externe
  - Échec/suppression
  
Les messages suspects soumis sont catégorisés comme étant résolus ou non résolus. Dans la plupart des cas, les messages résolus et non résolus doivent être ajoutés au nombre total de messages envoyés. Toutefois, il peut y avoir quelques rares cas où les messages soumis peuvent ne pas être ajoutés à la somme des éléments résolus et non résolus, et peuvent être plus ou moins élevés que le nombre total de messages envoyés. Cela peut se produire en raison de délais système, délais ou messages expirés. Les messages expirent en fonction de la période de rétention de l’Explorateur pour votre organisation.

À moins que vous ne corrigez les anciens messages après la période de rétention de l’Explorateur de votre organisation, si vous constatez des incohérences dans les numéros, il est recommandé de réessayer d’effectuer la correction des éléments. Pour les retards système, les mises à jour correctives sont généralement actualisées en quelques heures.

Si la période de rétention de votre organisation pour les messages électroniques dans Explorer est de 30 jours et que vous corrigez les courriers électroniques à 29-30 jours en arrière, le nombre de messages envoyés peut ne pas être toujours ajouté car les messages peuvent avoir commencé à sortir de la période de rétention.

Si la médiation est bloquée dans un État « en cours » pendant un certain temps, cela est probablement dû à des retards système. La correction peut prendre jusqu’à quelques heures. Il peut y avoir une variation observée dans le compte d’envoi de messages, car certains messages n’étaient pas inclus dans la requête pendant le démarrage de la correction suite à des retards système. Il est recommandé de retenter la correction dans de tels cas.  

Pour obtenir de meilleurs résultats, la correction doit être réalisée dans des lots moins volumineux de plus de 50 000 ou moins de messages électroniques.  

Parmi tous les messages électroniques envoyés, les messages électroniques résolus sont les seuls qui seront traités pendant la correction. Les courriers électroniques non résolus ne peuvent pas être corrigés par le système de courrier Office 365, car ils ne sont pas stockés dans les boîtes aux lettres Cloud.

Pour les messages électroniques détectés en quarantaine, les administrateurs peuvent mettre en quarantaine pour prendre des mesures sur ces messages électroniques si nécessaire, mais les messages seront Expires en quarantaine s’ils ne sont pas supprimés manuellement. Les messages mis en quarantaine en raison d’un contenu malveillant ne sont pas accessibles par les utilisateurs finaux, de sorte que le personnel de sécurité n’a pas besoin de prendre des mesures spécifiques pour se débarrasser de la menace en quarantaine. Si les messages électroniques sont local ou externes, l’utilisateur final peut être contacté afin de traiter le courrier électronique suspect ou utiliser un serveur de messagerie/outils de sécurité distincts pour la suppression. Ces e-mails peuvent être identifiés par l’application de l’emplacement de remise = local/filtre externe dans l’Explorateur de menaces. Pour les messages électroniques ayant échoué ou supprimés, ou les messages électroniques qui ne sont pas accessibles par l’utilisateur final, il ne doit pas y avoir de courrier électronique à limiter, car ils n’atteignent pas la boîte aux lettres.

Voici comment un envoi apparaît dans le centre de notifications. Une correction peut contenir plusieurs envois. Si plusieurs actions sont approuvées par le biais d’une enquête automatisée, chaque action de messagerie électronique ou de cluster de messagerie s’affiche dans les mêmes mesures correctives qu’une autre soumission.

:::image type="content" source="../../../media/tp-RemediationArticle6.png" alt-text="Zap panneau de débattement du cluster de messagerie.":::

Le fait de cliquer sur un élément de dépôt de courrier indique les détails de ces corrections telles que la requête (lorsque la correction est déclenchée via des analyses automatiques ou l’Explorateur de menaces par la sélection d’une requête), l’heure de début et l’heure de fin, de correction. Il affiche également une liste des messages qui ont été envoyés pour correction. Lorsque les messages quittent la période de rétention de l’Explorateur, les messages disparaissent de cette liste. Cette liste affiche également les messages individuels de la liste qui sont résolus.

2. **Onglet journaux des actions**: cet onglet affiche le résultat des messages corrigés, notamment les détails tels que date approuvée, approbateur (administrateur qui a approuvé l’action), action, État et nombre.  

Status indique l’état global de la correction. L’État peut être :

  - **Démarré**: lorsqu’une correction est déclenchée.
  - En **file d’attente**: lorsque la correction est mise en file d’attente pour atténuer les messages électroniques.
  - **En cours**: lorsque l’atténuation est en cours.
  - **Terminé**: lorsque l’atténuation sur tous les e-mails résolus est effectuée avec succès ou avec certains échecs. 
  - **Échec**: lorsque aucune correction n’aboutit.

À mesure que seuls des e-mails pouvant être résolus peuvent être traités, le nettoyage de chaque message électronique est considéré comme réussi ou échoué. À partir du total des e-mails résolus, nous exposez les atténuations ayant réussi et échoué.

  - **Réussite**: lorsque l’action souhaitée sur des courriers électroniques résolus est effectuée et correspond à l’intention de l’administrateur. Par exemple : un administrateur souhaite supprimer les courriers électroniques des boîtes aux lettres, de sorte qu’il effectue l’action de suppression logicielle des courriers électroniques. Si un e-mail résolu est introuvable dans le dossier d’origine une fois l’action effectuée, l’État s’affiche avec succès.  

  - **Échec**: lorsque l’action souhaitée sur des courriers électroniques résolus échoue. Par exemple : un administrateur souhaite supprimer les courriers électroniques des boîtes aux lettres, de sorte qu’il effectue l’action de suppression logicielle des courriers électroniques. Si un e-mail résolu est toujours trouvé dans la boîte aux lettres, l’état indique échec.

En cliquant sur n’importe quel élément dans le journal des actions, affiche les détails de la correction. Pour les éléments réussis, si les détails indiquent, réussi ou introuvable dans la boîte aux lettres, cela signifie que l’élément a déjà été supprimé de la boîte aux lettres. Il peut arriver que des défaillances se produisent suite à une erreur système lors de la correction, et dans ce cas, il est recommandé de retenter la correction.  

La correction est un outil puissant pour atténuer les menaces et résoudre les courriers électroniques suspects. Elle permet de maintenir la sécurité et la sécurité d’une organisation.  

## <a name="more-info"></a>Plus d’informations

Obtenir<https://docs.microsoft.com/microsoft-365/security/office-365-security/investigate-malicious-email-that-was-delivered?view=o365-worldwide>