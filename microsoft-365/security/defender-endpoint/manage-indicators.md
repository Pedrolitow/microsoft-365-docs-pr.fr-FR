---
title: Créer des indicateurs
ms.reviewer: ''
description: Créez des indicateurs pour un hachage de fichier, une adresse IP, des URL ou des domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, URL, domaine
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 8274c99ba61e5901b5f380783b2e242ce1387e4f
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67522871"
---
# <a name="create-indicators"></a>Créer des indicateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

L’indicateur de compromission est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité permet à SecOps de définir une liste d’indicateurs pour la détection et le blocage (prévention et réponse).

Créez des indicateurs qui définissent la détection, la prévention et l’exclusion des entités. Vous pouvez définir l’action à entreprendre, ainsi que la durée d’application de l’action, ainsi que l’étendue du groupe d’appareils auquel l’appliquer.

Les sources actuellement prises en charge sont le moteur de détection cloud de Defender pour point de terminaison, le moteur d’investigation et de correction automatisé et le moteur de prévention des points de terminaison (Antivirus Microsoft Defender).

## <a name="cloud-detection-engine"></a>Moteur de détection cloud

Le moteur de détection cloud de Defender pour point de terminaison analyse régulièrement les données collectées et tente de faire correspondre les indicateurs que vous définissez. En cas de correspondance, une action est effectuée en fonction des paramètres que vous avez spécifiés pour l’IoC.

## <a name="endpoint-prevention-engine"></a>Moteur de prévention des points de terminaison

La même liste d’indicateurs est honorée par l’agent de prévention. Autrement dit, si l’Antivirus Microsoft Defender est l’antivirus principal configuré, les indicateurs correspondants sont traités en fonction des paramètres. Par exemple, si l’action est « Alerte et blocage », l’Antivirus Microsoft Defender empêche les exécutions de fichiers (bloquer et corriger) et une alerte correspondante est déclenchée. En revanche, si l’action est définie sur « Autoriser », l’Antivirus Microsoft Defender ne détecte pas ni ne bloque l’exécution du fichier.

## <a name="automated-investigation-and-remediation-engine"></a>Moteur d’investigation et de correction automatisé

L’investigation et la correction automatisées se comportent de la même façon. Si un indicateur est défini sur « Autoriser », l’examen et la correction automatisés ignorent un « mauvais » verdict pour celui-ci. S’il est défini sur « Bloquer », l’examen et la correction automatisés le traitent comme « mauvais ».

Le paramètre EnableFileHashComputation calcule le hachage de fichier pour le certificat et l’IoC de fichier pendant les analyses de fichiers. Il prend en charge l’application IoC des hachages et des certificats appartenant à des applications approuvées. Il sera activé et désactivé simultanément avec le paramètre autoriser ou bloquer le fichier. EnableFileHashComputation est activé manuellement via stratégie de groupe et est désactivé par défaut.

Lors de la création d’un indicateur (IoC), une ou plusieurs des actions suivantes sont disponibles :

- Autoriser : l’IoC sera autorisé à s’exécuter sur vos appareils.
- Audit : une alerte est déclenchée lors de l’exécution de l’IoC.
- Avertir : l’IoC invite un avertissement indiquant que l’utilisateur peut contourner 
- Bloquer l’exécution : l’IoC ne sera pas autorisé à s’exécuter.
- Bloquer et corriger : l’IoC ne sera pas autorisé à s’exécuter et une action de correction sera appliquée à l’IoC.

>[!NOTE]
> L’utilisation du mode Avertir invite les utilisateurs à recourir à un avertissement s’ils ouvrent une application risquée. L’invite ne les empêchera pas d’utiliser l’application, mais vous pouvez fournir un message personnalisé et des liens vers une page d’entreprise qui décrit l’utilisation appropriée de l’application. Les utilisateurs peuvent toujours contourner l’avertissement et continuer à utiliser l’application s’ils en ont besoin. Pour plus d’informations, consultez [Régir les applications découvertes par Microsoft Defender pour point de terminaison](/cloud-app-security/mde-govern).

Vous pouvez créer un indicateur pour :

- [Files](indicator-file.md)
- [Adresses IP, URL/domaines](indicator-ip-domain.md)
- [Certificats](indicator-certificates.md)

Le tableau ci-dessous indique exactement quelles actions sont disponibles par type d’indicateur (IoC) :

| Type IoC | Actions disponibles |
|:---|:---|
| [Files](indicator-file.md) | Autoriser <br> Audit <br> Bloquer et corriger |
| [Adresses IP](indicator-ip-domain.md) | Autoriser <br> Audit <br> Bloquer l’exécution <br> Avertir |
| [URL et domaines](indicator-ip-domain.md) | Autoriser <br> Audit <br> Bloquer l’exécution<br> Avertir |
| [Certificats](indicator-certificates.md) | Autoriser <br> Bloquer et corriger |

Les fonctionnalités des IOC préexistantes ne changeront pas. Toutefois, les indicateurs ont été renommés pour correspondre aux actions de réponse prises en charge actuelles :

- L’action de réponse « alerte uniquement » a été renommée « audit » avec le paramètre générer l’alerte activé.
- La réponse « alerte et bloc » a été renommée « bloquer et corriger » avec le paramètre d’alerte de génération facultatif.

Le schéma de l’API IoC et les ID de menace à l’avance ont été mis à jour pour s’aligner sur le changement de nom des actions de réponse IoC. Les modifications apportées au schéma d’API s’appliquent à tous les types IoC.

> [!Note]
> Il existe une limite de 15 000 indicateurs par locataire. Les indicateurs de fichier et de certificat ne bloquent pas [les exclusions définies pour l’antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Les indicateurs ne sont pas pris en charge dans l’Antivirus Microsoft Defender lorsqu’il est en mode passif.
>
> Le format d’importation de nouveaux indicateurs a changé en fonction des nouvelles actions mises à jour et des paramètres d’alerte. Nous vous recommandons de télécharger le nouveau format CSV qui se trouve en bas du panneau d’importation.

## <a name="related-topics"></a>Voir aussi

- [Créer un IoC contextuel](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Utiliser l’API d’indicateurs Microsoft Defender pour point de terminaison](ti-indicator.md)
- [Utiliser des solutions intégrées aux partenaires](partner-applications.md)
