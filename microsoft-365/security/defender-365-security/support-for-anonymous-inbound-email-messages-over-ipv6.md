---
title: Ajouter la prise en charge des e-mails entrants anonymes par IPv6
f1.keywords:
- NOCSH
author: chrisda
ms.author: chrisda
manager: chrisda
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: b68df621-0a5f-4824-8abc-41e0c4fd1398
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: L’administrateur peut apprendre à configurer la prise en charge du courrier entrant anonyme à partir de sources IPv6 dans Exchange Online et Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: df06891401802d212cbfdb55085662901f5546e9
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51061910"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>Ajouter la prise en charge du courrier entrant anonyme sur IPv6 dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les organisations Microsoft 365 avec boîtes aux lettres Exchange Online et les organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online peuvent prendre en charge le courrier entrant anonyme sur IPv6. Le serveur de messagerie IPv6 source doit répondre aux deux exigences suivantes :

- L’adresse IPv6 source doit avoir un enregistrement de recherche DNS inverse (PTR) valide qui permet à la destination de trouver le nom de domaine à partir de l’adresse IPv6.

- L'expéditeur doit répondre aux exigences de l'étape de vérification SPF (définie dans le fichier [RFC 7208](https://tools.ietf.org/html/rfc7208)) ou de l'étape de [vérification DKIM](http://dkim.org/) (définie dans le fichier [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

Avant que votre organisation puisse recevoir des messages entrants anonymes sur IPv6, un administrateur doit contacter le support Microsoft et le demander. Pour obtenir des instructions sur l’ouverture d’une demande de support, voir Contacter le support technique pour les [produits d’entreprise - Aide de l’administrateur.](../../admin/contact-support-for-business-products.md)

Une fois que la prise en charge des messages IPv6 entrants anonymes est activée dans votre organisation, le message passe par le filtrage des messages normal fourni par le service.

## <a name="troubleshooting"></a>Résolution des problèmes

- Si le serveur de messagerie source n’a pas d’enregistrement de recherche DNS inverse IPv6, les messages sont rejetés avec l’erreur suivante :

  > Service 450 4.7.25 indisponible, l’envoi de l’adresse IPv6 [2a01:111:f200:2004::240] doit avoir un enregistrement DNS inverse.

- Si l’expéditeur ne passe pas la validation SPF ou DKIM, les messages sont rejetés avec l’erreur suivante :

  > Service 450 4.7.26 indisponible, le message envoyé sur IPv6 [2a01:111:f200:2004::240] doit réussir la validation SPF ou DKIM.

- Si vous essayez de recevoir des messages IPv6 anonymes avant d’avoir choisi de le faire, le message sera rejeté avec l’erreur suivante :

  > Service 550 5.2.1 indisponible, [contoso.com] n’accepte pas le courrier électronique sur IPv6.

## <a name="related-topics"></a>Voir aussi

[Prise en charge de la validation des messages signés DKIM](support-for-validation-of-dkim-signed-messages.md)
