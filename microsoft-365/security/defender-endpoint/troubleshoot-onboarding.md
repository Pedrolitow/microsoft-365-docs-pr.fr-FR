---
title: Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison
description: Résolvez les problèmes qui peuvent survenir lors de l’intégration d’appareils ou du service Microsoft Defender pour point de terminaison.
keywords: résoudre les problèmes d’intégration, d’intégration, de visionneuse d’événements, de collecte et de préversion de données, de données de capteur et de diagnostics
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: troubleshooting
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: e1de2e186eea9fbe3b62e2e650f3419de43c6874
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232339"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-onboarding-issues"></a>Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows Server 2012 R2
- Windows Server 2016
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Vous devrez peut-être résoudre le Microsoft Defender pour point de terminaison processus d’intégration si vous rencontrez des problèmes.
Cette page fournit des étapes détaillées pour résoudre les problèmes d’intégration qui peuvent se produire lors du déploiement avec l’un des outils de déploiement et les erreurs courantes qui peuvent se produire sur les appareils.

Avant de commencer à résoudre les problèmes liés aux outils d’intégration, il est important de vérifier si les exigences minimales sont remplies pour l’intégration d’appareils aux services. [Découvrez les exigences en matière de licences, de matériel et de logiciels pour intégrer des appareils au service](minimum-requirements.md).

## <a name="troubleshoot-issues-with-onboarding-tools"></a>Résoudre les problèmes liés aux outils d’intégration

Si vous avez terminé le processus d’intégration et que vous ne voyez pas les appareils dans la [liste des appareils](investigate-machines.md) après une heure, cela peut indiquer un problème d’intégration ou de connectivité.

### <a name="troubleshoot-onboarding-when-deploying-with-group-policy"></a>Résoudre les problèmes d’intégration lors du déploiement avec stratégie de groupe

Le déploiement avec stratégie de groupe s’effectue en exécutant le script d’intégration sur les appareils. La console stratégie de groupe n’indique pas si le déploiement a réussi ou non.

