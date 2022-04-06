---
title: Corriger les messages malveillants qui ont été remis dans Office 365
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
ms.openlocfilehash: 3ba8564ef5ecbd261dc47b2f0a48d6d4d77d620a
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64638303"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Corriger les courriers malveillants remis dans Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

La correction signifie prendre une action prescrite contre une menace. Les e-mails malveillants envoyés à votre organisation peuvent être nettoyés par le système, par le biais d’une purge automatique de zéro heure (ZAP) ou par les équipes de sécurité par le biais d’actions de correction telles que le déplacement vers la boîte de *réception, le* déplacement vers le courrier *indésirable, le* déplacement vers les éléments supprimés *, la* suppression possible ou la suppression *définitivement.* Microsoft Defender pour Office 365 Plan 2/E5 permet aux équipes de sécurité de corriger les menaces dans les fonctionnalités de messagerie électronique et de collaboration par le biais d’examens manuels et automatisés.

> [!NOTE]
> Pour corriger les messages malveillants, les équipes de sécurité ont besoin du rôle *Rechercher* et Vider qui leur est attribué. L’attribution de rôle est effectuée [par le biais des autorisations dans Microsoft 365 Defender portail.](permissions-microsoft-365-security-center.md)

## <a name="what-you-need-to-know-before-you-begin"></a>Ce que vous devez savoir avant de commencer

Les administrateurs peuvent effectuer les actions requises sur les e-mails, mais pour obtenir ces actions approuvées, le rôle Recherche et purge doit leur être affecté dans les autorisations de **collaboration** de l'& de messagerie sur le portail Microsoft 365 Defender. Sans le *rôle Rechercher et purger ajouté* à l’un des groupes de rôles, ils ne pourront pas exécuter l’action.

## <a name="manual-and-automated-remediation"></a>Correction manuelle et automatisée

*Le recherche manuel* se produit lorsque les équipes de sécurité identifient les menaces manuellement à l’aide des fonctionnalités de recherche et de filtrage dans l’Explorateur. La correction manuelle du courrier électronique peut être déclenchée par n’importe quel affichage de *courrier électronique (**programmes malveillants*, hameçonnage ou *tous les* e-mails) une fois que vous avez identifié un ensemble d’e-mails qui doivent être corrigés.

