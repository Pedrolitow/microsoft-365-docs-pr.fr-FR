---
title: Procédure permettant aux partenaires d’inscrire des appareils
description: Comment les partenaires peuvent inscrire des appareils afin qu’ils soient gérés par Microsoft Manged Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: da55965a95251319467f86caebeb8909bb8585a0
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2022
ms.locfileid: "62035653"
---
# <a name="steps-for-partners-to-register-devices"></a>Procédure permettant aux partenaires d’inscrire des appareils


Cet article décrit les étapes que les partenaires doivent suivre pour inscrire des appareils. Le processus d’inscription des appareils vous-même est documenté dans Enregistrer les appareils [Microsoft Manged Desktop vous-même.](register-devices-self.md)



## <a name="prepare-for-registration"></a>Préparer l’inscription 
Avant d’achever l’inscription d’un client, vous devez d’abord établir une relation avec lui dans [l’Partner Center](https://partner.microsoft.com/dashboard). Pour plus [d’informations](/windows/deployment/windows-autopilot/registration-auth#csp-authorization) sur ce processus, voir la documentation relative au consentement. N’importe quel partenaire CSP peut ajouter des appareils au nom de n’importe quel client, tant que le client y consent. Vous pouvez également en savoir plus sur les relations de partenariat et les autorisations Autopilot dans l’aide [de l’Centre partenaires.](/partner-center/customers_revoke_admin_privileges#windows-autopilot)


> [!NOTE]
> Cette documentation est uniquement pour les partenaires et les fabricants OEM. Le processus d’auto-inscription est documenté dans Enregistrer les appareils [Microsoft Manged Desktop vous-même.](register-devices-self.md)


## <a name="register-devices-by-using-partner-center"></a>Inscrire des appareils à l’aide de l’Partner Center

Une fois que vous avez établi la relation avec vos clients, vous pouvez utiliser l’Partner Center pour ajouter des appareils à Autopilot pour tous les clients avec qui vous avez une relation en suivant les étapes suivantes :

1. Accéder à [l’Partner Center](https://partner.microsoft.com/dashboard)
2. Sélectionnez **Clients** dans le menu De l’Centre partenaires, puis sélectionnez le client dont vous souhaitez gérer les appareils.
3. Dans la page de détails du client, sélectionnez **Appareils.**
4. Sous **Appliquer des profils** aux appareils, **sélectionnez Ajouter des appareils.**
5. Entrez la balise de groupe appropriée pour le profil d’appareil que vous  avez sélectionné (comme indiqué dans le tableau suivant), puis sélectionnez Parcourir pour télécharger la liste du client (au format de fichier .csv) dans l’Partner Center.

|[Profil d’appareil](../service-description/profiles.md)  |Balise de groupe  |
|---------|---------|
|Données sensibles     |**Microsoft365Managed \_ SensitiveData**    |
|Utilisateur avec pouvoir     | **Microsoft365Managed \_ PowerUser**          |
|Standard     | **Microsoft365Managed \_ Standard**        |

> [!IMPORTANT]
> Le nom du groupe doit correspondre exactement à ceux répertoriés dans le tableau, y compris les majuscules et les caractères spéciaux. Cela permettra aux appareils nouvellement inscrits d’être affectés avec le Microsoft Manged Desktop Autopilot.

>[!NOTE]
> Vous devriez avoir reçu ce fichier .csv l’achat de votre appareil. Si vous n’avez pas reçu de fichier .csv, vous pouvez en créer un vous-même en suivant les étapes de l’étape Ajout d’appareils [Windows Autopilot](/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell). Les colonnes supplémentaires ne sont pas pris en charge. Les guillemets ne sont pas pris en charge. Seuls les fichiers texte au format ANSI peuvent être utilisés (et non Unicode). Les en-têtes sont sensibles à la cas. La modification du fichier dans Excel et son enregistrement en tant que fichier CSV ne génèreront pas de fichier utilisable en raison de ces exigences. Veillez à conserver les zéros non élevés dans les numéros de série de l’appareil. Les partenaires doivent [utiliser Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) pour inscrire des appareils Microsoft Manged Desktop appareils dans l’Partner Center.

Si vous recevez un message d’erreur lors de la tentative de chargement .csv fichier, vérifiez le format du fichier. Assurez-vous que l’ordre des colonnes correspond à ce qui est décrit dans Utiliser les profils Autopilot Windows sur les nouveaux appareils pour personnaliser l’expérience pré-encadrée [d’un client.](/partner-center/autopilot#add-devices-to-a-customers-account) Vous pouvez également utiliser l’exemple .csv fichier fourni à partir du lien en dessous d’Ajouter des appareils **pour** créer une liste d’appareils. 

Pour plus d’informations sur Autopilot dans les scénarios partenaires, voir Ajouter des [appareils au compte d’un client.](/partner-center/autopilot#add-devices-to-a-customers-account)


## <a name="register-devices-by-using-the-oem-api"></a>Inscrire des appareils à l’aide de l’API OEM

Avant d’achever l’inscription d’un client, vous devez d’abord établir une relation avec lui. Vous devez avoir un lien unique à fournir à vos clients respectifs. Découvrez [comment établir une relation OEM.](/windows/deployment/windows-autopilot/registration-auth#oem-authorization)

Une fois la relation établie, vous pouvez commencer à inscrire des appareils pour les clients à l’aide de la balise de groupe appropriée pour chaque profil d’appareil qu’ils ont sélectionné :


|Profil d’appareil  |Balise de groupe  |
|---------|---------|
|Données sensibles     | **Microsoft365Managed \_ SensitiveData**     |
|Utilisateur avec pouvoir     | **Microsoft365Managed \_ PowerUser**          |
|Standard     | **Microsoft365Managed \_ Standard**      |

> [!IMPORTANT]
> Les balises de groupe doivent correspondre exactement à celles répertoriées dans le tableau, notamment les majuscules et les caractères spéciaux. Cela permettra aux appareils nouvellement inscrits d’être affectés avec le Microsoft Manged Desktop Autopilot.
