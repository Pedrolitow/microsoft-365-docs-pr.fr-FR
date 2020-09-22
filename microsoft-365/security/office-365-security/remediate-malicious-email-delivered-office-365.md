---
title: Correction du courrier électronique malveillant remis dans Office 365
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.service: O365-seccomp
audience: admin
f1.keywords:
- NOCSH
localization_priority: Normal
MS.collection: ''
search.appverid: MET150
description: Correction des menaces
appliesto:
- Microsoft Threat Protection
ms.openlocfilehash: 526a88409514127d4fb484f88632bf3185004854
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48197440"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Correction des courriers électroniques malveillants remis dans Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


La correction consiste à prendre une mesure apposée contre une menace. Les courriers électroniques malveillants envoyés à votre organisation peuvent être nettoyés par le système, via la suppression automatique de zéro heure ou par les équipes de sécurité par le biais d’actions correctives telles que le *déplacement vers la boîte de réception*, le déplacement vers le *courrier indésirable*, le déplacement vers les *éléments supprimés*, la *suppression douce*ou la *Suppression définitive*. Office Advanced Threat Protection (Office ATP) P2/E5 permet aux équipes de sécurité de corriger les menaces dans les fonctionnalités de messagerie et de collaboration via une enquête manuelle et automatisée.

> [!NOTE]
> Pour résoudre les courriers électroniques malveillants, les équipes de sécurité doivent avoir le rôle de *recherche et de purge* affecté. L’attribution de rôle s’effectue par le biais d’autorisations dans le centre de sécurité et de conformité.

## <a name="what-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

Pour effectuer des opérations comme afficher les en-têtes des messages ou télécharger le contenu du courrier électronique, vous devez disposer d’un nouveau rôle appelé *Aperçu* ajouté à un autre groupe de rôles approprié. Le tableau suivant indique les rôles et autorisations requis.

****

|Activité|Groupe de rôles|*Prévisualiser* le rôle nécessaire ?|
|---|---|---|
|Utilisation de l’Explorateur de menaces (et des détections en temps réel) pour analyser les menaces |Administrateur général <br> Administrateur de sécurité <br> Lecteur de sécurité|Non|
|Utiliser l’Explorateur de menaces (et la détection en temps réel) pour afficher des en-têtes de messages électroniques et pour afficher un aperçu et télécharger des messages électroniques mis en quarantaine|Administrateur général <br> Administrateur de sécurité <br>Lecteur de sécurité|Non|
|Utiliser l’Explorateur de menaces pour afficher les en-têtes et télécharger les messages électroniques remis aux boîtes aux lettres|Administrateur général <br>Administrateur de sécurité <br> Lecteur de sécurité <br> Aperçu|Oui|

