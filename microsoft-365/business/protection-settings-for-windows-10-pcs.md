---
title: Définir les paramètres de protection des appareils pour les PC Windows 10
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: bd66c26c-73a4-45a8-8642-3ea4ee7cd89d
description: Découvrez les par défaut et d’autres paramètres disponibles dans Microsoft 365 Business pour sécuriser les périphériques Windows 10.
ms.openlocfilehash: ebfe5f59e544b67e5a4f2ecd990031e9221ff8e5
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866835"
---
# <a name="set-device-protection-settings-for-windows-10-pcs"></a>Définir les paramètres de protection des appareils pour les PC Windows 10

## <a name="secure-windows-10-devices"></a>Sécuriser les appareils Windows 10

Visionnez une vidéo sur la sécurisation des appareils Windows 10 avec Microsoft 365 Entreprise :
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/a5734146-620a-4cec-8618-536b3ca37972?autoplay=false]
  
1. Connectez-vous à [Microsoft 365 Business](https://portal.office.com) avec des informations d'identification d'administrateur général. 
    
2. Dans la carte **Stratégies d'appareil** du Centre d'administration, sélectionnez **Ajouter une stratégie**.
    
    ![Device policies card in the admin center.](media/27c12b61-d112-4348-b557-4f3e46204797.png)
  
3. Dans le volet **Ajouter une stratégie**, entrez un nom unique pour cette stratégie. 
    
4. Sous **Type de stratégie**, sélectionnez **Configuration d'appareil Windows 10**.
    
5. Développez **Sécuriser Windows 10 périphériques** \> configurer les paramètres des manière dont vous souhaitez. Pour plus d’informations, voir [paramètres disponibles](protection-settings-for-windows-10-pcs.md#bkmk_availablesettings) . 
    
    Vous pouvez toujours utiliser le lien **Réinitialiser les paramètres par défaut** pour rétablir la valeur par défaut. 
    
    ![Add policy pane with Windows 10 Device configuration selected](media/fa9e2dc2-7eae-4c96-af34-765a1f641ecf.png)
  
6. Maintenant, définissez **Qui recevra ces paramètres ?** Si vous ne voulez pas utiliser le groupe de sécurité par défaut **Tous les utilisateurs**, sélectionnez **Modifier**, puis recherchez le groupe qui obtiendra ces paramètres \> **Sélectionner**.
    
7. Enfin, sélectionnez **Terminé** pour enregistrer la stratégie et l'affecter à des appareils. 
    
## <a name="available-settings"></a>Paramètres disponibles

Par défaut, tous les paramètres sont **Activés**. Les paramètres suivants sont disponibles.
  
Pour plus d'informations, voir [Correspondance entre les fonctionnalités de protection de Microsoft 365 Business et les paramètres Intune](map-protection-features-to-intune-settings.md). 
  
|||
|:-----|:-----|
|Paramètre  <br/> |Description  <br/> |
|Protéger les ordinateurs des virus et d'autres menaces à l'aide de l'antivirus Windows Defender  <br/> |L'anti-virus Windows Defender doit être activé pour protéger les ordinateurs contre les risques liés à la connexion à internet.  <br/> |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  <br/> |Active les paramètres Microsoft Edge qui protègent les utilisateurs contre les sites et téléchargements malveillants.  <br/> |
|Utiliser des règles qui réduisent la surface d'attaque des appareils  <br/> |Quand elle est activée, la réduction de la surface d'attaque aide à bloquer les actions et applications que les logiciels malveillants utilisent généralement pour contaminer des appareils. Ce paramètre est disponible uniquement si Antivirus Windows Defender est activé. Pour en savoir plus, voir [Réduire les surfaces d'attaque](https://go.microsoft.com/fwlink/?linkid=870417).  <br/> |
|Protéger les dossiers contre des menaces telles que des rançongiciels  <br/> |Ce paramètre utilise l'Accès contrôlé aux dossiers pour protéger les données de l'entreprise contre l'apport de modifications par des applications suspectes ou malveillantes, telles que les rançongiciels. L'apport de modifications aux dossiers protégés par des applications de ces types est bloqué. Ce paramètre est disponible uniquement si Antivirus Windows Defender est activé. Pour en savoir plus, voir [Protéger des dossiers importants avec l'Accès contrôlé aux dossiers](https://go.microsoft.com/fwlink/?linkid=870418).  <br/> |
|Empêcher l'accès réseau à du contenu potentiellement malveillant sur Internet  <br/> |Utilisez ce paramètre pour bloquer les connexions utilisateur sortantes à des sites Internet de faible réputation, susceptibles d'exposer à du hameçonnage en ligne, à des attaques ou à d'autres contenus malveillants. Ce paramètre est disponible uniquement si Antivirus Windows Defender est activé. Pour plus d'informations, voir [Protéger votre réseau](https://go.microsoft.com/fwlink/?linkid=870419).  <br/> |
|Protéger les fichiers et dossiers sur PC contre un accès non autorisé avec BitLocker  <br/> |Bitlocker protège les données en chiffrant les disques durs de l'ordinateur, et protège contre l'exposition des données en cas de perte ou de vol. Pour plus d'informations, voir [FAQ Bitlocker](https://go.microsoft.com/fwlink/?linkid=871000).  <br/> |
|Autoriser les utilisateurs à télécharger des applications à partir du Microsoft Store  <br/> |Permet aux utilisateurs de télécharger et d'installer des applications à partir du Microsoft Store. Il peut s'agir de jeux ou d'outils de productivité, c'est pourquoi nous laissons ce paramètre **activé**, mais vous pouvez le désactiver pour plus de sécurité.  <br/> |
|Autoriser les utilisateurs à accéder à Cortana  <br/> |Cortana peut être très utile ! Elle peut activer ou désactiver des paramètres pour vous, vous indiquer un trajet ou veiller à ce que vous arriviez à l'heure à vos rendez-vous. C'est la raison pour laquelle ce paramètre est **activé** par défaut.  <br/> |
|Autoriser les utilisateurs à recevoir des conseils de Windows et des annonces de Microsoft  <br/> |Les conseils Windows peuvent être très pratiques et aident les utilisateurs lors du lancement de nouvelles fonctionnalités.  <br/> |
|Maintenir les appareils Windows 10 à jour automatiquement  <br/> |Permet d'assurer que les appareils Windows 10 reçoivent automatiquement les dernières mises à jour.  <br/> |
|Désactiver l'écran d'un appareil resté inactif pendant  <br/> |Permet d'assurer la protection des données d'entreprise lorsqu'un utilisateur est inactif. Il est possible qu'un utilisateur travaille dans un lieu public, par exemple un café, et s'éloigne ou soit distrait pendant un instant, laissant son appareil à la vue de tous. Ce paramètre vous permet de contrôler la durée pendant laquelle l'utilisateur peut être inactif avant l'extinction de l'écran.  <br/> |
   
  

