---
title: Effectuer des actions de réponse sur un fichier dans Microsoft Defender pour point de terminaison
description: Effectuez des actions de réponse sur les alertes liées aux fichiers en arrêtant et en mettant en quarantaine un fichier ou en bloquant un fichier et en vérifiant les détails de l’activité.
keywords: répondre, arrêter et mettre en quarantaine, bloquer un fichier, analyser en profondeur
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
ms.openlocfilehash: 53f9516c327272d2bee517e1a4236caaaedbe736
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67581643"
---
# <a name="take-response-actions-on-a-file"></a>Prendre des mesures de réponse sur un fichier

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-responddile-abovefoldlink)

Répondez rapidement aux attaques détectées en arrêtant et en mettant en quarantaine des fichiers ou en bloquant un fichier. Après avoir pris des mesures sur les fichiers, vous pouvez vérifier les détails de l’activité dans le Centre d’actions.

Les actions de réponse sont disponibles sur la page de profil détaillé d’un fichier. Une fois sur cette page, vous pouvez basculer entre les mises en page nouvelles et anciennes en basculant la **nouvelle page fichier**. Le reste de cet article décrit la mise en page la plus récente.

Les actions de réponse s’exécutent en haut de la page du fichier et incluent :

- Arrêter et mettre en quarantaine le fichier
- Ajouter un indicateur
- Télécharger un fichier
- Consulter un spécialiste des menaces
- Centre de notifications

Vous pouvez également envoyer des fichiers pour une analyse approfondie afin d’exécuter le fichier dans un bac à sable cloud sécurisé. Une fois l’analyse terminée, vous obtenez un rapport détaillé qui fournit des informations sur le comportement du fichier. Vous pouvez envoyer des fichiers pour une analyse approfondie et lire des rapports passés en sélectionnant l’onglet **Analyse approfondie** . Il se trouve sous les cartes d’informations de fichier.

Certaines actions nécessitent certaines autorisations. Le tableau suivant décrit l’action que certaines autorisations peuvent effectuer sur les fichiers exécutables portables (PE) et non PE :

|Autorisation|Fichiers PE|Fichiers non PE|
|---|:---:|:---:|
|Afficher les données|X|X|
|Investigation des alertes|&#x2611;|X|
|Base de la réponse en direct|X|X|
|Réponse dynamique avancée|&#x2611;|&#x2611;|

Pour plus d’informations sur les rôles, consultez [Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle](user-roles.md).

## <a name="stop-and-quarantine-files-in-your-network"></a>Arrêter et mettre en quarantaine des fichiers de votre réseau

Vous pouvez contenir une attaque dans votre organisation en arrêtant le processus malveillant et en mettant en quarantaine le fichier où il a été observé.

