---
title: Configurer un compte de services d’annuaire dans Microsoft Defender pour l’identité
description: Découvrez comment configurer le compte Microsoft Defender pour les services d’annuaire d’identités dans Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.openlocfilehash: 45cc01103a578f84d49bb293ff8801aae3b4c216
ms.sourcegitcommit: 251551539b1532fdac7b7e3dd2733a75c62e8a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58360694"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Compte Microsoft Defender pour les services d’annuaire d’identités dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment configurer le compte [Microsoft Defender for Identity](/defender-for-identity) Directory Services dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender for Identity. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

## <a name="configure-directory-services-account"></a>Configurer le compte des services d’annuaire

Pour connecter le [capteur](sensor-health.md#add-a-sensor) à vos domaines Active Directory, vous devez configurer les comptes des services d’annuaire.

1. In [Microsoft 365 Defender](https://security.microsoft.com/), go to **Paramètres** and then **Identities**.

    ![Go to Paramètres, then Identities](../../media/defender-identity/settings-identities.png)

1. Sélectionnez **des comptes de service d’annuaire.** Vous verrez quels comptes sont associés à quels domaines.

    ![Comptes de service d’annuaire](../../media/defender-identity/directory-service-accounts.png)

1. Si vous sélectionnez un compte, un volet s’ouvre avec les paramètres de ce compte.

    ![Paramètres du compte](../../media/defender-identity/account-settings.png)

1. Pour ajouter un nouveau compte  de services d’annuaire, sélectionnez Créer un compte et remplissez le nom de **compte,** le domaine **et** le mot de **passe.** Vous pouvez également choisir s’il s’agit d’un compte de **service** géré de groupe (gMSA) et s’il appartient à un **domaine d’étiquette unique.**

    ![Nouveau compte de service d’annuaire](../../media/defender-identity/new-directory-service-account.png)

1. Sélectionnez **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Paramètres et l’état du capteur Microsoft Defender pour l’identité](sensor-health.md)
