---
title: Configurer un compte Directory Services dans Microsoft Defender pour Identity
description: Découvrez comment configurer le compte Microsoft Defender pour Identity Directory Services dans Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: ecd32aec05c867e360ec5dd98400334e551ba7b0
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67690868"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Microsoft Defender pour Identity compte Directory Services dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment configurer le compte [Microsoft Defender pour Identity](/defender-for-identity) Directory Services dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé à partir de leur emplacement dans le portail Defender pour Identity. Lisez les détails ci-dessous pour découvrir où trouver les fonctionnalités familières et nouvelles.

## <a name="configure-directory-services-account"></a>Configurer un compte Directory Services

Pour connecter le [capteur](sensor-health.md#add-a-sensor) à vos domaines Active Directory, vous devez configurer des comptes Directory Services.

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, accédez aux **paramètres**, puis **aux identités**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités dans la page Paramètres" lightbox="../../media/defender-identity/settings-identities.png":::


1. Sélectionnez **comptes de service d’annuaire**. Vous verrez quels comptes sont associés à quels domaines.

   :::image type="content" source="../../media/defender-identity/directory-service-accounts.png" alt-text="Élément de menu Comptes du service d’annuaire" lightbox="../../media/defender-identity/directory-service-accounts.png":::

1. Si vous sélectionnez un compte, un volet s’ouvre avec les paramètres de ce compte.

   :::image type="content" source="../../media/defender-identity/account-settings.png" alt-text="Page Paramètres du compte" lightbox="../../media/defender-identity/account-settings.png":::

1. Pour ajouter un nouveau compte Directory Services, **sélectionnez Créer un compte** et renseignez le **nom du compte**, le **domaine** et le **mot de passe**. Vous pouvez également choisir s’il s’agit d’un **compte de service administré** de groupe (gMSA) et s’il appartient à un **domaine d’étiquette unique**.

   :::image type="content" source="../../media/defender-identity/new-directory-service-account.png" alt-text="Option Créer un compte" lightbox="../../media/defender-identity/new-directory-service-account.png":::

1. Sélectionnez **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Microsoft Defender pour Identity l’intégrité et les paramètres du capteur](sensor-health.md)