> [!IMPORTANT]
> Vous ne pouvez effectuer cette action que si :
>
> - L’appareil sur lequel vous effectuez l’action est en cours d’exécution Windows 10, version 1703 ou ultérieure, et Windows 11
> - Le fichier n’appartient pas à des éditeurs tiers approuvés ou n’est pas signé par Microsoft
> - L’Antivirus Microsoft Defender doit au moins s’exécuter en mode passif. Pour plus d’informations, consultez [Compatibilité de l’antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

L’action **Arrêter et mettre en quarantaine le fichier** inclut l’arrêt des processus en cours d’exécution, la mise en quarantaine des fichiers et la suppression de données persistantes telles que les clés de Registre.

Cette action prend effet sur les appareils avec Windows 10, version 1703 ou ultérieure, et Windows 11, où le fichier a été observé au cours des 30 derniers jours.

> [!NOTE]
> Vous pourrez restaurer le fichier à partir de la mise en quarantaine à tout moment.

### <a name="stop-and-quarantine-files"></a>Arrêter et mettre en quarantaine des fichiers

1. Sélectionnez le fichier que vous souhaitez arrêter et mettre en quarantaine. Vous pouvez sélectionner un fichier dans l’une des vues suivantes ou utiliser la zone de recherche :

   - **Alertes** : cliquez sur les liens correspondants à partir de la description ou des détails dans la chronologie de l’histoire des alertes
   - **Zone de recherche** : sélectionnez **Fichier** dans le menu déroulant et entrez le nom du fichier

   > [!NOTE]
   > L’action de fichier d’arrêt et de mise en quarantaine est limitée à un maximum de 1 000 appareils. Pour arrêter un fichier sur un plus grand nombre d’appareils, consultez [Ajouter un indicateur pour bloquer ou autoriser le fichier](#add-indicator-to-block-or-allow-a-file).

2. Accédez à la barre supérieure, puis **sélectionnez Arrêter et mettre en quarantaine le fichier**.

   :::image type="content" source="images/atp-stop-quarantine-file.png" alt-text="Action arrêter et mettre en quarantaine le fichier" lightbox="images/atp-stop-quarantine-file.png":::

3. Spécifiez une raison, puis **sélectionnez Confirmer**.

   :::image type="content" source="images/atp-stop-quarantine.png" alt-text="Page arrêter et mettre en quarantaine le fichier" lightbox="images/atp-stop-quarantine.png":::

   Le Centre d’actions affiche les informations de soumission :

   :::image type="content" source="images/atp-stopnquarantine-file.png" alt-text="Centre d’action arrêter et mettre en quarantaine les fichiers" lightbox="images/atp-stopnquarantine-file.png":::

   - **Temps d’envoi** : indique le moment où l’action a été soumise.
   - **Réussite** : indique le nombre d’appareils sur lesquels le fichier a été arrêté et mis en quarantaine.
   - **Échec** : affiche le nombre d’appareils sur lesquels l’action a échoué et des détails sur l’échec.
   - **En attente** : indique le nombre d’appareils sur lesquels le fichier doit encore être arrêté et mis en quarantaine. Cela peut prendre du temps lorsque l’appareil est hors connexion ou n’est pas connecté au réseau.

4. Sélectionnez l’un des indicateurs d’état pour afficher plus d’informations sur l’action. Par exemple, sélectionnez **Échec** pour voir où l’action a échoué.

#### <a name="notification-on-device-userf"></a>Notification sur device userf

Lorsque le fichier est supprimé d’un appareil, la notification suivante s’affiche :

:::image type="content" source="images/atp-notification-file.png" alt-text="Notification d’un utilisateur sur l’appareil" lightbox="images/atp-notification-file.png":::

Dans la chronologie de l’appareil, un nouvel événement est ajouté pour chaque appareil où un fichier a été arrêté et mis en quarantaine.

Un avertissement s’affiche avant que l’action ne soit implémentée pour les fichiers largement utilisés dans toute une organisation. Il s’agit de vérifier que l’opération est prévue.

## <a name="restore-file-from-quarantine"></a>Restaurer un fichier à partir de la mise en quarantaine

Vous pouvez restaurer et supprimer un fichier de la quarantaine si vous avez déterminé qu’il est propre après une enquête. Exécutez la commande suivante sur chaque appareil sur lequel le fichier a été mis en quarantaine.

1. Ouvrez une invite de ligne de commande avec élévation de privilèges sur l’appareil :

   1. Accéder à **Démarrer** et taper _cmd_.

   1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante, puis **appuyez sur Entrée** :

   ```dos
   "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
   ```

   > [!NOTE]
   > Dans certains scénarios, **threatName** peut apparaître comme suit : EUS:Win32/CustomEnterpriseBlock!cl.
   >
   > Defender pour point de terminaison restaure tous les fichiers bloqués personnalisés qui ont été mis en quarantaine sur cet appareil au cours des 30 derniers jours.

> [!IMPORTANT]
> Un fichier qui a été mis en quarantaine en tant que menace réseau potentielle peut ne pas être récupérable. Si un utilisateur tente de restaurer le fichier après la mise en quarantaine, ce fichier n’est peut-être pas accessible. Cela peut être dû au fait que le système n’a plus d’informations d’identification réseau pour accéder au fichier. En règle générale, il s’agit d’un résultat d’une connexion temporaire à un système ou à un dossier partagé, et les jetons d’accès ont expiré.

## <a name="download-or-collect-file"></a>Télécharger ou collecter un dossier

La sélection d’un **fichier de téléchargement** à partir des actions de réponse vous permet de télécharger une archive locale protégée par mot de passe .zip contenant votre fichier. Un menu volant s’affiche pour vous permettre d’enregistrer une raison de télécharger le fichier et de définir un mot de passe.

Par défaut, vous devez être en mesure de télécharger les fichiers en quarantaine.

:::image type="content" source="images/atp-download-file-action.png" alt-text="Action de téléchargement du fichier" lightbox="images/atp-download-file-action.png":::

### <a name="download-quarantined-files"></a>Télécharger des fichiers mis en quarantaine

Les fichiers qui ont été mis en quarantaine par l’Antivirus Microsoft Defender ou votre équipe de sécurité seront enregistrés de manière conforme en fonction de vos [exemples de configurations de soumission](enable-cloud-protection-microsoft-defender-antivirus.md). Votre équipe de sécurité peut télécharger les fichiers directement à partir de la page de détails du fichier via le bouton « Télécharger le fichier ». **Cette fonctionnalité est activée par défaut**.

L’emplacement dépend des paramètres géographiques de votre organisation (UE, Royaume-Uni ou États-Unis). Un fichier mis en quarantaine ne sera collecté qu’une seule fois par organisation. Pour en savoir plus sur la protection des données de Microsoft à partir du portail d’approbation de services, consultez https://aka.ms/STP.

Le fait d’activer ce paramètre peut aider les équipes de sécurité à examiner les fichiers potentiellement incorrects et à examiner les incidents rapidement et de manière moins risquée. Toutefois, si vous devez désactiver ce paramètre, accédez à **Paramètres Points** \> de terminaison **Fonctionnalités** \> **avancées** \> **Télécharger les fichiers mis en quarantaine** pour ajuster le paramètre. [En savoir plus sur les fonctionnalités avancées](advanced-features.md)

#### <a name="backing-up-quarantined-files"></a>Sauvegarde de fichiers mis en quarantaine

Les utilisateurs peuvent être invités à fournir un consentement explicite avant de sauvegarder le fichier mis en quarantaine, en fonction de votre [exemple de configuration de soumission](enable-cloud-protection-microsoft-defender-antivirus.md#use-group-policy-to-turn-on-cloud-protection).

Cette fonctionnalité ne fonctionnera pas si l’exemple de soumission est désactivé. Si la soumission automatique d’exemples est définie pour demander l’autorisation de l’utilisateur, seuls les exemples que l’utilisateur accepte d’envoyer sont collectés.

> [!IMPORTANT]
> Télécharger les exigences relatives aux fichiers mis en quarantaine :
>
> - Votre organisation utilise l’antivirus Microsoft Defender en mode actif
> - La version du moteur antivirus est 1.1.17300.4 ou ultérieure. Voir [les versions mensuelles de la plateforme et du moteur](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)
> - La protection basée sur le cloud est activée. Voir [Activer la protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
> - L’exemple de soumission est activé
> - Les appareils ont Windows 10 version 1703 ou ultérieure, ou Windows Server 2016 ou 2019, ou Windows Server 2022 ou Windows 11

### <a name="collect-files"></a>Collecter des fichiers

Si un fichier n’est pas déjà stocké par Microsoft Defender pour point de terminaison, vous ne pouvez pas le télécharger. Au lieu de cela, vous **verrez** un bouton Collecter le fichier au même emplacement. Si aucun fichier n’a été vu dans l’organisation au cours des 30 derniers jours, **le fichier Collect** est désactivé.
> [!Important]
> Un fichier qui a été mis en quarantaine en tant que menace réseau potentielle peut ne pas être récupérable. Si un utilisateur tente de restaurer le fichier après la mise en quarantaine, ce fichier n’est peut-être pas accessible. Cela peut être dû au fait que le système n’a plus d’informations d’identification réseau pour accéder au fichier. En règle générale, il s’agit d’un résultat d’une connexion temporaire à un système ou à un dossier partagé, et les jetons d’accès ont expiré.

## <a name="add-indicator-to-block-or-allow-a-file"></a>Ajouter un indicateur pour bloquer ou autoriser un fichier

Empêchez la propagation d’une attaque dans votre organisation en interdisant les fichiers potentiellement malveillants ou les programmes malveillants suspectés. Si vous connaissez un fichier exécutable portable (PE) potentiellement malveillant, vous pouvez le bloquer. Cette opération empêche sa lecture, son écriture ou son exécution sur les appareils de votre organisation.

> [!IMPORTANT]
>
> - Cette fonctionnalité est disponible si votre organisation utilise l’antivirus Microsoft Defender et que la protection fournie par le cloud est activée. Pour plus d’informations, consultez [Gérer la protection fournie par le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
>
> - La version du client Antimalware doit être 4.18.1901.x ou ultérieure.
> - Cette fonctionnalité est conçue pour empêcher le téléchargement de logiciels malveillants (ou de fichiers potentiellement malveillants) à partir du web. Il prend actuellement en charge les fichiers exécutables portables (PE), y compris _les fichiers.exe_ et _.dll_ . La couverture sera prolongée au fil du temps.
> - Cette action de réponse est disponible pour les appareils sur Windows 10, version 1703 ou ultérieure et Windows 11.
> - La fonction allow ou block ne peut pas être effectuée sur les fichiers si la classification du fichier existe dans le cache de l’appareil avant l’action d’autorisation ou de blocage.

> [!NOTE]
> Le fichier PE doit se trouver dans la chronologie de l’appareil pour que vous puissiez effectuer cette action.
>
> Il peut y avoir quelques minutes de latence entre le moment où l’action est effectuée et le fichier réel bloqué.

### <a name="enable-the-block-file-feature"></a>Activer la fonctionnalité de fichier de bloc

Pour commencer à bloquer des fichiers, vous devez d’abord [activer le **bloc ou autoriser** la fonctionnalité](advanced-features.md) dans Paramètres.

### <a name="allow-or-block-file"></a>Autoriser ou bloquer un fichier

Lorsque vous ajoutez un hachage d’indicateur pour un fichier, vous pouvez choisir de déclencher une alerte et de bloquer le fichier chaque fois qu’un appareil de votre organisation tente de l’exécuter.

Les fichiers automatiquement bloqués par un indicateur ne s’affichent pas dans le centre d’action du fichier, mais les alertes restent visibles dans la file d’attente des alertes.

Pour plus d’informations sur le blocage et le déclenchement d’alertes sur les fichiers, consultez [gérer les indicateurs](manage-indicators.md) .

Pour arrêter de bloquer un fichier, supprimez l’indicateur. Vous pouvez le faire via l’action **Modifier l’indicateur** sur la page de profil du fichier. Cette action est visible à la même position que l’action **Ajouter un indicateur** , avant d’ajouter l’indicateur.

Vous pouvez également modifier les indicateurs à partir de la page **Paramètres**, sous **Indicateurs de règles**\>. Les indicateurs sont répertoriés dans cette zone par le hachage de leur fichier.

## <a name="consult-a-threat-expert"></a>Consulter un spécialiste des menaces

Consultez un expert en menaces Microsoft pour obtenir plus d’informations sur un appareil potentiellement compromis ou déjà compromis. Spécialistes des menaces Microsoft sont engagés directement à partir du portail Microsoft 365 Defender pour obtenir une réponse rapide et précise. Les experts fournissent des insights sur un appareil potentiellement compromis et vous aident à comprendre les menaces complexes et les notifications d’attaque ciblées. Ils peuvent également fournir des informations sur les alertes ou un contexte de renseignement sur les menaces que vous voyez dans le tableau de bord de votre portail.

Pour plus [d’informations, consultez un expert Microsoft sur les menaces](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) .

## <a name="check-activity-details-in-action-center"></a>Vérifier les détails de l’activité dans le Centre de notifications

Le **Centre d’actions** fournit des informations sur les actions qui ont été effectuées sur un appareil ou un fichier. Vous pouvez afficher les détails suivants :

- Collection de packages d’investigation
- Analyse antivirus
- Restriction d’application
- Isolation de l’appareil

Tous les autres détails connexes sont également affichés, tels que la date/l’heure de soumission, l’envoi de l’utilisateur et si l’action a réussi ou échoué.

:::image type="content" source="images/action-center-details.png" alt-text="Centre d’action avec des informations" lightbox="images/action-center-details.png":::

## <a name="deep-analysis"></a>Analyse profonde

Les enquêtes sur la cybersécurité sont généralement déclenchées par une alerte. Les alertes sont liées à un ou plusieurs fichiers observés qui sont souvent nouveaux ou inconnus. La sélection d’un fichier vous permet d’accéder à la vue de fichier dans laquelle vous pouvez voir les métadonnées du fichier. Pour enrichir les données associées au fichier, vous pouvez soumettre le fichier à des fins d’analyse approfondie.

La fonctionnalité d’analyse approfondie exécute un fichier dans un environnement cloud sécurisé et entièrement instrumenté. Les résultats d’analyse approfondie montrent les activités du fichier, les comportements observés et les artefacts associés, tels que les fichiers supprimés, les modifications du Registre et la communication avec les adresses IP.
L’analyse approfondie prend actuellement en charge une analyse approfondie des fichiers exécutables portables (PE) (y compris _les fichiers.exe_ et _.dll_ ).

L’analyse approfondie d’un fichier prend plusieurs minutes. Une fois l’analyse de fichier terminée, l’onglet Analyse approfondie est mis à jour pour afficher un résumé et la date et l’heure des derniers résultats disponibles.

Le résumé de l’analyse approfondie inclut une liste des *comportements observés*, dont certains peuvent indiquer une activité malveillante, et *des observables*, y compris les adresses IP et les fichiers contactés créés sur le disque. Si rien n’a été trouvé, ces sections affichent un bref message.

Les résultats d’une analyse approfondie sont mis en correspondance avec le renseignement sur les menaces et toutes les correspondances génèrent des alertes appropriées.

Utilisez la fonctionnalité d’analyse approfondie pour examiner les détails d’un fichier, généralement lors d’une investigation d’une alerte ou pour toute autre raison où vous soupçonnez un comportement malveillant. Cette fonctionnalité est disponible sous l’onglet **Analyse approfondie** , sur la page de profil du fichier.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4aAYy?rel=0]

**L’envoi pour analyse approfondie** est activé lorsque le fichier est disponible dans la collection d’exemples de back-end Defender pour point de terminaison, ou s’il a été observé sur un appareil Windows 10 qui prend en charge l’envoi à une analyse approfondie.

> [!NOTE]
> Seuls les fichiers de Windows 10 et de Windows 11 peuvent être collectés automatiquement.

Vous pouvez également envoyer un exemple via le [portail Microsoft 365 Defender](https://www.microsoft.com/security/portal/submission/submit.aspx) si le fichier n’a pas été observé sur un appareil Windows 10 (ou Windows 11), et attendre que le bouton **Envoyer pour une analyse approfondie** soit disponible.

> [!NOTE]
> En raison des flux de traitement back-end dans le portail Microsoft 365 Defender, il peut y avoir jusqu’à 10 minutes de latence entre la soumission de fichiers et la disponibilité de la fonctionnalité d’analyse approfondie dans Defender pour point de terminaison.

### <a name="submit-files-for-deep-analysis"></a>Envoyer des fichiers pour une analyse approfondie

1. Sélectionnez le fichier que vous souhaitez envoyer pour une analyse approfondie. Vous pouvez sélectionner ou rechercher un fichier à partir de l’une des vues suivantes :

    - **Alertes** : sélectionnez les liens de fichier dans la **description** ou les détails dans la chronologie de l’histoire des **alertes**
    - **Liste des appareils** : sélectionnez les liens de fichier dans la **section Description** ou **Détails** de la section **Appareil dans l’organisation**
    - **Zone de recherche** : sélectionnez **Fichier** dans le menu déroulant et entrez le nom du fichier

2. Sous l’onglet **Analyse approfondie** de la vue fichier, **sélectionnez Envoyer**.

   :::image type="content" source="images/submit-file.png" alt-text="Bouton Envoyer des fichiers PE" lightbox="images/submit-file.png":::

   > [!NOTE]
   > Seuls les fichiers PE sont pris en charge, y compris _les fichiers.exe_ et _.dll_ .

   Une barre de progression s’affiche et fournit des informations sur les différentes étapes de l’analyse. Vous pouvez ensuite afficher le rapport lorsque l’analyse est terminée.

> [!NOTE]
> Selon la disponibilité de l’appareil, le temps de collecte des exemples peut varier. Il existe un délai d’expiration de 3 heures pour la collecte d’exemples. La collection échoue et l’opération est abandonnée si aucun appareil Windows 10 en ligne (ou Windows 11) n’est signalé à ce moment-là. Vous pouvez soumettre à nouveau des fichiers pour une analyse approfondie afin d’obtenir de nouvelles données sur le fichier.

### <a name="view-deep-analysis-reports"></a>Afficher les rapports d’analyse approfondie

Affichez le rapport d’analyse approfondie fourni pour obtenir des insights plus détaillés sur le fichier que vous avez envoyé. Cette fonctionnalité est disponible dans le contexte d’affichage de fichiers.

Vous pouvez afficher le rapport complet qui fournit des détails sur les sections suivantes :

- Behaviors
- Observables

Les détails fournis peuvent vous aider à déterminer s’il existe des indications d’une attaque potentielle.

1. Sélectionnez le fichier que vous avez envoyé pour une analyse approfondie.
2. Sélectionnez l’onglet **Analyse approfondie** . S’il existe des rapports précédents, le résumé du rapport s’affiche dans cet onglet.

   :::image type="content" source="images/analysis-results-nothing500.png" alt-text="Rapport d’analyse approfondie présentant des informations détaillées sur un certain nombre de catégories" lightbox="images/analysis-results-nothing500.png":::

#### <a name="troubleshoot-deep-analysis"></a>Résoudre les problèmes d’analyse approfondie

Si vous rencontrez un problème lors de la tentative d’envoi d’un fichier, essayez chacune des étapes de dépannage suivantes.

1. Vérifiez que le fichier en question est un fichier PE. Les fichiers PE ont généralement _des_ extensions.exeou _.dll_ (programmes exécutables ou applications).

2. Vérifiez que le service a accès au fichier, qu’il existe toujours et qu’il n’a pas été endommagé ou modifié.

3. Patientez un court instant et réessayez d’envoyer le fichier. La file d’attente peut être pleine ou une erreur de connexion ou de communication temporaire s’est produite.

4. Si l’exemple de stratégie de collecte n’est pas configuré, le comportement par défaut est d’autoriser la collecte d’exemples. S’il est configuré, vérifiez que le paramètre de stratégie autorise la collecte d’exemples avant de soumettre à nouveau le fichier. Lorsque l’exemple de collection est configuré, vérifiez la valeur de Registre suivante :

    ```text
    Path: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
    Name: AllowSampleCollection
    Type: DWORD
    Hexadecimal value :
      Value = 0 - block sample collection
      Value = 1 - allow sample collection
    ```

5. Modifiez l’unité organisationnelle par le biais de la stratégie de groupe. Pour plus d’informations, consultez [Configurer avec stratégie de groupe](configure-endpoints-gp.md).

6. Si ces étapes ne résolvent pas le problème, contactez le support technique.

## <a name="related-topics"></a>Voir aussi

- [Prendre des mesures de réponse sur un appareil](respond-machine-alerts.md)
- [Examiner des fichiers](investigate-files.md)
- [Actions de réponse manuelles dans Microsoft Defender pour point de terminaison Plan 1](defender-endpoint-plan-1.md#manual-response-actions)