Si vous avez terminé le processus d’intégration et que vous ne voyez pas les appareils dans la [liste des](investigate-machines.md) appareils après une heure, vous pouvez vérifier la sortie du script sur les appareils. Pour plus d’informations, consultez [Résolution des problèmes d’intégration lors du déploiement avec un script](#troubleshoot-onboarding-when-deploying-with-a-script).

Si le script se termine correctement, consultez [Résoudre les problèmes d’intégration sur les appareils](#troubleshoot-onboarding-issues-on-the-device) en cas d’erreurs supplémentaires susceptibles de se produire.

### <a name="troubleshoot-onboarding-issues-when-deploying-with-microsoft-endpoint-configuration-manager"></a>Résoudre les problèmes d’intégration lors du déploiement avec Microsoft Endpoint Configuration Manager

Lors de l’intégration d’appareils à l’aide des versions suivantes de Configuration Manager :

- Microsoft Endpoint Configuration Manager
- Gestionnaire de configuration System Center 2012
- System Center 2012 Configuration Manager R2

Le déploiement avec les versions mentionnées ci-dessus de Configuration Manager est effectué en exécutant le script d’intégration sur les appareils. Vous pouvez suivre le déploiement dans la console Configuration Manager.

Si le déploiement échoue, vous pouvez vérifier la sortie du script sur les appareils.

Si l’intégration s’est terminée avec succès, mais que les appareils ne s’affichent pas dans la **liste Des appareils** après une heure, consultez [Résoudre les problèmes d’intégration sur l’appareil](#troubleshoot-onboarding-issues-on-the-device) en cas d’erreurs supplémentaires susceptibles de se produire.

### <a name="troubleshoot-onboarding-when-deploying-with-a-script"></a>Résoudre les problèmes d’intégration lors du déploiement avec un script

**Vérifiez le résultat du script sur l’appareil :**

1. Cliquez sur **Démarrer, tapez** **observateur d'événements**, puis **appuyez sur Entrée**.

2. Accédez à **l’application** **journaux** \> Windows.

3. Recherchez un événement à partir de la source **d’événement WDATPOnboarding** .

Si le script échoue et que l’événement est une erreur, vous pouvez vérifier l’ID d’événement dans le tableau suivant pour vous aider à résoudre le problème.

> [!NOTE]
> Les ID d’événement suivants sont spécifiques au script d’intégration uniquement.

<br>

****

|ID d’événement|Type d’erreur|Étapes de résolution|
|:---:|---|---|
|`5`|Des données de désintégrage ont été trouvées, mais n’ont pas pu être supprimées|Vérifier les autorisations sur le Registre, en particulier <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.|
|`10`|Impossible d’écrire des données d’intégration dans le Registre|Vérifier les autorisations sur le Registre, en particulier <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`. <p> Vérifiez que le script a été exécuté en tant qu’administrateur.|
|`15`|Échec du démarrage du service SENSE|Vérifiez l’intégrité du service (`sc query sense` commande). Assurez-vous qu’il n’est pas dans un état intermédiaire (*« Pending_Stopped »,* *« Pending_Running* ») et réessayez d’exécuter le script (avec des droits d’administrateur). <p> Si l’appareil exécute Windows 10, version 1607 et que l’exécution de la commande `sc query sense` retourne, `START_PENDING`redémarrez l’appareil. Si le redémarrage de l’appareil ne répond pas au problème, effectuez une mise à niveau vers KB4015217 et réessayez d’intégrer.|
|`15`|Échec du démarrage du service SENSE|Si le message d’erreur est le suivant : Erreur système 577 ou erreur 1058, vous devez activer le pilote ELAM antivirus Microsoft Defender. Pour obtenir des instructions, voir [Vérifier que Microsoft Defender Antivirus n’est pas désactivé par une stratégie](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).|
|`30`|Le script n’a pas pu attendre le démarrage de l’exécution du service|Le service a peut-être pris plus de temps pour démarrer ou a rencontré des erreurs lors de la tentative de démarrage. Pour plus d’informations sur les événements et les erreurs liés à SENSE, consultez [Vérifier les événements et les erreurs à l’aide de la visionneuse d’événements](event-error-codes.md).|
|`35`|Le script n’a pas trouvé la valeur de Registre d’état d’intégration nécessaire|Lorsque le service SENSE démarre pour la première fois, il écrit l’état d’intégration à l’emplacement du Registre <p> `HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status`. <p> Le script n’a pas pu le trouver après plusieurs secondes. Vous pouvez le tester manuellement et vérifier s’il est présent. Pour plus d’informations sur les événements et les erreurs liés à SENSE, consultez [Vérifier les événements et les erreurs à l’aide de la visionneuse d’événements](event-error-codes.md).|
|`40`|L’état d’intégration du service SENSE n’est pas défini sur **1**|Le service SENSE n’a pas pu s’intégrer correctement. Pour plus d’informations sur les événements et les erreurs liés à SENSE, consultez [Vérifier les événements et les erreurs à l’aide de la visionneuse d’événements](event-error-codes.md).|
|`65`|Privilèges insuffisants|Réexélez le script avec des privilèges d’administrateur.|
|

### <a name="troubleshoot-onboarding-issues-using-microsoft-intune"></a>Résoudre les problèmes d’intégration à l’aide de Microsoft Intune

Vous pouvez utiliser Microsoft Intune pour vérifier les codes d’erreur et tenter de résoudre la cause du problème.

Si vous avez configuré des stratégies dans Intune et qu’elles ne sont pas propagées sur les appareils, vous devrez peut-être configurer l’inscription MDM automatique.

Utilisez les tableaux suivants pour comprendre les causes possibles des problèmes lors de l’intégration :

- Microsoft Intune codes d’erreur et table OMA-URIs
- Problèmes connus avec la table de non-conformité
- Table des journaux des événements mobile Gestion des appareils (MDM)

Si aucun des journaux des événements et des étapes de dépannage ne fonctionne, téléchargez le script local à partir de la section **Gestion des appareils** du portail et exécutez-le dans une invite de commandes avec élévation de privilèges.

#### <a name="microsoft-intune-error-codes-and-oma-uris"></a>Microsoft Intune codes d’erreur et OMA-URIs

<br>

****

|Code d’erreur Hex|Code d’erreur Dec|Description de l’erreur|OMA-URI|Causes possibles et étapes de dépannage|
|:---:|---|---|---|---|
|0x87D1FDE8|-2016281112|Échec de la correction|Intégration <p> Désintégrage|**Cause possible :** Échec de l’intégration ou de la désintégrage sur un objet blob incorrect : signature incorrecte ou champs PreviousOrgIds manquants. <p> **Étapes de résolution des problèmes :** <p> Vérifiez les ID d’événement dans les [erreurs d’intégration de l’agent View dans la section journal des événements de l’appareil](#view-agent-onboarding-errors-in-the-device-event-log) . <p> Vérifiez les journaux des événements GPM dans le tableau suivant ou suivez les instructions [fournies dans Diagnostiquer les échecs de GPM dans Windows](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).|
||||Intégration <p> Désintégrage <p> SampleSharing|**Cause possible :** Microsoft Defender pour point de terminaison clé de Registre de stratégie n’existe pas ou le client OMA DM n’est pas autorisé à y écrire. <p> **Étapes de résolution des problèmes :** Vérifiez que la clé de Registre suivante existe : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <p> S’il n’existe pas, ouvrez une commande avec élévation de privilèges et ajoutez la clé.|
||||SenseIsRunning <p> OnboardingState <p> OrgId|**Cause possible :** Tentative de correction par une propriété en lecture seule. Échec de l’intégration. <p> **Étapes de résolution des problèmes :** Consultez les étapes de résolution des problèmes de [résolution des problèmes d’intégration sur l’appareil](#troubleshoot-onboarding-issues-on-the-device). <p> Vérifiez les journaux des événements GPM dans le tableau suivant ou suivez les instructions [fournies dans Diagnostiquer les échecs de GPM dans Windows](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).|
||||Tous|**Cause possible :** Tentez de déployer Microsoft Defender pour point de terminaison sur une référence SKU/plateforme non prise en charge, en particulier la référence SKU holographique. <p> Plateformes actuellement prises en charge : <p> Entreprise, Éducation et Professionnel.<p> Le serveur n’est pas pris en charge.|
|0x87D101A9|-2016345687|SyncML(425) : échec de la commande demandée, car l’expéditeur ne dispose pas des autorisations de contrôle d’accès (ACL) appropriées sur le destinataire.|Tous|**Cause possible :** Tentez de déployer Microsoft Defender pour point de terminaison sur une référence SKU/plateforme non prise en charge, en particulier la référence SKU holographique.<p> Plateformes actuellement prises en charge : <p> Entreprise, Éducation et Professionnel.|
|

#### <a name="known-issues-with-non-compliance"></a>Problèmes connus liés à la non-conformité

Le tableau suivant fournit des informations sur les problèmes de non-conformité et la façon dont vous pouvez résoudre les problèmes.

<br>

****

|Cas|Symptômes|Causes possibles et étapes de dépannage|
|:---:|---|---|
|`1`|L’appareil est conforme par SenseIsRunning OMA-URI. Mais n’est pas conforme par OrgId, Onboarding et OnboardingState OMA-URI.|**Cause possible :** Vérifiez que l’utilisateur a passé OOBE après l’installation ou la mise à niveau de Windows. Lors de l’intégration OOBE n’a pas pu être effectuée, mais SENSE est déjà en cours d’exécution. <p> **Étapes de résolution des problèmes :** Attendez la fin de l’opération OOBE.|
|`2`|L’appareil est conforme par OrgId, Onboarding et OnboardingState OMA-URI, mais n’est pas conforme par SenseIsRunning OMA-URI.|**Cause possible :** Le type de démarrage du service Sense est défini sur « Début différé ». Parfois, le serveur Microsoft Intune signale que l’appareil n’est pas conforme par SenseIsRunning lorsque la session DM se produit au démarrage du système. <p> **Étapes de résolution des problèmes :** Le problème doit être résolu automatiquement dans les 24 heures.|
|`3`|L’appareil n’est pas conforme|**Étapes de résolution des problèmes :** Assurez-vous que les stratégies d’intégration et de désintégrage ne sont pas déployées simultanément sur le même appareil.|
|

#### <a name="mobile-device-management-mdm-event-logs"></a>Journaux des événements MDM (Mobile Gestion des appareils)

Affichez les journaux des événements GPM pour résoudre les problèmes qui peuvent survenir lors de l’intégration :

Nom du journal : Microsoft\Windows\DeviceManagement-EnterpriseDiagnostics-Provider

Nom du canal : Administration

<br>

****

|ID|Severity|Description de l’événement|Étapes de résolution des problèmes|
|---|---|---|---|
|1819|Error|Microsoft Defender pour point de terminaison CSP : Échec de la définition de la valeur du nœud. NodeId : (%1), TokenName : (%2), Résultat : (%3).|Téléchargez la [mise à jour cumulative pour Windows 10, 1607](https://go.microsoft.com/fwlink/?linkid=829760).|
|

## <a name="troubleshoot-onboarding-issues-on-the-device"></a>Résoudre les problèmes d’intégration sur l’appareil

Si les outils de déploiement utilisés n’indiquent pas d’erreur dans le processus d’intégration, mais que les appareils n’apparaissent toujours pas dans la liste des appareils dans une heure, consultez les rubriques de vérification suivantes pour vérifier si une erreur s’est produite avec l’agent Microsoft Defender pour point de terminaison.

- [Afficher les erreurs d’intégration de l’agent dans le journal des événements de l’appareil](#view-agent-onboarding-errors-in-the-device-event-log)
- [Vérifier que le service de données de diagnostic est activé](#ensure-the-diagnostics-service-is-enabled)
- [Vérifier que le service est configuré pour démarrer](#ensure-the-service-is-set-to-start)
- [Vérifier que l’appareil dispose d’une connexion Internet](#ensure-the-device-has-an-internet-connection)
- [Vérifier que Microsoft Defender Antivirus n’est pas désactivé par une stratégie](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

### <a name="view-agent-onboarding-errors-in-the-device-event-log"></a>Afficher les erreurs d’intégration de l’agent dans le journal des événements de l’appareil

1. Cliquez sur **Démarrer, tapez** **observateur d'événements**, puis **appuyez sur Entrée**.

2. Dans le volet **observateur d'événements (local),** développez **Les journaux des applications et des** \> services **Microsoft** \> **Windows** \> **SENSE**.

   > [!NOTE]
   > SENSE est le nom interne utilisé pour faire référence au capteur comportemental qui alimente Microsoft Defender pour point de terminaison.

3. Sélectionnez **Opération** pour charger le journal.

4. Dans le volet **Action** , cliquez sur **Filtrer le journal actuel**.

5. Sous l’onglet **Filtre** , sous **Niveau d’événement :** sélectionnez **Critique**, **Avertissement** et **Erreur**, puis cliquez sur **OK**.

   :::image type="content" source="images/filter-log.png" alt-text="Filtre de journal observateur d'événements" lightbox="images/filter-log.png":::

6. Les événements qui peuvent indiquer des problèmes apparaissent dans le volet **Opérationnel** . Vous pouvez tenter de les résoudre en fonction des solutions du tableau suivant :

   <br>

   ****

   |ID d’événement|Message|Étapes de résolution|
   |:---:|---|---|
   |`5`|Microsoft Defender pour point de terminaison service n’a pas pu se connecter au serveur à l’adresse _variable_|[Vérifiez que l’appareil dispose d’un accès à Internet](#ensure-the-device-has-an-internet-connection).|
   |`6`|Microsoft Defender pour point de terminaison service n’est pas intégré et aucun paramètre d’intégration n’a été trouvé. Code d’échec : _variable_|[Réexécriez le script d’intégration](configure-endpoints-script.md).|
   |`7`|Microsoft Defender pour point de terminaison service n’a pas pu lire les paramètres d’intégration. Code d’échec : _variable_|[Vérifiez que l’appareil dispose d’un accès à Internet](#ensure-the-device-has-an-internet-connection), puis réexélez l’intégralité du processus d’intégration.|
   |`9`|Microsoft Defender pour point de terminaison service n’a pas pu modifier son type de démarrage. Code d’échec : variable|Si l’événement s’est produit pendant l’intégration, redémarrez et réessayez d’exécuter le script d’intégration. Pour plus d’informations, consultez [Exécuter à nouveau le script d’intégration](configure-endpoints-script.md). <br><br>Si l’événement s’est produit pendant la désintégrage, contactez le support technique.|
   |`10`|Microsoft Defender pour point de terminaison service n’a pas pu conserver les informations d’intégration. Code d’échec : variable|Si l’événement s’est produit pendant l’intégration, réessayez d’exécuter le script d’intégration. Pour plus d’informations, consultez [Exécuter à nouveau le script d’intégration](configure-endpoints-script.md). <br><br>Si le problème persiste, contactez le support technique.|
   |`15`|Microsoft Defender pour point de terminaison ne peut pas démarrer le canal de commande avec l’URL : _variable_|[Vérifiez que l’appareil dispose d’un accès à Internet](#ensure-the-device-has-an-internet-connection).|
   |`17`|Microsoft Defender pour point de terminaison service n’a pas pu modifier l’emplacement du service Expériences utilisateur connectées et Télémétrie. Code d’échec : variable|[Réexécriez le script d’intégration](configure-endpoints-script.md). Si le problème persiste, contactez le support technique.|
   |`25`|Microsoft Defender pour point de terminaison service n’a pas pu réinitialiser l’état d’intégrité dans le Registre. Code d’échec : _variable_|Contactez le support technique.|
   |`27`|Échec de l’activation du mode Microsoft Defender pour point de terminaison dans Windows Defender. Échec du processus d’intégration. Code d’échec : variable|Contactez le support technique.|
   |`29`|Impossible de lire les paramètres de désintégrage. Type d’erreur : %1, Code d’erreur : %2, Description : %3|Vérifiez que l’appareil dispose d’un accès à Internet, puis réexélez le processus de désintégrage.|
   |`30`|Échec de la désactivation du mode $(build.sense.productDisplayName) dans Microsoft Defender pour point de terminaison. Code d’échec : %1|Contactez le support technique.|
   |`32`|Le service $(build.sense.productDisplayName) n’a pas pu demander de s’arrêter après le processus de désintégrage. Code d’échec : %1|Vérifiez que le type de démarrage du service est manuel et redémarrez l’appareil.|
   |`55`|Échec de la création du journal automatique ETW sécurisé. Code d’échec : %1|Redémarrez l’appareil.|
   |`63`|Mise à jour du type de démarrage du service externe. Nom : %1, type de démarrage réel : %2, type de démarrage attendu : %3, code de sortie : %4|Identifiez les causes des modifications apportées au type de démarrage du service mentionné. Si le code de sortie n’est pas égal à 0, corrigez manuellement le type de démarrage en fonction du type de démarrage attendu.|
   |`64`|Démarrage du service externe arrêté. Nom : %1, code de sortie : %2|Contactez le support technique si l’événement ne cesse de réapparaître.|
   |`68`|Le type de démarrage du service est inattendu. Nom du service : %1, type de démarrage réel : %2, type de démarrage attendu : %3|Identifiez les causes des modifications apportées au type de démarrage. Correction du type de démarrage du service mentionné.|
   |`69`|Le service est arrêté. Nom du service : %1|Démarrez le service mentionné. Contactez le support technique s’il persiste.|
   |

Il existe des composants supplémentaires sur l’appareil dont dépend l’agent Microsoft Defender pour point de terminaison pour fonctionner correctement. S’il n’existe aucune erreur liée à l’intégration dans le journal des événements de l’agent Microsoft Defender pour point de terminaison, procédez comme suit pour vous assurer que les composants supplémentaires sont correctement configurés.

<span id="ensure-the-diagnostics-service-is-enabled" />

### <a name="ensure-the-diagnostic-data-service-is-enabled"></a>Vérifier que le service de données de diagnostic est activé

Si les appareils ne signalent pas correctement, vous devrez peut-être vérifier que le service de données de diagnostic Windows est configuré pour démarrer automatiquement et s’exécute sur l’appareil. Le service a peut-être été désactivé par d’autres programmes ou modifications de configuration de l’utilisateur.

Tout d’abord, vous devez vérifier que le service est configuré pour démarrer automatiquement au démarrage de Windows, puis vérifier que le service est en cours d’exécution (et le démarrer s’il ne l’est pas).

### <a name="ensure-the-service-is-set-to-start"></a>Vérifier que le service est configuré pour démarrer

**Utilisez la ligne de commande pour vérifier le type de démarrage du service de données de diagnostic Windows** :

1. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil :

   a. Cliquez sur **Démarrer**, tapez **cmd**, puis **appuyez sur Entrée**.

   b. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis **appuyez sur Entrée** :

   ```console
   sc qc diagtrack
   ```

   Si le service est activé, le résultat doit ressembler à la capture d’écran suivante :

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="Résultat de la commande de requête sc pour diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

   Si la `START_TYPE` valeur n’est pas définie `AUTO_START`, vous devez définir le service pour qu’il démarre automatiquement.

**Utilisez la ligne de commande pour définir le service de données de diagnostic Windows de manière à démarrer automatiquement :**

1. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil :

   a. Cliquez sur **Démarrer**, tapez **cmd**, puis **appuyez sur Entrée**.

   b. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis **appuyez sur Entrée** :

   ```console
   sc config diagtrack start=auto
   ```

3. Un message de réussite s’affiche. Vérifiez la modification en entrant la commande suivante, puis **appuyez sur Entrée** :

   ```console
   sc qc diagtrack
   ```

4. Démarrez le service. Dans l’invite de commandes, tapez la commande suivante, puis **appuyez sur Entrée** :

   ```console
   sc start diagtrack
   ```

### <a name="ensure-the-device-has-an-internet-connection"></a>Vérifier que l’appareil dispose d’une connexion Internet

Le capteur Microsoft Defender pour point de terminaison requiert Microsoft Windows HTTP (WinHTTP) pour signaler les données du capteur et communiquer avec le service Microsoft Defender pour point de terminaison.

WinHTTP est indépendant des paramètres de proxy de navigation Internet et d’autres applications de contexte utilisateur et doit être en mesure de détecter les serveurs proxy disponibles dans votre environnement particulier.

Pour vous assurer que le capteur dispose d’une connectivité de service, suivez les étapes décrites dans la rubrique [Vérifier la connectivité du client aux URL de service Microsoft Defender pour point de terminaison](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls).

Si la vérification échoue et que votre environnement utilise un proxy pour se connecter à Internet, suivez les [étapes décrites dans la rubrique Configurer le proxy et les paramètres de connectivité Internet](configure-proxy-internet.md) .

### <a name="ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy"></a>Vérifier que Microsoft Defender Antivirus n’est pas désactivé par une stratégie

> [!IMPORTANT]
> Ce qui suit s’applique uniquement aux appareils qui **n’ont pas** encore reçu la mise à jour d’août 2020 (version 4.18.2007.8) vers Microsoft Defender Antivirus.
>
> La mise à jour garantit que Microsoft Defender Antivirus ne peut pas être désactivé sur les appareils clients via la stratégie système.

**Problème** : le service Microsoft Defender pour point de terminaison ne démarre pas après l’intégration.

**Symptôme** : l’intégration s’est terminée correctement, mais l’erreur 577 ou l’erreur 1058 s’affiche lors de la tentative de démarrage du service.

**Solution** : si vos appareils exécutent un client anti-programme malveillant tiers, l’agent Microsoft Defender pour point de terminaison a besoin que le pilote ELAM (Early Launch Antimalware) soit activé. Vous devez vous assurer qu’il n’est pas désactivé par une stratégie système.

- Selon l’outil que vous utilisez pour implémenter des stratégies, vous devez vérifier que les stratégies Windows Defender suivantes sont effacées :

  - DisableAntiSpyware
  - DisableAntiVirus

  Par exemple, dans stratégie de groupe il ne doit pas y avoir d’entrées telles que les valeurs suivantes :

  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiSpyware"/></Key>`
  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiVirus"/></Key>`

> [!IMPORTANT]
> Le `disableAntiSpyware` paramètre est abandonné et sera ignoré sur tous les appareils Windows 10, à compter de la mise à jour d’août 2020 (version 4.18.2007.8) vers Microsoft Defender Antivirus.

- Après avoir effacé la stratégie, exécutez à nouveau les étapes d’intégration.

- Vous pouvez également vérifier les valeurs de clé de Registre précédentes pour vérifier que la stratégie est désactivée, en ouvrant la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`de Registre.

  :::image type="content" source="images/atp-disableantispyware-regkey.png" alt-text="Clé de Registre pour Microsoft Defender Antivirus" lightbox="images/atp-disableantispyware-regkey.png":::

   > [!NOTE]
   > Tous les services Windows Defender (wdboot, wdfilter, wdnisdrv, wdnissvc et windefend) doivent être dans leur état par défaut. La modification du démarrage de ces services n’est pas prise en charge et peut vous forcer à réinitialiser votre système.
   >
   > Exemples de configurations par défaut pour WdBoot et WdFilter :
   >
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdBoot"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdFilter"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`

## <a name="troubleshoot-onboarding-issues"></a>Résoudre des problèmes d’intégration 

> [!NOTE]
> Les conseils de dépannage suivants s’appliquent uniquement aux Windows Server 2016 et aux versions inférieures.

Si vous rencontrez des problèmes lors de l’intégration d’un serveur, suivez les étapes de vérification suivantes pour résoudre les problèmes possibles.


- [Vérifier que Microsoft Monitoring Agent (MMA) est installé et configuré pour signaler des données de capteur au service](configure-server-endpoints.md)
- [Vérifier que les paramètres de proxy de serveur et de connectivité Internet sont correctement configurés](configure-server-endpoints.md)

Vous devrez peut-être également vérifier les éléments suivants :

- Vérifiez qu’un service Microsoft Defender pour point de terminaison s’exécute sous l’onglet **Processus** du **Gestionnaire des tâches**. Par exemple :

  :::image type="content" source="images/atp-task-manager.png" alt-text="Vue de processus avec Microsoft Defender pour point de terminaison Service en cours d’exécution" lightbox="images/atp-task-manager.png":::

- Vérifiez **observateur d'événements** \> **Gestionnaire des opérations des journaux des applications et des** \> services **pour voir** s’il existe des erreurs.

- Dans **Services**, vérifiez si Microsoft **Monitoring Agent** est en cours d’exécution sur le serveur. Par exemple :

  :::image type="content" source="images/atp-services.png" alt-text="Les services" lightbox="images/atp-services.png":::

- Dans **Microsoft Monitoring Agent** \> **Azure Log Analytics (OMS),** vérifiez les espaces de travail et vérifiez que l’état est en cours d’exécution.

  :::image type="content" source="images/atp-mma-properties.png" alt-text="Propriétés de Microsoft Monitoring Agent" lightbox="images/atp-mma-properties.png":::

- Vérifiez que les appareils sont reflétés dans la **liste Des appareils** dans le portail.

## <a name="confirming-onboarding-of-newly-built-devices"></a>Confirmation de l’intégration des appareils nouvellement créés

Il peut y avoir des instances lors du déploiement de l’intégration sur un appareil nouvellement créé, mais pas terminé.

Les étapes ci-dessous fournissent des conseils pour le scénario suivant :

- Le package d’intégration est déployé sur les appareils nouvellement créés
- Le capteur ne démarre pas, car l’expérience OOBE (Out-of-box experience) ou la première ouverture de session utilisateur n’est pas terminée
- L’appareil est désactivé ou redémarré avant que l’utilisateur final n’effectue une première ouverture de session
- Dans ce scénario, le service SENSE ne démarre pas automatiquement même si le package d’intégration a été déployé

> [!NOTE]
> L’ouverture de session utilisateur après OOBE n’est plus nécessaire pour que le service SENSE démarre sur les versions Windows suivantes ou plus récentes : Windows 10, version 1809 ou Windows Server 2019, ou Windows Server 2022 avec le [correctif cumulatif du 22 avril 2021](https://support.microsoft.com/kb/5001384). Windows 10, version 1909 avec [correctif cumulatif d’avril 2021](https://support.microsoft.com/kb/5001396). Windows 10, version 2004/20H2 avec [correctif cumulatif du 28 avril 2021](https://support.microsoft.com/kb/5001391). 


> [!NOTE]
> Les étapes suivantes sont pertinentes uniquement lors de l’utilisation de Microsoft Endpoint Configuration Manager. Pour plus d’informations sur l’intégration à l’aide de Microsoft Endpoint Configuration Manager, consultez [Microsoft Defender pour point de terminaison](/mem/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection).

1. Créez une application dans Microsoft Endpoint Configuration Manager.

   :::image type="content" source="images/mecm-1.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-1" lightbox="images/mecm-1.png":::

2. Sélectionnez **Manuellement pour spécifier les informations de l’application**.

   :::image type="content" source="images/mecm-2.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-2" lightbox="images/mecm-2.png":::

3. Spécifiez des informations sur l’application, puis sélectionnez **Suivant**.

   :::image type="content" source="images/mecm-3.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-3" lightbox="images/mecm-3.png":::

4. Spécifiez des informations sur le centre logiciel, puis sélectionnez **Suivant**.

   :::image type="content" source="images/mecm-4.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-4" lightbox="images/mecm-4.png":::

5. Dans **Types de déploiement** , sélectionnez **Ajouter**.

   :::image type="content" source="images/mecm-5.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-5" lightbox="images/mecm-5.png":::

6. Sélectionnez **Manuellement spécifier les informations de type de déploiement**, puis sélectionnez **Suivant**.

   :::image type="content" source="images/mecm-6.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-6" lightbox="images/mecm-6.png":::

7. Spécifiez des informations sur le type de déploiement, puis sélectionnez **Suivant**.

   :::image type="content" source="images/mecm-7.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-7" lightbox="images/mecm-7.png":::

8. Dans le **programme d’installation** de **contenu**\>, spécifiez la commande : `net start sense`.

   :::image type="content" source="images/mecm-8.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-8" lightbox="images/mecm-8.png":::

9. Dans **la méthode Detection**, **sélectionnez Configurer les règles pour détecter la présence de ce type de déploiement**, puis sélectionnez **Ajouter une clause**.

   :::image type="content" source="images/mecm-9.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-9" lightbox="images/mecm-9.png":::

10. Spécifiez les détails de la règle de détection suivantes, puis sélectionnez **OK** :

    :::image type="content" source="images/mecm-10.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-10" lightbox="images/mecm-10.png":::

11. Dans **la méthode Detection** , sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-11.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-11" lightbox="images/mecm-11.png":::

12. Dans **Expérience utilisateur**, spécifiez les informations suivantes, puis sélectionnez **Suivant** :

    :::image type="content" source="images/mecm-12.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-12" lightbox="images/mecm-12.png":::

13. Dans **Configuration requise**, sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-13.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-13" lightbox="images/mecm-13.png":::

14. Dans **Dépendances**, sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-14.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-14" lightbox="images/mecm-14.png":::

15. Dans **Résumé**, sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-15.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-15" lightbox="images/mecm-15.png":::

16. Dans **Achèvement**, sélectionnez **Fermer**.

    :::image type="content" source="images/mecm-16.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-16" lightbox="images/mecm-16.png":::

17. Dans **Types de déploiement**, sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-17.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-17" lightbox="images/mecm-17.png":::

18. Dans **Résumé**, sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-18.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-18" lightbox="images/mecm-18.png":::

    L’état s’affiche ensuite : :::image type="content" source="images/mecm-19.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-19" lightbox="images/mecm-19.png":::

19. Dans **Achèvement**, sélectionnez **Fermer**.

    :::image type="content" source="images/mecm-20.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-20" lightbox="images/mecm-20.png":::

20. Vous pouvez maintenant déployer l’application en cliquant avec le bouton droit sur l’application et en sélectionnant **Déployer**.

    :::image type="content" source="images/mecm-21.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-21" lightbox="images/mecm-21.png":::

21. En **général** , sélectionnez **Distribuer automatiquement le contenu pour les dépendances** et **Parcourir**.

    :::image type="content" source="images/mecm-22.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-22" lightbox="images/mecm-22.png":::

22. Dans **Contenu** , sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-23.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-23" lightbox="images/mecm-23.png":::

23. Dans **paramètres de déploiement**, sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-24.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-24" lightbox="images/mecm-24.png":::

24. Dans **Planification,** sélectionnez **Dès que possible après l’heure disponible**, puis sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-25.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-25" lightbox="images/mecm-25.png":::

25. Dans **l’expérience utilisateur**, sélectionnez **Valider les modifications à l’échéance ou pendant une fenêtre de maintenance (nécessite des redémarrages),** puis sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-26.png" alt-text="Configuration du point de terminaison Microsoft Configuration Manager-26" lightbox="images/mecm-26.png":::

26. Dans **Alertes** , sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-27.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-27" lightbox="images/mecm-27.png":::

27. Dans **Résumé**, sélectionnez **Suivant**.

    :::image type="content" source="images/mecm-28.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-28" lightbox="images/mecm-28.png":::
      

    L’état s’affiche ensuite :::image type="content" source="images/mecm-29.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-29" lightbox="images/mecm-29.png":::

28. Dans **Achèvement**, sélectionnez **Fermer**.

    :::image type="content" source="images/mecm-30.png" alt-text="Le point de terminaison Microsoft Configuration Manager configuration-30" lightbox="images/mecm-30.png":::

## <a name="related-topics"></a>Voir aussi

- [Résoudre des problèmes avec Microsoft Defender pour point de terminaison](troubleshoot-mdatp.md)
- [Intégrer des appareils](onboard-configure.md)
- [Configurer les paramètres de proxy du dispositif et de connectivité Internet](configure-proxy-internet.md)
