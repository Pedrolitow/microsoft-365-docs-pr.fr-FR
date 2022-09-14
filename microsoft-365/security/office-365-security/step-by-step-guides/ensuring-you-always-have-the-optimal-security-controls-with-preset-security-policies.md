---
title: Étapes de configuration rapide des stratégies de sécurité prédéfinies Standard ou Strict pour Microsoft Defender pour Office 365
description: Étape de configuration des stratégies de sécurité prédéfinies dans Microsoft Defender pour Office 365 afin que vous ayez la sécurité recommandée par le produit. Les stratégies prédéfinies définissent un profil de sécurité *standard* ou *strict*. Définissez ces contrôles et Microsoft Defender pour Office 365 gérerez et conservez ces contrôles de sécurité pour vous.
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
search.appverid: met150
ms.openlocfilehash: 6ee5ffd388d5bb278c4655e90e217d5d663cca08
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67686502"
---
# <a name="set-up-steps-for-the-standard-or-strict-preset-security-policies-in-microsoft-defender-for-office-365"></a>Configurer les étapes des stratégies de sécurité prédéfinies Standard ou Strict dans Microsoft Defender pour Office 365

Est-ce que Microsoft Defender pour Office 365 vous a donné un moyen d’appliquer des stratégies de sécurité qu’elle conserverait alors ?

Saviez-vous que lorsqu’une bonne pratique pour un contrôle de sécurité change en raison de l’évolution du paysage des menaces ou que de nouveaux contrôles sont ajoutés, Microsoft met *automatiquement* à jour les paramètres de contrôle de sécurité pour les utilisateurs affectés à une stratégie de sécurité *prédéfinies Standard* ou *Strict* ?

En utilisant des stratégies de sécurité prédéfinies (*Standard* ou *Strict*), vous disposerez toujours de *la configuration recommandée par Microsoft, meilleure pratique,* pour vos utilisateurs.

**Suivez les étapes ci-dessous** pour appliquer des stratégies de sécurité prédéfinies et avoir Microsoft Defender pour Office 365 gérer et gérer les contrôles de sécurité *pour vous*.

## <a name="what-you-will-need"></a>Ce dont vous aurez besoin
- Microsoft Defender pour Office 365 plan 1 ou supérieur (inclus dans E5)
- Autorisations suffisantes (rôle Administrateur de sécurité)
- 5 minutes pour effectuer les étapes ci-dessous.

## <a name="choose-between-standard-and-strict-policies"></a>Choisir entre les stratégies Standard et Strict

Notre stratégie de sécurité prédéfinies stricte a des limites et des paramètres plus agressifs pour les contrôles de sécurité, ce qui entraîne des détections plus agressives et implique l’administrateur dans la prise de décisions sur les e-mails bloqués qui sont publiés aux utilisateurs finaux.

- Collectez la liste de vos utilisateurs qui nécessitent des détections plus agressives, même si cela signifie que plus de messages sont signalés comme suspects. Il s’agit généralement de votre personnel exécutif, du personnel de support exécutif et d’utilisateurs historiquement très ciblés.

- Assurez-vous que les utilisateurs sélectionnés disposent d’une couverture administrateur pour passer en revue et publier des e-mails si l’utilisateur final pense que le courrier peut être correct et demande que le message leur soit remis.

- Si les critères ci-dessus sont remplis, l’utilisateur doit être placé dans la stratégie de sécurité prédéfinies strict. Sinon, l’utilisateur doit être placé dans la stratégie de sécurité prédéfinies Standard.

> [!TIP]
> Pour plus d’informations sur les polices de sécurité Standard et Strict, consultez cet [article](../../office-365-security/recommended-settings-for-eop-and-office365.md).

## <a name="enable-security-presets-in-microsoft-defender-for-office-365"></a>Activer les présélections de sécurité dans Microsoft Defender pour Office 365

Une fois que vous avez choisi entre les stratégies de préréglage de sécurité Standard et Strict pour vos utilisateurs, il faut quelques étapes supplémentaires pour affecter des utilisateurs à chaque présélection.

1. Identifiez les utilisateurs, groupes ou domaines que vous souhaitez inclure dans les présélections de sécurité Standard et Strict.
1. Connectez-vous au portail Microsoft Security à l’adresse https://security.microsoft.com.
1. Dans le volet de navigation gauche, sous **Email & collaboration**, sélectionnez **Stratégies & règles**.
1. Sélectionnez **Stratégies de menace**.
1. Sélectionnez **Stratégies de sécurité prédéfinies** sous le titre **Stratégies modèles**
1. Sélectionnez **Gérer** sous la présélection de protection Standard.
1. Sélectionnez **Tous les destinataires** à appliquer Exchange Online Protection à l’échelle du locataire, ou sélectionnez **Destinataires spécifiques** pour ajouter manuellement des utilisateurs, des groupes ou des domaines auxquels vous souhaitez appliquer la stratégie de protection. Cliquez sur le bouton **Suivant** .
1. Sélectionnez **Tous les destinataires** pour appliquer Defender pour Office 365 protection à l’échelle du locataire, ou sélectionnez **Destinataires spécifiques** pour ajouter manuellement des utilisateurs, des groupes ou des domaines auxquels vous souhaitez appliquer la stratégie de protection. Cliquez sur le bouton **Suivant** .
1. Dans la section **Protection** de l’emprunt d’identité, ajoutez des adresses e-mail & domaines à protéger contre les attaques d’emprunt d’identité, puis ajoutez les expéditeurs approuvés et les domaines auxquelles vous ne souhaitez pas appliquer la protection d’emprunt d’identité, puis appuyez sur **Suivant**.
1. Cliquez sur le bouton **Confirmer** .
1. Sélectionnez le lien **Gérer** dans la présélection De protection stricte.
1. Répétez les étapes 7 à 10, mais pour les utilisateurs, une protection stricte doit être appliquée. (le cas échéant)
1. Cliquez sur le bouton **Confirmer** .

> [!TIP]
> Pour en savoir plus sur les stratégies prédéfinies, cliquez [ici](../../office-365-security/preset-security-policies.md)

## <a name="your-next-step-is-config-analyzer"></a>L’étape suivante est l’analyseur de configuration

Utilisez l’analyseur de configuration pour déterminer si vos utilisateurs sont configurés conformément aux meilleures pratiques de Microsoft.

> [!TIP]
> L’analyseur de configuration permet aux administrateurs de rechercher et de corriger les stratégies de sécurité où les paramètres sont inférieurs aux paramètres de profil de protection standard ou strict dans les stratégies de sécurité prédéfinies. En savoir plus sur l’analyseur de configuration [ici](../../office-365-security/configuration-analyzer-for-security-policies.md).

Les présélections sécurisées sont toujours recommandées, car elles *garantissent que* les administrateurs appliquent les meilleures pratiques de Microsoft. Toutefois, dans certains cas, des configurations personnalisées sont requises. Découvrez les stratégies personnalisées [ici](../../office-365-security/tenant-wide-setup-for-increased-security.md).

