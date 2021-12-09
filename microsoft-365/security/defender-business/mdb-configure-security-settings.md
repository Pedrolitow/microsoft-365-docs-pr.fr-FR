---
title: Configurer vos paramètres de sécurité dans Microsoft Defender entreprise
description: Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les entreprises
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/08/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 3d6d1a0b4099e52124a4965061fe85f46049815b
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61375226"
---
# <a name="configure-your-security-settings-and-policies-in-microsoft-defender-for-business"></a>Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les entreprises

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

Une fois que vous avez intégré les appareils de votre entreprise à Microsoft Defender pour Entreprises, l’étape suivante consiste à afficher et, si nécessaire, à modifier vos paramètres et stratégies de sécurité. 

## <a name="what-to-do"></a>Procédure

1. [Choisissez où gérer vos paramètres et stratégies de sécurité.](#choose-where-to-manage-security-settings-and-policies)

2. [Afficher vos paramètres et stratégies de sécurité.](#view-your-security-settings-and-policies) 

3. [Procédez comme vous le faire pour les étapes suivantes.](#next-steps)

## <a name="choose-where-to-manage-security-settings-and-policies"></a>Choisir où gérer les paramètres et stratégies de sécurité

En ce qui concerne la gestion de vos paramètres et stratégies de sécurité, vous pouvez choisir parmi plusieurs options, comme décrit dans le tableau suivant : <br/><br/>

| Option | Description |
|:---|:---|
| **Utiliser les stratégies et paramètres de** sécurité par défaut dans le portail Microsoft 365 Defender *(recommandé)* | Defender for Business a été conçu pour les petites et moyennes entreprises occupées à l’esprit. Les stratégies et paramètres de sécurité par défaut dans Defender pour les entreprises sont conçus pour protéger les appareils de votre entreprise dès le premier jour.<br/><br/>Vous pouvez utiliser le portail Microsoft 365 Defender ( ) pour afficher et gérer vos [https://security.microsoft.com/](https://security.microsoft.com/) paramètres et stratégies de sécurité.<br/><br/>Pour plus d’informations, voir [Afficher ou modifier des stratégies d’appareil.](mdb-view-edit-policies.md) |
| **Utiliser Microsoft Endpoint Manager** | Si votre entreprise utilise Microsoft Endpoint Manager pour gérer les paramètres et stratégies de sécurité, vous pouvez continuer à utiliser Endpoint Manager et appliquer des stratégies et paramètres de sécurité à certains appareils ou à tous. Pour plus d’informations, voir [Gérer la sécurité des appareils avec les stratégies](/mem/intune/protect/endpoint-security-policy)de sécurité des points de terminaison dans Microsoft Intune . <br/><br/>Envisagez de passer au [processus de configuration simplifiée dans Defender pour Entreprise.](mdb-simplified-configuration.md) Si vous faites le changement, vous serez invité à supprimer les stratégies de sécurité existantes dans Microsoft Endpoint Manager avant de poursuivre le processus de configuration simplifié dans Defender for Business. La suppression de vos stratégies dans Microsoft Endpoint Manager éviter les conflits de stratégie ultérieurement. |

> [!TIP]
> Si vous souhaitez vous inscrire au programme d’aperçu de Microsoft Defender entreprise, visitez [https://aka.ms/MDB-Preview](https://aka.ms/MDB-Preview) . Pour plus d’informations, [voir Obtenir Microsoft Defender pour Entreprise.](get-defender-business.md)

## <a name="view-your-security-settings-and-policies"></a>Afficher vos paramètres et stratégies de sécurité

Pour afficher vos paramètres et stratégies de sécurité, utilisez l’une des procédures du tableau suivant :
<br/><br/>

| Portail | Procedure |
|:---|:---|
| Microsoft 365 Defender portail ( [https://security.microsoft.com](https://security.microsoft.com) ) | 1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), and sign in. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil.** Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients).**<br/><br/>4. Développez une catégorie (telle que la protection nouvelle génération ou le **pare-feu)** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Comprendre les paramètres de configuration nouvelle génération](mdb-next-gen-configuration-settings.md)<br/>- [Paramètres du pare-feu](mdb-firewall.md)  |
| Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) | 1. Go to [https://endpoint.microsoft.com](https://endpoint.microsoft.com) and sign in. Vous êtes maintenant dans le centre d Microsoft Endpoint Manager’administration.<br/><br/>2. Sélectionnez **Sécurité des points de terminaison.**<br/><br/>3. Sélectionnez une catégorie, telle **qu’Antivirus,** **Pare-feu,** Détection et réponse des points de terminaison ou Réduction de la **surface** d’attaque pour afficher les stratégies de cette catégorie. <br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Microsoft Endpoint Manager, commencez par gérer la sécurité des points de terminaison [dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="next-steps"></a>Prochaines étapes

Procédez à une ou plusieurs des tâches suivantes :

- [Commencer à utiliser Microsoft Defender pour les entreprises](mdb-get-started.md)

- [Gérer les appareils dans Microsoft Defender pour les entreprises](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Afficher ou modifier des stratégies dans Microsoft Defender entreprise](mdb-view-edit-policies.md)

