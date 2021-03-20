---
title: Prise en charge du protocole IPv6 dans les services Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
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
description: 'Résumé : Décrit la prise en charge d’IPv6 dans Microsoft Office 365 et dans les offres Office 365 pour le gouvernement.'
ms.openlocfilehash: 7f06ed6f8df2c6552ee0a331ad958bca289d0a09
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50909681"
---
# <a name="ipv6-support-in-office-365-services"></a>Prise en charge du protocole IPv6 dans les services Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Office 365 prend en charge IPv6 et IPv4 ; Toutefois, toutes les fonctionnalités Office 365 ne sont pas entièrement activées avec IPv6. Cela signifie que vous devez utiliser IPv4 et IPv6 pour vous connecter à Office 365. Si vous filtrez votre trafic sortant vers Office 365, vous pouvez trouver la liste complète des adresses IPv6 pris en charge par Office 365 dans l’article URL et [plages d’adresses IP Office 365.](urls-and-ip-address-ranges.md) Une fois votre réseau configuré et les adresses IPv6 appropriées autorisées, vous pouvez télécharger le plan de [test Office 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) à partir du Centre de téléchargement Microsoft.
  
## <a name="ipv6-support-in-office-365-subscription-service"></a>Prise en charge d’IPv6 dans le service d’abonnement Office 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online et IPv6

Si le programme que vous utilisez pour vous connecter à Exchange Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications vers Exchange Online, utilisez les plages d’adresses IP dans les URL Office 365 et les [plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online et IPv6

 **Office 365 Pour le gouvernement G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il tentera d’utiliser IPv6 par défaut.
  
 **Cloud public multi-locataire** Microsoft active SharePoint Online IPv6 à votre demande. Vous devez fournir les adresses IP notées CIDR pour l’infrastructure DNS de votre organisation. N’oubliez pas que cette infrastructure DNS ne peut pas être partagée par d’autres organisations pour qu’IPv6 soit activé pour votre client. Une fois IPv6 activé, si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilise IPv6 par défaut.
  
Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications vers SharePoint Online, utilisez les plages d’adresses IP dans les URL Office 365 et les [plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
 **Office 365 Pour le gouvernement G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il tentera d’utiliser IPv6 par défaut.
  
### <a name="skype-for-business-and-ipv6"></a>Skype Entreprise et IPv6

Sachez qu’IPv6 n’est pas pris en charge dans Skype Entreprise et ne peut plus être activé.

### <a name="microsoft-teams-and-ipv6"></a>Microsoft Teams et IPV6

Le routage direct De Microsoft Teams prend uniquement en charge IPv4. Le service et le client Microsoft Teams supportent IPv4 et IPv6. Si vous souhaitez contrôler les communications vers Microsoft Teams, utilisez les plages d’adresses IP dans les URL Office 365 et les [plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection et IPv6

Exchange Online Protection (EOP) prend en charge IPv6 si la transmission se produit par le protocole transport Layer Security. Pour la plage EOP, utilisez les URL [Office 365 et les plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Prise en charge d’IPv6 pour les offres Office 365 pour le gouvernement

La prise en charge d’Office 365 IPv6 pour les offres gouvernementales est conforme à la loi OMB (Office of Management and Budget) Premier responsable de l’information des services et agences, ainsi qu’à l’adoption par le gouvernement fédéral du protocole IPv6 (Internet Protocol Version 6). [Microsoft Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414) pour le gouvernement est un service multi-clients qui stocke les données du gouvernement américain dans un cloud communautaire séparé. Comme d’autres offres Office 365, il fournit des services de productivité et de collaboration, notamment Exchange Online, Skype Entreprise, SharePoint Online et Microsoft 365 Apps for enterprise. 

Les Microsoft Office 365 pour le gouvernement s’appliquent uniquement pour 2013 et les ultérieures. Pour plus d’informations sur les offres Office 365 pour le gouvernement, voir [Annonce d’Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414)pour le gouvernement : un cloud communautaire pour le gouvernement des États-Unis. La réglementation ITAR (International Traffic in Arms Regulations) est un ensemble de réglementations du gouvernement américain qui contrôlent l’exportation et l’importation d’articles et de services relatifs à la défense sur la liste de munitions des États-Unis [(USML).](https://go.microsoft.com/fwlink/p/?LinkId=325415) 

Microsoft Office 365 pour les entreprises fournit des services d’hébergement dédiés pour les solutions de productivité Microsoft qui assurent la sécurité, la confidentialité et la conformité réglementaire pour les agences fédérales américaines nécessitant la certification FISMA (Federal Information Security Management) et les entités commerciales soumises à ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Éléments à prendre en compte lors de l’utilisation d’IPv6 et d’Office 365

Nous vous recommandons de ne pas désactiver IPv6. Pour plus d’informations, consultez cet [article d’aide.](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users) Pour déterminer les versions IP utilisées sur votre réseau, prenons en compte les considérations suivantes :
  
- Si l’affichage de la commande **IPConfig** à l’invite de commandes contient des lignes nommées « Adresse IPv6 » ou « Adresse IPv6 temporaire », vous avez IPv6 dans votre environnement.

- Si toutes les adresses IPv6 commencent par « fe80 » et correspondent aux lignes nommées « Link-Local IPv6 Address », vous n’avez pas IPv6 dans votre environnement.

Ces considérations peuvent s’appliquer à votre réseau :
  
- Le service d’abonnement public ne prend pas en charge l’achat par carte de crédit sur IPv6. Cela ne s’applique pas au cloud communautaire du gouvernement (GCC), car les gouvernements disposent de licences d’accord Entreprise (EA).

- IPv6 ne prend pas en charge certains scénarios RMS (Rights Management Services).

- IPv6 ne prend pas en charge BlackBerry® Enterprise Server (BES), car BlackBerry ne prend pas en charge IPv6.

- Si vous utilisez les services AD FS (Active Directory Federation Services) avec Office 365, la publicité de votre point de terminaison réseau AD FS vers Office 365 à l’aide d’IPv6 n’est pas prise en charge. Vous ne devez pas inclure d’enregistrements AAAA dans l’entrée DNS AD FS lors de l’utilisation d’Exchange Online. 

Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365ip6]()
  
## <a name="see-also"></a>Voir aussi

[Parcours de formation IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Guide de survie IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)