> [!NOTE]
> La préversion est un *rôle*et non un *groupe de rôles*. Le rôle aperçu doit être ajouté à un groupe de rôles existant pour Office 365. Le *rôle administrateur général* est affecté dans le [centre d’administration 365 de Microsoft](https://admin.microsoft.com). Les rôles Administrateur de sécurité et lecteur de sécurité sont affectés dans les [centres de sécurité et de conformité](https://protection.office.com). Pour en savoir plus sur les rôles et les autorisations, consultez [la rubrique autorisations dans les centres de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> Les administrateurs peuvent effectuer une action obligatoire sur les courriers électroniques, mais pour qu’ils soient approuvés, le rôle de *recherche et de purge* doit leur être attribué via les autorisations du **Centre de sécurité et de conformité**  >  **Permissions**.

## <a name="manual-and-automated-remediation"></a>Correction manuelle et automatique

La *chasse manuelle* survient lorsque les équipes de sécurité identifient les menaces manuellement à l’aide des fonctionnalités de recherche et de filtrage dans l’Explorateur de menaces. Les corrections de messagerie manuelles peuvent être déclenchées via n’importe quelle vue e-mail (*programme malveillant*, *hameçonnage*ou *tout le courrier électronique*) après avoir identifié un ensemble de courriers électroniques à résoudre.

![Chasse manuelle dans Office 365 Threat Explorer par date.](../../media/tp-RemediationArticle1.png)

Les équipes de sécurité peuvent utiliser l’Explorateur de menaces pour sélectionner des messages électroniques de différentes manières :

- Choisir les e-mails manuellement : utilisez des filtres dans différents affichages. Sélectionnez jusqu’à 100 courriers électroniques à corriger.

- Sélection de requête : sélectionnez une requête entière à l’aide du bouton **Sélectionner tout** . La même requête est également affichée dans les détails de l’envoi du message du centre d’action.

- Sélection de requête avec exclusion : parfois, les équipes des opérations de sécurité peuvent souhaiter corriger les courriers électroniques en sélectionnant une requête entière et en excluant manuellement certains messages électroniques de la requête. Pour ce faire, un administrateur peut utiliser la case à cocher **Sélectionner tout** et faire défiler vers le bas pour exclure les e-mails manuellement. La requête peut contenir un maximum de 1 000 courriers électroniques. Le nombre maximal d’exclusions est de 100.

Une fois que vous avez sélectionné les courriers électroniques via l’Explorateur de menaces, vous pouvez démarrer la correction en effectuant une action directe ou en mettant en file d’attente des courriers électroniques pour une action :

- Approbation directe : lorsque les actions telles que *déplacer vers la boîte de réception*, déplacer vers le *courrier indésirable*, *déplacer vers des éléments supprimés*, *supprimer* *définitivement ou supprimer définitivement* sont sélectionnées par le personnel de sécurité disposant des autorisations appropriées et que les étapes suivantes de correction sont suivies, le processus de correction commence à exécuter l’action sélectionnée. Un lanceur temporaire affiche la correction en cours.

- Approbation en deux étapes : une action « Ajouter à la correction » peut être effectuée par les administrateurs qui ne disposent pas des autorisations appropriées ou qui doivent attendre pour exécuter l’action. Dans ce cas, les messages électroniques ciblés sont ajoutés à un conteneur de correction. L’approbation est requise avant l’exécution de la correction.

Les actions d’analyse **et de réponse automatisées** sont déclenchées par des alertes ou par des équipes d’opérations de sécurité à partir de l’Explorateur de menaces. Celles-ci peuvent inclure les actions correctives recommandées qui doivent être approuvées par une équipe des opérations de sécurité. Ces actions sont incluses dans l’onglet **action** de l’enquête automatisée.

![Courrier avec programme malveillant dans la page « zapped » indiquant le moment de l’exécution de l’opération zap.](../../media/tp-RemediationArticle3.png)

Toutes les corrections (approbation directe ou approbation en deux étapes) qui ont été créées dans l’Explorateur de menaces, ainsi que les actions approuvées provenant d’enquêtes automatisées, sont affichées dans le centre de maintenance. Pour accéder à ces éléments via le volet de navigation de gauche, sous **examiner**le  >  **Centre de maintenance**.

![Centre de notifications avec une liste des menaces par date et gravité.](../../media/tp-RemediationArticle4.png)

Le centre de maintenance affiche toutes les actions de correction au cours des 30 derniers jours. Les actions effectuées via l’Explorateur de menaces sont répertoriées par le nom que l’équipe des opérations de sécurité a fournies lors de la correction. Les actions réalisées par le biais d’enquêtes automatisées ont des titres qui commencent par l’alerte associée qui a déclenché l’enquête, par exemple «zap e-mail cluster... ."

Ouvrez un élément de correction pour en afficher les détails, y compris son nom, sa date de création, sa description, la gravité de la menace et son état. Elle présente également les deux onglets suivants.

- Onglet **envoi de courrier** : affiche le nombre de messages envoyés par le biais de l’Explorateur de menaces ou des analyses automatiques à résoudre. Ces e-mails peuvent être exploitables ou non.<br/><br/>![Le centre de notifications avec des menaces actionnables et non exploitables.](../../media/tp-RemediationArticle5.png)

   - **Exploitable**: les courriers électroniques dans les emplacements de boîtes aux lettres Cloud suivants peuvent être traités et déplacés :

     - Boîte de réception
     - Filtre
     - Dossier supprimé
     - Dossier supprimé (récupérable)

     > [!NOTE]
     > Actuellement, seul un utilisateur ayant accès à la boîte aux lettres peut récupérer des éléments à partir d’un dossier supprimé (récupérable).

   - **Non exploitable**: les courriers électroniques aux emplacements suivants ne peuvent pas être traités ou déplacés dans les actions de correction :

     - Quarantaine
     - Dossier supprimé de manière irréversible
     - Local/externe
     - Échec/suppression

   Les messages suspects sont classés comme résolus ou non résolus. Dans la plupart des cas, les messages résolus et non résolus sont égaux à l’ensemble des messages envoyés. Toutefois, dans de rares cas, cela n’est peut-être pas vrai. Cela peut se produire en raison de délais système, de délais d’expiration ou de messages expirés. Les messages expirent en fonction de la période de rétention de l’Explorateur de menaces pour votre organisation.

   À moins que vous ne corrigez les anciens messages après la période de rétention de l’Explorateur de menaces de votre organisation, il est recommandé de relancer la correction des éléments si vous voyez des incohérences de numéros. Pour les retards système, les mises à jour correctives sont généralement actualisées en quelques heures.

   Si la période de rétention de votre organisation pour les courriers électroniques dans l’Explorateur de menaces est de 30 jours et que vous corrigez les courriers électroniques à 29-30 jours, il se peut que les décomptes de dépôt du courrier ne soient pas toujours ajoutés. Il se peut que les messages électroniques commencent à sortir de la période de rétention.

   Si les corrections sont bloquées dans l’État « en cours » pendant un certain temps, cela est probablement dû à des retards système. La correction peut prendre jusqu’à quelques heures. Il se peut que des variantes du nombre d’expéditeurs de messages apparaissent, car certains de ces messages n’ont peut-être pas été inclus dans la requête au début des corrections causées par le système. Il est recommandé d’effectuer une nouvelle tentative de correction dans ce cas.

  >[!Note]
  >Pour obtenir de meilleurs résultats, la correction doit être réalisée par lots de 50 000 ou moins.

   Seuls les courriers électroniques résolus sont traités pendant la correction. Les e-mails non résolus ne peuvent pas être corrigés par le système de courrier Office 365, car ils ne sont pas stockés dans les boîtes aux lettres Cloud.

   Les administrateurs peuvent effectuer des actions sur les courriers électroniques en quarantaine si nécessaire, mais ces messages ne seront pas mis en quarantaine s’ils ne sont pas supprimés manuellement. Les e-mails mis en quarantaine en raison d’un contenu malveillant ne sont pas accessibles par les utilisateurs, de sorte que le personnel de sécurité n’a à effectuer aucune action pour se débarrasser des menaces en quarantaine. Si les messages électroniques sont locaux ou externes, l’utilisateur peut être contacté afin de résoudre le courrier électronique suspect. Les administrateurs peuvent utiliser des outils de serveur/de sécurité distincts pour la suppression. Ces e-mails peuvent être identifiés en appliquant l' *emplacement de remise =* filtre externe local dans l’Explorateur de menaces. Pour les messages électroniques ayant échoué ou supprimés, ou les messages qui ne sont pas accessibles par les utilisateurs, il n’y aura aucun courrier électronique à limiter, étant donné que ces messages n’atteignent pas la boîte aux lettres.

   L’image suivante montre l’apparence d’une soumission dans le centre de notifications. Une correction peut contenir plusieurs envois. Si plusieurs actions sont approuvées via une enquête automatisée, chaque action de messagerie électronique ou de cluster de messagerie apparaît dans la même correction qu’une autre soumission.

   ![ZAP panneau flyout de cluster de messagerie.](../../media/tp-RemediationArticle6.png)

   Sélectionnez un élément de dépôt de courrier pour afficher les détails de cette correction, tels que la requête (lorsque les corrections sont déclenchées via des analyses automatiques ou l’Explorateur de menaces par le biais de la sélection d’une requête), ainsi que les heures de début et de fin de correction. Il affiche également une liste des messages qui ont été envoyés pour correction. Lorsque les messages quittent la période de rétention de l’Explorateur de menaces, les messages disparaissent de cette liste. La liste affiche également les messages individuels résolus.

- **Journaux des actions**: cet onglet affiche les messages corrigés, notamment la date approuvée, l’administrateur qui a approuvé l’action, l’action, le statut et le nombre de comptes.

   L’État peut être :

     - **Démarré**: la correction est déclenchée.
     - En **file d’attente**: la correction est mise en file d’attente pour atténuer les messages électroniques.
     - **En cours**: une atténuation est en cours.
     - **Terminé**: l’atténuation sur tous les e-mails résolus s’est terminée correctement ou avec certains échecs.
     - **Échec**: aucune correction n’a réussi.

   À mesure que seuls des e-mails pouvant être résolus peuvent être traités, le nettoyage de chaque e-mail est indiqué comme réussi ou échec. À partir du total des e-mails résolus, les atténuations réussies et ayant échoué sont signalées.

   - **Opération réussie**: l’action souhaitée sur les courriers électroniques résolus a été effectuée. Par exemple : un administrateur souhaite supprimer les courriers électroniques des boîtes aux lettres, de sorte que l’administrateur prenne l’action de supprimer des courriers électroniques. Si un e-mail résolu est introuvable dans le dossier d’origine une fois l’action effectuée, l’État s’affiche avec succès.

   - **Échec**: l’action souhaitée sur les messages électroniques résolus a échoué. Par exemple : un administrateur souhaite supprimer les courriers électroniques des boîtes aux lettres, de sorte que l’administrateur prenne l’action de supprimer des courriers électroniques. Si un e-mail résolu est toujours trouvé dans la boîte aux lettres une fois l’action effectuée, l’état indique échec.

   Sélectionnez un élément dans le journal des actions pour afficher les détails de la correction. Si les détails indiquent « réussi » ou « introuvable dans la boîte aux lettres », cet élément a déjà été supprimé de la boîte aux lettres. Parfois, il y a une erreur système lors de la correction. Dans ce cas, il est recommandé de relancer la correction.

 La correction est un outil puissant pour atténuer les menaces et résoudre les courriers électroniques suspects. Elle permet de maintenir la sécurité d’une organisation.

