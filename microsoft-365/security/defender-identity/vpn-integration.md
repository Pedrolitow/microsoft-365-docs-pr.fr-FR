---
title: Intégration VPN Microsoft Defender pour l’identité dans Microsoft 365 Defender
description: Découvrez comment collecter des informations de comptabilité en intégrant un VPN pour Microsoft Defender pour l’identité dans Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.openlocfilehash: e6b8015cc8b6ac073c689bde3b15a411c859cada
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58561277"
---
# <a name="defender-for-identity-vpn-integration-in-microsoft-365-defender"></a>Intégration VPN De Defender pour l’identité dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment intégrer un VPN à [Microsoft Defender pour l’identité](/defender-for-identity) [dans Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender for Identity. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

[!INCLUDE [Product long](includes/product-long.md)] peut collecter des informations de comptabilité à partir de solutions VPN. Lorsque la page de profil de l’utilisateur est configurée, elle inclut les informations des connexions VPN, telles que les adresses IP et les emplacements d’origine des connexions. Ce processus complète l’examen en fournissant des informations supplémentaires sur l’activité des utilisateurs, ainsi qu’une nouvelle détection des connexions VPN anormales. L’appel de résolution d’une adresse IP externe à un emplacement est anonyme. Aucun identificateur personnel n’est envoyé dans cet appel.

[!INCLUDE [Product short](includes/product-short.md)] s’intègre à votre solution VPN en écouteant les événements de comptabilité RADIUS transmis aux [!INCLUDE [Product short](includes/product-short.md)] capteurs. Ce mécanisme est basé sur la comptabilité RADIUS standard ([RFC 2866](https://tools.ietf.org/html/rfc2866)), et les fournisseurs VPN suivants sont pris en charge :

- Microsoft
- F5
- Point de contrôle
- Cisco ASA

## <a name="prerequisites"></a>Configuration requise

Pour activer l’intégration VPN, veillez à définir les paramètres suivants :

- Ouvrez le port UDP 1813 sur vos [!INCLUDE [Product short](includes/product-short.md)] capteurs et/ou capteurs [!INCLUDE [Product short](includes/product-short.md)] autonomes.

> [!NOTE]
>
> - En **activant Radius Accounting,** le capteur active une stratégie de pare-feu Windows pré-mise en service appelée Capteur pour autoriser la comptabilité RADIUS entrante sur le [!INCLUDE [Product short](includes/product-short.md)] port UDP 1813. **[!INCLUDE [Product long](includes/product-long.md)]**
> - L’intégration VPN n’est pas prise en charge dans les environnements respectant les normes FIPS (Federal Information Processing Standards)

L’exemple ci-dessous utilise Le routage Microsoft et le serveur d’accès à distance (RRAS) pour décrire le processus de configuration VPN.

Si vous utilisez une solution VPN tierce, consultez leur documentation pour obtenir des instructions sur la façon d’activer la comptabilité RADIUS.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>Configurer la comptabilité RADIUS sur le système VPN

Effectuez les étapes suivantes sur votre serveur RRAS.

1. Ouvrez **la console Routage et accès** à distance.
1. Cliquez avec le bouton droit sur le nom du serveur et sélectionnez **Propriétés.**
1. Dans **l’onglet Sécurité,** sous **Fournisseur de comptabilité,** sélectionnez **RADIUS Accounting** et **sélectionnez Configurer**.

    ![Configuration RADIUS.](../../media/defender-identity/radius-setup.png)

1. Dans la **fenêtre Ajouter un serveur RADIUS,** tapez le nom **du** serveur du capteur le plus proche [!INCLUDE [Product short](includes/product-short.md)] (qui dispose d’une connectivité réseau). Pour la haute disponibilité, vous pouvez ajouter des capteurs [!INCLUDE [Product short](includes/product-short.md)] supplémentaires en tant que serveurs RADIUS. Sous **Port,** assurez-vous que la valeur par défaut de 1813 est configurée. Sélectionnez **Modifier** et tapez une nouvelle chaîne secrète partagée de caractères alphanumériques. Notez la nouvelle chaîne secrète partagée, car vous devrez la remplir ultérieurement pendant la [!INCLUDE [Product short](includes/product-short.md)] configuration. **Cochez la case Envoyer un compte RADIUS et** tenir compte des messages et sélectionnez **OK** dans toutes les boîtes de dialogue ouvertes.

    ![Configuration VPN.](../../media/defender-identity/vpn-set-accounting.png)

## <a name="configure-vpn-in-defender-for-identity"></a>Configurer vpn dans Defender pour l’identité

[!INCLUDE [Product short](includes/product-short.md)] collecte des données VPN qui permettent de profiler les emplacements à partir des lesquels les ordinateurs se connectent au réseau et de détecter les connexions VPN suspectes.

Pour configurer les données VPN dans [!INCLUDE [Product short](includes/product-short.md)] Microsoft 365 Defender :

1. In [Microsoft 365 Defender](https://security.microsoft.com/), go to **Paramètres** and then **Identities**.

    ![Go to Paramètres, then Identities.](../../media/defender-identity/settings-identities.png)

1. Sélectionnez **VPN**.
1. Sélectionnez **Activer la comptabilité du** rayon et tapez la secret **partagé** que vous avez configurée précédemment sur votre serveur VPN RRAS. Sélectionnez **Enregistrer**.

    ![Intégration VPN.](../../media/defender-identity/vpn-integration.png)

Une fois cette opération activée, tous les capteurs Defender for Identity écoutent le port 1813 pour les événements de comptabilité RADIUS, et votre configuration VPN est terminée.

Une fois que le capteur Defender pour l’identité a reçu les événements VPN et les a envoyés au service cloud de Defender for Identity pour traitement, le profil d’entité indique des emplacements VPN et des activités VPN distincts dans le profil indiquent les emplacements.

## <a name="see-also"></a>Voir aussi

- [Examiner les alertes dans Microsoft 365 Defender](../defender/investigate-alerts.md)
