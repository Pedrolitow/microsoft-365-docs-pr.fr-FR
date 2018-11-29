---
title: 'Étape 2 : Configurer les connexions Internet locales pour chaque bureau'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez votre résolution DNS pour de meilleures performances.
ms.openlocfilehash: 9ccd5c477b4aeda8e7dcf482cc09c8a357f19f40
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866856"
---
# <a name="step-2-configure-local-internet-connections-for-each-office"></a>Étape 2 : Configurer les connexions Internet locales pour chaque bureau

*Cette étape est requise et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/networking_icon-small.png)

À l’Étape 2, vous vérifiez que chacun de vos bureaux est équipé de connexions Internet locales et utilise des serveurs DNS locaux. Ces deux éléments sont requis pour réduire la latence de connexion et garantir que les ordinateurs clients locaux établissent des connexions avec le point d’entrée le plus proche aux services services cloud Microsoft 365.

Dans les réseaux traditionnels des grandes entreprises, le trafic Internet traverse la structure fondamentale du réseau jusqu’à atteindre une connexion Internet centrale. Cela ne fonctionne pas correctement pour optimiser les performances sur une infrastructure SaaS distribuée globalement, qui inclut les produits Office 365 et Enterprise Mobility + Security (EMS) dans Microsoft 365.

Le réseau global Microsoft inclut des serveurs frontaux sur l’ensemble des services cloud de Microsoft 365 dans le monde entier. Pour de meilleures performances, les clients locaux doivent accéder au serveur frontal le plus proche géographiquement, plutôt que d’envoyer le trafic sur une structure fondamentale du réseau et sur le serveur frontal qui est le plus proche de la connexion Internet centrale de l’organisation.

Pour diriger la demande d’un client vers le serveur frontal le plus proche géographiquement, les serveurs DNS de Microsoft utilisent des requêtes DNS correspondant à la demande de connexion initiale du client. Par conséquent, pour la latence de réseau la plus faible :

- Tous les bureaux de votre organisation doivent avoir des connexions Internet locales pour le trafic réseau de catégorie [Optimiser](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories).
- Chaque connexion Internet locale doit utiliser un serveur DNS régional local pour le trafic Internet sortant de cet emplacement.

Pour plus d’informations, reportez-vous à [Sortir les connexions réseau localement](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#egress-network-connections-locally). 

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](networking-exit-criteria.md#crit-networking-step2) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step3.png)|[Éviter les épingles de réseau](networking-avoid-network-hairpins.md)|
