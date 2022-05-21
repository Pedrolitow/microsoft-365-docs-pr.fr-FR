---
title: Microsoft 365 routage réseau informé
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 routage réseau informé
ms.openlocfilehash: fc946b3a1de057605b89bcadeb4e5b7269aebcb0
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622492"
---
# <a name="microsoft-365-informed-network-routing"></a>Microsoft 365 routage réseau informé

Le routage réseau informé est une fonctionnalité qui intègre différentes applications Microsoft 365 à des solutions SD-WAN (Software Defined Network) tierces afin d’optimiser et d’améliorer votre connectivité réseau aux points de terminaison de service Microsoft. Une connectivité SD-WAN optimisée peut améliorer les expériences utilisateur et les performances.

## <a name="overview"></a>Vue d’ensemble

Le routage réseau informé fournit un canal de partage de données bidirectionnel entre Microsoft et votre solution SD-WAN. Pour chaque emplacement de bureau et circuit Internet que vous configurez, Microsoft partage régulièrement des commentaires avec la solution SD-WAN sur la qualité des expériences d’application Microsoft 365 sélectionnées pour le trafic réseau associé à chaque circuit Internet spécifique. À l’aide de ces commentaires, la solution SD-WAN peut ensuite effectuer des actions de récupération intelligente en routant Microsoft 365 trafic d’application via d’autres liens disponibles. 

Les dégradations de la qualité de service dans le chemin d’accès d’un circuit Internet particulier, telles qu’une latence accrue ou une perte élevée de paquets, sont difficiles à détecter en continu. Ces dégradations peuvent nuire aux expériences utilisateur pour des applications telles que Exchange Online, SharePoint, OneDrive et Microsoft Teams. Les symptômes courants incluent une recherche lente de contenu Exchange, des temps de transfert élevés lors de l’interaction avec des bibliothèques de documents SharePoint ou OneDrive, ou une qualité d’appel ou de réunion médiocre dans Microsoft Teams.

Le mécanisme de rétroaction et de récupération dans le routage réseau informé cherche à détecter dynamiquement ces problèmes en quasi-temps réel et informe la solution SD-WAN déployée d’effectuer des actions de récupération automatique.

Le canal de partage de données est également utilisé pour recevoir régulièrement des données optiques au niveau du réseau de la solution SD-WAN, y compris les informations de configuration et les statistiques d’utilisation associées à l’appareil et aux circuits attachés. Aucune information personnelle n’est collectée ou stockée. Toutes les informations collectées sont agrégées dans les bureaux et les circuits Internet connectés. Ces informations peuvent aider Microsoft à résoudre plus efficacement les problèmes signalés liés à l’utilisation de Microsoft 365 services et applications.

>[!NOTE]
>Microsoft 365 le routage réseau informé prend en charge les locataires dans le cloud commercial WW, mais pas les clouds Cloud de la communauté du secteur public Modéré, Cloud de la communauté du secteur public Élevé, DoD, Allemagne ou Chine.

## <a name="requirements"></a>Configuration requise

### <a name="integrated-sd-wan-solutions"></a>Solutions SD-WAN intégrées

Microsoft travaille avec différents partenaires pour permettre l’intégration à Microsoft 365 routage réseau informé. Les solutions actuellement activées sont les suivantes :

| Fabricant d’appareils | Nom de solution | Version minimale |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Topologie de réseau

Le routage réseau informé identifie actuellement le trafic associé à un emplacement de bureau et un circuit Internet spécifiques en fonction de l’adresse IP publique utilisée pour envoyer le trafic réseau à Microsoft. 

Dans le cas où il n’existe pas au moins un circuit réseau fournissant un accès Internet direct à un emplacement de succursale, le routage réseau informé peut ne pas fournir de valeur significative.

### <a name="application-usage"></a>Utilisation de l’application

Les données d’expérience d’application (reflétées par les métriques de qualité réseau) sont collectées par le biais de l’utilisation d’applications clientes Microsoft spécifiques. Exchange métriques reflètent l’utilisation du client Outlook et certaines Outlook l’utilisation de l’application web. SharePoint et les métriques OneDrive reflètent l’utilisation des points de terminaison SharePoint spécifiques au locataire, quelle que soit l’application cliente. Teams métriques reflètent l’utilisation du client de bureau Teams. Le trafic d’autres applications n’est pas pris en compte lors de l’évaluation de l’intégrité d’un circuit réseau.

