---
title: Création de rapports de pare-feu d’hôte dans Microsoft Defender pour point de terminaison
description: Hébergez et affichez les rapports de pare-feu dans Microsoft 365 Defender portail.
keywords: windows defender, pare-feu
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 0d541fe3d129f1533c6642a0eb34547245faa489
ms.sourcegitcommit: 6bff75867764335685f972943170c7db46e33a6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2022
ms.locfileid: "67301307"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Création de rapports de pare-feu d’hôte dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Si vous êtes administrateur général ou de sécurité, vous pouvez désormais héberger des rapports de pare-feu sur le [portail Microsoft 365 Defender](https://security.microsoft.com). Cette fonctionnalité vous permet d’afficher les rapports de pare-feu Windows à partir d’un emplacement centralisé.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez exécuter Windows 10 ou une version ultérieure, Windows Server 2012 R2 ou une version ultérieure.
     > [!NOTE]
     > Pour que Windows2012 R2 et Windows Server 2016 apparaissent dans les rapports de pare-feu, ces appareils doivent être intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution).
- Pour intégrer des appareils au service Microsoft Defender pour point de terminaison, voir [ici](onboard-configure.md).
- Pour <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">que Microsoft 365 Defender portail</a> commence à recevoir les données, vous devez activer **les événements d’audit** pour Windows Defender Pare-feu avec Advanced Security :
  - [Audit Filtering Platform Packet Drop](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Auditer la connexion à la plateforme de filtrage](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Activez ces événements à l’aide de l’éditeur d’objets stratégie de groupe, de la stratégie de sécurité locale ou des commandes auditpol.exe. Pour plus d’informations, voir [ici](/windows/win32/fwp/auditing-and-logging).
  - Les deux commandes PowerShell sont les suivantes :
    - `auditpol /set /subcategory:"Filtering Platform Packet Drop" /failure:enable`
    - `auditpol /set /subcategory:"Filtering Platform Connection" /failure:enable`

```powershell
param (
    [switch]$remediate
)
try {

    $categories = "Filtering Platform Packet Drop,Filtering Platform Connection"
    $current = auditpol /get /subcategory:"$($categories)" /r | ConvertFrom-Csv    
    if ($current."Inclusion Setting" -ne "failure") {
        if ($remediate.IsPresent) {
            Write-Host "Remediating. No Auditing Enabled. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})"
            $output = auditpol /set /subcategory:"$($categories)" /failure:enable
            if($output -eq "The command was successfully executed.") {
                Write-Host "$($output)"
                exit 0
            }
            else {
                Write-Host "$($output)"
                exit 1
            }
        }
        else {
            Write-Host "Remediation Needed. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})."
            exit 1
        }
    }

}
catch {
    throw $_
} 
```

## <a name="the-process"></a>Le processus

> [!NOTE]
> Veillez à suivre les instructions de la section ci-dessus et à configurer correctement vos appareils pour la participation en préversion anticipée.

- Une fois les événements activés, Microsoft 365 Defender commence à surveiller les données, notamment : 
   - Adresse IP distante
   - Port distant
   - Local Port
   - Adresse IP locale
   - Computer Name
   - Traiter les connexions entrantes et sortantes
- Les administrateurs peuvent maintenant voir [l’activité](https://security.microsoft.com/firewall) du pare-feu hôte Windows ici.
   - Vous pouvez faciliter la création de rapports supplémentaires en téléchargeant le [script de création de rapports personnalisés](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) pour surveiller les activités de pare-feu Windows Defender à l’aide de Power BI.
   - Jusqu’à 12 heures peuvent être nécessaires avant que les données ne se reflètent.

## <a name="supported-scenarios"></a>Scénarios pris en charge

- [Création de rapports de pare-feu](#firewall-reporting)
- [De « Ordinateurs avec une connexion bloquée » à l’appareil](#from-computers-with-a-blocked-connection-to-device)
- [Explorer la chasse avancée (actualisation en préversion)](#drill-into-advanced-hunting-preview-refresh)

### <a name="firewall-reporting"></a>Création de rapports de pare-feu

Voici quelques exemples de pages de rapport de pare-feu. Vous trouverez ici un résumé de l’activité entrante, sortante et d’application. Vous pouvez accéder directement à cette page en accédant à <https://security.microsoft.com/firewall>.

:::image type="content" source="images/host-firewall-reporting-page.png" alt-text="Page de création de rapports du pare-feu hôte" lightbox="\images\host-firewall-reporting-page.png":::

Ces rapports sont également accessibles en accédant à  >  la section Rapports sur les **périphériques** de rapport de **sécurité** >  situés en bas de la carte **Connexions entrantes bloquées par le pare-feu**.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>De « Ordinateurs avec une connexion bloquée » à l’appareil

Les cartes prennent en charge les objets interactifs. Vous pouvez explorer l’activité d’un appareil en cliquant sur le nom de l’appareil, qui lancera le portail Microsoft 365 Defender dans un nouvel onglet et vous amènera directement à l’onglet **Chronologie** de l’appareil.

:::image type="content" source="images/firewall-reporting-blocked-connection.png" alt-text="Les ordinateurs avec une page de connexion bloquée" lightbox="\images\firewall-reporting-blocked-connection.png":::

Vous pouvez maintenant sélectionner l’onglet **Chronologie** , qui vous donne la liste des événements associés à cet appareil.

Après avoir cliqué sur le bouton **Filtres** dans le coin supérieur droit du volet d’affichage, sélectionnez le type d’événement souhaité. Dans ce cas, sélectionnez **Événements de pare-feu** et le volet est filtré sur les événements de pare-feu.

:::image type="content" source="images/firewall-reporting-filters-button.png" alt-text="Bouton Filtres" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Explorer la chasse avancée (actualisation en préversion)

Les rapports de pare-feu prennent en charge l’exploration de la carte directement dans **La chasse avancée** en cliquant sur le bouton **Ouvrir la chasse avancée** . La requête sera préremplie.

:::image type="content" source="images/firewall-reporting-advanced-hunting.png" alt-text="Bouton Ouvrir la chasse avancée" lightbox="\images\firewall-reporting-advanced-hunting.png":::

La requête peut maintenant être exécutée et tous les événements de pare-feu associés des 30 derniers jours peuvent être explorés.

Pour plus de rapports ou de modifications personnalisées, la requête peut être exportée dans Power BI pour une analyse plus approfondie. Vous pouvez faciliter la création de rapports personnalisés en téléchargeant le [script de création de rapports personnalisés](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) pour surveiller les activités de pare-feu Windows Defender à l’aide de Power BI.
