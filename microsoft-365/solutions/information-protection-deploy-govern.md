---
title: Régir les informations soumises au règlement de confidentialité des données
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
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Utilisez les étiquettes et les stratégies de rétention de Microsoft 365 pour gérer les données personnelles dans votre environnement Microsoft 365.
ms.openlocfilehash: c2a933e556213ae4b78db9dc5f903885df969b27
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377044"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Régir les informations soumises au règlement de confidentialité des données

Les contrôles de gouvernance des informations peuvent être employés dans votre environnement afin de répondre aux besoins de conformité des données en matière de confidentialité, y compris un numéro spécifique au règlement général sur la protection des données (RGPD), au HIPAA-Hi (la loi américaine Health Care Privacy Act), California Consumer Protection Act (CCPA) et le Brésil Data Protection Act (LGPD). 

Ces contrôles appartiennent principalement aux sections de solution suivantes :

- Stratégies de conservation
- Étiquettes de rétention
- Gestion des enregistrements

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Réglementations en matière de confidentialité des données ayant un impact sur les contrôles de gouvernance des informations

Voici un exemple de liste de réglementations sur la confidentialité des données pouvant être liées aux contrôles de la gouvernance des informations :

- Article RGPD (13) (2) (a)
- Article RGPD (5) (1) (f)
- HIPAA-Hi (45 CFR 164.312 (c) (2))
- HIPAA-Hi (45 CFR 164.316 (b) (1) (i))
- HIPAA-Hi (45 CFR 164.316 (b) (1) (II))
- Article 46 de la LGPD

Pour plus d’informations sur ces réglementations, voir l’article relatif à l' [évaluation des risques de confidentialité des données et de l’identification des informations sensibles](information-protection-deploy-assess.md).

Pour la gouvernance des informations, les réglementations en matière de confidentialité des données appellent généralement les suivantes :

- Vous devez utiliser un modèle technique de rétention et de suppression pour les données personnelles stockées dans Microsoft 365.
- Si vous envisagez de stocker des données personnelles, Informez l’objet de la durée de stockage des données, qui est une pratique standard sur les systèmes Web frontaux.
- Les données personnelles doivent être protégées contre le traitement, la perte ou la modification accidentels à l’aide de méthodes vérifiables.
- Toute action exécutée sur des données personnelles doit être documentée et cette documentation doit être conservée pendant une période spécifiée.

Étant donné que les réglementations sur la confidentialité des données ne sont pas très spécifiques en matière de rétention et de suppression des données, d’autres facteurs doivent être pris en considération afin de pouvoir imposer des directives de gouvernance des informations pour les informations personnelles stockées dans votre abonnement Microsoft 365. Voici quelques exemples :

- Vieillissement des comptes des consommateurs après 5 ans d’inactivité et nécessite une suppression ou une anonymisation des données de compte après ce point, nécessitant une orchestration entre le système stockant les données et les flux de travail liés aux notifications et à d’autres automatisations.
- La configuration des règles de conservation des stratégies et des procédures liées à RGPD pendant trois ans après leur remplacement, qui s’aligne sur la planification de rétention de l’Organisation pour les stratégies et les procédures.
- Maintenance d’un abonnement distinct pour la communication avec les consommateurs via son organisation de support technique. Toutes les communications de messagerie ont été conservées et supprimées au bout de deux semaines afin de réduire les accumulations de dettes de confidentialité dans le système.

Une question clé à répondre est la suivante : 

- Combien de temps les informations contenant des données personnelles doivent-elles être conservées pour des raisons professionnelles valides afin d’éviter les pratiques de « conserver définitivement » ? Cela doit être équilibré en fonction des besoins de rétention pour la continuité de l’activité.

Quelles que soient les raisons juridiques et professionnelles de conserver des informations personnelles ou de les supprimer, Microsoft fournit un certain nombre de fonctionnalités pour implémenter votre schéma de gouvernance des données dans Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>Gestion de la gouvernance des informations dans Microsoft 365

Pour commencer, consultez la rubrique [Manage information Governance](../compliance/manage-information-governance.md) and [Data Retention, suppression et Destruction dans Microsoft 365](https://docs.microsoft.com/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Développer des planifications de conservation des données pour les conteneurs, le courrier électronique et le contenu

Gardez les éléments suivants à l’esprit :

- La création d’une planification de rétention des données pour les types d’informations définis doit être considérée comme une condition préalable à l’implémentation d’un modèle de rétention ou de suppression.

- Étant donné le nombre de types d’informations que la plupart des organisations considèrent importantes et les calendriers de rétention des enregistrements volumineux correspondants qui y sont associés, la mise en œuvre d’une stratégie de gestion des enregistrements et de rétention des données nécessite une planification. 

- La clé de l’établissement d’une stratégie de gouvernance des données efficace de ce type consiste à vous concentrer sur les fonctions d’entreprise et les types d’informations de plus haute priorité qui nécessitent une gestion plus formelle. Il s’agit par exemple de contrats légaux, financiers et de la documentation sur la conformité réglementaire. Essayez d’éviter d’avoir un planning de rétention distinct pour chaque type d’information unique. Essayez d’utiliser les catégories générales autant que possible, par exemple, avec des calendriers de rétention de 7 ans pour le contenu professionnel général.

- Une fois que les types d’informations personnelles de votre environnement sont mieux connus, établissez des calendriers de rétention et de suppression pour ce type de contenu et ajustez votre architecture d’informations pour faciliter la gestion de ce type d’informations. Par exemple, isolez les informations personnelles dans des sites, bibliothèques ou dossiers distincts avec un accès contrôlé.

### <a name="retention-policies-and-retention-labels"></a>Stratégies de rétention et étiquettes de rétention.

Utilisez [des stratégies de rétention et des étiquettes de rétention](../compliance/retention.md) pour conserver ou supprimer du contenu dans Microsoft 365 qui contient ou est supposé contenir des données personnelles.

### <a name="records-management"></a>Gestion des enregistrements

Utilisez des étiquettes de rétention qui déclarent le contenu a record pour mettre en œuvre une [solution de gestion des enregistrements](../compliance/records-management.md) pour les données dans Microsoft 365.

Pour la confidentialité des données, les demandes des personnes concernées (DSR) reçues par le service juridique sont déclarées en tant qu’enregistrements et peuvent être conservées indéfiniment ou cédées avec preuve, afin de respecter les spécifications de rétention des activités réglementaires.

