---
title: Protéger les dossiers importants contre les ransomware contre le chiffrement de vos fichiers avec accès contrôlé aux dossiers
description: Les fichiers des dossiers par défaut peuvent être protégés contre les changements par des applications malveillantes. Empêcher les ransomware de chiffrer vos fichiers.
keywords: accès contrôlé aux dossiers, windows 10, windows defender, ransomware, protéger, fichiers, dossiers
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
audience: ITPro
ms.date: 06/10/2021
ms.reviewer: v-maave
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.openlocfilehash: ffcb986198cbe672b935980aea39f340bab947b9f3ba21ad890feadf6cc8f2ee
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53863678"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>Protéger les dossiers importants avec accès contrôlé aux dossiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>Qu’est-ce que l’accès contrôlé aux dossiers ?

L’accès contrôlé aux dossiers permet de protéger vos données précieuses contre les applications malveillantes et les menaces, telles que les ransomware. L’accès contrôlé aux dossiers protège vos données en vérifiant les applications par rapport à une liste d’applications connues et fiables. Pris en charge sur les clients Windows Server 2019 et Windows 10, l’accès contrôlé aux dossiers peut être désactivé à l’aide de Sécurité Windows App, Microsoft Endpoint Configuration Manager ou Intune (pour les appareils gérés). 

> [!NOTE]
> Les moteurs de script ne sont pas fiables et vous ne pouvez pas leur autoriser l’accès aux dossiers protégés contrôlés.  Par exemple, PowerShell n’est pas approuvé par l’accès contrôlé aux [dossiers,](/microsoft-365/security/defender-endpoint/indicator-certificates)même si vous l’autorisez avec des indicateurs de certificat et de fichier. 

L’accès contrôlé aux dossiers fonctionne mieux avec [Microsoft Defender pour point](microsoft-defender-endpoint.md)de terminaison, qui vous fournit des rapports détaillés sur les événements et les blocs d’accès contrôlé aux dossiers dans le cadre des scénarios d’investigation d’alerte [habituels.](investigate-alerts.md)

> [!TIP]
> Les blocs d’accès contrôlé aux dossiers ne génèrent pas d’alertes dans la file [d’attente des alertes.](alerts-queue.md) Toutefois, vous pouvez afficher des informations [](investigate-machines.md)sur les blocs d’accès contrôlés aux dossiers dans l’affichage chronologie de l’appareil, lors de l’utilisation d’un repérage avancé [ou](advanced-hunting-overview.md)avec des règles de [détection personnalisées.](custom-detection-rules.md)

## <a name="how-does-controlled-folder-access-work"></a>Comment fonctionne l’accès contrôlé aux dossiers ?

L’accès contrôlé aux dossiers fonctionne uniquement en permettant aux applications de confiance d’accéder aux dossiers protégés. Les dossiers protégés sont spécifiés lorsque l’accès contrôlé aux dossiers est configuré. En règle générale, les dossiers couramment utilisés, tels que ceux utilisés pour les documents, les images, les téléchargements, etc., sont inclus dans la liste des dossiers contrôlés. 

L’accès contrôlé aux dossiers fonctionne avec une liste d’applications de confiance. Les applications incluses dans la liste des logiciels de confiance fonctionnent comme prévu. Les applications qui ne sont pas incluses dans la liste sont empêchées d’apporter des modifications aux fichiers à l’intérieur de dossiers protégés. 

Les applications sont ajoutées à la liste en fonction de leur prévalence et de leur réputation. Les applications qui sont très répandues dans toute votre organisation et qui n’ont jamais affiché de comportement considéré comme malveillant sont considérées comme fiables. Ces applications sont ajoutées automatiquement à la liste.

Les applications peuvent également être ajoutées manuellement à la liste de confiance à l’aide de Configuration Manager ou d’Intune. Des actions supplémentaires, telles que l’ajout d’un [indicateur de fichier](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file) pour une application, peuvent être effectuées à partir de la console du centre de sécurité.

## <a name="why-controlled-folder-access-is-important"></a>Pourquoi l’accès contrôlé aux dossiers est-il important ?

