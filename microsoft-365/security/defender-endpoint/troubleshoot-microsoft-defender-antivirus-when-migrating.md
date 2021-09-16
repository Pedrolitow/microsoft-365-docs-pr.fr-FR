---
title: Résoudre des problèmes de l’antivirus Microsoft Defender lors de la migration à partir d’une solution tierce
description: Résoudre les erreurs courantes lors de la migration vers Antivirus Microsoft Defender
keywords: événement, code d’erreur, journalisation, résolution des problèmes, antivirus microsoft defender, antivirus windows defender, migration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
ms.topic: article
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.date: 09/11/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 337f034dced0cad5d483b55fa279a7b220fb8e72
ms.sourcegitcommit: 4740e69326eb7f8302eec7bab5bd516d498e4492
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2021
ms.locfileid: "59401577"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Résoudre des problèmes de l’antivirus Microsoft Defender lors de la migration à partir d’une solution tierce

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)


Vous trouverez de l’aide ici si vous rencontrez des problèmes lors de la migration d’une solution de sécurité tierce vers Antivirus Microsoft Defender.

## <a name="review-event-logs"></a>Passer en revue les journaux des événements

Ouvrez l’application Observateur  d’événements en sélectionnant l’icône Rechercher dans la barre des tâches et en recherchant l’Observateur *d’événements.*

Des informations sur Antivirus Microsoft Defender sont disponibles sous **Journaux** des applications et des services \> **Microsoft** \> **Windows** \> **Windows Defender**.

À partir de là, **sélectionnez Ouvrir** sous **Opérationnel.**

La sélection d’un événement dans le volet d’informations vous permet d’obtenir plus d’informations sur un événement dans le volet inférieur, sous les **onglets** Général et Détails. 

## <a name="microsoft-defender-antivirus-wont-start"></a>Antivirus Microsoft Defender ne démarre pas

Ce problème peut se manifester sous la forme de plusieurs ID d’événement différents, qui ont tous la même cause sous-jacente.

### <a name="associated-event-ids"></a>ID d’événement associés

ID d’événement|Nom du journal|Description|Source
---|---|---|---
15 |Application|Mise à jour Windows Defender statut de l’SECURITY_PRODUCT_STATE_OFF.|Centre de sécurité
5007|Microsoft-Windows-Windows Defender/Opérationnel|Antivirus Windows Defender La configuration a changé. S’il s’agit d’un événement inattendu, vous devez passer en revue les paramètres, car cela peut être le résultat d’un programme malveillant. <p> **Ancienne valeur :** Default\IsServiceRunning = 0x0 <p> **Nouvelle valeur :** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Opérationnel|Antivirus Windows Defender recherche de logiciels espions et d’autres logiciels potentiellement indésirables est désactivée.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Comment savoir si Antivirus Microsoft Defender ne démarre pas car un antivirus tiers est installé

Sur un Windows 10, si vous n’utilisez pas Microsoft Defender pour Endpoint et qu’un antivirus tiers est installé, Antivirus Microsoft Defender sera automatiquement désactivé. Si vous utilisez Microsoft Defender pour Endpoint avec un antivirus tiers installé, Antivirus Microsoft Defender démarrera en mode passif, avec des fonctionnalités réduites.

> [!TIP]
> Le scénario décrit s’applique uniquement aux Windows 10. D’autres versions Windows [ont des réponses différentes aux](microsoft-defender-antivirus-compatibility.md) Antivirus Microsoft Defender en cours d’utilisation avec des logiciels de sécurité tiers.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Utiliser l’application Services pour vérifier si Antivirus Microsoft Defender est désactivé

Pour ouvrir l’application Services, sélectionnez l’icône **Rechercher** dans la barre des tâches et recherchez des *services.* Vous pouvez également ouvrir l’application à partir de la ligne de commande en tapant *services.msc*.

Les informations sur Antivirus Microsoft Defender seront répertoriées dans l’application Services sous **Windows Defender** \> **Opérationnel**. Le nom du service antivirus *est Antivirus Windows Defender Service.*

Lors de la vérification de l’application, vous pouvez voir que le service *Antivirus Windows Defender* est prêt à être démarré manuellement, mais lorsque vous essayez de démarrer ce service manuellement, vous recevez un avertissement indiquant que le service Antivirus Windows Defender sur l’ordinateur local a démarré, puis s’est *arrêté. Certains services s’arrêtent automatiquement s’ils ne sont pas utilisés par d’autres services ou programmes.*

Cela indique que la Antivirus Microsoft Defender a été automatiquement désactivée pour préserver la compatibilité avec un antivirus tiers.

