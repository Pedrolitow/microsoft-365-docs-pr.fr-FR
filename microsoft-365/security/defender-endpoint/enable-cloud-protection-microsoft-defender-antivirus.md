---
title: Activer la protection cloud dans Antivirus Microsoft Defender
description: Activez la protection cloud pour bénéficier des fonctionnalités de protection rapides et avancées.
keywords: Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, cloud, bloquer à première vue
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 02/03/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 95269837e4ad26b4928a2ff82df65a259c707290
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790655"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Activer la protection cloud dans Antivirus Microsoft Defender

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Plateformes**
- Windows

[La protection cloud dans Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) offre une protection précise, en temps réel et intelligente. La protection cloud doit être activée par défaut ; toutefois, vous pouvez configurer la protection cloud en fonction des besoins de votre organisation.

## <a name="methods-to-configure-cloud-protection"></a>Méthodes de configuration de la protection cloud

Vous pouvez activer ou désactiver Antivirus Microsoft Defender protection cloud à l’aide de l’une des méthodes suivantes :

- Microsoft Endpoint Manager, qui inclut Microsoft Intune et Configuration Manager
- Stratégie de groupe
- Cmdlets PowerShell

Vous pouvez également activer ou désactiver la protection cloud sur des points de terminaison individuels à l’aide de l’application Sécurité Windows. 

