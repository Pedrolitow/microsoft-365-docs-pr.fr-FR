---
title: Augmenter la précision du classifieur
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Découvrez comment augmenter la précision de vos classifieurs
ms.openlocfilehash: 4254571c5b98f18f5c914010d5b2ecd3f814ccd8
ms.sourcegitcommit: 078149c9645ce220911ccd6ce54f984a4c92ce53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67812618"
---
# <a name="increase-classifier-accuracy-preview"></a>Augmenter la précision du classifieur (préversion)

Les classifieurs, tels que les [types d’informations sensibles](sensitive-information-type-learn-about.md) (SIT) et [les classifieurs pouvant être formés, sont utilisés](classifier-learn-about.md) dans différents types de stratégies pour identifier les informations sensibles. Comme tous les modèles, ils identifient parfois un élément comme étant sensible qui ne l’est pas. Ou parfois qui n’identifient pas un élément comme étant sensible quand il l’est réellement. Ils sont appelés faux positifs et faux négatifs. 

Cet article vous montre comment vérifier si les éléments mis en correspondance par un classifieur sont vrais positifs **(correspondance)** ou faux positifs (**non une correspondance**) et fournir la **correspondance**, ou **non un** commentaire de correspondance. Vous pouvez utiliser ces commentaires pour ajuster vos classifieurs afin d’augmenter la précision. Vous pouvez également envoyer des versions expurgées du document ainsi que les commentaires **Match**, **Not a Match** à Microsoft si vous souhaitez améliorer la précision des classifieurs que Microsoft fournit. 

L’expérience **Match**, **Not a match** est disponible dans :

- Explorateur de contenu
- Page Éléments correspondants du type d’informations sensibles
- Page Éléments correspondants du classifieur pouvant être formé
- page Alertes Protection contre la perte de données Microsoft Purview (DLP)

## <a name="applies-to"></a>S’applique à

|Classifieur |Résumé contextuel| Panneau Aperçu expurgé| Correspondance et non correspondance|  
|---------|---------|---------|---------|
|S' asseoir     |Oui| Oui|Oui|
|SIT personnalisé  | Oui|Non | Oui|
|SIT d’empreinte digitale| Non|Non|Oui|
|Correspondance exacte des données SIT|Non|Non|Non|
|Entités nommées| Non| Non| Non|
|Classifieurs trainables intégrés|Non| Oui| Oui|
|Classifieur pouvant être entraîné personnalisé |Non| Non| Oui|

> [!IMPORTANT]
> L’expérience de commentaires de correspondance/non-correspondance prend en charge les éléments des sites SharePoint Online, des sites OneDrive Entreprise et des e-mails dans Exchange Online.

## <a name="licensing-and-subscriptions"></a>Licences et abonnements

