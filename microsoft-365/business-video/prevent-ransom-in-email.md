---
title: Créer des règles de messagerie pour les ransomware
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
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
description: Découvrez comment créer des règles de messagerie électronique pour empêcher les ransomware.
ms.openlocfilehash: 85898480438225848fc09db9a9c507045f8a182c
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49701934"
---
# <a name="create-email-rules-to-prevent-ransomware"></a>Créer des règles de messagerie pour empêcher les ransomware

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

Microsoft 365 vous aide à protéger votre entreprise contre les ransomware en empêchant l’ouverture de fichiers potentiellement dangereux, tels que JavaScript, batch et exécutables dans Outlook. Pour augmenter ce niveau de protection en ajoutant des règles qui bloquent ou vous avertissent de types de fichiers supplémentaires, procédez comme suit.

## <a name="try-it"></a>Essayez !

1. Dans le centre d’administration [https://admin.microsoft.com](https://admin.microsoft.com) , sélectionnez **Exchange** sous **centres d’administration**.
1. Dans le menu de gauche, sélectionnez **flux de messagerie**.
1. Dans l’onglet Règles, cliquez sur la flèche en regard du symbole plus (+), puis choisissez **créer une nouvelle règle**.
1. Sur la page **nouvelle règle** , entrez un nom pour votre règle, faites défiler vers le bas, puis choisissez **autres options**.
1. Sous **appliquer cette règle si**, sélectionnez **une pièce jointe**, puis sélectionnez l' **extension de fichier inclut ces mots**.
1. Dans la zone sous **spécifier des mots ou des expressions**, entrez les extensions de fichier auxquelles vous voulez appliquer la règle, par exemple les extensions de fichier pouvant contenir des macros. Utilisez le symbole plus (+) pour les ajouter un par un.

    Pour plus d’informations sur les types de fichiers, consultez la rubrique [protection contre les ransomware](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/secure-your-business-data#ransomware).

1. Faites défiler vers le bas pour examiner votre liste, puis cliquez sur **OK**.
1. Sur la page **nouvelle règle** , choisissez **Ajouter une condition**, puis choisissez une condition sous **effectuer les opérations suivantes**.
1. Vous pouvez choisir parmi plusieurs options de règle, mais dans cet exemple, nous allons choisir d' **informer le destinataire avec un message**.
1. Entrez le texte du message pour votre notification, puis choisissez **OK**.
1. Facultatif : sur la page **nouvelle règle** , choisissez **Ajouter une exception**, puis entrez les détails des exceptions à votre règle, par exemple les messages provenant d’expéditeurs approuvés.
1. Sur la page nouvelle règle, sélectionnez **Enregistrer**, puis passez en revue les informations de résumé de la règle fournies.