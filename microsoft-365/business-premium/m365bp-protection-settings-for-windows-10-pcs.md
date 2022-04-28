---
title: Modifier ou créer des paramètres de protection d’appareil pour Windows 10 PC
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: bd66c26c-73a4-45a8-8642-3ea4ee7cd89d
description: Découvrez les paramètres disponibles dans Microsoft 365 pour les entreprises afin de sécuriser les appareils Windows 10.
ms.openlocfilehash: ef4df7b308c52275db8d43c1c0619a64594ed690
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096241"
---
# <a name="edit-or-create-device-protection-settings-for-windows-10-pcs"></a>Modifier ou créer des paramètres de protection d’appareil pour Windows 10 PC

Cet article s’applique à Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender for Business](../security/defender-business/mdb-overview.md).

Après avoir configuré les paramètres de protection Windows par défaut sur la page d’installation, vous pouvez en ajouter de nouveaux qui s’appliquent à tous les utilisateurs ou à un ensemble d’utilisateurs. Vous pouvez également modifier celles que vous avez créées.

## <a name="watch-create-protection-settings-for-windows-10-devices"></a>Regarder : Créer des paramètres de protection pour les appareils Windows 10

Visionnez une vidéo sur la sécurisation des appareils Windows 10 avec Microsoft 365 Entreprise :
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/a5734146-620a-4cec-8618-536b3ca37972?autoplay=false]
  
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 

2. Dans le volet de navigation gauche, choisissez **Appareils** \> **Stratégies** \> **Ajouter**.

3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 

4. Sous **Type de stratégie**, sélectionnez **Configuration d'appareil Windows 10**.

5. Développez **Périphériques Windows 10 sécurisés**\> configurer les paramètres comme vous le souhaitez. Pour plus d’informations, consultez [Paramètres disponibles](#available-settings). 
    
    Vous pouvez toujours utiliser le lien **Réinitialiser les paramètres par défaut** pour rétablir la valeur par défaut. 
    
    ![Volet Ajouter une stratégie avec Windows 10 configuration de l’appareil sélectionnée.](./../media/fa9e2dc2-7eae-4c96-af34-765a1f641ecf.png)
  
6. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis recherchez le groupe qui obtiendra ces paramètres \> **Sélectionner**.

7. Enfin, sélectionnez **Terminé** pour enregistrer la stratégie et l'affecter à des appareils. 

## <a name="edit-windows-10-protection-settings"></a>Modifier les paramètres de protection Windows 10
 
1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     

2. Dans le volet de navigation gauche, choisissez **Appareils** \> **Stratégies** .

3. Choisissez une stratégie d’appareil Windows existante, puis **Modifier**.

4. Choisissez **Modifier** à côté d’un paramètre que vous souhaitez modifier, puis **Enregistrer**.

## <a name="available-settings"></a>Paramètres disponibles

Par défaut, tous les paramètres sont **Activés**. Les paramètres suivants sont disponibles.
  
Pour plus d’informations, consultez [Comment les fonctionnalités de protection dans Microsoft 365 Premium sont mappées aux paramètres Intune](m365bp-map-protection-features-to-intune-settings.md). 


|Paramètre  |Description  |
|:-----|:-----|
|Protéger les ordinateurs des virus et d'autres menaces à l'aide de l'antivirus Windows Defender  |L'antivirus Windows Defender doit être activé pour protéger les ordinateurs contre les risques liés à la connexion à internet.  |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  |Active les paramètres Microsoft Edge qui protègent les utilisateurs contre les sites et téléchargements malveillants.  |
|Utiliser des règles qui réduisent la surface d'attaque des appareils  |Quand elle est activée, la réduction de la surface d'attaque aide à bloquer les actions et applications que les logiciels malveillants utilisent généralement pour contaminer des appareils. Ce paramètre est disponible uniquement si Antivirus Windows Defender est activé. Pour en savoir plus, voir [Réduire les surfaces d'attaque](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection).    |
|Protéger les dossiers contre des menaces telles que des rançongiciels  |Ce paramètre utilise l'Accès contrôlé aux dossiers pour protéger les données de l'entreprise contre l'apport de modifications par des applications suspectes ou malveillantes, telles que les rançongiciels. L'apport de modifications aux dossiers protégés par des applications de ces types est bloqué. Ce paramètre est disponible uniquement si Antivirus Windows Defender est activé. Pour en savoir plus, voir [Protéger des dossiers importants avec l'Accès contrôlé aux dossiers](/mem/configmgr/protect/deploy-use/create-deploy-exploit-guard-policy#bkmk_CFA).  |
|Empêcher l'accès réseau à du contenu potentiellement malveillant sur Internet  |Utilisez ce paramètre pour bloquer les connexions utilisateur sortantes à des emplacements Internet de faible réputation susceptibles d’héberger des tentatives d’hameçonnage, des attaques ou d’autres contenus malveillants. Ce paramètre n’est disponible que si Antivirus Windows Defender est défini sur **Activé**. Pour plus d’informations, consultez [Protéger votre réseau](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus).  |
|Protéger les fichiers et dossiers sur PC contre un accès non autorisé avec BitLocker  |BitLocker protège les données en chiffrant les disques durs de l’ordinateur et en les protégeant contre l’exposition des données en cas de perte ou de vol d’un ordinateur. Pour plus d’informations, consultez [FAQ BitLocker](/windows/security/information-protection/BitLocker/BitLocker-frequently-asked-questions).  |
|Autoriser les utilisateurs à télécharger des applications à partir du Microsoft Store  |Permet aux utilisateurs de télécharger et d'installer des applications à partir du Microsoft Store. Il peut s'agir de jeux ou d'outils de productivité, c'est pourquoi nous laissons ce paramètre **activé**, mais vous pouvez le désactiver pour plus de sécurité.    |
|Autoriser les utilisateurs à accéder à Cortana  |Cortana peut être très utile ! Elle peut activer ou désactiver des paramètres pour vous, vous indiquer un trajet ou veiller à ce que vous arriviez à l'heure à vos rendez-vous. C'est la raison pour laquelle ce paramètre est **activé** par défaut.  |
|Autoriser les utilisateurs à recevoir des conseils de Windows et des annonces de Microsoft  |Les conseils Windows peuvent être très pratiques et aident les utilisateurs lors du lancement de nouvelles fonctionnalités.  |
|Maintenir les appareils Windows 10 à jour automatiquement  |Permet d'assurer que les appareils Windows 10 reçoivent automatiquement les dernières mises à jour.  |
|Désactiver l'écran d'un appareil resté inactif pendant  |Permet d'assurer la protection des données d'entreprise lorsqu'un utilisateur est inactif. Il est possible qu'un utilisateur travaille dans un lieu public, par exemple un café, et s'éloigne ou soit distrait pendant un instant, laissant son appareil à la vue de tous. Ce paramètre vous permet de contrôler la durée pendant laquelle l'utilisateur peut être inactif avant l'extinction de l'écran.  |

## <a name="see-also"></a>Voir aussi

[10 principales façons de sécuriser les plans Microsoft 365 pour les entreprises](../admin/security-and-compliance/secure-your-business-data.md) 