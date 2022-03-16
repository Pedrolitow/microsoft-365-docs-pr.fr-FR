---
title: Créer des indicateurs
ms.reviewer: ''
description: Créez des indicateurs pour un hachage de fichier, une adresse IP, des URL ou des domaines qui définissent la détection, la prévention et l’exclusion des entités.
keywords: gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, url, domaine
ms.prod: m365-security
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
ms.technology: mde
ms.openlocfilehash: 00685ee4540949028b8bb438dd8a4965e2e9a5e7
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63513057"
---
# <a name="create-indicators"></a>Créer des indicateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

L’indicateur de compromission (IoCs) est une fonctionnalité essentielle dans chaque solution de protection des points de terminaison. Cette fonctionnalité permet à SecOps de définir une liste d’indicateurs pour la détection et le blocage (prévention et réponse).

Créez des indicateurs qui définissent la détection, la prévention et l’exclusion des entités. Vous pouvez définir l’action à prendre, ainsi que la durée de l’application de l’action, ainsi que l’étendue du groupe d’appareils à appliquer.

Les sources actuellement pris en charge sont le moteur de détection cloud de Defender for Endpoint, le moteur automatisé d’investigation et de correction et le moteur de prévention des points de terminaison (Antivirus Microsoft Defender).

## <a name="cloud-detection-engine"></a>Moteur de détection cloud

Le moteur de détection cloud de Defender for Endpoint analyse régulièrement les données collectées et tente de correspondre aux indicateurs que vous avez définies. En cas de correspondance, une action est prise en fonction des paramètres que vous avez spécifiés pour l’IoC.

## <a name="endpoint-prevention-engine"></a>Moteur de prévention des points de terminaison

La même liste d’indicateurs est honorée par l’agent de prévention. Autrement dit, si Microsoft Defender AV est le principal antivirus configuré, les indicateurs de correspondance seront traités en fonction des paramètres. Par exemple, si l’action est « Alerte et bloquer », Microsoft Defender AV empêche les exécutions de fichiers (bloquer et corriger) et une alerte correspondante est élevée. En revanche, si l’action est définie sur « Autoriser », l’Antivirus Microsoft Defender ne détecte pas et ne bloque pas l’exécuter.

## <a name="automated-investigation-and-remediation-engine"></a>Moteur d’examen et de correction automatisé

L’examen et la correction automatisés se comportent de la même manière. Si un indicateur est définie sur « Autoriser », l’examen et la correction automatisés ignorent un verdict « mauvais » pour lui. S’il est définie sur « Bloquer », les examens et corrections automatisés le traitent comme « mauvais ».

Le paramètre EnableFileHashComputation calcule le hachage de fichier pour le cert et l’IoC de fichier pendant les analyses de fichiers. Il prend en charge l’application IoC des haps et des certs appartenant à des applications fiables. Elle sera activée et désactivée simultanément avec le paramètre autoriser ou bloquer le fichier. EnableFileHashComputation est activé manuellement par le biais de la stratégie de groupe et est désactivé par défaut.

Lors de la création d’un indicateur (IoC), une ou plusieurs des actions suivantes sont disponibles :

- Allow : l’IoC sera autorisé à s’exécuter sur vos appareils.
- Audit : une alerte est déclenchée lors de l’ioC.
- Avertir : l’IoC invite un avertissement que l’utilisateur peut contourner 
- Bloquer l’exécution : l’IoC n’est pas autorisé à s’exécuter.
- Bloquer et corriger : l’IoC n’est pas autorisé à s’exécuter et une action de correction est appliquée à l’IoC.

>[!NOTE]
> L’utilisation du mode Avertissement invite vos utilisateurs à s’avertir s’ils ouvrent une application à risque. L’invite ne les empêchera pas d’utiliser l’application, mais vous pouvez fournir un message personnalisé et des liens vers une page d’entreprise qui décrit l’utilisation appropriée de l’application. Les utilisateurs peuvent toujours ignorer l’avertissement et continuer à utiliser l’application s’ils en ont besoin. Pour plus d’informations, voir [Govern apps discovered by Microsoft Defender for Endpoint](/cloud-app-security/mde-govern).

Vous pouvez créer un indicateur pour :

- [Files](indicator-file.md)
- [Adresses IP, URL/domaines](indicator-ip-domain.md)
- [Certificats](indicator-certificates.md)

Le tableau ci-dessous indique exactement les actions disponibles par type d’indicateur (IoC) :

| Type IoC | Actions disponibles |
|:---|:---|
| [Files](indicator-file.md) | Autoriser <br> Audit <br> Bloquer et corriger |
| [Adresses IP](indicator-ip-domain.md) | Autoriser <br> Audit <br> Bloquer l’exécution <br> Avertir |
| [URL et domaines](indicator-ip-domain.md) | Autoriser <br> Audit <br> Bloquer l’exécution<br> Avertir |
| [Certificats](indicator-certificates.md) | Autoriser <br> Bloquer et corriger |

Les fonctionnalités des IOC pré-existants ne changeront pas. Toutefois, les indicateurs ont été renommés pour correspondre aux actions de réponse prises en charge en cours :

- L’action de réponse « alerte uniquement » a été renommée « audit » avec le paramètre d’alerte généré activé.
- La réponse « alerte et blocage » a été renommée « bloquer et corriger » avec le paramètre d’alerte de générer facultatif.

Le schéma de l’API IoC et les ID de menace à l’avance de recherche ont été mis à jour pour s’aligner sur le changement de nom des actions de réponse IoC. Les modifications apportées au schéma d’API s’appliquent à tous les types IoC.

> [!Note]
> Il existe une limite de 15 000 indicateurs par client. Les indicateurs de fichier et de certificat ne bloquent pas les [exclusions définies pour Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Les indicateurs ne sont pas pris en charge Antivirus Microsoft Defender lorsqu’il est en mode passif.
>
> Le format d’importation de nouveaux indicateurs (IOC) a changé en fonction des nouvelles actions mises à jour et des paramètres d’alerte. Nous vous recommandons de télécharger le nouveau format CSV disponible en bas du panneau d’importation.

## <a name="related-topics"></a>Sujets associés

- [Créer un IoC contextuel](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Utiliser l’API d’indicateurs microsoft Defender pour les points de terminaison](ti-indicator.md)
- [Utiliser des solutions intégrées par des partenaires](partner-applications.md)
