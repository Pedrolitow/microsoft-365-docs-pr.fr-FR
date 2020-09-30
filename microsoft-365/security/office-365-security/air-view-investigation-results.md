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
ms.collection: M365-security-compliance
description: Pendant et après une enquête automatisée dans Microsoft 365, vous pouvez afficher les résultats et les résultats clés.
ms.date: 09/29/2020
ms.openlocfilehash: df0eaa54d8bc1c9cd6c91b6b36958e1eb0d2bfd6
ms.sourcegitcommit: 6b1d0bea86ced26cae51695c0077adce8bcff3c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "48309105"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Détails et résultats d’une enquête automatisée dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Lorsqu’une [enquête automatisée](office-365-air.md) se produit dans [Office 365 protection avancée contre les menaces](office-365-atp.md), des informations détaillées sur cette enquête sont disponibles pendant et après le processus d’enquête automatisé. Si vous disposez des autorisations nécessaires, vous pouvez afficher ces détails dans une vue Détails de l'examen. La vue Détails de l’examen vous fournit l’État à jour et la possibilité d’approuver les actions en attente.

## <a name="investigation-status"></a>État de l’enquête

L’état d’enquête indique la progression de l’analyse et des actions. Lors de l’exécution de l’enquête, les États changent pour indiquer si des menaces ont été détectées et si des actions ont été approuvées.

****

