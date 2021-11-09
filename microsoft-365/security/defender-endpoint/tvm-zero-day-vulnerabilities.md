---
title: 'Atténuer les vulnérabilités du jour zéro : Gestion des menaces et des vulnérabilités'
description: Découvrez comment rechercher et atténuer les vulnérabilités « zero-day » dans votre environnement à l’Gestion des menaces et des vulnérabilités.
keywords: Vulnérabilités microsoft Defender pour endpoint tvm zero day, tvm, threat & gestion des vulnérabilités, zero day, 0-day, mitigate 0 day vulnerabilities, vulnerable CVE
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 9f1ed6e23c462e78ad0aaf6e94e59aa1c8efb11e
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2021
ms.locfileid: "60881756"
---
# <a name="mitigate-zero-day-vulnerabilities---threat-and-vulnerability-management"></a>Atténuer les vulnérabilités du jour zéro : Gestion des menaces et des vulnérabilités

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Menaces et gestion des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Une vulnérabilité « zero-day » est une vulnérabilité publiquement divulguée pour laquelle aucune mise à jour de sécurité ou correctifs officiels n’a été publié. Les vulnérabilités du jour zéro ont souvent des niveaux de gravité élevés et sont activement exploitées.

Les menaces et gestion des vulnérabilités afficheront uniquement les vulnérabilités zero-day dont ils disposent d’informations.

## <a name="find-information-about-zero-day-vulnerabilities"></a>Trouver des informations sur les vulnérabilités du jour zéro

Une fois qu’une vulnérabilité zéro jour a été trouvée, les informations à ce sujet sont transmises via les expériences suivantes dans le portail Microsoft 365 Defender web.

> [!NOTE]
> La fonctionnalité de vulnérabilité de 0 jour est actuellement disponible uniquement pour Windows produits.

### <a name="threat-and-vulnerability-management-dashboard"></a>Tableau de bord des menaces gestion des vulnérabilités de sécurité

Recherchez des recommandations avec une balise « zero-day » dans la carte « Recommandations de sécurité les plus importantes ».

![Recommandations les plus importantes avec une balise « zero-day ».](images/tvm-zero-day-top-security-recommendations.png)

Recherchez les principaux logiciels avec la balise « zero-day » dans la carte « Logiciels les plus vulnérables ».

![Logiciels les plus vulnérables avec une balise « zero-day ».](images/tvm-zero-day-top-software.png)

### <a name="weaknesses-page"></a>Page Faiblesses

Recherchez la vulnérabilité nommée « zero-day » ainsi qu’une description et des détails.

- Si un ID CVE est affecté à cette vulnérabilité, vous verrez l’étiquette « zero-day » en regard du nom CVE.

- Si aucun ID CVE n’est affecté à cette vulnérabilité, vous la trouverez sous un nom interne temporaire qui ressemble à « TVM-XXXX-XXXX ». Le nom sera mis à jour une fois qu’un ID CVE officiel a été affecté, mais le nom interne précédent peut toujours être recherché et trouvé dans le panneau latéral.

:::image type="content" alt-text="Exemple de jour zéro pour CVE-2020-17087 dans la page faiblesses." source="images/tvm-zero-day-weakness-name.png" lightbox="images/tvm-zero-day-weakness-name.png":::

### <a name="software-inventory-page"></a>Page Inventaire logiciel

Recherchez les logiciels avec la balise « zero-day ». Filtrez par la balise « zero day » pour voir uniquement les logiciels avec des vulnérabilités zero-day.

:::image type="content" alt-text="Exemple de jour zéro Windows Server 2016 dans la page d’inventaire logiciel." source="images/tvm-zero-day-software-inventory.png" lightbox="images/tvm-zero-day-software-inventory.png":::

### <a name="software-page"></a>Page de logiciels

Recherchez une balise « zero-day » pour chaque logiciel affecté par la vulnérabilité « zero-day ».

:::image type="content" alt-text="Exemple de jour zéro pour Windows Server 2016 page de logiciels." source="images/tvm-zero-day-software-page.png" lightbox="images/tvm-zero-day-software-page.png":::

### <a name="security-recommendations-page"></a>Page Recommandations en matière de sécurité

Affichez des suggestions claires sur les options de correction et d’atténuation, y compris les solutions de contournement si elles existent. Filtrez par balise « zero day » pour voir uniquement les recommandations de sécurité concernant les vulnérabilités zero-day.

S’il existe un logiciel avec une vulnérabilité zéro jour et des vulnérabilités supplémentaires à résoudre, vous recevrez une recommandation sur toutes les vulnérabilités.

:::image type="content" alt-text="Exemple de jour zéro de Windows Server 2016 dans la page recommandations de sécurité." source="images/tvm-zero-day-security-recommendation.png" lightbox="images/tvm-zero-day-security-recommendation.png":::

## <a name="addressing-zero-day-vulnerabilities"></a>Résoudre les vulnérabilités du jour zéro

Go to the security recommendation page and select a recommendation with a zero-day. Un flyout s’ouvre avec des informations sur le jour zéro et d’autres vulnérabilités pour ce logiciel.

Il y aura un lien vers les options d’atténuation et les solutions de contournement si elles sont disponibles. Les solutions de contournement peuvent aider à réduire les risques posés par cette vulnérabilité zero-day jusqu’à ce qu’un correctif ou une mise à jour de sécurité puisse être déployé.

Ouvrez les options de correction et choisissez le type d’attention. Une option de correction « attention requise » est recommandée pour les vulnérabilités du jour zéro, dans la mesure où une mise à jour n’a pas encore été publiée. Vous ne pourrez pas sélectionner une date d’échéance, car aucune action spécifique n’est à effectuer. S’il existe des vulnérabilités plus anciennes pour ce logiciel que vous souhaitez mettre à jour, vous pouvez remplacer l’option de correction « Attention requise » et choisir « mettre à jour ».

![Exemple de flyout zero day Windows Server 2016 dans la page recommandations de sécurité.](images/tvm-zero-day-recommendation-flyout400.png)

## <a name="track-zero-day-remediation-activities"></a>Suivre les activités de correction du jour zéro

Go to the Gestion des menaces et des vulnérabilités [Remediation](tvm-remediation.md) page to view the remediation activity item. Si vous avez choisi l’option de correction « Attention requise », il n’y aura aucune barre de progression, état du ticket ou date d’échéance, car il n’existe aucune action réelle que nous pouvons surveiller. Vous pouvez filtrer par type de correction, tel que « mise à jour logicielle » ou « attention requise », pour voir tous les éléments d’activité dans la même catégorie.

## <a name="patching-zero-day-vulnerabilities"></a>Correction des vulnérabilités du jour zéro

Lorsqu’un correctif est publié pour le jour zéro, la recommandation est modifiée en « Mise à jour » et une étiquette bleue en plus de celle-ci indique « Nouvelle mise à jour de sécurité pour le jour zéro ». Il ne sera plus considérer comme un jour zéro, la balise « zero-day » sera supprimée de toutes les pages.

![Recommandation pour « Mettre à jour Microsoft Windows 10 » avec une nouvelle étiquette de correctif.](images/tvm-zero-day-patch.jpg)

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble gestion des vulnérabilités menaces et gestion des vulnérabilités menaces](next-gen-threat-and-vuln-mgt.md)
- [Tableau de bord](tvm-dashboard-insights.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)
- [Inventaire des logiciels](tvm-software-inventory.md)
- [Les vulnérabilités dans mon organisation](tvm-weaknesses.md)
