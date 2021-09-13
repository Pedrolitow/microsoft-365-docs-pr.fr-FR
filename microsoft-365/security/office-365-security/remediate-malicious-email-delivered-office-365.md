---
title: Corriger les messages malveillants qui ont été remis dans Office 365
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
audience: admin
f1.keywords:
- NOCSH
localization_priority: Normal
MS.collection: ''
search.appverid: MET150
description: Correction des menaces
appliesto:
- Microsoft 365 Defender
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: de9f68c193a8c7ab4d4c78fc4f2cef3cf02142ec
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59179203"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Corriger les messages malveillants remis dans Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

La correction signifie prendre une action prescrite contre une menace. Les e-mails malveillants envoyés à votre organisation peuvent être nettoyés par le système, par le biais d’une purge automatique de zéro heure (ZAP) ou par les équipes de sécurité par le biais d’actions de correction telles que le déplacement vers la boîte de *réception,* le déplacement vers le courrier *indésirable,* le déplacement vers les éléments supprimés, la suppression possible ou la suppression *dure.* Microsoft Defender pour Office 365 Plan 2/E5 permet aux équipes de sécurité de corriger les menaces dans les fonctionnalités de messagerie électronique et de collaboration par le biais d’examens manuels et automatisés.

> [!NOTE]
> Pour corriger les messages malveillants, les équipes de sécurité *ont* besoin du rôle Rechercher et Vider qui leur est attribué. L’attribution de rôle est effectuée [par le biais des autorisations dans le portail Microsoft 365 Defender.](permissions-microsoft-365-security-center.md)

## <a name="what-you-need-to-know-before-you-begin"></a>Ce que vous devez savoir avant de commencer

Les administrateurs peuvent effectuer les actions requises sur les e-mails, mais pour obtenir ces actions approuvées, le rôle Recherche et purge doit leur être attribué dans les autorisations de **collaboration** de l'& de messagerie sur le portail Microsoft 365 Defender.  Sans le *rôle Rechercher et purger »* ajouté à l’un des groupes de rôles, ils ne pourront pas exécuter l’action.

## <a name="manual-and-automated-remediation"></a>Correction manuelle et automatisée

*Le hunting manuel* se produit lorsque les équipes de sécurité identifient les menaces manuellement à l’aide des fonctionnalités de recherche et de filtrage dans l’Explorateur. La correction manuelle du courrier électronique peut être déclenchée par n’importe quel affichage de courrier *électronique*(programme *malveillant,* hameçonnage ou tout e-mail) une fois que vous avez identifié un ensemble d’e-mails qui doivent être corrigés.

