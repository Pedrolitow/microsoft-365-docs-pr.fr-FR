---
title: Exigences de sécurité réseau supplémentaires pour Office 365 Cloud de la communauté du secteur public Haut et DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Résumé : Les Office 365 Cloud de la communauté du secteur public Élevé et DoD ont des exigences de sécurité réseau supplémentaires'
hideEdit: true
ms.openlocfilehash: f4c03d364e84d89a1b12e4d858ab46eb3be6ae5e
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52926558"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Autres exigences de sécurité réseau pour Office 365 GCC High et DoD

*Cet article s’applique aux Office 365 Cloud de la communauté du secteur public élevé, Office 365 DOD, Microsoft 365 Cloud de la communauté du secteur public Élevé et Microsoft 365 DOD.*

Office 365 Cloud de la communauté du secteur public High et DOD sont des environnements cloud sécurisés qui répondent aux besoins du gouvernement des États-Unis et de ses fournisseurs et sous-traitants.  Ces environnements cloud ont des restrictions réseau supplémentaires sur lesquelles les points de terminaison externes sont autorisés à accéder aux services.

Cloud de la communauté du secteur public Les clients haut et DOD qui prévoient d’utiliser des identités fédérées ou la coexistence hybride peuvent exiger que Microsoft autorise l’accès entrant et/ou sortant à vos déploiements locaux existants.  Voici quelques exemples de ces activités :

* Utilisation d’identités fédérées (avec les services de fédération Active Directory ou un service STS similaire pris en charge)
* Coexistence hybride avec un déploiement local Exchange Server ou Skype Entreprise déploiement
* Migration du contenu utilisateur existant à partir d’un système local

Pour permettre au service de communiquer avec vos points  de terminaison locaux, vous devez envoyer un courrier électronique à Office 365 ingénierie pour les modifications réseau.

> [!WARNING]
> Toutes les demandes ont **un** SLA de trois semaines et ne peuvent pas être accélérées en raison des contrôles de sécurité et de conformité requis et des pipelines de déploiement.  Cela inclut les demandes réseau d’intégration initiales, ainsi que les modifications apportées après la migration vers le service.  Assurez-vous que vos équipes réseau connaissent cette chronologie et l’incluent dans leurs cycles de planification.

Envoyez un e-mail [Office 365 Secteur Public Allow-List demandes avec](mailto:o365gwlt@microsoft.com) les informations suivantes :

* **À**: [Office 365 Secteur Public Allow-List demandes](mailto:o365gwlt@microsoft.com)
* **From**: A tenant administrator - the send email **must** match a Global Administrator contact in your tenant
* **Objet de** l’e-mail : Office 365 Cloud de la communauté du secteur public réseau élevé - contoso.onmicrosoft.us (remplacer par le nom de votre client)

Le corps de votre message doit inclure les données suivantes :

* Votre Microsoft Online Services client (par exemple, contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Une liste de distribution de courrier électronique avec qui Microsoft communiquera pour les communications en cours liées aux modifications du réseau et/ou le suivi des sous-réseaux non valides
* Indiquez si vous prévoyez d’Microsoft Teams la coexistence hybride avec vos déploiements locaux
* URL accessible en externe du système d’identité fédérée (par exemple, sts.contoso.com) et plage d’adresses IP en notation CIDR (par exemple, 10.1.1.0/28)
* URL et plage d’adresses IP de liste de révocation de certificats PKI sur site en notation CIDR
* URL et plage d’adresses IP accessibles en externe pour Exchange Server déploiement local en notation CIDR
* URL et plage d’adresses IP accessibles en externe pour Skype Entreprise déploiement local en notation CIDR

Pour des raisons de sécurité et de conformité, gardez à l’esprit les restrictions suivantes sur votre demande :

* Il existe quatre limites de sous-réseau par client
* Les sous-réseaux doivent être en notation CIDR (par exemple, 10.1.1.0/28)
* Les plages de sous-réseaux ne peuvent pas être plus /24
* Nous **ne pouvons** pas prendre en charge les demandes d’accès aux services cloud commerciaux (Office 365 commercial, Google G-Suite, Amazon Web Services, etc.)

Une fois que votre demande a été reçue et approuvée par Microsoft, il existe un accord de niveau de service de trois semaines pour l’implémentation et ne peut pas être accéléré.  Vous recevrez un accusé de réception initial lorsque nous recevons votre demande et un accusé de réception final une fois qu’elle est terminée.
