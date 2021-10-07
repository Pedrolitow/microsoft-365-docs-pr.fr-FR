---
title: Planification du réseau et de la migration pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Cet article contient des liens vers des informations sur la planification, les tests et la migration réseau vers Office 365.
ms.openlocfilehash: 21bd36395f6ceb6a13b3180a26f8dbf7f197f134
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60177086"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planification du réseau et de la migration pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Cet article contient des liens vers des informations sur la planification et les tests réseau, ainsi que sur la migration vers Office 365.
  
Avant de déployer pour la première fois ou de migrer vers Office 365, vous pouvez utiliser les informations de ces rubriques pour estimer la bande passante dont vous avez besoin, puis pour tester et vérifier que vous avez suffisamment de bande passante pour déployer ou migrer vers Office 365.

Cet article fait partie de la planification [réseau et de l’optimisation](./network-planning-and-performance.md)des performances pour Office 365 .

Pour obtenir la procédure d’optimisation de votre réseau pour Microsoft 365 et d’autres plateformes et services cloud Microsoft, consultez l’affiche Mise en réseau cloud microsoft pour les architectes [Enterprise.](../solutions/cloud-architecture-models.md)
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimer les besoins en bande passante réseau
<a name="EstimateBandwidthRequirements"> </a>

L Office 365 peut augmenter l’utilisation du circuit Internet de votre organisation. Il est important de déterminer si la quantité de bande passante actuellement disponible est suffisante pour gérer l’augmentation estimée une fois Office 365 entièrement déployé, tout en laissant au moins 20 % de capacité pour gérer les jours les plus occupés.
  
Pour estimer la bande passante, utilisez les étapes suivantes :
  
1. Évaluez le nombre de clients qui utiliseront chaque sortie Internet. Laissez notre réseau multiterabit gérer autant de connexions que possible. 
    
2. Déterminez les Office 365 et fonctionnalités disponibles pour les clients. Vous aurez probablement des groupes de personnes avec différents services ou profils d’utilisation.
    
3. Mesurer l’utilisation du réseau pour un groupe pilote de clients. Assurez-vous que les clients pilotes sont représentatifs des différents profils des membres de l’organisation ainsi que des différents emplacements géographiques. Vous pouvez vérifier vos résultats par rapport [](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) à nos anciennes calculatrices pour [](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) Exchange et [Microsoft Teams](/microsoftteams/prepare-network) ou l’étude de cas que nous avons effectuée sur notre propre réseau. 
    
4. Utilisez les mesures du groupe pilote pour extrapoler les besoins de l’ensemble de l’organisation et re-tester pour valider les estimations avant d’apporter des modifications à votre réseau.
    
## <a name="test-your-existing-network"></a>Tester votre réseau existant
<a name="calculators"> </a>

 **Outils réseau.** Testez et validez votre bande passante Internet pour déterminer les contraintes de téléchargement, de chargement et de latence. Ces outils vous aideront à déterminer les fonctionnalités de votre réseau pour la migration, ainsi qu’une fois que vous avez été entièrement déployé. 
    
- [Analyseur de connectivité à distance Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): teste la connectivité dans votre environnement Exchange Online de connexion.
    
