---
title: Procédure de recyclage d’un classifieur dans l’Explorateur de contenu
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment fournir des commentaires à un classifieur de formation dans l’Explorateur de contenu.
ms.openlocfilehash: 786ebb682e9cdd96c0c6503294bd4f316f777f68
ms.sourcegitcommit: 54d1a2f363b2d5b63aae258c3cec0573a08f2866
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49752621"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Procédure de recyclage d’un classifieur dans l’Explorateur de contenu

Un classificateur Microsoft 365 pouvant être formé est un outil que vous pouvez former afin de reconnaître différents types de contenu en leur donnant des exemples à consulter. Une fois l’apprentissage effectué, vous pouvez l’utiliser pour identifier un élément pour l’application des étiquettes de sensibilité d’Office, des stratégies de conformité des communications et des stratégies d’étiquette de rétention.

Cet article vous explique comment améliorer les performances des classifieurs de formation personnalisée et de certains classifieurs pré-formés en leur fournissant des commentaires supplémentaires.

Pour en savoir plus sur les différents types de classifieurs, reportez-vous à la rubrique [en savoir plus sur les classifieurs de formation](classifier-learn-about.md).

## <a name="permissions"></a>Autorisations

Pour accéder aux classifieurs dans le centre de conformité Microsoft 365 :

- le rôle d’administrateur de conformité ou l’administrateur des données de conformité est requis pour former un classifieur

Vous aurez besoin de comptes dotés des autorisations suivantes pour utiliser les classifieurs dans les scénarios suivants :

- Scénario de stratégie d’étiquette de rétention : rôles de gestion des enregistrements et de rétention 

## <a name="overall-workflow"></a>Flux de travail global

> [!IMPORTANT]
> Vous fournissez des commentaires dans l’Explorateur de contenu pour appliquer automatiquement des stratégies d’étiquette de rétention aux éléments Exchange et utilise le classifieur comme condition. **Si vous n’avez pas de stratégie de rétention qui applique automatiquement une étiquette de rétention aux éléments Exchange et utilise un classifieur comme condition, arrêtez-vous ici.**

Lorsque vous utilisez vos classifieurs, vous souhaiterez peut-être augmenter la précision des classifications qu’ils effectuent. Pour ce faire, vous évaluez la qualité des classifications effectuées pour les éléments qu’il a identifiés comme étant une correspondance ou non. Une fois que vous avez effectué 30 évaluations pour un classifieur, il effectue ces commentaires et proveille lui-même automatiquement.

Pour en savoir plus sur le flux de travail global de recyclage d’un classifieur, consultez la rubrique [processus Flow for Retraining a classificateur](classifier-learn-about.md#retraining-classifiers).

> [!NOTE]
> Un classifieur doit déjà être publié et en cours d’utilisation avant de pouvoir être reformé.

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>Procédure de recyclage d’un classifieur dans l’Explorateur de contenu

1. Connectez-vous au centre de conformité Microsoft 365 avec l’administrateur de conformité ou l’accès au rôle d’administrateur de sécurité et ouvrez l’Explorateur de contenu classification des données du **Centre de conformité Microsoft 365**  >    >  . 
2. Sous la liste **filtre sur les étiquettes, les types d’informations ou les catégories** , développez **classifieurs de formation**.

> [!IMPORTANT]
> Il peut falloir jusqu’à huit jours pour que les éléments agrégés apparaissent sous l’en-tête des classifieurs.

3. Sélectionnez le classificateur pilotable que vous avez utilisé dans la stratégie d’étiquette de rétention auto-appliquée. Il s’agit du classificateur de formation sur lequel vous allez donner votre avis.

> [!NOTE]
> Si un élément a une entrée dans la colonne **étiquette de rétention** , cela signifie que l’élément a été classé comme un `match` .  Si un élément n’a pas d’entrée dans la colonne **étiquette de rétention** , cela signifie qu’il a été classé comme un `close match` . Vous pouvez améliorer la précision de classifieur le plus en fournissant des commentaires sur des `close match` éléments. 

4. Choisissez un élément et ouvrez-le.
 
 > [!TIP]
> Vous pouvez envoyer vos commentaires sur plusieurs éléments simultanément en les sélectionnant, puis en choisissant **améliorer la classification** dans la barre de commandes.

5. Choisissez **fournir des commentaires**.
6. Dans le volet **commentaires détaillés** , si l’élément est un vrai positif, choisissez, **faire correspondre**.  S’il s’agit d’un faux positif, c’est qu’il était incorrectement inclus dans la catégorie, **ne choisira pas de correspondance**.
7. S’il existe un autre classifieur plus approprié pour l’élément, vous pouvez le sélectionner dans la liste **suggérer d’autres classifieurs de formation** . Cette opération déclenche l’évaluation de l’élément par l’autre classifieur.
8. Sélectionnez **Envoyer des commentaires** pour envoyer votre évaluation de `match` , `not a match` classifications et suggérer d’autres classifieurs de formation. Une fois que vous avez fourni 30 instances de commentaires à un classifieur, il est automatiquement retrainé. La reformation peut prendre entre une et quatre heures. Les classifieurs ne peuvent être reformés qu’une fois par jour.

> [!IMPORTANT]
> Ces informations sont dirigées vers le classificateur de votre client, **qui ne revient pas à Microsoft**.

9. Ouvrez les **classifieurs avec apprentissage**.
10. Le classifieur qui a été utilisé dans votre stratégie de conformité des communications apparaît sous le titre **nouvelle formation** .

![classifieur dans l’état de la reformation](../media/classifier-retraining.png)

11. Une fois la reformation terminée, sélectionnez le classifieur pour ouvrir la vue d’ensemble de la formation.

![vue d’ensemble des résultats de la formation du classifieur](../media/classifier-retraining-overview.png)

12. Examinez l’action recommandée, ainsi que les comparaisons de prédiction des versions reformation et actuellement publiées du classifieur.
13. Si vous êtes satisfait du résultat de la nouvelle formation, choisissez **republier**.
14. Si vous n’êtes pas satisfait du résultat de la nouvelle formation, vous pouvez choisir de fournir des commentaires supplémentaires au classifieur dans l’interface de conformité des communications et d’entamer un autre cycle de recyclage ou de ne rien faire, auquel cas la version actuellement publiée du classifieur continuera à être utilisée. 

## <a name="details-on-republishing-recommendations"></a>Détails sur les recommandations de republication

Voici quelques informations sur la formulation de la recommandation pour republier un classifieur de nouvelle formation ou suggérer une nouvelle formation. Cela nécessite un peu plus de compréhension de la façon dont fonctionnent les classifieurs.

Après un recyclage, nous évaluons les performances du classifieur sur les éléments à l’aide de commentaires, ainsi que sur les éléments initialement utilisés pour former le classifieur. 

- Pour les modèles intégrés, les éléments utilisés pour former le classifieur sont les éléments utilisés par Microsoft pour créer le modèle.
- Pour les modèles personnalisés, les éléments utilisés lors de la formation d’origine le classifieur proviennent des sites que vous avez ajoutés à des fins de test et de révision.

Nous comparons les numéros de performances des deux ensembles d’éléments pour le classificateur reformé et publié afin de fournir une recommandation quant à la nécessité de republier. 

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les classifieurs de formation](classifier-learn-about.md)
- [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
