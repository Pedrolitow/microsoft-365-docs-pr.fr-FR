---
title: Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: Apprenez à suivre les problèmes que vous avez à résoudre lors de la configuration d’un domaine personnalisé en vous assurez que les enregistrements DNS sont correctement configurer.
ms.openlocfilehash: dfb3c93c169a3d31c14d912ddd2cc94fb1e4ace1
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50915637"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
La mise en place de votre domaine pour utiliser Microsoft 365 peut être difficile. Le système DNS est exigeant et la configuration DNS pour votre domaine a une incidence sur les activités professionnelles importantes, comme le courrier.

> [!NOTE]
> Vous pouvez vérifier les problèmes liés à votre domaine en vérifiant son état. Go to **Setup**  >  **Domains** and view the notifications in the **Status** column. Si vous voyez un problème, sélectionnez Plus d’actions (trois points), puis **sélectionnez Vérifier l’état d’santé.** Le volet qui s’ouvre décrit les problèmes qui se produisent avec votre domaine.
  
## <a name="whats-going-on"></a>Que se passe-t-il ?

- [Vous ne pouvez pas vérifier votre domaine ?](#cant-verify-your-domain)
    
- [Outlook ne fonctionne pas ?](#outlook-isnt-working)
    
- [Tout le monde a basculé vers Microsoft 365 et vous souhaitez que votre courrier électronique bascule uniquement ?](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [Vous ne pouvez pas confirmer l’état d’un compte à but non lucratif ou scolaire ?](#cant-confirm-non-profit-or-school-account-status)

- [Les services ne fonctionnent pas avec votre domaine ?](#services-not-working-with-your-domain)
    
- [L’accès à votre site web ne fonctionne pas ?](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>Vous ne pouvez pas vérifier votre domaine ?
<a name="BKMK_verify"> </a>

Plusieurs raisons fréquentes peuvent empêcher le fonctionnement correct de la vérification du domaine :
  
1. **La valeur de l'enregistrement de vérification est incorrecte.** Vérifiez que vous avez copié et collé la valeur exacte dans l'enregistrement de vérification TXT configuré auprès de votre hôte DNS. Le problème vient souvent de l'omission de la portion « MS= » de l'enregistrement. Celle-ci est indispensable. 
    
2. **L'enregistrement n'a pas été sauvegardé.** Pour certains hôtes DNS, une étape supplémentaire est nécessaire pour enregistrer le fichier de zone (emplacement de stockage de l'enregistrement DNS) de façon à ce qu'il soit mis à jour sur Internet. Vérifiez que vous avez enregistré vos modifications afin que Microsoft 365 puisse voir et vérifier l’enregistrement. 
    
3. **L’enregistrement n’a pas été mis à jour sur Internet.** En règle générale, nous ne pouvons voir le nouvel enregistrement que quelques minutes, mais cela peut parfois prendre jusqu’à quelques heures. 
    
## <a name="outlook-isnt-working"></a>Outlook ne fonctionne pas ?
<a name="BKMK_OutlookBroken"> </a>

Si vous avez défini votre enregistrement MX et les autres enregistrements DNS correctement pour votre domaine, mais que le courrier ne fonctionne pas, nous pouvons vous aider à [résoudre les problèmes liés à Outlook que vous rencontrez](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>Tout le monde a basculé vers Microsoft 365 et vous souhaitez que votre courrier électronique bascule uniquement ?
<a name="BKMK_EmailSwitched"> </a>

Lorsque vous ajoutez votre domaine à Microsoft 365, l’enregistrement MX de votre domaine est généralement mis à jour (par vous ou Microsoft 365) pour pointer vers Microsoft 365, et tous les messages envoyés à ce domaine commencent à arriver vers Microsoft 365. Assurez-vous que vous avez créé des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui ont des messages sur votre domaine AVANT de modifier l’enregistrement MX.
  
Que se passe-t-il si vous ne souhaitez pas déplacer le courrier électronique de tous les employés de votre domaine vers Microsoft 365 ? Vous pouvez prendre des mesures pour [piloter Microsoft 365 avec seulement quelques adresses de messagerie à la place.](../setup/domains-faq.yml)
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>Vous ne pouvez pas confirmer l’état d’un compte à but non lucratif ou scolaire ?
<a name="BKMK_validateAcct"> </a>

Il existe quelques scénarios où vous devez simplement vérifier le domaine de votre organisation et ne pas configurer de services. Par exemple, pour prouver à Microsoft 365 que votre organisation est éligible pour un abonnement scolaire.
  
Consultez les instructions dans Vérifier votre domaine [Microsoft 365](../setup/domains-faq.yml) pour prouver la propriété, l’état des organisations à but non lucratif ou de l’éducation, ou pour activer Yammer pour vous assurer que vous avez effectué toutes les étapes requises. Il est légèrement différent pour chaque situation. 
  
## <a name="services-not-working-with-your-domain"></a>Les services ne fonctionnent pas avec votre domaine ?
<a name="BKMK_Test"> </a>

Nous pouvons vous aider à identifier les problèmes liés à la configuration DNS de votre domaine. L’dépannage des domaines dans Microsoft 365 vous montre tous les enregistrements qui doivent être corrigés et indique exactement ce que les enregistrements doivent être définies. 

> [!TIP]
> Votre DNS est correctement configuré, mais le courrier électronique ne fonctionne pas dans Outlook sur votre ordinateur de bureau ? Consultez les différents scénarios de flux de messagerie que vous pouvez avoir avec [Microsoft 365](/exchange/mail-flow-best-practices/mail-flow-best-practices) pour vous assurer que les choses sont correctement définies pour votre entreprise. Vous pouvez également obtenir de l'aide concernant la résolution des problèmes liés à le courrier dans la page suivante : [Résoudre les problèmes liés à Outlook](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>Vous ne parvenez pas à accéder à votre site web ?
<a name="BKMK_Website"> </a>

Si vous avez corrigé tous les problèmes DNS et que vous rencontrez toujours des difficultés, essayez l'une des solutions suivantes.
  
- Les utilisateurs ne peuvent pas accéder à votre site web à l'adresse www.mondomaine.com : [Identifier les problèmes liés au site web](../setup/add-domain.md)
    
- Vous ne pouvez pas mettre à jour votre enregistrement A ou CNAME pour qu’il pointe vers votre site web : mettre à jour des enregistrements DNS personnalisés [dans Microsoft 365](../setup/add-domain.md)

## <a name="related-content"></a>Contenu connexe

[Résolution des problèmes : données d’audit sur la modification vérifiée du domaine](/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain)