#### <a name="generate-a-detailed-report"></a>Générer un rapport détaillé

Vous pouvez générer un rapport détaillé sur les stratégies de groupe actives en ouvrant une invite de commandes en **mode** d’administration, puis en entrant la commande suivante :

```powershell
GPresult.exe /h gpresult.html
```

Cela génère un rapport situé à *l’emplacement ./gpresult.html*. Ouvrez ce fichier et vous pouvez voir les résultats suivants, selon la façon dont Antivirus Microsoft Defender été désactivé.

##### <a name="group-policy-results"></a>Résultats de la stratégie de groupe

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Si les paramètres de sécurité sont implémentés via la stratégie de groupe (GPO) au niveau du domaine ou au niveau local, ou via System Center Configuration Manager (SCCM)

Dans le rapport GPResults, sous le titre *Windows Components/Antivirus Windows Defender*, vous pouvez voir quelque chose comme l’entrée suivante, indiquant que Antivirus Microsoft Defender est désactivé.

Stratégie|Paramètre|GPO qui a été gagné
---|---|---
Désactiver la Antivirus Windows Defender|Activé|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Si les paramètres de sécurité sont implémentés via la stratégie de groupe de préférence (GPP)

Sous le titre, élément de Registre (chemin d’accès clé : HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Nom de la valeur : *DisableAntiSpyware)*, vous pouvez voir quelque chose comme l’entrée suivante, indiquant que Antivirus Microsoft Defender est désactivé.

DisableAntiSpyware|-
---|---
GPO qui a été gagné|Win10-Workstations
Résultat : réussite|
**Général**|
Action|Update
**Propriétés**|
Ruche|HKEY_LOCAL_MACHINE
Chemin d’accès de la touche|SOFTWARE\Policies\Microsoft\Windows Defender
Nom de la valeur|DisableAntiSpyware
Type de valeur|REG_DWORD
Données de la valeur|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Si les paramètres de sécurité sont implémentés via la clé de Registre

Le rapport peut contenir le texte suivant, indiquant que la Antivirus Microsoft Defender est désactivée :

> Registre (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Si les paramètres de sécurité sont Windows ou votre image Windows Server

Votre administrateur imaginant peut avoir définie la stratégie de **[sécurité, DisableAntiSpyware,](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** localement via *GPEdit.exe*, *LGPO.exe* ou en modifiant le Registre dans leur séquence de tâches. Vous pouvez [configurer un identificateur d’image approuvé](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) pour Antivirus Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Activer Antivirus Microsoft Defender l’autre

Antivirus Microsoft Defender s’active automatiquement si aucun autre antivirus n’est actif. Vous devez désactiver complètement l’antivirus tiers pour vous assurer Antivirus Microsoft Defender’exécuter avec toutes les fonctionnalités.

> [!WARNING]
> Les solutions qui vous suggèrent de modifier les valeurs de début *Windows Defender* pour *wdboot,* *wdfilter,* *wdnisdrv,* *wdnissvc* et *windefend* dans HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services ne sont pas pris en compte et peuvent vous obliger à ré-imager votre système.

Le mode passif est disponible si vous commencez à utiliser Microsoft Defender pour endpoint et un antivirus tiers avec Antivirus Microsoft Defender. Le mode passif permet à Microsoft Defender d’analyser les fichiers et de se mettre à jour lui-même, mais il ne remédie pas aux menaces. En outre, la surveillance du comportement via [la Protection](configure-real-time-protection-microsoft-defender-antivirus.md) en temps réel n’est pas disponible en mode passif, sauf si la protection contre la perte de données de point de terminaison [(DLP)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) est déployée.

Une autre fonctionnalité, appelée analyse périodique [limitée,](limited-periodic-scanning-microsoft-defender-antivirus.md)est disponible pour les utilisateurs finaux lorsque Antivirus Microsoft Defender est définie pour être automatiquement éteinte. Cette fonctionnalité permet Antivirus Microsoft Defender analyser régulièrement des fichiers avec un antivirus tiers, à l’aide d’un nombre limité de détections.

> [!IMPORTANT]
> L’analyse périodique limitée n’est pas recommandée dans les environnements d’entreprise. Les fonctionnalités de détection, de gestion et de rapport disponibles lors de l’Antivirus Microsoft Defender dans ce mode sont réduites par rapport au mode actif.

### <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender compatibilité](microsoft-defender-antivirus-compatibility.md)
- [Antivirus Microsoft Defender dans l’application Sécurité Windows de messagerie](microsoft-defender-security-center-antivirus.md)
