---
title: Corriger les e-mails malveillants qui ont été remis dans Office 365
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.collection: M365-security-compliance
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: ''
search.appverid: MET150
description: Correction des menaces
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d584ce10f4e119ec4fe8aa2991c6cac0edd5377c
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621906"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Corriger les courriers malveillants remis dans Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

La correction consiste à prendre une mesure prescrite contre une menace. Les e-mails malveillants envoyés à votre organisation peuvent être nettoyés par le système, par le biais d’un vidage automatique de zéro heure (ZAP), ou par des équipes de sécurité via des actions de correction telles que *le passage à la boîte de réception*, *le déplacement vers le courrier indésirable*, *le déplacement vers les éléments supprimés*, la *suppression réversible* ou la *suppression définitive*. Microsoft Defender pour Office 365 Plan 2/E5 permet aux équipes de sécurité de corriger les menaces dans les fonctionnalités de messagerie et de collaboration par le biais d’une investigation manuelle et automatisée.

> [!NOTE]
> Pour corriger les e-mails malveillants, les équipes de sécurité ont besoin du rôle *De recherche et de vidage* qui leur est attribué. L’attribution de rôle s’effectue via [des autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="what-you-need-to-know-before-you-begin"></a>Ce que vous devez savoir avant de commencer

Les administrateurs peuvent prendre les mesures nécessaires sur les e-mails, mais pour que ces actions soient approuvées, le rôle *De recherche et de vidage* doit leur être attribué dans les autorisations **e-mail & collaboration** dans le portail Microsoft 365 Defender. Sans le rôle *Rechercher et vider ajouté* à l’un des groupes de rôles, ils ne pourront pas exécuter l’action.

## <a name="manual-and-automated-remediation"></a>Correction manuelle et automatisée

*La chasse manuelle* se produit lorsque les équipes de sécurité identifient manuellement les menaces à l’aide des fonctionnalités de recherche et de filtrage dans l’Explorateur. La correction manuelle de l’e-mail peut être déclenchée via n’importe quelle vue de messagerie (*programme malveillant*, *hameçonnage* ou *tous les e-mails*) après avoir identifié un ensemble d’e-mails qui doivent être corrigés.

:::image type="content" source="../../media/microsoft-365-defender-threat-explorer-manual-remediation.png" alt-text="Capture d’écran de la chasse manuelle dans Office 365 Explorer par date.":::

Les équipes de sécurité peuvent utiliser l’Explorateur pour sélectionner des e-mails de plusieurs façons :

- Choisissez les e-mails manuellement : utilisez des filtres dans différentes vues. Sélectionnez jusqu’à 100 e-mails à corriger.

- Sélection de la requête : sélectionnez une requête entière à l’aide du bouton **Sélectionner tout** en haut. La même requête est également affichée dans les détails de la soumission de courrier du Centre d’actions. Les clients peuvent envoyer un maximum de 200 000 e-mails à partir de l’Explorateur de menaces.  

- Sélection des requêtes avec exclusion : parfois, les équipes chargées des opérations de sécurité peuvent vouloir corriger les e-mails en sélectionnant une requête entière et en excluant manuellement certains e-mails de la requête. Pour ce faire, un administrateur peut utiliser la case à cocher **Sélectionner tout** et faire défiler vers le bas pour exclure manuellement les e-mails. La requête peut contenir un maximum de 1 000 e-mails. Le nombre maximal d’exclusions est de 100.

Une fois les e-mails sélectionnés par le biais de l’Explorateur, vous pouvez commencer la correction en effectuant une action directe ou en mettant en file d’attente des e-mails pour une action :

- Approbation directe : lorsque des actions telles que *le déplacement vers la boîte de réception*, *le déplacement vers le courrier indésirable*, le *déplacement vers des éléments supprimés*, la *suppression réversible* ou la *suppression définitive* sont sélectionnées par le personnel de sécurité disposant des autorisations appropriées, et que les étapes suivantes de la correction sont suivies, le processus de correction commence à exécuter l’action sélectionnée.
> [!NOTE]
> Lorsque la correction est lancée, elle génère une alerte et une enquête en parallèle. L’alerte s’affiche dans la file d’attente des alertes avec le nom « Action administrative soumise par un administrateur », ce qui indique que le personnel de sécurité a pris l’action de corriger une entité. Il présente des détails tels que le nom de la personne qui a effectué l’action, la prise en charge du lien d’investigation, l’heure, etc. Il fonctionne vraiment bien de savoir chaque fois qu’une action dure comme la correction est effectuée sur les entités. Toutes ces actions peuvent être suivies sous l’onglet **Actions & Submissions** \> **Action** **centerHistory**  ->  (préversion publique).

- Approbation en deux étapes : une action « Ajouter à la correction » peut être effectuée par des administrateurs qui ne disposent pas des autorisations appropriées ou qui doivent attendre pour exécuter l’action. Dans ce cas, les e-mails ciblés sont ajoutés à un conteneur de correction. L’approbation est nécessaire avant l’exécution de la correction.

**Les actions d’investigation et de réponse automatisées** sont déclenchées par des alertes ou par des équipes d’opérations de sécurité de l’Explorateur. Il peut s’agir d’actions de correction recommandées qui doivent être approuvées par une équipe des opérations de sécurité. Ces actions sont incluses dans l’onglet **Action** de l’enquête automatisée.

> [!div class="mx-imgBorder"]
> [![Courrier avec un programme malveillant dans la page « Zapped » montrant l’heure d’exécution de Zap.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Toutes les corrections (approbations directes) créées dans l’Explorateur, la chasse avancée ou par le biais d’une investigation automatisée sont affichées dans le Centre d’actions. Accédez-y via le panneau de navigation gauche sous **l’onglet Actions & Submissions** \> **Action** **centerHistory**  -> .

Toutes les corrections (approbations directes) qui ont été créées dans l’Explorateur ou la chasse avancée ou par le biais d’une investigation automatisée sont affichées dans le Centre d’actions. Accédez-y via le panneau de navigation gauche sous **l’onglet Actions & Submissions** \> **Action** **centerHistory**  -> . 

Actions manuelles en attente d’approbation à l’aide du processus d’approbation en deux étapes (1. ajouter à la correction par un membre de l’équipe d’opération de sécurité, 2. examinés et approuvés par un autre membre de l’équipe d’opération de sécurité) sont visibles uniquement dans le **centre** d’action Defender pour Office 365 centre d’action **hérité et** \> non dans les incidents/investigations et le Centre d’action unifiée.

> [!NOTE]
> Approbation en deux étapes : actions disponibles uniquement dans le centre d’actions office  **Review** \> **Action Center**

:::image type="content" source="../../media/microsoft-365-defender-action-center-history.png" alt-text="Le Centre d’actions unifié affiche 30 jours d’actions de correction.":::

Le Centre d’actions unifié affiche les actions de correction des 30 derniers jours. Les actions effectuées via l’Explorateur sont répertoriées par le nom fourni par l’équipe des opérations de sécurité lors de la création de la correction, ainsi que l’ID d’approbation, ID d’investigation. Les actions effectuées dans le cadre d’enquêtes automatisées ont des titres qui commencent par l’alerte associée qui a déclenché l’enquête, telle que le *cluster de messagerie Zap*.

Ouvrez tout élément de correction pour afficher des détails à son sujet, notamment son nom de correction, son ID d’approbation, son ID d’investigation, sa date de création, sa description, son état, sa source d’action, son type d’action, son état. Il ouvre également un volet latéral avec les détails de l’action, les détails du cluster d’e-mail, les alertes et les détails de l’incident.

- *Ouvrez la page Investigation* pour ouvrir une enquête d’administration qui contient moins de détails et d’onglets. Il affiche des détails tels que : alerte associée, entité sélectionnée pour la correction, action effectuée, état de correction, nombre d’entités, journaux d’activité, approbateur d’action. Cette enquête effectue un suivi de l’enquête effectuée manuellement par l’administrateur et contient des détails sur les sélections effectuées par l’administrateur. Par conséquent, il s’agit de l’enquête sur les actions de l’administrateur. Pas besoin d’agir sur l’enquête et d’alerter son état déjà approuvé.
- *Nombre d’e-mails* Affiche le nombre d’e-mails envoyés via l’Explorateur de menaces. Ces e-mails peuvent être actionnables ou non exploitables.
- *Journaux d’activité des actions* Affichez les détails des états de correction tels que le succès, l’échec et déjà dans la destination.

:::image type="content" source="../../media/microsoft-365-defender-action-center-history-panel.png" alt-text="Centre d’actions avec l’option Déplacer vers la boîte de réception ouverte.":::

  - **Actionnable** : les e-mails dans les emplacements de boîte aux lettres cloud suivants peuvent être activés et déplacés :
    - Boîte de réception
    - Indésirable
    - Dossier supprimé
    - Dossier supprimé de manière réversible

      > [!NOTE]
      > Actuellement, seul un utilisateur ayant accès à la boîte aux lettres peut récupérer des éléments à partir d’un dossier supprimé de manière réversible.

  - **Non actionnable** : les e-mails situés aux emplacements suivants ne peuvent pas être activés ou déplacés dans les actions de correction :
    - Quarantaine
    - Dossier supprimé en dur
    - Local/externe
    - Échec/suppression

  Les messages suspects sont classés comme étant remédiables ou non irrémédiables. Dans la plupart des cas, les messages remédiables et non irrémédiables combinent le nombre total de messages envoyés. Mais dans de rares cas cela peut ne pas être vrai. Cela peut se produire en raison de retards système, de délais d’expiration ou de messages expirés. Les messages expirent en fonction de la période de rétention de l’Explorateur pour votre organisation.

  Sauf si vous corrigez les anciens messages après la période de rétention de l’Explorateur de votre organisation, il est recommandé de réessayer de corriger les éléments si des incohérences de nombre s’affichent. Pour les retards système, les mises à jour de correction sont généralement actualisées en quelques heures.

  Si la période de rétention de votre organisation pour les e-mails dans l’Explorateur est de 30 jours et que vous corrigez les e-mails entre 29 et 30 jours, le nombre de soumissions de courriers peut ne pas toujours s’additionner. Les e-mails ont peut-être déjà commencé à sortir de la période de rétention.

  Si les corrections sont bloquées dans l’état « En cours » pendant un certain temps, cela est probablement dû à des retards système. La correction peut prendre jusqu’à quelques heures. Vous pouvez voir des variations dans le nombre de soumissions de courrier, car certains e-mails n’ont peut-être pas été inclus dans la requête au début de la correction en raison de retards système. Il est judicieux de réessayer de corriger ce genre de situation.

  > [!NOTE]
  > Pour de meilleurs résultats, la correction doit être effectuée par lots de 50 000 ou moins.

  Seuls les e-mails remédiables sont activés lors de la correction. Les e-mails non irrémédiables ne peuvent pas être corrigés par le système de messagerie Office 365, car ils ne sont pas stockés dans des boîtes aux lettres cloud.

  Les administrateurs peuvent prendre des mesures sur les e-mails en quarantaine si nécessaire, mais ces e-mails expireront hors de la quarantaine s’ils ne sont pas vidés manuellement. Par défaut, les e-mails mis en quarantaine en raison d’un contenu malveillant ne sont pas accessibles par les utilisateurs. Par conséquent, le personnel de sécurité n’a pas à prendre d’action pour éliminer les menaces en quarantaine. Si les e-mails sont locaux ou externes, l’utilisateur peut être contacté pour répondre à l’e-mail suspect. Ou les administrateurs peuvent utiliser des outils de sécurité/serveur de messagerie distincts pour la suppression. Ces *e-mails* peuvent être identifiés en appliquant l’emplacement de remise = filtre externe local dans l’Explorateur. En cas d’échec ou de suppression d’e-mails, ou d’e-mail non accessible par les utilisateurs, il n’y aura aucun e-mail à atténuer, car ces messages n’atteignent pas la boîte aux lettres.

 
- **Journaux d’action** : affiche les messages corrigés, réussis, ayant échoué, déjà dans la destination.

  L’état peut être :

  - **Démarré** : la correction est déclenchée.
    - **Mis en file d’attente** : la correction est mise en file d’attente pour l’atténuation des e-mails.
    - **En cours** : l’atténuation est en cours.
    - **Terminé** : Atténuation de tous les e-mails remédiables terminés avec succès ou avec certains échecs.
    - **Échec** : aucune correction n’a réussi.

  Étant donné que seuls les e-mails remédiables peuvent être activés, le nettoyage de chaque e-mail s’affiche comme ayant réussi ou échoué. À partir du nombre total d’e-mails remédiables, des atténuations réussies et ayant échoué sont signalées.

  - **Réussite** : l’action souhaitée sur les e-mails remédiables a été effectuée. Par exemple : un administrateur souhaite supprimer les e-mails des boîtes aux lettres, de sorte que l’administrateur prend l’action de supprimer de manière réversible les e-mails. Si un e-mail remédiable est introuvable dans le dossier d’origine une fois l’action effectuée, l’état s’affiche comme ayant réussi.

  - **Échec** : l’action souhaitée sur les e-mails corrigés a échoué. Par exemple : un administrateur souhaite supprimer les e-mails des boîtes aux lettres, de sorte que l’administrateur prend l’action de supprimer de manière réversible les e-mails. Si un e-mail remédiable est toujours trouvé dans la boîte aux lettres une fois l’action effectuée, l’état s’affiche comme ayant échoué.
  
  - **Déjà dans la destination** : l’action souhaitée a déjà été effectuée sur l’e-mail ou l’e-mail existait déjà dans l’emplacement de destination. Par exemple : un e-mail a été supprimé de manière réversible par l’administrateur via l’Explorateur au premier jour. Des e-mails similaires apparaissent alors le jour 2, qui sont à nouveau supprimés de manière réversible par l’administrateur. Lors de la sélection de ces e-mails, l’administrateur finit par sélectionner certains e-mails du premier jour qui sont déjà supprimés de manière réversible. Maintenant, ces e-mails ne seront plus utilisés, ils s’afficheront simplement comme étant « déjà dans la destination », car aucune action n’a été prise sur eux comme ils existaient dans l’emplacement de destination.

  - **Nouveau** : une colonne *Déjà dans la destination* a été ajoutée dans le journal des actions. Cette fonctionnalité utilise l’emplacement de remise le plus récent dans l’Explorateur de menaces pour signaler si le courrier a déjà été corrigé. *Déjà à destination* , les équipes de sécurité comprennent le nombre total de messages qui doivent encore être traités.

Les actions peuvent uniquement être effectuées sur les messages dans les dossiers Boîte de réception, Courrier indésirable, Supprimé et Supprimé de manière réversible de l’Explorateur de menaces. Voici un exemple de fonctionnement de la nouvelle colonne. Une *action de suppression réversible* a lieu sur le message présent dans la boîte de réception, puis le message est géré en fonction des stratégies. La prochaine fois qu’une suppression réversible est effectuée, ce message s’affiche sous la colonne « Déjà dans la destination » indiquant qu’il n’a pas besoin d’être traité à nouveau.

Sélectionnez n’importe quel élément dans le journal des actions pour afficher les détails de la correction. Si les détails indiquent « réussite » ou « introuvable dans la boîte aux lettres », cet élément a déjà été supprimé de la boîte aux lettres. Parfois, il y a une erreur système pendant la correction. Dans ce cas, il est judicieux de réessayer l’action de correction.

En cas de correction de lots importants de courriers électroniques, exportez les messages envoyés à des fins de correction par le biais de l’envoi de courriers et les messages qui ont été corrigés via les journaux d’action. La limite d’exportation est augmentée à 100 000 enregistrements.

 Les administrateurs peuvent effectuer des actions de correction telles que le déplacement des messages électroniques vers le dossier Courrier indésirable, Boîte de réception ou Éléments supprimés et supprimer des actions telles que la suppression réversible ou la suppression définitive des pages De chasse avancée.

:::image type="content" source="../../media/microsoft-365-defender-advanced-hunting-actions-pane.png" alt-text="Panneau Repérage avancé, Prendre des actions avec votre choix d’actions.":::

La correction atténue les menaces, résout les e-mails suspects et permet de sécuriser une organisation.
