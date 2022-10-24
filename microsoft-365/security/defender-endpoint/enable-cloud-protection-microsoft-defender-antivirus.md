---
title: Activer la protection cloud dans Microsoft Defender Antivirus
description: Activez la protection cloud pour bénéficier de fonctionnalités de protection rapides et avancées.
keywords: Microsoft Defender Antivirus, anti-programme malveillant, sécurité, cloud, bloquer à la première consultation
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 10/24/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: fa0a72f68542b12df5edec8aa1f7d3a7603cc60d
ms.sourcegitcommit: 0ca3ab2abe07810e9b2cc2d806e3c6b9f35b146c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68684919"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Activer la protection cloud dans Microsoft Defender Antivirus

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Plateformes**
- Windows

[La protection cloud dans Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md) offre une protection précise, en temps réel et intelligente. La protection cloud doit être activée par défaut. Toutefois, vous pouvez configurer la protection cloud en fonction des besoins de votre organisation.

## <a name="methods-to-configure-cloud-protection"></a>Méthodes de configuration de la protection cloud

Vous pouvez activer ou désactiver Microsoft Defender protection cloud antivirus en utilisant l’une des méthodes suivantes :

- Microsoft Endpoint Manager, qui inclut Microsoft Intune et Configuration Manager
- Stratégie de groupe
- Cmdlets PowerShell

Vous pouvez également activer ou désactiver la protection cloud sur des points de terminaison individuels à l’aide de l’application Sécurité Windows. 