> [!div class="mx-imgBorder"]
> [![Capture d’écran du hunting manuel dans Office 365'Explorateur de menaces par date.](../../media/tp-RemediationArticle1.png)](../../media/tp-RemediationArticle1.png#lightbox)

Les équipes de sécurité peuvent utiliser l’Explorateur pour sélectionner des e-mails de plusieurs manières :

- Sélectionnez les e-mails à la main : utilisez des filtres dans différents affichages. Sélectionnez jusqu’à 100 e-mails à corriger.

- Sélection de requête : sélectionnez une requête entière à l’aide du bouton **Tout sélectionner en** haut. La même requête est également affichée dans les détails de l’envoi de courrier du centre de messages. Les clients peuvent envoyer un maximum de 200 000 e-mails à partir de l’Explorateur de menaces.  

- Sélection de requête avec exclusion : parfois, les équipes en charge des opérations de sécurité peuvent vouloir corriger les messages électroniques en sélectionnant une requête entière et en excluant manuellement certains e-mails de la requête. Pour ce faire, un administrateur peut utiliser la  case à cocher Sélectionner tout et faire défiler vers le bas pour exclure manuellement les e-mails. La requête peut contenir un maximum de 1 000 e-mails. Le nombre maximal d’exclusions est de 100.

Une fois que les e-mails sont sélectionnés par le biais de l’Explorateur, vous pouvez commencer la correction en prenant des mesures directes ou en les interrogeant pour une action :

- Approbation directe : lorsque des actions telles que le déplacement vers la  boîte de *réception, le* déplacement vers le courrier *indésirable, le* déplacement vers les éléments supprimés *, la* suppression définitive ou la suppression définitive sont sélectionnées par le personnel de sécurité qui a les autorisations appropriées et que les étapes suivantes de la correction sont suivies, le processus de correction commence à exécuter l’action sélectionnée.
> [!NOTE]
>Au lancement de la correction, une alerte et un examen sont générés en parallèle. L’alerte s’affiche dans la file d’attente des alertes sous le nom « Action administrative envoyée par un administrateur », ce qui suggère que le personnel de sécurité a pris l’action de correction d’une entité. Il présente des détails tels que le nom de la personne qui a effectué l’action, le lien d’examen de prise en charge, l’heure, etc. Il fonctionne vraiment bien de savoir chaque fois qu’une action de nettoyage telle que la correction est effectuée sur des entités. Toutes ces actions peuvent être trcaked sous **l’onglet Actions &** **Centre**  ->  de **soumissionsHistory** \> (prévisualisation publique).

- Approbation en deux étapes : une action d’ajout à la correction peut être prise par les administrateurs qui ne sont pas autorisés à exécuter l’action ou qui doivent attendre. Dans ce cas, les e-mails ciblés sont ajoutés à un conteneur de correction. Une approbation est nécessaire avant l’exécution de la correction.

**Les actions d’investigation et de** réponse automatisées sont déclenchées par des alertes ou par des équipes d’opérations de sécurité de l’Explorateur. Il peut s’agir d’actions de correction recommandées qui doivent être approuvées par une équipe des opérations de sécurité. Ces actions sont incluses sous **l’onglet Action** dans l’examen automatisé.

> [!div class="mx-imgBorder"]
> [![Courrier électronique avec programme malveillant dans la page « Péred » montrant l’heure de l’exécution de Zap.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Toutes les corrections (approbations directes) créées dans l’Explorateur, le recherche avancée ou par le biais d’un examen automatisé sont affichées dans le Centre de gestion des actions. Accédez à ces éléments via le panneau de navigation gauche sous **l’onglet Actions &** **Centre de**  ->  **soumissionsHistory**\>.

Toutes les corrections (approbations directes) qui ont été créées dans l’Explorateur ou le recherche avancée ou par le biais d’un examen automatisé sont affichées dans le Centre de gestion des actions. Accédez à ces éléments via le panneau de navigation gauche sous **l’onglet Actions &** **Centre de**  ->  **soumissionsHistory**\>. 

Actions manuelles en attente d’approbation à l’aide du processus d’approbation en deux étapes (1. ajouter à la correction par un membre de l’équipe d’opération de sécurité, 2. examinées et approuvées par un autre membre de l’équipe d’opérations de sécurité) sont visibles uniquement dans le centre de contrôle de l’action Defender pour Office 365  \> hérité et non dans les incidents/enquêtes et le centre de l’action unifiée.

> [!NOTE]
> Approbation en deux étapes : actions disponibles uniquement dans le centre de  contrôle de l’action \> **Office**

:::image type="content" source="../../media/microsoft-365-defender-action-center-history.png" alt-text="Le centre de mise en œuvre unifié affiche 30 jours d’actions de correction.":::

Le centre de mise en œuvre unifié affiche les actions de correction pour les 30 derniers jours. Les actions entreprises par le biais de l’Explorateur sont répertoriées par le nom fourni par l’équipe des opérations de sécurité lors de la création de la correction, ainsi que par l’ID d’approbation, ID d’examen. Les actions entreprises via des enquêtes automatisées ont des titres qui commencent par l’alerte associée qui a déclenché l’enquête, telle que le cluster de messagerie *Zap*.

Ouvrez n’importe quel élément de correction pour afficher les détails à son sujet, notamment son nom de correction, son ID d’approbation, l’ID d’examen, la date de création, la description, l’état, la source de l’action, le type d’action, décidé par, état. Il ouvre également un volet latéral avec les détails de l’action, les détails du cluster de messagerie, l’alerte et les détails de l’incident.

- *Ouvrir la page Examen* ouvre une investigation d’administration qui contient moins de détails et d’onglets. Il affiche des détails tels que : alerte associée, entité sélectionnée pour la correction, action entreprise, état de la correction, nombre d’entités, journaux, approbation de l’action. Cette enquête assure le suivi de l’examen effectué manuellement par l’administrateur et contient des détails sur les sélections réalisées par l’administrateur. Par conséquent, il s’agit de l’examen d’action de l’administrateur. Il n’est pas nécessaire d’agir sur l’examen et d’alerter son état déjà approuvé.   
- *Nombre d’e-mails* Affiche le nombre d’e-mails envoyés via l’Explorateur de menaces. Ces e-mails peuvent être actionnables ou ne peuvent pas être actionnables. 
- *Journaux d’action* Affiche les détails de l’état de correction comme réussite/échec/ déjà dans la destination

  > [!div class="mx-imgBorder"]
  > [![Capture d’écran du centre de actions avec des menaces actionnables et non actionnables.](../../media/tp-RemediationArticle5.png)](../../media/tp-RemediationArticle5.png#lightbox)

  - **Actionnable :** les e-mails des emplacements de boîtes aux lettres cloud suivants peuvent être actionnables et déplacés :
    - Boîte de réception
    - Courrier indésirable
    - Dossier supprimé
    - Dossier supprimé (supprimé(s) (supprimé(s) (supprimé(s)

      > [!NOTE]
      > Actuellement, seul un utilisateur ayant accès à la boîte aux lettres peut récupérer des éléments à partir d’un dossier supprimé (récupérable).

  - **Non actionnable** : les messages électroniques aux emplacements suivants ne peuvent pas être actionnables ou déplacés dans les actions de correction :
    - Quarantaine
    - Dossier supprimé définitivement
    - Local/externe
    - Échec/abandon

  Les messages suspects sont classés comme étant soit remédiables, soit non immédiates. Dans la plupart des cas, les messages remédiables et les messages non immédiatement remédiables sont égaux au nombre total de messages envoyés. Mais dans de rares cas, cela peut ne pas être vrai. Cela peut se produire en raison de retards système, de délais d’expiration ou de messages expirés. Les messages expirent en fonction de la période de rétention de l’Explorateur pour votre organisation.

  Sauf si vous remédiez aux anciens messages après la période de rétention de l’Explorateur de votre organisation, il est conseillé de réessayer de corriger les éléments en cas d’incohérence de nombre. Pour les retards du système, les mises à jour de correction sont généralement actualisées en quelques heures.

  Si la période de rétention du courrier électronique de votre organisation dans l’Explorateur est de 30 jours et que vous remédiez aux messages électroniques de 29 à 30 jours, il se peut que le nombre d’envois de courriers ne s’ajoute pas toujours. Les e-mails ont peut-être déjà commencé à sortir de la période de rétention.

  Si les corrections sont bloquées à l’état « En cours » pendant un certain temps, cela est probablement dû à des retards du système. La correction peut prendre jusqu’à quelques heures. Vous pouvez voir des variations dans le nombre d’envois de courrier, car certains messages électroniques n’ont peut-être pas été inclus dans la requête au début de la correction en raison de retards du système. Il est bon de réessayer d’y remédier.

  > [!NOTE]
  > Pour de meilleurs résultats, la correction doit être effectuée par lots de 50 000 ou moins.

  Seuls les e-mails remédiables sont actionn s pendant la correction. Les messages électroniques non instantanés ne peuvent pas être corrigés par le système de messagerie Office 365, car ils ne sont pas stockés dans des boîtes aux lettres cloud.

  Les administrateurs peuvent prendre des mesures sur les e-mails mis en quarantaine si nécessaire, mais ils expireront hors de la quarantaine s’ils ne sont pas purgés manuellement. Par défaut, les e-mails mis en quarantaine en raison de contenus malveillants ne sont pas accessibles par les utilisateurs, de sorte que le personnel de sécurité n’a aucune action à prendre pour se débarrasser des menaces en quarantaine. Si les e-mails sont locaux ou externes, l’utilisateur peut être contacté pour traiter le message suspect. Les administrateurs peuvent également utiliser des outils de sécurité/serveur de messagerie distincts pour la suppression. Ces *e-mails* peuvent être identifiés en appliquant l’emplacement de remise = filtre externe sur site dans l’Explorateur. En cas d’échec ou de abandon du courrier électronique ou de courrier non accessible par les utilisateurs, il n’y aura aucun message électronique à atténuer, car ces messages n’atteignent pas la boîte aux lettres.

 
- **Journaux d’action** : affiche les messages corrigés, réussis, échoués, déjà à destination.

  L’état peut être :

  - **Démarré :** la correction est déclenchée.
    - **Mise en file d’attente** : la correction est mise en file d’attente pour l’atténuation des messages électroniques.
    - **En cours :** l’atténuation est en cours.
    - **Terminé :** l’atténuation sur tous les e-mails remédiables s’est terminée correctement ou avec certains échecs.
    - **Échec :** aucune correction n’a réussi.

  Comme seuls les e-mails remédiables peuvent être pris en compte, le nettoyage de chaque e-mail s’affiche comme réussi ou a échoué. À partir du nombre total d’e-mails remédiables, les atténuations réussies et échouées sont signalées.

  - **Réussite :** l’action souhaitée sur les e-mails corrects a été accomplie. Par exemple : un administrateur souhaite supprimer des courriers électroniques des boîtes aux lettres, afin qu’il prenne l’action de supprimer les e-mails de la sorte. Si un e-mail remédiable n’est pas trouvé dans le dossier d’origine une fois l’action entreprise, l’état s’affiche comme réussi.

  - **Échec :** échec de l’action souhaitée sur les e-mails corrects. Par exemple : un administrateur souhaite supprimer des courriers électroniques des boîtes aux lettres, afin qu’il prenne l’action de supprimer les e-mails de la sorte. Si un e-mail remédiable est toujours trouvé dans la boîte aux lettres après l’action, l’état s’affiche comme étant un échec.
  
  - **Déjà dans la destination** : l’action souhaitée a déjà été prise sur l’e-mail ou l’e-mail existait déjà dans l’emplacement de destination. Par exemple : un e-mail a été supprimé (à la demande) par l’administrateur via l’Explorateur le premier jour. Ensuite, des messages électroniques similaires s’afficheront le jour 2, qui seront supprimés de nouveau de façon souple par l’administrateur. Lors de la sélection de ces e-mails, l’administrateur finit par sélectionner certains messages électroniques du premier jour qui sont déjà supprimés (supprimés de la sorte). À présent, ces e-mails ne seront pas retentés, ils s’afficheront simplement comme « déjà dans la destination », car aucune action n’a été prise sur eux comme ils existaient dans l’emplacement de destination.

  - **Nouveau** : une *colonne déjà dans la destination* a été ajoutée dans le journal des actions. Cette fonctionnalité utilise le dernier emplacement de remise dans l’Explorateur de menaces pour signaler si le courrier a déjà été corrigé. *La destination déjà en cours* permettra aux équipes de sécurité de comprendre le nombre total de messages qui doivent encore être traités.

Les actions peuvent uniquement être prises sur les messages dans les dossiers Boîte de réception, Courrier indésirable, Supprimé et Supprimé (suppression possible) de l’Explorateur de menaces. Voici un exemple de fonctionnement de la nouvelle colonne. Une *action de suppression souple* a lieu sur le message présent dans la boîte de réception, puis le message est géré conformément aux stratégies. Lors de la prochaine suppression, ce message s’affichera sous la colonne « Déjà dans la destination » signalant qu’il n’est pas nécessaire de le traiter à nouveau.

Sélectionnez n’importe quel élément dans le journal des actions pour afficher les détails de correction. Si les détails indiquent « réussite » ou « in trouvé dans la boîte aux lettres », cet élément a déjà été supprimé de la boîte aux lettres. Parfois, il y a une erreur système lors de la correction. Dans ce cas, il est bon de réessayer l’action de correction.

En cas de correction de lots importants de courriers électroniques, exportez les messages envoyés pour correction via l’envoi du courrier, ainsi que les messages corrigés via les journaux d’action. La limite d’exportation est augmentée à 100 000 enregistrements.

 Les administrateurs peuvent prendre des mesures correctives, telles que le déplacement de messages électroniques vers le dossier Courrier indésirable, Boîte de réception ou Éléments supprimés, et supprimer des actions telles que la suppression (ou suppression possible) des pages de recherche avancée.

:::image type="content" source="../../media/microsoft-365-defender-advanced-hunting-actions-pane.png" alt-text="Panneau Actions de recherche avancée avec votre choix d’actions.":::

La correction permet d’atténuer les menaces, de répondre aux messages électroniques suspects et de sécuriser une organisation.
