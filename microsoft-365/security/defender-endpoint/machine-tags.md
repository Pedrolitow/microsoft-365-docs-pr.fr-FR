---
title: Créer et gérer des balises d’appareils
description: Utiliser des balises de périphérique pour grouper des appareils pour capturer le contexte et activer la création de listes dynamiques dans le cadre d’un incident
keywords: tags, device tags, device groups, groups, remediation, level, rules, aad group, role, assign, rank
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
ms.openlocfilehash: e23980133d2fb0c69ca79f6dfdde7656e1961097
ms.sourcegitcommit: 6a73f0f0c0360fc015d9c0d0af26fb6926d9477d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2021
ms.locfileid: "58745636"
---
# <a name="create-and-manage-device-tags"></a>Créer et gérer des balises d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ajoutez des balises sur les appareils pour créer une affiliation de groupe logique. Les balises d’appareil prennent en charge le mappage approprié du réseau, ce qui vous permet d’attacher différentes balises pour capturer le contexte et d’activer la création de liste dynamique dans le cadre d’un incident. Les balises peuvent être  utilisées comme filtre dans l’affichage Liste des appareils ou pour grouper des appareils. Pour plus d’informations sur le regroupement d’appareils, voir [Créer et gérer des groupes d’appareils.](machine-groups.md)

Vous pouvez ajouter des balises sur les appareils en utilisant les méthodes suivantes :

- Utilisation du portail
- Définition d’une valeur de clé de Registre

> [!NOTE]
> Il peut y avoir une certaine latence entre le moment où une balise est ajoutée à un appareil et sa disponibilité dans la liste des appareils et la page de l’appareil.

Pour ajouter des balises d’appareil à l’aide de l’API, consultez [Ajouter ou supprimer des balises d’appareil API](add-or-remove-machine-tags.md).

## <a name="add-and-manage-device-tags-using-the-portal"></a>Ajouter et gérer des balises d’appareil à l’aide du portail

1. Sélectionnez l’appareil sur lequel vous souhaitez gérer les balises. Vous pouvez sélectionner ou rechercher un appareil à partir de l’une des vues suivantes :

   - **Tableau de bord Opérations de sécurité** : sélectionnez le nom de l’appareil dans la section Principaux appareils avec alertes actives.
   - **File d’attente des alertes** : sélectionnez le nom de l’appareil en regard de l’icône de l’appareil dans la file d’attente des alertes.
   - **Liste des appareils** : sélectionnez le nom de l’appareil dans la liste des appareils.
   - **Zone de recherche** : sélectionnez Appareil dans le menu déroulant et entrez le nom de l’appareil.

     Vous pouvez également accéder à la page d’alerte via les Affichages de fichier et d’adresse IP.

2. Sélectionnez **Gérer les balises** dans la ligne des actions de réponse.

    :::image type="content" alt-text="Image du bouton Gérer les balises." source="images/manage-tags-option.png":::

3. Tapez pour rechercher ou créer des balises

    :::image type="content" alt-text="Image de l’ajout de balises sur un appareil1." source="images/create-new-tag.png":::

Les balises sont ajoutées à l’affichage de l’appareil et sont également reflétées dans l’affichage Liste **des** appareils. Vous pouvez ensuite utiliser le filtre **Balises** pour voir la liste des appareils appropriés.

> [!NOTE]
> Le filtrage peut ne pas fonctionner sur les noms de balises qui contiennent des parenthèses.
>
> Lorsque vous créez une balise, une liste de balises existantes s’affiche. La liste affiche uniquement les balises créées via le portail. Les balises existantes créées à partir d’appareils clients ne seront pas affichées.

Vous pouvez également supprimer des balises de cet affichage.

:::image type="content" alt-text="Image de l’ajout de balises sur un appareil2." source="images/new-tag-label-display.png":::

## <a name="add-device-tags-by-setting-a-registry-key-value"></a>Ajouter des balises d’appareil en définition d’une valeur de clé de Registre

> [!NOTE]
> Applicable uniquement sur les appareils suivants :
>
> - Windows 10, version 1709 ou ultérieure
> - Windows Serveur, version 1803 ou ultérieure
> - Windows Server 2016
> - Windows Server 2012 R2
> - Windows Server 2008 R2 SP1
> - Windows 8.1
> - Windows 7 SP1

> [!NOTE]
> Le nombre maximal de caractères qui peuvent être définies dans une balise est de 200.

Les appareils avec des balises similaires peuvent être pratiques lorsque vous devez appliquer une action contextuelle sur une liste spécifique d’appareils.

Utilisez l’entrée de clé de Registre suivante pour ajouter une balise sur un appareil :

- Clé de Registre : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging\`
- Valeur de clé de Registre (REG_SZ) : `Group`
- Données de clé de Registre : `Name of the tag you want to set`

> [!NOTE]
> La balise d’appareil fait partie du rapport d’informations sur l’appareil qui est généré une fois par jour. Vous pouvez également choisir de redémarrer le point de terminaison qui transférerait un nouveau rapport d’informations sur l’appareil.
>
> Si vous devez supprimer une balise ajoutée à l’aide de la clé de Registre ci-dessus, supprimez le contenu des données de clé de Registre au lieu de supprimer la clé « Group ».
