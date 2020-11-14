---
title: Conditions préalables pour les comptes invités
description: Instructions de configuration pour les comptes invités et comment les ajuster
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: d8953e9f451daa02671a1e1544f2dfe6649ab1b3
ms.sourcegitcommit: fcc1b40732f28f075d95faffc1655473e262dd95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2020
ms.locfileid: "49073202"
---
# <a name="prerequisites-for-guest-accounts"></a>Conditions préalables pour les comptes invités

Microsoft Managed Desktop requiert les paramètres suivants dans votre organisation Azure AD pour l’accès au compte invité. Vous pouvez ajuster ces paramètres sur le [portail Azure](https://portal.azure.com) sous **identités externes/collaboration externe** :

-   Les **administrateurs et les utilisateurs du rôle invités invité peuvent inviter la** valeur **Oui**
-   Pour les **restrictions de collaboration** , choisissez l’une des options suivantes :
    -   Si vous sélectionnez **autoriser l’envoi d’invitations à n’importe quel domaine (la plus incluse)** , aucune autre configuration n’est requise.
    -   Si vous sélectionnez **refuser les invitations aux domaines spécifiés** , vérifiez que Microsoft.com n’est pas indiqué dans les domaines cibles.
    -   Si vous sélectionnez **autoriser uniquement les invitations aux domaines spécifiés (le plus restrictif)** , assurez-vous que Microsoft.com *est* indiqué dans les domaines cibles.

Si vous définissez des restrictions qui interagissent avec ces paramètres, veillez à exclure les **comptes de service espace de travail moderne** Azure Active Directory. Par exemple, si vous avez une stratégie d’accès conditionnel qui empêche les comptes invités d’accéder au portail Intune, excluez le groupe de comptes de service de l' **espace de travail moderne** de cette stratégie.

