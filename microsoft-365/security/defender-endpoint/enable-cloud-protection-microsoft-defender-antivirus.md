---
title: Activer la protection cloud dans Antivirus Microsoft Defender
description: Activer la protection cloud pour bénéficier des fonctionnalités de protection rapide et avancée.
keywords: 'Antivirus Microsoft Defender logiciel anti-programme malveillant, sécurité, cloud, bloquer à la première vue'
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
---

# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Activer la protection cloud dans Antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

[La protection cloud Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) offre une protection précise, en temps réel et intelligente. La protection cloud doit être activée par défaut . toutefois, vous pouvez configurer la protection cloud en fonction des besoins de votre organisation.

## <a name="methods-to-configure-cloud-protection"></a>Méthodes de configuration de la protection cloud

Vous pouvez activer ou Antivirus Microsoft Defender protection cloud à l’aide de l’une des méthodes ci-après :

- Microsoft Endpoint Manager, qui inclut Microsoft Intune configuration manager
- Stratégie de groupe
- Cmdlets PowerShell

Vous pouvez également activer ou désactiver la protection cloud sur des points de terminaison individuels à l’aide Sécurité Windows app. 

Pour plus d’informations sur les exigences de connectivité réseau spécifiques pour vous assurer que vos points de terminaison peuvent se connecter au service de protection cloud, voir Configurer et valider les [connexions réseau](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> Dans Windows 10 et Windows 11, il n’existe aucune différence entre les options de rapports  de base  et avancées décrites dans cet article. Il s’agit d’une distinction héritée et le choix de l’un ou l’autre des paramètres entraîne le même niveau de protection cloud. Il n’existe aucune différence dans le type ou la quantité d’informations partagées. Pour plus d’informations sur ce que nous collectons, voir la déclaration [de confidentialité de Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Utiliser Intune pour activer la protection cloud

1. Go to the Microsoft Endpoint Manager admin center ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) and sign in.

2. Dans le **volet Accueil**, sélectionnez **Configuration de l’appareil > profils.**

3. Sélectionnez **le type de profil restrictions d’appareil** que vous souhaitez configurer. Si vous devez créer un type de profil de **restrictions** d’appareil, voir [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **les paramètres** \> **de configuration des propriétés : Antivirus Microsoft Defender**\>.

5. Sur le **commutateur de protection cloud** , sélectionnez **Activer**.

6. Dans la demande **d’utilisateurs avant la** soumission d’exemples, **sélectionnez Envoyer toutes les données automatiquement**.

Pour plus d’informations sur les profils d’appareil Intune, notamment sur la création et la configuration de leurs paramètres, voir [Quelles sont les Microsoft Intune’appareil ?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Utiliser Microsoft Endpoint Manager pour activer la protection cloud

1. Go to the Microsoft Endpoint Manager admin center ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) and sign in.

2. Choisissez **l’Antivirus de sécurité des points de** \> **terminaison**.

3. Sélectionnez un profil antivirus. (Si vous n’en avez pas encore, ou si vous souhaitez créer un profil, voir [Configurer les paramètres de restriction d’appareil dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **Propriétés**. Ensuite, en de côté **des paramètres de configuration**, choisissez **Modifier**.

5. **Développez la protection** cloud, puis dans la liste des niveaux de **protection** cloud, sélectionnez l’une des listes suivantes :
   - **Élevé** : applique un niveau élevé de détection.
   - **Plus élevé :** utilise le **niveau élevé** et applique davantage de mesures de protection (peut affecter les performances du client).
   - **Tolérance zéro :** bloque tous les exécutables inconnus.

6. **Sélectionnez Révision + Enregistrer**, puis **Enregistrer**.

Pour plus d’informations sur la configuration Microsoft Endpoint Configuration Manager, voir Comment créer et déployer des stratégies [anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Utiliser une stratégie de groupe pour activer la protection cloud

1. Sur votre appareil de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration de l’ordinateur**.

3. **Sélectionnez modèles d’administration**.

4. Développez l’arborescence **Windows composants** >  **Antivirus Microsoft Defender > MAPS**

    > [!NOTE]
    > Les paramètres MAPS sont égaux à la protection cloud.

5. Double-cliquez sur **Rejoindre Microsoft MAPS**. Assurez-vous que l’option est allumée et définie sur **Maps de base** **ou Cartes avancées**. Sélectionnez **OK**.

    Vous pouvez choisir d’envoyer des informations de base ou supplémentaires sur les logiciels détectés :

    - MAP de base : l’appartenance de base envoie des informations de base à Microsoft sur les programmes malveillants et les logiciels potentiellement indésirables détectés sur votre appareil. Les informations incluent l’endroit d’où le logiciel est issu (comme les URL et les chemins d’accès partiels), les actions prises pour résoudre la menace et si les actions ont réussi.

    - CARTES avancées : en plus des informations de base, l’appartenance avancée envoie des informations détaillées sur les programmes malveillants et les logiciels potentiellement indésirables, y compris le chemin d’accès complet au logiciel et des informations détaillées sur la façon dont le logiciel a affecté votre appareil.

6. Double-cliquez sur **Envoyer des exemples de fichier lorsque d’autres analyses sont nécessaires**. Assurez-vous que la première option est définie sur **Activé** et que les autres options sont définies sur :

   - **Envoyer des exemples sécurisés** (1)
   - **Envoyer tous les exemples** (3)

   >[!NOTE]
   > **L’option Envoyer des échantillons sûrs** (1) signifie que la plupart des échantillons seront envoyés automatiquement. Les fichiers susceptibles de contenir des informations personnelles seront toujours invités et nécessitent une confirmation supplémentaire.
   > La définition de **l’option sur Always Prompt** (0) réduit l’état de protection de l’appareil. Le fait de la définir sur **Ne** jamais envoyer (2) [](configure-block-at-first-sight-microsoft-defender-antivirus.md) signifie que la fonctionnalité Bloquer à la première vue de Microsoft Defender pour le point de terminaison ne fonctionne pas.

7. Sélectionnez **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Utiliser les cmdlets PowerShell pour activer la protection cloud

Les cmdlets suivantes peuvent activer la protection cloud :

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir Utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter Antivirus Microsoft Defender et [Antivirus Microsoft Defender cmdlets](/powershell/module/defender/). [CSP Stratégie - Defender](/windows/client-management/mdm/policy-csp-defender) a également plus d’informations spécifiques sur [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> Vous pouvez définir **-SubmitSamplesConsent** sur `SendSafeSamples` (paramètre par défaut, recommandé) `NeverSend`ou `AlwaysPrompt`. Le `SendSafeSamples` paramètre signifie que la plupart des échantillons seront envoyés automatiquement. Les fichiers susceptibles de contenir des informations personnelles entraînent une invite de continuer et nécessitent une confirmation.
> Les `NeverSend` paramètres `AlwaysPrompt` et les paramètres diminuent le niveau de protection de l’appareil. En outre, le paramètre `NeverSend` signifie que la [](configure-block-at-first-sight-microsoft-defender-antivirus.md) fonctionnalité Bloquer à la première vue de Microsoft Defender pour le point de terminaison ne fonctionne pas.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Utiliser Windows Management Instruction (WMI) pour activer la protection cloud

Utilisez la [**méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) pour les propriétés suivantes :

```WMI
MAPSReporting
SubmitSamplesConsent
```

Pour plus d’informations sur les paramètres autorisés, [voir Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Activer la protection cloud sur des clients individuels avec l’Sécurité Windows client

> [!NOTE]
> Si le paramètre Configurer le remplacement de paramètre local pour la création de rapports sur la stratégie de groupe **Microsoft MAPS** est **désactivé, le** paramètre de protection basée sur le **cloud** dans Windows Paramètres est grisé et indisponible. Les modifications apportées via un objet de stratégie de groupe doivent d’abord être déployées vers les points de terminaison individuels avant que le paramètre soit mis à jour dans les Paramètres Windows.

1. Ouvrez Sécurité Windows’application en sélectionnant l’icône de bouclier dans la barre des tâches ou en recherchant Sécurité Windows dans **le menu Démarrer**.

2. Sélectionnez la **vignette & protection** contre les virus contre les menaces (ou l’icône de bouclier dans la barre de menus de gauche), puis, sous Gérer les **paramètres** , sélectionnez **Paramètres de protection** contre & virus.

3. Confirmez que **la protection basée sur le cloud et** **l’envoi** automatique d’échantillons sont tous deux **activés**.

   > [!NOTE]
   > Si l’envoi automatique d’échantillons a été configuré avec la stratégie de groupe, le paramètre est grisé et indisponible.

## <a name="see-also"></a>Voir aussi

- [Utiliser la protection cloud Microsoft dans Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- [Comment créer et déployer des stratégies de logiciel anti-programme malveillant : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Utiliser des cmdlets PowerShell pour gérer l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
