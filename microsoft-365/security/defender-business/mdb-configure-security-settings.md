---
title: Configurer vos paramètres de sécurité dans Microsoft Defender entreprise
description: Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender pour les entreprises
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/29/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365initiative-defender-business
ms.openlocfilehash: 7faefe829bc9ebdbc718e6c7ec370ceca612445a
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "62244594"
---
# <a name="configure-your-security-settings-and-policies-in-microsoft-defender-for-business-preview"></a>Configurer vos paramètres et stratégies de sécurité dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Une fois que vous avez intégré les appareils de votre entreprise à Microsoft Defender pour Entreprises (prévisualisation), l’étape suivante consiste à afficher et, si nécessaire, à modifier vos paramètres et stratégies de sécurité. Dans Defender pour Entreprise (prévisualisation), les paramètres de sécurité sont appliqués aux appareils par le biais de stratégies. Ces stratégies sont appliquées aux [groupes d’appareils.](mdb-create-edit-device-groups.md#what-is-a-device-group) 

Vous pouvez également configurer d’autres paramètres dans Defender for Business (prévisualisation). Ces paramètres incluent votre fuseau horaire, la réception ou non des fonctionnalités d’aperçu, et bien plus encore.

## <a name="what-to-do"></a>Procédure

1. [Obtenir une vue d’ensemble rapide des stratégies de sécurité par défaut dans Defender for Business](#default-policies-in-defender-for-business)

2. [Choisissez où gérer vos stratégies et appareils de sécurité.](#choose-where-to-manage-security-policies-and-devices)

3. [Afficher vos stratégies de sécurité.](#view-your-security-policies)

4. [Afficher et modifier d’autres paramètres dans le portail Microsoft 365 Defender web](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal) 

5. [Procédez comme vous le faire pour les étapes suivantes.](#next-steps)

## <a name="default-policies-in-defender-for-business"></a>Stratégies par défaut dans Defender for Business

Defender for Business (aperçu) inclut des stratégies par défaut qui utilisent les paramètres recommandés. Ces stratégies sont les suivantes :

- [Les paramètres de protection nouvelle](mdb-next-gen-configuration-settings.md) génération qui déterminent la configuration Antivirus Microsoft Defender et d’autres fonctionnalités de protection contre les menaces ; et 
- [Paramètres de pare-feu](mdb-firewall.md) qui déterminent le trafic réseau autorisé à circuler vers et depuis les appareils clients Windows de votre entreprise.

Vous pouvez appliquer vos stratégies par défaut aux Windows clients pendant le processus de configuration initial. Vous pouvez également définir de nouvelles stratégies et modifier des stratégies existantes en fonction des besoins de votre entreprise. 

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Choisir où gérer les stratégies et les appareils de sécurité

Defender for Business (prévisualisation) propose un processus [de configuration simplifié](mdb-simplified-configuration.md) qui simplifie le processus d’installation et de configuration. Si vous sélectionnez le processus de configuration simplifié, vous pouvez afficher et gérer vos stratégies de sécurité dans le portail Microsoft 365 Defender ( [https://security.microsoft.com/](https://security.microsoft.com/) ). Toutefois, vous n’êtes pas limité à cette option. Si vous avez utilisé Microsoft Endpoint Manager (qui inclut Microsoft Intune) ou une solution de productivité non Microsoft pour gérer vos stratégies et appareils de sécurité, vous pouvez continuer à utiliser votre solution actuelle.

Le tableau suivant peut vous aider à choisir l’endroit où gérer vos stratégies et appareils de sécurité. <br/><br/>

| Option | Description |
|:---|:---|
| **Utiliser les stratégies et paramètres de** sécurité par défaut dans le portail Microsoft 365 Defender *(recommandé)* | Defender pour les entreprises (prévisualisation) a été conçu pour les petites et moyennes entreprises occupées à l’esprit. Les stratégies et paramètres de sécurité par défaut dans Defender pour les entreprises sont conçus pour protéger les appareils de votre entreprise dès le premier jour.<br/><br/>Vous pouvez utiliser le portail Microsoft 365 Defender ( ) pour afficher et gérer vos [https://security.microsoft.com/](https://security.microsoft.com/) paramètres et stratégies de sécurité.<br/><br/>Pour plus d’informations, voir [Afficher ou modifier des stratégies d’appareil.](mdb-view-edit-policies.md) |
| **Utiliser Microsoft Endpoint Manager** | Si votre entreprise utilise Microsoft Endpoint Manager pour gérer les paramètres et stratégies de sécurité, vous pouvez continuer à utiliser Endpoint Manager et appliquer des stratégies et paramètres de sécurité à certains appareils ou à tous. Pour plus d’informations, voir [Gérer la sécurité des appareils avec les stratégies](/mem/intune/protect/endpoint-security-policy)de sécurité des points de terminaison dans Microsoft Intune . <br/><br/>Envisagez de passer au [processus de configuration simplifiée dans Defender pour Entreprise.](mdb-simplified-configuration.md) Si vous faites le changement, vous serez invité à supprimer les stratégies de sécurité existantes dans Microsoft Endpoint Manager avant de poursuivre le processus de configuration simplifié dans Defender for Business. La suppression de vos stratégies dans Microsoft Endpoint Manager éviter les conflits de stratégie ultérieurement. |

> [!TIP]
> Si vous souhaitez vous inscrire au programme d’aperçu de Microsoft Defender entreprise, visitez [https://aka.ms/MDB-Preview](https://aka.ms/MDB-Preview) . Pour plus d’informations, [voir Obtenir Microsoft Defender entreprise (prévisualisation).](get-defender-business.md)

## <a name="view-your-security-policies"></a>Afficher vos stratégies de sécurité

Pour afficher votre liste de stratégies de sécurité, utilisez l’une des procédures du tableau suivant :
<br/><br/>

| Portail | Procedure |
|:---|:---|
| Microsoft 365 Defender portail ( [https://security.microsoft.com](https://security.microsoft.com) ) | 1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), and sign in. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil.** Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients).**<br/><br/>4. Développez une catégorie (telle que la protection nouvelle génération ou le **pare-feu)** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Comprendre les paramètres de configuration nouvelle génération](mdb-next-gen-configuration-settings.md)<br/>- [Paramètres du pare-feu](mdb-firewall.md)  |
| Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) | 1. Go to [https://endpoint.microsoft.com](https://endpoint.microsoft.com) and sign in. Vous êtes maintenant dans le centre d Microsoft Endpoint Manager’administration.<br/><br/>2. Sélectionnez **Sécurité des points de terminaison.**<br/><br/>3. Sélectionnez une catégorie, telle **qu’Antivirus,** **Pare-feu,** Détection et réponse des points de terminaison ou Réduction de la **surface** d’attaque pour afficher les stratégies de cette catégorie. <br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Microsoft Endpoint Manager, commencez par gérer la sécurité des points de terminaison [dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Afficher et modifier d’autres paramètres dans le portail Microsoft 365 Defender web

Outre les stratégies de sécurité appliquées aux appareils, il existe d’autres paramètres que vous pouvez afficher et modifier dans Defender for Business (prévisualisation). Par exemple, vous spécifiez le fuseau horaire à utiliser, et vous pouvez intégrer (ou horsboard) des appareils. 

> [!NOTE]
> Vous pouvez voir plus de paramètres dans votre client que ceux répertoriés dans cet article. Nous allons mettre en surbrillance les paramètres que vous devez examiner dans Defender for Business (prévisualisation).

### <a name="settings-to-review-for-defender-for-business"></a>Paramètres à réviser pour Defender for Business

Le tableau suivant décrit les paramètres à afficher (et si nécessaire, modifier) dans Defender pour Entreprise (prévisualisation).

<br/><br/>

| Catégorie | Paramètre | Description |
|:---|:---|:---|
| **Centre de sécurité** | **Fuseau horaire** | Sélectionnez le fuseau horaire à utiliser pour les dates et heures affichées dans les incidents, les menaces détectées et les examens automatisés & correction. Vous pouvez utiliser l’heure UTC ou votre fuseau horaire local *(recommandé).*  |
| **Microsoft 365 Defender** | **Account** | Afficher des détails, tels que l’endroit où vos données sont stockées, votre ID de client et votre ID d’entreprise (organisation). |
| **Microsoft 365 Defender**  | **Fonctionnalités en préversion**  | Activer les fonctionnalités d’aperçu pour essayer les fonctionnalités à venir et les nouvelles fonctionnalités. Vous pouvez être parmi les premiers à afficher un aperçu des nouvelles fonctionnalités et à fournir des commentaires. |
| **Points de terminaison**  | **Notifications par courrier électronique** | Configurer ou modifier vos règles de notification par courrier électronique. Lorsque des vulnérabilités sont détectées ou qu’une alerte est créée, les destinataires spécifiés dans vos règles de notification par courrier électronique reçoivent un e-mail. [En savoir plus sur les notifications par courrier électronique.](mdb-email-notifications.md) |
| **Points de terminaison**   | **Gestion des appareils**  >  **Intégration** | Intégrer des appareils à Defender for Business à l’aide d’un script téléchargeable. Pour plus d’informations, [voir Intégrer un appareil à l’aide d’un script local dans Defender for Business.](mdb-onboard-devices.md#onboard-a-device-using-a-local-script-in-defender-for-business)   |  
| **Points de terminaison**  |  **Gestion des appareils**  >  **Offboarding** | Déboard (supprimer) des appareils de Defender for Business (prévisualisation). Lorsque vousboardez un appareil, il n’envoie plus de données à Defender for Business (prévisualisation), mais les données reçues avant laboardisation sont conservées. Pour plus d’informations, voir [« Horsboard » d’un appareil.](mdb-onboard-devices.md#what-if-i-want-to-offboard-a-device)  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Accéder à vos paramètres dans le portail Microsoft 365 Defender web

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com/](https://security.microsoft.com/) ), and sign in.

2. Sélectionnez **Paramètres,** puis sélectionnez une catégorie (par **exemple,** Centre de sécurité, **Microsoft 365 Defender** ou Points **de terminaison).**

3. Dans la liste des paramètres, sélectionnez un élément à afficher ou à modifier.


## <a name="next-steps"></a>Prochaines étapes

Procédez à une ou plusieurs des tâches suivantes :

- [Commencer à utiliser Microsoft Defender pour les entreprises (prévisualisation)](mdb-get-started.md)

- [Gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation)](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Afficher ou modifier des stratégies dans Microsoft Defender entreprise (prévisualisation)](mdb-view-edit-policies.md)

