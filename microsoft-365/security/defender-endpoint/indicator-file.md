---
title: Créer des indicateurs pour les fichiers
ms.reviewer: ''
description: Créez des indicateurs pour un hachage de fichier qui définissent la détection, la prévention et l’exclusion des entités.
keywords: fichier, hachage, gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, url, domaine
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d78f90e78a50d5902070f441a1d60693a5f531c8
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185718"
---
# <a name="create-indicators-for-files"></a>Créer des indicateurs pour les fichiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Vous pouvez empêcher toute propagation supplémentaire d’une attaque dans votre organisation en interdit les fichiers potentiellement malveillants ou les programmes malveillants suspects. Si vous connaissez un fichier exécutable portable (PE) potentiellement malveillant, vous pouvez le bloquer. Cette opération l’empêche d’être lue, écrite ou exécutée sur des ordinateurs de votre organisation.

Il existe deux façons de créer des indicateurs pour les fichiers :
- En créant un indicateur via la page paramètres
- En créant un indicateur contextuel à l’aide du bouton Ajouter un indicateur à partir de la page de détails du fichier

### <a name="before-you-begin"></a>Avant de commencer
Il est important de comprendre les conditions préalables suivantes avant de créer des indicateurs pour les fichiers :

- Cette fonctionnalité est disponible si votre organisation utilise Windows Defender antivirus et la protection basée sur le cloud est activée. Pour plus d’informations, voir Utiliser les technologies de nouvelle génération dans [l’Antivirus Microsoft Defender via](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus)la protection livrée par le cloud.
- La version du client anti-programme malveillant doit être 4.18.1901.x ou version ultérieure.
- Pris en charge sur les ordinateurs sur Windows 10, version 1703 ou ultérieure, Windows Server 2016 et 2019.
- Pour commencer à bloquer des fichiers, vous devez d’abord activer la fonctionnalité Bloquer ou [autoriser dans  ](advanced-features.md) paramètres.
- Cette fonctionnalité est conçue pour empêcher le téléchargement de programmes malveillants (ou de fichiers potentiellement malveillants) à partir du web. Il prend actuellement en charge les fichiers exécutables portables (PE), y compris les fichiers _.exe_ et _.dll._ La couverture sera étendue au fil du temps.

>[!IMPORTANT]
>- La fonction autoriser ou bloquer ne peut pas être effectuée sur les fichiers si la classification du fichier existe sur le cache de l’appareil avant l’action autoriser ou bloquer 
>- Les fichiers signés fiables seront traités différemment. Defender for Endpoint est optimisé pour gérer les fichiers malveillants. Dans certains cas, la tentative de blocage des fichiers signés de confiance peut avoir des conséquences sur les performances.

 
>[!NOTE]
>En règle générale, les blocs de fichiers sont appliqués en quelques minutes, mais peuvent prendre jusqu’à 30 minutes.

### <a name="create-an-indicator-for-files-from-the-settings-page"></a>Créer un indicateur pour les fichiers à partir de la page paramètres

1. Dans le volet de navigation, sélectionnez **Indicateurs**  >  **de paramètres.**  

2. Sélectionnez **l’onglet De hachage de** fichier.

3. Sélectionnez **Ajouter un indicateur**.

4. Spécifiez les détails suivants :
   - Indicateur : spécifiez les détails de l’entité et définissez l’expiration de l’indicateur.
   - Action : spécifiez l’action à prendre et fournissez une description.
   - Étendue : définir l’étendue du groupe d’ordinateurs.

5. Consultez les détails de l’onglet Résumé, puis cliquez sur **Enregistrer.**

### <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Créer un indicateur contextuel à partir de la page de détails du fichier
L’une des options lorsque vous prenez des mesures de réponse sur un [fichier consiste](respond-file-alerts.md) à ajouter un indicateur pour le fichier. 

Lorsque vous ajoutez un hachage d’indicateur pour un fichier, vous pouvez choisir de lancer une alerte et de bloquer le fichier chaque fois qu’un ordinateur de votre organisation tente de l’exécuter.

Les fichiers automatiquement bloqués par un indicateur ne s’afficheront pas dans le centre de l’action du fichier, mais les alertes resteront visibles dans la file d’attente des alertes.


## <a name="related-topics"></a>Voir aussi
- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les adresses IP et les URL/domaines](indicator-ip-domain.md)
- [Créer des indicateurs basés sur des certificats](indicator-certificates.md)
- [Gérer les indicateurs](indicator-manage.md)
