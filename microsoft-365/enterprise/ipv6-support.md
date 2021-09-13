---
title: Prise en charge D’ipv6 dans les services Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/28/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Résumé : Décrit la prise en charge d’IPv6 dans Microsoft 365 composants et dans Microsoft 365 offres gouvernementales.'
ms.openlocfilehash: be9ce7cc2eaaec74889e9d88ddfa9b781c6d308e
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59205532"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Prise en charge D’ipv6 dans les services Microsoft 365

Microsoft 365 prend en charge IPv6 et IPv4 ; toutefois, toutes les Microsoft 365 fonctionnalités sont entièrement activées avec IPv6. Cela signifie que vous devez utiliser IPv4 et IPv6 pour vous connecter à Microsoft 365. Si vous filtrez votre trafic sortant vers Microsoft 365, la liste complète des adresses IPv6 qui sont pris en charge par Microsoft 365 se trouve dans l’article Microsoft 365 URL et [plages d’adresses IP.](urls-and-ip-address-ranges.md) Une fois votre réseau configuré et les adresses IPv6 appropriées autorisées, vous pouvez télécharger le plan de [test Microsoft 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) à partir du Centre de téléchargement Microsoft.

> [!NOTE]
> Permettre aux clients d’Microsoft 365 services SaaS à partir de n’importe quel emplacement et n’importe quel appareil est une priorité pour Microsoft. Cela inclut l’autoriser à se connecter et à utiliser des Microsoft 365 à partir de clients et de systèmes d’information IPv6 activés et IPv6 uniquement. Il inclut également la possibilité pour les clients du secteur gouvernemental de respecter les engagements IPv6 sur leurs réseaux tout en continuant à consommer Microsoft 365 scénarios de productivité sans interruption.  
> Cet article fournit la liste des services SaaS Microsoft 365 qui autorisent la connectivité IPv6 directe aujourd’hui. L’étendue des services permettant une connectivité IPv6 directe devrait continuer à se développer. Microsoft 365 services non explicitement mentionnés pour la prise en charge IPv6 directe, pour inclure les services d’authentification Azure Active Directory (AAD), doivent être considérés comme nécessitant la connexion DNS64/NAT64 à partir des clients et environnements IPv6 uniquement.  Cela est en adéquation avec l’intention actuellement décrite dans la documentation USGv6 NIST existante : les exigences de capacité du mécanisme de transition dans la composition spéciale [NIST 500-267A Revision 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 sont des technologies acceptables à utiliser.
> - Prise en charge de NAT64 pour le mécanisme de transition [NAT64 RFC6146 NAT64](https://datatracker.ietf.org/doc/html/rfc6146) avec état : adresse réseau et traduction de protocole des clients IPv6 vers les serveurs IPv4
> - Prise en charge DNS64 du mécanisme de transition DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64 : extensions DNS pour la traduction d’adresses réseau des clients IPv6 vers le serveur IPv4

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>Prise en charge d’IPv6 dans Microsoft 365 service d’abonnement

### <a name="exchange-online-and-ipv6"></a>Exchange Online et IPv6

Si le programme que vous utilisez pour vous connecter à Exchange Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications à Exchange Online, utilisez les plages d’adresses IP dans Microsoft 365 URL et les [plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint En ligne et IPv6

 **Microsoft 365 gouvernement G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il tentera d’utiliser IPv6 par défaut.
  
 **Cloud public multi-locataire** Microsoft active SharePoint Online IPv6 à votre demande. Vous devez fournir les adresses IP notées CIDR pour l’infrastructure DNS de votre organisation. N’oubliez pas que cette infrastructure DNS ne peut pas être partagée par d’autres organisations pour qu’IPv6 soit activé pour votre client. Une fois IPv6 activé, si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilise IPv6 par défaut.
  
Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications vers SharePoint Online, utilisez les plages d’adresses IP dans Microsoft 365 URL et les [plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype Entreprise et IPv6

Sachez qu’IPv6 n’est pas pris en Skype Entreprise et ne peut plus être activé.

### <a name="microsoft-teams-and-ipv6"></a>Microsoft Teams et IPV6

Microsoft Teams Le routage direct prend uniquement en charge IPv4. Le service Microsoft Teams et le client sont tous deux en charge IPv4 et IPv6. Si vous souhaitez contrôler les communications à Microsoft Teams, utilisez les plages d’adresses IP dans Microsoft 365 [URL et les plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection et IPv6

Exchange Online Protection (EOP) prend en charge IPv6 si la transmission se produit par le protocole transport Layer Security. Pour la plage EOP, utilisez [Microsoft 365 URL et plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>Prise en charge d’IPv6 Microsoft 365 offres gouvernementales

Microsoft 365 La prise en charge d’IPv6 pour les offres gouvernementales est conforme à la Office de gestion et de budget (OMB) Premier responsable des responsables de l’information des services et agences exécutifs, ainsi qu’au programme d’adoption du protocole IPv6 (Internet Protocol Version 6) par le gouvernement fédéral. [Microsoft Microsoft 365 pour le gouvernement](https://go.microsoft.com/fwlink/p/?LinkId=325414) est un service multi-clients qui stocke les données du gouvernement américain dans un cloud communautaire séparé. Comme d’autres Microsoft 365, il fournit des services de productivité et de collaboration, notamment Exchange Online, Skype Entreprise, SharePoint Online et Applications Microsoft 365 pour les grandes entreprises. 

Les offres Microsoft Microsoft 365 pour le gouvernement s’appliquent uniquement pour 2013 et les ultérieures. Pour plus d’informations sur les offres Microsoft 365 pour le gouvernement, voir [Annonces](https://go.microsoft.com/fwlink/p/?LinkId=325414)Microsoft 365 pour le gouvernement : une Cloud de la communauté du secteur public . La réglementation ITAR (International Traffic in Arms Regulations) est un ensemble de réglementations gouvernementales américaines qui contrôlent l’exportation et l’importation d’articles et de services relatifs à la défense sur la liste de munitions des États-Unis [(USML).](https://go.microsoft.com/fwlink/p/?LinkId=325415) 

Microsoft Microsoft 365 pour entreprises fournit des services d’hébergement dédiés pour les solutions de productivité Microsoft qui permettent de prendre en charge les exigences de sécurité, de confidentialité et de conformité réglementaire pour les agences fédérales américaines nécessitant la certification FISMA (Federal Information Security Management) et les entités commerciales soumises à ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>Éléments à prendre en compte lors de l’utilisation d’IPv6 Microsoft 365

Nous vous recommandons de ne pas désactiver IPv6. Pour plus d’informations, consultez cet [article d’aide.](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users) Pour déterminer les versions IP utilisées sur votre réseau, prenons en compte les considérations suivantes :
  
- Si l’affichage de la commande **IPConfig** à l’invite de commandes contient des lignes nommées « Adresse IPv6 » ou « Adresse IPv6 temporaire », vous avez IPv6 dans votre environnement.

- Si toutes les adresses IPv6 commencent par « fe80 » et correspondent aux lignes nommées « Link-Local IPv6 Address », vous n’avez pas IPv6 dans votre environnement.

Ces considérations peuvent s’appliquer à votre réseau :
  
- Le service d’abonnement public ne prend pas en charge l’achat par carte de crédit sur IPv6. Cela ne s’applique pas au Cloud de la communauté du secteur public (Cloud de la communauté du secteur public), car les gouvernements ont Accord Entreprise (EA).

- IPv6 ne prend pas en charge certains scénarios RMS (Rights Management Services).

- IPv6 ne prend pas en charge BlackBerry® Enterprise Server (BES), car BlackBerry ne prend pas en charge IPv6.

- Si vous utilisez les services AD FS (Active Directory Federation Services) avec Microsoft 365, la publicité de votre point de terminaison réseau AD FS pour Microsoft 365 l’utilisation d’IPv6 n’est pas prise en charge. Vous ne devez pas inclure d’enregistrements AAAA dans l’entrée DNS AD FS lors de l’utilisation Exchange Online. 

Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Voir aussi

[Feuille de route Learning IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Guide de survie IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
