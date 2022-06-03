---
title: Redirection de comptes de Microsoft Defender pour Identity vers Microsoft 365 Defender
description: Comment rediriger des comptes et des sessions de Defender pour Identity vers Microsoft 365 Defender.
keywords: Microsoft 365 Defender, Prise en main de Microsoft 365 Defender, redirection du centre de sécurité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: b5c122f01d37d066e0f20bf817ca45ad5c57480b
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864624"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-identity-to-microsoft-365-defender"></a>Redirection de comptes de Microsoft Defender pour Identity vers Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Ce guide explique comment router des comptes vers Microsoft 365 Defender en activant la redirection automatique de l’ancien portail Microsoft Defender pour Identity (portal.atp.azure.com) vers <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

## <a name="what-to-expect"></a>À quoi s’attendre

Une fois la redirection automatique activée, les comptes qui accèdent à l’ancien portail Microsoft Defender pour Identity à portal.atp.azure.com sont automatiquement routées vers le portail Microsoft 365 Defender à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">security.microsoft.com</a>.

## <a name="when-does-this-take-effect"></a>Quand cela prend-il effet ?

Une fois activée, cette mise à jour peut prendre effet presque immédiatement pour certains comptes. Toutefois, la redirection peut prendre plus de temps pour se propager à chaque compte de votre organisation. Les comptes des sessions actives pendant l’application de ce paramètre ne seront pas éjectés de leur session et ne seront routées vers Microsoft 365 Defender qu’après avoir mis fin à leur session active et se reconnecter.  

### <a name="set-up-portal-redirection"></a>Configurer la redirection du portail

Pour démarrer le routage des comptes vers Microsoft 365 Defender :

1. Vérifiez que vous êtes administrateur général ou que vous disposez d’autorisations d’administrateur de sécurité dans Azure Active Directory.

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

1. Accédez à **Paramètres** >  **Identities** > **General** > **Portal redirection** ou [cliquez ici](https://security.microsoft.com/preferences2/portal_redirection).

    :::image type="content" source="../../media/portal-redirection.png" alt-text="Redirection du portail."lightbox="../../media/portal-redirection.png":::

1. Basculez le paramètre de redirection automatique **sur Activé**.

>[!IMPORTANT]
>L’activation de ce paramètre ne met pas fin aux sessions utilisateur actives. Les comptes qui se trouvent dans une session active pendant l’application de ce paramètre ne sont dirigés vers Microsoft 365 Defender qu’après la fin de leur session active et la nouvelle connexion.

>[!NOTE]
>Vous devez être administrateur général ou disposer d’autorisations d’administrateur de sécurité dans Azure Active Directory pour activer ou désactiver ce paramètre.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’utilisation de l’ancien portail ?

Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne pouvez pas terminer par Microsoft 365 Defender, nous voulons en entendre parler. Si vous avez rencontré des problèmes de redirection, nous vous encourageons à nous le faire savoir à l’aide du formulaire De soumission de commentaires.

Pour revenir à l’ancien portail Microsoft Defender pour Identity :

1. Connectez-vous à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> en tant qu’administrateur général ou utilisez et comptez avec des autorisations d’administrateur de sécurité dans Azure Active Directory.

2. Accédez à **Paramètres** >  **Identities** > **General** > **Portal redirection** ou [ouvrez la page ici](https://security.microsoft.com/preferences2/portal_redirection).  

3. Basculez le paramètre de redirection automatique sur **Désactivé**.

Ce paramètre peut être réactivé à tout moment.

Une fois désactivés, les comptes ne sont plus routées vers security.microsoft.com.

## <a name="related-information"></a>Informations connexes

- [vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
- [À propos de Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender)
- [Portails de sécurité et centres d’administration Microsoft](portals.md)
