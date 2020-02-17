---
title: Recherche et réponse automatiques dans Office 365
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
description: Obtenez une vue d’ensemble des fonctionnalités d’analyse et de réponse automatisées dans Office 365 Advanced Threat Protection Plan 2.
ms.openlocfilehash: 4ca4cf6033b843b92a2edceaae27f43d6eed8e7d
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42086805"
---
# <a name="automated-investigation-and-response-air-in-office-365"></a>Recherche et réponse automatiques dans Office 365

Les fonctionnalités d’analyse et de réponse automatisées (AIR) vous permettent d’exécuter des processus d’enquête automatisés en réponse à des menaces connues qui existent aujourd’hui. AIR peut aider votre équipe opérationnelle en matière de sécurité à fonctionner de manière plus efficace.
- Pour obtenir une vue d’ensemble du fonctionnement de l’avion, utilisez cet article.
- Pour commencer à utiliser AIR, consultez la rubrique [enquêter et répondre aux menaces dans Office 365](office-365-air.md).

> [!TIP]
> Avez-vous Microsoft 365 E5 ou Microsoft 365 E3 conjointement avec identité et protection contre les menaces ? Nous recommandons d’utiliser [Protection Microsoft contre les menaces](../mtp/microsoft-threat-protection.md).

## <a name="the-overall-flow-of-air"></a>Flux d’AIR global

À un niveau élevé, le flux d’AIR fonctionne comme ceci :

