---
title: Inscrire vous-même les appareils dans le bureau géré Microsoft
description: Inscrire des appareils vous-même afin qu'ils puissent être gérés par le bureau géré Microsoft
ms.prod: w10
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: 02b3b7ab32ff92304ab27ca8e8c805ade803c971
ms.sourcegitcommit: cf77e4bf69e6ae144563f1e764ea3437ed6fc836
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2019
ms.locfileid: "33296164"
---
# <a name="register-devices-in-microsoft-managed-desktop"></a>Inscrire des appareils dans le bureau géré Microsoft

>[!NOTE]
>Cette rubrique décrit la procédure à suivre pour enregistrer des appareils de manière autonome. Le processus pour les partenaires est documenté dans [inscrire les appareils dans Microsoft Managed Desktop pour les partenaires](register-devices-partner.md).

Microsoft maNaged Desktop peut fonctionner avec les nouveaux appareils ou vous pouvez réutiliser des appareils que vous avez peut-être déjà (ce qui vous obligera à les réimager). Vous pouvez enregistrer des appareils à l'aide de Microsoft maNaged Desktop sur le portail Azure ou gagner en flexibilité à l'aide d'une API.

## <a name="prepare-to-register-devices"></a>Préparer l'inscription des appareils

Si vous n'avez pas encore obtenu les appareils que vous souhaitez utiliser, vérifiez [Microsoft Managed Desktop](../service-description/device-list.md) Devices et travaillez avec un partenaire d'appareil pour obtenir des appareils pris en charge.

Que vous travailliez avec des périphériques entièrement nouveaux ou que vous réutilisiez des appareils existants, pour les enregistrer auprès du bureau géré Microsoft, vous devez préparer un **fichier CSV**. Ce fichier doit inclure les informations suivantes pour chaque périphérique:

>[!NOTE]
>Ce format est réservé à l'enregistrement en libre-service. Le format que les partenaires doivent utiliser est documenté dans [inscrire les appareils dans le bureau géré Microsoft pour les partenaires](register-devices-partner.md).

Ces valeurs sont utilisées à des fins d'affichage et n'ont pas besoin de faire correspondre exactement les propriétés de l'appareil.
- Fabricant de l'appareil (exemple: SpiralOrbit) 
- Modèle d'appareil (par exemple: ContosoABC)
- Numéro de série du périphérique

La hachage du matériel doit être une correspondance exacte.
- Hachage matériel

Pour obtenir le hachage du matériel, vous pouvez demander de l'aide auprès de votre OEM ou de votre partenaire, ou suivez ces étapes pour chaque appareil:

1.  Ouvrez une invite PowerShell avec des droits d'administration.
2.  Générer`Install-Script -Name Get-WindowsAutoPilotInfo`
3.  Générer`powershell -ExecutionPolicy Unrestricted Get-WindowsAutopilotInfo -OutputFile <path>\hardwarehash.csv`


Vous pouvez également suivre ces étapes sur un nouveau périphérique (avant de passer par OOBE pour la première fois):

1. Sur un autre appareil, insérez un lecteur USB.
2. Ouvrez une invite PowerShell avec des droits d'administration.
3. Générer`Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`
4. Activez l'appareil cible, mais ne démarrez pas l'installation. Si vous démarrez accidentellement le programme d'installation, vous devrez réinitialiser ou recréer l'image de l'appareil.
5. Insérez le lecteur USB, puis appuyez sur MAJ + F10.
6. Ouvrez une invite PowerShell avec des droits d'administration, puis `cd <pathToUsb>`exécutez.
7. Générer`Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. Générer`.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
3. Supprimez le lecteur USB, puis arrêtez l'appareil en exécutant`shutdown -s -t 0`

>[!IMPORTANT]
>Ne mettez pas sous tension le périphérique cible tant que vous n'avez pas terminé son inscription. 

>[!NOTE]
>Pour des raisons de commodité, vous pouvez télécharger un [modèle](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-started/downloads/device-registration-sample-partner.xlsx) pour ce fichier CSV.

Votre fichier doit inclure exactement les **mêmes en-têtes de colonne** que l'exemple (fabricant, modèle, etc.), mais vos propres données pour les autres lignes. Si vous utilisez le modèle, ouvrez-le dans un outil d'édition de texte tel que le bloc-notes, et pensez à laisser toutes les données de la ligne 1 uniquement, en entrant uniquement les données dans les lignes 2 et ci-dessous. 
    
  ```
 Manufacturer,Model,Serial Number,Hardware Hash
  SpiralOrbit,ContosoABC,000000000000,dGhpc2RldmljZWlzYW5tbWRkZXZpY2U
  
  
  ```

