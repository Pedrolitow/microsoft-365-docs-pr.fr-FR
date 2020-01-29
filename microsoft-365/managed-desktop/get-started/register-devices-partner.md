---
title: Procédure permettant aux partenaires d’inscrire des appareils
description: Comment les partenaires peuvent enregistrer les appareils afin qu’ils puissent être gérés par le bureau géré Microsoft
ms.prod: w10
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: eb7ff76ef51078e423201b41cf24780b822ba452
ms.sourcegitcommit: 3f8957ddd04b8710bb5f314a0902fdee50c7c9b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "41572240"
---
# <a name="steps-for-partners-to-register-devices"></a>Procédure permettant aux partenaires d’inscrire des appareils


Cette rubrique décrit les étapes à suivre par les partenaires pour inscrire des appareils. Le processus d’inscription des appareils vous-même est documenté dans [inscrire des appareils dans Microsoft Managed Desktop vous-même](register-devices-self.md).



## <a name="prepare-for-registration"></a>Préparer l’inscription 
Avant de terminer l’enregistrement d’un client, vous devez d’abord établir une relation avec ceux-ci dans le [Centre partenaires](https://partner.microsoft.com/dashboard). Veillez à sélectionner **inclure les privilèges d’administration déléguée pour Azure Active Directory et Office 365**. Pour plus d’informations, consultez [l’aide du centre de partenaires](https://docs.microsoft.com/partner-center/request-a-relationship-with-a-customer).

Pour terminer l’inscription de votre client, commencez par créer un fichier CSV.

>[!NOTE]
>Pour des raisons de commodité, vous pouvez télécharger un [exemple de fichier CSV](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-started/downloads/device-registration-sample-self.csv) pour cette *version de partenaire*.

Votre fichier doit inclure exactement les **mêmes en-têtes de colonne** que l’exemple (fabricant, modèle, etc.), mais vos propres données pour les autres lignes. Si vous utilisez le modèle, ouvrez-le dans un outil d’édition de texte tel que le bloc-notes, et pensez à laisser toutes les données de la ligne 1 uniquement, en entrant uniquement les données dans les lignes 2 et ci-dessous. 
    
  ```
 Manufacturer,Model,Serial Number
  SpiralOrbit,ContosoABC,000000000000
  
  
  ```




>[!NOTE]
>Ce format est uniquement destiné au processus partenaire. Le processus d’auto-enregistrement est documenté dans [inscrire les appareils dans Microsoft Managed Desktop vous-même](register-devices-self.md).

>[!IMPORTANT]
>Ces valeurs doivent correspondre exactement aux valeurs du fabricant de SMBIOS, y compris les majuscules et les caractères spéciaux. 

- Fabricant de l’appareil (exemple : SpiralOrbit) 
- Modèle d’appareil (par exemple : ContosoABC)
- Numéro de série du périphérique

## <a name="register-devices-by-using-the-azure-portal"></a>Inscrire des appareils à l’aide du portail Azure

L’inscription à l’aide du portail Azure est identique à celle de self-service, sauf que vous accédez au portail différemment. Procédez comme suit :

1. Accéder au [Centre de partenaires](https://partner.microsoft.com/dashboard)
2. Sélectionnez **clients**.
3. Sélectionnez le client que vous souhaitez gérer.
4. Sélectionnez **administration du service**.
5. Sélectionnez **Intune**.
6. Recherchez « MMD » dans la zone de recherche située dans la partie supérieure du portail Azure.
7. Sélectionnez **appareils**.
8. Dans **chargement du fichier**, indiquez le chemin d’accès au fichier CSV que vous avez créé précédemment.
9. Si vous le souhaitez, vous pouvez ajouter un **ID de commande** ou un **ID d’achat** à vos fins de suivi. Il n’y a pas de mise en forme requise pour ces valeurs.
10. Sélectionnez **inscrire les appareils**. Le système ajoute les périphériques à votre liste d’appareils sur le panneau des **appareils**, marqué comme **inscription en attente**. L’inscription prend généralement moins de 10 minutes et, lorsque le périphérique s’affiche comme **prêt pour l’utilisateur** , ce qui signifie qu’il est prêt et qu’il attend qu’un utilisateur final commence à utiliser.


Vous pouvez surveiller la progression de l’inscription de l’appareil sur la page principale **des périphériques de bureau gérés par Microsoft** . Les États possibles sont les suivants :

| État | Description |
|---------------|-------------|
| Inscription en attente | L’inscription n’est pas encore terminée. Réactivez-vous plus tard. |
| Échec de l’inscription | L’inscription n’a pas pu aboutir. Pour plus d’informations, consultez la rubrique [Troubleshooting Device Registration](register-devices-self.md#troubleshooting-device-registration) . |
| Prêt pour l’utilisateur | L’inscription a réussi et l’appareil est maintenant prêt à être remis à l’utilisateur final. Microsoft Managed Desktop les guide tout au long du paramétrage, il n’est donc pas nécessaire d’effectuer d’autres préparatifs. |
| Actif | L’appareil a été remis à l’utilisateur final et il a été enregistré auprès de votre client. Cela indique également qu’ils utilisent régulièrement l’appareil. |
| Inactive | L’appareil a été remis à l’utilisateur final et il a été enregistré auprès de votre client. Toutefois, ils n’ont pas utilisé le périphérique récemment (au cours des 7 derniers jours).  |



## <a name="troubleshooting"></a>Résolution des problèmes

| Message d’erreur | Détails |
|---------------|-------------|
| Appareil introuvable | Nous n’avons pas pu inscrire cet appareil, car nous n’avons pas pu trouver de correspondance pour le fabricant, le modèle ou le numéro de série fourni. Vérifiez ces valeurs auprès de votre fournisseur d’appareils. |
| Hachage matériel non valide | Le hachage matériel que vous avez fourni pour cet appareil n’a pas été correctement mis en forme. Vérifiez le hachage matériel, puis renvoyez-le. |
| L’appareil est déjà enregistré | Ce périphérique est déjà enregistré dans votre organisation. Aucune autre action n’est requise. |
| Appareil revendiqué par une autre organisation | Ce périphérique a déjà été revendiqué par une autre organisation. Vérifiez auprès de votre fournisseur d’appareils. |
| Erreur inattendue | Votre demande n’a pas pu être traitée automatiquement. Contactez le support<support link>technique () et indiquez l’ID de la demande :<requestId> |
