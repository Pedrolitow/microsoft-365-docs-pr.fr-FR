---
title: Mappage d’identités entre locataires (préversion)
description: Comment mapper des identités entre les organisations Microsoft 365 lors de la préparation des migrations entre locataires.
author: briandaymsft
ms.author: brianday
manager: rolowe
ms.topic: overview
ms.date: 07/18/2022
ms.service: office-365
ms.custom: template-overview
ms.openlocfilehash: 21738fd4131bcaa7ea8c1022608003eea6f1562e
ms.sourcegitcommit: ecc04b5b8f84b34255a2d5e90b5ab596af0d16c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67497397"
---
# <a name="cross-tenant-identity-mapping-preview"></a>Mappage d’identités entre locataires (préversion)

Le mappage d’identités entre locataires est une fonctionnalité qui peut être utilisée pendant les migrations d’une organisation Microsoft 365 vers une autre (communément appelée migration entre locataires). Il fournit une méthode sécurisée d’établissement de relations d’objet un-à-un au-delà des limites de l’organisation et prépare automatiquement les objets cibles pour une migration réussie.

>[!NOTE]
>Le mappage d’identités entre locataires est dans une phase de développement en préversion privée. En tant que projet non terminé, toutes les informations ou disponibilités peuvent être modifiées à tout moment. La prise en charge des clients en préversion privée est gérée par e-mail. Le mappage des identités entre locataires est couvert par les **conditions d’évaluation des conditions** de [licence universelle Microsoft pour les services en ligne](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all).

## <a name="benefits-of-using-cross-tenant-identity-mapping"></a>Avantages de l’utilisation du mappage d’identités entre locataires

Le mappage d’identités inter-locataires supprime la nécessité d’exporter des jeux de données volumineux à partir d’une organisation source dans le seul but de configurer des objets utilisateur avec extension messagerie dans l’organisation cible.

Avec le mappage des identités entre locataires, les données restent dans la limite de sécurité Microsoft et sont copiées en toute sécurité directement à partir de l’organisation source vers l’organisation cible à l’aide **de relations d’organisation** spécialement configurées servant d’approbation unidirectionnelle.

L’utilisation du mappage d’identités entre locataires réduit le risque d’erreurs lors de la configuration de milliers d’objets cibles pour une migration en configurant automatiquement des valeurs telles _qu’ExchangeGuid_, _ArchiveGuid_ et toutes les _adresses proxy X500_ nécessaires.

Voici quelques avantages supplémentaires liés à l’utilisation du mappage d’identités entre locataires :

- Réduit le nombre de processus manuels où une erreur peut entraîner l’échec des migrations
- Automatise l’identification des objets dans l’étendue pour migrer de l’organisation source vers l’organisation cible
- Établit une carte 1:1 d’un objet Utilisateur de boîte aux lettres dans l’organisation source à un objet Utilisateur avec activation du courrier préexistant dans l’organisation cible
- Automatise le remplissage des attributs requis de l’utilisateur de boîte aux lettres de l’organisation source à l’utilisateur cible de messagerie activé
- Fournit une liste d’objets préparés et prêts pour la [migration de boîtes aux lettres entre locataires](cross-tenant-mailbox-migration.md) en fonction de la valeur primarySMTPAddress des utilisateurs de l’organisation source

## <a name="faq-about-cross-tenant-identity-mapping"></a>FAQ sur le mappage d’identités entre locataires

Nous souhaitons fournir des informations fréquemment demandées afin que vous puissiez évaluer si vous souhaitez participer à la préversion privée.

- La fonctionnalité est destinée uniquement à être utilisée avec [la migration de boîtes aux lettres entre locataires (préversion)](cross-tenant-mailbox-migration.md) et non avec des solutions de migration tierces non-Microsoft.
- Le traitement des données (stockage, calcul, transfert, etc.) se trouve actuellement dans le États-Unis de l’Amérique et dans la région d’accueil Exchange Online des organisations participant à la migration.
  - Pour les organisations multigéographiques, la géo d’accueil de l’organisation pour Exchange Online sera utilisée.
- Cette fonctionnalité ne peut actuellement être activée que dans l’offre Microsoft 365 dans le monde entier. Il ne fonctionne pas dans GCC, GCC High, DoD, Office 365 by 21 Vianet, etc.
- Une certaine connaissance de PowerShell est actuellement requise, car la fonctionnalité est basée sur PowerShell
- La fonctionnalité communique via une connexion chiffrée à un point de terminaison REST.
- La fonctionnalité nécessite actuellement le rôle Administrateur général pour la configuration initiale. Ce comportement peut changer dans une prochaine mise à jour.
- Les relations organisationnelles sont utilisées comme une approche de négociation double pour garantir que les deux organisations ont autorisé ce type de transaction à avoir lieu.
- Il fonctionne avec des organisations cloud uniquement ou hybrides.
- Les organisations cibles dans une configuration hybride nécessitent un serveur Exchange local pour modifier tous les objets utilisateur avec activation du courrier synchronisés à partir du répertoire local. Nous n’avons pas testé la prise en charge de la nouvelle fonctionnalité outil de gestion Exchange publiée dans Exchange Server 2019 CU12.

## <a name="what-does-participating-in-the-private-preview-entail"></a>Qu’implique la participation à la préversion privée ?

Nous recherchons des clients prêts à essayer le mappage d’identités entre locataires et à fournir des commentaires en fonction de leur expérience. Cela vous a-t-il facilité la migration par rapport aux migrations antérieures que vous avez effectuées ? Y a-t-il des fonctionnalités qui vous manquent ? Tous les commentaires constructifs sont les bienvenus.

## <a name="how-to-participate"></a>Comment participer

Si vous souhaitez participer ou si vous avez d’autres questions, envoyez un e-mail [CTIMPreview@service.microsoft.com](mailto:CTIMPreview@service.microsoft.com) et fournissez des informations de base sur la migration avec laquelle vous souhaitez utiliser le mappage d’identités entre locataires.

## <a name="next-steps"></a>Prochaines étapes

Nous vous recommandons de passer en revue les étapes de migration de boîte aux lettres interlocataires actuelles liées à la préparation des objets utilisateur cibles pour la migration, car cette préparation est ce que le mappage des identités interlocataires automatisera.

- [Passer en revue la migration de boîtes aux lettres entre locataires (préversion)](cross-tenant-mailbox-migration.md#prepare-target-user-objects-for-migration)
