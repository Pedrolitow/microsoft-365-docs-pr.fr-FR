---
title: Optimiser et corriger les stratégies de sécurité avec l’analyseur de configuration
description: Étapes permettant d’optimiser et de corriger les stratégies de sécurité avec l’analyseur de configuration. L’analyseur de configuration est un emplacement central et un seul volet de verre permettant d’administrer et d’afficher les stratégies de sécurité des e-mails que vous avez configurées dans votre locataire.
search.product: ''
ms.service: microsoft-365-security
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
ms.collection:
- m365-guidance-templates
- m365-security
- tier3
ms.topic: how-to
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: bb801085fecb446ff933f13c9e58dd4975f27225
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68226995"
---
# <a name="optimize-and-correct-security-policies-with-configuration-analyzer"></a>Optimiser et corriger les stratégies de sécurité avec l’analyseur de configuration

L’analyseur de configuration est un emplacement central et un seul volet de verre permettant d’administrer et d’afficher les stratégies de sécurité des e-mails que vous avez configurées dans votre locataire. Vous pouvez effectuer une comparaison côte à côte de vos paramètres avec nos paramètres recommandés Standard et Strict, appliquer des recommandations et afficher les modifications historiques qui ont affecté votre posture.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin
- Exchange Online Protection
- Autorisations suffisantes (rôle Administrateur de sécurité)
- 5 minutes pour effectuer les étapes ci-dessous.

## <a name="compare-settings-and-apply-recommendations"></a>Comparer les paramètres et appliquer des recommandations
1. Accédez à la page [https://security.microsoft.com/configurationAnalyzer](https://security.microsoft.com/configurationAnalyzer).
1. Sélectionnez **des recommandations standard** ou **des recommandations strictes** dans le menu supérieur en fonction de la comparaison côte à côte que vous souhaitez effectuer.
1. Des recommandations pour les modifications de stratégie s’affichent. (Le cas échéant)
1. Vous pouvez ensuite sélectionner une recommandation, noter l’action recommandée, la stratégie à laquelle la recommandation s’applique, définir le nom & configuration actuelle, etc.
1. Avec une recommandation sélectionnée, vous pouvez appuyer sur **Appliquer la recommandation** , puis **SUR OK** sur le message de confirmation qui s’affiche.
1. Si vous souhaitez modifier manuellement une stratégie ou confirmer les paramètres directement dans la stratégie, vous pouvez appuyer sur **Afficher** la stratégie au lieu **d’appliquer une recommandation** qui chargera un nouvel onglet et vous amènera directement à la stratégie concernée pour faciliter la tâche.

## <a name="view-historical-configuration-changes"></a>Afficher les modifications de configuration historiques

Dans **l’analyseur de configuration** , vous pouvez sélectionner **l’analyse de dérive de configuration et l’historique** dans la barre de menus supérieure.

La page qui se charge affiche les modifications apportées à vos stratégies de sécurité dans la plage de temps sélectionnée par les filtres, ainsi que les données relatives à la modification et si elle a augmenté ou diminué votre posture globale.

Pour en savoir plus sur Configuration Analyzer, consultez [l’analyseur de configuration pour les stratégies de sécurité - Office 365 | Microsoft Docs](../../office-365-security/configuration-analyzer-for-security-policies.md).
