---
title: Inscrire des appareils dans le bureau géré Microsoft pour les partenaires
description: Comment les partenaires peuvent enregistrer les appareils afin qu'ils puissent être gérés par le bureau géré Microsoft
ms.prod: w10
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: 23a2eae6435f5ce234cf6406f2753ec54f675bce
ms.sourcegitcommit: 7af6350fb5a6d37934c1b6bfdc38acd09b2d5d86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "31988420"
---
# <a name="register-devices-in-microsoft-managed-desktop-for-partners"></a>Inscrire des appareils dans le bureau géré Microsoft pour les partenaires


Cette rubrique décrit les étapes à suivre par les partenaires pour inscrire des appareils. Le processus d'inscription des appareils vous-même est documenté dans [inscrire des appareils dans Microsoft Managed Desktop vous-même](register-devices-self.md).



## <a name="prepare-for-registration"></a>Préparer l'inscription 
Avant de terminer l'enregistrement d'un client, vous devez d'abord établir une relation avec ceux-ci dans le [Centre partenaires](https://partner.microsoft.com/dashboard). Pour plus d'informations, consultez [l'aide du centre de partenaires](https://docs.microsoft.com/en-us/partner-center/request-a-relationship-with-a-customer).

Pour terminer l'inscription de votre client, commencez par créer un fichier CSV.

>[!NOTE]
>Pour des raisons de commodité, vous pouvez télécharger un [modèle](https://github.com/MicrosoftDocs/microsoft-365-docs-pr/raw/live/microsoft-365/managed-desktop/get-started/downloads/device-registration-sample-partner.xlsx) pour cette *version de partenaire* du fichier CSV.

Votre fichier doit inclure exactement les **mêmes en-têtes de colonne** que l'exemple (fabricant, modèle, etc.), mais vos propres données pour les autres lignes. Si vous utilisez le modèle, ouvrez-le dans un outil d'édition de texte tel que le bloc-notes, et pensez à laisser toutes les données de la ligne 1 uniquement, en entrant uniquement les données dans les lignes 2 et ci-dessous. 
    
  ```
 Manufacturer,Model,Serial Number,Hardware Hash
  SpiralOrbit,ContosoABC,000000000000,
  
  
  ```


>[!NOTE]
>Ce format est uniquement destiné au processus partenaire. Le processus d'auto-enregistrement est documenté dans [inscrire les appareils dans Microsoft Managed Desktop vous-même](register-devices-self.md).

>[!IMPORTANT]
>Ces valeurs doivent correspondre exactement aux valeurs du fabricant de SMBIOS. Vous devez également inclure le *hachage matériel* dans la première ligne (mais pas sa valeur sur la deuxième ligne) après la virgule de fin après la valeur de *numéro de série* dans la deuxième ligne.

- Fabricant de l'appareil (exemple: SpiralOrbit) 
- Modèle d'appareil (par exemple: ContosoABC)
- Numéro de série du périphérique

## <a name="register-devices-by-using-the-azure-portal"></a>Inscrire des appareils à l'aide du portail Azure

L'inscription à l'aide du portail Azure est identique à celle de self-service, sauf que vous accédez au portail différemment. Procédez comme suit :

1. Accéder au [Centre de partenaires](https://partner.microsoft.com/dashboard)
2. Sélectionnez **clients**.
3. Sélectionnez le client que vous souhaitez gérer.
4. Sélectionnez **administration du service**.
5. Sélectionnez **Intune**.
6. Recherchez «MMD» dans la zone de recherche située dans la partie supérieure du portail Azure.
7. Sélectionnez **appareils**.
8. Dans **chargement du fichier**, indiquez le chemin d'accès au fichier CSV que vous avez créé précédemment.
9. Si vous le souhaitez, vous pouvez ajouter un **ID de commande** ou un **ID d'achat** à vos fins de suivi. Il n'y a pas de mise en forme requise pour ces valeurs.
10. Sélectionnez **inscrire les appareils**. Le système ajoute les périphériques à votre liste d'appareils sur le panneau des **appareils**, marqué comme **inscription en attente**. L'inscription prend généralement moins de 10 minutes et, lorsque le périphérique s'affiche comme **prêt pour l'utilisateur** , ce qui signifie qu'il est prêt et qu'il attend qu'un utilisateur final commence à utiliser.


Vous pouvez surveiller la progression de l'inscription de l'appareil sur la page principale **des périphériques de bureau gérés par Microsoft** . Les États possibles sont les suivants:

| État | Description |
|---------------|-------------|
| Inscription en attente | L'inscription n'est pas encore terminée. RéActivez-vous plus tard. |
| Échec de l'inscription | L'inscription n'a pas pu aboutir. Pour plus [](register-devices-self.md#troubleshooting) d'informations, rePortez-vous à la rubrique Troubleshooting. |
| Prêt pour l'utilisateur | L'inscription a réussi et l'appareil est maintenant prêt à être remis à l'utilisateur final. Microsoft maNaged Desktop les guide tout au long du paramétrage, il n'est donc pas nécessaire d'effectuer d'autres préparatifs. |
| Actif | L'appareil a été remis à l'utilisateur final et il a été enregistré auprès de votre client. Cela indique également qu'ils utilisent régulièrement l'appareil. |
| Inactive | L'appareil a été remis à l'utilisateur final et il a été enregistré auprès de votre client. Toutefois, ils n'ont pas utilisé le périphérique récemment (au cours des 7 derniers jours).  |

## <a name="register-devices-by-using-an-api"></a>Inscrire des appareils à l'aide d'une API

L'inscription par API est identique à self-service, mais la propriété de hachage de matériel de la collection de périphériques est facultative, comme décrit dans la section CSV. 

## <a name="troubleshooting"></a>Résolution des problèmes

| Message d’erreur | Détails |
|---------------|-------------|
| Appareil introuvable | Nous n'avons pas pu inscrire cet appareil, car nous n'avons pas pu trouver de correspondance pour le fabricant, le modèle ou le numéro de série fourni. Vérifiez ces valeurs auprès de votre fournisseur d'appareils. |
| Appareil introuvable | Nous n'avons pas pu enregistrer cet appareil, car il n'existe pas dans votre organisation. Aucune autre action n'est requise. |
| Hachage matériel non valide | Le hachage matériel que vous avez fourni pour cet appareil n'a pas été correctement mis en forme. Vérifiez le hachage matériel, puis renvoyez-le. |
| L'appareil est déjà enregistré | Ce périphérique est déjà enregistré dans votre organisation. Aucune autre action n'est requise. |
| Appareil revendiqué par une autre organisation | Ce périphérique a déjà été revendiqué par une autre organisation. Vérifiez auprès de votre fournisseur d'appareils. |
| Erreur inattendue | Votre demande n'a pas pu être traitée automatiquement. Contactez le support<support link>technique () et indiquez l'ID de la demande:<requestId> |