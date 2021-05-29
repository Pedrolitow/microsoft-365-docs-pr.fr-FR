---
title: Ajouter un domaine
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
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Votre organisation peut avoir besoin de plusieurs domaines pour que les clients vous trouvent. Découvrez comment ajouter un autre domaine à votre abonnement.
ms.openlocfilehash: 13fc3cf73a112945db4372231cce70c1837c1321
ms.sourcegitcommit: a05f61a291eb4595fa9313757a3815b7f217681d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "52706429"
---
# <a name="add-another-domain"></a>Ajouter un autre domaine

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Votre entreprise peut avoir besoin de plusieurs noms de domaine à des fins différentes. Par exemple, vous souhaitez peut-être ajouter une orthographe différente du nom de votre société, car les clients l’utilisent déjà et leurs communications n’ont pas pu vous joindre.

## <a name="try-it"></a>Essayez !

1. In the Microsoft 365 admin center, choose **Setup**.
1. Sous **Obtenir votre domaine personnalisé, sélectionnez** **Afficher.**
1. Sélectionnez **Gérer,** puis **Ajouter un domaine.**
1. Entrez le nouveau nom de domaine à ajouter, puis sélectionnez **Suivant.**
1. Connectez-vous à votre bureau d’enregistrement de domaines, dans ce cas GoDaddy, puis sélectionnez **Suivant**.
1. Si vous y êtes invité, connectez-vous à votre bureau d’enregistrement, puis choisissez **Autoriser.**
1. Sélectionnez **Ajouter les enregistrements DNS** pour moi, puis sélectionnez **Suivant.**
1. Choisissez les services pour votre nouveau domaine et cochez les cases pour tous les services qui seront gérés par un autre domaine. Par exemple, si vous souhaitez simplement utiliser le nouveau domaine pour la messagerie, choisissez **Exchange** et cochez les cases pour Skype Entreprise **et** **Gestion des périphériques mobiles pour Office 365**.
1. Sélectionnez **Suivant**, **Autoriser**, **Suivant,** puis **Terminer**. Votre nouveau domaine a été ajouté.

Pour recevoir des messages électroniques sur votre nouveau domaine, vous devez ajouter un nouvel alias de messagerie pour chaque utilisateur :

1. Sélectionnez **Utilisateurs,** **Utilisateurs** actifs, puis sélectionnez l’utilisateur qui se voit attribuer le nouvel alias.
1. Choisissez **Gérer les alias de messagerie,** puis **ajoutez un alias.**
1. Entrez le nom d’utilisateur, puis choisissez le nouveau domaine dans la liste liste.
1. Sélectionnez **Enregistrer les modifications,** puis fermez la fenêtre.
1. Répétez ces étapes pour chaque utilisateur qui doit recevoir des messages électroniques sur le nouveau domaine.

## <a name="related-content"></a>Contenu associé

[Ajouter un domaine à Microsoft 365](../admin/setup/add-domain.md) (article)\
[Ajouter des enregistrements DNS pour connecter votre domaine](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (article)\
[Modifier les serveurs de noms de manière à configurer Microsoft 365 avec n'importe quel bureau d'enregistrement de domaines](../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (article)\
[FAQ sur les domaines](../admin/setup/domains-faq.yml) (article)