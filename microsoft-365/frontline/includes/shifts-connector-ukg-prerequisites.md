---
author: LanaChin
ms.author: v-lanachin
ms.date: ''
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: f3a764a66f3be2fc553581b45dead569ffda1fb6
ms.sourcegitcommit: 99b174a8d431092b3cf7d650593248671297fd91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68301826"
---
Avant de commencer, assurez-vous d'avoir les prérequis suivants :

- Le nom de votre compte de service UKG Dimensions, le mot de passe et les URL de service :

  - URL de l’interface du programme d’application
  - Clé d’application
  - ID du client
  - Clé secrète client
  - URL d’authentification unique

  Si vous ne disposez pas de ces informations, contactez le support UKG Dimensions.
- L’authentification unique fédérée (SSO) est activée dans votre environnement UKG Dimensions. </br>Azure Active Directory (Azure AD) est le fournisseur d’identité pris en charge pour l’authentification unique. Pour activer l’authentification unique, configurez l’intégration entre Azure AD et UKG Dimensions. Pour un didacticiel pas à pas, consultez [Didacticiel : Intégration de l’authentification unique Azure AD à Kronos Workforce Dimensions](/azure/active-directory/saas-apps/kronos-workforce-dimensions-tutorial). Si vous avez besoin d’aide ou d’informations supplémentaires sur la configuration de l’authentification unique, contactez le support UKG Dimensions.

    Une fois l’intégration configurée, configurez les utilisateurs en tant que comptes fédérés sur leur page de profil dans UKG Dimensions.
- Au moins une équipe est configurée dans Teams.
- Vous avez ajouté un compte système Microsoft 365 en tant que propriétaire d’équipe à toutes les équipes que vous souhaitez mapper.</br> [Créez ce compte dans Microsoft 365](/microsoft-365/admin/add-users/add-users) et attribuez-lui une licence Microsoft 365. Ensuite, ajoutez le compte en tant que propriétaire d'équipe à toutes les équipes que vous souhaitez mapper. Le connecteur Shifts utilise ce compte lors de la synchronisation des modifications shifts à partir des dimensions UKG.

    Nous vous recommandons de créer un compte spécifiquement à cet effet et de ne pas utiliser votre compte utilisateur.
