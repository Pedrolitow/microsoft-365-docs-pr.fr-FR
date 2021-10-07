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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- AdminTemplateSet
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Votre organisation peut avoir besoin de plusieurs domaines pour que les clients vous trouvent. Découvrez comment ajouter un autre domaine à votre abonnement.
ms.openlocfilehash: 6e994bfdb50995d9a75c36eb831e35daf58561d4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60153665"
---
# <a name="add-another-domain"></a>Ajouter un autre domaine

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Votre entreprise peut avoir besoin de plusieurs noms de domaine à des fins différentes. Par exemple, vous pouvez ajouter une orthographe différente du nom de votre société, car les clients l’utilisent déjà et leurs communications n’ont pas pu vous joindre.

## <a name="try-it"></a>Essayez !

1. In the Centre d'administration Microsoft 365, choose <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Setup**</a>.
1. Sous **Obtenir votre domaine personnalisé, sélectionnez** **Afficher.**
1. Sélectionnez **Gérer,** puis **Ajouter un domaine.**
1. Entrez le nouveau nom de domaine à ajouter, puis sélectionnez **Suivant.**
1. Connectez-vous à votre bureau d’enregistrement de domaines, dans ce cas GoDaddy, puis sélectionnez **Suivant**.
1. Si vous y êtes invité, connectez-vous à votre bureau d’enregistrement, puis choisissez **Autoriser.**
1. Sélectionnez **Ajouter les enregistrements DNS** pour moi, puis sélectionnez **Suivant.**
1. Choisissez les services pour votre nouveau domaine et cochez les cases pour tous les services qui seront gérés par un autre domaine. Par exemple, si vous souhaitez simplement utiliser le nouveau domaine pour la messagerie, choisissez **Exchange** et cochez les cases pour Skype Entreprise **et** **Gestion des périphériques mobiles pour Office 365**.
1. Sélectionnez **Suivant**, **Autoriser**, **Suivant,** puis **Terminer**. Votre nouveau domaine a été ajouté.

Pour recevoir des messages électroniques sur votre nouveau domaine, vous devez ajouter un nouvel alias de messagerie pour chaque utilisateur :

1. Sélectionnez **Utilisateurs,** <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Utilisateurs**</a>actifs, puis sélectionnez l’utilisateur qui se voit attribuer le nouvel alias.
1. Choisissez **Gérer les alias de messagerie,** puis **ajoutez un alias.**
1. Entrez le nom d’utilisateur, puis choisissez le nouveau domaine dans la liste liste.
1. Sélectionnez **Enregistrer les modifications,** puis fermez la fenêtre.
1. Répétez ces étapes pour chaque utilisateur qui doit recevoir des messages électroniques sur le nouveau domaine.

## <a name="related-content"></a>Contenu associé

[Ajouter un domaine à Microsoft 365](../admin/setup/add-domain.md) (article)\
[Ajouter des enregistrements DNS pour connecter votre domaine](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (article)\
[Modifier les serveurs de noms de manière à configurer Microsoft 365 avec n'importe quel bureau d'enregistrement de domaines](../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (article)\
[FAQ sur les domaines](../admin/setup/domains-faq.yml) (article)