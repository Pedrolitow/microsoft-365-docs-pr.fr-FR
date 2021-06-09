---
title: Microsoft Defender for Endpoint Device Control Printer Protection
description: Microsoft Defender pour endpoint Device Control Printer Protection empêche les personnes d’imprimer via des imprimantes non d’entreprise ou des imprimantes USB non approuvées.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: v-lsaldanha
author: lovina-saldanha
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.technology: mde
ms.openlocfilehash: 431497ded684543c33d91c49a0da47e92297321f
ms.sourcegitcommit: e1e275eb88153bafddf93327adf8f82318913a8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52809229"
---
# <a name="device-control-printer-protection"></a>Protection de l’Imprimante de Contrôle d’Appareil 

Microsoft Defender pour endpoint Device Control Printer Protection empêche les personnes d’imprimer via des imprimantes non d’entreprise ou des imprimantes USB non approuvées.

## <a name="licensing"></a>Licences 

Avant de commencer à vous lancer avec printer Protection, vous devez [confirmer votre abonnement Microsoft 365.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) Pour accéder à printer Protection et l’utiliser, vous devez avoir les informations suivantes :

- Microsoft 365 E3 pour le déploiement des fonctionnalités/stratégies 
- Microsoft 365 E5 de rapports 

## <a name="permission"></a>Autorisation 

Pour le déploiement de stratégie dans Intune, pour déployer une stratégie via OMA-URI, le compte doit être autorisé à créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser n’importe quel rôle intégré avec les autorisations ci-après :  

- Rôle gestionnaire de stratégies et de profils. 
- Ou rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lecture/Supprimer/Afficher les rapports pour les profils de configuration d’appareil  
- Ou administrateur global

Pour afficher les rapports de configuration d’appareil, le compte doit avoir les autorisations d’affichage des rapports. Vous pouvez créer des rôles personnalisés ou utiliser les rôles intégrés avec les autorisations ci-après :  

- Administrateur de sécurité global
- Administrateur de la sécurité
- Lecteur de sécurité 

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Assurez-vous que les Windows 10 que vous prévoyez de déployer Printer Protection pour répondre à ces exigences.

1. Rejoignez le programme Insider.

1. Les mises à jour Windows suivantes sont installées. 

    - For Windows 1809: install Windows Update [KB5003217](https://support.microsoft.com/en-us/topic/may-20-2021-kb5003217-os-build-17763-1971-preview-08687c95-0740-421b-a205-54aa2c716b46) 
    - For Windows 1909: install Windows Update [KB5003212](https://support.microsoft.com/en-us/topic/may-20-2021-kb5003212-os-build-18363-1593-preview-05381524-8380-4b30-b783-e330cad3d4a1)
    - Pour Windows 2004 ou ultérieure 
    
1. Si vous envisagez de déployer une stratégie via une stratégie de groupe, l’appareil doit être MDATP joint ; Si vous envisagez de déployer une stratégie via MEM, l’appareil doit être joint à Intune.

## <a name="deploy-device-control-printer-protection-policy"></a>Déployer une stratégie de protection de l’imprimante de contrôle d’appareil

Vous pouvez déployer la stratégie via la stratégie de groupe ou Intune.

| Titre | Description | Prise en charge du programme CSP | Prise en charge des GPO | Prise en charge basée sur l’utilisateur | Prise en charge basée sur l’ordinateur |
|:--|:--|:--|:--|:--|:--|
|**Activer les restrictions d’impression des contrôles d’appareil**|Empêcher les personnes d’imprimer via une imprimante non d’entreprise|Oui|Oui|Oui|Oui|
|**Liste des appareils d’impression connectés usb approuvés**\*|Autoriser une imprimante USB spécifique|Oui|Oui|Oui|Oui|
|||||||

\* Cette stratégie doit être utilisée avec les restrictions d’impression **d’activer le contrôle d’appareil**
## <a name="deploy-policy-via-intune"></a>Déployer une stratégie via Intune 

Pour Intune, la protection de l’imprimante de contrôle d’appareil prend uniquement en charge l’OMA-URI.

**Scénario 1 : empêcher les personnes d’imprimer via une imprimante non d’entreprise** 

 - Appliquez la stratégie sur l’ordinateur : 

    - ./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControl 

- Appliquez la stratégie à l’utilisateur : 

    - ./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControlUser 

Chaîne de prise en charge du programme CSP avec `` <enabled/>`` : 

:::image type="content" source="../../media/customeditrow.png" alt-text="ligne d’édition personnalisée":::

**Scénario 2 : autoriser des imprimantes USB approuvées spécifiques**

- Appliquez la stratégie sur l’ordinateur : 

    - ./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevices 

- Appliquez la stratégie à l’utilisateur : 

    - ./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevicesUser  

La chaîne de prise en charge du programme CSP avec des imprimantes USB approuvées via la propriété « ApprovedUsbPrintDevices » (par `` <enabled/><data id="ApprovedUsbPrintDevices_List" value="03F0/0853,0351/0872"/>`` exemple : 

:::image type="content" source="../../media/editrow.png" alt-text="modifier la ligne":::

## <a name="deploy-policy-via-group-policy"></a>Déployer une stratégie via une stratégie de groupe 

Si l’appareil n’est pas joint à Intune, vous pouvez également déployer la stratégie via la stratégie de groupe. 

**Scénario 1 : empêcher les personnes d’imprimer via une imprimante non d’entreprise** 

- Appliquez la stratégie sur l’ordinateur : 

    - Configuration ordinateur > modèles d’administration > imprimante : activer les restrictions d’impression des contrôles d’appareil 

- Appliquez la stratégie à l’utilisateur : 

    - Configuration utilisateur > modèles d’administration > Panneau de configuration > imprimantes : activer les restrictions d’impression des contrôles d’appareil 

:::image type="content" source="../../media/enable-device-ctrl-printing-restrictions.png" alt-text="activer les restrictions d’impression d’appareil":::
 

**Scénario 2 : autoriser des imprimantes USB approuvées spécifiques**

- Appliquez la stratégie sur l’ordinateur : 

    - Configuration ordinateur > modèles d’administration > imprimante : liste des périphériques d’impression connectés USB approuvés 

- Appliquez la stratégie à l’utilisateur :  

    - Configuration utilisateur > modèles d’administration > panneau de configuration > imprimantes : liste des périphériques d’impression connectés USB approuvés 
 
 :::image type="content" source="../../media/list-of-approved-connected-print-devices.png" alt-text="liste des périphériques d’impression connectés usb approuvés":::

## <a name="view-device-control-printer-protection-data-in-microsoft-defender-for-endpoint-portal"></a>Afficher les données de protection des imprimantes des contrôles d’appareil dans le portail Microsoft Defender pour les points de terminaison 

Le centre [Microsoft 365 de sécurité affiche](https://security.microsoft.com) l’impression bloquée par la stratégie Device Control Printer Protection ci-dessus.
 
```sql
DeviceEvents 

|where ActionType == 'PrintJobBlocked' 

| extend parsed=parse_json(AdditionalFields) 

| extend PrintedFile=tostring(parsed.JobOrDocumentName) 

| extend PrintPortName=tostring(parsed.PortName) 

| extend PrinterName=tostring(parsed.PrinterName) 

| extend Policy=tostring(parsed.RestrictionReason)  

| project Timestamp, DeviceId, DeviceName, ActionType, InitiatingProcessAccountName,Policy, PrintedFile, PrinterName, PrintPortName, AdditionalFields 

| order by Timestamp desc 
```

 :::image type="content" source="../../media/device-control-advanced-hunting.png" alt-text="recherche avancée":::
