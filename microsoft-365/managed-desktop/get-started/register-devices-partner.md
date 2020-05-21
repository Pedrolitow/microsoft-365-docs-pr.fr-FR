---
title: Procédure permettant aux partenaires d’inscrire des appareils
description: Comment les partenaires peuvent enregistrer les appareils afin qu’ils puissent être gérés par le bureau géré Microsoft
ms.prod: w10
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: f1b1a8f03b7a11a0467826281bc2b789140dbcee
ms.sourcegitcommit: f6840dfcfdbcadc53cda591fd6cf9ddcb749d303
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44327055"
---
# <a name="steps-for-partners-to-register-devices"></a>Procédure permettant aux partenaires d’inscrire des appareils


Cette rubrique décrit les étapes à suivre par les partenaires pour inscrire des appareils. Le processus d’inscription des appareils vous-même est documenté dans [inscrire des appareils dans Microsoft Managed Desktop vous-même](register-devices-self.md).



## <a name="prepare-for-registration"></a>Préparer l’inscription 
Avant de terminer l’enregistrement d’un client, vous devez d’abord établir une relation avec ceux-ci dans le [Centre partenaires](https://partner.microsoft.com/dashboard). Pour plus d’informations sur ce processus, consultez la [documentation de consentement](https://docs.microsoft.com/windows/deployment/windows-autopilot/registration-auth#csp-authorization) . Tout partenaire CSP peut ajouter des appareils pour le compte de n’importe quel client, à condition que le client accepte. Vous pouvez également en savoir plus sur les relations avec les partenaires et les autorisations AutoPilot dans [l’aide du centre de partenaires](https://docs.microsoft.com/partner-center/customers_revoke_admin_privileges#windows-autopilot).


> [!NOTE]
> Cette documentation est uniquement destinée aux partenaires et aux OEM. Le processus d’auto-enregistrement est documenté dans [inscrire les appareils dans Microsoft Managed Desktop vous-même](register-devices-self.md).


## <a name="register-devices-by-using-partner-center"></a>Inscrire des appareils à l’aide du centre de partenaires

Une fois que vous avez établi la relation avec vos clients, vous pouvez utiliser le centre partenaires pour ajouter des appareils à AutoPilot pour tous les clients avec lesquels vous avez une relation en procédant comme suit :

1. Accéder au [Centre de partenaires](https://partner.microsoft.com/dashboard)
2. Sélectionnez **clients** dans le menu centre partenaire, puis sélectionnez le client dont vous souhaitez gérer les appareils.
3. Sur la page Détails du client, sélectionnez **appareils**.
4. Sous **appliquer des profils** aux appareils, sélectionnez **Ajouter des périphériques**.
5. Entrez **Microsoft365Managed_Autopilot** pour le nom du groupe, puis cliquez sur **Parcourir** pour télécharger la liste du client (au format de fichier. csv) vers le centre de partenaires.


> [!IMPORTANT]
> Le nom du groupe doit correspondre exactement à **Microsoft365Managed_Autopilot** , y compris les majuscules et les caractères spéciaux. Cela permettra aux nouveaux appareils enregistrés d’être affectés avec le profil AutoPilot de bureau géré Microsoft.

>[!NOTE]
> Vous devriez avoir reçu ce fichier. csv avec l’achat de votre appareil. Si vous n’avez pas reçu de fichier. csv, vous pouvez en créer un vous-même en suivant les étapes décrites dans la partie [Ajout de périphériques à Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell). Le script Windows PowerShell est différent de celui utilisé pour le [portail d’administration de bureau géré Microsoft](https://docs.microsoft.com/microsoft-365/managed-desktop/get-started/register-devices-self?view=o365-worldwide#obtain-the-hardware-hash). Les partenaires doivent utiliser [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour inscrire des appareils pour les appareils de bureau gérés Microsoft dans le centre de partenaires.

Si vous obtenez un message d’erreur lors d’une tentative de chargement du fichier. csv, vérifiez le format du fichier. Vous pouvez utiliser le hachage matériel uniquement, ou le nom du fabricant, le numéro de série et le modèle (dans l’ordre de cette colonne) ou l’ID de produit Windows. Vous pouvez également utiliser l’exemple de fichier. csv fourni par le lien en regard de **Ajouter des périphériques** pour créer une liste d’appareils. 

Pour plus d’informations sur le pilotage automatique dans les scénarios de partenaires, consultez la rubrique [Ajouter des périphériques au compte d’un client](https://docs.microsoft.com/partner-center/autopilot#add-devices-to-a-customers-account).


## <a name="register-devices-by-using-the-oem-api"></a>Inscrire des appareils à l’aide de l’API OEM

Avant de procéder à l’inscription d’un client, vous devez d’abord établir une relation avec ceux-ci. Vous devez disposer d’un lien unique à fournir à vos clients respectifs. Découvrez [Comment établir une relation OEM](https://docs.microsoft.com/windows/deployment/windows-autopilot/registration-auth#oem-authorization).

Une fois que vous avez établi la relation, vous pouvez commencer à inscrire des appareils pour les clients à l’aide de la balise Group **Microsoft365Managed_Autopilot**.

> [!IMPORTANT]
> Le nom du groupe doit correspondre exactement à **Microsoft365Managed_Autopilot** , y compris les majuscules et les caractères spéciaux. Cela permettra aux nouveaux appareils enregistrés d’être affectés avec le profil AutoPilot de bureau géré Microsoft.
