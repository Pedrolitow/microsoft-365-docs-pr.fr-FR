---
title: Résoudre les faux positifs/négatifs dans Microsoft Defender pour point de terminaison
description: Découvrez comment gérer les faux positifs ou les faux négatifs dans Microsoft Defender pour point de terminaison.
keywords: antivirus, exception, exclusion, Microsoft Defender pour point de terminaison, faux positif, faux négatif, fichier bloqué, URL bloquée
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
- m365solution-scenario
- m365scenario-fpfn
ms.topic: how-to
ms.date: 12/02/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
ms.openlocfilehash: d7477c2006acd04008e6cb56cb22261a4db4a92b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789910"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>Résoudre les faux positifs/négatifs dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Dans les solutions endpoint protection, un faux positif est une entité, telle qu’un fichier ou un processus, qui a été détectée et identifiée comme malveillante, même si l’entité n’est pas réellement une menace. Un faux négatif est une entité qui n’a pas été détectée comme une menace, même si elle est réellement malveillante. Les faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection contre les menaces, y compris [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md).

:::image type="content" source="images/false-positives-overview.png" alt-text="Définition des faux positifs et négatifs dans le portail Microsoft Defender pour point de terminaison" lightbox="images/false-positives-overview.png":::

Heureusement, des mesures peuvent être prises pour résoudre et réduire ce genre de problèmes. Si vous voyez des faux positifs/négatifs dans [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender), vos opérations de sécurité peuvent prendre des mesures pour y remédier à l’aide du processus suivant :

