---
title: Résoudre les problèmes d’intégration et les messages d’erreur
description: Résoudre les problèmes d’intégration et le message d’erreur lors de la configuration de Microsoft Defender pour le point de terminaison.
keywords: résolution des problèmes, dépannage, Azure Active Directory, intégration, message d’erreur, messages d’erreur, microsoft defender pour le point de terminaison
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: cfbd91743ed2e61809d9e2b6f0243b5c327bdae4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467552"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>Résoudre des problèmes d’abonnement et de portail d’accès

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

Cette page fournit des étapes détaillées pour résoudre les problèmes qui peuvent se produire lors de la configuration de votre service Microsoft Defender for Endpoint.

Si vous recevez un message d’erreur, Microsoft 365 Defender fournit une explication détaillée du problème et des liens pertinents sont fournis.

## <a name="no-subscriptions-found"></a>Aucun abonnement trouvé

Si, lors de l’accès à Microsoft 365 Defender vous obtenez **un message aucun** abonnement trouvé, cela signifie que le Azure Active Directory (Azure AD) utilisé pour se connecter à l’utilisateur sur le portail n’a pas de licence Microsoft Defender pour le point de terminaison.

Raisons potentielles :

- Les licences Windows E5 et Office E5 sont des licences distinctes.
- La licence a été achetée, mais elle n’a pas été mise en service Azure AD instance.
  - Il peut s’agit d’un problème de mise en service de licence.
  - Il se peut que vous avez mis en service par inadvertance la licence sur une autre Microsoft Azure AD que celle utilisée pour l’authentification dans le service.

Dans les deux cas, vous devez contacter le support Microsoft au niveau du support [général de Microsoft Defender for Endpoint](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) ou de la prise en charge des [licences en volume](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

:::image type="content" source="images/atp-no-subscriptions-found.png" alt-text="Page Aucun abonnement trouvé" lightbox="images/atp-no-subscriptions-found.png":::

## <a name="your-subscription-has-expired"></a>Votre abonnement a expiré

Si, lors de l’Microsoft 365 Defender vous obtenez **un message votre** abonnement a expiré, votre abonnement de service en ligne a expiré. L’abonnement Microsoft Defender pour les points de terminaison, comme tout autre abonnement de service en ligne, a une date d’expiration.

Vous pouvez choisir de renouveler ou de prolonger la licence à tout moment. Lorsque vous accédez au portail après la date d’expiration, **un message votre** abonnement a expiré se présente avec une option pour télécharger le package de la sortie de l’appareil, si vous choisissez de ne pas renouveler la licence.

> [!NOTE]
> Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages de offboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

:::image type="content" source="images/atp-subscription-expired.png" alt-text="Message de notification expiré de l’abonnement" lightbox="images/atp-subscription-expired.png":::

## <a name="you-are-not-authorized-to-access-the-portal"></a>Vous n’êtes pas autorisé à accéder au portail

Si vous recevez une demande Vous n’êtes pas autorisé à accéder au **portail,** sachez que Microsoft Defender pour le point de terminaison est un produit de surveillance de la sécurité, d’examen des incidents et de réponse. En tant que tel, l’accès à celui-ci est restreint et contrôlé par l’utilisateur.
Pour plus d’informations, voir [**Attribuer un accès utilisateur au portail**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

:::image type="content" source="images/atp-not-authorized-to-access-portal.png" alt-text="Message de notification d’accès non autorisé" lightbox="images/atp-not-authorized-to-access-portal.png":::

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>Les données ne sont actuellement pas disponibles sur certaines sections du portail

Si le tableau de bord du portail et d’autres sections indiquent un message d’erreur tel que « Les données ne sont actuellement pas disponibles » :

:::image type="content" source="images/atp-data-not-available.png" alt-text="Message de notification d’indisponibilité des données" lightbox="images/atp-data-not-available.png":::

Vous devez autoriser tous `security.windows.com` les sous-domaine sous celui-ci sur votre navigateur web. Par exemple : `*.security.windows.com`.

## <a name="portal-communication-issues"></a>Problèmes de communication du portail

Si vous rencontrez des problèmes d’accès au portail, de données manquantes ou d’accès restreint à certaines parties du portail, vous devez vérifier que les URL suivantes sont autorisées et ouvertes pour la communication.

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
