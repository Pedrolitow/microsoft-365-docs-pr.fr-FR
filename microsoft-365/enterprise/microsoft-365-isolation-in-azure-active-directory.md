---
title: isolation et Access Control Microsoft 365 dans Azure Active Directory
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Dans cet article, découvrez comment l’isolation et les Access Control fonctionnent pour conserver les données de plusieurs locataires isolés les uns des autres dans Azure Active Directory.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 409528847d04a55926138e49128f018b349da0a3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093874"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>isolation et Access Control Microsoft 365 dans Azure Active Directory

Azure Active Directory (Azure AD) a été conçu pour héberger plusieurs locataires de manière hautement sécurisée via l’isolation des données logiques. L’accès à Azure AD est contrôlé par une couche d’autorisation. Azure AD isole les clients qui utilisent des conteneurs de locataires comme limites de sécurité pour protéger le contenu d’un client afin qu’il ne soit pas accessible ou compromis par les co-locataires. Trois vérifications sont effectuées par la couche d’autorisation de Azure AD :

- Le principal est-il activé pour l’accès à Azure AD locataire ?
- Le principal est-il activé pour l’accès aux données dans ce locataire ?
- Le rôle du principal dans ce locataire est-il autorisé pour le type d’accès aux données demandé ?

Aucune application, utilisateur, serveur ou service ne peut accéder à Azure AD sans l’authentification et le jeton ou le certificat appropriés. Les demandes sont rejetées si elles ne sont pas accompagnées d’informations d’identification appropriées.

En fait, Azure AD héberge chaque locataire dans son propre conteneur protégé, avec des stratégies et des autorisations pour et au sein du conteneur détenu et géré uniquement par le locataire.
 
![Conteneur Azure.](../media/office-365-isolation-azure-container.png)

Le concept de conteneurs de locataires est profondément ancré dans le service d’annuaire à toutes les couches, des portails jusqu’au stockage persistant. Même lorsque plusieurs métadonnées de locataire Azure AD sont stockées sur le même disque physique, il n’existe aucune relation entre les conteneurs autre que ce qui est défini par le service d’annuaire, qui à son tour est dicté par l’administrateur du locataire. Il ne peut y avoir aucune connexion directe à Azure AD stockage à partir d’une application ou d’un service demandeur sans passer par la couche d’autorisation.

Dans l’exemple ci-dessous, Contoso et Fabrikam ont tous deux des conteneurs distincts et dédiés, et même si ces conteneurs peuvent partager une partie de la même infrastructure sous-jacente, comme les serveurs et le stockage, ils restent séparés et isolés les uns des autres, et contrôlés par des couches d’autorisation et de contrôle d’accès.
 
![Conteneurs dédiés Azure.](../media/office-365-isolation-azure-dedicated-containers.png)

En outre, aucun composant d’application ne peut s’exécuter à partir de Azure AD, et il n’est pas possible pour un locataire de violer de force l’intégrité d’un autre locataire, d’accéder aux clés de chiffrement d’un autre locataire ou de lire des données brutes à partir du serveur.

Par défaut, Azure AD interdit toutes les opérations émises par les identités dans d’autres locataires. Chaque locataire est isolé logiquement dans Azure AD par le biais de contrôles d’accès basés sur les revendications. Les lectures et écritures de données d’annuaire sont limitées aux conteneurs de locataires et contrôlées par une couche d’abstraction interne et une couche de contrôle d’accès en fonction du rôle (RBAC), qui appliquent ensemble le locataire comme limite de sécurité. Chaque demande d’accès aux données d’annuaire est traitée par ces couches et chaque demande d’accès dans Microsoft 365 est surveillée par la logique ci-dessus.

Azure AD a Amérique du Nord, le gouvernement des États-Unis, l’Union européenne, l’Allemagne et les partitions à l’échelle mondiale. Un locataire existe dans une partition unique et les partitions peuvent contenir plusieurs locataires. Les informations de partition sont supprimées des utilisateurs. Une partition donnée (y compris tous les locataires qu’elle contient) est répliquée dans plusieurs centres de données. La partition d’un locataire est choisie en fonction des propriétés du locataire (par exemple, le code du pays). Les secrets et autres informations sensibles dans chaque partition sont chiffrés avec une clé dédiée. Les clés sont générées automatiquement lorsqu’une nouvelle partition est créée.

Azure AD fonctionnalités système sont une instance unique pour chaque session utilisateur. En outre, Azure AD utilise des technologies de chiffrement pour assurer l’isolation des ressources système partagées au niveau du réseau afin d’empêcher le transfert non autorisé et involontaire d’informations.