## <a name="enabling-informed-network-routing"></a>Activation du routage réseau informé

L’activation du routage réseau éclairé nécessite plusieurs étapes, dont certaines doivent être effectuées dans l’interface de configuration de votre solution SD-WAN. Consultez le fournisseur de votre solution SD-WAN pour obtenir des conseils sur la façon de lancer le processus d’activation du routage réseau informé au sein de la solution SD-WAN avant de poursuivre la configuration dans le Centre d'administration Microsoft 365.

Une fois que vous êtes prêt à activer le routage réseau informé dans le Centre d'administration Microsoft 365, vérifiez que vous disposez des autorisations **d’administrateur utilisateur** ou **d’administrateur général** nécessaires.

>[!IMPORTANT]
>Pour fournir le consentement des autorisations d’applications au niveau du locataire nécessaires pour que la solution SD-WAN sélectionnée accède au canal de partage de données de routage réseau informé, vous devez effectuer les étapes suivantes en tant qu’administrateur général.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Étape 1 : Ouvrir les options de configuration de la solution SD-WAN

Dans le [Centre d'administration Microsoft 365](https://admin.microsoft.com/), sélectionnez **Connectivité réseau > Intégrité** dans le volet de navigation de gauche.

Cette section du Centre d’administration fournit des métriques de connectivité réseau agrégées pour votre organisation et des conseils sur la façon d’améliorer votre connectivité. Pour plus d’informations sur ces fonctionnalités disponibles dans le Centre d’administration, consultez la [connectivité réseau dans le centre de Administration Microsoft 365](office-365-network-mac-perf-overview.md).

Sélectionnez **Paramètres > solution SD-WAN** pour ouvrir le volet de configuration du routage réseau informé. Les autres options qui apparaissent sous **Paramètres** s’appliquent aux instructions générales de connectivité réseau dans le Centre d’administration et ne sont pas requises pour activer le routage réseau informé.

Dans le volet de configuration, sélectionnez **Ajouter votre solution SD-WAN**.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>Étape 2 : Sélectionner votre solution SD-WAN et l’emplacement de stockage des données

Dans les zones déroulantes, sélectionnez la solution SD-WAN que vous avez déployée et l’emplacement où vous souhaitez stocker les données associées au routage réseau informé. Pour plus [d’informations](#data-storage) , consultez la section Stockage de données.

Sélectionnez **Suivant**.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>Étape 3 : Accepter les conditions pour le partage des données

Lisez attentivement et reconnaissez les termes fournis associés au partage de données entre Microsoft et votre solution SD-WAN sélectionnée, puis activez la case à cocher indiquée.

Sélectionnez **Suivant**.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>Étape 4 : Accorder des autorisations à la solution SD-WAN

Cette étape lance une demande d’octroi d’autorisations avec Azure Active Directory (Azure AD). Vous serez invité à accorder des autorisations au niveau du locataire qui permettent à votre solution SD-WAN sélectionnée d’accéder au stockage de données de routage réseau informé et aux informations d’intégrité du service associées à votre locataire. Cette action nécessite des autorisations **d’administrateur de contrôleur de domaine Azure AD** ou **d’administrateur général** .

Sélectionnez le lien **Accorder l’autorisation à ce lien d’application** et suivez les demandes Azure AD.

Une fois que vous avez terminé l’octroi des autorisations, sélectionnez **Suivant**.

### <a name="step-5-confirm-your-configuration-settings"></a>Étape 5 : Confirmer vos paramètres de configuration

La dernière étape de l’activation du routage réseau informé pour votre locataire est une page de confirmation qui affiche les paramètres que vous avez fournis. 

Le routage réseau informé est désormais activé pour votre locataire.

Sélectionnez **Terminé** , puis fermez le volet de configuration de la solution SD-WAN.

## <a name="configuring-informed-network-routing"></a>Configuration du routage réseau informé

Vous allez effectuer une grande partie de la configuration du routage réseau informé au sein de votre solution SD-WAN, comme la configuration de la façon dont votre trafic doit être routée dans des circonstances normales et les chemins d’accès alternatifs qui doivent être utilisés si des problèmes sont détectés. Consultez votre fournisseur de solutions SD-WAN pour plus d’informations sur ces étapes de configuration.

Chaque emplacement de bureau doit être configuré dans le Centre d'administration Microsoft 365 afin que le routage réseau informé puisse identifier correctement le trafic associé aux circuits réseau fournissant une connectivité à ces emplacements.

Office emplacements peuvent être détectés automatiquement dans le cadre de la collecte continue de données de télémétrie réseau de Microsoft. Par conséquent, certains emplacements peuvent être préremplis dans le centre d’administration de votre locataire. 

Si ces emplacements sont précis, vous devez simplement activer la fonctionnalité de routage réseau informé pour chaque emplacement souhaité et configurer les circuits Internet et leurs adresses IP publiques. 

Si les emplacements détectés automatiquement ne sont pas exacts ou s’il n’existe aucun emplacement prérempli dans votre locataire, vous devez ajouter ou modifier manuellement des emplacements pour refléter une topologie précise de votre organisation.

### <a name="updating-locations"></a>Mise à jour des emplacements

Les emplacements de votre locataire se trouvent sous l’onglet **Emplacements** . Les emplacements peuvent être modifiés directement dans la liste ou mis à jour à l’aide d’un fichier CSV.

Vérifiez que chaque emplacement de bureau où vous souhaitez activer le routage réseau informé est présent dans cette liste.

>[!NOTE]
>Les colonnes de la liste **Emplacements** des exemples collectés et d’autres informations relatives à l’évaluation ne sont pas liées à la fonctionnalité de routage réseau informée.

### <a name="enabling-a-location-for-informed-network-routing"></a>Activation d’un emplacement pour le routage réseau informé

1. Dans la liste **Emplacements** , sélectionnez **Modifier** dans le menu Actions rapides pour ouvrir le volet de configuration de l’emplacement.

2. Sélectionnez **Utiliser Microsoft 365 routage réseau informé à cet emplacement**.

3. Ajoutez tous les circuits réseau fournissant une connectivité Internet à cet emplacement de bureau dans les **plages d’adresses IP Egress dans cette section d’emplacement de bureau**. Assurez-vous que chaque circuit est associé aux sous-réseaux d’adresses IP publiques uniques représentant votre trafic réseau.

4. Sélectionnez **Enregistrer** pour enregistrer vos modifications.

## <a name="disabling-informed-network-routing"></a>Désactivation du routage réseau informé

La fonctionnalité de routage réseau informé peut être désactivée pour l’ensemble du locataire en réinitialisant vos paramètres de solution SD-WAN. Bien que cela arrête tout traitement des données dans Microsoft 365, vous devez également désactiver le routage réseau informé au sein du centre d’administration.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Étape 1 : Ouvrir les options de configuration de la solution SD-WAN

Dans le [Centre d'administration Microsoft 365](https://admin.microsoft.com/) sélectionnez **Connectivité réseau > Intégrité** dans le volet de navigation de gauche.

Sélectionnez **Paramètres > solution SD-WAN** pour ouvrir le volet de configuration du routage réseau informé.

Le volet de configuration affiche un résumé de votre solution SD-WAN actuellement configurée.

### <a name="step-2-reset-your-configuration"></a>Étape 2 : Réinitialiser votre configuration

Dans le volet de configuration, sélectionnez **Réinitialiser les paramètres de votre solution SD-WAN**.

Vos paramètres ont été réinitialisés et le routage réseau informé a été désactivé. Vous pouvez le réactiver à tout moment en suivant les étapes [de l’activation du routage réseau informé](#enabling-informed-network-routing).

## <a name="data-storage"></a>Stockage des données

Les données échangées entre Microsoft et le fournisseur de solutions SD-WAN sont stockées dans l’emplacement de stockage de données sélectionné lors de l’activation initiale du routage réseau informé. Les options d’emplacement de stockage des données représentent des zones géographiques contenant Microsoft Azure régions où les données sont stockées.

Les données sont conservées à cet emplacement pendant 30 jours maximum. Quand elle est désactivée, toutes les données restantes sont supprimées dans cette fenêtre de rétention de 30 jours.

Les données de cet emplacement sont échangées avec la solution SD-WAN sélectionnée, et l’emplacement de la solution SD-WAN configurée peut ne pas se trouver dans la même région. Les clients doivent travailler avec leur fournisseur de solutions SD-WAN pour évaluer les exigences d’emplacement de stockage de données avant le déploiement en production.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le Centre d'administration Microsoft 365](office-365-network-mac-perf-overview.md)

[Microsoft 365 services d’emplacement de connectivité réseau](office-365-network-mac-location-services.md)
