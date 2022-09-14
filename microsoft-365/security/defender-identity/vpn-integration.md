---
title: Microsoft Defender pour Identity intégration VPN dans Microsoft 365 Defender
description: Découvrez comment collecter des informations comptables en intégrant un VPN pour Microsoft Defender pour Identity dans Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 02a0ecf0dea5b4e3fc820280a389c30b79b5fb43
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67682280"
---
# <a name="defender-for-identity-vpn-integration-in-microsoft-365-defender"></a>Intégration de Defender pour Identity VPN dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment intégrer un VPN à [Microsoft Defender pour Identity](/defender-for-identity) dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, certaines options et détails ont changé à partir de leur emplacement dans le portail Defender pour Identity. Lisez les détails ci-dessous pour découvrir où trouver les fonctionnalités familières et nouvelles.

[!INCLUDE [Product long](includes/product-long.md)] peut collecter des informations comptables à partir de solutions VPN. Lorsque la page de profil de l’utilisateur est configurée, elle inclut les informations des connexions VPN, telles que les adresses IP et les emplacements d’origine des connexions. Ce processus complète l’examen en fournissant des informations supplémentaires sur l’activité des utilisateurs, ainsi qu’une nouvelle détection des connexions VPN anormales. L’appel pour résoudre une adresse IP externe vers un emplacement est anonyme. Aucun identificateur personnel n’est envoyé dans cet appel.

[!INCLUDE [Product short](includes/product-short.md)] s’intègre à votre solution VPN en écoutant les événements comptables RADIUS transférés aux [!INCLUDE [Product short](includes/product-short.md)] capteurs. Ce mécanisme est basé sur la comptabilité RADIUS standard ([RFC 2866](https://tools.ietf.org/html/rfc2866)) et les fournisseurs VPN suivants sont pris en charge :

- Microsoft
- F5
- Check Point
- Cisco ASA

## <a name="prerequisites"></a>Prerequisites

Pour activer l’intégration VPN, veillez à définir les paramètres suivants :

- Ouvrez le port UDP 1813 sur vos [!INCLUDE [Product short](includes/product-short.md)] capteurs et/ou [!INCLUDE [Product short](includes/product-short.md)] capteurs autonomes.

> [!NOTE]
>
> - En activant **Radius Accounting**, le [!INCLUDE [Product short](includes/product-short.md)] capteur active une stratégie de pare-feu Windows préprovisionnée appelée **[!INCLUDE [Product long](includes/product-long.md)] Capteur** pour autoriser la comptabilité RADIUS entrante sur le port UDP 1813.
> - L’intégration VPN n’est pas prise en charge dans les environnements conformes aux normes fédérales de traitement de l’information (FIPS)

L’exemple ci-dessous utilise le routage Microsoft et le serveur d’accès à distance (RRAS) pour décrire le processus de configuration VPN.

Si vous utilisez une solution VPN tierce, consultez sa documentation pour obtenir des instructions sur l’activation de RADIUS Accounting.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>Configurer RADIUS Accounting sur le système VPN

Effectuez les étapes suivantes sur votre serveur RRAS.

1. Ouvrez la console **Routage et Accès à distance** .
1. Cliquez avec le bouton droit sur le nom du serveur, puis sélectionnez **Propriétés**.
1. Sous l’onglet **Sécurité** , sous **Fournisseur de comptabilité**, sélectionnez **RADIUS Accounting** , puis **Configurer**.

   :::image type="content" source="../../media/defender-identity/radius-setup.png" alt-text="Le programme d’installation de RADIUS" lightbox="../../media/defender-identity/radius-setup.png":::

1. Dans la fenêtre **Ajouter un serveur RADIUS** , tapez le **nom** du serveur du capteur le plus proche [!INCLUDE [Product short](includes/product-short.md)] (qui a une connectivité réseau). Pour la haute disponibilité, vous pouvez ajouter des capteurs supplémentaires [!INCLUDE [Product short](includes/product-short.md)] en tant que serveurs RADIUS. Sous **Port**, vérifiez que la valeur par défaut de 1813 est configurée. Sélectionnez **Modifier** et tapez une nouvelle chaîne secrète partagée de caractères alphanumériques. Notez la nouvelle chaîne de secret partagé, car vous devrez la remplir ultérieurement lors [!INCLUDE [Product short](includes/product-short.md)] de la configuration. Cochez la boîte **de dialogue Envoyer un compte RADIUS activé et comptabilisant les messages** , puis sélectionnez **OK** dans toutes les boîtes de dialogue ouvertes.

   :::image type="content" source="../../media/defender-identity/vpn-set-accounting.png" alt-text="Configuration du VPN" lightbox="../../media/defender-identity/vpn-set-accounting.png":::

## <a name="configure-vpn-in-defender-for-identity"></a>Configurer un VPN dans Defender pour Identity

[!INCLUDE [Product short](includes/product-short.md)] collecte des données VPN qui permettent de profiler les emplacements à partir desquelles les ordinateurs se connectent au réseau et de détecter les connexions VPN suspectes.

Pour configurer des données VPN dans [!INCLUDE [Product short](includes/product-short.md)] Microsoft 365 Defender :

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, accédez aux **paramètres**, puis **aux identités**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités sous l’élément de menu Paramètres" lightbox="../../media/defender-identity/settings-identities.png":::

1. Sélectionnez **VPN**.
1. Sélectionnez **Activer la comptabilité de rayon** et tapez le **secret partagé** que vous avez configuré précédemment sur votre serveur VPN RRAS. Sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/defender-identity/vpn-integration.png" alt-text="Intégration VPN" lightbox="../../media/defender-identity/vpn-integration.png":::

Une fois cette option activée, tous les capteurs Defender pour Identity écoutent sur le port 1813 les événements de comptabilité RADIUS, et votre configuration VPN est terminée.

Une fois que le capteur Defender pour Identity reçoit les événements VPN et les envoie au service cloud Defender pour Identity à des fins de traitement, le profil d’entité indique des emplacements et des activités VPN accessibles distincts dans le profil.

## <a name="see-also"></a>Voir aussi

- [Examiner les alertes dans Microsoft 365 Defender](../defender/investigate-alerts.md)
