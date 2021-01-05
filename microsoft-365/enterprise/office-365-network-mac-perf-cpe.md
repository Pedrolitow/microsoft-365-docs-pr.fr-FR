---
title: Routage réseau Microsoft 365 informé
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/22/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Routage réseau Microsoft 365 informé
ms.openlocfilehash: 367f83684a4a200e3ddd630e1412c756d7093da1
ms.sourcegitcommit: ae646779d84e993cf80b1207e76b856a21be5790
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "49749550"
---
# <a name="microsoft-365-informed-network-routing-preview"></a>Routage réseau Microsoft 365 informé (préversion)

Le routage réseau informé est une fonctionnalité qui intègre différentes applications Microsoft 365 avec des solutions de réseau SD-WAN (Software Defined Network) tierces afin d’optimiser et d’améliorer la connectivité réseau aux points de terminaison de service Microsoft. Une connectivité SD-WAN optimisée peut entraîner des expériences utilisateur et des performances améliorées.

>[!IMPORTANT]
>Le service de routage réseau Microsoft 365 est actuellement en état d’aperçu. Pour plus d’informations sur cet aperçu, y compris des conseils pour recevoir de l’assistance, consultez la rubrique [Microsoft 365 Informed Network Routing public Preview](https://go.microsoft.com/fwlink/?linkid=2151565).

## <a name="overview"></a>Vue d’ensemble

Le routage de réseau informé fournit un canal de partage de données bidirectionnel entre Microsoft et votre solution SD-WAN. Pour chaque emplacement Office et le circuit Internet que vous configurez, Microsoft partage régulièrement les commentaires avec la solution SD-WAN sur la qualité des expériences d’applications Microsoft 365 sélectionnées pour le trafic réseau associé à chaque circuit Internet spécifique. À l’aide de ces commentaires, la solution SD-WAN peut ensuite prendre des actions de récupération intelligente en acheminant le trafic de l’application Microsoft 365 via d’autres liens disponibles. 

Les dégradations de qualité de service dans le chemin d’un circuit Internet particulier, telles qu’une latence accrue ou une perte de paquets élevée, sont difficiles à détecter de façon continue. Ces dégradations peuvent nuire à l’expérience utilisateur pour les applications telles qu’Exchange Online, SharePoint, OneDrive et Microsoft Teams. Les symptômes courants incluent le ralentissement de la recherche de contenu Exchange, des temps de transfert élevés lors de l’interaction avec les bibliothèques de documents SharePoint ou OneDrive, ou une mauvaise qualité des appels ou des réunions dans Microsoft Teams.

Le mécanisme de commentaires et de récupération au sein du réseau de routage informé cherche à détecter de façon dynamique de tels problèmes en temps réel et à la solution SD-WAN déployée pour effectuer des actions de récupération automatique.

Le canal de partage de données est également utilisé pour recevoir régulièrement des données optiques de niveau réseau à partir de la solution SD-WAN, y compris des informations de configuration et des statistiques d’utilisation associées à l’appareil et aux circuits connectés. Aucune information personnelle n’est collectée ou stockée. Toutes les informations collectées sont regroupées sur les emplacements de bureau et les circuits Internet connectés. Ces informations peuvent aider Microsoft à résoudre plus efficacement les problèmes signalés avec votre utilisation des services et applications Microsoft 365.

>[!NOTE]
>Le routage réseau informé de Microsoft 365 prend en charge les clients dans le nuage commercial WW, mais pas dans les nuages de GCC modérés, GCC High, DoD, Germany ou China.

## <a name="requirements"></a>Conditions requises

### <a name="integrated-sd-wan-solutions"></a>Solutions SD-WAN intégrées

Microsoft collabore avec différents partenaires pour permettre l’intégration avec le routage réseau Microsoft 365 informé. Les solutions actuellement activées sont les suivantes :

| Fabricant d’appareils | Nom de solution | Version minimale |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Topologie de réseau

Le routage réseau informé identifie actuellement le trafic associé à un emplacement de bureau spécifique et un circuit Internet basé sur l’adresse IP publique utilisée pour envoyer le trafic réseau à Microsoft. 

Dans le cas où il n’existe pas au moins un circuit réseau offrant un accès direct à Internet à un emplacement de succursale, le routage du réseau peut ne pas fournir de valeur significative.

### <a name="application-usage"></a>Utilisation des applications

Les données de l’expérience d’application (reflétées via les mesures de qualité du réseau) sont collectées par le biais de Microsoft Outlook sur des appareils exécutant Windows, teams, SharePoint et OneDrive. Les autres trafics d’application ne sont pas pris en compte lors de l’évaluation de l’intégrité d’un circuit réseau.

## <a name="enabling-informed-network-routing"></a>Activation du routage de réseau informé

L’activation du routage réseau informé nécessite plusieurs étapes, dont certaines doivent être exécutées au sein de l’interface de configuration de votre solution SD-WAN. Consultez votre fournisseur de solution SD-WAN pour obtenir des instructions sur la façon de lancer le processus d’activation du routage informé du réseau au sein de la solution SD-WAN avant de procéder à la configuration dans le centre d’administration 365 de Microsoft.

Une fois que vous êtes prêt à activer le routage de réseau informé dans le centre d’administration 365 de Microsoft, vérifiez que vous disposez des autorisations d’administrateur global nécessaires.

>[!IMPORTANT]
>Afin de fournir le consentement des autorisations des applications au niveau du client pour la solution SD-WAN sélectionnée pour accéder au canal de partage des données de routage réseau, vous devez effectuer les étapes suivantes en tant qu’administrateur général.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Étape 1 : ouvrir les options de configuration de solution SD-WAN

Dans le [Centre d’administration 365 de Microsoft](https://admin.microsoft.com/), sélectionnez **intégrité > connectivité réseau** dans le volet de navigation de gauche.

Cette section du centre d’administration fournit des mesures de connectivité réseau agrégées pour votre organisation et des conseils sur la façon d’améliorer votre connectivité. Voir [connectivité réseau dans le centre d’administration Microsoft 365 (version préliminaire)](office-365-network-mac-perf-overview.md) pour plus d’informations sur ces fonctionnalités disponibles dans le centre d’administration.

Sélectionnez **paramètres > solution SD-WAN** pour ouvrir le volet de configuration de routage réseau éclairé. Les autres options qui apparaissent sous **paramètres** s’appliquent aux conseils généraux de connectivité réseau dans le centre d’administration et ne sont pas nécessaires pour activer le routage réseau informé.

Dans le volet configuration, sélectionnez **ajouter votre solution SD-WAN (aperçu)**.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>Étape 2 : sélectionnez votre solution SD-WAN et l’emplacement de stockage des données

Dans les zones de liste déroulante, sélectionnez la solution SD-WAN que vous avez déployée et l’emplacement où vous souhaitez que les données associées au routage réseau soient stockées. Pour plus d’informations, consultez la section [stockage des données](#data-storage) .

Sélectionnez **Suivant**.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>Étape 3 : accepter les termes de partage des données

Lisez attentivement les termes fournis associés au partage de données entre Microsoft et votre solution SD-WAN sélectionnée, puis activez la case à cocher indiquée.

Sélectionnez **Suivant**.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>Étape 4 : accorder des autorisations à la solution SD-WAN

Cette étape permet de lancer une demande d’octroi d’autorisations avec Azure Active Directory (Azure AD). Vous serez invité à accorder des autorisations au niveau du client qui permettent à votre solution SD-WAN d’accéder au stockage de données de routage réseau informé et aux informations sur l’état du service associées à votre client. Cette action nécessite des autorisations de rôle d’administrateur général.

Sélectionnez le lien **accorder l’autorisation à cette application** et suivez les demandes Azure ad.

Une fois que vous avez terminé l’octroi des autorisations, sélectionnez **suivant**.

### <a name="step-5-confirm-your-configuration-settings"></a>Étape 5 : confirmez vos paramètres de configuration

La dernière étape de l’activation du routage informé du réseau pour votre client est une page de confirmation qui affiche les paramètres que vous avez fournis. 

Le routage réseau informé est maintenant activé pour votre client.

Sélectionnez **Terminer** , puis fermez le volet Configuration de solution SD-WAN.

## <a name="configuring-network-informed-routing"></a>Configuration du routage informé du réseau

Vous effectuerez une grande partie de la configuration du routage réseau informé au sein de votre solution SD-WAN, telle que la configuration de l’acheminement de votre trafic dans des circonstances normales, ainsi que les chemins d’accès alternatifs qui doivent être utilisés si des problèmes sont détectés. Pour plus d’informations sur ces étapes de configuration, consultez votre fournisseur de solutions SD-WAN.

Chaque emplacement de bureau doit être configuré dans le centre d’administration 365 de Microsoft afin que le routage réseau informé puisse identifier correctement le trafic associé aux circuits réseau assurant la connectivité à ces emplacements.

Les emplacements Office peuvent être détectés automatiquement dans le cadre de la collection de télémétrie réseau de Microsoft en cours. Par conséquent, certains emplacements peuvent être pré-remplis dans le centre d’administration de votre client. 

Si ces emplacements sont précis, il vous suffit d’activer la fonctionnalité de routage réseau informé pour chaque emplacement souhaité et de configurer les circuits Internet et leurs adresses IP publiques. 

Si les emplacements détectés automatiquement ne sont pas précis, ou qu’aucun emplacement n’a été pré-rempli dans votre client, vous devez ajouter ou modifier les emplacements manuellement pour refléter une topologie précise de votre organisation.

### <a name="updating-locations"></a>Mise à jour des emplacements

Vous pouvez trouver les emplacements de votre client dans l’onglet **emplacements** . Les emplacements peuvent être modifiés directement dans la liste ou mis à jour à l’aide d’un fichier CSV.

Assurez-vous que chaque emplacement de bureau pour lequel vous souhaitez activer un routage de réseau informé est présent dans cette liste.

>[!NOTE]
>Les colonnes de la liste **emplacements** pour les échantillons collectés et d’autres informations relatives à l’évaluation ne sont pas liées à la fonctionnalité de routage réseau informé.

### <a name="enabling-a-location-for-informed-network-routing"></a>Activation d’un emplacement pour le routage réseau informé

1. Dans la liste **emplacements** , sélectionnez **modifier** dans le menu actions rapides pour ouvrir le volet Configuration de l’emplacement.

2. Sélectionnez **utiliser le routage réseau Microsoft 365 informé à cet emplacement**.

3. Ajoutez tous les circuits réseau fournissant une connectivité Internet à cet emplacement de bureau dans la section **plages d’adresses IP sortantes à cet emplacement Office** . Assurez-vous que chaque circuit est associé aux sous-réseaux d’adresses IP publiques uniques représentant votre trafic réseau.

4. Sélectionnez **Enregistrer** pour enregistrer vos modifications.

## <a name="disabling-network-informed-routing"></a>Désactivation du routage informé du réseau

La fonctionnalité de routage réseau informé peut être désactivée pour l’ensemble du client en redéfinissant les paramètres de votre solution SD-WAN. Bien que cette opération arrête tout le traitement des données au sein de Microsoft 365, vous devez également désactiver le routage informé du réseau dans le centre d’administration.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Étape 1 : ouvrir les options de configuration de solution SD-WAN

Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/) , sélectionnez **intégrité > connectivité réseau** dans le volet de navigation de gauche.

Sélectionnez **paramètres > solution SD-WAN** pour ouvrir le volet de configuration de routage réseau éclairé.

Le volet de configuration affiche un résumé de votre solution SD-WAN actuellement configurée.

### <a name="step-2-reset-your-configuration"></a>Étape 2 : réinitialiser votre configuration

Dans le volet configuration, sélectionnez **Réinitialiser les paramètres de votre solution SD-WAN**.

Vos paramètres ont été réinitialisés et le routage réseau est informé. Vous pouvez le réactiver à tout moment en suivant les étapes indiquées dans [activation du routage réseau informé](#enabling-informed-network-routing).

## <a name="data-storage"></a>Stockage des données

Les données échangées entre Microsoft et le fournisseur de solution SD-WAN sont stockées dans l’emplacement de stockage de données sélectionné lors de l’activation initiale du routage réseau. Les options d’emplacement de stockage de données représentent les zones géographiques contenant des régions Microsoft Azure où les données sont stockées.

>[!NOTE]
>Lors de la phase d’évaluation, le seul emplacement de stockage de données disponible est l' **Amérique du Nord**. Des emplacements de stockage de données supplémentaires seront disponibles avant la disponibilité générale du routage réseau informé.

Les données sont conservées à cet emplacement pendant une période de 30 jours. Lorsque ce dernier est désactivé, toutes les données restantes sont supprimées dans cette fenêtre de rétention de 30 jours.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le centre d’administration Microsoft 365 (version d’évaluation)](office-365-network-mac-perf-overview.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-location-services.md)
