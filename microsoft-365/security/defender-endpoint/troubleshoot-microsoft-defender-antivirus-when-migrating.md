---
title: Résoudre les problèmes de l'Antivirus Microsoft Defender lors de la migration à partir d'une solution tierce
description: Résoudre les erreurs courantes lors de la migration vers l'Antivirus Microsoft Defender
keywords: événement, code d'erreur, journalisation, résolution des problèmes, antivirus microsoft defender, antivirus windows defender, migration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.date: 09/11/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 2ca486b86c24e18ae08753b5e88f2eb42986dddf
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690657"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Résoudre les problèmes de l'Antivirus Microsoft Defender lors de la migration à partir d'une solution tierce

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)


Vous trouverez de l'aide ici si vous rencontrez des problèmes lors de la migration d'une solution de sécurité tierce vers l'Antivirus Microsoft Defender.

## <a name="review-event-logs"></a>Passer en revue les journaux des événements

Ouvrez l'application Observateur  d'événements en sélectionnant l'icône Rechercher dans la barre des tâches et en recherchant l'Observateur *d'événements.*

Vous pouvez trouver des informations sur l'Antivirus Microsoft Defender sous **Journaux des applications** et des services  >  **Microsoft**  >  **Windows**  >  **Windows Defender**. 

À partir de là, **sélectionnez Ouvrir** sous **Opérationnel.**

La sélection d'un événement dans le volet d'informations vous permet d'obtenir plus d'informations sur un événement dans le volet inférieur, sous les **onglets** Général et Détails. 

## <a name="microsoft-defender-antivirus-wont-start"></a>L'Antivirus Microsoft Defender ne démarre pas

Ce problème peut se manifester sous la forme de plusieurs ID d'événement différents, qui ont tous la même cause sous-jacente.

### <a name="associated-event-ids"></a>ID d'événement associés

 ID de l'événement | Nom du journal | Description | Source
-|-|-|-
15  | Application | Mise à jour Windows Defender statut de l'SECURITY_PRODUCT_STATE_OFF. | Centre de sécurité
5007 | Microsoft-Windows-Windows Defender/Opérationnel | Windows Defender'antivirus a changé.  S'il s'agit d'un événement inattendu, vous devez passer en revue les paramètres, car cela peut être le résultat d'un programme malveillant.<br /><br />**Ancienne valeur :** Default\IsServiceRunning = 0x0<br />**Nouvelle valeur :** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1 | Windows Defender
5010 | Microsoft-Windows-Windows Defender/Opérationnel | Windows Defender antivirus pour les logiciels espions et autres logiciels potentiellement indésirables est désactivé. | Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Comment savoir si l'Antivirus Microsoft Defender ne démarre pas car un antivirus tiers est installé

Sur un appareil Windows 10, si vous n'utilisez pas Microsoft Defender pour Endpoint et qu'un antivirus tiers est installé, l'Antivirus Microsoft Defender est automatiquement désactivé. Si vous utilisez Microsoft Defender pour Endpoint avec un antivirus tiers installé, l'Antivirus Microsoft Defender démarre en mode passif, avec des fonctionnalités réduites.

> [!TIP]
> Le scénario décrit s'applique uniquement à Windows 10. D'autres versions de Windows [ont des réponses différentes à](microsoft-defender-antivirus-compatibility.md) l'Antivirus Microsoft Defender en cours d'utilisation avec un logiciel de sécurité tiers.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Utiliser l'application Services pour vérifier si l'Antivirus Microsoft Defender est désactivé

Pour ouvrir l'application Services, sélectionnez l'icône **Rechercher** dans la barre des tâches et recherchez des *services.* Vous pouvez également ouvrir l'application à partir de la ligne de commande en tapant *services.msc*.

Les informations sur l'Antivirus Microsoft Defender sont répertoriées dans l'application Services sous **Windows Defender**  >  **Opérationnel**. Le nom du service antivirus *est Windows Defender antivirus.*

Lors de la vérification de l'application, vous pouvez constater que le service *antivirus Windows Defender* est prêt à être démarré manuellement, mais lorsque vous essayez de démarrer ce service manuellement, vous recevez un avertissement indiquant que le service antivirus Windows Defender a démarré sur l'ordinateur local, puis s'est *arrêté. Certains services s'arrêtent automatiquement s'ils ne sont pas utilisés par d'autres services ou programmes.*

Cela indique que l'Antivirus Microsoft Defender a été automatiquement désactivé pour préserver la compatibilité avec un antivirus tiers.

#### <a name="generate-a-detailed-report"></a>Générer un rapport détaillé

