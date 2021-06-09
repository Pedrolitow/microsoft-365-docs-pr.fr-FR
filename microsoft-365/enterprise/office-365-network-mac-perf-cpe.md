---
title: Microsoft 365 routage réseau informé
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/10/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 routage réseau informé
ms.openlocfilehash: 5275f8ea55afaf621555b440e7fae4a6d11cad91
ms.sourcegitcommit: 6e4ddf35aaf747599f476f9988bcef02cacce1b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2021
ms.locfileid: "50717591"
---
# <a name="microsoft-365-informed-network-routing-preview"></a>Microsoft 365 routage réseau informé (aperçu)

Le routage réseau informé est une fonctionnalité qui intègre diverses applications Microsoft 365 à des solutions de réseau SD-WAN (Software Defined Network) tierces afin d’optimiser et d’améliorer votre connectivité réseau aux points de terminaison du service Microsoft. Une connectivité SD-WAN optimisée peut améliorer les performances et les expériences utilisateur.

>[!IMPORTANT]
>Microsoft 365 routage réseau informé est actuellement en état d’aperçu. Pour plus d’informations sur cette prévisualisation, notamment des conseils pour la réception de l’assistance, voir Microsoft 365 la prévisualisation publique du [routage réseau informé.](https://go.microsoft.com/fwlink/?linkid=2151565)

## <a name="overview"></a>Vue d’ensemble

Le routage réseau informé fournit un canal de partage de données bi-directionnel entre Microsoft et votre solution SD-WAN. Pour chaque emplacement de bureau et circuit Internet que vous configurez, Microsoft partage régulièrement des commentaires avec la solution SD-WAN sur la qualité des expériences d’application Microsoft 365 sélectionnées pour le trafic réseau associé à chaque circuit Internet spécifique. À l’aide de ce commentaire, la solution SD-WAN peut ensuite prendre des mesures de récupération intelligentes en routant le trafic Microsoft 365'application via d’autres liaisons disponibles. 

Les dégradations de qualité de service dans le chemin d’accès d’un circuit Internet particulier, telles que l’augmentation de la latence ou la perte de paquets élevée, sont difficiles à détecter en permanence. Ces dégradations peuvent nuire aux expériences utilisateur pour des applications telles que Exchange Online, SharePoint, OneDrive et Microsoft Teams. Les symptômes courants incluent la lenteur de recherche de contenu Exchange, les temps de transfert élevés lors de l’interaction avec les bibliothèques de documents SharePoint ou OneDrive, ou la qualité médiocre des appels ou des réunions dans Microsoft Teams.

Le mécanisme de commentaires et de récupération au sein du routage informé du réseau cherche à détecter dynamiquement ces problèmes en temps quasi réel et informe la solution SD-WAN déployée de prendre des mesures de récupération automatique.

Le canal de partage de données est également utilisé pour recevoir régulièrement des données optiques au niveau du réseau à partir de la solution SD-WAN, y compris les informations de configuration et les statistiques d’utilisation associées à l’appareil et aux circuits attachés. Aucune information personnelle n’est collectée ou stockée. Toutes les informations collectées sont agrégées aux emplacements de bureau et aux circuits Internet connectés. Ces informations peuvent aider Microsoft à résoudre plus efficacement et plus efficacement les problèmes signalés lors de l’utilisation de Microsoft 365 services et d’applications.

>[!NOTE]
>Microsoft 365 routage réseau informé prend en charge les locataires dans le cloud commercial WW, mais pas les clouds Cloud de la communauté du secteur public Modéré, Cloud de la communauté du secteur public Haut, DoD, Allemagne ou Chine.

## <a name="requirements"></a>Conditions requises

### <a name="integrated-sd-wan-solutions"></a>Solutions SD-WAN intégrées

Microsoft travaille avec différents partenaires pour permettre l’intégration avec Microsoft 365 routage réseau informé. Les solutions actuellement activées sont les suivantes :

| Device Maker | Nom de solution | Version minimale |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Topologie de réseau

Le routage réseau informé identifie actuellement le trafic associé à un emplacement de bureau et à un circuit Internet spécifiques en fonction de l’adresse IP publique utilisée pour envoyer le trafic réseau à Microsoft. 

Dans le cas où il n’existe pas au moins un circuit réseau fournissant un accès Internet direct à un emplacement de succursale, le routage informé du réseau peut ne pas fournir de valeur significative.

### <a name="application-usage"></a>Utilisation des applications

Les données d’expérience d’application (reflétées par les mesures de qualité du réseau) sont collectées par le biais de l’utilisation d’applications clientes Microsoft spécifiques. Exchange mesure reflètent l’utilisation du client Outlook ainsi que certaines Outlook’utilisation de Web App. SharePoint et OneDrive mesure reflètent l’utilisation des points de terminaison propres SharePoint client, quelle que soit l’application cliente. Teams mesure reflètent l’utilisation du client Teams bureau. Le trafic d’autres applications n’est pas pris en compte lors de l’évaluation de l’état d’un circuit réseau.

## <a name="enabling-informed-network-routing"></a>Activation du routage réseau informé

L’activation du routage réseau informé nécessite plusieurs étapes, dont certaines devront être effectuées dans l’interface de configuration de votre solution SD-WAN. Consultez le fournisseur de votre solution SD-WAN pour obtenir des instructions sur la façon de lancer le processus d’activation du routage en connaissance de réseau au sein de la solution SD-WAN avant de poursuivre la configuration dans le Centre d’administration Microsoft 365.

Une fois que vous êtes prêt à activer le routage réseau informé dans le Centre d’administration Microsoft 365, assurez-vous que vous avez les autorisations d’administrateur général nécessaires.

>[!IMPORTANT]
>Pour fournir le consentement nécessaire aux autorisations d’applications au niveau du client pour que la solution SD-WAN sélectionnée accède au canal de partage de données de routage réseau informé, vous devez effectuer les étapes suivantes en tant qu’administrateur général.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Étape 1 : Ouvrir les options de configuration d’une solution SD-WAN

Dans le [Microsoft 365 d’administration,](https://admin.microsoft.com/)sélectionnez > l’état d'> connectivité réseau dans le volet de navigation gauche. 

Cette section du Centre d’administration fournit des mesures agrégées de connectivité réseau pour votre organisation et des conseils sur la façon d’améliorer votre connectivité. Pour plus d’informations sur ces fonctionnalités disponibles dans le [centre d’administration, voir](office-365-network-mac-perf-overview.md) connectivité réseau dans le Centre d’administration Microsoft 365 (prévisualisation).

Sélectionnez **Paramètres > solution SD-WAN pour** ouvrir le volet de configuration du routage réseau informé. Les autres options qui s’affichent **sous Paramètres** s’appliquent aux conseils généraux sur la connectivité réseau dans le Centre d’administration et ne sont pas nécessaires pour activer le routage réseau informé.

Dans le volet de configuration, **sélectionnez Ajouter votre solution SD-WAN (prévisualisation).**

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>Étape 2 : Sélectionnez votre solution SD-WAN et l’emplacement de stockage des données

Dans les zones de la zone de drop-down, sélectionnez la solution SD-WAN que vous avez déployée et l’emplacement où vous souhaitez stocker les données associées au routage informé du réseau. Pour plus [d’informations, voir](#data-storage) la section stockage des données.

Sélectionnez **Suivant**.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>Étape 3 : Accepter les termes du partage des données

Lisez attentivement et reconnaissez les termes fournis associés au partage de données entre Microsoft et votre solution SD-WAN sélectionnée, puis cochez la case indiquée.

Sélectionnez **Suivant**.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>Étape 4 : Accorder des autorisations à la solution SD-WAN

Cette étape lance une demande d’octroi d’autorisations Azure Active Directory (Azure AD). Vous serez invité à accorder des autorisations au niveau du client qui permettent à votre solution SD-WAN sélectionnée d’accéder au stockage des données de routage réseau et aux informations d’état du service associées à votre client. Cette action nécessite des autorisations de rôle d’administrateur général.

Sélectionnez **l’autorisation Accorder à ce lien d’application** et suivez les demandes Azure AD.

Une fois que vous avez terminé l’octroi d’autorisations, sélectionnez **Suivant**.

### <a name="step-5-confirm-your-configuration-settings"></a>Étape 5 : Confirmez vos paramètres de configuration

La dernière étape de l’activation du routage informé du réseau pour votre client est une page de confirmation qui affiche les paramètres que vous avez fournis. 

Le routage réseau informé est désormais activé pour votre client.

Sélectionnez **Terminé,** puis fermez le volet de configuration de la solution SD-WAN.

## <a name="configuring-network-informed-routing"></a>Configuration du routage informé du réseau

Vous effectuerez une grande partie de la configuration pour le routage réseau informé au sein de votre solution SD-WAN, telle que la configuration de la façon dont votre trafic doit être acheminé dans des circonstances normales et les autres chemins à utiliser si des problèmes sont détectés. Pour plus d’informations sur ces étapes de configuration, consultez votre fournisseur de solutions SD-WAN.

Chaque emplacement de bureau doit être configuré dans le Centre d’administration Microsoft 365 afin que le routage réseau informé puisse identifier correctement le trafic associé aux circuits réseau fournissant la connectivité à ces emplacements.

Office’emplacements peuvent être détectés automatiquement dans le cadre de la collection continue de télémétrie réseau de Microsoft. Par conséquent, certains emplacements peuvent être pré-remplis dans le centre d’administration de votre client. 

Si ces emplacements sont exacts, il vous suffit d’activer la fonctionnalité de routage réseau informée pour chaque emplacement souhaité et de configurer les circuits Internet et leurs adresses IP publiques. 

Si les emplacements détectés automatiquement ne sont pas exacts ou s’il n’y a aucun emplacement pré-rempli dans votre client, vous devez ajouter ou modifier manuellement des emplacements pour refléter une topologie précise de votre organisation.

### <a name="updating-locations"></a>Mise à jour des emplacements

Les emplacements de votre client se trouvent sous **l’onglet Emplacements.** Les emplacements peuvent être modifiés directement dans la liste ou mis à jour à l’aide d’un fichier CSV.

Assurez-vous que chaque emplacement de bureau où vous souhaitez activer le routage réseau informé est présent dans cette liste.

>[!NOTE]
>Les colonnes de la liste **Emplacements** pour les exemples collectés et d’autres informations relatives à l’évaluation ne sont pas liées à la fonctionnalité de routage réseau informée.

### <a name="enabling-a-location-for-informed-network-routing"></a>Activation d’un emplacement pour le routage réseau informé

1. Dans la liste **Emplacements,** **sélectionnez Modifier** dans le menu Actions rapides pour ouvrir le volet de configuration de l’emplacement.

2. Sélectionnez **Utiliser Microsoft 365 routage réseau informé à cet emplacement.**

3. Ajoutez tous les circuits réseau fournissant une connectivité Internet à cet emplacement de bureau dans **les plages d Egress IP** de ce bureau. Assurez-vous que chaque circuit est associé aux sous-réseaux d’adresse IP publics uniques représentant votre trafic réseau.

4. Sélectionnez **Enregistrer** pour enregistrer vos modifications.

## <a name="disabling-network-informed-routing"></a>Désactivation du routage informé du réseau

La fonctionnalité de routage réseau informée peut être désactivée pour l’ensemble du client en réinitialisation de vos paramètres de solution SD-WAN. Bien que cela arrête tout le traitement des données dans Microsoft 365, vous devez également désactiver le routage informé du réseau dans le Centre d’administration.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Étape 1 : Ouvrir les options de configuration d’une solution SD-WAN

Dans le [Microsoft 365 d’administration,](https://admin.microsoft.com/) **sélectionnez** > Connectivité réseau dans le volet de navigation gauche.

Sélectionnez **Paramètres > solution SD-WAN pour** ouvrir le volet de configuration du routage réseau informé.

Le volet de configuration présente un résumé de votre solution SD-WAN actuellement configurée.

### <a name="step-2-reset-your-configuration"></a>Étape 2 : Réinitialiser votre configuration

Dans le volet de configuration, sélectionnez **Réinitialiser vos paramètres de solution SD-WAN.**

Vos paramètres ont été réinitialisés et le routage réseau informé a été désactivé. Vous pouvez le réactiver à tout moment en suivant les étapes de [l’activation du routage réseau informé.](#enabling-informed-network-routing)

## <a name="data-storage"></a>Stockage des données

Les données échangées entre Microsoft et le fournisseur de solutions SD-WAN sont stockées dans l’emplacement de stockage des données sélectionné lors de l’initialisation du routage informé du réseau. Les options d’emplacement de stockage des données représentent des zones géographiques Microsoft Azure des régions où les données sont stockées.

>[!NOTE]
>Pendant la phase d’aperçu, le seul emplacement de stockage de données disponible est Amérique **du Nord.** Des emplacements de stockage de données supplémentaires seront disponibles avant la disponibilité générale du routage réseau informé.

Les données sont conservées à cet emplacement pendant 30 jours au plus. Lorsqu’elle est désactivée, toutes les données restantes sont supprimées dans cette fenêtre de rétention de 30 jours.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le Centre d’administration Microsoft 365(prévisualisation)](office-365-network-mac-perf-overview.md)

[Microsoft 365 Services de localisation de connectivité réseau (prévisualisation)](office-365-network-mac-location-services.md)
