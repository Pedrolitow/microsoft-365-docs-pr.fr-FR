---
title: Exigences de sécurité réseau supplémentaires pour Office 365 GCC High et DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
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
description: 'Résumé : Office 365 GCC High et DoD ont des exigences de sécurité réseau supplémentaires'
hideEdit: true
ms.openlocfilehash: 90dae84ac9fb5144aaf6e3049dedfa8c27dd227b
ms.sourcegitcommit: 62368e5a48e569c8e475b07d194d7d8ff7d167ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67556279"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Autres exigences de sécurité réseau pour Office 365 GCC High et DoD

*Cet article s’applique à Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High et Microsoft 365 DOD.*

Office 365 GCC High et DOD sont des environnements cloud sécurisés pour répondre aux besoins du gouvernement États-Unis et de ses fournisseurs et sous-traitants.  Ces environnements cloud ont des restrictions réseau supplémentaires auxquelles les points de terminaison externes auxquels les services sont autorisés à accéder.

Les clients GCC High et DOD qui envisagent d’utiliser des identités fédérées ou une coexistence hybride peuvent exiger que Microsoft autorise l’accès entrant et/ou sortant à vos déploiements locaux existants.  Voici quelques exemples de ces activités :

* Utilisation d’identités fédérées (avec Services ADFS ou un STS pris en charge similaire)
* Coexistence hybride avec un déploiement Exchange Server local ou Skype Entreprise
* Migration de contenu utilisateur existant à partir d’un système local

Pour permettre au service de communiquer avec vos points de terminaison locaux, vous **devez** envoyer un e-mail à Office 365 ingénierie pour les modifications réseau.

> [!WARNING]
> Toutes les demandes ont un contrat SLA **de trois semaines** et ne peuvent pas être accélérées en raison des contrôles de sécurité et de conformité requis et des pipelines de déploiement.  Cela inclut les demandes réseau d’intégration initiales, ainsi que toutes les modifications après avoir migré vers le service.  Assurez-vous que vos équipes réseau connaissent cette chronologie et l’incluent dans leurs cycles de planification.

Envoyez un e-mail à [Office 365 Secteur Public Allow-List Demandes](mailto:o365gwlt@microsoft.com) avec les informations suivantes :

* **À** : [Office 365 Secteur Public Allow-List demandes](mailto:o365gwlt@microsoft.com)
* **À partir de** : administrateur de locataire : l’e-mail d’envoi **doit** correspondre à un contact d’administrateur général dans votre locataire
* **Email sujet** : Office 365 demande réseau GCC High - contoso.onmicrosoft.us (remplacez par le nom de votre locataire)

Le corps de votre message doit inclure les données suivantes :

* Nom de votre locataire Microsoft Online Services (par exemple, contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Liste de distribution des e-mails avec laquelle Microsoft communiquera pour les communications en cours liées aux modifications réseau et/ou le suivi des sous-réseaux non valides
* Indiquez si vous envisagez d’utiliser la coexistence hybride de Microsoft Teams avec vos déploiements locaux
* URL accessible en externe du système d’identité fédérée (par exemple, sts.contoso.com) et plage d’adresses IP dans la notation CIDR (par exemple, . 10.1.1.0/28)
* URL de liste de révocation de certificats PKI locale et plage d’adresses IP dans la notation CIDR
* URL et plage d’adresses IP accessibles en externe pour Exchange Server déploiement local dans la notation CIDR
* URL et plage d’adresses IP accessibles en externe pour Skype Entreprise déploiement local dans la notation CIDR

Pour des raisons de sécurité et de conformité, gardez à l’esprit les restrictions suivantes sur votre demande :

* Il existe une limitation de quatre sous-réseaux par locataire
* Les sous-réseaux doivent être en notation CIDR (par exemple, 10.1.1.0/28)
* Les plages de sous-réseaux ne peuvent pas être supérieures à /24
* Nous **ne pouvons pas** prendre en charge les demandes d’autorisation d’accès aux services cloud commerciaux (Office 365 commerciales, Google G-Suite, Amazon Web Services, etc.)

Une fois que votre demande a été reçue et approuvée par Microsoft, il existe un contrat SLA de trois semaines pour l’implémentation et ne peut pas être accéléré.  Vous recevrez un accusé de réception initial lorsque nous aurons reçu votre demande et un accusé de réception final une fois celle-ci terminée.
