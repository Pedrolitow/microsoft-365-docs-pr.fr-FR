---
title: Planification du réseau et de la migration pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Cet article contient des liens vers des informations sur la planification, les tests et la migration du réseau vers Office 365.
ms.openlocfilehash: 6288c9afae66206b7284f751f8a63381ab8451e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077463"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planification du réseau et de la migration pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Cet article contient des liens vers des informations sur la planification et les tests réseau, ainsi que sur la migration vers Office 365.
  
Avant de déployer pour la première fois ou de migrer vers Office 365, vous pouvez utiliser les informations contenues dans ces rubriques pour estimer la bande passante dont vous avez besoin, puis pour tester et vérifier que vous disposez de suffisamment de bande passante pour déployer ou migrer vers Office 365.

Cet article fait partie de la [planification du réseau et de l’optimisation des performances pour Office 365](./network-planning-and-performance.md).

Pour connaître les étapes à suivre pour optimiser votre réseau pour Microsoft 365 et d’autres plateformes et services cloud Microsoft, consultez l’affiche [Microsoft Cloud Networking for Enterprise Architects](../solutions/cloud-architecture-models.md).
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimer les besoins en bande passante réseau
<a name="EstimateBandwidthRequirements"> </a>

L’utilisation de Office 365 peut augmenter l’utilisation du circuit Internet de votre organisation. Il est important de déterminer si la quantité de bande passante actuellement disponible est suffisante pour gérer l’augmentation estimée une fois que Office 365 est entièrement déployée tout en laissant au moins 20 % de capacité pour gérer les jours les plus chargés.
  
Pour estimer la bande passante, procédez comme suit :
  
1. Évaluez le nombre de clients qui utiliseront chaque sortie Internet. Laissez notre réseau multitérabit gérer la plus grande partie possible de la connexion. 
    
2. Déterminez les services et fonctionnalités Office 365 disponibles pour les clients. Vous aurez probablement des groupes de personnes avec différents services ou profils d’utilisation.
    
3. Mesurez l’utilisation du réseau pour un groupe pilote de clients. Assurez-vous que les clients pilotes sont représentatifs des différents profils des membres de l’organisation ainsi que des différents emplacements géographiques. Vous pouvez contre-vérifier vos résultats par rapport à nos anciennes calculatrices pour [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) et [Microsoft Teams](/microsoftteams/prepare-network) ou l’étude de [cas](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) que nous avons effectuée sur notre propre réseau. 
    
4. Utilisez les mesures du groupe pilote pour extrapoler l’ensemble des besoins de l’organisation et retentez les tests pour valider les estimations avant d’apporter des modifications à votre réseau.
    
## <a name="test-your-existing-network"></a>Tester votre réseau existant
<a name="calculators"> </a>

 **Outils réseau.** Testez et validez votre bande passante Internet pour déterminer les contraintes de téléchargement, de chargement et de latence. Ces outils vous aideront à déterminer les fonctionnalités de votre réseau pour la migration, ainsi qu’une fois que vous avez été entièrement déployé. 
    
- [Analyseur de connectivité à distance Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243) : teste la connectivité dans votre environnement Exchange Online.
    
