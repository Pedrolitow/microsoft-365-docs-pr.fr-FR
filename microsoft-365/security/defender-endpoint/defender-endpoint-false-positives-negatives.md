---
title: Résoudre les faux positifs/négatifs dans Microsoft Defender pour point de terminaison
description: Découvrez comment gérer les faux positifs ou les faux négatifs dans Microsoft Defender pour point de terminaison.
keywords: antivirus, exception, exclusion, Microsoft Defender pour point de terminaison, faux positif, faux négatif, fichier bloqué, URL bloquée
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
ms.date: 10/24/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365initiative-defender-endpoint
- m365solution-overview
- m365solution-fpfn
- highpri
- tier1
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
search.appverid: met150
ms.openlocfilehash: 18b5745e9d8104f6a4eea370923e318e227ac9a3
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68794179"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>Résoudre les faux positifs/négatifs dans Microsoft Defender pour point de terminaison

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Dans les solutions de protection des points de terminaison, un faux positif est une entité, telle qu’un fichier ou un processus qui a été détecté et identifié comme malveillant, même si l’entité n’est pas réellement une menace. Un faux négatif est une entité qui n’a pas été détectée comme une menace, même si elle est en réalité malveillante. Des faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection contre les menaces, y compris [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md).

:::image type="content" source="images/false-positives-overview.png" alt-text="Définition des faux positifs et négatifs dans le portail Microsoft Defender pour point de terminaison" lightbox="images/false-positives-overview.png":::

Heureusement, des mesures peuvent être prises pour résoudre et réduire ce genre de problèmes. Si vous voyez des faux positifs/négatifs dans [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender), vos opérations de sécurité peuvent prendre des mesures pour y remédier à l’aide du processus suivant :

