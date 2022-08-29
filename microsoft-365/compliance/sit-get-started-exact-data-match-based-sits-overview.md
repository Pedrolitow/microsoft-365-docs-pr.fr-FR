---
title: Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Obtenez une vue d’ensemble de la création de types d’informations sensibles basés sur des correspondances de données exactes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a9fc1af50c329b96ff77108698c8bbf952813f7f
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67359489"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes

## <a name="applies-to"></a>S’applique à 

- [Nouvelle expérience](sit-create-edm-sit-unified-ux-workflow.md)
- [Expérience classique](sit-create-edm-sit-classic-ux-workflow.md)

La création et la mise à disposition d’un type d’informations sensibles basé sur EDM (EDM) sont un processus en plusieurs phases. Vous pouvez utiliser la *nouvelle expérience* de *l’expérience classique*  existante ou via PowerShell. Cet article vous aide à comprendre les différences entre les deux expériences et vous aide à choisir la bonne pour vos besoins.

Les SIT EDM peuvent être utilisés dans :

- Protection contre la perte de données Microsoft Purview
- Étiquetage automatique (côté service et côté client)
- Gestion des risques internes Microsoft Purview stratégies
- Microsoft Purview eDiscovery
- Microsoft Purview : gestion des risques internes
- Microsoft Defender for Cloud Apps



## <a name="before-you-begin"></a>Avant de commencer

Familiarisez-vous avec les concepts et la terminologie de ces articles :

- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md).
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md)

## <a name="supported-regions"></a>Régions prises en charge

La correspondance exacte des données est disponible dans les régions suivantes :

- Asie-Pacifique
- Australie
- Brésil
- Canada
- Europe
- France
- Allemagne
- Inde
- Japon
- Corée
- Norvège
- Afrique du Sud
- Suisse
- Émirats arabes unis
- Royaume-Uni
- États-Unis
- DoD des États-Unis
- GCC des États-Unis
- US GCCH