> [!div class="mx-imgBorder"]
> [![Recherche manuelle dans Office 365'Explorateur de menaces par date.](../../media/tp-RemediationArticle1.png)](../../media/tp-RemediationArticle1.png#lightbox)

Les équipes de sécurité peuvent utiliser l’Explorateur pour sélectionner des e-mails de plusieurs manières :

- Sélectionnez les e-mails à la main : utilisez des filtres dans différents affichages. Sélectionnez jusqu’à 100 e-mails à corriger.

- Sélection de requête : sélectionnez une requête entière à l’aide du bouton **Tout sélectionner en** haut. La même requête est également affichée dans les détails de l’envoi de courrier du centre de messages.

- Sélection de requête avec exclusion : parfois, les équipes en charge des opérations de sécurité peuvent vouloir corriger les messages électroniques en sélectionnant une requête entière et en excluant manuellement certains e-mails de la requête. Pour ce faire, un  administrateur peut utiliser la case à cocher Sélectionner tout et faire défiler vers le bas pour exclure manuellement les e-mails. La requête peut contenir un maximum de 1 000 e-mails. Le nombre maximal d’exclusions est de 100.

Une fois que les e-mails sont sélectionnés par le biais de l’Explorateur, vous pouvez commencer la correction en prenant des mesures directes ou en les interrogeant pour une action :

- Approbation directe : lorsque des actions telles que le déplacement vers la  boîte de *réception,* le déplacement vers le courrier *indésirable,* le déplacement vers les éléments supprimés, la suppression définitive ou la suppression définitive sont sélectionnées par le personnel de sécurité qui a les autorisations appropriées et que les étapes suivantes de la correction sont suivies, le processus de correction commence à exécuter l’action sélectionnée. Un programme volant temporaire affiche la correction en cours.

- Approbation en deux étapes : une action d’ajout à la correction peut être prise par les administrateurs qui ne sont pas autorisés à exécuter l’action ou qui doivent attendre. Dans ce cas, les e-mails ciblés sont ajoutés à un conteneur de correction. Une approbation est nécessaire avant l’exécution de la correction.

**Les actions d’investigation et de** réponse automatisées sont déclenchées par des alertes ou par des équipes d’opérations de sécurité de l’Explorateur. Il peut s’agir d’actions de correction recommandées qui doivent être approuvées par une équipe des opérations de sécurité. Ces actions sont incluses sous **l’onglet Action** dans l’examen automatisé.

> [!div class="mx-imgBorder"]
> [![Courrier avec programme malveillant dans la page « Péred » affichant l’heure de l’exécution de Zap.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Toutes les corrections (approbation directe ou approbation en deux étapes) qui ont été créées dans l’Explorateur, ainsi que les actions approuvées provenant d’enquêtes automatisées, sont affichées dans le Centre de gestion des actions. Accédez à ces éléments via le panneau de navigation de gauche sous **Centre** \> **de révision de l’action.**

> [!div class="mx-imgBorder"]
> [![Centre de mesures avec une liste des menaces par date et gravité.](../../media/tp-RemediationArticle4.png)](../../media/tp-RemediationArticle4.png#lightbox)

Le centre de mise en œuvre affiche toutes les actions de correction pour les 30 derniers jours. Les actions entreprises via l’Explorateur sont répertoriées par le nom fourni par l’équipe des opérations de sécurité lors de la création de la correction. Les actions entreprises par le biais d’enquêtes automatisées ont des titres qui commencent par l’alerte associée qui a déclenché l’enquête, telles que « Cluster de courrier Zap... ».

Ouvrez n’importe quel élément de correction pour afficher des détails à son sujet, notamment son nom, sa date de création, sa description, sa gravité et son état. Il affiche également les deux onglets suivants.

- **Onglet Envoi du** courrier : affiche le nombre d’e-mails envoyés par le biais de l’Explorateur de menaces ou d’enquêtes automatisées à corriger. Ces e-mails peuvent être actionnables ou ne peuvent pas être actionnables.

  > [!div class="mx-imgBorder"]
  > [![Centre de actions avec des menaces actionnables et non actionnables.](../../media/tp-RemediationArticle5.png)](../../media/tp-RemediationArticle5.png#lightbox)

  - **Actionnable**: les e-mails des emplacements de boîte aux lettres cloud suivants peuvent être actionnables et déplacés :
    - Boîte de réception
    - Courrier indésirable
    - Dossier supprimé
    - Dossier supprimé (supprimé(s) (supprimé(s) (supprimé(s)

      > [!NOTE]
      > Actuellement, seul un utilisateur ayant accès à la boîte aux lettres peut récupérer des éléments à partir d’un dossier supprimé (récupérable).

  - **Non actionnable**: les messages électroniques aux emplacements suivants ne peuvent pas être actionnables ou déplacés dans les actions de correction :
    - Quarantaine
    - Dossier supprimé définitivement
    - Local/externe
    - Échec/abandon

  Les messages suspects sont classés comme étant soit remédiables, soit non immédiates. Dans la plupart des cas, les messages remédiables et les messages non immédiatement remédiables sont égaux au nombre total de messages envoyés. Mais dans de rares cas, cela peut ne pas être vrai. Cela peut se produire en raison de retards du système, de délais d’expiration ou de messages expirés. Les messages expirent en fonction de la période de rétention de l’Explorateur pour votre organisation.

  Sauf si vous remédiez aux anciens messages après la période de rétention de l’Explorateur de votre organisation, il est conseillé de réessayer de corriger les éléments en cas d’incohérence de nombre. Pour les retards du système, les mises à jour de correction sont généralement actualisées en quelques heures.

  Si la période de rétention du courrier électronique de votre organisation dans l’Explorateur est de 30 jours et que vous remédiez aux messages électroniques de 29 à 30 jours, il se peut que le nombre de dépôts de messages ne s’ajoute pas toujours. Les e-mails ont peut-être déjà commencé à sortir de la période de rétention.

  Si les corrections sont bloquées à l’état « En cours » pendant un certain temps, cela est probablement dû à des retards du système. La correction peut prendre jusqu’à quelques heures. Vous pouvez voir des variations dans le nombre d’envois de courrier, car certains messages électroniques n’ont peut-être pas été inclus dans la requête au début de la correction en raison de retards du système. Il est bon de réessayer d’y remédier.

  > [!NOTE]
  > Pour de meilleurs résultats, la correction doit être effectuée par lots de 50 000 ou moins.

  Seuls les e-mails remédiables sont actionn s pendant la correction. Les messages électroniques non instantanés ne peuvent pas être corrigés par le système de messagerie Office 365, car ils ne sont pas stockés dans des boîtes aux lettres cloud.

  Les administrateurs peuvent prendre des mesures sur les e-mails mis en quarantaine si nécessaire, mais ils expireront hors de la quarantaine s’ils ne sont pas purgés manuellement. Les e-mails mis en quarantaine en raison de contenus malveillants ne sont pas accessibles par les utilisateurs, de sorte que le personnel de sécurité n’a aucune action à prendre pour se débarrasser des menaces en quarantaine. Si les e-mails sont locaux ou externes, l’utilisateur peut être contacté pour traiter le message suspect. Les administrateurs peuvent également utiliser des outils de sécurité/serveur de messagerie distincts pour la suppression. Ces *e-mails* peuvent être identifiés en appliquant l’emplacement de remise = filtre externe sur site dans l’Explorateur. En cas d’échec ou de abandon du courrier électronique ou de courrier non accessible par les utilisateurs, il n’y aura aucun message électronique à atténuer, car ces messages n’atteignent pas la boîte aux lettres.

  L’image suivante montre l’apparence d’une soumission dans le centre de données. Une correction peut contenir plusieurs soumissions. Si plusieurs actions sont approuvées par le biais d’un examen automatisé, chaque action de cluster de courrier ou de courrier électronique apparaît dans la même correction qu’une soumission différente.

  > [!div class="mx-imgBorder"]
  > [![Panneau volant de cluster de messagerie ZAP.](../../media/tp-RemediationArticle6.png)](../../media/tp-RemediationArticle6.png#lightbox)

  Sélectionnez un élément de soumission de courrier pour afficher les détails de cette correction, par exemple la requête (lorsque la correction est déclenchée par des enquêtes automatisées ou l’Explorateur par le biais de la sélection d’une requête) et les heures de début et de fin de la correction. Il affiche également une liste des messages qui ont été envoyés pour correction. À mesure que les messages sortent de la période de rétention de l’Explorateur, ils disparaissent de cette liste. La liste affiche également les messages individuels qui sont remédiables.

- **Journaux d’action**: cet onglet affiche les messages corrigés, y compris la date approuvée, l’administrateur qui a approuvé l’action, l’action, l’état et le nombre.

  L’état peut être :

  - **Démarré :** la correction est déclenchée.
    - **Mise en file d’attente**: la correction est mise en file d’attente pour l’atténuation des messages électroniques.
    - **En cours**: l’atténuation est en cours.
    - **Terminé :** l’atténuation sur tous les e-mails remédiables s’est terminée correctement ou avec certains échecs.
    - **Échec :** aucune correction n’a réussi.

  Comme seuls les e-mails remédiables peuvent être pris en compte, le nettoyage de chaque e-mail s’affiche comme réussi ou a échoué. À partir du nombre total d’e-mails remédiables, les atténuations réussies et échouées sont signalées.

  - **Réussite**: l’action souhaitée sur les e-mails corrects a été accomplie. Par exemple : un administrateur souhaite supprimer des e-mails des boîtes aux lettres, afin qu’il prenne l’action de supprimer les e-mails de la sorte. Si un e-mail remédiable n’est pas trouvé dans le dossier d’origine une fois l’action entreprise, l’état s’affiche comme réussi.

  - **Échec :** échec de l’action souhaitée sur les e-mails corrects. Par exemple : un administrateur souhaite supprimer des e-mails des boîtes aux lettres, afin qu’il prenne l’action de supprimer les e-mails de la sorte. Si un e-mail remédiable est toujours trouvé dans la boîte aux lettres après que l’action a été prise, l’état s’affiche comme étant un échec.
  
  - **Déjà dans la destination**: l’action souhaitée a déjà été prise sur l’e-mail ou l’e-mail existait déjà dans l’emplacement de destination. Par exemple : un e-mail a été supprimé (à la demande) par l’administrateur via l’Explorateur le premier jour. Ensuite, des messages électroniques similaires s’afficheront le jour 2, qui sont de nouveau supprimés (supprimés de façon souple) par l’administrateur. Lors de la sélection de ces e-mails, l’administrateur finit par sélectionner certains e-mails du premier jour qui sont déjà supprimés (supprimés de la sorte). À présent, ces e-mails ne seront pas retentés, ils s’afficheront simplement comme « déjà dans la destination », car aucune action n’a été prise sur eux comme ils existaient dans l’emplacement de destination.

  - **Nouveau**: une colonne déjà dans *la destination* a été ajoutée dans le journal des actions. Cette fonctionnalité utilise le dernier emplacement de remise dans l’Explorateur de menaces pour signaler si le courrier a déjà été corrigé. *La destination déjà en cours* permettra aux équipes de sécurité de comprendre le nombre total de messages qui doivent encore être traités.
                
Les actions peuvent uniquement être prises sur les messages dans les dossiers Boîte de réception, Courrier indésirable, Supprimé et Supprimé (suppression possible) de l’Explorateur de menaces. Voici un exemple de fonctionnement de la nouvelle colonne. Une *action de suppression souple* a lieu sur le message présent dans la boîte de réception, puis le message est géré conformément aux stratégies. Lors de la prochaine suppression, ce message s’affichera sous la colonne « Déjà dans la destination » signalant qu’il n’est pas nécessaire de le traiter à nouveau.

Sélectionnez n’importe quel élément dans le journal des actions pour afficher les détails de correction. Si les détails indiquent « réussite » ou « in trouvé dans la boîte aux lettres », cet élément a déjà été supprimé de la boîte aux lettres. Parfois, il y a une erreur système lors de la correction. Dans ce cas, il est bon de réessayer l’action de correction.

Dans le cas de la correction de lots importants de courriers électroniques, exportez les messages envoyés pour correction via l’envoi du courrier électronique et les messages qui ont été corrigés via les journaux d’action. La limite d’exportation est augmentée à 100 000 enregistrements.

La correction permet d’atténuer les menaces, de répondre aux messages électroniques suspects et de sécuriser une organisation.
