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
ms.openlocfilehash: bb181ab213cc02e5289681b8c3965a96bd8b8dcb
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182075"
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
2. Accédez à **gestion des**  >  **licences Administrateur de**  >  **rôles d’administration des locataires.**
3. Dans **Autoriser l’accès aux administrateurs** sans permis, sélectionnez **Oui.**

> [!IMPORTANT]
> Vous ne pouvez pas annuler ce paramètre après avoir sélectionné **Oui.**

Pour plus d’informations, [voir Administrateurs](/mem/intune/fundamentals/unlicensed-admins)sans Microsoft Intune .

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
2. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passer en revue les conditions préalables pour les comptes invités (cet article).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. [Préparer les applications](apps.md).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.
