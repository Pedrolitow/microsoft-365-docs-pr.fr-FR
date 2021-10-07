---
title: Planifier les certificats SSL tiers pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Résumé : Décrit les certificats SSL nécessaires pour Exchange sur site et hybride, l’ation sso à l’aide d’AD FS, des services Exchange Online et des services web Exchange.'
ms.openlocfilehash: 8c0bf69090abb87e71f2d51b73405ccf4e54d4bb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60202834"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>Planifier les certificats SSL tiers pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour chiffrer les communications entre vos clients et l’environnement Microsoft 365, des certificats SSL (Secure Socket Layer) tiers doivent être installés sur vos serveurs d’infrastructure.

Cet article fait partie de la planification [réseau et de l’optimisation](./network-planning-and-performance.md)des performances pour Microsoft 365 .
   
Les certificats sont requis pour les composants Microsoft 365 suivants :
  
- Exchange local
    
- Sign-on (SSO) (pour les serveurs de fédération AD FS (Active Directory Federation Services) et les serveurs proxy de fédération AD FS)
    
- Exchange Online, tels que la découverte automatique, Outlook Anywhere et Exchange Web Services
    
- Exchange serveur hybride
    
## <a name="certificates-for-exchange-on-premises"></a>Certificats pour Exchange local

Pour obtenir une vue d’ensemble de l’utilisation des certificats numériques pour sécuriser la communication entre l’organisation Exchange sur site et Exchange Online, consultez l’article TechNet Understanding [Certificate Requirements](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141)).
  
## <a name="certificates-for-single-sign-on"></a>Certificats pour l'authentification unique

Pour offrir à vos utilisateurs une expérience d' sign-on unique simplifiée qui inclut une sécurité robuste, les certificats indiqués dans le tableau suivant sont requis sur les serveurs de fédération ou les serveurs proxy de fédération. Le tableau [ci-dessous](/azure/active-directory/hybrid/how-to-connect-fed-compatibility)se concentre sur les services AD FS (Active Directory Federation Services), nous avons également plus d’informations sur l’utilisation de fournisseurs d’identité tiers.
  
| Type de certificat | Description | Ce que vous devez savoir avant de déployer |
|:-----|:-----|:-----|
|**Certificat SSL (également appelé certificat d’authentification de serveur)** <br/> |Il s’agit d’un certificat SSL standard utilisé pour sécuriser les communications entre les serveurs de fédération, les clients et les ordinateurs proxy de serveur de fédération.  <br/> |AD FS requiert un certificat SSL. Par défaut, AD FS utilise le certificat SSL configuré pour le site web par défaut dans Internet Information Services (IIS).  <br/> Le nom d’objet de ce certificat SSL est utilisé pour déterminer le nom du service FS (Federation Service) pour chaque instance d’AD FS que vous déployez. Envisagez de choisir un nom d’objet pour les nouveaux certificats émis par l’autorité de certification qui représentent le mieux le nom de votre entreprise ou organisation à Microsoft 365. Ce nom doit être routable sur Internet.  <br/>**Attention :** AD FS exige que ce certificat SSL n’a pas de nom d’objet pointless (nom court).          <br/> **Recommandation :** Étant donné que ce certificat doit être approuvé par les clients d’AD FS, nous vous recommandons d’utiliser un certificat SSL émis par une ca publique (tierce) ou par une ca qui est subordonnée à une racine publiquement fiable ; par exemple, VeriSign ou Thawte.  <br/> |
|**Certificat de signature de jetons** <br/> |Il s’agit d’un certificat X.509 standard utilisé pour signer en toute sécurité tous les jetons émis par le serveur de fédération et que Microsoft 365 accepte et valide.  <br/> |Le certificat de signature de jetons doit contenir une clé privée qui s’enchaîne à une racine de confiance dans les FS. Par défaut, AD FS crée un certificat auto-signé. Toutefois, en fonction des besoins de votre organisation, vous pouvez modifier ce certificat en certificat émis par une ca à l’aide du logiciel en snap-in de gestion AD FS.  <br/>**Attention :** Le certificat de signature de jetons est essentiel à la stabilité des FS. Si le certificat est modifié, Microsoft 365 être averti de la modification. Si aucune notification n’est fournie, les utilisateurs ne peuvent pas se Microsoft 365 offres de services.<br/>**Recommandation :** Nous vous recommandons d’utiliser le certificat de signature de jetons auto-signé généré par AD FS. Ce faisant, il gère ce certificat pour vous par défaut. Par exemple, lorsque ce certificat est sur le point d’expirer, AD FS génère un nouveau certificat auto-signé.  <br/> |
   
Les serveurs proxy de fédération nécessitent le certificat décrit dans le tableau suivant.
  
| Type de certificat | Description | Ce que vous devez savoir avant de déployer |
|:-----|:-----|:-----|
|certificat SSL  <br/> |Il s’agit d’un certificat SSL standard utilisé pour sécuriser les communications entre un serveur de fédération, un serveur proxy de fédération et des ordinateurs clients Internet.  <br/> |Ce certificat SSL doit être lié au site web par défaut dans IIS avant de pouvoir exécuter l’Assistant Configuration du serveur proxy de fédération AD FS.  <br/> Ce certificat doit avoir le même nom d’objet que le certificat SSL qui a été configuré sur le serveur de fédération dans le réseau d’entreprise.  <br/> **Recommandation :** Nous vous recommandons d’utiliser le même certificat d’authentification serveur configuré sur le serveur de fédération à qui ce serveur proxy de fédération se connecte.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certificats pour la découverte automatique, Outlook Anywhere et la synchronisation Active Directory

Vos serveurs d’accès au client Exchange 2013, Exchange 2010, Exchange 2007 et Exchange 2003 nécessitent un certificat SSL tiers pour les connexions sécurisées pour les services de synchronisation de découverte automatique, Outlook Anywhere et Active Directory. Ce certificat est peut-être déjà installé dans votre environnement local.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certificat pour un serveur Exchange hybride

Vos serveurs externes Exchange hybrides nécessitent un certificat SSL tiers pour une connectivité sécurisée avec le service Exchange Online client. Vous devez obtenir ce certificat auprès de votre fournisseur SSL tiers.
  
## <a name="microsoft-365-certificate-chains"></a>Microsoft 365 Chaînes de certificats

Cet article décrit les certificats que vous devrez peut-être installer sur votre infrastructure. Pour plus d’informations sur les certificats installés sur nos serveurs Microsoft 365, voir [Microsoft 365 chaînes de certificats.](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb)
  
## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 Entreprise](microsoft-365-overview.md)