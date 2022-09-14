---
title: Résoudre les problèmes d’intégration et les messages d’erreur
description: Résoudre les problèmes d’intégration et le message d’erreur lors de la configuration de Microsoft Defender pour point de terminaison.
keywords: résolution des problèmes, résolution des problèmes, Azure Active Directory, intégration, message d’erreur, messages d’erreur, microsoft defender pour point de terminaison
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 2e00f431858685bb0d1eefe6ef098890074cf6ac
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67682600"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>Résoudre des problèmes d’abonnement et de portail d’accès

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

Cette page fournit des étapes détaillées pour résoudre les problèmes qui peuvent se produire lors de la configuration de votre service Microsoft Defender pour point de terminaison.

Si vous recevez un message d’erreur, Microsoft 365 Defender fournit une explication détaillée de ce qu’est le problème et des liens pertinents sont fournis.

## <a name="no-subscriptions-found"></a>Aucun abonnement trouvé

Si, lors de l’accès à Microsoft 365 Defender vous recevez un message **Aucun abonnement trouvé**, cela signifie qu’Azure Active Directory (Azure AD) utilisé pour se connecter à l’utilisateur sur le portail ne dispose pas d’une licence Microsoft Defender pour point de terminaison.

Raisons potentielles :

- Les licences Windows E5 et Office E5 sont des licences distinctes.
- La licence a été achetée, mais pas approvisionnée sur cette instance Azure AD.
  - Il peut s’agir d’un problème d’approvisionnement de licences.
  - Il se peut que vous provisionniez par inadvertance la licence sur un Microsoft Azure AD différent de celui utilisé pour l’authentification dans le service.

Dans les deux cas, vous devez contacter le support Microsoft auprès du support [général Microsoft Defender pour point de terminaison ou du](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) [support des licences en volume](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

:::image type="content" source="images/atp-no-subscriptions-found.png" alt-text="Page Aucun abonnement trouvé" lightbox="images/atp-no-subscriptions-found.png":::

## <a name="your-subscription-has-expired"></a>Votre abonnement a expiré

Si, lors de l’accès à Microsoft 365 Defender vous obtenez un message **votre abonnement a expiré**, votre abonnement de service en ligne a expiré. Microsoft Defender pour point de terminaison abonnement, comme tout autre abonnement de service en ligne, a une date d’expiration.

Vous pouvez choisir de renouveler ou d’étendre la licence à tout moment. Lorsque vous accédez au portail après la date d’expiration, un message de **votre abonnement ayant expiré** s’affiche avec une option de téléchargement du package de désintégrage de l’appareil, si vous choisissez de ne pas renouveler la licence.

> [!NOTE]
> Pour des raisons de sécurité, le package utilisé pour désintégrez les appareils expirera 30 jours après la date de téléchargement. Les packages de désintégrage expirés envoyés à un appareil seront rejetés. Lors du téléchargement d’un package de désintégrage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

:::image type="content" source="images/atp-subscription-expired.png" alt-text="Message de notification d’expiration de l’abonnement" lightbox="images/atp-subscription-expired.png":::

## <a name="you-are-not-authorized-to-access-the-portal"></a>Vous n’êtes pas autorisé à accéder au portail

Si vous recevez un **Vous n’êtes pas autorisé à accéder au portail**, sachez que Microsoft Defender pour point de terminaison est un produit de surveillance de la sécurité, d’investigation et de réponse aux incidents, et que par conséquent, l’accès à celui-ci est restreint et contrôlé par l’utilisateur.
Pour plus d’informations, consultez [**Affecter l’accès utilisateur au portail**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

:::image type="content" source="images/atp-not-authorized-to-access-portal.png" alt-text="Message de notification d’accès non autorisé" lightbox="images/atp-not-authorized-to-access-portal.png":::

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>Les données ne sont actuellement pas disponibles dans certaines sections du portail

Si le tableau de bord du portail et d’autres sections affichent un message d’erreur tel que « Les données ne sont pas disponibles actuellement » :

:::image type="content" source="images/atp-data-not-available.png" alt-text="Message de notification d’indisponibilité des données" lightbox="images/atp-data-not-available.png":::

Vous devez autoriser tous les `security.windows.com` sous-domaines sous celui-ci sur votre navigateur web. Par exemple : `*.security.windows.com`.

## <a name="portal-communication-issues"></a>Problèmes de communication dans le portail

Si vous rencontrez des problèmes d’accès au portail, de données manquantes ou d’accès restreint à des parties du portail, vous devez vérifier que les URL suivantes sont autorisées et ouvertes pour la communication.

- `*.blob.core.windows.net`
- `crl.microsoft.com`
- `https://*.microsoftonline-p.com`
- `https://*.security.microsoft.com`
- `https://automatediracs-eus-prd.security.microsoft.com`
- `https://login.microsoftonline.com`
- `https://login.windows.net`
- `https://onboardingpackagescusprd.blob.core.windows.net`
- `https://secure.aadcdn.microsoftonline-p.com`
- `https://security.microsoft.com`
- `https://static2.sharepointonline.com`
