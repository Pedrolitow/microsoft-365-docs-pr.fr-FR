---
title: Score de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Le score de conformité Microsoft aide les organisations à simplifier et à automatiser les évaluations des risques et suggère des actions recommandées pour résoudre les risques.
ms.openlocfilehash: 3c7a4bdfd5de7a9a6dcbede5146ebb517acdb4bb
ms.sourcegitcommit: 56772bed89516cebc5eb370e292ccfbb4889cb38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44330798"
---
# <a name="microsoft-compliance-score-preview"></a>Score de conformité Microsoft (aperçu)

Le [score de conformité Microsoft](https://compliance.microsoft.com/compliancescore) contribue à simplifier la gestion de la conformité et à réduire les risques de conformité grâce à une expérience conviviale. Le score de conformité est disponible pour la préversion publique dans le [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md).

**Dans cet article :** Lisez cet article pour comprendre le score de conformité et comment le configurer pour votre organisation.

**En savoir plus sur les mises à jour :** Nous avons publié plusieurs mises à jour dans la version d’avril 2020. Consultez les [notes de publication du score de conformité](compliance-score-release-notes.md) pour découvrir les problèmes nouveaux et connus liés à la version d’évaluation du score de conformité.

## <a name="what-is-compliance-score"></a>Qu’est-ce que le score de conformité

Microsoft Compliance score est une fonctionnalité d’aperçu dans le centre de conformité Microsoft 365 pour vous aider à comprendre la position de la conformité de votre organisation. Il calcule un score basé sur les risques mesurant votre progression dans la réalisation d’actions qui contribuent à réduire les risques liés à la protection des données et aux normes réglementaires.

Vous pouvez utiliser le score de conformité comme un outil permettant de suivre toutes vos évaluations de risques. Il fournit des fonctionnalités de flux de travail pour vous aider à effectuer efficacement les évaluations des risques par le biais d’un outil courant.

Si vous utilisez actuellement le [Gestionnaire de conformité](compliance-manager-overview.md), vous remarquerez que le score de conformité est désormais une fonctionnalité autonome avec un design plus simple et plus convivial pour vous aider à gérer plus facilement la conformité. 

La page principale du score de conformité est votre tableau de bord personnalisé. Il indique votre score actuel, vous aide à voir ce qui vous convient et vous guide sur les actions à effectuer pour améliorer votre score. Votre tableau de bord de score de conformité doit ressembler à ceci :

![Score de conformité-tableau de bord](../media/compliance-score-dashboard.png "Tableau de bord de score de conformité")

### <a name="simplified-compliance-management"></a>Gestion simplifiée de la conformité

Le score de conformité simplifie la gestion de la conformité en fournissant les éléments suivants :

- **Évaluations continues**: analyse automatiquement les environnements Microsoft 365 afin de détecter et de surveiller l’efficacité des contrôles de protection des données dans votre système.
- **Actions recommandées**: fournit des recommandations et des instructions pas à pas pour la mise en œuvre de contrôles afin d’optimiser votre score
-  **Mappage de contrôle intégré**: vous permet de rester au fait des dernières évolutions du paysage de conformité grâce à une infrastructure de contrôle commune intégrée

> [!IMPORTANT]
> Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme une garantie de conformité. Il vous revient d’évaluer et de valider l’efficacité des contrôles client selon votre environnement réglementaire. Ces services sont actuellement en version préliminaire et soumis aux conditions des [services en ligne](https://go.microsoft.com/fwlink/?linkid=2108910). Consultez également [les conseils Microsoft 365 sur les licences pour la sécurité et la conformité](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="relationship-to-compliance-manager"></a>Relation avec le gestionnaire de conformité

Considérez le score de conformité comme une version simplifiée du gestionnaire de conformité. Bien que les deux outils existants soient distincts mais encore intégrés, le score de conformité permet de surveiller plus facilement la position globale de votre conformité et de prendre des mesures pour l’améliorer.

Le score de conformité partage le même serveur principal avec le gestionnaire de conformité, de sorte que toutes les données que vous avez peut-être déjà dans le gestionnaire de conformité seront affichées dans le score de conformité.

Certaines fonctionnalités demeurent uniquement dans le gestionnaire de conformité lors de la préversion publique, comme la gestion des évaluations et la création de modèles. Nous vous recommandons de commencer toutes les activités de gestion de la conformité dans le score de conformité. Lorsque vous accédez à des fonctions gérées par le gestionnaire de conformité, vous serez guidé vers cet outil. Pour cette raison, une partie de cette documentation vous dirige vers les rubriques du gestionnaire de conformité.

En savoir plus sur la relation entre le score de conformité et le gestionnaire de conformité dans les [notes de publication du score de conformité](compliance-score-release-notes.md).

## <a name="understanding-your-score"></a>Présentation de votre score

Le score de conformité vous donne un score initial basé sur la base de données de protection des données Microsoft 365. Il s’agit d’un groupe de contrôles qui inclut les réglementations et normes courantes dans le secteur. Bien que ce score constitue un point de départ approprié pour évaluer votre position de conformité, le score de conformité devient plus puissant une fois que vous avez ajouté des évaluations qui sont plus pertinentes pour votre organisation.

Par exemple, si votre organisation appartient au secteur financier, vous souhaiterez peut-être ajouter l’évaluation FFIEC. Si votre organisation appartient au secteur de la santé, vous pouvez ajouter l’évaluation HIPAA/Hi-Tech. Découvrez comment [Ajouter des évaluations dans le gestionnaire de conformité](working-with-compliance-manager.md#assessments).

En savoir plus sur [la façon dont votre score de conformité est calculé et surveillé en continu](compliance-score-methodology.md).


## <a name="key-components-controls-assessments-templates-groups"></a>Composants clés : contrôles, évaluations, modèles, groupes

Le score de conformité utilise plusieurs composants pour vous aider à gérer vos activités de conformité. Lorsque vous utilisez le score de conformité pour affecter, tester et surveiller les activités de conformité, il est utile de comprendre les principaux composants : contrôles, évaluations, modèles et groupes.

### <a name="controls"></a>Contrôles

Un contrôle définit le mode d’évaluation et de gestion de la configuration du système, du processus organisationnel et des personnes chargées de répondre à une exigence spécifique d’un règlement, d’une stratégie standard ou d’une stratégie interne.

Le score de conformité effectue le suivi de deux types de contrôles :

1. **Contrôles gérés par Microsoft**: contrôles pour les services de Cloud Computing Microsoft, que Microsoft est responsable de l’implémentation
2. **Contrôles gérés**par le client : contrôles gérés par votre organisation, que vous êtes responsable de l’implémentation
 
### <a name="assessments"></a>Évaluations

Une évaluation est une évaluation d’un modèle qui lance le processus de notation pour votre organisation. Les évaluations regroupent les actions nécessaires pour répondre aux exigences d’une norme, d’une réglementation ou d’une loi. Par exemple, vous pouvez avoir une évaluation qui, lorsque vous terminez toutes les actions qu’elle contient, présente vos paramètres Office 365 conformément à la configuration ISO 27001 requise.

Le score de conformité fournit à votre organisation une évaluation initiale basée sur la base de données de protection des données Microsoft 365. Cette évaluation est une recommandation permettant de réduire les risques de protection et de conformité des données ([en savoir plus](compliance-score-methodology.md#initial-score-based-on-microsoft-365-data-protection-baseline)).

Les évaluations comportent plusieurs composants :

- **Services dans l’étendue**: l’ensemble spécifique des services Microsoft applicables à l’évaluation
- **Contrôles gérés par Microsoft**: contrôles mis en œuvre et testés par Microsoft
- **Contrôles gérés par le client**: contrôles que vous gérez
- **Score d’évaluation**: pourcentage des points obtenus en effectuant des actions au sein de cette évaluation

> [!NOTE]
> Le score de conformité affiche vos évaluations et la façon dont elles font partie de votre score global. Toutefois, pendant la préversion publique, vous serez dirigé vers le gestionnaire de conformité pour gérer vos évaluations.

Affichez les instructions détaillées pour [la gestion des évaluations dans le gestionnaire de conformité](working-with-compliance-manager.md#assessments).

### <a name="templates"></a>Modèles

Le score de conformité fournit des modèles préconfigurés pour les évaluations. Vous pouvez également créer une évaluation personnalisée en ajoutant vos propres contrôles et actions à un modèle préconfiguré. Par exemple, vous pouvez créer un modèle pour votre contrôle de processus d’entreprise ou un modèle pour une norme de conformité et de protection des données régionale qui n’est pas couverte par l’un des modèles préconfigurés. En plaçant vos propres modèles dans le score de conformité, vous pouvez suivre non seulement les évaluations de Microsoft Cloud, mais également d’autres évaluations des risques dans l’étendue de votre organisation.

Les modèles préconfigurés pour le score de conformité sont les suivants :

1. [Loi sur la protection générale des données du Brésil (LGPD)](https://go.microsoft.com/fwlink/?linkid=2115387)
2. [California Consumer Privacy Act (CCPA)](https://go.microsoft.com/fwlink/?linkid=2108871) (aperçu)
3. [Matrice de contrôles Cloud CSA (Cloud Security Alliance) 3.0.1](https://go.microsoft.com/fwlink/?linkid=2109076)
4. [Résolution de la sécurité des informations de Dubaï (DGISR)](https://go.microsoft.com/fwlink/?linkid=2131193)
5. [RGPD de l’Union européenne](https://go.microsoft.com/fwlink/?linkid=2108870)
6. [Livret de sécurité des informations sur les institutions financières fédérales (FFIEC)](https://go.microsoft.com/fwlink/?linkid=2109077)
7. [FedRAMP modéré](https://go.microsoft.com/fwlink/?linkid=2108869)
8. [HIPAA](https://go.microsoft.com/fwlink/?linkid=2109078)  /  [Hi-Tech](https://go.microsoft.com/fwlink/?linkid=2109079)
9. [IRAP](https://go.microsoft.com/fwlink/?linkid=2113709)  /  [Australian Government ISM](https://go.microsoft.com/fwlink/?linkid=2113024) (Preview)
10. [ISO 27001:2013](https://go.microsoft.com/fwlink/?linkid=2109073)
11. [ISO 27018:2014](https://go.microsoft.com/fwlink/?linkid=2109074)
12. [ISO 27701:2019](https://go.microsoft.com/fwlink/?linkid=2113025)
13. [Base de données de protection des données Microsoft 365](compliance-score-methodology.md#initial-score-based-on-microsoft-365-data-protection-baseline)
14. [NIST 800-53 rév. 4](https://go.microsoft.com/fwlink/?linkid=2109075)
15. [NIST 800-171](https://go.microsoft.com/fwlink/?linkid=2108867)
16. [Infrastructure NIST Cybersecurity (CSF)](https://go.microsoft.com/fwlink/?linkid=2108868)
17. [SOC 1](https://go.microsoft.com/fwlink/?linkid=2115184)
18. [SOC 2](https://go.microsoft.com/fwlink/?linkid=2115184)

Affichez [des instructions détaillées sur la création de modèles](working-with-compliance-manager.md#templates), qui se produit dans le gestionnaire de conformité.

### <a name="groups"></a>Groupes

Les groupes vous permettent d’organiser des évaluations de manière logique. Par exemple, vous pouvez choisir de regrouper les évaluations par année, standard de conformité, service, teams au sein de votre organisation ou une autre méthode.

Lorsque deux évaluations différentes dans le même groupe partagent des actions gérées par le client, les mises à jour effectuées dans les détails de l’implémentation, les tests et l’état de l’action dans une évaluation sont automatiquement synchronisées avec la même action dans toute autre évaluation du groupe. La synchronisation des actions de cette manière unifie les actions d’amélioration affectées dans le groupe et réduit le travail de duplication.

Découvrez comment [créer des groupes dans le gestionnaire de conformité](working-with-compliance-manager.md#groups). Une fois que vous avez créé des groupes, vous pouvez [filtrer votre tableau de bord de score de conformité](compliance-score-setup.md#filtering-your-dashboard-view) pour afficher votre score par un ou plusieurs groupes.

## <a name="next-step-begin-setup"></a>Étape suivante : début de l’installation

Découvrez comment vous connecter, configurer des autorisations et configurer des vues de tableau de bord et de tableau de bord lors de [la configuration du score de conformité](compliance-score-setup.md).
