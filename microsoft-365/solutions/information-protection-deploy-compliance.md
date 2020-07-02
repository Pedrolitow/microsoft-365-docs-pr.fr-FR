---
title: Utiliser le score de conformité et le gestionnaire de conformité pour gérer les actions d’amélioration
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- M365solutions
ms.custom: ''
description: Découvrez comment utiliser le score Complance et le gestionnaire de conformité pour améliorer votre niveau de protection des données personnelles.
ms.openlocfilehash: 4a45f24d66d08c2c0f17d75d897f523ef074936c
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016366"
---
# <a name="use-compliance-score-and-compliance-manager-to-manage-improvement-actions"></a>Utiliser le score de conformité et le gestionnaire de conformité pour gérer les actions d’amélioration

Le score de conformité de Microsoft et le gestionnaire de conformité peuvent être utilisés conjointement pour gérer les améliorations liées aux réglementations de confidentialité des données, telles que le règlement général sur la protection des [données (RGPD)](../compliance/gdpr.md), la [protection des consommateurs California CCPA)](../compliance/ccpa-faq.md), le HIPAA-Hi (USA Health Care Privacy Act) et le Brésil Data Protection Act (LGPD). 

Cet article fournit des instructions sur l’utilisation de ces outils à des fins de confidentialité des données.

>[!Note]
>Les actions client fournies dans le gestionnaire de conformité sont des recommandations. Il vous revient d’évaluer l’efficacité de ces recommandations dans vos environnements réglementaires avant de l’implémenter. Les recommandations du gestionnaire de conformité ne doivent pas être interprétées comme une garantie de conformité.
>

## <a name="planned-updates-for-compliance-score-and-compliance-manager"></a>Mises à jour planifiées pour le score de conformité et le gestionnaire de conformité

Le [score de conformité](../compliance/compliance-score.md) (actuellement en préversion) nécessite l’ajout de vos évaluations ciblées pour une réglementation (par exemple, RGPD) à partir du gestionnaire de [conformité](../compliance/compliance-manager-overview.md). Dans une prochaine version, la plupart des fonctionnalités du gestionnaire de conformité seront fusionnées en une expérience de score de conformité unifiée, ce qui réduira la nécessité d’utiliser plusieurs outils.

Voici les outils de votre abonnement, qui vous obligent à vous connecter :

