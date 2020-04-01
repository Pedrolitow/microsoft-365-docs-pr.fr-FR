---
title: Ajouter la prise en charge du courrier électronique entrant anonyme sur IPv6
f1.keywords:
- NOCSH
author: chrisda
ms.author: chrisda
manager: chrisda
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: b68df621-0a5f-4824-8abc-41e0c4fd1398
ms.collection:
- M365-security-compliance
description: L’administrateur peut apprendre à configurer la prise en charge des messages électroniques entrants anonymes provenant de sources IPv6 dans Exchange Online et Exchange Online Protection.
ms.openlocfilehash: 67e839249d41381be22bbccf6b09d1616c387c66
ms.sourcegitcommit: 748bc3484b7ccbd65b558f495b6fa42196c3c571
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "43083640"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-office-365"></a>Ajouter la prise en charge du courrier électronique entrant anonyme sur IPv6 dans Office 365

Les organisations Office 365 avec des boîtes aux lettres Exchange Online et les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online prennent en charge les messages électroniques entrants anonymes sur IPv6. Le serveur de messagerie IPv6 source doit respecter les deux conditions suivantes :

- L’adresse IPv6 source doit avoir un enregistrement DNS de recherche inversée (PTR) valide qui permet à la destination de trouver le nom de domaine à partir de l’adresse IPv6.

- L'expéditeur doit répondre aux exigences de l'étape de vérification SPF (définie dans le fichier [RFC 7208](https://tools.ietf.org/html/rfc7208)) ou de l'étape de [vérification DKIM](https://dkim.org/) (définie dans le fichier [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

Pour que votre organisation puisse recevoir des messages électroniques entrants anonymes sur IPv6, un administrateur doit contacter le support Microsoft et lui demander :

1. Ouvrez le centre d’administration Microsoft 365 <https://admin.microsoft.com/adminportal/home> à l’adresse, puis cliquez sur **aide** ( ?).

2. Dans le menu déroulant **besoin d’aide ?** qui s’affiche, tapez un texte descriptif dans la zone de recherche (par exemple, « demander un message électronique IPv6 entrant anonyme »), puis appuyez sur entrée.

3. Au bas de la page, cliquez sur **contacter le support technique**.

4. Sur la page **contacter le support technique** qui apparaît, renseignez et vérifiez les informations (faites défiler l’affichage si nécessaire), puis cliquez sur **me contacter**.

Une fois que la prise en charge des messages IPv6 entrants anonymes est activée dans votre organisation, le message passe par le filtre de messages normal fourni par le service.

## <a name="troubleshooting"></a>Résolution des problèmes

- Si le serveur de messagerie source ne dispose pas d’un enregistrement de recherche DNS inversée IPv6, les messages seront rejetés avec l’erreur suivante :

  > 450 4.7.25 Service indisponible, envoi de l’adresse IPv6 [2a01:111 : F200:2004 :: 240] doit avoir un enregistrement DNS inverse.

- Si l’expéditeur ne passe pas la validation SPF ou DKIM, les messages sont rejetés avec l’erreur suivante :

  > 450 4.7.26 Service indisponible, le message envoyé via IPv6 [2a01:111 : F200:2004 :: 240] doit transmettre la validation SPF ou DKIM.

- Si vous tentez de recevoir des messages IPv6 anonymes avant d’avoir choisi, le message sera rejeté avec l’erreur suivante :

  > 550 5.2.1 Service indisponible, [contoso.com] n’accepte pas le courrier électronique sur IPv6.

## <a name="for-more-information"></a>Pour plus d'informations

[Prise en charge de la validation des messages signés DKIM](support-for-validation-of-dkim-signed-messages.md)
