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
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
description: Utilisez des stratégies et des étiquettes de rétention Microsoft 365 pour gérer les données personnelles dans votre environnement Microsoft 365.
ms.openlocfilehash: 5998ddc4651a5a07ee5fd9cd53b632de2f72b39d
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67727169"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Régir les informations soumises à la réglementation sur la confidentialité des données

Les contrôles de gouvernance des informations peuvent être utilisés dans votre environnement pour répondre aux besoins en matière de conformité à la confidentialité des données, notamment un nombre spécifique au Règlement général sur la protection des données (RGPD), HIPAA-HITECH (loi Estados Unidos sur la confidentialité des soins de santé), à la Loi de Californie sur la protection des consommateurs (CCPA) et à la Loi sur la protection des données du Brésil (LGPD). 

Ces contrôles s’inscrivent principalement dans les domaines de solution suivants :

- Stratégies de conservation
- Étiquettes de rétention
- Gestion des enregistrements

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Réglementations sur la confidentialité des données qui ont un impact sur les contrôles de gouvernance des informations

Voici un exemple de liste des réglementations relatives à la confidentialité des données qui peuvent être liées aux contrôles de gouvernance des informations :

- Article RGPD (13)(2)(a)
- Article RGPD (5)(1)(f)
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- LGPD Article 46

Pour plus d’informations sur ces réglementations, consultez [l’article évaluer les risques liés à la confidentialité des données et identifier les informations sensibles](information-protection-deploy-assess.md).

Pour la gouvernance des informations, les réglementations sur la confidentialité des données appellent généralement les éléments suivants :

- Vous devez utiliser un schéma technique pour la rétention et la suppression des données personnelles stockées dans Microsoft 365.
- Si vous souhaitez stocker des données personnelles, informez l’objet de la durée de stockage des données, ce qui est une pratique standard désormais sur les systèmes web frontaux.
- Les données personnelles doivent être protégées contre le traitement accidentel, la perte ou la modification à l’aide de méthodes vérifiables.
- Toute action exécutée sur des données personnelles doit être documentée et cette documentation doit être conservée pendant une période spécifiée.

Étant donné que les réglementations sur la confidentialité des données ne sont pas très spécifiques en ce qui concerne la conservation et la suppression des données, d’autres facteurs doivent être pris en compte qui peuvent dicter des instructions de gouvernance des informations pour les informations personnelles stockées dans votre abonnement Microsoft 365. Voici quelques exemples :

- Le vieillissement des comptes de consommateur après 5 ans d’inactivité et nécessite la suppression ou l’anonymisation des données de compte après ce point, nécessitant une orchestration entre le système stockant les données et les flux de travail liés aux notifications et à d’autres automatisations.
- Configuration de règles pour conserver les stratégies et procédures relatives au RGPD environ trois ans après leur remplacement, ce qui s’aligne sur la planification de rétention de l’organisation pour les stratégies et procédures.
- Gestion d’un abonnement distinct pour communiquer avec les consommateurs via son organisation de support. Toutes les communications par courrier électronique ont été conservées et supprimées au bout de deux semaines afin de réduire l’accumulation de la dette de confidentialité dans le système.

Une question clé à répondre est la suivante : 

- Combien de temps les informations contenant des données personnelles doivent-elles être conservées pour des raisons commerciales valides afin d’éviter les pratiques de « conserver indéfiniment » ? Cela doit être équilibré avec les besoins de rétention pour la continuité d’activité.

Quelles que soient les raisons légales et commerciales pour conserver ou supprimer des informations personnelles, Microsoft fournit un certain nombre de fonctionnalités pour implémenter votre schéma de gouvernance des données dans Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>Gestion de la gouvernance des informations dans Microsoft 365

Pour commencer, consultez [Régir vos données avec Microsoft Purview](../compliance/manage-data-governance.md) et [la conservation, la suppression et la destruction des données dans Microsoft 365](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Développer des planifications de rétention des données pour les conteneurs, les e-mails et le contenu

Gardez les éléments suivants à l’esprit :

- L’établissement d’une planification de rétention des données pour les types d’informations définis doit être considéré comme une condition préalable à l’implémentation d’un schéma de rétention ou de suppression.

- Étant donné le nombre de types d’informations que la plupart des organisations considèrent comme importants et les planifications de rétention des enregistrements volumineux correspondantes qui les accompagnent, l’implémentation d’une stratégie de conservation des données et de gestion des enregistrements nécessite une planification. 

- La clé de l’établissement d’une stratégie efficace de gouvernance des données de ce type consiste à se concentrer sur les fonctions métier et les types d’informations les plus prioritaires qui nécessitent une gestion plus formelle. Les contrats juridiques, les états financiers et la documentation sur la conformité réglementaire en sont des exemples. Essayez d’éviter d’avoir une planification de rétention distincte pour chaque type d’informations. Essayez d’utiliser autant que possible des catégories générales, par exemple, avec des planifications de rétention de 7 ans pour le contenu général de l’entreprise.

- Une fois que les types d’informations personnelles de votre environnement sont mieux connus, établissez des planifications de rétention et de suppression pour ce type de contenu et ajustez votre architecture des informations pour faciliter la gouvernance de ce type d’informations. Par exemple, isolez les informations personnelles dans des sites, bibliothèques ou dossiers distincts avec un accès contrôlé.

### <a name="retention-policies-and-retention-labels"></a>Stratégies de rétention et étiquettes de rétention

Utilisez [des stratégies de rétention et des étiquettes de rétention](../compliance/retention.md) pour conserver ou supprimer du contenu dans Microsoft 365 qui contient ou doit contenir des données personnelles.

### <a name="records-management"></a>Gestion des enregistrements

Utilisez des étiquettes de rétention qui déclarent un enregistrement de contenu pour implémenter une [solution de gestion des enregistrements](../compliance/records-management.md) pour les données dans Microsoft 365.

Pour la confidentialité des données, les demandes de personnes concernées reçues par le service juridique sont déclarées comme un enregistrement et peuvent être stockées indéfiniment ou supprimées avec preuve, pour respecter les spécifications de conservation des activités réglementaires.