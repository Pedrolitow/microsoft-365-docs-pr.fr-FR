---
title: Migration OneDrive entre locataires
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
recommendations: true
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- SPMigration
- M365-collaboration
- m365initiative-migratetom365
search.appverid: MET150
description: Migration OneDrive entre locataires
ms.openlocfilehash: 0d2076ed4b74cd8bbe21e5d7e7b6e1d0189f822d
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537406"
---
# <a name="cross-tenant-onedrive-migration"></a>Migration OneDrive entre locataires

>[!Note]
> Les informations contenues dans cet article font référence à la **migration OneDrive interlocataire**. [En savoir plus sur la migration de boîtes aux lettres interlocataires ici](/microsoft-365/enterprise/cross-tenant-mailbox-migration)

Lors de fusions ou de désengagements, vous avez généralement besoin de la possibilité de déplacer vos comptes OneDrive utilisateur vers un nouveau locataire Microsoft 365. Avec la migration OneDrive entre locataires, les administrateurs clients peuvent utiliser des outils familiers tels que *SharePoint Online PowerShell* pour faire passer les utilisateurs vers leur nouvelle organisation.

Les administrateurs SharePoint de deux locataires distincts peuvent utiliser l’applet de commande *Set-SPOCrossTenantRelationship* pour établir une relation d’organisation, et la commande *Start-SPOCrossTenantUserContentMove* pour commencer les déplacements OneDrive interlocataires.

Jusqu’à 4 000 comptes OneDrive peuvent être planifiés pour la migration à l’avance à un moment donné. Une fois planifiées, les migrations se produisent sans que les données de l’utilisateur quittent le cloud Microsoft 365 et avec une interruption minimale, ce qui ne nécessite que quelques minutes où oneDrive d’un utilisateur sera en lecture seule. Une fois les migrations terminées, une redirection est placée à l’emplacement du OneDrive d’origine de l’utilisateur, de sorte que tous les liens vers des fichiers et des dossiers peuvent continuer à fonctionner dans le nouvel emplacement. 

>[!Important]
>- Chaque utilisateur disposant de son client oneDrive migré doit disposer d’une licence pour la migration des données utilisateur inter-locataires.
>- La migration OneDrive interlocataire ne peut pas être utilisée pour les clients utilisant Service Encryption avec la clé client Microsoft Purview. [En savoir plus sur le chiffrement de service avec la clé client Microsoft Purview - Microsoft Purview](/microsoft-365/compliance/customer-key-overview?view=o365-worldwide)