Vous pouvez générer un rapport détaillé sur les stratégies de groupe actives en ouvrant une invite de commandes en **mode** d'administration, puis en entrant la commande suivante :

```powershell
GPresult.exe /h gpresult.html
```

Cela génère un rapport situé sur *./gpresult.html*. Ouvrez ce fichier et vous pouvez voir les résultats suivants, selon la façon dont l'Antivirus Microsoft Defender a été désactivé.

##### <a name="group-policy-results"></a>Résultats de la stratégie de groupe

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Si les paramètres de sécurité sont implémentés via la stratégie de groupe (GPO) au niveau du domaine ou au niveau local, ou via System Center Configuration Manager (SCCM)

Dans le rapport GPResults, sous le titre *Composants Windows/Antivirus Windows Defender*, vous pouvez voir quelque chose comme l'entrée suivante, indiquant que l'Antivirus Microsoft Defender est désactivé.

Stratégie | Paramètre | GPO qui a été gagné
-|-|-
Désactiver l'antivirus Windows Defender | Activé | Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Si les paramètres de sécurité sont implémentés via la stratégie de groupe de préférence (GPP)

Sous l'en-tête, élément de Registre (chemin d'accès clé : HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Nom de la valeur : *DisableAntiSpyware)*, vous pouvez voir quelque chose comme l'entrée suivante, indiquant que l'Antivirus Microsoft Defender est désactivé.

DisableAntiSpyware | -
-|-
GPO qui a été gagné | Win10-Workstations
Résultat : réussite | 
**Général** | 
Action | Update
**Propriétés** | 
Ruche | HKEY_LOCAL_MACHINE
Chemin d'accès de la touche | SOFTWARE\Policies\Microsoft\Windows Defender
Nom de la valeur | DisableAntiSpyware
Type de valeur | REG_DWORD
Données de la valeur | 0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Si les paramètres de sécurité sont implémentés via la clé de Registre

Le rapport peut contenir le texte suivant, indiquant que l'Antivirus Microsoft Defender est désactivé :
 
> Registre (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Si les paramètres de sécurité sont définies dans Windows ou votre image Windows Server

Votre administrateur imaginant peut avoir définie la stratégie de **[sécurité, DisableAntiSpyware,](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** localement via *GPEdit.exe*, *LGPO.exe* ou en modifiant le Registre dans leur séquence de tâches. Vous pouvez [configurer un identificateur d'image approuvé](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) pour l'Antivirus Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Activer de nouveau l'Antivirus Microsoft Defender

L'Antivirus Microsoft Defender s'active automatiquement si aucun autre antivirus n'est actif. Vous devez désactiver complètement l'antivirus tiers pour vous assurer que l'Antivirus Microsoft Defender peut s'exécuter avec toutes les fonctionnalités.

> [!WARNING]
> Les solutions qui vous suggèrent de modifier les valeurs de début *Windows Defender* pour *wdboot,* *wdfilter,* *wdnisdrv*, *wdnissvc* et *windefend* dans HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services ne sont pas pris en compte et peuvent vous obliger à ré-imager votre système.

Le mode passif est disponible si vous commencez à utiliser Microsoft Defender pour Endpoint et un antivirus tiers avec l'Antivirus Microsoft Defender. Le mode passif permet à Microsoft Defender d'analyser les fichiers et de se mettre à jour lui-même, mais il ne remédie pas aux menaces. En outre, la surveillance du comportement via [la Protection](configure-real-time-protection-microsoft-defender-antivirus.md) en temps réel n'est pas disponible en mode passif, sauf si la protection contre la perte de données de point de terminaison [(DLP)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) est déployée.

Une autre fonctionnalité, appelée analyse périodique [limitée,](limited-periodic-scanning-microsoft-defender-antivirus.md)est disponible pour les utilisateurs finaux lorsque l'Antivirus Microsoft Defender est automatiquement éteint. Cette fonctionnalité permet à l'Antivirus Microsoft Defender d'analyser régulièrement des fichiers avec un antivirus tiers, à l'aide d'un nombre limité de détections.

> [!IMPORTANT]
> L'analyse périodique limitée n'est pas recommandée dans les environnements d'entreprise. Les fonctionnalités de détection, de gestion et de rapport disponibles lors de l'exécution de l'Antivirus Microsoft Defender dans ce mode sont réduites par rapport au mode actif.

### <a name="see-also"></a>Voir aussi

* [Compatibilité de l'Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md)
* [Antivirus Microsoft Defender dans l'application Sécurité Windows](microsoft-defender-security-center-antivirus.md)