Vous pouvez déterminer la région dans laquelle votre locataire héberge les données au repos en suivant les procédures décrites dans [l’emplacement où sont stockées vos données client Microsoft 365](../enterprise/o365-data-locations.md) et en faisant référence aux emplacements de la ville du centre de données dans le même article.

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Pour effectuer les tâches décrites dans cet article, vous devez être un administrateur général, un administrateur de conformité ou un administrateur Exchange Online. Pour en avoir plus sur les autorisations DLP, consultez la section[Autorisations](data-loss-prevention-policies.md#permissions).

Consultez la [description du service de protection contre la perte de données](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) pour obtenir des informations complètes sur les licences

## <a name="portal-links-for-your-subscription"></a>Liens vers les portails de votre abonnement

|Portail|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Portail Microsoft 365 Defender|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Portail de conformité Microsoft Purview|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="new-edm-experience"></a>Nouvelle expérience EDM

La nouvelle expérience EDM combine les fonctionnalités du schéma EDM et des assistants de types d’informations sensibles EDM dans une expérience utilisateur unique. La nouvelle expérience ajoute :

### <a name="simplified-workflow"></a>Flux de travail simplifié

Avec la nouvelle expérience, le schéma et sit sont créés via une expérience utilisateur, ce qui signifie moins de clics, de meilleures instructions sur le mappage des éléments principaux aux SIT par défaut et des niveaux de confiance par défaut pour les règles.

Lorsque vous devez voir l’état d’un sit EDM dans le processus de création, la nouvelle expérience le signale dans l’interface utilisateur.

- Données non encore chargées
- Pourcentage de chargement des données
- Chargement des données terminé
- Indexation terminée
- Échec du chargement des données
- Échec de l’indexation des données


### <a name="automated-schema-and-sit-creation"></a>Schéma automatisé et création SIT

Dans la nouvelle expérience, vous pouvez fournir au système un exemple de fichier de données qui a les mêmes valeurs d’en-tête et suffisamment de lignes (10 à 20) de données représentatives. Le système valide le format et crée le schéma en fonction des en-têtes. Vous identifiez ensuite les champs principaux dans le schéma et le système recommande les SIT qui correspondent le mieux à l’associer au champ principal. Si vous ne souhaitez pas charger le fichier, vous pouvez entrer les mêmes valeurs manuellement dans l’interface utilisateur.

> [!IMPORTANT]
> Veillez à utiliser des exemples de valeurs de données qui ne sont pas sensibles, mais qui sont au même format que vos données sensibles réelles. L’utilisation de données non sensibles est essentielle, car l’exemple de fichier de données n’est pas chiffré et haché lorsque vous le chargez comme le fait la table d’informations sensibles réelle. Les données de l’exemple de fichier de données ne sont pas conservées ou accessibles une fois le sit EDM créé.

Le système génère les règles de détection SIT EDM, une pour chaque champ principal. En fonction de la détection des champs principaux, le système crée des règles de confiance élevée et moyenne en utilisant tous les autres champs comme preuve corroborante. Vous pouvez ajouter des règles de faible confiance si vous le souhaitez. 

### <a name="additional-guardrails-to-ensure-better-performance"></a>Garde-fous supplémentaires pour garantir de meilleures performances

<!--As the Azure-based EDM cloud service leverages a shared infrastructure, a misconfigured EDM SIT that triggers excessive EDM lookups could impact EDM performance for other customers if it wasn't controlled. This is prevented by throttling instances where EDM is misconfigured in a way that would cause excessive lookups.--> 

Le système vous avertit s’il trouve un champ principal mappé à un SIT qui détecte un large éventail de valeurs, appelé *SIT faiblement défini*.  Cela peut amener le système à effectuer des recherches sur un grand nombre de chaînes qui ne sont pas liées au type de contenu que vous recherchez. Le mappage entre ces types de SIT et les champs principaux peut entraîner des faux négatifs et réduire les performances.

> [!NOTE]
> Comme *sit faiblement défini*, comme un sit personnalisé qui recherche tous les numéros d’identification personnelle, a des règles de détection qui permettent une plus grande variabilité dans les éléments détectés. Un *SIT fortement défini*, comme le numéro de sécurité sociale des États-Unis, a des règles de détection qui autorisent uniquement la détection d’un ensemble étroit et bien défini d’éléments. 

Le système vous avertit également si les valeurs du champ principal que vous sélectionnez se produisent plusieurs fois dans un grand nombre de lignes. Cela peut entraîner le retour et le traitement d’un grand nombre de jeux de résultats, ce qui peut entraîner un délai d’attente. Les délais d’expiration peuvent entraîner des détections manquées et des performances médiocres.


## <a name="choosing-the-right-edm-sit-creation-experience-for-you"></a>Choix de l’expérience de création sit EDM appropriée pour vous

Vous pouvez basculer entre les expériences nouvelles et classiques, mais nous vous recommandons d’utiliser la nouvelle expérience, à moins que vos besoins ne tombent dans un ou plusieurs de ces quatre cas d’usage. 

1. Lire cette section
1. Choisissez l’expérience que vous souhaitez utiliser
1. Sélectionnez le lien de [l’étape suivante](#next-steps) pour l’expérience souhaitée.

### <a name="you-want-to-map-multiple-edm-sits-to-the-same-schema"></a>Vous souhaitez mapper plusieurs EDM SITS au même schéma

Dans EDM, vous pouvez créer un maximum de 10 schémas. Chaque fois que vous créez un sit EDM à l’aide de la nouvelle expérience, un nouveau schéma est créé. Cela entraîne un mappage 1:1 entre le schéma EDM et EDM SIT. La nouvelle expérience ne prend pas en charge le mappage de plusieurs SIT au même schéma.

### <a name="you-need-to-create-or-manage-more-than-10-edm-sits"></a>Vous devez créer ou gérer plus de 10 SIT EDM

 Étant donné que la nouvelle expérience ne prend pas en charge le mappage de plusieurs SIT au même schéma, vous êtes limité à la création et à la gestion de 10 EDM SITS. Dans l’expérience classique, vous pouvez mapper plusieurs SIT EDM au même schéma et avoir donc plus de 10 SIT EDM. À l’aide du nouveau flux, vous recevez une erreur si vous essayez de créer un onzième schéma EDM et que vous ne pourrez pas afficher plus de 10 SIT EDM.

### <a name="you-need-to-specify-the-name-of-your-edm-schema"></a>Vous devez spécifier le nom de votre schéma EDM

Si vous devez spécifier un nom pour vos schémas SIT EDM, vous devez utiliser l’expérience classique pour les créer et les gérer. Étant donné que la nouvelle expérience crée automatiquement le schéma, vous n’avez pas la possibilité de donner un nom personnalisé à votre schéma. Le nom généré automatiquement est une concaténation du nom SIT EDM et du *schéma* de mot. Par exemple, si le nom SIT EDM est *PatientNumber*, le nom du schéma est *PatientNumberschema*.

### <a name="you-need-to-edit-edm-schemas-that-were-created-in-the-classic-experience"></a>Vous devez modifier les schémas EDM qui ont été créés dans l’expérience classique

Tous les schémas créés à l’aide de l’expérience classique ou chargés en tant que fichier XML à l’aide de PowerShell ne sont pas visibles ou gérables dans la nouvelle expérience.

## <a name="next-steps"></a>Prochaines étapes

- [Créer une nouvelle expérience de type de données exactes correspondant à des informations sensibles](sit-create-edm-sit-unified-ux-workflow.md)

ou

- [Créer une expérience classique de type de données exactes correspondant à des informations sensibles](sit-create-edm-sit-classic-ux-workflow.md)

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md)
- [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
- [Créer une nouvelle expérience de flux de travail de type de données exactes correspondant à des informations sensibles](sit-create-edm-sit-unified-ux-workflow.md)
- [Créer une expérience classique de type de flux de travail de type informations sensibles pour créer des données exactes](sit-create-edm-sit-classic-ux-workflow.md)