- [Score de conformité dans le centre d’administration de la conformité Microsoft](https://compliance.microsoft.com/compliancescore)
- [Gestionnaire de conformité dans le portail d’approbation des services Microsoft](https://servicetrust.microsoft.com/ComplianceManager/V3)

## <a name="getting-started-with-compliance-manager"></a>Mise en route avec le gestionnaire de conformité 

Le [Gestionnaire de conformité](../compliance/working-with-compliance-manager.md) (actuellement en version préliminaire) est un outil d’évaluation des risques gratuit basé sur un flux de travail dans le portail d’approbation de service Microsoft pour la gestion des activités de conformité aux réglementations concernant les services Cloud de Microsoft. Dans le cadre de votre abonnement Microsoft 365 ou Azure Active Directory (Azure AD), le gestionnaire de conformité vous aide à gérer la conformité réglementaire dans le cadre du modèle de responsabilité partagé pour les services Cloud de Microsoft.

Bien que vous puissiez consulter votre score de conformité global et effectuer un certain nombre d’autres fonctions dans la page **score de conformité** du centre de conformité, vous devez utiliser le gestionnaire de conformité via le portail d’approbation des services pour configurer d’abord les évaluations pour votre réglementation sur la confidentialité des données. Les données de ces évaluations apparaissent ensuite dans le score de conformité pour un affichage et un filtrage supplémentaires. 

À l’aide de l’interface du gestionnaire de conformité, vous pouvez sélectionner un ou plusieurs modèles de régulation liés à la confidentialité des données et les grouper pour évaluer et suivre les actions d’amélioration requises dans l’ensemble. Vous pouvez également afficher des informations sur les contrôles que chaque règlement appelle pour le service cible, séparé par les contrôles gérés par Microsoft vs client.

Les évaluations et les améliorations sélectionnées ici apparaissent également dans score de conformité dans le centre de conformité Microsoft, ce qui souligne l’importance de votre configuration initiale dans le gestionnaire de conformité. Ces relations sont illustrées dans la figure suivante.
 
![Relations du score de conformité dans le centre de conformité Microsoft](../media/information-protection-deploy-compliance/information-protection-deploy-compliance-ui.png)

Voici les étapes clés pour vous aider à commencer.

### <a name="1-assessment-templates"></a>1. modèles d’évaluation

À partir du gestionnaire de conformité, la première étape consiste à ajouter des évaluations spécifiques aux réglementations de confidentialité des données d’intérêt et à les inclure dans un groupe défini « réglementations sur la confidentialité des données ».

Les [groupes](../compliance/working-with-compliance-manager.md#groups) sont des conteneurs qui vous permettent d’organiser des évaluations et de partager des informations communes et des tâches de flux de travail entre les évaluations qui ont le même ou les mêmes contrôles gérés par le client. Lorsque deux évaluations différentes dans le même groupe partagent le contrôle géré par le client, l’exécution des détails de l’implémentation, des tests et de l’état du contrôle est automatiquement synchronisée avec le même contrôle dans n’importe quelle autre évaluation dans le groupe. Cette opération unifie les éléments d’action attribués pour chaque contrôle au sein du groupe et réduit le travail de duplication. 

Vous pouvez également choisir d’utiliser des groupes pour organiser. Évaluations par année, zone, norme de conformité ou autres groupements pour faciliter l’organisation de votre travail de conformité.


### <a name="2-action-items"></a>2. actions

Une fois les évaluations ajoutées, vous pouvez afficher les éléments d’action spécifiques à chaque groupe ou chaque réglementation :

- **Liste d’actions d’amélioration.** Accédez à la liste éléments d’action et affichez les actions d’amélioration associées aux réglementations incluses dans le groupe. De nombreuses actions couvrent les réglementations afin qu’un seul élément de liste puisse représenter plusieurs réglementations. 
 
- **Filtrage des actions d’amélioration.** Pour de nombreuses réglementations sur la confidentialité des données et des groupes de réglementations, la liste des actions d’amélioration peut être assez volumineuse, il est donc conseillé de filtrer la liste à l’aide de la liste déroulante des filtres. Par exemple, si vous sélectionnez « contrôles techniques », la liste sera réduite à celles qui disposent d’une implémentation technique au sein de l’organisation, car de nombreuses actions sont liées aux opérations administratives dans divers aspects de l’entreprise qui sont également documentés dans le gestionnaire de conformité. Dans cet article, nous allons nous concentrer sur les contrôles techniques, c’est pourquoi cette approche de filtrage est recommandée.
 
- **Informations supplémentaires et révision.** Pour chaque action, vous pouvez cliquer sur le lien pour **en savoir plus**, ce qui vous permet d’obtenir plus d’informations sur l’activité recommandée, ou sur **Review**, qui ouvre un formulaire qui vous permet d’effectuer les opérations suivantes :
 
   - Affecter l’action à une personne de votre organisation à gérer
   - Gérer les documents liés à l’action de l’action
   - Spécifier l’état de l’élément
   - Spécifier les dates d’implémentation et de test
   - Enregistrer des informations supplémentaires, des notes de mise en œuvre et des notes de plan de test pour l’action d’objet
  
- **Éléments non applicables en dehors de l’étendue.** Certaines actions d’amélioration comprises dans la liste d’actions peuvent ne pas s’appliquer à votre implémentation planifiée. Vous pouvez spécifier qu’ils sont hors de portée dans le gestionnaire de conformité et supprimer l’action et ses preuves du calcul de la valeur du score de conformité. 

Par exemple, si votre organisation a choisi d’utiliser Microsoft Managed Key, il n’est pas recommandé d’utiliser la clé client pour votre déploiement. Dans ce cas, votre organisation marquerait qu’elle **n’est pas dans l’étendue** dans les **actions de contrôle** pour le modèle réglementaire applicable.
 
### <a name="3-controls-info"></a>3. informations sur les contrôles

Pour un affichage spécifique à l’évaluation, affichez les informations relatives aux [contrôles](../compliance/compliance-manager-overview.md#controls) pour chaque groupe d’évaluation. Cela fournit une vue spécifique à l’évaluation, qui est la différence par rapport à la liste d’actions, qui fournit un affichage propre au contrôle technique.
 
![Relations de l’évaluation aux éléments de contrôle](../media/information-protection-deploy-compliance/information-protection-deploy-compliance-control.png)

Accédez à la liste d’informations sur les **contrôles** et affichez la liste des services dans l’étendue pour le règlement en question. 
 
Les groupes de contrôles spécifiques à la réglementation répertorient les actions fournies par le contrôle zone pour chaque domaine de service. Pour chaque ensemble d’actions, le gestionnaire de conformité fournit des informations supplémentaires sur l’action et peut suggérer ou fournir des options de révision pour aider l’organisation dans le choix d’une approche de contrôle.
 
Notez que cette interface permet d’afficher des détails spécifiques à l’action technique, ainsi que le statut des actions associées au contrôle, ainsi que le contexte supplémentaire concernant les réglementations liées à l’action.

### <a name="4-template-download"></a>4. téléchargement de modèle

Pour les personnes les plus familières de l’analyse réglementaire basée sur les feuilles de calcul, une autre approche consiste à télécharger le modèle pour chaque évaluation respective à l’aide de la liste des modèles. Les modèles téléchargés répertorient à la fois les informations de réglementation et de contrôle technique de chaque modèle et peuvent être plus faciles pour certains rôles de naviguer/filtrer et de générer des vues spécifiques de l’entreprise.
 
Vous pouvez également ajouter un nouveau modèle personnalisé pour votre organisation en fonction d’un modèle existant, à l’aide de **Add template**. Pour ce faire, vous devez télécharger un modèle de choix (tel que HIPAA/HI)), puis le modifier à votre guise et le charger à nouveau dans le gestionnaire de conformité, où il doit à présent effectuer des évaluations et des scores similaires aux autres modèles et évaluations dans le cadre du gestionnaire de conformité global et du jeu d’outils de score de conformité.
 
>[!Tip]
>Si vous traitez un grand nombre de règlements ou des actions d’amélioration qui se chevauchent, envisagez de télécharger chaque modèle respectif et de combiner les ensembles de données, en supprimant les actions d’amélioration ou les types de contrôle qui ne s’appliquent pas à votre organisation, et de rechargement. Cette opération peut être plus simple que la navigation dans chaque section d’informations de contrôle et le marquage de chacune d’elles en dehors de l’étendue.
>

## <a name="compliance-score"></a>Score de conformité

Une fois que les évaluations et les spécifications de révision sont effectuées dans le gestionnaire de conformité, vous pouvez accéder à l’outil de [score de conformité](../compliance/compliance-score.md) et passer en revue le score et le secteur, ainsi que la zone de contrôle.

L’outil de score de conformité dans le centre d’administration de conformité Microsoft 365 fournit plusieurs approches pour examiner et filtrer les données de conformité obtenues à partir du gestionnaire de conformité et de différents services Microsoft 365. Cet outil est automatiquement mis à jour lorsque plusieurs paramètres de configuration sont mis en œuvre et partage les signaux avec le score de sécurité Microsoft afin que de nombreuses actions d’amélioration apparaissent dans les deux résultats. 
 
Le score de conformité fournit les éléments suivants :

- Un score collecté, ventilé par Microsoft et les contrôles gérés par le client ;
- Un report des actions d’amélioration et de l’état d’achèvement
- Liste de solutions Microsoft 365 affectant votre score

### <a name="how-the-compliance-score-gets-calculated"></a>Mode de calcul du score de conformité

En bref, le score est calculé en fonction de la combinaison de Microsoft et des implémentations de contrôles gérées par le client, comme expliqué plus en détail dans l' [article de calcul du score de conformité Microsoft](../compliance/compliance-score-methodology.md).

Les contrôles se voient attribuer une valeur de score selon qu’ils sont obligatoires ou discrétionnaires, et s’ils sont préventifs, détectives ou correcteurs. Ces éléments représentent le risque de ne pas les implémenter par rapport à d’autres contrôles.

Comme indiqué dans l’article de calcul du score de conformité Microsoft, les contrôles de prévention obtiennent un meilleur score que le détective et les correcteurs, et les contrôles obligatoires obtiennent un meilleur score que les contrôles discrétionnaires.
 
Notez que l’interface utilisateur de l’administrateur du score de conformité ne répertorie pas ces paramètres et ne permet pas de les filtrer. Toutefois, si vous téléchargez le modèle associé à partir de l’outil Gestionnaire de conformité, le jeu de données résultant répertorie ces paramètres pour la plupart des réglementations.

Pour les contrôles techniques, le score de conformité met automatiquement à jour le score de l’action d’amélioration une fois que la fonctionnalité associée est activée. D’autres actions non techniques, &mdash; telles que celles qui sont opérationnelles ou liées à la documentation, &mdash; doivent être enregistrées manuellement dans l’outil Gestionnaire de conformité sur le portail d’approbation des services. 

Vous pouvez également mettre en œuvre certaines actions d’amélioration à d’autres fins &mdash; , par exemple, à l’aide d’étiquettes de rétention pour des raisons autres que le respect du règlement sur la confidentialité des données &mdash; , afin que vous soyez crédité pour l’utilisation d’une telle fonctionnalité même si elle est utilisée à d’autres fins, et qu’elle ne fait pas partie d’une action de conformité intentionnelle.

Votre score de conformité doit être considéré comme une mesure relative permettant de suivre l’amélioration à grande échelle. Vous ne devez pas suivre un score parfait. 

### <a name="additional-guidance"></a>Conseils supplémentaires

Voici quelques conseils importants pour l’utilisation du score de conformité et du gestionnaire de conformité pour vous permettre de respecter la réglementation relative à la confidentialité des données :

- Chaque règlement sur la confidentialité des données comporte une combinaison de contrôles techniques, de spécifications de documentation et d’exigences opérationnelles, de processus et de création de rapports. Tous ces éléments s’affichent dans les actions d’amélioration. 

- Cet article se concentre sur un sous-ensemble des contrôles techniques spécifiés pour la confidentialité des données dans le gestionnaire de conformité et le score de conformité. Pour plus d’informations sur les contrôles d’administration non techniques, reportez-vous à l’outil et à la [documentation](../compliance/compliance-score.md) du gestionnaire de conformité.

- Pour attirer l’attention sur l’affichage des actions d’amélioration dans votre domaine, vous pouvez filtrer par type d’action dans l’onglet **solutions** de l’administrateur du score de conformité.

- L’importance relative et la priorité des actions d’amélioration identifiées dans le score de conformité doivent être considérées comme faisant partie d’une analyse des risques plus large, ainsi que le risque de confidentialité des données que vous avez déterminé que votre organisation a besoin de gérer. 

- Si vous êtes une organisation globale et que vous ajoutez plusieurs modèles de régulation de confidentialité des données dans le gestionnaire de conformité en tant qu’évaluations, le score de conformité combinera chacun d’eux dans une liste de champs pour chaque action d’amélioration.
 
- Même avec une agrégation des actions d’amélioration pour plusieurs exigences réglementaires, si les modèles d’évaluation de la réglementation pour RGPD, LGPD, CCPA et HIPAA-Hi sont sélectionnés, par exemple, presque 400 les actions d’amélioration seront répertoriées dans le score de conformité. Pour mieux aborder cette longue liste, utilisez le filtre d’action d’amélioration pour réduire le jeu de résultats à une liste plus facile à gérer.

- Le filtre categories permet de filtrer les actions d’amélioration par le biais du regroupement logique, que les articles Track, pretent, Protect, retain et investigation de cette solution globale s’alignent sur. 

- Certains des contrôles répertoriés dans les actions d’amélioration peuvent être considérés plus directement liés à un article réglementaire spécifique, tandis que d’autres contrôles peuvent être plus indirectement associés à l’esprit d’une réglementation et sont de nombreuses choses que vous devez tout de même faire.

