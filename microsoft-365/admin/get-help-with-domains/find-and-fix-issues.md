---
title: Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: Découvrez comment effectuer le suivi des problèmes rencontrés lors de la configuration d’un domaine personnalisé en veillant à ce que les enregistrements DNS soient correctement configurés.
ms.openlocfilehash: f6c311926952d955813d2c45f688634c2c38fc01
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68198820"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
La configuration de votre domaine pour qu’il fonctionne avec Microsoft 365 peut s’avérer difficile. Le système DNS est exigeant et la configuration DNS pour votre domaine a une incidence sur les activités professionnelles importantes, comme le courrier.

> [!NOTE]
> Vous pouvez rechercher des problèmes avec votre domaine en vérifiant son état. Accédez à **Domaines** **d’installation** >  et affichez les notifications dans la colonne **État**. Si vous rencontrez un problème, sélectionnez les trois points (autres actions), puis **choisissez Vérifier l’intégrité**. Le volet qui s’ouvre décrit tous les problèmes qui se produisent avec votre domaine.
  
## <a name="whats-going-on"></a>Que se passe-t-il ?

- [Vous ne pouvez pas vérifier votre domaine ?](#cant-verify-your-domain)
    
- [Outlook ne fonctionne pas ?](#outlook-isnt-working)
    
- [L’e-mail de tout le monde a été basculé vers Microsoft 365 et vous vouliez uniquement que votre e-mail bascule ?](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [Vous ne pouvez pas confirmer l’état du compte scolaire ou à but non lucratif ?](#cant-confirm-non-profit-or-school-account-status)

- [Les services ne fonctionnent pas avec votre domaine ?](#services-not-working-with-your-domain)
    
- [L’accès à votre site web ne fonctionne pas ?](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>Vous ne pouvez pas vérifier votre domaine ?

Plusieurs raisons fréquentes peuvent empêcher le fonctionnement correct de la vérification du domaine :
  
1. **The verification record value isn't quite correct.** Doublecheck that you've copied and pasted the exact value into the TXT verification record at your DNS host. One common issue is not including the "MS=" part of the record. We need that too! 
    
2. **L'enregistrement n'a pas été sauvegardé.** Pour certains hôtes DNS, une étape supplémentaire est nécessaire pour enregistrer le fichier de zone (emplacement de stockage de l'enregistrement DNS) de façon à ce qu'il soit mis à jour sur Internet. Vérifiez que vous avez enregistré vos modifications afin que Microsoft 365 puisse voir et vérifier l’enregistrement. 
    
3. **L’enregistrement n’a pas été mis à jour sur Internet.** Il ne faut généralement que quelques minutes pour que nous puissions voir le nouvel enregistrement, mais il peut parfois prendre aussi longtemps que quelques heures. 
    
## <a name="outlook-isnt-working"></a>Outlook ne fonctionne pas ?

Si vous avez défini votre enregistrement MX et les autres enregistrements DNS correctement pour votre domaine, mais que le courrier ne fonctionne pas, nous pouvons vous aider à [résoudre les problèmes liés à Outlook que vous rencontrez](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>L’e-mail de tout le monde a été basculé vers Microsoft 365 et vous vouliez uniquement que votre e-mail bascule ?
<a name="BKMK_EmailSwitched"> </a>

Lorsque vous ajoutez votre domaine à Microsoft 365, l’enregistrement MX de votre domaine est généralement mis à jour (par vous ou Par Microsoft 365) pour pointer vers Microsoft 365, et tous les e-mails envoyés à ce domaine commencent à arriver à Microsoft 365. Avant de modifier l’enregistrement MX, veillez à créer des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui ont des e-mails sur votre domaine.
  
Que se passe-t-il si vous ne souhaitez pas déplacer le courrier électronique de tous les utilisateurs de votre domaine vers Microsoft 365 ? Vous pouvez prendre des mesures pour [piloter Microsoft 365 avec seulement quelques adresses e-mail à la place](../setup/domains-faq.yml).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>Vous ne pouvez pas confirmer l’état du compte scolaire ou à but non lucratif ?
<a name="BKMK_validateAcct"> </a>

Il existe quelques scénarios où vous devez simplement vérifier le domaine de votre organisation et ne pas configurer de services. Par exemple, pour prouver à Microsoft 365 que votre organisation est éligible pour un abonnement scolaire.
  
Consultez les conseils dans [Vérifier votre domaine Microsoft 365 pour prouver la propriété, l’état de l’éducation ou à but non lucratif, ou pour activer Yammer](../setup/domains-faq.yml) pour vous assurer que vous avez effectué toutes les étapes requises. C’est un peu différent pour chaque situation. 
  
## <a name="services-not-working-with-your-domain"></a>Les services ne fonctionnent pas avec votre domaine ?

Nous pouvons vous aider à identifier les problèmes liés à la configuration DNS de votre domaine. L’utilitaire de résolution des problèmes de domaines dans Microsoft 365 vous indique tous les enregistrements qui doivent être corrigés et exactement ce à quoi les enregistrements doivent être définis. 

> [!TIP]
> Votre DNS est correctement configuré, mais le courrier électronique ne fonctionne pas dans Outlook sur votre ordinateur de bureau ? Découvrez les [différents scénarios de flux de courrier que vous pouvez avoir avec Microsoft 365](/exchange/mail-flow-best-practices/mail-flow-best-practices) pour vous assurer que vous avez configuré les éléments correctement pour votre entreprise. Vous pouvez également obtenir de l'aide concernant la résolution des problèmes liés à le courrier dans la page suivante : [Résoudre les problèmes liés à Outlook](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>Vous ne parvenez pas à accéder à votre site web ?

Si vous avez corrigé tous les problèmes DNS et que vous rencontrez toujours des difficultés, essayez l'une des solutions suivantes.
  
- Personnes ne parvenez pas à accéder à votre site web à *l’adresse contoso.com* : [Suivi des problèmes de site web](../setup/add-domain.md)
    
- Vous ne pouvez pas mettre à jour votre enregistrement A ou CNAME pour pointer vers votre site web : [mettre à jour les enregistrements DNS personnalisés dans Microsoft 365](../setup/add-domain.md)

## <a name="related-content"></a>Contenu associé

[Résoudre les problèmes : Auditer les données sur les modifications de domaine vérifiées](/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain) (article)\
[FAQ sur les domaines](../setup/domains-faq.yml) (article)

