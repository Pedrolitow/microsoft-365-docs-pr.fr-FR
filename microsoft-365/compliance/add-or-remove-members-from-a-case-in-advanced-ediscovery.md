---
title: Ajouter ou supprimer des membres à partir d’un cas
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment ajouter ou supprimer les membres qui peuvent accéder à un cas lors de la gestion d’Advanced eDiscovery cas.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 13a97af715a3f81b5570617f18b10cd8e35f9aec
ms.sourcegitcommit: afee35210f8d68a7f20676ff2a829464b0b0adb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "60217101"
---
# <a name="add-or-remove-members-from-a-case"></a>Ajouter ou supprimer des membres à partir d’un cas

Vous pouvez ajouter ou supprimer des membres pour gérer les utilisateurs pouvant accéder au cas. Toutefois, pour qu’un membre puisse accéder à un cas de Advanced eDiscovery (et effectuer des tâches dans le cas), vous devez ajouter l’utilisateur au groupe de rôles Gestionnaire eDiscovery sur la page **Autorisations** de la Centre de conformité Microsoft 365. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](./assign-ediscovery-permissions.md).

1. Dans la page **Advanced eDiscovery**, accédez au cas auquel vous voulez ajouter un membre.

2. Cliquez sur l’onglet **Paramètres**, puis cliquez sur **Sélectionner** dans la vignette **Accès et autorisations**.

3. Cliquez sur **Mise à jour**.

4. Sous **Gérer les membres**, cliquez sur **Ajouter** pour ajouter des membres au cas. Vous pouvez également choisir d’ajouter un groupe de rôles au cas en cliquant sur **Ajouter** sous Gérer les groupes **de rôles.**

5. Dans la liste des personnes ou groupes de rôles pouvant être ajoutés en tant que membres du cas, activez la case à cocher en regard des noms des personnes ou des groupes de rôles que vous voulez ajouter.

   > [!NOTE]
   > Lorsque vous ajoutez un groupe de rôles à un cas, vous ne pouvez ajouter que les groupes de rôles dont vous êtes membre.

6. Une fois que vous avez sélectionné les personnes ou les groupes de rôles à ajouter en tant que membres du cas, cliquez sur **Ajouter**.

7. Dans la page de garde **Gérer ce cas**, cliquez sur **Enregistrer** pour enregistrer la nouvelle liste des membres de cas.

> [!IMPORTANT]
> Si un rôle est ajouté ou supprimé d’un groupe de rôles que vous avez ajouté en tant que membre d’un cas, le groupe de rôles est automatiquement supprimé en tant que membre du cas (ou tout autre cas dont le groupe de rôles est membre). La raison en est que votre organisation ne fournit pas par inadvertance des autorisations supplémentaires aux membres d’un cas. De même, si un groupe de rôles est supprimé, il sera supprimé de tous les cas dont il était membre. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases).