Pour plus d’informations sur les exigences de connectivité réseau spécifiques pour garantir que vos points de terminaison peuvent se connecter au service de protection cloud, consultez [Configurer et valider les connexions réseau](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> Dans Windows 10 et Windows 11, il n’existe aucune différence entre les options **de création de rapports de base** et **avancées** décrites dans cet article. Il s’agit d’une distinction héritée et le choix de l’un ou l’autre des paramètres entraîne le même niveau de protection cloud. Il n’existe aucune différence dans le type ou la quantité d’informations partagées. Pour plus d’informations sur ce que nous collectons, consultez la [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Utiliser Intune pour activer la protection cloud

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Dans le volet **Accueil** , sélectionnez **Configuration de l’appareil > Profils**.

3. Sélectionnez le type **de profil Restrictions** d’appareil que vous souhaitez configurer. Si vous devez créer un nouveau type de profil **restrictions** d’appareil, consultez [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **Propriétés** \> **Paramètres de configuration : Modifier** \> **Microsoft Defender Antivirus**.

5. Sur le commutateur **Protection fournie par le cloud** , sélectionnez **Activer**.

6. Dans la liste déroulante **Inviter les utilisateurs avant l’exemple de soumission** , sélectionnez **Envoyer automatiquement toutes les données**.

Pour plus d’informations sur Intune profils d’appareil, notamment sur la création et la configuration de leurs paramètres, consultez [Que sont les profils d’appareil Microsoft Intune ?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Utiliser Microsoft Endpoint Manager pour activer la protection cloud

1. Accédez au Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) et connectez-vous.

2. Choisissez **Antivirus de sécurité** \> de point de terminaison.

3. Sélectionnez un profil antivirus. (Si vous n’en avez pas encore, ou si vous souhaitez créer un profil, consultez [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **Propriétés**. Ensuite, en regard **de Paramètres de configuration**, choisissez **Modifier**.

5. Développez **Protection cloud**, puis dans la liste **Niveau de protection fourni par le cloud** , sélectionnez l’une des options suivantes :
   - **Élevé** : applique un niveau élevé de détection.
   - **Plus élevé** : utilise le **Niveau supérieur** et applique davantage de mesures de protection (peut affecter les performances du client).
   - **Tolérance zéro** : bloque tous les exécutables inconnus.

6. Sélectionnez **Vérifier + enregistrer**, **puis enregistrer.**

Pour plus d’informations sur la configuration de Microsoft Endpoint Configuration Manager, consultez [Guide pratique pour créer et déployer des stratégies anti-programme malveillant : service De protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Utiliser stratégie de groupe pour activer la protection cloud

1. Sur votre appareil de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’Éditeur de gestion stratégie de groupe**, accédez à **Configuration de l’ordinateur**.

3. Sélectionnez **Modèles d’administration**.

4. Développez l’arborescence **des composants** >  Windows **Microsoft Defender Antivirus > MAPS**

    > [!NOTE]
    > Les paramètres MAPS sont égaux à la protection fournie par le cloud.

5. Double-cliquez sur **Joindre Microsoft MAPS**. Vérifiez que l’option est activée et définie sur **Cartes de base** ou **CARTES avancées**. Sélectionnez **OK**.

    Vous pouvez choisir d’envoyer des informations de base ou supplémentaires sur les logiciels détectés :

    - CARTES de base : l’appartenance de base envoie des informations de base à Microsoft sur les programmes malveillants et les logiciels potentiellement indésirables détectés sur votre appareil. Les informations incluent l’origine du logiciel (comme les URL et les chemins d’accès partiels), les actions effectuées pour résoudre la menace et si les actions ont réussi.

    - CARTES avancées : en plus des informations de base, l’appartenance avancée envoie des informations détaillées sur les programmes malveillants et les logiciels potentiellement indésirables, y compris le chemin complet du logiciel et des informations détaillées sur la façon dont le logiciel a affecté votre appareil.

6. Double-cliquez sur **Envoyer des exemples de fichiers quand une analyse plus approfondie est nécessaire**. Vérifiez que la première option est définie sur **Activé** et que les autres options sont définies sur :

   - **Envoyer des exemples sécurisés** (1)
   - **Envoyer tous les exemples** (3)

   >[!NOTE]
   > L’option **Envoyer des exemples sécurisés** (1) signifie que la plupart des exemples seront envoyés automatiquement. Les fichiers susceptibles de contenir des informations personnelles seront toujours demandés et nécessitent une confirmation supplémentaire.
   > Définir l’option sur **Toujours demander** (0) réduit l’état de protection de l’appareil. Le fait de le définir sur **Ne jamais envoyer** (2) signifie que la fonctionnalité [Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md) de Microsoft Defender pour point de terminaison ne fonctionnera pas.

7. Sélectionnez **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Utiliser les applets de commande PowerShell pour activer la protection cloud

Les applets de commande suivantes peuvent activer la protection cloud :

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Pour plus d’informations sur l’utilisation de PowerShell avec Microsoft Defender Antivirus, consultez [Utiliser des applets de commande PowerShell pour configurer et exécuter Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md) et [les applets de commande antivirus Microsoft Defender](/powershell/module/defender/). [Fournisseur de services de configuration de stratégie - Defender](/windows/client-management/mdm/policy-csp-defender) contient également plus d’informations sur [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> Vous pouvez définir **-SubmitSamplesConsent** sur `SendSafeSamples` (paramètre par défaut, recommandé), `NeverSend`ou `AlwaysPrompt`. Le `SendSafeSamples` paramètre signifie que la plupart des exemples sont envoyés automatiquement. Les fichiers susceptibles de contenir des informations personnelles entraînent une invite à continuer et nécessitent une confirmation.
> Les `NeverSend` paramètres et `AlwaysPrompt` réduisent le niveau de protection de l’appareil. En outre, le `NeverSend` paramètre signifie que la fonctionnalité [Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md) de Microsoft Defender pour point de terminaison ne fonctionnera pas.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Utiliser WMI (Windows Management Instruction) pour activer la protection cloud

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) pour les propriétés suivantes :

```WMI
MAPSReporting
SubmitSamplesConsent
```

Pour plus d’informations sur les paramètres autorisés, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Activer la protection cloud sur des clients individuels avec l’application Sécurité Windows

> [!NOTE]
> Si le **paramètre Configurer le paramètre local pour la création de rapports microsoft MAPS** stratégie de groupe est défini sur **Désactivé**, le paramètre **de protection basée sur le cloud** dans Paramètres Windows est grisé et indisponible. Les modifications apportées via un objet de stratégie de groupe doivent d’abord être déployées vers les points de terminaison individuels avant que le paramètre soit mis à jour dans les Paramètres Windows.

1. Ouvrez l’application Sécurité Windows en sélectionnant l’icône de bouclier dans la barre des tâches ou en recherchant **Sécurité Windows** dans le menu Démarrer.

2. Sélectionnez la vignette **Protection contre les virus & les menaces** (ou l’icône de bouclier dans la barre de menus de gauche), puis, sous **Paramètres de protection contre les virus & contre les menaces**, sélectionnez **Gérer les paramètres**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Paramètres de protection contre les virus & les menaces" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Vérifiez que **protection basée sur le cloud** et **envoi automatique d’exemples** sont basculés sur **Activé**.

   > [!NOTE]
   > Si l’envoi automatique d’exemples a été configuré avec stratégie de groupe le paramètre est grisé et indisponible.

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

- [Utiliser la protection cloud Microsoft dans Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md)

- [Comment créer et déployer des stratégies anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Utiliser des cmdlets PowerShell pour gérer l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