- Utilisez le [microsoft Assistant Support et récupération pour Office 365](https://diagnostics.office.com/#/Download?env=SOC) résoudre les problèmes Outlook et Office 365 problèmes. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Meilleures pratiques en matière de planification réseau et d’amélioration des performances de migration pour Office 365
<a name="BestPractices"> </a>

Approfondissez ces meilleures pratiques pour plus d’informations sur l’amélioration Office 365 expérience utilisateur.
  
1. Vous souhaitez commencer à aider vos utilisateurs immédiatement ? Consultez les meilleures pratiques pour l’utilisation de [Office 365](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) sur un réseau lent pour obtenir des conseils sur l’utilisation de Office 365, notamment SharePoint Online, Exchange Online et Lync Online, lorsque votre réseau n’est pas en train de s’en délationr. Cet article propose des liens vers des chargements de contenu sur TechNet et Support.office.com pour optimiser votre expérience Office 365 et inclut des informations sur les méthodes simples de personnalisation de vos pages web et la définition de vos paramètres Internet Explorer pour une expérience Office 365 optimisée. 
    
2. Lisez [Office 365 principes](./microsoft-365-network-connectivity-principles.md) de connectivité réseau pour comprendre les principes de connectivité pour gérer en toute sécurité Office 365 trafic et obtenir les meilleures performances possibles. Cet article vous aidera à mieux comprendre les instructions les plus récentes pour vous permettre d’optimiser en toute sécurité la connectivité réseau Office 365. 
    
3. Améliorez les performances de migration de messagerie en gérant soigneusement la planification des mises à jour Windows de messagerie. Vous pouvez mettre à jour vos ordinateurs clients par lots et vous assurer que tous les ordinateurs clients sont mis à jour avant de migrer vers Office 365 afin de contrôler l’utilisation de la bande passante réseau. Pour plus d’informations, voir Mise à jour manuelle et configuration des ordinateurs de bureau [pour Office 365 pour les dernières mises à jour.](https://support.microsoft.com/gp/office-2013-365-update)
    
4. Office 365 trafic réseau est plus performant lorsqu’il est traité comme un service Internet approuvé et autorisé à contourner une grande partie du filtrage et de l’analyse traditionnels que certaines organisations placent sur le trafic réseau vers des services Internet non fiables. Cela inclut généralement la suppression du traitement sortant tel que l’authentification des utilisateurs proxy et l’inspection des paquets, ainsi que la garantie d’une sortie locale vers Internet avec la traduction d’adresses réseau (NAT) appropriée et une capacité de bande passante suffisante pour gérer les demandes réseau accrues. [Reportez-vous](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)à La gestion Office 365 points de terminaison pour obtenir des instructions supplémentaires sur la configuration de votre réseau pour gérer les Office 365 en tant que service Internet approuvé sur votre réseau.
    
1. Assurez [la gestion Office 365 de terminaison.](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) Le trafic supplémentaire à Office 365 entraîne une augmentation des connexions proxy sortantes, ainsi qu’une augmentation du trafic sécurisé sur TLS/SSL.
    
2. Si vos proxies sortants nécessitent l’authentification de l’utilisateur, vous risquez de voir une connectivité lente ou une perte de fonctionnalités. Le contournement de l’exigence d’authentification pour Office 365 domaines peut réduire cette surcharge.
    
3. Si vous avez un grand nombre de boîtes aux lettres et de calendriers partagés, vous pouvez constater une augmentation du nombre de connexions entre Outlook et Exchange. Par exemple, le client Outlook peut ouvrir jusqu’à deux connexions supplémentaires pour chaque calendrier partagé utilisé. Dans ce cas, assurez-vous que le proxy de sortie peut gérer les connexions ou contourner le proxy pour les connexions à Office 365 pour Outlook.
    
4. Déterminez le nombre maximal d’appareils pris en charge pour une adresse IP publique et comment équilibrer la charge entre plusieurs adresses IP. Pour plus d'informations, voir l'article [Prise en charge NAT avec Office 365](nat-support-with-microsoft-365.md).
    
5. Si vous examinez les connexions sortantes à partir d’ordinateurs de votre réseau, le contournement de ce filtrage vers les domaines Office 365 améliorera la connectivité et les performances. En outre, le contournement de l’inspection sortante supprime souvent la nécessité d’une sortie Internet unique et active la sortie Internet locale pour les demandes Office 365 réseau destinées.
    
6. Certains clients trouvent que les paramètres réseau internes peuvent affecter les performances. Paramètres par exemple, la taille maximale de l’unité de transmission (MTU), la négociation automatique ou la détection automatique du réseau, et les itinéraires sous-optimaux vers Internet sont des lieux courants à rechercher.
    
## <a name="network-planning-reference-for-office-365"></a>Référence de planification réseau pour Office 365
<a name="NetReference"> </a>

Ces rubriques contiennent des informations détaillées Office 365 de référence du réseau.
  
- [Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Réseaux de distribution de contenu](content-delivery-networks.md)
    
- [Enregistrements DNS externes pour Office 365](external-domain-name-system-records.md)
    
- [Prise en charge du protocole IPv6 dans les services Office 365](ipv6-support.md)
    
- [Principes de connectivité réseau Office 365](./microsoft-365-network-connectivity-principles.md)
    
- [Planifier les périphériques réseau qui se connectent aux services Office 365](plan-for-network-devices.md)
    
- [Guides d’installation pour Office 365 services](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)