|Phase  |Ce qui est impliqué  |
|---------|---------|
|0,1     |Une [alerte](#alerts) est déclenchée par un événement Office et un [Manuel de sécurité](#security-playbooks) lance une enquête automatisée pour les alertes sélectionnées. <br/><br/>Un analyste de la sécurité peut également [Démarrer une enquête automatisée manuellement](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer), à partir d’un e-mail à partir de l' [Explorateur](threat-explorer.md).        |
|n°2     |Lorsqu’une enquête automatisée s’exécute, elle recueille des données supplémentaires sur le courrier électronique et les entités associées à cet e-mail (fichiers, URL et destinataires).  L’étendue de l’enquête peut augmenter, car de nouvelles alertes associées sont déclenchées.         |
|3     |Pendant et après une enquête automatisée, des [Détails et des résultats](#investigation-graph) peuvent être consultés. Les résultats incluent les [actions recommandées](#recommended-actions) qui peuvent être prises pour répondre et corriger les menaces détectées. De plus, un [Journal des manifestes](#playbook-log) est disponible pour suivre toutes les activités d’enquête.<br/><br/>Si votre organisation utilise une solution de création de rapports personnalisée ou une solution tierce, vous pouvez [utiliser l’API activité de gestion d’Office 365](office-365-air.md#use-the-office-365-management-activity-api-for-custom-or-third-party-reporting-solutions) pour afficher des informations sur les analyses et les menaces automatisées.         |
|4      |Votre équipe de gestion des opérations de sécurité examine les résultats d’enquête et les recommandations, et approuve les actions de correction. Dans Office 365, les actions correctives sont mises en œuvre uniquement après approbation par l’équipe de sécurité de votre organisation.         |

Les sections suivantes fournissent plus d’informations sur AIR, notamment des informations sur les alertes, les règles de sécurité et les détails de l’enquête. De plus, deux exemples de fonctionnement de l’AIR sont inclus dans cet article. Pour commencer à utiliser AIR, consultez la rubrique [enquêter et répondre aux menaces dans Office 365](office-365-air.md).

## <a name="alerts"></a>Alertes

Les [alertes](../../compliance/alert-policies.md#viewing-alerts) représentent des déclencheurs pour les flux de travail d’équipe des opérations de sécurité pour la réponse aux incidents. La définition de la priorité des alertes à droite pour l’enquête, tout en s’assurant qu’aucune menace n’est sans adresse est complexe. Lorsque les enquêtes dans les alertes sont effectuées manuellement, les équipes des opérations de sécurité doivent rechercher et corréler les entités (telles que le contenu, les appareils et les utilisateurs) menacées. Ces tâches et les flux de travail peuvent être très longs et impliquer plusieurs outils et systèmes. Avec AIR, Investigation and Response for Office 365 Security Events is Automated by having Security and Threat Management Alerts déclenchent automatiquement des règles de réponse de sécurité. 

Pour l’AIR, les alertes générées à partir des types de stratégies d’alerte suivants sont analysées automatiquement :  

- Un clic d’URL potentiellement malveillant a été détecté
- Courrier électronique signalé par l’utilisateur comme hameçonnage *
- Messages électroniques contenant des programmes malveillants supprimés après la remise *
- Messages électroniques contenant des URL d’hameçonnage supprimées après la remise *
- Modèles d’envoi de courrier électronique suspects détectés #
- Utilisateur non autorisé à envoyer un message électronique #

> [!NOTE]
> Les alertes signalées par un astérisque (*) sont affectées d’une gravité *informatif* dans les stratégies d’alerte respectives dans le centre de sécurité & conformité, les notifications par courrier étant désactivées. Les notifications par courrier électronique peuvent être activées par le biais de la [Configuration des stratégies d’alerte](../../compliance/alert-policies.md#alert-policy-settings). Les alertes marquées avec un hachage (#) sont généralement des alertes disponibles associées aux règles de préversion publique.

Pour afficher les alertes, dans le centre de sécurité & conformité, sélectionnez **alertes** > **afficher les alertes**. Sélectionnez une alerte pour afficher ses détails, puis, à partir de là, utilisez le lien **consulter l’enquête** pour accéder à l' [enquête](#investigation-graph)correspondante.  

> [!NOTE]
> Les alertes d’information sont masquées par défaut dans l’affichage des alertes. Pour les afficher, modifiez le filtrage des alertes de manière à inclure des alertes d’information.

Si votre organisation gère vos alertes de sécurité par le biais d’un système de gestion des alertes, d’un système de gestion des services ou d’un système de gestion des événements et des informations de sécurité (SIEM), vous pouvez envoyer des alertes Office 365 à ce système via une notification par courrier électronique ou via l' [API d’activité de gestion d’office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference). Les notifications d’alerte d’enquête via le courrier électronique ou l’API incluent des liens permettant d’accéder aux alertes dans le centre de sécurité & conformité, ce qui permet à l’administrateur de sécurité affecté de naviguer rapidement dans l’enquête.

![Alertes liées à des enquêtes](../../media/air-alerts-page-details.png) 

## <a name="security-playbooks"></a>Règles de sécurité

Les règles de sécurité sont des stratégies principales qui sont au cœur de l’automatisation dans Office Advanced Threat Protection et Microsoft Threat Protection. Les règles de sécurité fournies dans AIR sont basées sur des scénarios de sécurité réels courants et sont développés en fonction des commentaires des équipes d’opérations de sécurité. Un manuel de sécurité est lancé automatiquement lorsque des alertes spécifiques sont déclenchées au sein de votre organisation. Une fois que l’alerte est déclenchée, le manuel associé est exécuté par le système automatisé d’enquête et de réponse (AIR). L’enquête passe par l’analyse de l’alerte en fonction du manuel de cette alerte en examinant toutes les métadonnées associées (notamment les messages électroniques, les utilisateurs, les objets, les expéditeurs, etc.). En fonction des conclusions du manuel d’enquête, AIR recommande un ensemble d’actions que l’équipe de sécurité de votre organisation peut prendre pour contrôler et atténuer la menace. 

Les règles de sécurité que vous obtenez avec AIR sont conçues pour aborder les menaces les plus fréquentes auxquelles les entreprises rencontrent actuellement des courriers électroniques. Elles sont basées sur les opérations de sécurité et les équipes de réponse aux incidents, notamment celles qui permettent de défendre Microsoft et les ressources de nos clients.

### <a name="security-playbooks-are-rolling-out-in-phases"></a>Les règles de sécurité sont déployées en plusieurs phases

Dans le cadre de l’AIR, les règles de sécurité sont déployées en plusieurs phases. La phase 1 est désormais généralement disponible et comprend plusieurs règles qui fournissent des recommandations pour les actions que les administrateurs de la sécurité peuvent examiner et approuver :
- Message hameçon signalé par l’utilisateur
- URL cliquez sur modifier le verdict
- Détection de programmes malveillants après la livraison (programmes malveillants ZAP)
- Hameçonnage détecté après la livraison ZAP (hameçon ZAP)

La phase 1 prend également en charge les enquêtes de courrier électronique déclenchées par l’administrateur (à l’aide de l' [Explorateur de menaces](threat-explorer.md)).

La phase 2 est désormais en cours avec les règles suivantes en **Aperçu public**, en fournissant des recommandations pour les actions et en aidant les administrateurs de la sécurité à examiner les problèmes :
- Utilisateur signalé comme compromis (préversion publique)

D’autres règles seront publiées au fur et à mesure de leur exécution. Consultez la feuille de [route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour voir les autres éléments planifiés et bientôt disponibles.

### <a name="playbooks-include-investigation-and-recommendations"></a>Les règles incluent une enquête et des recommandations

Dans AIR, chaque manuel de sécurité inclut les éléments suivants : 
- une enquête racine des entités d’un e-mail (fichiers, URL, destinataires, adresses IP, etc.);
- la chasse aux courriels similaires reçus par l’Organisation ; 
- les étapes à suivre pour identifier et corréler les autres menaces potentielles, et 
- actions de correction des menaces recommandées.

Chaque étape de haut niveau inclut un certain nombre de sous-étapes qui sont exécutées pour fournir une réponse approfondie, détaillée et exhaustive aux menaces.

## <a name="automated-investigations"></a>Analyses automatisées

La page enquêtes automatiques indique les évaluations de votre organisation et leurs États actuels.

![Page d’enquête principale pour l’AIR](../../media/air-maininvestigationpage.png) 
  
Vous pouvez :
- Accédez directement à une enquête (sélectionnez un **ID d’enquête**).
- Appliquer des filtres. Choisissez entre **type**d’enquête **, période**, **État**ou une combinaison de ces éléments.
- Exportez les données dans un fichier. csv.

L’état d’enquête indique la progression de l’analyse et des actions. Lors de l’exécution de l’enquête, les États changent pour indiquer si des menaces ont été détectées et si des actions ont été approuvées. 


|Statut  |Signification  |
|---------|---------|
|Démarrage | L’enquête est mise en file d’attente pour commencer bientôt |
|En cours d’exécution | L’enquête a commencé et mène son analyse |
|Aucune menace détectée | L’enquête a terminé son analyse et aucune menace n’a été trouvée |
|Terminé par le système | L’enquête n’a pas été fermée et a expiré après 7 jours |
|Action en attente | L’enquête a détecté des menaces avec des actions recommandées.  L’enquête continue de s’exécuter une fois que les menaces initiales ont été détectées et les actions recommandées, vous devez donc vérifier le journal avant d’approuver les actions afin de déterminer si les analyseurs sont toujours en cours d’exécution. |
|Menaces détectées | L’enquête a détecté des menaces, mais les menaces n’ont pas d’actions disponibles dans l’atmosphère.  Il s’agit des actions de l’utilisateur qui n’ont pas encore de mesure d’AIR de direction. |
|Corrigé | L’enquête s’est terminée et a été entièrement corrigée (toutes les actions ont été approuvées) |
|Partiellement résolu | L’enquête terminée et certaines des actions recommandées ont été approuvées |
|Interrompu par l’utilisateur | Un administrateur a mis fin à l’enquête |
|Échec | Une erreur s’est produite lors de l’enquête qui l’a empêché d’atteindre une conclusion sur les menaces |
|Mise en file d’attente par limitation | L’enquête est en attente d’analyse en raison de limitations de traitement du système (pour protéger les performances du service) |
|Interruption par la limitation | L’enquête n’a pas pu être terminée en temps suffisant en raison des limitations de traitement du volume et du système. Vous pouvez redéclencher l’enquête en sélectionnant l’e-mail dans l’Explorateur et en sélectionnant l’action examiner. |

### <a name="investigation-graph"></a>Graphique de l'examen

Lorsque vous ouvrez une enquête spécifique, vous voyez la page Graph de l’enquête. Cette page affiche toutes les entités différentes : les messages électroniques, les utilisateurs (ainsi que leurs activités) et les appareils qui ont été automatiquement analysés dans le cadre de l’alerte déclenchée.

![Page graphique d’enquête sur l’AIR](../../media/air-investigationgraphpage.png)

Vous pouvez :
- Obtenir une vue d’ensemble visuelle de l’enquête actuelle.
- Afficher un résumé de la durée de l’enquête.
- Sélectionnez un nœud dans la visualisation pour afficher les détails de ce nœud.
- Sélectionnez un onglet dans la partie supérieure pour afficher les détails de cet onglet.

### <a name="alert-investigation"></a>Enquête sur les alertes

Dans l’onglet **alertes** pour une enquête, vous pouvez voir des alertes relatives à l’enquête. Les détails incluent l’alerte qui a déclenché l’enquête et d’autres alertes corrélées, telles que la connexion à risque, les violations de stratégie DLP, etc., qui sont corrélées à l’enquête. À partir de cette page, un analyste de sécurité peut également afficher des détails supplémentaires sur des alertes individuelles.

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

Il est possible d’identifier deux types différents de clusters de messagerie lors de l’analyse du courrier : les clusters de similitudes et les clusters d’indicateurs. 
- Les clusters de similarité sont des messages électroniques identifiés par la chasse aux courriers électroniques avec des attributs d’expéditeur et de contenu similaires. Ces clusters sont évalués pour le contenu malveillant en fonction des résultats de la détection d’origine. Les clusters de messagerie qui contiennent suffisamment de détections de courriers électroniques malveillants sont considérés comme malveillants.
- Les clusters d’indicateurs sont des messages électroniques identifiés par la chasse à la même entité d’indicateur (hachage de fichier ou URL) à partir du message d’origine. Lorsque l’entité fichier/URL d’origine est identifiée comme malveillante, AIR applique le verdict de l’indicateur à l’ensemble du cluster de messages contenant cette entité. Un fichier identifié comme un programme malveillant signifie que le cluster de messages électroniques contenant ce fichier est traité comme un message électronique de programme malveillant.

L’objectif du clustering est de rechercher d’autres messages électroniques associés envoyés par le même expéditeur dans le cadre d’une attaque ou d’une campagne.  Dans certains cas, les messages légitimes peuvent déclencher une enquête (par exemple, un utilisateur signale un courrier électronique marketing).  Dans ces scénarios, le clustering de messagerie doit identifier les clusters de messagerie qui ne sont pas malveillants : lorsqu’il le fait de manière appropriée, il n’indique **pas** de menace ni ne recommande la suppression des messages.

L’onglet **courrier** électronique affiche également les éléments de courrier liés à l’enquête, tels que les détails du message électronique, le courrier électronique d’origine signalé, le ou les messages électroniques zapped en raison de programmes malveillants/hameçons, etc.

Le nombre de messages identifiés dans l’onglet e-mail représente actuellement la somme totale de tous les messages électroniques affichés dans l’onglet **e-mail** . Étant donné que les messages électroniques sont présents dans plusieurs clusters, le nombre total réel de messages électroniques identifiés (et affectés par les actions de correction) est le nombre de messages électroniques uniques présents sur tous les clusters et les messages électroniques des destinataires d’origine. 

L’Explorateur et l’AIR envoient les messages électroniques par destinataire, étant donné que les verdicts de sécurité, les actions et les emplacements de remise varient selon les destinataires. Par conséquent, un message électronique d’origine envoyé à trois utilisateurs est compté comme un total de trois messages électroniques au lieu d’un seul. Remarque dans certains cas, un courrier électronique est compté deux ou plusieurs fois, car le courrier électronique peut avoir plusieurs actions et il peut y avoir plusieurs copies de l’e-mail une fois toutes les actions effectuées. Par exemple, un courrier indésirable détecté lors de la remise peut entraîner le blocage du courrier électronique (mis en quarantaine) et le remplacement du courrier électronique (fichier de menace remplacé par un fichier d’avertissement, puis remis à la boîte aux lettres de l’utilisateur). Étant donné qu’il existe littéralement deux copies du courrier électronique dans le système, les deux peuvent être comptés dans le compte du cluster. 

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

Par exemple, dans l’image suivante, AIR a identifié des indicateurs de compromission et des anomalies en fonction d’une nouvelle règle de boîte de réception créée. Des détails supplémentaires (preuve) de l’enquête sont disponibles via des vues détaillées dans cet onglet. les indicateurs de compromis et d’anomalies peuvent également inclure des détections d’anomalies dans la [sécurité des applications Cloud de Microsoft](https://docs.microsoft.com/cloud-app-security).

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

|L’analyseur | Description |
|-----|-----|
|Enquête sur les violations DLP |Examiner toutes les violations détectées par la [protection contre la perte de données](../../compliance/data-loss-prevention-policies.md) (DLP) d’Office 365 |
|Extraction des indicateurs de courrier électronique |Extraire les indicateurs de l’en-tête, du corps et du contenu d’un message électronique à des fins d’enquête |
|Réputation de hachage de fichier |Détecter les anomalies en fonction des hachages de fichiers pour les utilisateurs et les ordinateurs de votre organisation |
|Identification du cluster de messagerie |Analyse du cluster de messagerie basée sur l’en-tête, le corps, le contenu et les URL |
|Analyse du volume du cluster de messagerie |Analyse du cluster de messagerie en fonction des modèles de volume de flux de messagerie sortants |
|Enquête de délégation de messagerie |Enquêter sur l’accès de délégation de messagerie pour les boîtes aux lettres utilisateur liées à cette enquête |
|Enquête sur les règles de transfert de courrier |Examiner les règles de transfert de courrier pour les boîtes aux lettres utilisateur associées à cette enquête |
|Programmes malveillants manqués détectés |Détecter les programmes malveillants manqués remis à la boîte aux lettres de l’utilisateur dans votre organisation |
|Détonation à la demande |Détonation à la demande déclenchée pour les messages électroniques, les pièces jointes et les URL |
|Analyse des anomalies de messages sortants |Détecter les anomalies en fonction de l’historique du flux de messagerie des modèles d’envoi pour les utilisateurs de votre organisation |
|Détection des programmes malveillants sortants et des anomalies du courrier indésirable |Détecter les programmes malveillants, les hameçons et les courriers indésirables internes et sortants provenant des utilisateurs de votre organisation |
|Enquête sur les domaines des expéditeurs |Vérification à la demande de la réputation de domaine à partir du [graphique de sécurité intelligent Microsoft](https://www.microsoft.com/security/operations/intelligence) et des sources externes de renseignement contre les menaces |
|Enquête sur l’adresse IP de l’expéditeur | Vérification de la réputation de l’IP à la demande à partir du [graphique de sécurité intelligent Microsoft](https://www.microsoft.com/security/operations/intelligence) et des sources d’aide à la décision externes |
|L’URL clique sur l’enquête | Examiner les clics des utilisateurs protégés par les [liens approuvés ATP d’Office 365](atp-safe-links.md) dans votre organisation |
|Enquête de réputation d’URL |Vérification à la demande de la réputation de l’URL à partir de [Microsoft intelligent Security Graph](https://www.microsoft.com/security/operations/intelligence) et External Threat Intelligence sources |
|Enquête sur l’activité des utilisateurs |Analyser les anomalies d’activité des utilisateurs dans [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) |
|Extraction d’indicateurs de messages électroniques signalés par l’utilisateur |Extraire les indicateurs de l’en-tête, du corps et du contenu de la [messagerie signalée](enable-the-report-message-add-in.md) par l’utilisateur pour l’enquête |


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

## <a name="remediation-actions"></a>Actions de correction

Lorsqu’une enquête automatisée est en cours d’exécution ou qu’elle est terminée, une ou plusieurs actions correctives s’affichent généralement. Le tableau suivant répertorie les actions de correction possibles dans Office 365 AIR.

|Opération | Description |
|-----|-----|
|Bloquer l’URL (heure du clic) |Se protéger contre les e-mails et les documents contenant des URL malveillantes. Cela permet de bloquer les liens malveillants et les pages Web associées via [des liens fiables](atp-safe-links.md) lorsque l’utilisateur clique sur un lien dans un fichier Office existant ou dans un ancien message électronique. |
|Courrier électronique de suppression douce  |Suppression logicielle de messages électroniques spécifiques de la boîte aux lettres d’un utilisateur|
|Clusters de suppression de courrier électronique  |Suppression logicielle de messages électroniques malveillants correspondant à une requête de toutes les boîtes aux lettres des utilisateurs|
|Désactiver le transfert de courrier externe |Supprime la règle de transfert d’une boîte aux lettres d’un utilisateur final spécifique.|

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Exemple : un message hameçon signalé par un utilisateur lance un manuel d’enquête.

Lorsqu’un utilisateur de votre organisation soumet un message électronique et le signale à Microsoft à l’aide du [complément de message de rapport pour Outlook ou Outlook Web App](enable-the-report-message-add-in.md), le rapport est également envoyé à votre système et est visible dans l’Explorateur dans la vue signalée par l’utilisateur. Ce message signalée par l’utilisateur déclenche désormais une alerte d’information basée sur le système, qui lance automatiquement le manuel d’enquête.

Lors de la phase d’enquête de racine, différents aspects du courrier électronique sont évalués. Cela inclut ce qui suit :
- Détermination du type de menace susceptible de se présenter ;
- Expéditeur ;
- Emplacement d’envoi du courrier électronique (infrastructure émettrice);
- Si d’autres instances du courrier électronique ont été remises ou bloquées ;
- Une évaluation de nos analystes ;
- Si le courrier électronique est associé à des campagnes connues ;
- et bien plus encore.

Une fois l’enquête terminée, le manuel fournit une liste des actions recommandées à effectuer sur le courrier électronique d’origine et les entités qui lui sont associées.
  
Ensuite, plusieurs étapes d’enquête sur les menaces et de chasse sont exécutées :

- Les messages électroniques similaires sont identifiés par des recherches de cluster de messagerie.
- Le signal est partagé avec d’autres plateformes, telles que [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Une détermination est effectuée sur le fait que les utilisateurs aient cliqué sur les liens malveillants dans les messages électroniques suspects.
- Une vérification est effectuée dans Office 365 Exchange Online Protection ([EOP](exchange-online-protection-eop.md)) et Office 365 Advanced Threat Protection ([ATP](office-365-atp.md)) pour voir s’il existe d’autres messages similaires signalés par les utilisateurs.
- Une vérification est exécutée pour déterminer si un utilisateur a été compromis. Cette vérification exploite les signaux entre Office 365, [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)et [Azure Active Directory](https://docs.microsoft.com/azure/active-directory), en mettant en corrélation les anomalies d’activité de l’utilisateur associées. 

Au cours de la phase de chasse, les risques et les menaces sont affectés à différentes étapes de la chasse. 

La correction est la phase finale du manuel. Pendant cette phase, les étapes de correction sont prises, en fonction des phases d’enquête et de chasse. 

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces

En plus des recherches automatiques déclenchées par une alerte, l’équipe des opérations de sécurité de votre organisation peut déclencher une enquête automatique à partir d’une vue dans l' [Explorateur de menaces](threat-explorer.md).

Par exemple, supposons que vous affichiez des données dans l’Explorateur à propos des messages signalés par l’utilisateur. Vous pouvez sélectionner un élément dans la liste des résultats, puis cliquer sur **Rechercher** dans le menu Action (en supposant que vous disposez des autorisations de correction appropriées).

![Messages signalés par l’utilisateur dans l’Explorateur avec le bouton Rechercher](../../media/Explorer-UserReported-Investigate.png)

Autre exemple : Supposons que vous affichiez des données sur les messages électroniques détectés comme contenant des programmes malveillants, et que plusieurs messages électroniques soient détectés comme contenant des programmes malveillants. Vous pouvez sélectionner l’onglet **courrier électronique** , sélectionner un ou plusieurs messages, puis, dans le menu **actions** , sélectionner **examiner**. 

![Démarrage d’une enquête pour les programmes malveillants dans l’Explorateur](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

À l’instar des règles déclenchées par une alerte, les recherches automatiques déclenchées à partir d’une vue dans l’Explorateur incluent une enquête de racine, des étapes permettant d’identifier et de corréler les menaces, ainsi que les actions recommandées pour atténuer ces menaces.

## <a name="how-to-get-air"></a>Comment obtenir de l’AIR

Office 365 Examen et réponse automatisés est inclus dans les abonnements suivants :

- Microsoft 365 E5
- Office 365 E5
- Protection Microsoft contre les menaces
- Office 365 – Protection avancée contre les menaces Plan 2

Si vous n’avez pas l’un de ces abonnements, [Démarrez une version d’évaluation gratuite](https://go.microsoft.com/fwlink/p/?LinkID=698279&culture=en-US&country=US).

Pour en savoir plus sur la disponibilité des fonctionnalités, consultez la rubrique [disponibilité des fonctionnalités dans les plans de protection avancée contre les menaces](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="required-permissions-to-use-air-capabilities"></a>Autorisations requises pour utiliser les fonctionnalités AIR

Les autorisations sont accordées par le biais de certains rôles, tels que ceux décrits dans le tableau suivant : 

|Tâche |Rôle (s) requis |
|--|--|
|Pour configurer les fonctionnalités AIR |Un des rôles suivants : <br/>- **Administrateur général**<br/>- **Administrateur de la sécurité** <br/>Ces rôles peuvent être attribués dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [Centre de conformité Office 365 Security &](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). |
|Pour approuver ou rejeter des actions recommandées|L’un des rôles suivants, affecté dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [centre de sécurité & conformité Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)) :<br/>- **Administrateur général** <br/>- **Administrateur de la sécurité**<br/>- **Lecteur de sécurité** <br/>--- et ---<br/>- **Recherche et purger** (ce rôle est affecté uniquement dans le [Centre de conformité Office 365 Security &](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). Vous devrez peut-être créer un groupe de rôles à cet emplacement et ajouter le rôle de recherche et de purge à ce nouveau groupe de rôles.)

## <a name="next-steps"></a>Étapes suivantes

- [Prise en main de l’utilisation de l’AIR dans Office 365](office-365-air.md)
- [En savoir plus sur AIR dans Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) 
- [Consultez la feuille de route Microsoft 365 pour découvrir les éléments bientôt disponibles et à déployer](https://www.microsoft.com/microsoft-365/roadmap?filters=)

## <a name="see-also"></a>Voir aussi

- [Protection Microsoft contre les menaces](../mtp/microsoft-threat-protection.md)
- [Recherche et correction automatisées (AIR) dans la protection contre les menaces Microsoft](../mtp/mtp-autoir.md)
