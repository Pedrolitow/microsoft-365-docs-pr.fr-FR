---
title: Comprendre et utiliser la réduction de la surface d’attaque (ASR)
ms.reviewer: ''
description: Découvrez les fonctionnalités de réduction de la surface d’attaque de Microsoft Defender pour point de terminaison.
keywords: asr, réduction de la surface d’attaque, règles de réduction de la surface d’attaque, Microsoft Defender pour point de terminaison, microsoft defender, antivirus, av, windows defender
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
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 5b71134f9a7d33880e9762701e825c3fbf708f6b
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705082"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>Comprendre et utiliser les fonctionnalités de réduction de la surface d’attaque

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Les surfaces d’attaque sont tous les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. Defender pour point de terminaison inclut plusieurs fonctionnalités pour réduire vos surfaces d’attaque. Regardez la vidéo suivante pour en savoir plus sur la réduction de la surface d’attaque.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>Configurer les fonctionnalités de la réduction de la surface d’attaque

Pour configurer la réduction de la surface d’attaque dans votre environnement, procédez comme suit :

1. [Activez l’isolation matérielle pour Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. Activez le contrôle d’application.

   1. Passez en revue les stratégies de base dans Windows. Consultez [les exemples de stratégies de base](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. Consultez le [guide de conception Windows Defender Application Control](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. Reportez-vous au [déploiement de stratégies de contrôle d’application Windows Defender (WDAC](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)).

3. [Activez l’accès contrôlé aux dossiers](enable-controlled-folders.md).

4. [Activez la protection réseau](enable-network-protection.md).

5. [Activez la protection contre les attaques](enable-exploit-protection.md).

6. [Déployez des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-deployment.md).

7. Configurez votre pare-feu réseau.

   1. Obtenez une vue d’ensemble du [pare-feu Windows Defender avec une sécurité avancée](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. Utilisez le [guide de conception du pare-feu Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) pour décider de la façon dont vous souhaitez concevoir vos stratégies de pare-feu.
   3. Utilisez le [guide de déploiement du pare-feu Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) pour configurer le pare-feu de votre organisation avec une sécurité avancée.

> [!TIP]
> Dans la plupart des cas, lorsque vous configurez des fonctionnalités de réduction de la surface d’attaque, vous pouvez choisir parmi plusieurs méthodes :
>
> - Microsoft Endpoint Manager (qui inclut désormais Microsoft Intune et Microsoft Endpoint Configuration Manager)
> - Stratégie de groupe
> - Cmdlets PowerShell

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Tester la réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison

Dans le cadre de l’équipe de sécurité de votre organisation, vous pouvez configurer les fonctionnalités de réduction de la surface d’attaque pour qu’elles s’exécutent en mode audit pour voir comment elles fonctionnent. Vous pouvez activer les fonctionnalités de sécurité ASR suivantes en mode audit :

- Règles de réduction des surfaces d'attaque
- Exploit Protection
- Protection réseau
- Accès contrôlé aux dossiers

Le mode Audit vous permet de voir un enregistrement de ce qui *se serait* passé si vous aviez activé la fonctionnalité.

Vous pouvez activer le mode audit lors du test du fonctionnement des fonctionnalités. L’activation du mode d’audit uniquement pour les tests permet d’empêcher le mode audit d’affecter vos applications métier. Vous pouvez également avoir une idée du nombre de tentatives de modification de fichier suspectes qui se produisent sur une certaine période de temps.

Les fonctionnalités ne bloquent pas ou n’empêchent pas la modification d’applications, de scripts ou de fichiers. Toutefois, le journal des événements Windows enregistre les événements comme si les fonctionnalités étaient entièrement activées. Avec le mode audit, vous pouvez passer en revue le journal des événements pour voir quel impact la fonctionnalité aurait eue si elle était activée.

Pour rechercher les entrées auditées, accédez à **Applications et Services** \> **Microsoft** \> **Windows** \> **Windows Defender** \> **Operational**.

Utilisez Defender pour point de terminaison pour obtenir plus de détails pour chaque événement. Ces détails sont particulièrement utiles pour examiner les règles de réduction de la surface d’attaque. L’utilisation de la console Defender pour point de terminaison vous permet [d’examiner les problèmes dans le cadre de la chronologie des alertes et des scénarios d’investigation](investigate-alerts.md).

Vous pouvez activer le mode audit à l’aide de stratégie de groupe, PowerShell et des fournisseurs de services de configuration (CSP).

> [!TIP]
> Vous pouvez également visiter le site web Windows Defender Testground à [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités fonctionnent et voir comment elles fonctionnent.

> [!NOTE]
> Le site de démonstration Defender pour point de terminaison sur demo.wd.microsoft.com est déconseillé et sera supprimé à l’avenir.

| Options d’audit | Comment activer le mode audit | Comment afficher des événements |
|---|---|---|
| L’audit s’applique à tous les événements | [Activer l’accès contrôlé aux dossiers](enable-controlled-folders.md) | [Événements d’accès contrôlé aux dossiers](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| L’audit s’applique à des règles individuelles | [Étape 1 : Tester des règles ASR à l’aide du mode Audit](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [Étape 2 : Comprendre la page de création de rapports sur les règles de réduction de la surface d’attaque](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| L’audit s’applique à tous les événements | [Activer la protection réseau](enable-network-protection.md) | [Événements de protection réseau](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| L’audit s’applique aux atténuations individuelles | [Activer la protection la protection contre les codes malveillants exploitant une faille de sécurité](enable-exploit-protection.md) | [Exploiter les événements de protection](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

### <a name="attack-surface-reduction-asr-rules"></a>Règles de réduction de la surface d’attaque (ASR)

Les règles de réduction de la surface d’attaque (ASR) sont prédéfinies pour renforcer les surfaces d’attaque courantes et connues. Il existe plusieurs méthodes que vous pouvez utiliser pour implémenter des règles de réduction de la surface d’attaque. La méthode recommandée est documentée dans les rubriques de déploiement des règles de réduction de la surface d’attaque (ASR) suivantes :

- [Vue d’ensemble du déploiement des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment.md)
- [Planifier le déploiement de règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-plan.md)
- [Tester les règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-test.md)
- [Activer les règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-implement.md)
- [Opérationnaliser les règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="view-attack-surface-reduction-events"></a>Afficher les événements de la réduction de la surface d’attaque

Passez en revue les événements de réduction de la surface d’attaque dans observateur d'événements pour surveiller les règles ou paramètres qui fonctionnent. Vous pouvez également déterminer si des paramètres sont trop « bruyants » ou affectent votre flux de travail quotidien.

L’examen des événements est pratique lorsque vous évaluez les fonctionnalités. Vous pouvez activer le mode d’audit pour les fonctionnalités ou les paramètres, puis examiner ce qui se serait passé s’ils étaient entièrement activés.

Cette section répertorie tous les événements, leur fonctionnalité ou paramètre associé, et explique comment créer des vues personnalisées à filtrer sur des événements spécifiques.

Obtenez des rapports détaillés sur les événements, les blocs et les avertissements dans le cadre de Sécurité Windows si vous disposez d’un abonnement E5 et que vous utilisez [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>Utiliser des vues personnalisées pour passer en revue les fonctionnalités de réduction de la surface d’attaque

Créez des vues personnalisées dans le Windows observateur d'événements pour afficher uniquement les événements pour des fonctionnalités et des paramètres spécifiques. Le moyen le plus simple consiste à importer une vue personnalisée en tant que fichier XML. Vous pouvez copier le code XML directement à partir de cette page.

Vous pouvez également accéder manuellement à la zone d’événements qui correspond à la fonctionnalité.

#### <a name="import-an-existing-xml-custom-view"></a>Importer une vue personnalisée XML existante

1. Créez un fichier .txt vide et copiez le code XML de l’affichage personnalisé que vous souhaitez utiliser dans le fichier .txt. Effectuez cette opération pour chacune des vues personnalisées que vous souhaitez utiliser. Renommez les fichiers comme suit (veillez à remplacer le type de .txt par .xml) :
    - Vue personnalisée des événements d’accès aux dossiers contrôlés : *cfa-events.xml*
    - Vue personnalisée des événements exploit protection : *ep-events.xml*
    - Vue personnalisée des événements de réduction de la surface d’attaque : *asr-events.xml*
    - Affichage personnalisé des événements réseau/protection : *np-events.xml*

2. Tapez **l’observateur d’événements** dans le menu Démarrer et ouvrez **observateur d'événements**.

3. Sélectionnez **Action** \> **Import Custom View...**

   > [!div class="mx-imgBorder"]
   > ![Animation mettant en surbrillance l’affichage personnalisé Importer à gauche de la fenêtre De la visionneuse pair.](images/events-import.gif)

4. Accédez à l’emplacement où vous avez extrait le fichier XML pour l’affichage personnalisé souhaité, puis sélectionnez-le.

5. Sélectionnez **Ouvrir**.

6. Il crée une vue personnalisée qui filtre pour afficher uniquement les événements liés à cette fonctionnalité.

#### <a name="copy-the-xml-directly"></a>Copier le code XML directement

1. Tapez **l’observateur d’événements** dans le menu Démarrer et ouvrez le **observateur d'événements Windows**.

2. Dans le volet gauche, sous **Actions**, **sélectionnez Créer une vue personnalisée...**

   > [!div class="mx-imgBorder"]
   > ![Animation mettant en surbrillance l’option Créer un affichage personnalisé dans la fenêtre Observateur d’événements.](images/events-create.gif)

3. Accédez à l’onglet XML et **sélectionnez Modifier la requête manuellement**. Vous verrez un avertissement indiquant que vous ne pouvez pas modifier la requête à l’aide de l’onglet **Filtrer** si vous utilisez l’option XML. Sélectionnez **Oui**.

4. Collez le code XML de la fonctionnalité à partir de laquelle vous souhaitez filtrer les événements dans la section XML.

5. Sélectionnez **OK**. Spécifiez un nom pour votre filtre. Cela crée une vue personnalisée qui filtre pour afficher uniquement les événements liés à cette fonctionnalité.

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

#### <a name="xml-for-exploit-protection-events"></a>XML pour les événements de protection contre les attaques

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

Tous les événements de réduction de la surface d’attaque se trouvent sous **les journaux des applications et des services > Microsoft > Windows**, puis le dossier ou le fournisseur, comme indiqué dans le tableau suivant.

Vous pouvez accéder à ces événements dans Windows Observateur d’événements :

1. Ouvrez le menu **Démarrer** et tapez **l’observateur d’événements**, puis sélectionnez le **résultat observateur d'événements**.
2. Développez **les journaux des applications et des services > Microsoft > Windows**, puis accédez au dossier répertorié sous **Fournisseur/source** dans le tableau ci-dessous.
3. Double-cliquez sur le sous-élément pour afficher les événements. Faites défiler les événements pour trouver celui que vous recherchez.

   ![Animation montrant l’utilisation de observateur d'événements.](images/event-viewer.gif)

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
|Protection réseau|Windows Defender (opérationnel)|1125|Événement lorsque la protection réseau se déclenche en mode Audit|
|Protection réseau|Windows Defender (opérationnel)|1126|Événement lorsque la protection réseau se déclenche en mode bloc|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|5007|Événement lorsque les paramètres sont modifiés|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1124|Événement d’accès contrôlé aux dossiers audité|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1123|Événement d’accès contrôlé aux dossiers bloqué|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1127|Événement de bloc d’écriture du secteur d’accès contrôlé aux dossiers bloqué|
|Accès contrôlé aux dossiers|Windows Defender (opérationnel)|1128|Événement de bloc d’écriture du secteur d’accès contrôlé aux dossiers audités|
|Réduction de la surface d'attaque|Windows Defender (opérationnel)|5007|Événement lorsque les paramètres sont modifiés|
|Réduction de la surface d'attaque|Windows Defender (opérationnel)|1122|Événement lors de l’déclenchement d’une règle en mode Audit|
|Réduction de la surface d'attaque|Windows Defender (opérationnel)|1121|Événement lorsque la règle se déclenche en mode bloc|

>[!NOTE]
> Du point de vue de l’utilisateur, les notifications en mode d’avertissement ASR sont effectuées en tant que notification toast Windows pour les règles de réduction de la surface d’attaque.
>
> Dans ASR, la protection réseau fournit uniquement les modes d’audit et de blocage.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>Ressources pour en savoir plus sur la réduction de la surface d’attaque

Comme mentionné dans la vidéo, Defender pour point de terminaison inclut plusieurs fonctionnalités de réduction de la surface d’attaque. Utilisez les ressources suivantes pour en savoir plus :

| Article | Description |
|:---|:---|
| [Isolation basée sur le matériel](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | Protégez et conservez l’intégrité d’un système au démarrage et pendant son exécution. Validez l’intégrité du système par le biais d’une attestation locale et distante. Utilisez l’isolation des conteneurs pour Microsoft Edge afin de vous protéger contre les sites web malveillants. |
| [Contrôle d’application](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | Utilisez le contrôle d’application pour que vos applications puissent gagner en confiance pour s’exécuter. |
| [Accès contrôlé aux dossiers](controlled-folders.md) | Empêcher les applications malveillantes ou suspectes (y compris les programmes malveillants de ransomware de chiffrement de fichiers) d’apporter des modifications aux fichiers dans vos dossiers système de clés (nécessite Antivirus Microsoft Defender) |
| [Protection du réseau](network-protection.md) | Étendez la protection au trafic réseau et à la connectivité sur les appareils de votre organisation. (Nécessite Antivirus Microsoft Defender) |
| [Exploit Protection](exploit-protection.md) | Protégez les systèmes d’exploitation et les applications utilisés par votre organisation contre l’exploitation. Exploit Protection fonctionne également avec des solutions antivirus tierces. |
| [Contrôle des appareils](device-control-report.md) | Protège contre la perte de données en surveillant et en contrôlant les supports utilisés sur les appareils, tels que le stockage amovible et les lecteurs USB, dans votre organisation. |
| [Guide de déploiement des règles de réduction de surface d’attaque (ASR)](attack-surface-reduction-rules-deployment.md) | Présente les informations de vue d’ensemble et les prérequis pour le déploiement de règles de réduction de la surface d’attaque |
| [Planifier le déploiement de règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-plan.md) | Répertorie les étapes recommandées pour le déploiement des règles de réduction de la surface d’attaque |
| [Tester les règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-test.md) | Fournit des étapes pour utiliser le mode audit pour tester les règles de réduction de la surface d’attaque. |
| [Activer les règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-implement.md) | Affiche les étapes de transition des règles de réduction de la surface d’attaque du mode test (audit) vers le mode actif et activé (bloquer). |
| [Opérationnaliser les règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-operationalize.md) | Fournit des informations sur les activités quotidiennes d’examen et de maintenance. |
| [Informations de référence sur les règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-reference.md) | Fournit des détails sur chaque règle de réduction de la surface d’attaque. |
| [Règles de réduction de la surface d’attaque](attack-surface-reduction.md) | Réduisez les vulnérabilités (surfaces d’attaque) de vos applications grâce à des règles intelligentes qui permettent d’arrêter le programme malveillant. (Nécessite Antivirus Microsoft Defender). |