Consultez les [exigences de licence pour l’analytique de la classification des données : Vue d’ensemble du contenu & l’Explorateur d’activités](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

## <a name="known-limitations-for-this-preview"></a>Limitations connues pour cette préversion

- Le résumé contextuel n’affiche qu’un nombre limité de correspondances dans un élément donné, et non toutes les correspondances.
- Le résumé contextuel et l’expérience de commentaires sont disponibles uniquement pour les éléments créés ou mis à jour après l’activation de l’expérience de commentaires pour le locataire. Les éléments qui ont été classés avant l’activation de la fonctionnalité peuvent ne pas avoir le résumé contextuel et l’expérience de commentaires disponibles.

## <a name="how-to-evaluate-match-accuracy-and-provide-feedback"></a>Comment évaluer la précision des correspondances et fournir des commentaires

L’expérience récapitulative contextuelle dans laquelle vous indiquez si un élément mis en correspondance est un vrai positif (**Correspondance**) ou un faux positif (**non une correspondance**) est similaire, quel que soit l’emplacement des surfaces.

> [!IMPORTANT]
> Vous devez avoir déjà déployé des stratégies DLP qui utilisent sit ou classifieur pouvant être formé sur des sites OneDrive, des sites SharePoint ou des boîtes aux lettres Exchange et des correspondances d’éléments avant de voir les éléments dans la page **résumé contextuelle** .

### <a name="using-content-explorer"></a>Utilisation de l’Explorateur de contenu

Cet exemple montre comment utiliser l’onglet **Résumé contextuel** pour envoyer des commentaires.

1. Ouvrez la page **de** **l’Explorateur** de contenu de classification  >  portail de conformité Microsoft Purview  > **Data**.
1. Tapez le nom du classifieur SIT ou pouvant être formé pour lequel vous souhaitez vérifier les correspondances dans **Filtrer sur les étiquettes, les types d’informations ou les catégories**.
1. Sélectionnez le SIT.
1. Sélectionnez l’emplacement. Vérifiez qu’il existe une valeur différente de zéro dans la colonne **Fichier** .
1. Ouvrez le dossier et sélectionnez un document.
1. Sélectionnez le lien dans la colonne **type d’informations sensibles** d’un élément pour voir les SIT correspondant à l’élément et le [niveau de confiance](/microsoft-365/compliance/sensitive-information-type-learn-about.md#more-on-confidence-levels).
1. Sélectionner **Fermer**
1. Ouvrez un élément et **développez la page Résumé contextuel** . Sélectionnez l’onglet **Résumé contextuel** .
1. Examinez l’élément et vérifiez s’il s’agit d’une correspondance.
1. S’il s’agit d’une correspondance, sélectionnez **Fermer**. Vous avez terminé.
1. FACULTATIF : Sélectionnez **J’accepte de fournir une copie du fichier à Microsoft** si vous souhaitez envoyer les commentaires de correspondance à Microsoft et sélectionner **Envoyer à Microsoft.**
1. S’il ne s’agit pas d’une correspondance, sélectionnez les points de suspension en regard de **Fermer** , puis **sélectionnez Retirer les commentaires**.
1. Sélectionnez **non une correspondance**.
1. Passez en revue l’élément et réactez ou annulez tout texte.
1. Facultatif : **sélectionnez J’accepte de fournir une copie du fichier à Microsoft** si vous souhaitez envoyer les commentaires à Microsoft et sélectionner **Envoyer à Microsoft**.
1. Sélectionnez **Fermer**.

Si vous décidez ultérieurement que les commentaires de non-correspondance sont incorrects, vous pouvez sélectionner le bouton **Retirer les commentaires** . Cela replace l’élément dans la page **Non une correspondance**, **Correspondance** .

### <a name="using-sensitive-information-type-matched-items-page"></a>Page Utilisation d’éléments correspondants de type d’informations sensibles

Vous pouvez accéder aux mêmes mécanismes de commentaires dans la page **Types d’informations sensibles** .

1. Ouvrez la page des **types d’informations sensibles** de **la classification** >  **portail de conformité Microsoft Purview** >  Data.
1. Tapez le nom du SIT dont vous souhaitez vérifier la précision dans  **La recherche**.
1. Ouvrez le SIT. L’onglet **Vue d’ensemble** s’affiche. Vous pouvez voir ici le nombre d’éléments qui correspondent, le nombre d’éléments qui ne correspondent pas et le nombre d’éléments avec commentaires.
1. Sélectionnez l’onglet **Éléments mis en correspondance** .
1. Ouvrez le dossier et sélectionnez un document.
1. Sélectionnez le lien dans la colonne **type d’informations sensibles** d’un élément pour voir les SIT correspondant à l’élément et le [niveau de confiance](/microsoft-365/compliance/sensitive-information-type-learn-about.md#more-on-confidence-levels).
1. Sélectionnez **Fermer**.
1. Ouvrez un élément et **développez la page Résumé contextuel** . Sélectionnez l’onglet **Résumé contextuel** .
1. Examinez l’élément et vérifiez s’il s’agit d’une correspondance.
1. S’il s’agit d’une correspondance, sélectionnez **Fermer**. Vous avez terminé.
1. S’il ne s’agit pas d’une correspondance, sélectionnez les points de suspension en regard de **Fermer** , puis **sélectionnez Retirer les commentaires**. Cela expose le bouton **Non une correspondance** .
1. Sélectionnez le bouton **Non une correspondance** .
1. Passez en revue l’élément et réactez ou annulez tout texte.
1. Facultatif : **sélectionnez J’accepte de fournir une copie du fichier à Microsoft** si vous souhaitez envoyer les commentaires à Microsoft et sélectionner **Envoyer à Microsoft**.
1. Sélectionnez **Fermer**.

Si vous décidez ultérieurement que les commentaires de non-correspondance sont incorrects, vous pouvez sélectionner le bouton **Retirer les commentaires** . Cela replace l’élément dans la page **Non une correspondance**, **Correspondance** .

### <a name="using-trainable-classifier-matched-items-page"></a>Utilisation de la page Éléments correspondants du classifieur pouvant être formé

1. Ouvrez la page **classifieurs portail de conformité Microsoft Purview** >  **Data classification** > **Trainable**.
1. Sélectionnez le classifieur pouvant être entraîné dont vous souhaitez vérifier la précision.
1. Ouvrez le classifieur pouvant être formé. L’onglet **Vue d’ensemble** s’affiche. Vous pouvez voir ici le nombre d’éléments qui correspondent, le nombre d’éléments qui ne correspondent pas et le nombre d’éléments avec commentaires.
1. Sélectionnez l’onglet **Éléments mis en correspondance** .
1. Ouvrez le dossier et ouvrez un document.
1.Ouvrez un élément et **développez la page Résumé contextuel** .
1. Examinez l’élément et vérifiez s’il s’agit d’une correspondance.
1. S’il s’agit d’une correspondance, sélectionnez **Fermer**. Vous avez terminé.
1. S’il ne s’agit pas d’une correspondance, sélectionnez **Retirer les commentaires**. Cela expose **le bouton Non une correspondance** .
1. Sélectionnez le bouton **Non une correspondance** .
1. Sélectionnez **Fermer**.

Si vous décidez ultérieurement que les commentaires de non-correspondance sont incorrects, vous pouvez sélectionner le bouton **Retirer les commentaires** . Cela replace l’élément dans la page **Non une correspondance**, **Correspondance** .

### <a name="using-data-loss-prevention-alerts-page"></a>Page Utilisation des alertes de protection contre la perte de données

1. Ouvrez la page **portail de conformité Microsoft Purview** >  **Data loss prevention** > **alerts**.
1. Sélectionnez une alerte pour un élément qui a été créé ou mis à jour après l’activation de la fonctionnalité **Match**/**not a Match** pour votre locataire.
1. Sélectionnez **Afficher les détails**.
1. Sélectionnez l’onglet **Événements** .
1. Sélectionnez l’onglet **Résumé contextuel** .
1. Examinez l’élément et vérifiez s’il s’agit d’une correspondance.
1. S’il s’agit d’une correspondance, sélectionnez **Fermer**. Vous avez terminé.
1. S’il ne s’agit pas d’une correspondance, sélectionnez **Actions** et **Non une correspondance**.
1. Passez en revue l’élément et réactez ou annulez tout texte.
1. Facultatif : **sélectionnez J’accepte de fournir une copie du fichier à Microsoft** si vous souhaitez envoyer les commentaires à Microsoft et sélectionner **Envoyer à Microsoft**.
1. Sélectionnez **Fermer**.

## <a name="using-the-feedback-to-tune-your-classifiers"></a>Utilisation des commentaires pour paramétrer vos classifieurs

Si vos classifieurs SIT ou formable retournent trop de faux positifs en fonction des commentaires, vous pouvez essayer certaines de ces étapes pour les régler et augmenter la précision. 

### <a name="trainable-classifiers"></a>Classifieurs avec capacité d’apprentissage

Suivez les étapes de [la procédure de reformation d’un classifieur dans l’Explorateur de contenu](classifier-how-to-retrain-content-explorer.md) pour augmenter la précision d’un classifieur pouvant être formé.

### <a name="sensitive-information-types"></a>Types d’informations sensibles
 
Si vous constatez de grandes quantités de faux positifs, utilisez ces recommandations pour affiner vos SIT :

- Augmentez les seuils des types d’informations sensibles détectés pour déterminer la gravité. Il est possible d’utiliser différents seuils pour les classifieurs individuels

- Comprendre les niveaux de confiance et la façon dont ils sont définis. Essayez d’utiliser une confiance faible avec un nombre d’instances élevé ou un niveau de confiance plus élevé avec un faible nombre d’instances.

- Clonez et modifiez les SIT intégrés pour inclure d’autres conditions, telles que des mots clés, une correspondance plus stricte des valeurs ou des exigences de mise en forme plus strictes.

- Modifiez un SIT personnalisé pour exclure les préfixes, suffixes ou modèles connus. Par exemple, un SIT personnalisé pour détecter les numéros de téléphone peut se déclencher pour chaque e-mail si vos signatures de courrier électronique ou en-têtes de document incluent des numéros de téléphone. L’exclusion des séquences de numéros de téléphone de vos organisations communes en tant que préfixes à votre sit personnalisé peut empêcher la règle de se déclencher pour chaque e-mail ou document.

- Incluez d’autres SIT basés sur des dictionnaires comme conditions pour limiter les correspondances à celles qui parlent des articles pertinents. Par exemple, une règle de correspondance des diagnostics des patients peut être améliorée en exigeant la présence de mots tels que diagnostic, diagnostic, état, symptôme et patient.

- Pour un SIT d’entité nommé, comme **Tous les noms complets**, il est préférable de définir un seuil de nombre d’instances plus élevé, comme 10 ou 50. Si les noms de personnes et les SSN sont détectés ensemble, il est plus probable que les SSN soient vraiment des SSN, et nous réduisons le risque que la stratégie ne se déclenche pas, car un nombre insuffisant de SSN est détecté.