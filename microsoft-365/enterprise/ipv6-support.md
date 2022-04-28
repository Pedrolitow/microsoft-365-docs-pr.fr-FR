---
title: Prise en charge D’ipv6 dans les services Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/03/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Résumé : Décrit le support IPv6 dans Microsoft 365 composants et dans Microsoft 365 offres gouvernementales.'
ms.openlocfilehash: 6cd53b71c6e15346d4940c539eea4aff0e5a613e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096477"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Prise en charge D’ipv6 dans les services Microsoft 365

Microsoft 365 prend en charge IPv6 et IPv4 ; toutefois, toutes les fonctionnalités Microsoft 365 ne sont pas entièrement activées avec IPv6. Cela signifie que vous devez utiliser IPv4 et IPv6 pour vous connecter à Microsoft 365. Si vous filtrez votre trafic sortant vers Microsoft 365, la liste complète des adresses IPv6 prises en charge par Microsoft 365 se trouve dans l’article [Microsoft 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md). Une fois que votre réseau est configuré et que les adresses IPv6 appropriées sont autorisées, vous pouvez télécharger le [plan de test Microsoft 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) à partir du Centre de téléchargement Microsoft.

> [!NOTE]
> Permettre aux clients de découvrir Microsoft 365 services SaaS à partir de n’importe quel emplacement et de n’importe quel appareil est une priorité pour Microsoft. Cela inclut le fait de permettre aux clients de se connecter et de consommer Microsoft 365 à partir de clients IPv6 activés et IPv6 uniquement des clients et des systèmes d’information. Il inclut également l’activation des clients gouvernementaux respectant les engagements IPv6 sur leurs réseaux tout en continuant à consommer Microsoft 365 scénarios de productivité sans interruption.  
> Cet article fournit la liste des Microsoft 365 services SaaS qui autorisent la connectivité IPv6 directe aujourd’hui. L’étendue des services permettant une connectivité IPv6 directe devrait continuer à s’étendre. Microsoft 365 services non mentionnés explicitement pour la prise en charge IPv6 directe, pour inclure les services d’authentification Azure Active Directory (AAD), doivent être considérés comme nécessitant que DNS64/NAT64 soit connecté à partir de clients et d’environnements IPv6 uniquement.  Ceci est conforme à l’intention actuellement décrite dans la documentation NIST USGv6 existante : Les exigences de capacité de mécanisme de transition dans la [publication spéciale NIST 500-267A Revision 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 sont des technologies acceptables à utiliser.
> - Prise en charge NAT64 du mécanisme de transition NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Avec état NAT64 : Traduction d’adresses réseau et de protocoles des clients IPv6 vers les serveurs IPv4
> - Prise en charge de DNS64 pour le mécanisme de transition DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64 : Extensions DNS pour la traduction d’adresses réseau des clients IPv6 vers le serveur IPv4

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>Prise en charge d’IPv6 dans Microsoft 365 service d’abonnement

### <a name="exchange-online-and-ipv6"></a>Exchange Online et IPv6

Si le programme que vous utilisez pour vous connecter à Exchange Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications vers Exchange Online, utilisez les plages d’adresses IP dans [Microsoft 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online et IPv6

 **Microsoft 365 Gouvernement G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il tente d’utiliser IPv6 par défaut.
  
 **Cloud multilocataire public** Microsoft active SharePoint IPv6 en ligne à votre demande. Vous devez fournir les adresses IP notées CIDR pour l’infrastructure DNS de votre organisation. N’oubliez pas que cette infrastructure DNS ne peut pas être partagée par d’autres organisations pour qu’IPv6 soit activé pour votre locataire. Une fois IPv6 activé, si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilise IPv6 par défaut.
  
Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications vers SharePoint Online, utilisez les plages d’adresses IP dans [Microsoft 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype Entreprise et IPv6

Sachez que IPv6 n’est pas pris en charge dans Skype Entreprise et ne peut plus être activé.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams, passerelle SIP et IPV6

Microsoft Teams le routage direct et la passerelle SIP prennent uniquement en charge IPv4. Le service Microsoft Teams et le client prennent en charge IPv4 et IPv6. Si vous souhaitez contrôler les communications vers Microsoft Teams, utilisez les plages d’adresses IP dans [Microsoft 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection et IPv6

Exchange Online Protection (EOP) prend en charge IPv6 si la transmission se produit via le protocole de sécurité de la couche de transport. Pour la plage EOP, utilisez [Microsoft 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>Support IPv6 pour Microsoft 365 offres gouvernementales

Microsoft 365 l’appui de l’IPv6 aux offres gouvernementales est conforme à la Office du Protocole de gestion et de budget (OMB) pour les directeurs de l’information en chef des ministères et organismes exécutifs, ainsi qu’au protocole IPv6 (Adoption par le gouvernement fédéral du protocole Internet version 6). [Microsoft Microsoft 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) est un service multilocataire qui stocke les données du gouvernement des États-Unis dans un cloud communautaire distinct. Comme d’autres offres Microsoft 365, elle fournit des services de productivité et de collaboration, notamment Exchange Online, Skype Entreprise, SharePoint Online et Applications Microsoft 365 pour les grandes entreprises. 

Les offres Microsoft Microsoft 365 gouvernement s’appliquent uniquement pour 2013 et versions ultérieures. Pour plus d’informations sur les offres gouvernementales Microsoft 365, consultez [Announcing Microsoft 365 for Government: A US Cloud de la communauté du secteur public](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) est un ensemble de réglementations du gouvernement américain qui contrôlent l’exportation et l’importation d’articles et de services liés à la défense sur la [liste des munitions États-Unis (USML).](https://go.microsoft.com/fwlink/p/?LinkId=325415) 

Microsoft Microsoft 365 for Enterprises fournit des services d’hébergement dédiés pour les solutions de productivité Microsoft qui prennent en charge les exigences de sécurité, de confidentialité et de conformité réglementaire pour les agences fédérales américaines nécessitant la certification FISMA (Federal Information Security Management) et les entités commerciales soumises à ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>Éléments à prendre en compte lors de l’utilisation d’IPv6 et de Microsoft 365

Nous vous recommandons de ne pas désactiver IPv6. Pour plus d’informations, consultez cet [article d’aide](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Pour déterminer les versions IP utilisées sur votre réseau, tenez compte des éléments suivants :
  
- Si l’affichage de la commande **IPConfig** à l’invite de commandes contient des lignes nommées « Adresse IPv6 » ou « Adresse IPv6 temporaire », vous avez IPv6 dans votre environnement.

- Si toutes les adresses IPv6 commencent par « fe80 » et correspondent à des lignes nommées « Link-Local IPv6 Address », vous n’avez pas IPv6 dans votre environnement.

Ces considérations peuvent s’appliquer à votre réseau :
  
- Le service d’abonnement public ne prend pas en charge l’achat par carte de crédit sur IPv6. Cela ne s’applique pas aux Cloud de la communauté du secteur public (Cloud de la communauté du secteur public), car les gouvernements disposent de licences Accord Entreprise (EA).

- IPv6 ne prend pas en charge certains scénarios RMS (Rights Management Services).

- IPv6 ne prend pas en charge BlackBerry® Enterprise Server (BES), car BlackBerry ne prend pas en charge IPv6.

- Si vous utilisez Services ADFS (AD FS) avec Microsoft 365, la publicité de votre point de terminaison réseau AD FS pour Microsoft 365 l’utilisation d’IPv6 n’est pas prise en charge. Vous ne devez pas inclure d’enregistrements AAAA dans l’entrée DNS AD FS lors de l’utilisation de Exchange Online. 

Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Voir aussi

[Feuille de route Learning IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Guide de survie IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