1. [Examiner et classifier les alertes](#part-1-review-and-classify-alerts)
2. [Passer en revue les mesures correctives qui ont été effectuées](#part-2-review-remediation-actions)
3. [Passer en revue et définir des exclusions](#part-3-review-or-define-exclusions)
4. [Envoyer une entité à des fins d’analyse](#part-4-submit-a-file-for-analysis)
5. [Examiner et ajuster vos paramètres de protection contre les menaces](#part-5-review-and-adjust-your-threat-protection-settings)

Vous pouvez obtenir de l’aide si vous rencontrez toujours des problèmes avec les faux positifs/négatifs après avoir effectué les tâches décrites dans cet article. Voir [Vous avez toujours besoin d’aide ?](#still-need-help)

:::image type="content" source="images/false-positives-step-diagram.png" alt-text="Étapes pour traiter les faux positifs et les négatifs" lightbox="images/false-positives-step-diagram.png":::

> [!NOTE]
> Cet article est destiné à guider les opérateurs de sécurité et les administrateurs de sécurité qui utilisent [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md).

## <a name="part-1-review-and-classify-alerts"></a>Partie 1 : Examiner et classifier les alertes

Si vous voyez une [alerte](alerts.md) qui s’est produite parce qu’un élément est détecté comme malveillant ou suspect et qu’il ne devrait pas l’être, vous pouvez supprimer l’alerte pour cette entité. Vous pouvez également supprimer les alertes qui ne sont pas nécessairement des faux positifs, mais qui ne sont pas importantes. Nous vous recommandons également de classifier les alertes.

La gestion de vos alertes et la classification des vrais/faux positifs permettent d’entraîner votre solution de protection contre les menaces et peuvent réduire le nombre de faux positifs ou de faux négatifs au fil du temps. Ces étapes permettent également de réduire le bruit dans votre file d’attente afin que votre équipe de sécurité puisse se concentrer sur des éléments de travail de priorité plus élevée.

### <a name="determine-whether-an-alert-is-accurate"></a>Déterminer si une alerte est exacte

Avant de classifier ou de supprimer une alerte, déterminez si l’alerte est exacte, fausse positive ou bénigne.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Incidents & alertes** , puis sélectionnez **Alertes**.

3. Sélectionnez une alerte pour afficher plus de détails à son sujet. (Voir [Passer en revue les alertes dans Microsoft Defender pour point de terminaison](review-alerts.md).)

4. Selon l’état de l’alerte, effectuez les étapes décrites dans le tableau suivant :

   |État de l’alerte|Procédure|
   |---|---|
   |L’alerte est précise|Affectez l’alerte, puis [examinez-la plus en](investigate-alerts.md) détail.|
   |L’alerte est un faux positif|1. [Classifier l’alerte](#classify-an-alert) comme un faux positif.<br/><br/>2. [Supprimez l’alerte](#suppress-an-alert).<br/><br/>3. [Créez un indicateur](#indicators-for-microsoft-defender-for-endpoint) pour Microsoft Defender pour point de terminaison.<br/><br/>4. [Envoyez un fichier à Microsoft pour analyse](#part-4-submit-a-file-for-analysis).|
   |L’alerte est précise, mais sans importance|[Classifiez l’alerte](#classify-an-alert) comme étant un vrai positif, puis [supprimez-la](#suppress-an-alert).|

### <a name="classify-an-alert"></a>Classifier une alerte

Les alertes peuvent être classées en tant que faux positifs ou vrais positifs dans Microsoft 365 Defender. La classification des alertes permet d’entraîner Microsoft Defender pour point de terminaison afin que, au fil du temps, vous voyiez plus d’alertes vraies et moins de fausses alertes.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Incidents & alertes**, sélectionnez **Alertes** , puis sélectionnez une alerte.

3. Pour l’alerte sélectionnée, sélectionnez **Gérer l’alerte**. Un volet de menu volant s’ouvre.

4. Dans la section **Gérer l’alerte** , dans le champ **Classification** , classez l’alerte (Vrai positif, Information, activité attendue ou Faux positif).

> [!TIP]
> Pour plus d’informations sur la suppression des alertes, consultez [Gérer les alertes Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/manage-alerts). Si votre organisation utilise un serveur SIEM (Security Information and Event Management), veillez également à définir une règle de suppression.

### <a name="suppress-an-alert"></a>Supprimer une alerte

Si vous avez des alertes qui sont des faux positifs ou qui sont des vrais positifs, mais pour des événements sans importance, vous pouvez supprimer ces alertes dans Microsoft 365 Defender. La suppression des alertes permet de réduire le bruit dans votre file d’attente.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Incidents & alertes** , puis sélectionnez **Alertes**.

3. Sélectionnez une alerte que vous souhaitez supprimer pour ouvrir son volet **Détails** .

4. Dans le volet **Détails** , choisissez les points de suspension (**...**), puis **Créer une règle de suppression**.

5. Spécifiez tous les paramètres de votre règle de suppression, puis choisissez **Enregistrer**.

> [!TIP]
> Vous avez besoin d’aide pour les règles de suppression ? Consultez [Supprimer une alerte et créer une règle de suppression](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>Partie 2 : Passer en revue les actions de correction

[Les actions de correction](manage-auto-investigation.md#remediation-actions), telles que l’envoi d’un fichier en quarantaine ou l’arrêt d’un processus, sont effectuées sur des entités (telles que des fichiers) détectées comme des menaces. Plusieurs types d’actions de correction se produisent automatiquement par le biais d’une investigation automatisée et d’Microsoft Defender Antivirus :

- Mettre en quarantaine un fichier
- Supprimer une clé de Registre
- Tuer un processus
- Arrêter un service
- Désactiver un pilote
- Supprimer une tâche planifiée

D’autres actions, telles que le démarrage d’une analyse antivirus ou la collecte d’un package d’investigation, se produisent manuellement ou via [Live Response](live-response.md). Les actions effectuées via Live Response ne peuvent pas être annulées.

Une fois que vous avez examiné vos alertes, l’étape suivante consiste à [passer en revue les actions de correction](manage-auto-investigation.md). Si des actions ont été effectuées à la suite de faux positifs, vous pouvez annuler la plupart des types d’actions de correction. Concrètement, vous pouvez :

- [Restaurer un fichier mis en quarantaine à partir du Centre de notifications](#restore-a-quarantined-file-from-the-action-center)
- [Annuler plusieurs actions à la fois](#undo-multiple-actions-at-one-time)
- [Supprimez un fichier de la mise en quarantaine sur plusieurs appareils](#remove-a-file-from-quarantine-across-multiple-devices). et
- [Restaurer un fichier à partir de la mise en quarantaine](#restore-file-from-quarantine)

Une fois que vous avez terminé d’examiner et d’annuler les actions qui ont été effectuées à la suite de faux positifs, passez en [revue ou définissez des exclusions](#part-3-review-or-define-exclusions).

### <a name="review-completed-actions"></a>Passer en revue les actions terminées

1. Dans le volet de navigation gauche du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, sélectionnez **Actions & soumissions**, puis **Centre de** notifications.

2. Sélectionnez l’onglet **Historique** pour afficher la liste des actions qui ont été effectuées.

3. Sélectionnez un élément pour afficher plus de détails sur l’action de correction qui a été effectuée.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>Restaurer un fichier mis en quarantaine à partir du Centre de notifications

1. Dans le volet de navigation gauche du portail Microsoft 365 Defender, sélectionnez **Actions & soumissions**, puis **Centre de** notifications.

2. Sous l’onglet **Historique** , sélectionnez une action que vous souhaitez annuler.

3. Dans le volet volant, sélectionnez **Annuler**. Si l’action ne peut pas être annulée avec cette méthode, vous ne verrez pas de bouton **Annuler** . (Pour en savoir plus, consultez [Annuler les actions terminées](manage-auto-investigation.md#undo-completed-actions).)

### <a name="undo-multiple-actions-at-one-time"></a>Annuler plusieurs actions à la fois

1. Dans le volet de navigation gauche du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, sélectionnez **Actions & soumissions**, puis **Centre de** notifications.

2. Sous l’onglet **Historique** , sélectionnez les actions que vous souhaitez annuler.

3. Dans le volet volant à droite de l’écran, sélectionnez **Annuler**.

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>Supprimer un fichier de la quarantaine sur plusieurs appareils

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/autoir-quarantine-file-1.png" alt-text="Fichier de mise en quarantaine" lightbox="images/autoir-quarantine-file-1.png":::

1. Dans le volet de navigation gauche du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, sélectionnez **Actions & soumissions**, puis **Centre de** notifications.

2. Sous l’onglet **Historique** , sélectionnez un fichier dont le type d’action est **Fichier de quarantaine**.

3. Dans le volet de droite de l’écran, sélectionnez **Appliquer à X instances supplémentaires de ce fichier**, **puis Annuler.**

### <a name="review-quarantined-messages"></a>Passer en revue les messages mis en quarantaine

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, sous **Email & collaboration**, sélectionnez Suivi des **messages Exchange**.

3. Sélectionnez un message pour afficher les détails.

### <a name="restore-file-from-quarantine"></a>Restaurer un fichier à partir de la mise en quarantaine

Vous pouvez restaurer et supprimer un fichier de la quarantaine si vous avez déterminé qu’il est propre après une enquête. Exécutez la commande suivante sur chaque appareil où le fichier a été mis en quarantaine.

1. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil :

   1. Accéder à **Démarrer** et taper _cmd_.
   2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis **appuyez sur Entrée** :

    ```console
    "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > Dans certains scénarios, **threatName** peut apparaître sous la forme `EUS:Win32/CustomEnterpriseBlock!cl`. Defender pour point de terminaison restaure tous les fichiers bloqués personnalisés qui ont été mis en quarantaine sur cet appareil au cours des 30 derniers jours.
    >
    > Un fichier qui a été mis en quarantaine en tant que menace réseau potentielle peut ne pas être récupérable. Si un utilisateur tente de restaurer le fichier après la mise en quarantaine, ce fichier risque de ne pas être accessible. Cela peut être dû au fait que le système n’a plus d’informations d’identification réseau pour accéder au fichier. En règle générale, cela est le résultat d’une connexion temporaire à un dossier système ou partagé et que les jetons d’accès ont expiré.

3. Dans le volet de droite de l’écran, sélectionnez **Appliquer à X instances supplémentaires de ce fichier**, **puis Annuler.**

## <a name="part-3-review-or-define-exclusions"></a>Partie 3 : Passer en revue ou définir des exclusions

Une exclusion est une entité, telle qu’un fichier ou une URL, que vous spécifiez comme exception aux actions de correction. L’entité exclue peut toujours être détectée, mais aucune action de correction n’est effectuée sur cette entité. Autrement dit, le fichier ou le processus détecté ne sera pas arrêté, envoyé en quarantaine, supprimé ou modifié par Microsoft Defender pour point de terminaison.

Pour définir des exclusions dans Microsoft Defender pour point de terminaison, effectuez les tâches suivantes :

- [Définir des exclusions pour Microsoft Defender Antivirus](#exclusions-for-microsoft-defender-antivirus)
- [Créer des indicateurs « autoriser » pour Microsoft Defender pour point de terminaison](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> Microsoft Defender exclusions antivirus s’appliquent uniquement à la protection antivirus, et non à d’autres fonctionnalités Microsoft Defender pour point de terminaison. Pour exclure des fichiers à grande échelle, utilisez des exclusions pour l’antivirus Microsoft Defender et [des indicateurs personnalisés](/microsoft-365/security/defender-endpoint/manage-indicators) pour Microsoft Defender pour point de terminaison.

Les procédures de cette section décrivent comment définir des exclusions et des indicateurs.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>Exclusions pour l’antivirus Microsoft Defender

En général, vous n’avez pas besoin de définir des exclusions pour Microsoft Defender Antivirus. Veillez à définir les exclusions avec parcimonie et à inclure uniquement les fichiers, dossiers, processus et fichiers ouverts par processus qui entraînent des faux positifs. En outre, veillez à examiner régulièrement vos exclusions définies. Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour définir ou modifier vos exclusions antivirus ; Toutefois, vous pouvez utiliser d’autres méthodes, telles que [stratégie de groupe](/azure/active-directory-domain-services/manage-group-policy) (voir [Gérer les Microsoft Defender pour point de terminaison](manage-mde-post-migration.md).

> [!TIP]
> Vous avez besoin d’aide pour les exclusions antivirus ? Consultez [Configurer et valider des exclusions pour Microsoft Defender analyses antivirus](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>Utiliser Microsoft Endpoint Manager pour gérer les exclusions antivirus (pour les stratégies existantes)

1. Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **Antivirus de sécurité** \> de point de terminaison, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante ou si vous souhaitez en créer une, passez à [la procédure suivante](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions)).

3. Choisissez **Propriétés**, puis en regard de **Paramètres de configuration**, choisissez **Modifier**.

4. Développez **Microsoft Defender Exclusions antivirus**, puis spécifiez vos exclusions.

5. Choisissez **Vérifier + enregistrer**, puis **Enregistrer**.

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>Utiliser Microsoft Endpoint Manager pour créer une stratégie antivirus avec des exclusions

1. Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **Antivirus** \> **de sécurité** \> du point de terminaison **+ Créer une stratégie**.

3. Sélectionnez une plateforme (par exemple **, Windows 10 et versions ultérieures**, **macOS** ou **Windows 10 et Windows Server**).

4. Pour **Profil**, sélectionnez **Microsoft Defender Exclusions antivirus**, puis choisissez **Créer**.

5. Spécifiez un nom et une description pour le profil, puis choisissez **Suivant**.

6. Sous l’onglet **Paramètres de configuration** , spécifiez vos exclusions antivirus, puis choisissez **Suivant**.

7. Sous l’onglet **Balises d’étendue** , si vous utilisez des balises d’étendue dans votre organisation, spécifiez des balises d’étendue pour la stratégie que vous créez. (Voir [Balises d’étendue](/mem/intune/fundamentals/scope-tags).)

8. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Si vous avez besoin d’aide pour les affectations, consultez [Attribuer des profils d’utilisateur et d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

9. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres, puis choisissez **Créer**.

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>Indicateurs pour Microsoft Defender pour point de terminaison

[Les indicateurs](/microsoft-365/security/defender-endpoint/manage-indicators) (en particulier les indicateurs de compromission, ou IoC) permettent à votre équipe des opérations de sécurité de définir la détection, la prévention et l’exclusion des entités. Par exemple, vous pouvez spécifier certains fichiers à omettre des analyses et des actions de correction dans Microsoft Defender pour point de terminaison. Vous pouvez également utiliser des indicateurs pour générer des alertes pour certains fichiers, adresses IP ou URL.

Pour spécifier des entités en tant qu’exclusions pour Microsoft Defender pour point de terminaison, créez des indicateurs « autoriser » pour ces entités. Ces indicateurs « autoriser » dans Microsoft Defender pour point de terminaison s’appliquent à la [protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md), à la [détection et](overview-endpoint-detection-response.md) à la réponse des points de terminaison, ainsi [qu’à l’examen automatisé & à la correction](/microsoft-365/security/defender-endpoint/automated-investigations).

Les indicateurs « Autoriser » peuvent être créés pour :

- [Files](#indicators-for-files)
- [Adresses IP, URL et domaines](#indicators-for-ip-addresses-urls-or-domains)
- [Certificats d’application](#indicators-for-application-certificates)

:::image type="content" source="images/false-positives-indicators.png" alt-text="Types d’indicateurs" lightbox="images/false-positives-indicators.png":::

#### <a name="indicators-for-files"></a>Indicateurs pour les fichiers

Lorsque vous [créez un indicateur « autoriser » pour un fichier, tel qu’un fichier exécutable](/microsoft-365/security/defender-endpoint/indicator-file), cela permet d’empêcher le blocage des fichiers que votre organisation utilise. Les fichiers peuvent inclure des fichiers exécutables portables (PE), tels que `.exe` des fichiers et `.dll` .

Avant de créer des indicateurs pour les fichiers, vérifiez que les conditions suivantes sont remplies :

- Microsoft Defender antivirus est configuré avec la protection basée sur le cloud activée (consultez [Gérer la protection basée sur le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- La version du client anti-programme malveillant est 4.18.1901.x ou ultérieure
- Les appareils exécutent Windows 10, version 1703 ou ultérieure, ou Windows 11 ; Windows Server 2016, Windows Server 2019 ou Windows Server 2022
- La [fonctionnalité Bloquer ou autoriser est activée](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>Indicateurs pour les adresses IP, les URL ou les domaines

Lorsque vous [créez un indicateur « autoriser » pour une adresse IP, une URL ou un domaine](/microsoft-365/security/defender-endpoint/indicator-ip-domain), cela permet d’empêcher le blocage des sites ou adresses IP que votre organisation utilise.

Avant de créer des indicateurs pour les adresses IP, les URL ou les domaines, vérifiez que les conditions suivantes sont remplies :

- La protection réseau dans Defender pour point de terminaison est activée en mode bloc (voir [Activer la protection réseau](/microsoft-365/security/defender-endpoint/enable-network-protection))
- La version du client anti-programme malveillant est 4.18.1906.x ou ultérieure
- Les appareils exécutent Windows 10, version 1709 ou ultérieure, ou Windows 11

Les indicateurs réseau personnalisés sont activés dans le [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Pour en savoir plus, consultez [Fonctionnalités avancées](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>Indicateurs pour les certificats d’application

Lorsque vous [créez un indicateur « autoriser » pour un certificat d’application](/microsoft-365/security/defender-endpoint/indicator-certificates), cela permet d’empêcher le blocage des applications, telles que les applications développées en interne, que votre organisation utilise. `.CER` ou `.PEM` les extensions de fichier sont prises en charge.

Avant de créer des indicateurs pour les certificats d’application, vérifiez que les conditions suivantes sont remplies :

- Microsoft Defender Antivirus est configuré avec la protection basée sur le cloud activée (consultez [Gérer la protection basée sur le cloud](deploy-manage-report-microsoft-defender-antivirus.md)
- La version du client anti-programme malveillant est 4.18.1901.x ou ultérieure
- Les appareils exécutent Windows 10, version 1703 ou ultérieure, ou Windows 11 ; Windows Server 2016, Windows Server 2019 ou Windows Server 2022
- Les définitions de protection contre les virus et les menaces sont à jour

> [!TIP]
> Lorsque vous créez des indicateurs, vous pouvez les définir un par un ou importer plusieurs éléments à la fois. Gardez à l’esprit qu’il existe une limite de 15 000 indicateurs pour un seul locataire. Vous devrez peut-être d’abord collecter certains détails, tels que les informations de hachage de fichier. Veillez à passer en revue les prérequis avant de [créer des indicateurs](manage-indicators.md).

## <a name="part-4-submit-a-file-for-analysis"></a>Partie 4 : Envoyer un fichier à des fins d’analyse

Vous pouvez soumettre des entités, telles que des fichiers et des détections sans fichier, à Microsoft pour analyse. Les chercheurs en sécurité Microsoft analysent toutes les soumissions, et leurs résultats aident à informer Microsoft Defender pour point de terminaison fonctionnalités de protection contre les menaces. Lorsque vous vous connectez au site de soumission, vous pouvez suivre vos soumissions.

### <a name="submit-a-file-for-analysis"></a>Envoyer un fichier pour analyse

Si vous avez un fichier qui a été détecté à tort comme malveillant ou qui a été manqué, procédez comme suit pour soumettre le fichier à des fins d’analyse.

1. Passez en revue les instructions ici : [Envoyer des fichiers à des fins d’analyse](/windows/security/threat-protection/intelligence/submission-guide).

2. Visitez le [site de soumission Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)et envoyez vos fichiers).

### <a name="submit-a-fileless-detection-for-analysis"></a>Envoyer une détection sans fichier à des fins d’analyse

Si un programme malveillant a été détecté en fonction du comportement et que vous n’avez pas de fichier, vous pouvez soumettre votre `Mpsupport.cab` fichier pour analyse. Vous pouvez obtenir le fichier *.cab* à l’aide de l’outil Microsoft Protection Command-Line Utility (MPCmdRun.exe) sur Windows 10 ou Windows 11.

1. Accédez à ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`, puis exécutez `MpCmdRun.exe` en tant qu’administrateur.

2. Tapez `mpcmdrun.exe -GetFiles`, puis appuyez sur **Entrée**.

   Un fichier .cab qui contient différents journaux de diagnostic est généré. L’emplacement du fichier est spécifié dans la sortie de l’invite de commandes. Par défaut, l’emplacement est `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

3. Passez en revue les instructions ici : [Envoyer des fichiers à des fins d’analyse](/windows/security/threat-protection/intelligence/submission-guide).

4. Visitez le [site de soumission de Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)et envoyez vos fichiers .cab.

### <a name="what-happens-after-a-file-is-submitted"></a>Que se passe-t-il après l’envoi d’un fichier ?

Votre soumission est immédiatement analysée par nos systèmes pour vous donner la dernière détermination avant même qu’un analyste commence à traiter votre cas. Il est possible qu’un fichier ait déjà été soumis et traité par un analyste. Dans ce cas, une décision est prise rapidement.

Pour les soumissions qui n’ont pas encore été traitées, elles sont classées par ordre de priorité pour l’analyse comme suit :

- Les fichiers répandus susceptibles d’affecter un grand nombre d’ordinateurs bénéficient d’une priorité plus élevée.
- Les clients authentifiés, en particulier les clients d’entreprise avec [des ID Software Assurance (SAID) valides](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx), bénéficient d’une priorité plus élevée.
- Les soumissions signalées comme étant prioritaires par les titulaires de SAID reçoivent une attention immédiate.

Pour vérifier les mises à jour relatives à votre soumission, connectez-vous au [site de soumission Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission).

> [!TIP]
> Pour plus d’informations, consultez [Envoyer des fichiers à des fins d’analyse](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>Partie 5 : Examiner et ajuster vos paramètres de protection contre les menaces

Microsoft Defender pour point de terminaison offre un large éventail d’options, y compris la possibilité d’ajuster les paramètres pour diverses fonctionnalités. Si vous recevez de nombreux faux positifs, veillez à passer en revue les paramètres de protection contre les menaces de votre organisation. Vous devrez peut-être apporter quelques ajustements aux éléments suivants :

- [Protection fournie par le cloud](#cloud-delivered-protection)
- [Correction pour les applications potentiellement indésirables](#remediation-for-potentially-unwanted-applications)
- [Investigation et correction automatisées](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>Protection fournie par le cloud

Vérifiez votre niveau de protection fourni par le cloud pour Microsoft Defender Antivirus. Par défaut, la protection fournie par le cloud est définie sur **Non configuré**, ce qui correspond à un niveau de protection normal pour la plupart des organisations. Si votre protection fournie par le cloud est définie sur **Tolérance élevée**, **Élevée +** ou **Zéro**, vous pouvez rencontrer un nombre plus élevé de faux positifs.

> [!TIP]
> Pour en savoir plus sur la configuration de votre protection fournie par le cloud, consultez [Spécifier le niveau de protection fourni par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour modifier ou définir vos paramètres de protection fournis par le cloud. Toutefois, vous pouvez utiliser d’autres méthodes, telles que [stratégie de groupe](/azure/active-directory-domain-services/manage-group-policy) (voir [Gérer les Microsoft Defender pour point de terminaison](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>Utiliser Microsoft Endpoint Manager pour passer en revue et modifier les paramètres de protection fournis par le cloud (pour les stratégies existantes)

1. Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **Antivirus** **de sécurité** \> du point de terminaison, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante ou si vous souhaitez en créer une, passez à [la procédure suivante](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy)).

3. Sous **Gérer**, choisissez **Propriétés**. Ensuite, en regard **de Paramètres de configuration**, choisissez **Modifier**.

4. Développez **Protection cloud** et passez en revue votre paramètre actuel dans la ligne **Niveau de protection fourni par le cloud** . Nous vous recommandons de définir la protection fournie par le cloud sur **Non configuré**, ce qui offre une protection forte tout en réduisant les risques d’obtenir des faux positifs.

5. Choisissez **Vérifier + enregistrer**, puis **Enregistrer**.

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>Utiliser Microsoft Endpoint Manager pour définir les paramètres de protection fournis par le cloud (pour une nouvelle stratégie)

1. Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **Antivirus** \> sécurité \> **du point de terminaison** **+ Créer une stratégie**.

3. Pour **Plateforme**, sélectionnez une option, puis pour **Profil**, sélectionnez **Antivirus** ou **antivirus Microsoft Defender** (l’option spécifique dépend de ce que vous avez sélectionné pour **Plateforme**.) Choisissez ensuite **Créer**.

4. Sous l’onglet **Informations de base** , spécifiez un nom et une description pour la stratégie. Sélectionnez **Suivant**.

5. Sous l’onglet **Paramètres de configuration** , développez **Protection cloud**, puis spécifiez les paramètres suivants :

   - **Définissez Activer la protection fournie par le cloud** sur **Oui**.
   - Définissez **Niveau de protection assuré par le cloud** sur **Non configuré**. (Ce niveau offre un niveau élevé de protection par défaut tout en réduisant les risques de faux positifs.)

6. Sous l’onglet **Balises d’étendue** , si vous utilisez des balises d’étendue dans votre organisation, spécifiez des balises d’étendue pour la stratégie. (Voir [Balises d’étendue](/mem/intune/fundamentals/scope-tags).)

7. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Si vous avez besoin d’aide pour les affectations, consultez [Attribuer des profils d’utilisateur et d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres, puis choisissez **Créer**.

### <a name="remediation-for-potentially-unwanted-applications"></a>Correction pour les applications potentiellement indésirables

Les applications potentiellement indésirables (PUA) sont une catégorie de logiciels qui peuvent ralentir l’exécution des appareils, afficher des publicités inattendues ou installer d’autres logiciels qui peuvent être inattendus ou indésirables. Parmi les exemples de puA, citons les logiciels publicitaires, les logiciels de regroupement et les logiciels d’évasion qui se comportent différemment avec les produits de sécurité. Bien que PUA ne soit pas considéré comme un programme malveillant, certains types de logiciels sont puA en fonction de leur comportement et de leur réputation.

> [!TIP]
> Pour en savoir plus sur puA, consultez [Détecter et bloquer les applications potentiellement indésirables](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

Selon les applications utilisées par votre organisation, vous pouvez obtenir des faux positifs en raison de vos paramètres de protection PUA. Si nécessaire, envisagez d’exécuter la protection PUA en mode audit pendant un certain temps, ou appliquez la protection PUA à un sous-ensemble d’appareils de votre organisation. La protection PUA peut être configurée pour le navigateur Microsoft Edge et pour Microsoft Defender Antivirus.

Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour modifier ou définir les paramètres de protection puA . Toutefois, vous pouvez utiliser d’autres méthodes, telles que [stratégie de groupe](/azure/active-directory-domain-services/manage-group-policy) (voir [Gérer les Microsoft Defender pour point de terminaison](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>Utiliser Microsoft Endpoint Manager pour modifier la protection puA (pour les profils de configuration existants)

1. Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **Appareils** \> **Profils de configuration**, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante ou si vous souhaitez en créer une, passez à [la procédure suivante](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile).)

3. Sous **Gérer**, choisissez **Propriétés**, puis, en regard de **Paramètres de configuration**, choisissez **Modifier**.

4. Sous l’onglet **Paramètres de configuration**, faites défiler vers le bas et développez **Microsoft Defender Antivirus**.

5. Définissez **Détecter les applications potentiellement indésirables** sur **Audit**. (Vous pouvez le désactiver, mais en utilisant le mode audit, vous serez en mesure de voir les détections.)

6. Choisissez **Vérifier + enregistrer**, puis **Enregistrer**.

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>Utiliser Microsoft Endpoint Manager pour définir la protection puA (pour un nouveau profil de configuration)

1. Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **Appareils** \> Profils \> **de configuration** **+ Créer un profil**.

3. Pour **Plateforme**, choisissez **Windows 10 et versions ultérieures**, puis pour **Profil**, sélectionnez **Restrictions d’appareil**.

4. Sous l’onglet **Informations de base** , spécifiez un nom et une description pour votre stratégie. Sélectionnez **Suivant**.

5. Sous l’onglet **Paramètres de configuration**, faites défiler vers le bas et développez **Microsoft Defender Antivirus**.

6. Définissez **Détecter les applications potentiellement indésirables** sur **Audit**, puis choisissez **Suivant**. (Vous pouvez désactiver la protection puA, mais en utilisant le mode audit, vous serez en mesure de voir les détections.)

7. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Si vous avez besoin d’aide pour les affectations, consultez [Attribuer des profils d’utilisateur et d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. Sous l’onglet **Règles d’applicabilité** , spécifiez les éditions ou versions du système d’exploitation à inclure ou exclure de la stratégie. Par exemple, vous pouvez définir la stratégie à appliquer à tous les appareils, certaines éditions de Windows 10. Sélectionnez **Suivant**.

9. Sous l’onglet **Vérifier + créer** , passez en revue vos paramètres, puis choisissez **Créer**.

### <a name="automated-investigation-and-remediation"></a>Investigation et résolution automatiques

[Les fonctionnalités d’investigation et de correction automatisées](automated-investigations.md) (AIR) sont conçues pour examiner les alertes et prendre des mesures immédiates pour résoudre les violations. À mesure que des alertes sont déclenchées et qu’une enquête automatisée s’exécute, un verdict est généré pour chaque élément de preuve examiné. Les verdicts peuvent être *malveillants*, *suspects* ou *Aucune menace trouvée*.

Selon le [niveau d’automatisation](/microsoft-365/security/defender-endpoint/automation-levels) défini pour votre organisation et d’autres paramètres de sécurité, des actions de correction sont effectuées sur les artefacts considérés comme *malveillants* ou *suspects*. Dans certains cas, les actions de correction se produisent automatiquement ; dans d’autres cas, les actions de correction sont effectuées manuellement ou uniquement après approbation par votre équipe des opérations de sécurité.

- [En savoir plus sur les niveaux d’automatisation](/microsoft-365/security/defender-endpoint/automation-levels) ; Et puis
- [Configurez les fonctionnalités AIR dans Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation).

> [!IMPORTANT]
> Nous vous recommandons d’utiliser *l’automatisation complète* pour l’examen et la correction automatisés. Ne désactivez pas ces fonctionnalités en raison d’un faux positif. Au lieu de cela, utilisez des [indicateurs « autoriser » pour définir des exceptions](#indicators-for-microsoft-defender-for-endpoint) et laissez l’examen et la correction automatisés définis pour prendre automatiquement les mesures appropriées. Suivre [ces conseils](automation-levels.md#levels-of-automation) permet de réduire le nombre d’alertes que votre équipe des opérations de sécurité doit gérer.

## <a name="still-need-help"></a>Encore besoin d’aide ?

Si vous avez effectué toutes les étapes de cet article et que vous avez toujours besoin d’aide, contactez le support technique.

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> et connectez-vous.

2. Dans le coin supérieur droit, sélectionnez le point d’interrogation (**?**), puis sélectionnez **Support Microsoft**.

3. Dans la fenêtre **Assistant Support** , décrivez votre problème, puis envoyez votre message. À partir de là, vous pouvez ouvrir une demande de service.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md) 

## <a name="see-also"></a>Voir aussi

[Gérer les Microsoft Defender pour point de terminaison](manage-mde-post-migration.md)

[Vue d’ensemble du portail Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
