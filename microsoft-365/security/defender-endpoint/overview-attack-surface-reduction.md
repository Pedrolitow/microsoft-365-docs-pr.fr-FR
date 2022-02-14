---
title: Comprendre et utiliser la réduction de la surface d’attaque (ASR)
ms.reviewer: ''
description: Découvrez les fonctionnalités de réduction de la surface d’attaque de Microsoft Defender pour point de terminaison.
keywords: asr, réduction de la surface d’attaque, Microsoft Defender pour point de terminaison, microsoft defender, antivirus, av, windows defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.custom: asr
ms.topic: conceptual
ms.technology: mde
ms.collection: m365initiative-m365-defender
ms.date: 1/18/2022
ms.openlocfilehash: 78fdd5c6c02990943874807c285f8e5eb60ad6ad
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62807583"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>Comprendre et utiliser les fonctionnalités de réduction de la surface d’attaque

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Les surfaces d’attaque sont tous les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. Defender pour le point de terminaison inclut plusieurs fonctionnalités pour réduire vos surfaces d’attaque. Regardez la vidéo suivante pour en savoir plus sur la réduction de la surface d’attaque.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>Configurer les fonctionnalités de la réduction de la surface d’attaque

Pour configurer la réduction de la surface d’attaque dans votre environnement, suivez les étapes suivantes :

