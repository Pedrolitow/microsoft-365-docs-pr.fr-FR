---
title: Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: Découvrez comment détecter les problèmes que vous rencontrez lors de la configuration d’un domaine personnalisé en vous assurant que les enregistrements DNS sont correctement configurés.
ms.openlocfilehash: 8d46d681e44a0bebd0a9571d18ffa95e1e554dc8
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295045"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
L’obtention de votre domaine configuré pour fonctionner avec Microsoft 365 peut être complexe. Le système DNS est exigeant et la configuration DNS pour votre domaine a une incidence sur les activités professionnelles importantes, comme le courrier.

> [!NOTE]
> Vous pouvez vérifier les problèmes liés à votre domaine en vérifiant son état. Accédez à **configurer**  >  les**domaines** et affichez les notifications dans la colonne **État** . Si vous voyez un problème, sélectionnez autres actions (trois points), puis sélectionnez **vérifier l’intégrité**. Le volet qui s’ouvre décrit tous les problèmes liés à votre domaine.
  
## <a name="whats-going-on"></a>Que se passe-t-il ?

- [Vous ne pouvez pas vérifier votre domaine ?](#cant-verify-your-domain)
    
- [Outlook ne fonctionne pas ?](#outlook-isnt-working)
    
- [Le courrier de tous les utilisateurs a été remplacé par Microsoft 365 et vous n’avez besoin que de votre courrier électronique pour basculer ?](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [Vous ne pouvez pas confirmer l’état des comptes scolaires ou scolaires ?](#cant-confirm-non-profit-or-school-account-status)

- [Les services ne fonctionnent-ils pas avec votre domaine ?](#services-not-working-with-your-domain)
    
- [L’accès à votre site Web ne fonctionne pas ?](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>Vous ne pouvez pas vérifier votre domaine ?
<a name="BKMK_verify"> </a>

Plusieurs raisons fréquentes peuvent empêcher le fonctionnement correct de la vérification du domaine :
  
1. **La valeur de l'enregistrement de vérification est incorrecte.** Vérifiez que vous avez copié et collé la valeur exacte dans l'enregistrement de vérification TXT configuré auprès de votre hôte DNS. Le problème vient souvent de l'omission de la portion « MS= » de l'enregistrement. Celle-ci est indispensable. 
    
2. **L'enregistrement n'a pas été sauvegardé.** Pour certains hôtes DNS, une étape supplémentaire est nécessaire pour enregistrer le fichier de zone (emplacement de stockage de l'enregistrement DNS) de façon à ce qu'il soit mis à jour sur Internet. Vérifiez que vous avez enregistré vos modifications afin que Microsoft 365 puisse voir et vérifier l’enregistrement. 
    
3. **L’enregistrement n’a pas été mis à jour sur Internet.** En règle générale, il ne prend que quelques minutes pour pouvoir voir le nouvel enregistrement, mais il peut arriver que quelques heures se soient nécessaires. 
    
## <a name="outlook-isnt-working"></a>Outlook ne fonctionne pas ?
<a name="BKMK_OutlookBroken"> </a>

Si vous avez défini votre enregistrement MX et les autres enregistrements DNS correctement pour votre domaine, mais que le courrier ne fonctionne pas, nous pouvons vous aider à [résoudre les problèmes liés à Outlook que vous rencontrez](https://docs.microsoft.com/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>Le courrier de tous les utilisateurs a été remplacé par Microsoft 365 et vous n’avez besoin que de votre courrier électronique pour basculer ?
<a name="BKMK_EmailSwitched"> </a>

Lorsque vous ajoutez votre domaine à Microsoft 365, l’enregistrement MX de votre domaine est généralement mis à jour (par vous-même ou par Microsoft 365) pour pointer vers Microsoft 365, et tous les messages envoyés à ce domaine débuteront à Microsoft 365. Assurez-vous que vous avez créé des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui disposent d’un courrier électronique sur votre domaine avant de modifier l’enregistrement MX.
  
Que faire si vous ne souhaitez pas déplacer le courrier électronique de tous les membres de votre domaine vers Microsoft 365 ? Vous pouvez prendre des mesures pour [piloter Microsoft 365 avec seulement quelques adresses de messagerie](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>Vous ne pouvez pas confirmer l’état des comptes scolaires ou scolaires ?
<a name="BKMK_validateAcct"> </a>

Il existe deux scénarios pour vérifier que le domaine de votre organisation n’a pas été configuré. Par exemple, pour prouver à Microsoft 365 que votre organisation est qualifiée pour un abonnement scolaire.
  
Consultez les conseils fournis dans la partie relative [à la vérification de votre domaine Microsoft 365 pour prouver la propriété, l’état de l’organisme ou l’état de l’éducation, ou pour activer Yammer](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq) afin de vous assurer que vous avez effectué toutes les étapes requises. Il s’agit d’un peu différent pour chaque situation. 
  
## <a name="services-not-working-with-your-domain"></a>Les services ne fonctionnent pas avec votre domaine ?
<a name="BKMK_Test"> </a>

Nous pouvons vous aider à identifier les problèmes liés à la configuration DNS de votre domaine. L’utilitaire de résolution des problèmes liés aux domaines dans Microsoft 365 affiche tous les enregistrements qui doivent être corrigés, ainsi que les éléments sur lesquels les enregistrements doivent être définis. 

> [!TIP]
> Votre DNS est correctement configuré, mais le courrier électronique ne fonctionne pas dans Outlook sur votre ordinateur de bureau ? Découvrez les [différents scénarios de flux de messagerie que vous pouvez rencontrer avec Microsoft 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/mail-flow-best-practices) afin de vous assurer que vous avez configuré correctement les éléments pour votre entreprise. Vous pouvez également obtenir de l'aide concernant la résolution des problèmes liés à le courrier dans la page suivante : [Résoudre les problèmes liés à Outlook](https://docs.microsoft.com/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>Vous ne parvenez pas à accéder à votre site web ?
<a name="BKMK_Website"> </a>

Si vous avez corrigé tous les problèmes DNS et que vous rencontrez toujours des difficultés, essayez l'une des solutions suivantes.
  
- Les utilisateurs ne peuvent pas accéder à votre site web à l'adresse www.mondomaine.com : [Identifier les problèmes liés au site web](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain)
    
- Vous ne pouvez pas mettre à jour votre enregistrement A ou CNAMe pour qu’il pointe vers votre site Web : [mettre à jour les enregistrements DNS personnalisés dans Microsoft 365](../dns/add-or-edit-custom-dns-records.md)

## <a name="related-content"></a>Contenu connexe

[Résolution des problèmes : données d’audit sur les modifications de domaine vérifiées](https://docs.microsoft.com/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain)

    
