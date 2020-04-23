---
title: Protéger des fichiers dans Teams avec des étiquettes de confidentialité
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Résumé : appliquez des étiquettes de confidentialité pour protéger les fichiers d’une équipe hautement confidentielle.'
ms.openlocfilehash: c36daef7f28ad8bd3306fd7f3f7f1558a3594e68
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43637615"
---
# <a name="protect-files-in-teams-with-sensitivity-labels"></a>Protéger des fichiers dans Teams avec des étiquettes de confidentialité


Contrairement à une étiquette de confidentialité pour les données hautement réglementées qu’une personne peut appliquer à n’importe quel fichier, une équipe hautement confidentielle doit avoir sa propre étiquette ou sous-étiquette de sorte que les fichiers auxquels elle est attribuée :

- Soient chiffrés individuellement.
- Contiennent des autorisations personnalisées de sorte que seuls les membres de l’équipe puissent l’ouvrir.

Pour atteindre ce niveau de sécurité supplémentaire pour les fichiers stockés sur le site SharePoint sous-jacent d’une équipe, vous devez configurer une étiquette de confidentialité personnalisée qui est soit sa propre étiquette, soit une sous-étiquette de l’étiquette générale pour les données hautement réglementées. Seuls les membres de l’équipe peuvent consulter l’étiquette ou sous-étiquette personnalisée dans leur liste d’étiquettes.

Utilisez une étiquette de confidentialité lorsque vous avez besoin d’un petit nombre d’étiquettes à la fois pour un usage global et pour des équipes privées individuelles. 

Utilisez une sous-étiquette de confidentialité lorsque vous avez un grand nombre d’étiquettes ou si vous souhaitez organiser les étiquettes pour les équipes hautement confidentielles sous l’étiquette hautement réglementée.

Suivez [ces instructions](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) pour configurer une étiquette distincte ou une sous-étiquette avec les paramètres suivants :

- Le nom de l’étiquette ou de la sous-étiquette contient le nom de l’équipe
- Le chiffrement est activé
- Le groupe Microsoft 365 pour les membres de l’équipe possède des autorisations de co-édition

Une fois que vous avez créé, publiez la nouvelle étiquette ou sous-étiquette pour vos utilisateurs, puis appliquez-les aux fichiers en local avant de les charger dans l’équipe ou plus tard une fois que le fichier est stocké dans l’équipe.

Voici la configuration de l’équipe hautement confidentielle qui utilise des étiquettes de confidentialité pour le chiffrement des fichiers et les autorisations.

![Protection de niveau de référence pour une équipe publique.](../../media/highly-confidential-team-dlp-sensitivity-labels.png)


## <a name="see-also"></a>Voir aussi

[Sécuriser des fichiers dans Microsoft Teams](secure-files-in-teams.md)
  
[Adoption du cloud et solutions hybrides](https://docs.microsoft.com/office365/enterprise/cloud-adoption-and-hybrid-solutions)