- Utilisez [l’Support Microsoft et l’Assistant Récupération pour Office 365](https://diagnostics.office.com/#/Download?env=SOC) afin de résoudre Outlook et Office 365 problèmes. 

- [Microsoft 365 outil de test de connectivité réseau](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool) : teste Microsoft 365 connectivité réseau.
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Meilleures pratiques pour la planification réseau et l’amélioration des performances de migration pour Office 365
<a name="BestPractices"> </a>

Explorez un peu plus en détail ces meilleures pratiques pour plus d’informations sur l’amélioration de votre expérience Office 365.
  
1. Vous voulez commencer à aider vos utilisateurs immédiatement ? Consultez [les meilleures pratiques d’utilisation de Office 365 sur un réseau lent](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) pour obtenir des conseils sur l’utilisation de Office 365, notamment SharePoint Online, Exchange Online et Lync Online, lorsque votre réseau ne coopère pas. Cet article fournit des liens vers des chargements de contenu sur TechNet et Support.office.com pour optimiser votre expérience de Office 365 et inclut des informations sur les moyens simples de personnaliser vos pages web et de définir vos paramètres Internet Explorer pour la meilleure expérience Office 365. 
    
2. Lisez [Office 365 Principes de connectivité réseau](./microsoft-365-network-connectivity-principles.md) pour comprendre les principes de connectivité pour gérer en toute sécurité Office 365 trafic et obtenir les meilleures performances possibles. Cet article vous aidera à mieux comprendre les instructions les plus récentes pour vous permettre d’optimiser en toute sécurité la connectivité réseau Office 365. 
    
3. Améliorez les performances de migration du courrier en gérant soigneusement la planification des mises à jour Windows. Vous pouvez mettre à jour vos ordinateurs clients par lots et vous assurer que tous les ordinateurs clients sont mis à jour avant de migrer vers Office 365 pour réglementer l’utilisation de la bande passante réseau. Pour plus d’informations, consultez [Mettre à jour manuellement et configurer des bureaux pour Office 365 pour les dernières mises à jour](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 trafic réseau fonctionne mieux lorsqu’il est traité comme un service Internet approuvé et qu’il est autorisé à contourner une grande partie du filtrage et de l’analyse traditionnels que certaines organisations placent sur le trafic réseau vers des services Internet non approuvés. Cela inclut généralement la suppression du traitement sortant, comme l’authentification des utilisateurs proxy et l’inspection des paquets, ainsi que la garantie de la sortie locale vers Internet avec la traduction d’adresses réseau (NAT) appropriée et une capacité de bande passante suffisante pour gérer les demandes réseau accrues. Reportez-vous à [la gestion des points](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) de terminaison Office 365 pour obtenir des conseils supplémentaires sur la configuration de votre réseau pour gérer Office 365 en tant que service Internet approuvé sur votre réseau.
    
1. Veillez [à gérer Office 365 points de terminaison](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Le trafic supplémentaire qui va Office 365 entraîne une augmentation des connexions proxy sortantes ainsi qu’une augmentation du trafic sécurisé sur TLS/SSL.
    
2. Si vos proxys sortants nécessitent une authentification de l’utilisateur, vous pouvez rencontrer une connectivité lente ou une perte de fonctionnalités. Le contournement de l’exigence d’authentification pour les domaines Office 365 peut réduire cette surcharge.
    
3. Si vous avez un grand nombre de calendriers partagés et de boîtes aux lettres, vous pouvez constater une augmentation du nombre de connexions de Outlook à Exchange. Par exemple, le client Outlook peut ouvrir jusqu’à deux connexions supplémentaires pour chaque calendrier partagé utilisé. Dans ce cas, assurez-vous que le proxy de sortie peut gérer les connexions, ou contournez le proxy pour les connexions à Office 365 pour Outlook.
    
4. Déterminez le nombre maximal d’appareils pris en charge pour une adresse IP publique et comment équilibrer la charge entre plusieurs adresses IP. Pour plus d'informations, voir l'article [Prise en charge NAT avec Office 365](nat-support-with-microsoft-365.md).
    
5. Si vous inspectez les connexions sortantes à partir d’ordinateurs sur votre réseau, le contournement de ce filtrage vers les domaines Office 365 améliorera la connectivité et les performances. En outre, le contournement de l’inspection sortante élimine souvent la nécessité d’une sortie Internet unique et permet la sortie Internet locale pour Office 365 demandes réseau destinées.
    
6. Certains clients trouvent que les paramètres réseau internes peuvent affecter les performances. Paramètres telles que la taille maximale de l’unité de transmission (MTU), la négociation automatique du réseau ou la détection automatique, et les itinéraires sous-optimaux vers Internet sont des lieux courants à regarder.
    
## <a name="network-planning-reference-for-office-365"></a>Informations de référence sur la planification réseau pour Office 365
<a name="NetReference"> </a>

Ces rubriques contiennent des informations de référence détaillées Office 365 réseau.
  
- [Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Réseaux de distribution de contenu](content-delivery-networks.md)
    
- [Enregistrements DNS externes pour Office 365](external-domain-name-system-records.md)
    
- [Prise en charge du protocole IPv6 dans les services Office 365](ipv6-support.md)
    
- [Principes de connectivité réseau Office 365](./microsoft-365-network-connectivity-principles.md)
    
- [Planifier les périphériques réseau qui se connectent aux services Office 365](plan-for-network-devices.md)
    
- [Guides d’installation pour les services Office 365](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)
