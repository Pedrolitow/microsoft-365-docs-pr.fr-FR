---
title: Créer des règles pour vos e-mails pour les rançongiciels
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
description: Découvrez comment créer des règles de messagerie pour empêcher les ransomware.
ms.openlocfilehash: 3dacaf51319f9a4b037d2e05c99ab9fa0e2e7e76807854c71997930e31193681
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53896546"
---
# <a name="create-email-rules-to-prevent-ransomware"></a>Créer des règles de messagerie pour empêcher les ransomware

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

Microsoft 365 protéger votre entreprise contre les ransomware en empêchant l’ouverture de fichiers potentiellement dangereux, tels que JavaScript, batch et executables, dans Outlook. Pour augmenter ce niveau de protection en ajoutant des règles qui bloquent ou vous avertissent de types de fichiers supplémentaires, suivez ces étapes.

## <a name="try-it"></a>Essayez !

1. Dans le Centre d’administration, choisissez [https://admin.microsoft.com](https://admin.microsoft.com) **Exchange** sous **Centres d’administration.**
1. Dans le menu de gauche, choisissez **flux de messagerie.**
1. Sous l’onglet Règles, sélectionnez la flèche en haut du symbole plus (+), puis choisissez Créer **une règle.**
1. Dans la **page nouvelle règle,** entrez un nom pour votre règle, faites défiler vers le bas, puis choisissez **Plus d’options.**
1. Sous **Appliquer cette règle si**, sélectionnez **n’importe** quelle pièce jointe, puis sélectionnez **l’extension** de fichier inclut ces mots .
1. Dans la zone sous spécifier des mots ou des **expressions,** entrez les extensions de fichier à appliquer à la règle, telles que les extensions de fichier qui peuvent contenir des macros. Utilisez le symbole plus (+) pour les ajouter un par un.

    En savoir plus sur les types de fichiers en lisant [Protéger contre les ransomware.](../admin/security-and-compliance/secure-your-business-data.md#ransomware)

1. Faites défiler vers le bas pour passer en revue votre liste, puis choisissez **OK.**
1. Dans la **page nouvelle règle,** choisissez **ajouter une condition,** puis choisissez une condition sous **Faire ce qui suit**.
1. Vous avez le choix entre de nombreuses options de règle, mais dans cet exemple, nous allons choisir d’avertir le destinataire **avec un message**.
1. Entrez le texte du message pour votre notification, puis choisissez **OK**.
1. Facultatif : sur **la** page nouvelle règle, choisissez ajouter une **exception,** puis entrez les détails des exceptions à votre règle, telles que les messages provenant d’expéditeurs fiables.
1. Dans la page nouvelle règle, **sélectionnez Enregistrer** et examinez les informations récapitulatifs de règle fournies.