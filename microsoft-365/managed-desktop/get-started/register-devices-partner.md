---
title: Procédure permettant aux partenaires d’inscrire des appareils
description: Comment les partenaires peuvent inscrire des appareils afin qu’ils soient gérés par Bureau géré Microsoft
ms.prod: w10
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: be314b20573cecfdb020caf778e51a684a9b6df8
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50909069"
---
# <a name="steps-for-partners-to-register-devices"></a>Procédure permettant aux partenaires d’inscrire des appareils


Cette rubrique décrit les étapes que les partenaires doivent suivre pour inscrire des appareils. Le processus d’inscription des appareils vous-même est documenté dans Enregistrer vous-même les appareils [dans Le Bureau géré Microsoft.](register-devices-self.md)



## <a name="prepare-for-registration"></a>Préparer l’inscription 
Avant d’achever l’inscription d’un client, vous devez d’abord établir une relation avec lui dans [l’Partner Center](https://partner.microsoft.com/dashboard). Pour plus [d’informations](/windows/deployment/windows-autopilot/registration-auth#csp-authorization) sur ce processus, voir la documentation relative au consentement. Tout partenaire CSP peut ajouter des appareils pour le compte de n’importe quel client, tant que le client y consent. Vous pouvez également en savoir plus sur les relations de partenariat et les autorisations Autopilot dans l’aide [de l’Centre partenaires.](/partner-center/customers_revoke_admin_privileges#windows-autopilot)


> [!NOTE]
> Cette documentation est uniquement pour les partenaires et les fabricants OEM. Le processus d’auto-inscription est documenté dans Enregistrer vous-même les appareils [dans Le Bureau géré Microsoft.](register-devices-self.md)


## <a name="register-devices-by-using-partner-center"></a>Inscrire des appareils à l’aide de l’Partner Center

Une fois que vous avez établi la relation avec vos clients, vous pouvez tirer parti de l’Partner Center pour ajouter des appareils à Autopilot pour tous les clients avec qui vous avez une relation en suivant les étapes suivantes :

1. Accéder à [l’Partner Center](https://partner.microsoft.com/dashboard)
2. Sélectionnez **Clients** dans le menu De l’Centre partenaires, puis sélectionnez le client dont vous souhaitez gérer les appareils.
3. Dans la page de détails du client, sélectionnez **Appareils.**
4. Sous **Appliquer des profils** aux appareils, **sélectionnez Ajouter des appareils.**
5. Entrez **Microsoft365Managed_Autopilot** le nom du groupe,  puis sélectionnez Parcourir pour télécharger la liste du client (au format de fichier .csv) dans l’Partner Center.


> [!IMPORTANT]
> Le nom du groupe doit correspondre **Microsoft365Managed_Autopilot** exactement, y compris les majuscules et les caractères spéciaux. Cela permettra aux appareils nouvellement inscrits d’être affectés avec le profil Microsoft Managed Desktop Autopilot.

>[!NOTE]
> Vous devriez avoir reçu ce fichier .csv avec l’achat de votre appareil. Si vous n’avez pas reçu de fichier .csv, vous pouvez en créer un vous-même en suivant les étapes de l’ajout d’appareils à [Windows Autopilot.](/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell) Le script Windows PowerShell est différent de celui utilisé pour le portail d’administration du bureau géré [Microsoft.](./register-devices-self.md?view=o365-worldwide#obtain-the-hardware-hash) Les partenaires doivent utiliser [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour inscrire des appareils pour les appareils bureau géré Microsoft dans l’Partner Center.

Si vous obtenez un message d’erreur lors de la tentative de téléchargement du fichier .csv, vérifiez le format du fichier. Assurez-vous que l’ordre des colonnes correspond à ce qui est décrit dans Utiliser les profils Windows Autopilot sur les nouveaux appareils pour personnaliser [l’expérience pré-encadrée d’un client.](/partner-center/autopilot#add-devices-to-a-customers-account) Vous pouvez également utiliser l’exemple de fichier .csv fourni à partir du lien en dessous d’Ajouter des appareils **pour** créer une liste d’appareils. 

Pour plus d’informations sur Autopilot dans les scénarios partenaires, voir Ajouter des [appareils au compte d’un client.](/partner-center/autopilot#add-devices-to-a-customers-account)


## <a name="register-devices-by-using-the-oem-api"></a>Inscrire des appareils à l’aide de l’API OEM

Avant d’achever l’inscription d’un client, vous devez d’abord établir une relation avec lui. Vous devez avoir un lien unique à fournir à vos clients respectifs. Découvrez [comment établir une relation OEM.](/windows/deployment/windows-autopilot/registration-auth#oem-authorization)

Une fois la relation établie, vous pouvez commencer à inscrire des appareils pour les clients à l’aide de la balise **de groupe Microsoft365Managed_Autopilot**.

> [!IMPORTANT]
> Le nom du groupe doit correspondre **Microsoft365Managed_Autopilot** exactement, y compris les majuscules et les caractères spéciaux. Cela permettra aux appareils nouvellement inscrits d’être affectés avec le profil Microsoft Managed Desktop Autopilot.