---
title: Prise en charge du protocole IPv6 dans les services Office 365
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
description: 'Résumé : Décrit la prise en charge d’IPv6 dans Microsoft Office 365 composants et dans Office 365 offres gouvernementales.'
ms.openlocfilehash: d526cc2c701ebfcfd322c10c3147f085c6eecb8acb47ed6a55a3c95641ea76cb
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53858998"
---
# <a name="ipv6-support-in-office-365-services"></a>Prise en charge du protocole IPv6 dans les services Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Office 365 prend en charge IPv6 et IPv4 ; toutefois, toutes les Office 365 fonctionnalités sont entièrement activées avec IPv6. Cela signifie que vous devez utiliser IPv4 et IPv6 pour vous connecter à Office 365. Si vous filtrez votre trafic sortant vers Office 365, la liste complète des adresses IPv6 qui sont pris en charge par Office 365 se trouve dans l’article Office 365 URL et [plages d’adresses IP.](urls-and-ip-address-ranges.md) Une fois votre réseau configuré et les adresses IPv6 appropriées autorisées, vous pouvez télécharger le plan de [test Office 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) à partir du Centre de téléchargement Microsoft.
  
## <a name="ipv6-support-in-office-365-subscription-service"></a>Prise en charge d’IPv6 dans Office 365 service d’abonnement

### <a name="exchange-online-and-ipv6"></a>Exchange Online et IPv6

Si le programme que vous utilisez pour vous connecter à Exchange Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications à Exchange Online, utilisez les plages d’adresses IP dans Office 365 URL et les [plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint En ligne et IPv6

 **Office 365 Secteur public G1/G3/G4/K1** Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il tentera d’utiliser IPv6 par défaut.
  
 **Cloud public multi-locataire** Microsoft active SharePoint Online IPv6 à votre demande. Vous devez fournir les adresses IP notées CIDR pour l’infrastructure DNS de votre organisation. N’oubliez pas que cette infrastructure DNS ne peut pas être partagée par d’autres organisations pour qu’IPv6 soit activé pour votre client. Une fois IPv6 activé, si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilise IPv6 par défaut.
  
Si le programme que vous utilisez pour vous connecter à SharePoint Online prend en charge IPv6, il utilisera IPv6 par défaut sur les réseaux câblés et sans fil. Si vous souhaitez contrôler les communications vers SharePoint Online, utilisez les plages d’adresses IP Office 365 [url et les plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype Entreprise et IPv6

Sachez qu’IPv6 n’est pas pris en Skype Entreprise et ne peut plus être activé.

### <a name="microsoft-teams-and-ipv6"></a>Microsoft Teams et IPV6

Microsoft Teams Le routage direct prend uniquement en charge IPv4. Le service Microsoft Teams et le client sont tous deux en charge IPv4 et IPv6. Si vous souhaitez contrôler les communications à Microsoft Teams, utilisez les plages d’adresses IP dans Office 365 [URL et les plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection et IPv6

Exchange Online Protection (EOP) prend en charge IPv6 si la transmission se produit par le protocole transport Layer Security. Pour la plage EOP, utilisez [Office 365 URL et plages d’adresses IP.](urls-and-ip-address-ranges.md)
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Prise en charge d’IPv6 pour Office 365 offres gouvernementales

Office 365 La prise en charge d’IPv6 pour les offres gouvernementales est conforme à la Office de gestion et de budget (OMB) Premier responsable des responsables de l’information des services et agences exécutifs, ainsi qu’au programme d’adoption du protocole IPv6 (Internet Protocol Version 6) par le gouvernement fédéral. [Microsoft Office 365 pour le gouvernement](https://go.microsoft.com/fwlink/p/?LinkId=325414) est un service multi-clients qui stocke les données du gouvernement américain dans un cloud communautaire séparé. Comme d’autres Office 365, il fournit des services de productivité et de collaboration, notamment Exchange Online, Skype Entreprise, SharePoint Online et Applications Microsoft 365 pour les grandes entreprises. 

Les Microsoft Office 365 du gouvernement ne s’appliquent qu’en 2013 et aux ultérieures. Pour plus d’informations sur les offres Office 365 pour le gouvernement, voir [Annonces](https://go.microsoft.com/fwlink/p/?LinkId=325414)Office 365 pour le gouvernement : une Cloud de la communauté du secteur public . La réglementation ITAR (International Traffic in Arms Regulations) est un ensemble de réglementations gouvernementales américaines qui contrôlent l’exportation et l’importation d’articles et de services relatifs à la défense sur la liste de munitions des États-Unis [(USML).](https://go.microsoft.com/fwlink/p/?LinkId=325415) 

Microsoft Office 365 entreprise fournit des services d’hébergement dédiés pour les solutions de productivité Microsoft qui permettent de prendre en charge les exigences de sécurité, de confidentialité et de conformité réglementaire pour les agences fédérales américaines nécessitant la certification FISMA (Federal Information Security Management) et les entités commerciales soumises à ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>Éléments à prendre en compte lors de l’utilisation d’IPv6 Office 365

Nous vous recommandons de ne pas désactiver IPv6. Pour plus d’informations, consultez cet [article d’aide.](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users) Pour déterminer les versions IP utilisées sur votre réseau, prenons en compte les considérations suivantes :
  
- Si l’affichage de la commande **IPConfig** à l’invite de commandes contient des lignes nommées « Adresse IPv6 » ou « Adresse IPv6 temporaire », vous avez IPv6 dans votre environnement.

- Si toutes les adresses IPv6 commencent par « fe80 » et correspondent aux lignes nommées « Link-Local IPv6 Address », vous n’avez pas IPv6 dans votre environnement.

Ces considérations peuvent s’appliquer à votre réseau :
  
- Le service d’abonnement public ne prend pas en charge l’achat par carte de crédit sur IPv6. Cela ne s’applique pas au Cloud de la communauté du secteur public (Cloud de la communauté du secteur public), car les gouvernements ont Accord Entreprise (EA).

- IPv6 ne prend pas en charge certains scénarios RMS (Rights Management Services).

- IPv6 ne prend pas en charge BlackBerry® Enterprise Server (BES), car BlackBerry ne prend pas en charge IPv6.

- Si vous utilisez les services AD FS (Active Directory Federation Services) avec Office 365, la publicité de votre point de terminaison réseau AD FS pour Office 365 l’utilisation d’IPv6 n’est pas prise en charge. Vous ne devez pas inclure d’enregistrements AAAA dans l’entrée DNS AD FS lors de l’utilisation Exchange Online. 

Voici un bref lien que vous pouvez utiliser pour revenir : [https://aka.ms/o365ip6]()
  
## <a name="see-also"></a>Voir aussi

[Feuille de route Learning IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Guide de survie IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
