---
title: Configurer un compte de services d’annuaire dans Microsoft Defender pour l’identité
description: Découvrez comment configurer le compte Microsoft Defender pour les services d’annuaire d’identités dans Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e31c226037d5d9e945350ba73e1df9abc79571e9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469996"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Compte Microsoft Defender pour les services d’annuaire d’identités dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment configurer le compte [Microsoft Defender for Identity](/defender-for-identity) Directory Services dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender pour l’identité. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

## <a name="configure-directory-services-account"></a>Configurer le compte des services d’annuaire

Pour connecter le [capteur](sensor-health.md#add-a-sensor) à vos domaines Active Directory, vous devez configurer les comptes des services d’annuaire.

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, go to **Paramètres** and then **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités dans la page Paramètres page" lightbox="../../media/defender-identity/settings-identities.png":::


1. **Sélectionnez des comptes de service d’annuaire**. Vous verrez quels comptes sont associés à quels domaines.

   :::image type="content" source="../../media/defender-identity/directory-service-accounts.png" alt-text="Élément de menu Comptes du service d’annuaire" lightbox="../../media/defender-identity/directory-service-accounts.png":::

1. Si vous sélectionnez un compte, un volet s’ouvre avec les paramètres de ce compte.

   :::image type="content" source="../../media/defender-identity/account-settings.png" alt-text="Page Paramètres du compte" lightbox="../../media/defender-identity/account-settings.png":::

1. Pour ajouter un nouveau compte de services d’annuaire, sélectionnez Créer un compte et remplissez le **nom du compte****, le** domaine et le mot de **passe**. Vous pouvez également choisir s’il s’agit d’un compte de **service** géré de groupe (gMSA) et s’il appartient à un **domaine d’étiquette unique**.

   :::image type="content" source="../../media/defender-identity/new-directory-service-account.png" alt-text="Option Créer un compte" lightbox="../../media/defender-identity/new-directory-service-account.png":::

1. Sélectionnez **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Paramètres et l’état du capteur Microsoft Defender pour l’identité](sensor-health.md)
