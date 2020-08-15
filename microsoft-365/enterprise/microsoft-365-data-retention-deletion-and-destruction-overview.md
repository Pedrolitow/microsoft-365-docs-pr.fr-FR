---
title: Conservation, suppression et destruction des données dans Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Vue d’ensemble des stratégies Microsoft pour Microsoft 365 concernant la rétention, la suppression et la destruction des données.
ms.openlocfilehash: c522c1a1a4de46a4fc36bd87a031be8b47c5523d
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46689806"
---
# <a name="data-retention-deletion-and-destruction-in-microsoft-365"></a>Conservation, suppression et destruction des données dans Microsoft 365

Microsoft propose une stratégie standard de gestion des données pour Microsoft 365 qui indique la durée de conservation des données client après la suppression. Il existe généralement deux scénarios dans lesquels les données client sont supprimées :

- **Suppression active**: le client a un abonnement actif et un utilisateur ou un administrateur supprime des données, ou les administrateurs suppriment un utilisateur.
- **Suppression passive**: l’abonnement client prend fin.

## <a name="data-retention"></a>Rétention des données

Pour chacun de ces scénarios de suppression, le tableau suivant indique la période maximale de rétention des données, par catégorie de données et par classification :

| Catégorie de données | Classification des données | Description | Exemples | Période de rétention |
|-----------------|-----------------|-----------------|----------------------------------|-------------------------------|
| Données client | Contenu client| Contenu fourni/créé directement par les administrateurs et les utilisateurs <br><br> Inclut tout le texte, le son, la vidéo, les fichiers image et les logiciels créés et stockés dans les centres de données Microsoft lors de l’utilisation des services dans Microsoft 365 | Exemples d’applications Microsoft 365 les plus couramment utilisées qui permettent aux utilisateurs de créer des données : Word, Excel, PowerPoint, Outlook et OneNote <br><br> Le contenu du client inclut également les secrets fournis par le client (mots de passe, certificats, clés de chiffrement, clés de stockage). | **Scénario de suppression active :** au plus 30 jours <br><br> **Scénario de suppression passive :** au plus 180 jours |
| Données client | Informations identifiables de l’utilisateur final (EUII) | Données qui identifient ou peuvent être utilisées pour identifier l’utilisateur d’un service Microsoft. EUII ne contient pas de contenu client | Nom d’utilisateur ou nom d’affichage (domaine\nom_utilisateur) <br><br> Nom d’utilisateur principal (name@domain) <br><br>  Adresses IP spécifiques de l’utilisateur | **Scénario de suppression active :** au plus 180 jours (seule une action de l’administrateur client) <br><br> **Scénario de suppression passive :** au plus 180 jours |
| Données personnelles <br> (données non incluses dans les données client) | Identificateurs de pseudonyme de l’utilisateur final (EUPI) | Identificateur créé par Microsoft et lié à l’utilisateur d’un service Microsoft. Lorsqu’il est combiné à d’autres informations, telles qu’une table de mappage, EUPI identifie l’utilisateur final <br><br> EUPI ne contient pas les informations chargées ou créées par le client. | GUID d’utilisateur, PUIDs ou sid <br><br> ID de session | **Scénario de suppression active :** au plus 30 jours <br><br> **Scénario de suppression passive :** au plus 180 jours |

## <a name="subscription-retention"></a>Rétention d’abonnement

Dans le terme d’un abonnement actif, un abonné peut accéder aux données client stockées dans Microsoft 365, les extraire ou les supprimer. Si un abonnement payant se termine ou est arrêté, Microsoft conserve les données client stockées dans Microsoft 365 dans un compte à fonction limitée pendant 90 jours pour permettre à l’abonné d’extraire les données. Une fois la période de rétention de 90 jours terminée, Microsoft désactive le compte et supprime les données client. Après un maximum de 180 jours suivant l’expiration ou la résiliation d’un abonnement Microsoft 365, Microsoft désactive le compte et supprime toutes les données client du compte. Une fois la période de rétention maximale des données écoulée, celles-ci sont rendues irrécupérables au plan commercial.

Pour une version d’évaluation gratuite, votre compte passe à un statut de grâce pour 30 jours dans la plupart des pays et régions. Au cours de cette période de grâce, vous pouvez acheter Microsoft 365. Si vous décidez de ne pas acheter Microsoft 365, vous pouvez soit annuler votre version d’évaluation, soit laisser l’expiration de la période de grâce, et les informations et les données de votre compte d’évaluation sont supprimées.

## <a name="expedited-deletion"></a>Suppression accélérée

Pour les abonnements, l’abonné peut contacter le support Microsoft et demander une rapide mise hors service de l’abonnement. Dans le cadre de ce processus, toutes les données utilisateur sont supprimées trois jours après la saisie par l’administrateur du code de verrouillage fourni par Microsoft. Cela inclut les données présentes dans SharePoint Online et Exchange Online mises en attente ou stockées dans des boîtes aux lettres inactives.

Pour plus d’informations sur la désactivation accélérée, reportez-vous à [la rubrique annuler votre abonnement](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/cancel-your-subscription).

## <a name="related-links"></a>Liens connexes

- [Destruction de données](microsoft-365-data-destruction.md)
- [Immuabilité dans Office 365](microsoft-365-data-immutability.md)
- [Suppression de données Exchange Online](microsoft-365-exchange-online-data-deletion.md)
- [Suppression de données SharePoint Online](microsoft-365-sharepoint-online-data-deletion.md)
- [Suppression des données Skype Entreprise](microsoft-365-skype-data-deletion.md)