L’accès contrôlé aux dossiers est particulièrement utile pour protéger vos documents et informations contre les [ransomware.](https://www.microsoft.com/wdsi/threats/ransomware) Dans le cas d’une attaque par ransomware, vos fichiers peuvent être chiffrés et maintenus en maison d’amis. Une fois l’accès contrôlé aux dossiers en place, une notification s’affiche sur l’ordinateur sur lequel une application a tenté d’apporter des modifications à un fichier dans un dossier protégé. Vous pouvez [personnaliser la notification](customize-attack-surface-reduction.md#customize-the-notification) avec les informations et les coordonnées de l’entreprise. Vous pouvez également activer les règles individuellement pour personnaliser les techniques analysées par la fonctionnalité.

Les [dossiers protégés incluent les dossiers](#review-controlled-folder-access-events-in-windows-event-viewer) système courants (y compris les secteurs de démarrage) et vous pouvez [ajouter d’autres dossiers.](customize-controlled-folders.md#protect-additional-folders) Vous pouvez également [autoriser les applications](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) à leur donner accès aux dossiers protégés.

Vous pouvez utiliser le [mode audit pour](audit-windows-defender.md) évaluer l’impact de l’accès contrôlé aux dossiers sur votre organisation s’il était activé. Vous pouvez également visiter le site web Windows Defender test au [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que la fonctionnalité fonctionne et voir comment elle fonctionne.

L’accès contrôlé aux dossiers est pris en charge sur les versions suivantes Windows :
- [Windows 10, version 1709 et](/windows/whats-new/whats-new-windows-10-version-1709) ultérieures
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)

## <a name="windows-system-folders-are-protected-by-default"></a>Windows dossiers système sont protégés par défaut

Windows système sont protégés par défaut, ainsi que plusieurs autres dossiers : 

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

> [!NOTE]
> Vous pouvez configurer des dossiers supplémentaires comme étant protégés, mais vous ne pouvez pas supprimer les Windows système qui sont protégés par défaut.

## <a name="requirements-for-controlled-folder-access"></a>Conditions requises pour l’accès contrôlé aux dossiers

L’accès contrôlé aux dossiers [nécessite l’activation Antivirus Microsoft Defender protection en temps réel.](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>Passer en revue les événements d’accès contrôlé aux dossiers dans Microsoft 365 Defender portail

Defender for Endpoint fournit des rapports détaillés sur les événements et les blocages dans le cadre de ses [scénarios](investigate-alerts.md) d’investigation d’alerte dans Microsoft 365 Defender portail. (Voir [Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender.)](../defender/microsoft-365-security-center-mde.md)

Vous pouvez interroger Microsoft Defender pour obtenir des données de point de terminaison à l’aide du [recherche avancée.](/microsoft-365/security/defender-endpoint/advanced-hunting-windows-defender-advanced-threat-protection) Si vous utilisez le [mode audit,](audit-windows-defender.md)vous pouvez utiliser la recherche avancée pour voir comment les paramètres d’accès contrôlé aux dossiers auraient une incidence sur votre environnement s’ils étaient activés. [](advanced-hunting-overview.md)

Exemples de requête :

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Passer en revue les événements d’accès contrôlé aux dossiers dans Windows’observateur d’événements

Vous pouvez consulter le journal Windows événements pour voir les événements créés lorsque l’accès contrôlé aux dossiers bloque (ou audite) une application :

1. Téléchargez le [package d’évaluation](https://aka.ms/mp7z2w) et *extrayez* le fichiercfa-events.xmlun emplacement facilement accessible sur l’appareil.
2. Tapez **l’Observateur** d’événements menu Démarrer pour ouvrir l Windows’observateur d’événements.
3. Dans le panneau gauche, sous **Actions,** **sélectionnez Importer un affichage personnalisé...**.
4. Accédez à l’endroit où *vous avezcfa-events.xml* et sélectionnez-le. Vous pouvez également [copier le XML directement.](event-views.md)
5. Sélectionnez **OK**.

Le tableau suivant indique les événements liés à l’accès contrôlé aux dossiers :

|ID d’événement | Description |
|:---|:---|
|5007 | Événement lorsque les paramètres sont modifiés |
|1124 | Événement d’accès contrôlé aux dossiers audité | 
|1123 | Événement d’accès contrôlé aux dossiers bloqué |

## <a name="view-or-change-the-list-of-protected-folders"></a>Afficher ou modifier la liste des dossiers protégés

Vous pouvez utiliser l’application Sécurité Windows pour afficher la liste des dossiers protégés par un accès contrôlé aux dossiers. 

1. Sur votre Windows 10, ouvrez l’application Sécurité Windows’application.
2. Sélectionnez **Protection contre les virus et les menaces**.
3. Sous Protection **contre les ransomware,** **sélectionnez Gérer la protection contre les ransomware.**
4. Si l’accès contrôlé aux dossiers est désactivé, vous devez l’activer. Sélectionnez **les dossiers protégés.**
5. Effectuez l’une des étapes suivantes :
   - Pour ajouter un dossier, **sélectionnez + Ajouter un dossier protégé.**
   - Pour supprimer un dossier, sélectionnez-le, puis sélectionnez **Supprimer.** 

> [!NOTE]
> [Windows dossiers système](#windows-system-folders-are-protected-by-default) sont protégés par défaut et vous ne pouvez pas les supprimer de la liste.


