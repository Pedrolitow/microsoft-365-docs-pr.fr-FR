---
title: Régir les informations soumises à la réglementation sur la confidentialité des données
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
description: Utilisez Microsoft 365 étiquettes et stratégies de rétention pour gérer les données personnelles dans votre environnement Microsoft 365 de rétention.
ms.openlocfilehash: 06d3c19918d7e2963bffbb0f663971bbbbb209891f62ee9c83ebcc59b74e16d1
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53843874"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Régir les informations soumises à la réglementation sur la confidentialité des données

Les contrôles de gouvernance des informations peuvent être utilisés dans votre environnement pour répondre aux besoins de conformité de la confidentialité des données, y compris un nombre spécifique au Règlement général sur la protection des données (RGPD), hipAA-HITECH (loi américaine sur la confidentialité des soins de santé), au CCPA (California Consumer Protection Act) et au LGPD (Brazil Data Protection Act). 

Ces contrôles sont principalement pris en compte dans les zones de solution suivantes :

- Stratégies de conservation
- Étiquettes de rétention
- Gestion des enregistrements

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Réglementations en matière de confidentialité des données qui ont un impact sur les contrôles de gouvernance des informations

Voici un exemple de liste des réglementations de confidentialité des données qui peuvent être liées aux contrôles de gouvernance des informations :

- Article R GDPR (13)(2)(a)
- Article R GDPR (5)(1)(f)
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- LGPD Article 46

Pour plus d’informations sur ces réglementations, consultez l’article d’évaluation des risques de confidentialité des données [et d’identification des informations sensibles.](information-protection-deploy-assess.md)

Pour la gouvernance des informations, les réglementations en matière de confidentialité des données appellent généralement les règles suivantes :

- Vous devez utiliser un schéma technique pour la rétention et la suppression des données personnelles stockées dans Microsoft 365.
- Si vous comptez stocker des données personnelles, informez l’objet de la durée de stock des données, ce qui est désormais une pratique standard sur les systèmes web frontaux.
- Les données personnelles doivent être protégées contre le traitement accidentel, la perte ou l’altération à l’aide de méthodes vérifiables.
- Toute action exécutée sur des données personnelles doit être documentée et cette documentation doit être conservée pendant une période spécifiée.

Étant donné que les réglementations en matière de confidentialité des données ne sont pas très spécifiques en matière de rétention et de suppression des données, d’autres facteurs doivent être pris en compte pour dicter les instructions de gouvernance des informations relatives aux informations personnelles stockées dans votre abonnement Microsoft 365. Voici quelques exemples :

- L’âge des comptes consommateur après 5 ans d’inactivité et nécessite la suppression ou l’anonymisation des données de compte après ce point, nécessitant une orchestration entre le système stockant les données et les flux de travail liés aux notifications et à d’autres automatisations.
- Configuration des règles de conservation des stratégies et procédures liées au R GDPR pendant trois ans après leur sur-place, ce qui s’aligne sur la planification de rétention de l’organisation pour les stratégies et procédures.
- Maintien d’un abonnement distinct pour la communication avec les consommateurs via son organisation de support. Toutes les communications par courrier électronique ont été conservées et supprimées au bout de deux semaines afin de réduire l’endettement de confidentialité dans le système.

Une question clé à se poser est la suivante : 

- Combien de temps les informations contenant des données personnelles doivent-elles être conservées pour des raisons professionnelles valides afin d’éviter de « les conserver indéfiniment » ? Cela doit être équilibré avec les besoins de rétention pour la continuité de l’activité.

Quelles que soient les raisons juridiques et professionnelles de conserver des informations personnelles ou de les supprimer, Microsoft fournit un certain nombre de fonctionnalités pour implémenter votre modèle de gouvernance des données dans Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>Gestion de la gouvernance des informations dans Microsoft 365

Pour commencer, voir [Gérer la gouvernance des informations](../compliance/manage-information-governance.md) et la [rétention, la suppression](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview)et la destruction des données dans Microsoft 365 .

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Développer des planifications de rétention des données pour les conteneurs, la messagerie et le contenu

Gardez les éléments suivants à l’esprit :

- L’établissement d’une planification de rétention des données pour les types d’informations définis doit être considéré comme une condition préalable à l’implémentation d’un schéma de rétention ou de suppression.

- Étant donné le nombre de types d’informations que la plupart des organisations considèrent comme importants et les planifications de rétention des enregistrements importantes correspondantes qui vont de même, l’implémentation d’une stratégie de rétention et de gestion des enregistrements de données nécessite une planification. 

- La clé de l’établissement d’une stratégie de gouvernance des données efficace de ce type consiste à se concentrer sur les fonctions métiers et les types d’informations les plus prioritaires qui nécessitent une gestion plus formelle. Les contrats juridiques, les états financiers et la documentation de conformité réglementaire en sont des exemples. Essayez d’éviter d’avoir une planification de rétention distincte pour chaque type d’informations unique. Essayez d’utiliser autant que possible des catégories générales, par exemple, avec des planifications de rétention de 7 ans pour le contenu d’entreprise général.

- Une fois que les types d’informations personnelles de votre environnement sont mieux connus, établissez des planifications de rétention et de suppression pour ce type de contenu et ajustez votre architecture des informations pour faciliter la gouvernance de ce type d’informations. Par exemple, isolez les informations personnelles dans des sites, des bibliothèques ou des dossiers distincts avec un accès contrôlé.

### <a name="retention-policies-and-retention-labels"></a>Stratégies de rétention et étiquettes de rétention.

Utilisez des [stratégies de rétention et](../compliance/retention.md) des étiquettes de rétention pour conserver ou supprimer du contenu Microsoft 365 contenant ou devant contenir des données personnelles.

### <a name="records-management"></a>Gestion des enregistrements

Utilisez des étiquettes de rétention qui déclarent le contenu d’un enregistrement pour implémenter une solution de [gestion](../compliance/records-management.md) des enregistrements pour les données Microsoft 365.

Pour la confidentialité des données, les demandes des personnes responsables des données reçues par le service juridique sont déclarées comme un enregistrement et peuvent être stockées indéfiniment ou éliminées avec preuve, afin de respecter les spécifications de rétention des activités réglementaires.