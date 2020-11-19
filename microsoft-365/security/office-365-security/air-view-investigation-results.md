---
title: Afficher les résultats d’une enquête automatisée dans Microsoft 365
keywords: AIR, autoIR, ATP, automatisation, analyse, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Pendant et après une enquête automatisée dans Microsoft 365, vous pouvez afficher les résultats et les résultats clés.
ms.date: 11/05/2020
ms.openlocfilehash: 4dc74987619c3f958c874927af6e4240b9d7e154
ms.sourcegitcommit: 474bd6a86c3692d11fb2c454591c89029ac5bbd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49357284"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Détails et résultats d’une enquête automatisée dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Lorsqu’une [enquête automatisée](office-365-air.md) se produit dans [Microsoft defender pour Office 365](office-365-atp.md), des informations détaillées sur cette enquête sont disponibles pendant et après le processus d’enquête automatisé. Si vous disposez des autorisations nécessaires, vous pouvez consulter ces détails dans le centre de sécurité Microsoft 365. Les détails de l’enquête vous fournissent un statut à jour et la possibilité d’approuver les actions en attente.

## <a name="investigation-status"></a>État de l’enquête

L’état d’enquête indique la progression de l’analyse et des actions. Lors de l’exécution de l’enquête, les États changent pour indiquer si des menaces ont été détectées et si des actions ont été approuvées.

