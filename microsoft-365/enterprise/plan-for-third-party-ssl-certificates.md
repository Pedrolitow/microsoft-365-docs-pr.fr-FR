---
title: Planifier les certificats SSL tiers pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Résumé : Décrit les certificats SSL nécessaires pour Exchange localement et hybride, l’authentification unique utilisant AD FS, les services Exchange Online et les services web Exchange.'
ms.openlocfilehash: 0cd7cce2cd5f0aba8baecab7048d86d629d30427
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100300"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>Planifier les certificats SSL tiers pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour chiffrer les communications entre vos clients et l’environnement Microsoft 365, des certificats SSL (Secure Socket Layer) tiers doivent être installés sur vos serveurs d’infrastructure.

Cet article fait partie de la [planification du réseau et de l’optimisation des performances pour Microsoft 365](./network-planning-and-performance.md).
   
Des certificats sont requis pour les composants Microsoft 365 suivants :
  
- Exchange local
    
- Authentification unique (SSO) (pour les serveurs de fédération Services ADFS (AD FS) et les serveurs proxy de fédération AD FS)
    
- Exchange Online services, tels que la découverte automatique, Outlook n’importe où et les services web Exchange
    
- serveur hybride Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certificats pour Exchange local

Pour obtenir une vue d’ensemble de l’utilisation des certificats numériques pour sécuriser la communication entre l’organisation Exchange locale et Exchange Online, consultez l’article TechNet Sur la [compréhension des exigences en matière de certificats](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141)).
  
## <a name="certificates-for-single-sign-on"></a>Certificats pour l'authentification unique

Pour fournir à vos utilisateurs une expérience d’authentification unique simplifiée qui inclut une sécurité robuste, les certificats indiqués dans le tableau suivant sont requis sur les serveurs de fédération ou les proxys de serveur de fédération. Le tableau ci-dessous se concentre sur Services ADFS (AD FS), nous avons également plus d’informations sur [l’utilisation de fournisseurs d’identité tiers](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
| Type de certificat | Description | Ce que vous devez savoir avant de déployer |
|:-----|:-----|:-----|
|**Certificat SSL (également appelé certificat d’authentification serveur)** <br/> |Il s’agit d’un certificat SSL standard qui est utilisé pour sécuriser les communications entre les serveurs de fédération, les clients et les ordinateurs proxy de serveur de fédération.  <br/> |AD FS nécessite un certificat SSL. Par défaut, AD FS utilise le certificat SSL configuré pour le site web par défaut dans Internet Information Services (IIS).  <br/> Le nom d’objet de ce certificat SSL est utilisé pour déterminer le nom du service de fédération (FS) pour chaque instance d’AD FS que vous déployez. Envisagez de choisir un nom d’objet pour les nouveaux certificats émis par l’autorité de certification qui représente le mieux le nom de votre entreprise ou organisation à Microsoft 365. Ce nom doit être routable sur Internet.  <br/>**Attention:** AD FS requiert que ce certificat SSL n’ait pas de nom d’objet sans point (nom court).          <br/> **Recommandation:** Étant donné que ce certificat doit être approuvé par les clients d’AD FS, nous vous recommandons d’utiliser un certificat SSL émis par une autorité de certification publique (tierce) ou par une autorité de certification subordonnée à une racine approuvée publiquement; par exemple, VeriSign ou Thawte.  <br/> |
|**Certificat de signature de jeton** <br/> |Il s’agit d’un certificat X.509 standard utilisé pour signer en toute sécurité tous les jetons que le serveur de fédération émet et que Microsoft 365 accepte et valide.  <br/> |Le certificat de signature de jeton doit contenir une clé privée qui est chaîne à une racine approuvée dans le service FS. Par défaut, AD FS crée un certificat auto-signé. Toutefois, en fonction des besoins de votre organisation, vous pouvez remplacer ce certificat par un certificat émis par l’autorité de certification à l’aide du composant logiciel enfichable de gestion AD FS.  <br/>**Attention:** Le certificat de signature de jeton est essentiel à la stabilité du FS. Si le certificat est modifié, Microsoft 365 devez être averti de la modification. Si aucune notification n’est fournie, les utilisateurs ne peuvent pas se connecter à leurs offres de service Microsoft 365.<br/>**Recommandation:** Nous vous recommandons d’utiliser le certificat de signature de jeton auto-signé généré par AD FS. Ce faisant, il gère ce certificat pour vous par défaut. Par exemple, lorsque ce certificat est sur le point d’expirer, AD FS génère un nouveau certificat auto-signé.  <br/> |
   
Les proxys de serveur de fédération nécessitent le certificat décrit dans le tableau suivant.
  
| Type de certificat | Description | Ce que vous devez savoir avant de déployer |
|:-----|:-----|:-----|
|certificat SSL  <br/> |Il s’agit d’un certificat SSL standard utilisé pour sécuriser les communications entre un serveur de fédération, un proxy de serveur de fédération et des ordinateurs clients Internet.  <br/> |Ce certificat SSL doit être lié au site web par défaut dans IIS avant de pouvoir exécuter correctement l’Assistant Configuration du proxy du serveur de fédération AD FS.  <br/> Ce certificat doit avoir le même nom d’objet que le certificat SSL qui a été configuré sur le serveur de fédération dans le réseau d’entreprise.  <br/> **Recommandation:** Nous vous recommandons d’utiliser le même certificat d’authentification de serveur configuré sur le serveur de fédération auquel ce proxy de serveur de fédération se connecte.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificats pour la découverte automatique, Outlook n’importe où et la synchronisation Active Directory

Vos serveurs Exchange 2013, Exchange 2010, Exchange 2007 et Exchange 2003 nécessitent un certificat SSL tiers pour des connexions sécurisées pour la découverte automatique, Outlook n’importe où et les services de synchronisation Active Directory. Ce certificat est peut-être déjà installé dans votre environnement local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificat pour un serveur hybride Exchange

Vos serveurs Exchange hybrides externes nécessitent un certificat SSL tiers pour une connectivité sécurisée avec le service Exchange Online. Vous devez obtenir ce certificat auprès de votre fournisseur SSL tiers.
  
## <a name="microsoft-365-certificate-chains"></a>chaînes de certificats Microsoft 365

Cet article décrit les certificats que vous devrez peut-être installer sur votre infrastructure. Pour plus d’informations sur les certificats installés sur nos serveurs Microsoft 365, consultez [Microsoft 365 Chaînes de certificats](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)