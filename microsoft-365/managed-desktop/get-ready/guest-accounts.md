---
title: Conditions préalables pour les comptes invité
description: Instructions de configuration pour les comptes invités et comment les ajuster
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 6cd7b69d154444bb6b39e61bc3446ea01d54321a
ms.sourcegitcommit: b3091791196828883d8284497561027df692d109
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2021
ms.locfileid: "53663850"
---
# <a name="prerequisites-for-guest-accounts"></a>Conditions préalables pour les comptes invité

## <a name="external-collaboration-settings"></a>Paramètres de collaboration externe

Microsoft Manged Desktop nécessite les paramètres suivants dans votre organisation Azure AD pour l’accès au compte invité. Vous pouvez ajuster ces paramètres sur le portail [Azure](https://portal.azure.com) sous **Identités externes /Paramètres de collaboration externe**:

-   Pour **les restrictions d’invitation d’invité définies** sur les utilisateurs membres et les utilisateurs affectés à des rôles d’administrateur spécifiques peuvent inviter des utilisateurs invités, y compris des invités avec des **autorisations de membre**
-   Pour **les restrictions de collaboration,** choisissez l’une des options ci-après :
    -   Si vous **sélectionnez Autoriser l’envoi d’invitations** à un domaine (le plus inclus), aucune autre configuration n’est requise.
    -   Si vous sélectionnez Refuser les invitations aux domaines **spécifiés,** assurez-vous Microsoft.com n’est pas répertorié dans les domaines cibles.
    -   Si vous sélectionnez Autoriser les invitations uniquement aux domaines **spécifiés (les plus restrictifs),** assurez-vous que Microsoft.com est répertorié dans les domaines cibles. 

Si vous définissez des restrictions qui interagissent avec ces paramètres, veillez à exclure les Azure Active Directory des comptes de **service Workplace modernes.** Par exemple, si vous avez une stratégie d’accès conditionnel qui empêche les comptes invités d’accéder au portail Intune, excluez le groupe Comptes de **service** Workplace modernes de cette stratégie.

## <a name="unlicensed-intune-admin"></a>Administrateur Intune sans permis

Le **paramètre Autoriser l’accès aux administrateurs** sans permis doit être activé. Si ce paramètre n’est pas activé, des erreurs peuvent se produire lorsque nous essayons d’accéder à votre organisation Azure AD pour le service. Vous pouvez activer ce paramètre en toute sécurité sans vous soucier des implications en matière de sécurité, car l’étendue de l’accès est définie par les rôles attribués aux utilisateurs, y compris le personnel opérationnel.

Pour activer ce paramètre, suivez les étapes suivantes :

1. Go to the Microsoft Endpoint Manager [admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Accédez à **gestion des licences Administrateur**  >  **de rôles**  >  **d’administration des locataires.**
3. Dans **Autoriser l’accès aux administrateurs** sans permis, sélectionnez **Oui.**

> [!IMPORTANT]
> Vous ne pouvez pas annuler ce paramètre après avoir sélectionné **Oui.**

Pour plus d’informations, [voir Administrateurs](/mem/intune/fundamentals/unlicensed-admins)sans Microsoft Intune .

## <a name="steps-to-get-ready"></a>Étapes pour vous préparer

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
2. Utiliser les [outils de préparation d’évaluation](readiness-assessment-tool.md).
3. [Conditions préalables pour les comptes invités](guest-accounts.md) (cet article)
4. [Configuration du réseau pour Bureau géré Microsoft](network.md)
5. [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft](certs-wifi-lan.md)
6. [Préparer l’accès aux ressources locales pour le Bureau géré Microsoft](authentication.md)
7. [Applications dans le Bureau géré Microsoft](apps.md)
8. [Préparer les lecteurs mappés pour le Bureau géré Microsoft](mapped-drives.md)
9. [Préparer des ressources d’impression pour le Bureau géré Microsoft](printing.md)