|Statut|Description|
|---|---|
|**Démarrage**|L’enquête a été déclenchée et attend de démarrer.|
|**En cours d’exécution**|Le processus d’enquête a commencé et est en cours d’exécution. Cet État se produit également lorsque les [actions en attente](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) sont approuvées.|
|**Aucune menace détectée**|L’enquête est terminée et aucune menace (compte d’utilisateur, message électronique, URL ou fichier) n’a été identifiée. <p> **Conseil**: Si vous pensez qu’un événement a été manqué (par exemple, un faux négatif), vous pouvez prendre une mesure à l’aide de l' [Explorateur de menaces](threat-explorer.md).|
|**Menaces détectées**|L’enquête automatisée a détecté des problèmes, mais il n’existe aucune action de correction spécifique pour résoudre ces problèmes. <p> L’état **menaces détectées** peut se produire lorsqu’un type d’activité utilisateur a été identifié mais qu’aucune action de nettoyage n’est disponible. Voici quelques exemples d’activités utilisateur : <ul><li>Un événement de [protection contre la perte de données](https://docs.microsoft.com/Microsoft-365/compliance/data-loss-prevention-policies) (DLP)</li><li>Envoi d’une anomalie par courrier électronique</li><li>Programmes malveillants envoyés</li><li>Hameçonnage envoyé</li></ul> <p> L’enquête n’a trouvé aucune URL, aucun fichier ou message électronique malveillant à corriger, ni aucune activité de boîte aux lettres à corriger, telle que la désactivation des règles de transfert ou la délégation. <p> **Conseil**: Si vous pensez qu’un événement a été manqué (par exemple, un faux négatif), vous pouvez examiner et prendre des mesures à l’aide de l' [Explorateur de menaces](threat-explorer.md).|
|**Terminé par le système**|L’enquête s’est arrêtée. Une enquête peut s’arrêter pour plusieurs raisons : <ul><li>Les actions en attente de l’enquête ont expiré. Délai d’expiration des actions en attente après approbation d’une semaine.</li><li>Il y a trop d’actions. Par exemple, si un trop grand nombre d’utilisateurs cliquent sur des URL malveillantes, il peut dépasser la capacité de l’enquête à exécuter tous les analyseurs, de sorte que l’enquête s’arrête.</li></ul> <p> **Conseil**: si une enquête s’arrête avant que des actions ne soient prises, essayez d’utiliser l' [Explorateur de menaces](threat-explorer.md) pour trouver et résoudre les menaces.|
|**Action en attente**|L’enquête a détecté une menace, telle qu’un e-mail malveillant, une URL malveillante ou un paramètre de boîte aux lettres à risque, et une action visant à corriger cette menace est en [attente d’approbation](air-review-approve-pending-completed-actions.md). <p> L’état de l' **action en attente** est déclenché lorsqu’une menace avec une action correspondante est trouvée. Toutefois, la liste des actions en attente peut augmenter à mesure qu’une enquête s’exécute. Consultez le [Journal d’enquête](#playbook-log) pour voir si d’autres éléments sont toujours en attente de réalisation.|
|**Corrigé**|L’enquête s’est terminée et toutes les actions de correction ont été approuvées (ce problème est signalé comme étant entièrement résolu). <p> **Remarque**: les actions de correction approuvées peuvent comporter des erreurs qui empêchent le suivi des actions. Que les actions de correction soient exécutées avec succès ou non, l’état de l’enquête ne change pas. Pour obtenir des résultats détaillés, consultez le [Journal d’enquête](#playbook-log) .|
|**Partiellement résolu**|L’enquête a entraîné des actions de correction, et certaines ont été approuvées et terminées. D’autres actions sont toujours [en attente](air-review-approve-pending-completed-actions.md).|
|**Échec**|Au moins un analyseur d’enquête a rencontré un problème où il n’a pas pu se terminer correctement. <p> **Remarque**: si une enquête échoue après l’approbation des actions correctives, les actions correctives ont pu encore aboutir. Pour obtenir des résultats détaillés, consultez le [Journal d’enquête](#playbook-log) .|
|**Mise en file d’attente par limitation**|Une enquête est placée dans une file d’attente. Lorsque d’autres enquêtes sont terminées, les recherches en attente commencent. La limitation permet d’éviter les performances de service médiocres.  <p> **Conseil**: les actions en attente permettent de limiter le nombre de nouvelles enquêtes pouvant être exécutées. Veillez à [approuver (ou refuser) les actions en attente](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions).|
|**Interruption par la limitation**|Si une enquête est conservée dans la file d’attente trop longtemps, elle s’arrête. <p> **Conseil**: vous pouvez [Démarrer une enquête à partir de l’Explorateur de menaces](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|
|

## <a name="view-details-of-an-investigation"></a>Afficher les détails d’une enquête

1. Accédez au centre de sécurité & conformité ( [https://protection.office.com](https://protection.office.com) ) et connectez-vous.

2. Effectuez l’une des opérations suivantes :

    - Accédez au tableau de bord **gestion des menaces** \> **Dashboard**. Cela vous amène au [tableau de bord de sécurité](security-dashboard.md). Vos widgets d’AIR s’affichent dans la partie supérieure du [tableau de bord de sécurité](security-dashboard.md). Sélectionnez un widget, par exemple, **Résumé des enquêtes**.

    - Accédez aux enquêtes de **gestion des menaces** \> **Investigations**.

    L’une ou l’autre de ces méthodes vous permet d’accéder à une liste d’investigations.

    ![Page d’enquête principale pour l’AIR](../../media/air-maininvestigationpage.png)

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** . Cette action ouvre la page des détails de l’enquête, en commençant par le graphique d’enquête dans l’affichage.

    ![Page graphique d’enquête sur l’AIR](../../media/air-investigationgraphpage.png)

   Utilisez les différents onglets pour en savoir plus sur l’enquête.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Afficher les détails d’une alerte liée à une enquête

Certains types d’alertes déclenchent une enquête automatisée dans Microsoft 365. Pour plus d’informations, consultez la rubrique [Alert Policies that Trigger Automated investigations](office-365-air.md#which-alert-policies-trigger-automated-investigations).

Utilisez la procédure suivante pour afficher les détails d’une alerte associée à une enquête automatisée.

1. Accédez au centre de sécurité & conformité ( [https://protection.office.com](https://protection.office.com) ) et connectez-vous.

2. Accédez aux enquêtes de **gestion des menaces** \> **Investigations**.

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** .

4. Les détails d’une enquête étant ouverts, sélectionnez l’onglet **alertes** . Les alertes qui ont déclenché l’enquête sont répertoriées ici.

5. Sélectionnez un élément dans la liste. Un menu volant s’ouvre, avec des détails sur l’alerte et des liens vers des informations et des actions supplémentaires.

6. Passez en revue les informations de la fenêtre mobile et, en fonction de l’alerte en particulier, effectuez une action, telle que **résoudre**, **supprimer** ou **avertir les utilisateurs**.

    - La **résolution** équivaut à la fermeture d’une alerte

    - La **suppression** entraîne le déclenchement d’alertes par une stratégie pendant une période de temps spécifiée.

    - **Avertir les utilisateurs** de l’envoi d’un courrier électronique avec les adresses de messagerie des utilisateurs déjà entrées, et permet à l’équipe des opérations de sécurité de taper un message pour ces utilisateurs. (Ceci est similaire à l’envoi d’un message à des destinataires à l’aide de l' [Explorateur de menaces](threat-explorer.md).)

## <a name="how-to-use-the-various-tabs"></a>Utilisation des différents onglets

Les sections suivantes décrivent les différents onglets de la page enquêtes automatisées et la façon dont vous pouvez utiliser ces informations.

### <a name="automated-investigations-page"></a>Page enquêtes automatisées

La page enquêtes automatiques indique les évaluations de votre organisation et leurs États actuels.

![Page d’enquête principale pour l’AIR](../../media/air-maininvestigationpage.png)

Vous pouvez :

- Accédez directement à une enquête (sélectionnez un **ID d’enquête**).

- Appliquer des filtres. Choisissez entre **type** d’enquête **, période**, **État** ou une combinaison de ces éléments.

- Exportez les données dans un fichier. csv.

### <a name="investigation-graph"></a>Graphique de l'examen

Lorsque vous ouvrez une enquête spécifique, vous voyez la page Graph de l’enquête. Cette page affiche toutes les entités différentes : les messages électroniques, les utilisateurs (ainsi que leurs activités) et les appareils qui ont été automatiquement analysés dans le cadre de l’alerte déclenchée.

![Page graphique d’enquête sur l’AIR](../../media/air-investigationgraphpage.png)

Vous pouvez :

- Obtenir une vue d’ensemble visuelle de l’enquête actuelle.
- Afficher un résumé de la durée de l’enquête.
- Sélectionnez un nœud dans la visualisation pour afficher les détails de ce nœud.
- Sélectionnez un onglet dans la partie supérieure pour afficher les détails de cet onglet.

### <a name="alert-investigation"></a>Enquête sur les alertes

Dans l’onglet **alertes** pour une enquête, vous pouvez voir des alertes relatives à l’enquête. Les détails incluent l’alerte qui a déclenché l’enquête et d’autres alertes corrélées, telles que la connexion à risque, les violations de [stratégie DLP](https://docs.microsoft.com/Microsoft-365/compliance/data-loss-prevention-policies) , etc., qui sont corrélées à l’enquête. À partir de cette page, un analyste de sécurité peut également afficher des détails supplémentaires sur des alertes individuelles.

![Page alertes AÉRIENNEs](../../media/air-investigationalertspage.png)

Vous pouvez :

- Obtenir une vue d’ensemble visuelle de l’alerte de déclenchement actuelle et de toutes les alertes associées.
- Sélectionnez une alerte dans la liste pour ouvrir une page de survol qui affiche les détails de l’alerte complète.

### <a name="email-investigation"></a>Enquête par courrier électronique

Dans l’onglet **e-mail** pour une enquête, vous pouvez voir les courriers électroniques d’origine et les clusters de messages similaires identifiés dans le cadre de l’enquête. L’onglet **courrier** électronique affiche également les éléments de courrier liés à l’enquête, tels que les détails du message électronique, le courrier électronique d’origine signalé, le ou les messages électroniques zapped en raison de programmes malveillants/hameçons, etc.

![Page d’enquête sur le courrier électronique aérien](../../media/air-investigationemailpage.png)

À l’aide de l’enquête par courrier électronique, vous pouvez :

- Obtenir une vue d’ensemble visuelle des résultats de clustering actuels et des menaces détectées.
- Cliquez sur une entité de cluster ou une liste de menaces pour ouvrir une page de survol qui affiche les détails de l’alerte complète.
- Pour approfondir le cluster de messagerie, cliquez sur le lien **ouvrir dans l’Explorateur** en haut de l’onglet **Détails du cluster de messagerie** .

![Courrier électronique d’enquête aérienne avec détails du menu volant](../../media/air-investigationemailpageflyoutdetails.png)

Étant donné le volume de courrier électronique que les utilisateurs d’une organisation envoient et reçoivent, ainsi que la nature multi-utilisateur des communications et des attaques de messagerie, le processus suivant peut prendre un certain temps :

1. Mise en cluster des messages électroniques en fonction d’attributs similaires provenant d’un en-tête, d’un corps, d’une URL et de pièces jointes.
2. Séparation du courrier électronique malveillant du courrier électronique.
3. Prendre des mesures sur les messages électroniques malveillants.

AIR automatise ce processus en enregistrant le temps et les efforts de l’équipe de sécurité de votre organisation.

#### <a name="types-of-email-clusters"></a>Types de clusters de messagerie

Trois types de clusters de messagerie différents peuvent être identifiés lors de l’analyse du courrier : les clusters de similarité (toutes les enquêtes), les clusters d’indicateurs (toutes les enquêtes) et les clusters de boîtes aux lettres/utilisateurs. Le tableau suivant décrit ces types de clusters de messagerie.

|Cluster de messagerie|Description|
|---|---|
|Clusters de similarité|Messages électroniques identifiés par la chasse aux messages électroniques avec des attributs d’expéditeur et de contenu similaires. Ces clusters sont évalués pour le contenu malveillant en fonction des résultats de la détection d’origine. Les clusters de messagerie qui contiennent suffisamment de détections de courriers électroniques malveillants sont considérés comme malveillants.|
|Clusters d’indicateurs|Messages électroniques identifiés par la chasse à la même entité d’indicateur (hachage de fichier ou URL) à partir du message d’origine. Lorsque l’entité fichier/URL d’origine est identifiée comme malveillante, AIR applique le verdict de l’indicateur à l’ensemble du cluster de messages contenant cette entité. Un fichier identifié comme un programme malveillant signifie que le cluster de messages électroniques contenant ce fichier est traité comme un message électronique de programme malveillant.|
|Boîtes aux lettres/clusters d’utilisateurs|Messages électroniques liés à l’utilisateur impliqué dans une enquête de compromission d’un utilisateur. Ces clusters de messagerie sont destinés à une analyse plus poussée par l’équipe des opérations de sécurité et ne génèrent pas d’actions de correction de messagerie. <p> Les manifestes de sécurité de l’utilisateur compromis examinent les e-mails envoyés par l’utilisateur en cours d’analyse afin de comprendre l’impact potentiel des messages envoyés à partir de la boîte aux lettres.|

> [!NOTE]
> L’objectif du clustering est de rechercher d’autres messages électroniques associés envoyés par le même expéditeur dans le cadre d’une attaque ou d’une campagne.  Dans certains cas, les messages légitimes peuvent déclencher une enquête (par exemple, un utilisateur signale un courrier électronique marketing).  Dans ces scénarios, le clustering de messagerie doit identifier les clusters de messagerie qui ne sont pas malveillants : lorsqu’il le fait de manière appropriée, il n’indique pas de menace et ne recommande **pas** la suppression des messages.

#### <a name="email-classifications"></a>Classifications de courrier électronique

À mesure que les messages électroniques sont analysés, ils sont classés comme *malveillants*, *suspects* ou *propres* (comme dans, *non identifiés comme une menace*) :

- Les *courriers électroniques malveillants* envoyés à partir de la boîte aux lettres/utilisateur indiquent une compromission potentielle de la boîte aux lettres/du compte. Les autres utilisateurs/boîtes aux lettres susceptibles d’avoir un impact sur un courrier malveillant dans le cadre d’un compromis sont affichés.

- Les *E-mails suspects* envoyés par la boîte aux lettres/l’utilisateur indiquent le potentiel pour un compte compromis ou une activité de courrier indésirable. Ces messages incluent tout courrier indésirable/courrier électronique envoyé à partir de la boîte aux lettres.

- Les *messages électroniques nettoyés* (les e-mails considérés comme n’étant pas une menace) envoyés par la boîte aux lettres ou l’utilisateur peuvent fournir à votre équipe des opérations de sécurité un aperçu des courriers électroniques utilisateur légitimes envoyés. Toutefois, ces messages peuvent également inclure l’exfiltration des données si le compte de messagerie est compromis.

#### <a name="more-about-email-counts"></a>En savoir plus sur le nombre de messages

Le nombre de messages identifiés dans l’onglet e-mail représente actuellement la somme totale de tous les messages électroniques affichés dans l’onglet **e-mail** . Étant donné que les messages électroniques sont présents dans plusieurs clusters, le nombre total réel de messages électroniques identifiés (et affectés par les actions de correction) est le nombre de messages électroniques uniques présents sur tous les clusters et les messages électroniques des destinataires d’origine.

L' [Explorateur](threat-explorer.md) et l’air comptent tous les deux par destinataire, car les verdicts de sécurité, les actions et les emplacements de remise varient selon les destinataires. Ainsi, un message électronique d’origine envoyé à trois utilisateurs compte au total trois messages électroniques au lieu d’un seul.

Dans certains cas, un message électronique est compté deux ou plusieurs fois, par exemple lorsqu’un courrier électronique comporte plusieurs actions, ou lorsqu’il y a plusieurs copies de l’e-mail lorsque toutes les actions se produisent.

Par exemple, un courrier indésirable détecté lors de la remise peut entraîner l’envoi d’un message électronique bloqué (mis en quarantaine) et d’un message électronique remplacé (fichier de menace remplacé par un fichier d’avertissement, puis remis à la boîte aux lettres de l’utilisateur). Étant donné qu’il y a littéralement deux copies du courrier électronique dans le système, les deux peuvent être comptés dans le compte du cluster.

> [!IMPORTANT]
> Voici quelques points à garder à l’esprit :
>
> - Le nombre de messages est calculé lors de l’enquête, et certains comptes sont recalculés lorsque vous ouvrez des lanceurs d’investigation (sur la base d’une requête sous-jacente).
>
> - Le nombre de messages affichés pour les clusters de courrier électronique sous l’onglet **e-mail** et la valeur de quantité de courrier électronique affichée dans la fenêtre mobile du cluster sont calculés au moment de l’enquête et ne changent pas.
>
> - Le nombre de courriers électroniques affiché en bas de l’onglet **e-mail** de la fenêtre mobile du cluster de messagerie et le nombre de messages électroniques affichés dans l’Explorateur reflètent les messages électroniques reçus après l’analyse initiale de l’enquête.

Ainsi, un cluster de messagerie qui affiche une quantité initiale de 10 messages électroniques affiche une liste de courriers au total 15 lorsque cinq autres messages électroniques arrivent entre la phase d’analyse de l’enquête et lorsque l’administrateur révise l’enquête. De la même manière, les anciennes enquêtes peuvent présenter un nombre plus élevé que les requêtes Explorer, car les données de Microsoft Defender pour Office 365 plan 2 expirent après 7 jours pour les versions d’évaluation et après 30 jours pour les licences payantes.

L’affichage des compteurs historique et actuel dans différentes vues permet d’indiquer l’impact du courrier électronique au moment de l’examen et l’impact actuel jusqu’à l’exécution de la correction.

> [!NOTE]
> Dans le contexte de la messagerie électronique, vous pouvez voir une surface d’anomalie de volume dans le cadre de l’enquête. Une anomalie de volume indique un pic dans les messages électroniques similaires de la durée de l’événement d’enquête par rapport aux délais précédents. Ce pic dans le trafic de messagerie avec des caractéristiques similaires (par exemple, domaine d’objet et de l’expéditeur, similitude entre le corps et IP de l’expéditeur) est typique du début des campagnes ou des attaques par courrier électronique.
> Toutefois, les campagnes de courrier électronique, de courrier indésirable et légitimes partagent généralement ces caractéristiques.
>
> Les anomalies de volume représentent une menace potentielle et peuvent donc être moins sévères par rapport aux menaces de programmes malveillants ou hameçons identifiées à l’aide de moteurs antivirus, de détonation ou de réputation malveillante.

### <a name="user-investigation"></a>Enquête utilisateur

Sous l’onglet **utilisateurs** , vous pouvez voir tous les utilisateurs identifiés dans le cadre de l’enquête. Les comptes d’utilisateur apparaissent dans l’enquête lorsqu’il existe un événement ou une indication que ces comptes d’utilisateur peuvent être affectés ou compromis.

Par exemple, dans l’image suivante, AIR a identifié des indicateurs de compromission et des anomalies en fonction d’une nouvelle règle de boîte de réception créée. Des détails supplémentaires (preuve) de l’enquête sont disponibles par le biais d’affichages détaillés au sein de cet onglet. Des indicateurs de compromis et des anomalies peuvent également inclure des détections d’anomalies à partir de la [sécurité des applications Cloud de Microsoft](https://docs.microsoft.com/cloud-app-security).

![Page des utilisateurs de l’enquête aérienne](../../media/air-investigationuserspage.png)

Vous pouvez :

- Obtenir une vue d’ensemble visuelle des résultats et des risques utilisateur identifiés.

- Sélectionnez un utilisateur pour ouvrir une page de survol qui affiche les détails de l’alerte complète.

### <a name="machine-investigation"></a>Enquête sur les machines

Sous l’onglet **ordinateurs** , vous pouvez voir tous les ordinateurs identifiés dans le cadre de l’enquête.

![Page de l’ordinateur d’enquête aérien](../../media/air-investigationmachinepage.png)

Dans certains cas, AIR corrèle les menaces de messagerie aux appareils (par exemple, les programmes malveillants zapped). Par exemple, une enquête transmet un hachage de fichier malveillant à [Microsoft Defender pour](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection
) que le point de terminaison effectue une enquête. Cela permet l’analyse automatisée des ordinateurs pertinents pour vos utilisateurs, afin de garantir que les menaces sont résolues à la fois dans le nuage et sur vos points de terminaison.

Vous pouvez :

- Obtenir une vue d’ensemble visuelle des ordinateurs et menaces actuels détectés.

- Sélectionnez un ordinateur pour ouvrir une vue dans le centre de sécurité Microsoft Defender [pour les enquêtes de point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) dans le centre de sécurité Microsoft Defender.

### <a name="entity-investigation"></a>Enquête d’entité

Sous l’onglet **entités** , vous pouvez voir les entités identifiées et analysées dans le cadre de l’enquête.

Ici, vous pouvez voir les entités analysées et les détails des types d’entités, tels que les messages électroniques, les clusters, les adresses IP, les utilisateurs, et bien plus encore. Vous pouvez également voir le nombre d’entités analysées et les menaces associées à chacune d’elles.

![Page des entités d’enquête sur l’AIR](../../media/air-investigationentitiespage.png)

Vous pouvez :

- Obtenir une vue d’ensemble visuelle des entités d’enquête et des menaces détectées.

- Sélectionnez une entité pour ouvrir une page de survol qui affiche les détails de l’entité associée.

![Détails des entités d’enquête aérienne](../../media/air-investigationsentitiespagedetails.png)

### <a name="playbook-log"></a>Journal des manifestes

Sous l’onglet **Journal** , vous pouvez voir toutes les étapes du manuel qui ont eu lieu lors de l’enquête. Le journal capture un inventaire complet de tous les analyseurs et actions exécutés par les fonctionnalités d’enquête automatique d’Office 365 dans le cadre de l’AIR. Elle offre une vue claire de toutes les étapes effectuées, y compris l’action elle-même, une description et la durée du début à la fin.

![Page Journal d’enquête aérienne](../../media/air-investigationlogpage.png)

Vous pouvez :

- Obtenir une vue d’ensemble visuelle des étapes du manuel.
- Exportez les résultats dans un fichier CSV.
- Filtrer l’affichage.

### <a name="recommended-actions"></a>Actions recommandées

Sous l’onglet **actions** , vous pouvez voir toutes les actions de recherche qui sont recommandées pour la correction une fois l’enquête terminée. Actions Capturez les étapes que Microsoft vous recommande de suivre à la fin de l’enquête. Vous pouvez prendre des mesures de correction ici en sélectionnant une ou plusieurs actions.

La sélection **approuver** permet de commencer la correction. (Les autorisations appropriées sont nécessaires : le rôle de **recherche et de purge** est requis pour exécuter des actions à partir de l’Explorateur et de l’air).

Par exemple, un lecteur de sécurité peut afficher les actions, mais pas les approuver.

> [!IMPORTANT]
> Vous n’avez pas besoin d’approuver toutes les actions. Si vous n’acceptez pas l’action recommandée ou si votre organisation ne choisit pas certains types d’actions, vous pouvez choisir de **refuser** les actions ou simplement les ignorer et n’effectuer aucune action.
> L’approbation et/ou le rejet de toutes les actions permet de faire en sorte que l’enquête se ferme complètement (l’État est résolu), tout en laissant certaines actions incomplètes dans l’état de l’enquête en passant à un état partiellement résolu.

![Page action de l’enquête par avion](../../media/air-investigationactionspage.png)

Vous pouvez :

- Obtenir une vue d’ensemble visuelle des actions recommandées.
- Sélectionnez une ou plusieurs actions.
- Approuver ou rejeter les actions recommandées avec les commentaires.
- Exportez les résultats dans un fichier CSV.
- Filtrer l’affichage.

## <a name="next-steps"></a>Étapes suivantes

- [Vérifier et approuver les actions en attente](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