>[!NOTE]
>Si vous oubliez de modifier l'un des exemples de données, l'inscription échouera.   


## <a name="register-devices-by-using-the-azure-portal"></a>Inscrire des appareils à l'aide du portail Azure

Dans le portail Microsoft maNaged Desktop [Azure](https://aka.ms/mmdportal), sélectionnez **périphériques** dans le volet de navigation de gauche. Sélectionnez **+ inscrire les appareils**; le survol s'ouvre:

[![Entrée brusque après la sélection d'appareils de Registre](images/register-devices-flyin-sterile.png)](images/register-devices-flyin-sterile.png)


[//]: # (Malheureusement, cela n'est pas vrai. Nous pouvons supprimer cette note, mais la laisser maintenant jusqu'à ce que nous ayons la possibilité de discuter.)

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->


Procédez comme suit :

1. Dans **chargement du fichier**, indiquez le chemin d'accès au fichier CSV que vous avez créé précédemment.
2. Si vous le souhaitez, vous pouvez ajouter un **ID de commande** ou un **ID d'achat** à vos fins de suivi. Il n'y a pas de mise en forme requise pour ces valeurs.
3. Sélectionnez **inscrire les appareils**. Le système ajoute les périphériques à votre liste d'appareils sur le panneau des **appareils**, marqué comme **inscription en attente**. L'inscription prend généralement moins de 10 minutes et, lorsque le périphérique s'affiche comme **prêt pour l'utilisateur** , ce qui signifie qu'il est prêt et qu'il attend qu'un utilisateur final commence à utiliser.


Vous pouvez surveiller la progression de l'inscription de l'appareil sur la page principale **des périphériques de bureau gérés par Microsoft** . Les États possibles sont les suivants:

| État | Description |
|---------------|-------------|
| Inscription en attente | L'inscription n'est pas encore terminée. RéActivez-vous plus tard. |
| Échec de l'inscription | L'inscription n'a pas pu aboutir. Pour plus [](register-devices-self.md#troubleshooting) d'informations, rePortez-vous à la rubrique Troubleshooting. |
| Prêt pour l'utilisateur | L'inscription a réussi et l'appareil est maintenant prêt à être remis à l'utilisateur final. Microsoft maNaged Desktop les guide tout au long du paramétrage, il n'est donc pas nécessaire d'effectuer d'autres préparatifs. |
| Actif | L'appareil a été remis à l'utilisateur final et il a été enregistré auprès de votre client. Cela indique également qu'ils utilisent régulièrement l'appareil. |
| Inactive | L'appareil a été remis à l'utilisateur final et il a été enregistré auprès de votre client. Toutefois, ils n'ont pas utilisé le périphérique récemment (au cours des 7 derniers jours).  | 


## <a name="register-devices-by-using-an-api"></a>Inscrire des appareils à l'aide d'une API

Une API REST est disponible pour vous permettre de bénéficier d'une plus grande flexibilité et d'une répétabilité avec des enregistrements de périphérique fréquemment séparés. Actuellement, pour utiliser l'API, demandez de l'aide auprès de votre contact Microsoft pour rejoindre un aperçu de cette fonctionnalité.



## <a name="troubleshooting"></a>Résolution des problèmes

| Message d’erreur | Détails |
|---------------|-------------|
| Appareil introuvable | Nous n'avons pas pu inscrire cet appareil, car nous n'avons pas pu trouver de correspondance pour le fabricant, le modèle ou le numéro de série fourni. Vérifiez ces valeurs auprès de votre fournisseur d'appareils. |
| Appareil introuvable | Nous n'avons pas pu enregistrer cet appareil, car il n'existe pas dans votre organisation. Aucune autre action n'est requise. |
| Hachage matériel non valide | Le hachage matériel que vous avez fourni pour cet appareil n'a pas été correctement mis en forme. Vérifiez le hachage matériel, puis renvoyez-le. |
| L'appareil est déjà enregistré | Ce périphérique est déjà enregistré dans votre organisation. Aucune autre action n'est requise. |
| Appareil revendiqué par une autre organisation | Ce périphérique a déjà été revendiqué par une autre organisation. Vérifiez auprès de votre fournisseur d'appareils. |
| Erreur inattendue | Votre demande n'a pas pu être traitée automatiquement. Contactez le support technique et indiquez l'ID de la demande:<requestId> |