1. [Activez l’isolation matérielle pour Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. Activer le contrôle d’application.

   1. Passer en revue les stratégies de base Windows. Voir [exemples de stratégies de base](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. Consultez le [Windows Defender de conception du contrôle d’application](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. [Reportez-vous au Déploiement Windows Defender de contrôle d’application (WDAC).](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)

3. [Activer l’accès contrôlé aux dossiers](enable-controlled-folders.md).

4. [Activer la protection du réseau](enable-network-protection.md).

5. [Activez Exploit Protection](enable-exploit-protection.md).

6. [Déployer des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-deployment.md).

7. Configurer votre pare-feu réseau.

   1. Obtenez une vue d’ensemble [Windows Defender pare-feu avec une sécurité avancée](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. Utilisez le [guide Windows Defender pare-feu](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) pour déterminer la façon dont vous souhaitez concevoir vos stratégies de pare-feu.
   3. Utilisez le [guide Windows Defender pare-feu](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) pour configurer le pare-feu de votre organisation avec une sécurité avancée.

> [!TIP]
> Dans la plupart des cas, lorsque vous configurez des fonctionnalités de réduction de la surface d’attaque, vous pouvez choisir parmi plusieurs méthodes :
>
> - Microsoft Endpoint Manager (qui inclut désormais Microsoft Intune et Microsoft Endpoint Configuration Manager)
> - Stratégie de groupe
> - Cmdlets PowerShell

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Tester la réduction de la surface d’attaque dans Microsoft Defender pour le point de terminaison

Dans le cadre de l’équipe de sécurité de votre organisation, vous pouvez configurer les fonctionnalités de réduction de la surface d’attaque pour qu’elles s’exécutent en mode audit pour voir comment elles fonctionneront. En mode audit, vous pouvez activer :

- Règles de réduction de la surface d’attaque
- Exploit Protection
- Protection réseau
- Accès contrôlé aux dossiers en mode audit

Le mode audit vous permet d’enregistrer ce qui  se serait passé si vous aviez activé la fonctionnalité.

Vous pouvez activer le mode audit lors du test du fonctionnement des fonctionnalités. L’activation du mode audit uniquement pour les tests permet d’empêcher le mode audit d’affecter vos applications métier. Vous pouvez également avoir une idée du nombre de tentatives de modification de fichier suspectes qui se produisent sur une certaine période de temps.

Les fonctionnalités ne bloquent pas ou n’empêchent pas les applications, les scripts ou les fichiers d’être modifiés. Toutefois, le Windows journal des événements enregistre les événements comme si les fonctionnalités étaient entièrement activées. Avec le mode audit, vous pouvez consulter le journal des événements pour voir l’impact que la fonctionnalité aurait eu si elle avait été activée.

Pour rechercher les entrées auditées, allez à **Applications et services** \> **Microsoft** \> **Windows** \> **Windows Defender** \> **Opérationnel**.

Utilisez Defender pour le point de terminaison pour obtenir plus de détails pour chaque événement. Ces détails sont particulièrement utiles pour examiner les règles de réduction de la surface d’attaque. L’utilisation de la console Defender for Endpoint vous permet d’examiner les problèmes dans le cadre de la chronologie des [alertes et des scénarios d’enquête](investigate-alerts.md).

Vous pouvez activer le mode audit à l’aide de la stratégie de groupe, de PowerShell et des fournisseurs de services de configuration (CSP).

> [!TIP]
> Vous pouvez également visiter le site Windows Defender Testground sur [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités fonctionnent et voir comment elles fonctionnent.

> [!NOTE]
> Le site de démonstration Defender for Endpoint demo.wd.microsoft.com est supprimé et sera supprimé à l’avenir.

| Options d’audit | Comment activer le mode audit | Comment afficher les événements |
|---|---|---|
| L’audit s’applique à tous les événements | [Activer l’accès contrôlé aux dossiers](enable-controlled-folders.md) | [Événements d’accès contrôlé aux dossiers](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| L’audit s’applique à des règles individuelles | [Étape 1 : Tester les règles de la asr à l’aide de l’audit](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [Étape 2 : Comprendre la page de rapports sur les règles de réduction de la surface d’attaque](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| L’audit s’applique à tous les événements | [Activer la protection du réseau](enable-network-protection.md) | [Événements de protection du réseau](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| L’audit s’applique aux atténuations individuelles | [Activer la protection la protection contre les codes malveillants exploitant une faille de sécurité](enable-exploit-protection.md) | [Événements Exploit Protection](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

## <a name="view-attack-surface-reduction-events"></a>Afficher les événements de la réduction de la surface d’attaque

Examinez les événements de réduction de la surface d’attaque dans l’Observateur d’événements pour surveiller les règles ou paramètres qui fonctionnent. Vous pouvez également déterminer si des paramètres sont trop « bruyants » ou ont un impact sur votre flux de travail quotidien.

La révision des événements est pratique lorsque vous évaluez les fonctionnalités. Vous pouvez activer le mode audit pour les fonctionnalités ou les paramètres, puis passer en revue ce qui se serait passé s’ils étaient entièrement activés.

Cette section répertorie tous les événements, leurs fonctionnalités ou paramètres associés, et explique comment créer des affichages personnalisés pour filtrer des événements spécifiques.

Obtenez des rapports détaillés sur les événements, les blocs et les avertissements dans le cadre de Sécurité Windows si vous avez un abonnement E5 et utilisez [Microsoft Defender pour endpoint](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>Utiliser des affichages personnalisés pour examiner les fonctionnalités de réduction de la surface d’attaque

Créez des affichages personnalisés dans Windows’observateur d’événements pour voir uniquement les événements pour des fonctionnalités et des paramètres spécifiques. Le moyen le plus simple consiste à importer un affichage personnalisé en tant que fichier XML. Vous pouvez copier le XML directement à partir de cette page.

Vous pouvez également accéder manuellement à la zone d’événement qui correspond à la fonctionnalité.

#### <a name="import-an-existing-xml-custom-view"></a>Importer un affichage personnalisé XML existant

1. Créez un fichier .txt vide et copiez le fichier XML de l’affichage personnalisé que vous souhaitez utiliser dans .txt fichier. Faites-le pour chacun des affichages personnalisés que vous souhaitez utiliser. Renommez les fichiers comme suit (assurez-vous de modifier le type de .txt en .xml) :
    - Affichage personnalisé des événements d’accès *contrôlé aux dossiers :cfa-events.xml*
    - Vue personnalisée des événements Exploit Protection *:ep-events.xml*
    - Affichage personnalisé des événements de réduction de la surface *d’attaque :asr-events.xml*
    - Affichage personnalisé des événements réseau/protection *:np-events.xml*

2. Tapez **l’Observateur** d’événements menu Démarrer et ouvrez **l’Observateur d’événements**.

3. Sélectionner **l’affichage personnalisé** \> **d’importation d’action...**

   > [!div class="mx-imgBorder"]
   > ![Animation mettant en surbrillance l’importation d’un affichage personnalisé à gauche de la fenêtre visionneuse even.](images/events-import.gif)

4. Accédez à l’endroit où vous avez extrait le fichier XML pour l’affichage personnalisé que vous souhaitez, puis sélectionnez-le.

5. Sélectionnez **Ouvrir**.

6. Il crée un affichage personnalisé qui filtre pour afficher uniquement les événements liés à cette fonctionnalité.

#### <a name="copy-the-xml-directly"></a>Copier le XML directement

1. **Tapez l’Observateur** d’événements menu Démarrer et ouvrez l’observateur Windows **événements**.

2. Dans le panneau gauche, sous **Actions**, **sélectionnez Créer un affichage personnalisé...**

   > [!div class="mx-imgBorder"]
   > ![Animation mettant en surbrillance l’option créer un affichage personnalisé dans la fenêtre de l’Observateur d’événements.](images/events-create.gif)

3. Go to the XML tab and select **Edit query manually**. Vous verrez un avertissement vous signalant que vous ne pouvez pas modifier la requête à l’aide de l’onglet Filtre si vous utilisez l’option XML. Sélectionnez **Oui**.

4. Collez le code XML de la fonctionnalité dont vous souhaitez filtrer les événements dans la section XML.

5. Sélectionnez **OK**. Spécifiez un nom pour votre filtre. Cela crée un affichage personnalisé qui filtre pour afficher uniquement les événements liés à cette fonctionnalité.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>XML pour les événements de règle de réduction de la surface d’attaque

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>XML pour les événements d’accès contrôlé aux dossiers

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-exploit-protection-events"></a>XML pour les événements Exploit Protection

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Security-Mitigations/KernelMode">
   <Select Path="Microsoft-Windows-Security-Mitigations/KernelMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Concurrency">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Contention">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Messages">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Operational">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Power">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Render">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Tracing">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/UIPI">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="System">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Security-Mitigations/UserMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-network-protection-events"></a>XML pour les événements de protection réseau

```xml
<QueryList>
 <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
  <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
  <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
 </Query>
</QueryList>
```

### <a name="list-of-attack-surface-reduction-events"></a>Liste des événements de réduction de la surface d’attaque

Tous les événements de réduction de la surface d’attaque se trouvent sous Journaux des applications et des **services > Microsoft > Windows**, puis dans le dossier ou le fournisseur répertoriés dans le tableau suivant.

Vous pouvez accéder à ces événements dans l Windows’observateur d’événements :

1. Ouvrez le menu **Démarrer** et tapez **l’Observateur** d’événements, puis sélectionnez le résultat de **l’Observateur d’événements** .
2. **Développez Journaux des applications et des services > Microsoft > Windows** puis allez dans le dossier répertorié sous Fournisseur **/source** dans le tableau ci-dessous.
3. Double-cliquez sur le sous-élément pour voir les événements. Faites défiler les événements pour trouver celui que vous recherchez.

   ![Animation montrant l’utilisation de l’Observateur d’événements.](images/event-viewer.gif)

<br>

****

|Fonctionnalité|Fournisseur/source|ID d’événement|Description|
|---|---|:---:|---|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|1|Audit ACG|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|2|Forcer ACG|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|3|Ne pas autoriser l’audit des processus enfants|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|4|Ne pas autoriser le blocage des processus enfants|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|5|Bloquer l’audit des images à faible intégrité|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|6 |Bloquer le blocage des images à faible intégrité|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|7 |Bloquer l’audit des images distantes|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|8 |Bloquer le blocage des images distantes|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|9 |Désactiver l’audit des appels système win32k|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|10|Désactiver le blocage des appels système win32k|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|11|Audit de la protection d’intégrité du code|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|12 |Blocage de la protection d’intégrité du code|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|13|Audit EAF|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|14 |Forcer EAF|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|15 |Audit EAF+|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|16|Forcer EAF+|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|17 |Audit IAF|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|18 |Forcer IAF|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|19|Audit de StackPivot ROP|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|20|Forcer StackPivot ROP|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)| 21|Audit de CallerCheck ROP|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|22|Forcer CallerCheck ROP|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|23|Audit de SimExec ROP|
|Exploit Protection|Security-Mitigations (mode noyau/mode utilisateur)|24|Forcer SimExec ROP|
|Exploit Protection|WER-Diagnostics|5|Bloquer CFG|
|Exploit Protection|Win32K (opérationnel)|260|Police non approuvée|
|Protection réseau|Windows Defender (opérationnel)|5007|Événement lorsque les paramètres sont modifiés|
|Protection réseau|Windows Defender (opérationnel)|1125|Événement lorsque la protection du réseau se déclenche en mode audit|
|Protection réseau|Windows Defender (opérationnel)|1126|Événement lorsque la protection du réseau se déclenche en mode blocage|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|5007|Événement lorsque les paramètres sont modifiés|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1124|Événement d’accès contrôlé aux dossiers audité|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1123|Événement d’accès contrôlé aux dossiers bloqué|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1127|Événement bloqué de bloc d’écriture de secteur d’accès contrôlé aux dossiers|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1128|Événement de bloc d’écriture du secteur d’accès contrôlé aux dossiers audité|
|Réduction de la surface d'attaque|Windows Defender (opérationnel)|5007|Événement lorsque les paramètres sont modifiés|
|Réduction de la surface d'attaque|Windows Defender (opérationnel)|1122|Événement lorsque la règle se déclenche en mode audit|
|Réduction de la surface d'attaque|Windows Defender (opérationnel)|1121|Événement lorsque la règle se déclenche en mode blocage|

>[!NOTE]
> Du point de vue de l’utilisateur, les notifications en mode avertissement de la réduction de la surface d’attaque sont Windows notification toast pour les règles de réduction de la surface d’attaque.
>
> Dans la protection du réseau, la protection du réseau fournit uniquement les modes Audit et Blocage.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>Ressources pour en savoir plus sur la réduction de la surface d’attaque

Comme mentionné dans la vidéo, Defender pour le point de terminaison inclut plusieurs fonctionnalités de réduction de la surface d’attaque. Pour en savoir plus, utilisez les ressources suivantes :

| Article | Description |
|:---|:---|
| [Isolation basée sur le matériel](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | Protégez et maintenez l’intégrité d’un système au démarrage et pendant son exécution. Valider l’intégrité du système par le biais d’une attestation locale et distante. Utilisez l’isolation de conteneur pour Microsoft Edge pour vous protéger contre les sites web malveillants. |
| [Contrôle d’application](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | Utilisez le contrôle d’application pour que vos applications gagnent en confiance pour pouvoir s’exécuter. |
| [Accès contrôlé aux dossiers](controlled-folders.md) | Empêcher les applications malveillantes ou suspectes (y compris les programmes malveillants de ransomware de chiffrement de fichiers) d’apporter des modifications aux fichiers dans vos dossiers système clés (nécessite Antivirus Microsoft Defender) |
| [Protection du réseau](network-protection.md) | Étendez la protection au trafic réseau et à la connectivité sur les appareils de votre organisation. (Nécessite une Antivirus Microsoft Defender) |
| [Exploit Protection](exploit-protection.md) | Protéger les systèmes d’exploitation et les applications que votre organisation utilise contre l’exploitation. Exploit Protection fonctionne également avec des solutions antivirus tierces. |
| [Règles de réduction de la surface d’attaque](attack-surface-reduction.md) | Réduisez les vulnérabilités (surfaces d’attaque) de vos applications grâce à des règles intelligentes qui permettent d’arrêter le programme malveillant. (Nécessite une Antivirus Microsoft Defender). |
| [Contrôle des appareils](device-control-report.md) | Protège contre la perte de données en surveillant et en contrôlant les médias utilisés sur les appareils, tels que le stockage amovible et les lecteurs USB, dans votre organisation. |