1. [Examiner et classer les alertes](#part-1-review-and-classify-alerts)
2. [Passer en revue les actions de correction qui ont été prises](#part-2-review-remediation-actions)
3. [Examiner et définir des exclusions](#part-3-review-or-define-exclusions)
4. [Envoyer une entité à des fins d’analyse](#part-4-submit-a-file-for-analysis)
5. [Examiner et ajuster vos paramètres de protection contre les menaces](#part-5-review-and-adjust-your-threat-protection-settings)

Vous pouvez obtenir de l’aide si vous rencontrez toujours des problèmes avec les faux positifs/négatifs après avoir effectué les tâches décrites dans cet article. Vous voyez [Still besoin d’aide ?](#still-need-help)

:::image type="content" source="images/false-positives-step-diagram.png" alt-text="Étapes pour résoudre les faux positifs et les négatifs" lightbox="images/false-positives-step-diagram.png":::

> [!NOTE]
> Cet article est destiné aux opérateurs de sécurité et aux administrateurs de sécurité qui utilisent [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md).

## <a name="part-1-review-and-classify-alerts"></a>Partie 1 : Examiner et classer les alertes

Si vous voyez une [alerte](alerts.md) qui a été déclenchée parce que quelque chose a été détecté comme malveillant ou suspect qui n’aurait pas dû l’être, vous pouvez supprimer l’alerte pour cette entité. Vous pouvez également supprimer les alertes qui ne sont pas nécessairement des faux positifs, mais qui ne sont pas importantes. Nous vous recommandons également de classer les alertes.

La gestion de vos alertes et la classification des vrais/faux positifs permettent d’entraîner votre solution de protection contre les menaces et peuvent réduire le nombre de faux positifs ou de faux négatifs au fil du temps. Ces étapes permettent également de réduire le bruit dans votre tableau de bord des opérations de sécurité afin que votre équipe de sécurité puisse se concentrer sur des éléments de travail de priorité plus élevée.

### <a name="determine-whether-an-alert-is-accurate"></a>Déterminer si une alerte est précise

Avant de classer ou de supprimer une alerte, déterminez si l’alerte est exacte, un faux positif ou bénin.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, choisissez **La file d’attente des alertes**.

3. Sélectionnez une alerte pour plus d’informations sur l’alerte. (Voir [Vérifier les alertes dans Microsoft Defender pour point de terminaison](review-alerts.md).)

4. Selon l’état de l’alerte, effectuez les étapes décrites dans le tableau suivant :

   |État de l’alerte|Procédure|
   |---|---|
   |L’alerte est précise|Affectez l’alerte, puis [examinez-la](investigate-alerts.md) plus en détail.|
   |L’alerte est un faux positif|1. [Classer l’alerte](#classify-an-alert) comme un faux positif.<br/><br/>2. [Supprimez l’alerte](#suppress-an-alert).<br/><br/>3. [Créez un indicateur](#indicators-for-microsoft-defender-for-endpoint) pour Microsoft Defender pour point de terminaison.<br/><br/>4. [Envoyez un fichier à Microsoft pour analyse](#part-4-submit-a-file-for-analysis).|
   |L’alerte est précise, mais sans gravité (sans importance)|[Classifiez l’alerte](#classify-an-alert) comme un vrai positif, puis [supprimez l’alerte](#suppress-an-alert).|

### <a name="classify-an-alert"></a>Classifier une alerte

Les alertes peuvent être classées sous forme de faux positifs ou de vrais positifs dans Microsoft 365 Defender. La classification des alertes permet d’entraîner Microsoft Defender pour point de terminaison de sorte qu’au fil du temps, vous verrez plus d’alertes vraies et moins de fausses alertes.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Sélectionnez **la file d’attente Alertes**, puis sélectionnez une alerte.

3. Pour l’alerte sélectionnée, sélectionnez **Actions** \> **Gérer l’alerte**. Un volet volant s’ouvre.

4. Dans la section **Gérer l’alerte** , sélectionnez **Alerte true** ou **Alerte False**. (Utilisez **l’alerte False** pour classer un faux positif.)

> [!TIP]
> Pour plus d’informations sur la suppression des alertes, consultez [Gérer les alertes Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/manage-alerts). Et, si votre organisation utilise un serveur SIEM (Security Information and Event Management), veillez également à définir une règle de suppression.

### <a name="suppress-an-alert"></a>Supprimer une alerte

Si vous avez des alertes qui sont des faux positifs ou qui sont de vrais positifs, mais pour des événements sans importance, vous pouvez supprimer ces alertes dans Microsoft 365 Defender. La suppression des alertes permet de réduire le bruit dans votre tableau de bord des opérations de sécurité.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans le volet de navigation, sélectionnez **La file d’attente des alertes**.

3. Sélectionnez une alerte à supprimer pour ouvrir son volet **Détails** .

4. Dans le volet **Détails** , choisissez les points de suspension (**...**), puis **créez une règle de suppression**.

5. Spécifiez tous les paramètres de votre règle de suppression, puis **choisissez Enregistrer**.

> [!TIP]
> Vous avez besoin d’aide sur les règles de suppression ? Consultez [Supprimer une alerte et créez une règle de suppression](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>Partie 2 : Examiner les actions de correction

[Les actions de correction](manage-auto-investigation.md#remediation-actions), telles que l’envoi d’un fichier en quarantaine ou l’arrêt d’un processus, sont effectuées sur des entités (telles que des fichiers) détectées comme des menaces. Plusieurs types d’actions de correction se produisent automatiquement par le biais d’une investigation automatisée et de Antivirus Microsoft Defender :

- Mettre en quarantaine un fichier
- Supprimer une clé de Registre
- Tuer un processus
- Arrêter un service
- Désactiver un pilote
- Supprimer une tâche planifiée

D’autres actions, telles que le démarrage d’une analyse antivirus ou la collecte d’un package d’investigation, se produisent manuellement ou via [live Response](live-response.md). Les actions effectuées via Live Response ne peuvent pas être annulées.

Une fois que vous avez examiné vos alertes, l’étape suivante consiste à [passer en revue les actions de correction](manage-auto-investigation.md). Si des actions ont été effectuées à la suite de faux positifs, vous pouvez annuler la plupart des types d’actions de correction. Concrètement, vous pouvez :

- [Restaurer un fichier mis en quarantaine à partir du Centre d’actions](#restore-a-quarantined-file-from-the-action-center)
- [Annuler plusieurs actions à la fois](#undo-multiple-actions-at-one-time)
- [Supprimez un fichier de la quarantaine sur plusieurs appareils](#remove-a-file-from-quarantine-across-multiple-devices). et
- [Restaurer un fichier à partir de la mise en quarantaine](#restore-file-from-quarantine)

Lorsque vous avez terminé d’examiner et d’annuler les actions qui ont été effectuées à la suite de faux positifs, passez en [revue ou définissez des exclusions](#part-3-review-or-define-exclusions).

### <a name="review-completed-actions"></a>Passer en revue les actions terminées

1. Dans le volet de navigation gauche du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, cliquez sur **Centre d’actions**.

2. Sélectionnez l’onglet **Historique** pour afficher la liste des actions qui ont été effectuées.

3. Sélectionnez un élément pour afficher plus de détails sur l’action de correction qui a été effectuée.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>Restaurer un fichier mis en quarantaine à partir du Centre d’actions

1. Dans le volet de navigation gauche du portail Microsoft 365 Defender, cliquez sur **Centre d’actions**.

2. Sous l’onglet **Historique** , sélectionnez une action à annuler.

3. Dans le volet de menu volant, sélectionnez **Annuler**. Si l’action ne peut pas être annulée avec cette méthode, vous ne **verrez** pas de bouton Annuler. (Pour en savoir plus, consultez [Annuler les actions terminées](manage-auto-investigation.md#undo-completed-actions).)

### <a name="undo-multiple-actions-at-one-time"></a>Annuler plusieurs actions à la fois

1. Dans le volet de navigation gauche du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, cliquez sur **Centre d’actions**.

2. Sous l’onglet **Historique** , sélectionnez les actions que vous souhaitez annuler.

3. Dans le volet à droite de l’écran, sélectionnez **Annuler**.

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>Supprimer un fichier de la quarantaine sur plusieurs appareils

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/autoir-quarantine-file-1.png" alt-text="Fichier de mise en quarantaine" lightbox="images/autoir-quarantine-file-1.png":::

1. Dans le volet de navigation gauche du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, cliquez sur **Centre d’actions**.

2. Sous l’onglet **Historique** , sélectionnez un fichier contenant le **fichier de mise en quarantaine** de type Action.

3. Dans le volet à droite de l’écran, **sélectionnez Appliquer à X autres instances de ce fichier**, puis **sélectionnez Annuler**.

### <a name="restore-file-from-quarantine"></a>Restaurer un fichier à partir de la mise en quarantaine

Vous pouvez restaurer et supprimer un fichier de la quarantaine si vous avez déterminé qu’il est propre après une enquête. Exécutez la commande suivante sur chaque appareil sur lequel le fichier a été mis en quarantaine.

1. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil :

   1. Accéder à **Démarrer** et taper _cmd_.
   2. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis **appuyez sur Entrée** :

    ```console
    "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > Dans certains scénarios, **threatName** peut apparaître comme `EUS:Win32/CustomEnterpriseBlock!cl`. Defender pour point de terminaison restaure tous les fichiers bloqués personnalisés qui ont été mis en quarantaine sur cet appareil au cours des 30 derniers jours.
    >
    > Un fichier qui a été mis en quarantaine en tant que menace réseau potentielle peut ne pas être récupérable. Si un utilisateur tente de restaurer le fichier après la mise en quarantaine, ce fichier n’est peut-être pas accessible. Cela peut être dû au fait que le système n’a plus d’informations d’identification réseau pour accéder au fichier. En règle générale, il s’agit d’un résultat d’une connexion temporaire à un système ou à un dossier partagé, et les jetons d’accès ont expiré.

3. Dans le volet à droite de l’écran, **sélectionnez Appliquer à X autres instances de ce fichier**, puis **sélectionnez Annuler**.

## <a name="part-3-review-or-define-exclusions"></a>Partie 3 : Examiner ou définir des exclusions

Une exclusion est une entité, telle qu’un fichier ou une URL, que vous spécifiez comme exception aux actions de correction. L’entité exclue peut toujours être détectée, mais aucune action de correction n’est effectuée sur cette entité. Autrement dit, le fichier ou le processus détecté ne sera pas arrêté, envoyé en quarantaine, supprimé ou modifié par Microsoft Defender pour point de terminaison.

Pour définir des exclusions entre Microsoft Defender pour point de terminaison, effectuez les tâches suivantes :

- [Définir des exclusions pour Antivirus Microsoft Defender](#exclusions-for-microsoft-defender-antivirus)
- [Créer des indicateurs « autoriser » pour Microsoft Defender pour point de terminaison](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> Antivirus Microsoft Defender exclusions s’appliquent uniquement à la protection antivirus, et non à d’autres fonctionnalités Microsoft Defender pour point de terminaison. Pour exclure les fichiers de manière générale, utilisez des exclusions pour Antivirus Microsoft Defender et [des indicateurs personnalisés](/microsoft-365/security/defender-endpoint/manage-indicators) pour Microsoft Defender pour point de terminaison.

Les procédures de cette section décrivent comment définir des exclusions et des indicateurs.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>Exclusions pour Antivirus Microsoft Defender

En général, vous n’avez pas besoin de définir d’exclusions pour Antivirus Microsoft Defender. Veillez à définir les exclusions avec parcimonie et à inclure uniquement les fichiers, dossiers, processus et fichiers ouverts par le processus qui génèrent des faux positifs. En outre, veillez à examiner régulièrement vos exclusions définies. Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour définir ou modifier vos exclusions antivirus. Toutefois, vous pouvez utiliser d’autres méthodes, telles que [stratégie de groupe](/azure/active-directory-domain-services/manage-group-policy) (voir [Gérer Microsoft Defender pour point de terminaison](manage-mde-post-migration.md).

> [!TIP]
> Vous avez besoin d’aide pour les exclusions antivirus ? Consultez [Configurer et valider les exclusions pour les analyses Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>Utiliser Microsoft Endpoint Manager pour gérer les exclusions antivirus (pour les stratégies existantes)

1. Accédez au centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **l’antivirus** **de sécurité** \> de point de terminaison, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante ou si vous souhaitez créer une stratégie, passez à [la procédure suivante](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions)).

3. Choisissez **Propriétés**, puis, en regard **des paramètres de configuration**, choisissez **Modifier**.

4. Développez **Antivirus Microsoft Defender exclusions**, puis spécifiez vos exclusions.

5. Choisissez **Vérifier + enregistrer**, puis **Enregistrer**.

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>Utiliser Microsoft Endpoint Manager pour créer une stratégie antivirus avec exclusions

1. Accédez au centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **l’antivirus** \> **de sécurité de point de terminaison** \> **+ Créer une stratégie**.

3. Sélectionnez une plateforme (par exemple **, Windows 10 et versions ultérieures**, **macOS** ou **Windows 10 et Windows Server**).

4. Pour **Profil**, sélectionnez **Antivirus Microsoft Defender exclusions**, puis **choisissez Créer**.

5. Spécifiez un nom et une description pour le profil, puis choisissez **Suivant**.

6. Sous l’onglet **Paramètres de configuration** , spécifiez vos exclusions antivirus, puis choisissez **Suivant**.

7. Sous l’onglet **Balises d’étendue** , si vous utilisez des balises d’étendue dans votre organisation, spécifiez des balises d’étendue pour la stratégie que vous créez. (Voir [Balises d’étendue](/mem/intune/fundamentals/scope-tags).)

8. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Si vous avez besoin d’aide pour les affectations, consultez [Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

9. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres, puis choisissez **Créer**.

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>Indicateurs pour Microsoft Defender pour point de terminaison

[Les indicateurs](/microsoft-365/security/defender-endpoint/manage-indicators) (en particulier, les indicateurs de compromission ou les IOC) permettent à votre équipe des opérations de sécurité de définir la détection, la prévention et l’exclusion des entités. Par exemple, vous pouvez spécifier certains fichiers à omettre des analyses et des actions de correction dans Microsoft Defender pour point de terminaison. Vous pouvez également utiliser des indicateurs pour générer des alertes pour certains fichiers, adresses IP ou URL.

Pour spécifier des entités en tant qu’exclusions pour Microsoft Defender pour point de terminaison, créez des indicateurs « autoriser » pour ces entités. Ces indicateurs « autorisés » dans Microsoft Defender pour point de terminaison s’appliquent à la [protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md), [à la protection évolutive des points de terminaison](overview-endpoint-detection-response.md) et à [l’examen automatisé & correction](/microsoft-365/security/defender-endpoint/automated-investigations).

Des indicateurs « Autoriser » peuvent être créés pour :

- [Files](#indicators-for-files)
- [Adresses IP, URL et domaines](#indicators-for-ip-addresses-urls-or-domains)
- [Certificats d’application](#indicators-for-application-certificates)

:::image type="content" source="images/false-positives-indicators.png" alt-text="Types d’indicateurs" lightbox="images/false-positives-indicators.png":::

#### <a name="indicators-for-files"></a>Indicateurs pour les fichiers

Lorsque vous [créez un indicateur « autoriser » pour un fichier, tel qu’un exécutable](/microsoft-365/security/defender-endpoint/indicator-file), cela permet d’empêcher le blocage des fichiers utilisés par votre organisation. Les fichiers peuvent inclure des fichiers exécutables portables (PE), tels que `.exe` des `.dll` fichiers.

Avant de créer des indicateurs pour les fichiers, assurez-vous que les exigences suivantes sont remplies :

- Antivirus Microsoft Defender est configuré avec la protection basée sur le cloud activée (voir Gérer la [protection basée sur le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- La version du client Antimalware est 4.18.1901.x ou ultérieure
- Les appareils exécutent Windows 10, version 1703 ou ultérieure, ou Windows 11 ; Windows Server 2016 ou Windows Server 2019 ou Windows Server 2022
- La [fonctionnalité Bloquer ou autoriser est activée](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>Indicateurs pour les adresses IP, les URL ou les domaines

Lorsque vous [créez un indicateur « autoriser » pour une adresse IP, une URL ou un domaine](/microsoft-365/security/defender-endpoint/indicator-ip-domain), cela permet d’empêcher le blocage des sites ou adresses IP utilisés par votre organisation.

Avant de créer des indicateurs pour les adresses IP, les URL ou les domaines, assurez-vous que les exigences suivantes sont remplies :

- La protection réseau dans Defender pour point de terminaison est activée en mode bloc (voir [Activer la protection réseau](/microsoft-365/security/defender-endpoint/enable-network-protection))
- La version du client Antimalware est 4.18.1906.x ou ultérieure
- Les appareils exécutent Windows 10, version 1709 ou ultérieure, ou Windows 11

Les indicateurs réseau personnalisés sont activés dans le [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Pour en savoir plus, consultez [Fonctionnalités avancées](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>Indicateurs pour les certificats d’application

Lorsque vous [créez un indicateur « autoriser » pour un certificat d’application](/microsoft-365/security/defender-endpoint/indicator-certificates), cela permet d’empêcher le blocage des applications, telles que les applications développées en interne, que votre organisation utilise. `.CER` ou `.PEM` les extensions de fichier sont prises en charge.

Avant de créer des indicateurs pour les certificats d’application, assurez-vous que les exigences suivantes sont remplies :

- Antivirus Microsoft Defender est configuré avec la protection basée sur le cloud activée (voir [Gérer la protection basée sur le cloud](deploy-manage-report-microsoft-defender-antivirus.md)
- La version du client Antimalware est 4.18.1901.x ou ultérieure
- Les appareils exécutent Windows 10, version 1703 ou ultérieure, ou Windows 11 ; Windows Server 2016 ou Windows Server 2019 ou Windows Server 2022
- Les définitions de protection contre les virus et les menaces sont à jour

> [!TIP]
> Lorsque vous créez des indicateurs, vous pouvez les définir un par un ou importer plusieurs éléments à la fois. Gardez à l’esprit qu’il existe une limite de 15 000 indicateurs pour un seul locataire. Vous devrez peut-être d’abord collecter certains détails, tels que des informations de hachage de fichier. Veillez à passer en revue les prérequis avant de [créer des indicateurs](manage-indicators.md).

## <a name="part-4-submit-a-file-for-analysis"></a>Partie 4 : Soumettre un fichier à des fins d’analyse

Vous pouvez envoyer des entités, telles que des fichiers et des détections sans fichier, à Microsoft à des fins d’analyse. Les chercheurs en sécurité Microsoft analysent toutes les soumissions et leurs résultats aident à informer Microsoft Defender pour point de terminaison fonctionnalités de protection contre les menaces. Lorsque vous vous connectez au site de soumission, vous pouvez suivre vos soumissions.

### <a name="submit-a-file-for-analysis"></a>Envoyer un fichier à des fins d’analyse

Si vous avez un fichier qui a été détecté à tort comme malveillant ou qui a été manqué, procédez comme suit pour soumettre le fichier à des fins d’analyse.

1. Passez en revue les instructions ici : [Soumettre des fichiers à des fins d’analyse](/windows/security/threat-protection/intelligence/submission-guide).

2. Visitez le [site de soumission Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)et envoyez vos fichiers).

### <a name="submit-a-fileless-detection-for-analysis"></a>Envoyer une détection sans fichier à des fins d’analyse

Si un logiciel malveillant a été détecté en fonction du comportement et que vous n’avez pas de fichier, vous pouvez soumettre votre `Mpsupport.cab` fichier à des fins d’analyse. Vous pouvez obtenir le fichier *.cab* à l’aide de l’outil Utilitaire de protection contre les programmes malveillants Microsoft Command-Line (MPCmdRun.exe) sur Windows 10 ou Windows 11.

1. Accédez à ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`, puis exécutez en `MpCmdRun.exe` tant qu’administrateur.

2. Tapez `mpcmdrun.exe -GetFiles`, puis **appuyez sur Entrée**.

   Un fichier .cab est généré qui contient différents journaux de diagnostic. L’emplacement du fichier est spécifié dans la sortie de l’invite de commandes. Par défaut, l’emplacement est `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

3. Passez en revue les instructions ici : [Soumettre des fichiers à des fins d’analyse](/windows/security/threat-protection/intelligence/submission-guide).

4. Visitez le [site de soumission Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)et envoyez vos fichiers .cab.

### <a name="what-happens-after-a-file-is-submitted"></a>Que se passe-t-il après l’envoi d’un fichier ?

Votre soumission est immédiatement analysée par nos systèmes pour vous donner la dernière détermination avant même qu’un analyste commence à gérer votre cas. Il est possible qu’un fichier ait déjà été soumis et traité par un analyste. Dans ces cas-là, une décision est prise rapidement.

Pour les soumissions qui n’ont pas encore été traitées, elles sont classées par ordre de priorité pour l’analyse comme suit :

- Les fichiers courants susceptibles d’avoir un impact sur un grand nombre d’ordinateurs ont une priorité plus élevée.
- Les clients authentifiés, en particulier les clients d’entreprise disposant [d’ID Software Assurance valides,](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) bénéficient d’une priorité plus élevée.
- Les soumissions marquées comme haute priorité par les titulaires SAID sont immédiatement considérées.

Pour rechercher les mises à jour concernant votre soumission, connectez-vous au [site de soumission Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission).

> [!TIP]
> Pour plus d’informations, consultez [Envoyer des fichiers à des fins d’analyse](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>Partie 5 : Examiner et ajuster vos paramètres de protection contre les menaces

Microsoft Defender pour point de terminaison offre une grande variété d’options, notamment la possibilité d’affiner les paramètres pour différentes fonctionnalités. Si vous recevez de nombreux faux positifs, veillez à passer en revue les paramètres de protection contre les menaces de votre organisation. Vous devrez peut-être effectuer quelques ajustements pour :

- [Protection fournie par le cloud](#cloud-delivered-protection)
- [Correction des applications potentiellement indésirables](#remediation-for-potentially-unwanted-applications)
- [Examen et correction automatisés](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>Protection fournie par le cloud

Vérifiez le niveau de protection fourni par le cloud pour Antivirus Microsoft Defender. Par défaut, la protection fournie par le cloud est définie sur **Non configuré**, ce qui correspond à un niveau de protection normal pour la plupart des organisations. Si votre protection fournie par le cloud est définie sur **Tolérance Élevée**, **Élevée +** ou **Zéro**, vous pouvez rencontrer un plus grand nombre de faux positifs.

> [!TIP]
> Pour en savoir plus sur la configuration de votre protection fournie par le cloud, consultez [Spécifier le niveau de protection fourni par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour modifier ou définir vos paramètres de protection fournis par le cloud. Toutefois, vous pouvez utiliser d’autres méthodes, telles que [stratégie de groupe](/azure/active-directory-domain-services/manage-group-policy) (voir [Gérer Microsoft Defender pour point de terminaison](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>Utilisez Microsoft Endpoint Manager pour examiner et modifier les paramètres de protection fournis par le cloud (pour les stratégies existantes)

1. Accédez au centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **l’antivirus** **de sécurité** \> de point de terminaison, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante ou si vous souhaitez créer une stratégie, passez à [la procédure suivante](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy)).

3. Sous **Gérer**, sélectionnez **Propriétés**. Ensuite, en regard **des paramètres de configuration**, choisissez **Modifier**.

4. Développez **la protection cloud** et passez en revue votre paramètre actuel dans la ligne de **niveau de protection fournie par le cloud** . Nous vous recommandons de définir la protection fournie par le cloud sur **Non configuré,** ce qui offre une protection forte tout en réduisant les risques d’obtention de faux positifs.

5. Choisissez **Vérifier + enregistrer**, puis **Enregistrer**.

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>Utiliser Microsoft Endpoint Manager pour définir des paramètres de protection fournis par le cloud (pour une nouvelle stratégie)

1. Accédez au centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez **Antivirus** \> **de sécurité de point de terminaison** \> **+ Créer une stratégie**.

3. Pour **La plateforme**, sélectionnez une option, puis, pour **Profil**, sélectionnez **Antivirus** ou **Antivirus Microsoft Defender** (l’option spécifique dépend de ce que vous avez sélectionné pour **Platform**.) Ensuite, **choisissez Créer**.

4. Sous l’onglet **De base** , spécifiez un nom et une description pour la stratégie. Sélectionnez **Suivant**.

5. Sous l’onglet **Paramètres de configuration** , développez la **protection cloud** et spécifiez les paramètres suivants :

   - **Définissez la valeur Oui pour activer la protection fournie par le cloud**.
   - Définissez **Niveau de protection assuré par le cloud** sur **Non configuré**. (Ce niveau fournit un niveau de protection fort par défaut tout en réduisant les chances d’obtenir des faux positifs.)

6. Sous l’onglet **Balises d’étendue** , si vous utilisez des balises d’étendue dans votre organisation, spécifiez des balises d’étendue pour la stratégie. (Voir [Balises d’étendue](/mem/intune/fundamentals/scope-tags).)

7. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Si vous avez besoin d’aide pour les affectations, consultez [Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. Sous l’onglet **Vérifier + créer** , passez en revue les paramètres, puis choisissez **Créer**.

### <a name="remediation-for-potentially-unwanted-applications"></a>Correction des applications potentiellement indésirables

Les applications potentiellement indésirables (PUA) sont une catégorie de logiciels qui peuvent entraîner l’exécution lente des appareils, l’affichage de publicités inattendues ou l’installation d’autres logiciels qui peuvent être inattendus ou indésirables. Les exemples de PUA incluent les logiciels publicitaires, les logiciels de regroupement et les logiciels d’évasion qui se comportent différemment avec les produits de sécurité. Bien que PUA ne soit pas considéré comme un programme malveillant, certains types de logiciels sont PUA en fonction de leur comportement et de leur réputation.

> [!TIP]
> Pour en savoir plus sur PUA, consultez [Détecter et bloquer les applications potentiellement indésirables](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

Selon les applications que votre organisation utilise, vous pouvez obtenir des faux positifs en raison de vos paramètres de protection PUA. Si nécessaire, envisagez d’exécuter la protection PUA en mode audit pendant un certain temps, ou appliquez la protection PUA à un sous-ensemble d’appareils de votre organisation. La protection PUA peut être configurée pour le navigateur Microsoft Edge et pour Antivirus Microsoft Defender.

Nous vous recommandons d’utiliser [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) pour modifier ou définir des paramètres de protection PUA. Toutefois, vous pouvez utiliser d’autres méthodes, telles que [stratégie de groupe](/azure/active-directory-domain-services/manage-group-policy) (voir [Gérer Microsoft Defender pour point de terminaison](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>Utiliser Microsoft Endpoint Manager pour modifier la protection PUA (pour les profils de configuration existants)

1. Accédez au centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisissez les **profils de configuration** **des appareils**\>, puis sélectionnez une stratégie existante. (Si vous n’avez pas de stratégie existante ou si vous souhaitez en créer une, passez à [la procédure suivante](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile).)

3. Sous **Gérer**, choisissez **Propriétés**, puis, en regard **des paramètres de configuration**, **choisissez Modifier**.

4. Sous l’onglet **Paramètres de configuration**, faites défiler vers le bas et développez **Antivirus Microsoft Defender**.

5. **Définissez Détecter les applications potentiellement indésirables** sur **Audit**. (Vous pouvez le désactiver, mais en utilisant le mode audit, vous pourrez voir les détections.)

6. Choisissez **Vérifier + enregistrer**, puis **Enregistrer**.

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>Utiliser Microsoft Endpoint Manager pour définir la protection PUA (pour un nouveau profil de configuration)

1. Accédez au centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) et connectez-vous.

2. Choisir les **profils** \> de configuration **des appareils** \> **+ Créer un profil**.

3. Pour la **plateforme**, choisissez **Windows 10 et versions ultérieures**, puis, pour **Profil**, sélectionnez **Restrictions d’appareil**.

4. Sous l’onglet **De base** , spécifiez un nom et une description pour votre stratégie. Sélectionnez **Suivant**.

5. Sous l’onglet **Paramètres de configuration**, faites défiler vers le bas et développez **Antivirus Microsoft Defender**.

6. **Définissez Détecter les applications potentiellement indésirables** sur **Audit**, puis choisissez **Suivant**. (Vous pouvez désactiver la protection PUA, mais en utilisant le mode audit, vous pourrez voir les détections.)

7. Sous l’onglet **Affectations** , spécifiez les utilisateurs et les groupes auxquels votre stratégie doit être appliquée, puis choisissez **Suivant**. (Si vous avez besoin d’aide pour les affectations, consultez [Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. Sous **l’onglet Règles d’applicabilité** , spécifiez les éditions ou versions du système d’exploitation à inclure ou exclure de la stratégie. Par exemple, vous pouvez définir la stratégie à appliquer à tous les appareils certaines éditions de Windows 10. Sélectionnez **Suivant**.

9. Sous l’onglet **Vérifier + créer** , passez en revue vos paramètres, puis choisissez **Créer**.

### <a name="automated-investigation-and-remediation"></a>Investigation et résolution automatiques

Les fonctionnalités [d’investigation et de correction automatisées](automated-investigations.md) (AIR) sont conçues pour examiner les alertes et prendre des mesures immédiates pour résoudre les violations. À mesure que des alertes sont déclenchées et qu’une enquête automatisée s’exécute, un verdict est généré pour chaque élément de preuve examiné. Les verdicts peuvent être *malveillants*, *suspects* ou *introuvables*.

Selon le [niveau d’automatisation](/microsoft-365/security/defender-endpoint/automation-levels) défini pour votre organisation et d’autres paramètres de sécurité, des actions de correction sont effectuées sur les artefacts considérés comme *malveillants* ou *suspects*. Dans certains cas, les actions de correction se produisent automatiquement ; dans d’autres cas, les actions de correction sont effectuées manuellement ou uniquement après approbation par votre équipe des opérations de sécurité.

- [En savoir plus sur les niveaux d’automatisation](/microsoft-365/security/defender-endpoint/automation-levels) ; Et puis
- [Configurez les fonctionnalités AIR dans Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation).

> [!IMPORTANT]
> Nous vous recommandons d’utiliser *l’automatisation complète* pour l’investigation et la correction automatisées. Ne désactivez pas ces fonctionnalités en raison d’un faux positif. Au lieu de cela, utilisez [des indicateurs « autoriser » pour définir des exceptions](#indicators-for-microsoft-defender-for-endpoint), et conservez l’investigation et la correction automatisées définies pour prendre automatiquement les mesures appropriées. En suivant [ces instructions](automation-levels.md#levels-of-automation) , vous réduisez le nombre d’alertes que votre équipe des opérations de sécurité doit gérer.

## <a name="still-need-help"></a>Encore besoin d’aide ?

Si vous avez suivi toutes les étapes décrites dans cet article et que vous avez encore besoin d’aide, contactez le support technique.

1. Accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> et connectez-vous.

2. Dans le coin supérieur droit, sélectionnez le point d’interrogation (**?**), puis sélectionnez **support Microsoft**.

3. Dans la fenêtre **Assistant Support** , décrivez votre problème, puis envoyez votre message. À partir de là, vous pouvez ouvrir une demande de service.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md) 

## <a name="see-also"></a>Voir aussi

[Gérer Microsoft Defender pour point de terminaison](manage-mde-post-migration.md)

[Vue d’ensemble du portail Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