|Statut|Signification|
|---|---|
|Démarrage| L’enquête a été déclenchée et attend de démarrer.|
|En cours d’exécution| Le processus d’enquête a commencé et est en cours d’exécution. Cet État se produit également lorsque les [actions en attente](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-review-approve-pending-completed-actions#approve-or-reject-pending-actions) sont approuvées.|
|Aucune menace détectée| L’enquête est terminée et aucune menace (compte d’utilisateur, message électronique, URL ou fichier) n’a été identifiée. <br/><br/>**Conseil**: Si vous pensez qu’un événement a été manqué (par exemple, un faux négatif), vous pouvez prendre une mesure à l’aide de l' [Explorateur de menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer).|
|Menaces détectées|L’enquête automatisée a détecté des problèmes, mais il n’existe aucune action de correction spécifique pour résoudre ces problèmes.<br/><br/> L’État menaces détectées peut se produire lorsqu’un type d’activité utilisateur a été identifié mais qu’aucune action de nettoyage n’est disponible. Voici quelques exemples d’activités utilisateur : <br/>-Un événement de [protection contre la perte de données](https://docs.microsoft.com/Microsoft-365/compliance/data-loss-prevention-policies) (DLP) <br/>-Un e-mail envoyant une anomalie <br/>-Programmes malveillants envoyés <br/>-Hameçon envoyé<br/>L’enquête n’a trouvé aucune URL, aucun fichier ou message électronique malveillant à corriger, ni aucune activité de boîte aux lettres à corriger, telle que la désactivation des règles de transfert ou la délégation. <br/><br/>**Conseil**: Si vous pensez qu’un événement a été manqué (par exemple, un faux négatif), vous pouvez examiner et prendre des mesures à l’aide de l' [Explorateur de menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer).|
|Terminé par le système| L’enquête s’est arrêtée. Une enquête peut s’arrêter pour plusieurs raisons :<br/>-Les actions en attente de l’enquête ont expiré. Délai d’expiration des actions en attente après approbation d’une semaine. <br/>-Il y a trop d’actions. Par exemple, si un trop grand nombre d’utilisateurs cliquent sur des URL malveillantes, il peut dépasser la capacité de l’enquête à exécuter tous les analyseurs, de sorte que l’enquête s’arrête. <br/><br/>**Conseil**: si une enquête s’arrête avant que des actions ne soient prises, essayez d’utiliser l' [Explorateur de menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer) pour trouver et résoudre les menaces.|
|Action en attente| L’enquête a détecté une menace, telle qu’un e-mail malveillant, une URL malveillante ou un paramètre de boîte aux lettres à risque, et une action visant à corriger cette menace est en attente d' [approbation](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-review-approve-pending-completed-actions).<br/><br/>L’état de l’action en attente est déclenché lorsqu’une menace avec une action correspondante est trouvée. Toutefois, la liste des actions en attente peut augmenter à mesure qu’une enquête s’exécute. Consultez le [Journal d’enquête](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-view-investigation-results#playbook-log) pour voir si d’autres éléments sont toujours en attente de réalisation.|
|Corrigé| L’enquête terminée et toutes les actions ont été approuvées (corrigées entièrement).<br/><br/>**Remarque**: les actions de correction approuvées peuvent comporter des erreurs qui empêchent le suivi des actions. Que les actions de correction soient exécutées avec succès ou non, l’état de l’enquête ne change pas. Pour obtenir des résultats détaillés, consultez le [Journal d’enquête](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-view-investigation-results) .|
|Partiellement résolu| L’enquête a entraîné des actions de correction, et certaines ont été approuvées et terminées. D’autres actions sont toujours [en attente](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-review-approve-pending-completed-actions).|
|Échec| Au moins un analyseur d’enquête a rencontré un problème où il n’a pas pu se terminer correctement. <br/><br/>**Remarque**: si une enquête échoue après l’approbation des actions correctives, les actions correctives ont pu encore aboutir. Pour obtenir des résultats détaillés, consultez le [Journal d’enquête](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-view-investigation-results) .|
|Mise en file d’attente par limitation| Une enquête est placée dans une file d’attente. Lorsque d’autres enquêtes sont terminées, les recherches en attente commencent. La limitation permet d’éviter les performances de service médiocres. <br/><br/>**Conseil**: les actions en attente permettent de limiter le nombre de nouvelles enquêtes pouvant être exécutées. Veillez à [approuver (ou refuser) les actions en attente](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-review-approve-pending-completed-actions#approve-or-reject-pending-actions).|
|Interruption par la limitation| Si une enquête est conservée dans la file d’attente trop longtemps, elle s’arrête. <br/><br/>**Conseil**: vous pouvez [Démarrer une enquête à partir de l’Explorateur de menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|
|

## <a name="view-details-of-an-investigation"></a>Afficher les détails d’une enquête

1. Accédez au centre de sécurité & conformité ( [https://protection.office.com](https://protection.office.com) ) et connectez-vous.

2. Effectuez l'une des opérations suivantes :

    - Accédez au tableau de bord **gestion des menaces**  >  **Dashboard**. Cela vous amène au [tableau de bord de sécurité](security-dashboard.md). Vos widgets d’AIR s’affichent dans la partie supérieure du [tableau de bord de sécurité](security-dashboard.md). Sélectionnez un widget, par exemple, **Résumé des enquêtes**.

    - Accédez aux enquêtes de **gestion des menaces**  >  **Investigations**.

    L’une ou l’autre de ces méthodes vous permet d’accéder à une liste d’investigations.

    ![Page d’enquête principale pour l’AIR](../../media/air-maininvestigationpage.png)

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** . Cette action ouvre la page des détails de l’enquête, en commençant par le graphique d’enquête dans l’affichage.

    ![Page graphique d’enquête sur l’AIR](../../media/air-investigationgraphpage.png)

   Utilisez les différents onglets pour en savoir plus sur l’enquête.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Afficher les détails d’une alerte liée à une enquête

Certains types d’alertes déclenchent une enquête automatisée dans Microsoft 365. Pour en savoir plus, consultez la rubrique [alertes](automated-investigation-response-office.md#alerts). Utilisez la procédure suivante pour afficher les détails d’une alerte associée à une enquête automatisée.

1. Accédez au centre de sécurité & conformité ( [https://protection.office.com](https://protection.office.com) ) et connectez-vous.

2. Accédez aux enquêtes de **gestion des menaces**  >  **Investigations**.

3. Dans la liste des enquêtes, sélectionnez un élément dans la colonne **ID** .

4. Les détails d’une enquête étant ouverts, sélectionnez l’onglet **alertes** . Les alertes qui ont déclenché l’enquête sont répertoriées ici.

5. Sélectionnez un élément dans la liste. Un menu volant s’ouvre, avec des détails sur l’alerte et des liens vers des informations et des actions supplémentaires.

6. Passez en revue les informations de la fenêtre mobile et, en fonction de l’alerte en particulier, effectuez une action, telle que **résoudre**, **supprimer**ou **avertir les utilisateurs**.

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
- Appliquer des filtres. Choisissez entre **type**d’enquête **, période**, **État**ou une combinaison de ces éléments.
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

Dans l’onglet **e-mail** pour une enquête, vous pouvez voir les courriers électroniques d’origine et les clusters de messages similaires identifiés dans le cadre de l’enquête.

Étant donné le volume de courrier électronique que les utilisateurs d’une organisation envoient et reçoivent, ainsi que la nature multi-utilisateur des communications et des attaques de messagerie, le processus de

- mise en cluster de messages électroniques en fonction d’attributs similaires provenant d’un en-tête, d’un corps, d’une URL et de pièces jointes de message ;
- séparation du courrier électronique malveillant du courrier électronique approprié ; les
- prendre des mesures sur les messages électroniques malveillants

peut prendre beaucoup de temps. AIR automatise ce processus en enregistrant le temps et les efforts de l’équipe de sécurité de votre organisation.

Trois types de clusters de messagerie différents peuvent être identifiés lors de l’analyse du courrier : les clusters de similarité (toutes les enquêtes), les clusters d’indicateurs (toutes les enquêtes) et les clusters de boîtes aux lettres/utilisateurs.

- Les clusters de similarité sont des messages électroniques identifiés par la chasse aux courriers électroniques avec des attributs d’expéditeur et de contenu similaires. Ces clusters sont évalués pour le contenu malveillant en fonction des résultats de la détection d’origine. Les clusters de messagerie qui contiennent suffisamment de détections de courriers électroniques malveillants sont considérés comme malveillants.
- Les clusters d’indicateurs sont des messages électroniques identifiés par la chasse à la même entité d’indicateur (hachage de fichier ou URL) à partir du message d’origine. Lorsque l’entité fichier/URL ouserriginal est identifiée comme malveillante, AIR applique le verdict de l’indicateur à l’ensemble du cluster de messages contenant cette entité. Un fichier identifié comme un programme malveillant signifie que le cluster de messages électroniques contenant ce fichier est traité comme un message électronique de programme malveillant.
- Les clusters de boîtes aux lettres/utilisateurs sont des messages électroniques liés à l’utilisateur impliqué dans une enquête de compromission d’un utilisateur.  Notez que ces clusters de messagerie sont destinés à une analyse plus poussée par l’équipe des opérations de sécurité et ne génèrent pas d’actions de correction de messagerie.  Les clusters d’utilisateurs/boîtes aux lettres de manifeste de compromission examinent les e-mails envoyés par l’utilisateur en cours d’analyse, afin de comprendre l’impact potentiel des messages envoyés à partir de la boîte aux lettres :
    - Les courriers électroniques malveillants envoyés à partir de la boîte aux lettres ou de l’utilisateur, qui indiquent une éventuelle compromission de la boîte aux lettres/du compte et affichent d’autres utilisateurs/boîtes aux lettres susceptibles d’avoir un impact sur les messages envoyés comme faisant partie d’un compromis.
    - E-mails suspects envoyés par la boîte aux lettres ou l’utilisateur, affichant les courriers indésirables/en masse envoyés à partir de la boîte aux lettres, qui peuvent être liés à une compromission potentielle ou au moins indiquer une activité potentielle indésirable à partir du compte de messagerie.
    - Nettoyez les e-mails envoyés par la boîte aux lettres/l’utilisateur, qui fournira à l’équipe des opérations de sécurité une vue des messages électroniques légitimes envoyés, mais peut inclure l’exfiltration des données lorsque le compte de messagerie est compromis.

L’objectif du clustering est de rechercher d’autres messages électroniques associés envoyés par le même expéditeur dans le cadre d’une attaque ou d’une campagne.  Dans certains cas, les messages légitimes peuvent déclencher une enquête (par exemple, un utilisateur signale un courrier électronique marketing).  Dans ces scénarios, le clustering de messagerie doit identifier les clusters de messagerie qui ne sont pas malveillants : lorsqu’il le fait de manière appropriée, il n’indique **pas** de menace ni ne recommande la suppression des messages.

L’onglet **courrier** électronique affiche également les éléments de courrier liés à l’enquête, tels que les détails du message électronique, le courrier électronique d’origine signalé, le ou les messages électroniques zapped en raison de programmes malveillants/hameçons, etc.

Le nombre de messages identifiés dans l’onglet e-mail représente actuellement la somme totale de tous les messages électroniques affichés dans l’onglet **e-mail** . Étant donné que les messages électroniques sont présents dans plusieurs clusters, le nombre total réel de messages électroniques identifiés (et affectés par les actions de correction) est le nombre de messages électroniques uniques présents sur tous les clusters et les messages électroniques des destinataires d’origine.

L’Explorateur et l’AIR comptent tous les deux par destinataire, car les verdicts de sécurité, les actions et les emplacements de remise varient selon les destinataires. Ainsi, un message électronique d’origine envoyé à trois utilisateurs compte au total trois messages électroniques au lieu d’un seul. Dans certains cas, un message électronique est compté deux ou plusieurs fois, par exemple lorsqu’un courrier électronique comporte plusieurs actions, ou lorsqu’il y a plusieurs copies de l’e-mail lorsque toutes les actions se produisent. Par exemple, un courrier indésirable détecté lors de la remise peut entraîner l’envoi d’un message électronique bloqué (mis en quarantaine) et d’un message électronique remplacé (fichier de menace remplacé par un fichier d’avertissement, puis remis à la boîte aux lettres de l’utilisateur). Étant donné qu’il y a littéralement deux copies du courrier électronique dans le système, les deux peuvent être comptés dans le compte du cluster.

Le nombre de messages est calculé lors de l’enquête et certains comptes sont recalculés lorsque vous ouvrez des lanceurs d’investigation (sur la base d’une requête sous-jacente). Le nombre de messages affichés pour les clusters de courrier électronique sous l’onglet e-mail et la valeur de quantité de courrier électronique affichée dans le menu volant de cluster sont calculés lors de l’enquête et ne changent pas. Le nombre de courriers électroniques affiché en bas de l’onglet e-mail de la fenêtre mobile du cluster de messagerie et le nombre de messages électroniques affichés dans l’Explorateur reflètent les messages électroniques reçus après l’analyse initiale de l’enquête. Par conséquent, un cluster de messagerie qui affiche une quantité initiale de 10 messages électroniques affiche une liste de courriers au total 15 lorsque cinq autres messages électroniques arrivent entre la phase d’analyse de l’enquête et lorsque l’administrateur révise l’enquête.  De la même manière que les enquêtes anciennes peuvent commencer à avoir un nombre plus important que les requêtes de l’Explorateur s’affichent, puisque le service ATP P2 expire les données après 7 jours pour les tirages et 30 jours pour les licences payantes  L’affichage des compteurs historique et actuel dans différentes vues permet d’indiquer l’impact du courrier électronique au moment de l’examen et l’impact actuel jusqu’à l’exécution de la correction.

À titre d’exemple, considérons le scénario suivant. Le premier cluster de trois messages électroniques était considéré comme un hameçonnage. Un autre cluster de messages similaires avec la même adresse IP et l’objet a été trouvé et considéré comme malveillant, car certains d’entre eux étaient identifiés comme des hameçons lors de la détection initiale.

![Page d’enquête sur le courrier électronique aérien](../../media/air-investigationemailpage.png)

Vous pouvez :
- Obtenir une vue d’ensemble visuelle des résultats de clustering actuels et des menaces détectées.
- Cliquez sur une entité de cluster ou une liste de menaces pour ouvrir une page de survol qui affiche les détails de l’alerte complète.
- Pour approfondir le cluster de messagerie, cliquez sur le lien « ouvrir dans l’Explorateur » en haut de l’onglet « Détails du cluster de messagerie ».

![Courrier électronique d’enquête aérienne avec détails du menu volant](../../media/air-investigationemailpageflyoutdetails.png)

> [!NOTE]
> Dans le contexte de la messagerie électronique, vous pouvez voir une surface d’anomalie de volume dans le cadre de l’enquête. Une anomalie de volume indique un pic dans les messages électroniques similaires de la durée de l’événement d’enquête par rapport aux délais précédents. Ce pic dans le trafic de messagerie avec des caractéristiques similaires (par exemple, domaine d’objet et de l’expéditeur, similitude entre le corps et IP de l’expéditeur) est typique du début des campagnes ou des attaques par courrier électronique. Toutefois, les campagnes de courrier électronique, de courrier indésirable et légitimes partagent généralement ces caractéristiques. Les anomalies de volume représentent une menace potentielle et peuvent donc être moins sévères par rapport aux menaces de programmes malveillants ou hameçons identifiées à l’aide de moteurs antivirus, de détonation ou de réputation malveillante.

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

Dans certains cas, AIR établit une corrélation entre les menaces de messagerie et les appareils (par exemple, les programmes malveillants zapped). Par exemple, une enquête transmet un hachage de fichier malveillant à [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection
) pour enquêter. Cela permet l’analyse automatisée des ordinateurs pertinents pour vos utilisateurs, afin de garantir que les menaces sont résolues à la fois dans le nuage et sur vos points de terminaison.

Vous pouvez :

- Obtenir une vue d’ensemble visuelle des ordinateurs et menaces actuels détectés.
- Sélectionnez un ordinateur pour ouvrir une vue dans les [recherches Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) associées dans le centre de sécurité Microsoft Defender.

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

****

|L’analyseur| Description|
|---|---|
|Enquête sur les violations DLP|Examiner toutes les violations détectées par la [protection contre la perte de données](../../compliance/data-loss-prevention-policies.md) (DLP)|
|Extraction des indicateurs de courrier électronique|Extraire les indicateurs de l’en-tête, du corps et du contenu d’un message électronique à des fins d’enquête|
|Réputation de hachage de fichier|Détecter les anomalies en fonction des hachages de fichiers pour les utilisateurs et les ordinateurs de votre organisation|
|Identification du cluster de messagerie|Analyse du cluster de messagerie basée sur l’en-tête, le corps, le contenu, les fichiers et les URL|
|Analyse du volume du cluster de messagerie|Analyse du cluster de messagerie en fonction des modèles de volume de flux de messagerie sortants|
|Enquête de délégation de messagerie|Enquêter sur l’accès de délégation de messagerie pour les boîtes aux lettres utilisateur liées à cette enquête|
|Enquête sur les règles de transfert de courrier|Examiner les règles de transfert de courrier pour les boîtes aux lettres utilisateur associées à cette enquête|
|Programmes malveillants manqués détectés|Détecter les programmes malveillants manqués remis à la boîte aux lettres de l’utilisateur dans votre organisation|
|Détonation à la demande|Détonation à la demande déclenchée pour les messages électroniques, les pièces jointes et les URL|
|Analyse des anomalies de messages sortants|Détecter les anomalies en fonction de l’historique du flux de messagerie des modèles d’envoi pour les utilisateurs de votre organisation|
|Détection des programmes malveillants sortants et des anomalies du courrier indésirable|Détecter les programmes malveillants, les hameçons et les courriers indésirables internes et sortants provenant des utilisateurs de votre organisation|
|Enquête sur les domaines des expéditeurs|Vérification à la demande de la réputation de domaine à partir du [graphique de sécurité intelligent Microsoft](https://www.microsoft.com/security/operations/intelligence) et des sources externes de renseignement contre les menaces|
|Enquête sur l’adresse IP de l’expéditeur| Vérification de la réputation de l’IP à la demande à partir du [graphique de sécurité intelligent Microsoft](https://www.microsoft.com/security/operations/intelligence) et des sources d’aide à la décision externes|
|L’URL clique sur l’enquête| Examiner les clics des utilisateurs protégés par les [liens approuvés ATP d’Office 365](atp-safe-links.md) dans votre organisation|
|Enquête de réputation d’URL|Vérification à la demande de la réputation de l’URL à partir de [Microsoft intelligent Security Graph](https://www.microsoft.com/security/operations/intelligence) et External Threat Intelligence sources|
|Enquête sur l’activité des utilisateurs|Analyser les anomalies d’activité des utilisateurs dans [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)|
|Extraction d’indicateurs de messages électroniques signalés par l’utilisateur|Extraire les indicateurs de l’en-tête, du corps et du contenu de la [messagerie signalée](enable-the-report-message-add-in.md) par l’utilisateur pour l’enquête|
|

### <a name="recommended-actions"></a>Actions recommandées

Sous l’onglet **actions** , vous pouvez voir toutes les actions de recherche qui sont recommandées pour la correction une fois l’enquête terminée.

Actions Capturez les étapes que Microsoft vous recommande de suivre à la fin de l’enquête. Vous pouvez prendre des mesures de correction ici en sélectionnant une ou plusieurs actions. Si vous cliquez sur **approuver** , le début de la correction est possible. (Les autorisations appropriées sont nécessaires : le rôle « recherche et purge » est requis pour exécuter des actions à partir de l’Explorateur et de l’AIR). Par exemple, un lecteur de sécurité peut afficher les actions mais pas les approuver. Remarque : vous n’avez pas besoin d’approuver toutes les actions. Si vous n’acceptez pas l’action recommandée ou si votre organisation ne choisit pas certains types d’actions, vous pouvez choisir de **refuser** les actions ou simplement les ignorer et n’effectuer aucune action. L’approbation et/ou le rejet de toutes les actions permet de faire en sorte que l’enquête se ferme complètement (l’État est résolu), tout en laissant certaines actions incomplètes dans l’état de l’enquête en passant à un état partiellement résolu.

![Page action de l’enquête par avion](../../media/air-investigationactionspage.png)

Vous pouvez :

- Obtenir une vue d’ensemble visuelle des actions recommandées.
- Sélectionnez une ou plusieurs actions.
- Approuver ou rejeter les actions recommandées avec les commentaires.
- Exportez les résultats dans un fichier CSV.
- Filtrer l’affichage.

## <a name="next-steps"></a>Étapes suivantes

- [Vérifier et approuver les actions en attente](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-review-approve-pending-completed-actions?view=o365-worldwide#approve-or-reject-pending-actions)

- [En savoir plus sur l’analyse et la réponse automatisées dans Microsoft Threat Protection](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)
