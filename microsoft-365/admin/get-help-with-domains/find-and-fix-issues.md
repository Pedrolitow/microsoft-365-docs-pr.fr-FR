---
title: Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS dans Office 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: Découvrez comment détecter les problèmes que vous rencontrez lors de la configuration d’un domaine personnalisé en vous assurant que les enregistrements DNS sont correctement configurés.
ms.openlocfilehash: a93318d54b950b908319fe50a0cfedefe8586036
ms.sourcegitcommit: 8edad75338cf74712ca1ab5d6631b9b52ff54410
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "43115971"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records-in-office-365"></a>Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS dans Office 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
[] La configuration de votre domaine pour qu'il fonctionne avec Office 365 peut présenter des difficultés. Le système DNS est exigeant et la configuration DNS pour votre domaine a une incidence sur les activités professionnelles importantes, comme le courrier.

> [!NOTE]
> Vous pouvez vérifier les problèmes liés à votre domaine en vérifiant son état. Accédez à **configurer** > les**domaines** et affichez les notifications dans la colonne **État** . Si vous voyez un problème, sélectionnez autres actions (trois points), puis sélectionnez **vérifier l’intégrité**. Le volet qui s’ouvre décrit tous les problèmes liés à votre domaine.
  
## <a name="whats-going-on"></a>Que se passe-t-il ?

- [Vous ne pouvez pas vérifier votre domaine ?](#cant-verify-your-domain)
    
- [Outlook ne fonctionne pas ?](#outlook-isnt-working)
    
- [Le courrier de tous les utilisateurs a été basculé vers Office 365 et vous n’avez besoin que de votre courrier électronique ?](#everyones-email-got-switched-to-office-365-and-you-only-wanted-your-email-to-switch)

- [Vous ne pouvez pas confirmer l’état des comptes scolaires ou scolaires ?](#cant-confirm-non-profit-or-school-account-status)

- [Les services ne fonctionnent-ils pas avec votre domaine ?](#services-not-working-with-your-domain)
    
- [L’accès à votre site Web ne fonctionne pas ?](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>Vous ne pouvez pas vérifier votre domaine ?
<a name="BKMK_verify"> </a>

Plusieurs raisons fréquentes peuvent empêcher le fonctionnement correct de la vérification du domaine :
  
1. **La valeur de l'enregistrement de vérification est incorrecte.** Vérifiez que vous avez copié et collé la valeur exacte dans l'enregistrement de vérification TXT configuré auprès de votre hôte DNS. Le problème vient souvent de l'omission de la portion « MS= » de l'enregistrement. Celle-ci est indispensable. 
    
2. **L'enregistrement n'a pas été sauvegardé.** Pour certains hôtes DNS, une étape supplémentaire est nécessaire pour enregistrer le fichier de zone (emplacement de stockage de l'enregistrement DNS) de façon à ce qu'il soit mis à jour sur Internet. Vérifiez que vous avez enregistré vos modifications, pour permettre à Office 365 de consulter et vérifier l'enregistrement. 
    
3. **L’enregistrement n’a pas été mis à jour sur Internet.** En règle générale, il ne prend que quelques minutes pour pouvoir voir le nouvel enregistrement, mais il peut arriver que quelques heures se soient nécessaires. 
    
## <a name="outlook-isnt-working"></a>Outlook ne fonctionne pas ?
<a name="BKMK_OutlookBroken"> </a>

Si vous avez défini votre enregistrement MX et les autres enregistrements DNS correctement pour votre domaine, mais que le courrier ne fonctionne pas, nous pouvons vous aider à [résoudre les problèmes liés à Outlook que vous rencontrez](https://support.office.com/article/b3e740b9-171d-4179-bcd1-e279a363fa75.aspx).
  
## <a name="everyones-email-got-switched-to-office-365-and-you-only-wanted-your-email-to-switch"></a>Le courrier de tous les utilisateurs a été basculé vers Office 365 et vous n’avez besoin que de votre courrier électronique ?
<a name="BKMK_EmailSwitched"> </a>

Lorsque vous ajoutez votre domaine à Office 365, l’enregistrement MX de votre domaine est généralement mis à jour (par vous-même ou par Office 365) pour pointer vers Office 365 et tous les messages envoyés à ce domaine débuteront dans Office 365. Assurez-vous que vous avez créé des boîtes aux lettres dans Office 365 pour tous les utilisateurs qui disposent d’un courrier électronique sur votre domaine avant de modifier l’enregistrement MX.
  
Que faire si vous ne souhaitez pas déplacer le courrier électronique de tous les membres de votre domaine vers Office 365 ? Vous pouvez prendre des mesures pour [tester Office 365 avec seulement quelques adresses de courrier](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7.aspx).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>Vous ne pouvez pas confirmer l’état des comptes scolaires ou scolaires ?
<a name="BKMK_validateAcct"> </a>

Il existe deux scénarios pour vérifier que le domaine de votre organisation n’a pas été configuré. Par exemple, pour prouver à Office 365 que votre organisation est qualifiée pour un abonnement scolaire.
  
Consultez les conseils fournis dans la partie [vérification de votre domaine Office 365 pour prouver le propriétaire, l’organisme ou l’état de l’éducation, ou pour activer Yammer](https://support.office.com/article/87d1844e-aa47-4dc0-a61b-1b773fd4e590) afin de vous assurer que vous avez effectué toutes les étapes requises. Il s’agit d’un peu différent pour chaque situation. 
  
## <a name="services-not-working-with-your-domain"></a>Les services ne fonctionnent pas avec votre domaine ?
<a name="BKMK_Test"> </a>

Nous pouvons vous aider à identifier les problèmes liés à la configuration DNS de votre domaine. L'utilitaire de résolution des problèmes liés aux domaines dans Office 365 vous montre tous les enregistrements nécessitant une résolution et les valeurs devant être affectées aux enregistrements. 

> [!TIP]
> Votre DNS est correctement configuré, mais le courrier électronique ne fonctionne pas dans Outlook sur votre ordinateur de bureau ? Découvrez les [différents scénarios de flux de courrier que vous pouvez rencontrer dans Office 365](https://go.microsoft.com/fwlink/?LinkId=787530) pour confirmer que vous avez configuré correctement votre environnement au sein de votre entreprise. Vous pouvez également obtenir de l'aide concernant la résolution des problèmes liés à le courrier dans la page suivante : [Résoudre les problèmes liés à Outlook](https://support.office.com/article/b3e740b9-171d-4179-bcd1-e279a363fa75.aspx). 
  
## <a name="accessing-your-website-isnt-working"></a>Vous ne parvenez pas à accéder à votre site web ?
<a name="BKMK_Website"> </a>

Si vous avez corrigé tous les problèmes DNS et que vous rencontrez toujours des difficultés, essayez l'une des solutions suivantes.
  
- Les utilisateurs ne peuvent pas accéder à votre site web à l'adresse www.mondomaine.com : [Identifier les problèmes liés au site web](https://support.office.com/article/61f34ca1-ca7f-4a65-9348-def20db09ddf.aspx)
    
- Vous ne pouvez pas mettre à jour votre enregistrement A ou CNAME de façon à ce qu'il pointe vers votre site web : [Mettre à jour les enregistrements DNS personnalisés dans Office 365](../dns/add-or-edit-custom-dns-records.md)
    