Pour plus d’informations sur les exigences spécifiques de connectivité réseau pour garantir que vos points de terminaison peuvent se connecter au service de protection cloud, consultez [Configurer et valider les connexions réseau](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> Dans Windows 10 et Windows 11, il n’existe aucune différence entre les options de création de rapports **de base** et **avancées** décrites dans cet article. Il s’agit d’une distinction héritée, et le choix de l’un ou l’autre des paramètres entraîne le même niveau de protection cloud. Il n’existe aucune différence dans le type ou la quantité d’informations partagées. Pour plus d’informations sur ce que nous collectons, consultez la [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Utiliser Intune pour activer la protection cloud

1. Accédez au centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Dans le volet **Accueil** , sélectionnez **Configuration de l’appareil > Profils**.

3. Sélectionnez le type de profil **Restrictions d’appareil** que vous souhaitez configurer. Si vous devez créer un type de profil de **restrictions** d’appareil, consultez [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionner **les paramètres de configuration des propriétés**  \> : Modifier \> **Antivirus Microsoft Defender**.

5. Dans le commutateur **de protection fournie par le cloud** , **sélectionnez Activer**.

6. Dans la liste **déroulante Inviter les utilisateurs avant l’exemple de soumission** , **sélectionnez Envoyer toutes les données automatiquement**.

Pour plus d’informations sur Intune profils d’appareil, notamment sur la création et la configuration de leurs paramètres, voir [Que sont Microsoft Intune profils d’appareil ?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Utiliser Microsoft Endpoint Manager pour activer la protection cloud

1. Accédez au centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Choisissez **l’antivirus de sécurité de point de terminaison**\>.

3. Sélectionnez un profil antivirus. (Si vous n’en avez pas encore, ou si vous souhaitez créer un profil, consultez [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **Propriétés**. Ensuite, en regard **des paramètres de configuration**, choisissez **Modifier**.

5. Développez **la protection cloud**, puis, dans la liste des **niveaux de protection fournis par le cloud** , sélectionnez l’une des options suivantes :
   - **Élevé** : applique un niveau de détection fort.
   - **Haut plus** : utilise le **niveau élevé** et applique davantage de mesures de protection (peut affecter les performances du client).
   - **Tolérance zéro** : bloque tous les exécutables inconnus.

6. Sélectionnez **Vérifier + enregistrer**, puis **enregistrer**.

Pour plus d’informations sur la configuration de Microsoft Endpoint Configuration Manager, consultez [Comment créer et déployer des stratégies anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Utiliser stratégie de groupe pour activer la protection cloud

1. Sur votre appareil de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur**.

3. Sélectionnez **Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** >  **Antivirus Microsoft Defender > MAPS**

    > [!NOTE]
    > Les paramètres MAPS sont égaux à la protection fournie par le cloud.

5. Double-cliquez sur **Joindre Microsoft MAPS**. Vérifiez que l’option est activée et définie sur **Cartes de base** ou **Cartes avancées**. Sélectionnez **OK**.

    Vous pouvez choisir d’envoyer des informations de base ou supplémentaires sur les logiciels détectés :

    - Cartes de base : l’appartenance de base envoie des informations de base à Microsoft sur les programmes malveillants et les logiciels potentiellement indésirables détectés sur votre appareil. Les informations incluent l’endroit d’où provient le logiciel (comme les URL et les chemins partiels), les actions prises pour résoudre la menace et si les actions ont réussi.

    - Cartes avancées : en plus des informations de base, l’appartenance avancée envoie des informations détaillées sur les programmes malveillants et les logiciels potentiellement indésirables, y compris le chemin d’accès complet au logiciel, ainsi que des informations détaillées sur la façon dont le logiciel a affecté votre appareil.

6. Double-cliquez sur **Envoyer des exemples de fichier quand une analyse plus approfondie est nécessaire**. Vérifiez que la première option est **activée et que** les autres options sont définies sur l’une des options suivantes :

   - **Envoyer des exemples sécurisés** (1)
   - **Envoyer tous les exemples** (3)

   >[!NOTE]
   > L’option **Envoyer des échantillons sécurisés** (1) signifie que la plupart des échantillons seront envoyés automatiquement. Les fichiers susceptibles de contenir des informations personnelles sont toujours invités et nécessitent une confirmation supplémentaire.
   > La définition de l’option **Always Prompt** (0) réduit l’état de protection de l’appareil. Le fait de le définir sur **Ne jamais envoyer** (2) signifie que la fonctionnalité [Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md) de Microsoft Defender pour point de terminaison ne fonctionnera pas.

7. Sélectionnez **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Utiliser des applets de commande PowerShell pour activer la protection cloud

Les applets de commande suivantes peuvent activer la protection cloud :

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [Antivirus Microsoft Defender applets de commande](/powershell/module/defender/). [Fournisseur CSP de stratégie - Defender](/windows/client-management/mdm/policy-csp-defender) contient également plus d’informations spécifiquement sur [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> Vous pouvez définir **-SubmitSamplesConsent** `SendSafeSamples` sur (paramètre par défaut, recommandé) `NeverSend`ou `AlwaysPrompt`. Le `SendSafeSamples` paramètre signifie que la plupart des exemples seront envoyés automatiquement. Les fichiers susceptibles de contenir des informations personnelles se traduisent par une invite de continuer et nécessiteront une confirmation.
> Les `NeverSend` paramètres et `AlwaysPrompt` les paramètres réduisent le niveau de protection de l’appareil. En outre, le `NeverSend` paramètre signifie que la fonctionnalité [Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md) de Microsoft Defender pour point de terminaison ne fonctionnera pas.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Utiliser Windows Management Instruction (WMI) pour activer la protection cloud

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) pour les propriétés suivantes :

```WMI
MAPSReporting
SubmitSamplesConsent
```

Pour plus d’informations sur les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Activer la protection cloud sur des clients individuels avec l’application Sécurité Windows

> [!NOTE]
> Si le **paramètre Configurer le remplacement du paramètre local pour la création de rapports Microsoft MAPS** stratégie de groupe est défini sur **Désactivé**, le paramètre de **protection cloud** dans Windows Paramètres sera grisé et indisponible. Les modifications apportées via un objet de stratégie de groupe doivent d’abord être déployées vers les points de terminaison individuels avant que le paramètre soit mis à jour dans les Paramètres Windows.

1. Ouvrez l’application Sécurité Windows en sélectionnant l’icône du bouclier dans la barre des tâches ou en recherchant **Sécurité Windows** dans le menu démarrer.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche), puis, sous **Gérer les paramètres** , sélectionnez **Virus & paramètres de protection contre les menaces**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Paramètres de protection contre les menaces & virus" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Vérifiez que **la protection basée sur le cloud** et la **soumission automatique d’exemples** sont activées **.**

   > [!NOTE]
   > Si l’envoi automatique d’exemples a été configuré avec stratégie de groupe le paramètre est grisé et indisponible.

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

- [Utiliser la protection cloud Microsoft dans Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- [Comment créer et déployer des stratégies anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Utiliser des cmdlets PowerShell pour gérer l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
