---
title: Activez la protection fournie par le cloud dans Antivirus Microsoft Defender
description: Activez la protection fournie par le cloud pour bénéficier de fonctionnalités de protection rapides et avancées.
keywords: Antivirus Microsoft Defender, antimalware, sécurité, cloud, bloc à première vue
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.date: 05/18/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 8c45fb4b60e3c20c2001cc0008ecc8154e854273
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572056"
---
# <a name="turn-on-cloud-delivered-protection"></a>Activer la protection par le cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

> [!NOTE]
> Le service Antivirus Microsoft Defender cloud est un mécanisme permettant d’offrir une protection mise à jour à votre réseau et à vos points de terminaison. Bien qu’il soit appelé un service cloud, il n’est pas simplement une protection pour les fichiers stockés dans le cloud; il utilise plutôt des ressources distribuées et l’apprentissage automatique pour fournir une protection à vos points de terminaison à un rythme beaucoup plus rapide que les mises à jour traditionnelles du renseignement de sécurité.

Antivirus Microsoft Defender utilise de multiples technologies de détection et de prévention pour offrir une protection précise, en temps réel et intelligente. [Faites la point de vue des technologies de pointe au cœur de Microsoft Defender pour la protection de prochaine génération Endpoint.](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

Vous pouvez activer Antivirus Microsoft Defender protection fournie par le cloud de plusieurs façons :

- Microsoft Intune
- Microsoft Endpoint Manager
- Stratégie de groupe
- Cmdlets PowerShell.

 Vous pouvez également l’activer ou l’éteindre chez des clients individuels avec l’application Sécurité Windows’application.

Consultez [la protection microsoft fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md) pour une vue d’ensemble Antivirus Microsoft Defender protection fournie par le cloud.

Pour plus d’informations sur les exigences spécifiques de connectivité réseau pour vous assurer que vos points de terminaison peuvent se connecter au service de protection livré dans le cloud, [consultez Configurer et valider les connexions réseau.](configure-network-connections-microsoft-defender-antivirus.md)

> [!NOTE]
> En Windows 10, il n’y a pas de différence entre les options **de** rapports **de** base et avancées décrites dans ce sujet. Il s’agit d’une distinction héritée et le choix de l’un ou l’autre paramètre se traduira par le même niveau de protection fournie par le cloud. Il n’y a aucune différence dans le type ou la quantité d’informations qui sont partagées. Pour plus d’informations sur ce que nous recueillons, consultez la [déclaration de confidentialité de Microsoft](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-delivered-protection"></a>Utilisez Intune pour activer la protection fournie par le cloud

1. Allez au centre Microsoft Endpoint Manager admin [https://endpoint.microsoft.com](https://endpoint.microsoft.com) () et connectez-vous.

2. Sur le **volet Accueil,** sélectionnez la **configuration de l'> profils**.

3. Sélectionnez le type **de profil** de restriction s’appliquant à l’appareil que vous souhaitez configurer. Si vous avez besoin de créer un nouveau type **de profil de restriction** s’appliquant aux périphériques, consultez les paramètres de restriction de [l’appareil Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **Paramètres**  >  **de configuration propriétés :**  >  **Modifiez Antivirus Microsoft Defender**.

5. Sur le **commutateur de protection livré par Cloud,** sélectionnez **Activer**.

6. Dans les utilisateurs **prompts avant la baisse de soumission** de l’échantillon, **sélectionnez Envoyer toutes les données automatiquement**.

Pour plus d’informations sur les profils des périphériques Intune, y compris la façon de créer et de configurer leurs paramètres, voir [Quels sont les profils Microsoft Intune’appareils ?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-delivered-protection"></a>Utilisez Microsoft Endpoint Manager pour activer la protection fournie par le cloud

1. Allez au centre Microsoft Endpoint Manager admin [https://endpoint.microsoft.com](https://endpoint.microsoft.com) () et connectez-vous.

2. Choisissez **Endpoint security**  >  **Antivirus**.

3. Sélectionnez un profil antivirus. (Si vous n’en avez pas encore, ou si vous souhaitez créer un nouveau profil, consultez les paramètres [de restriction de l’appareil Configure dans Microsoft Intune](/intune/device-restrictions-configure).

4. Sélectionnez **Propriétés**. Ensuite, à côté des **paramètres de configuration,** choisissez **Modifier**.

5. Élargissez **la protection** cloud, puis dans la liste de **niveau de protection fournie par cloud,** sélectionnez l’un des éléments suivants :
   - **Haut**: Applique un fort niveau de détection.
   - **High plus :** Utilise le niveau élevé **et** applique des mesures de protection supplémentaires (peuvent avoir une incidence sur les performances des clients).
   - **Tolérance zéro**: Bloque tous les exécutables inconnus.

6. Sélectionnez **Examen + enregistrer**, puis choisissez **Enregistrer**.

Pour plus d’informations sur la configuration Microsoft Endpoint Configuration Manager, voir [Comment créer et déployer des stratégies antimalware : service de protection cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-delivered-protection"></a>Utilisez la stratégie de groupe pour activer la protection fournie par le cloud

1. Sur votre appareil de gestion de stratégie de groupe, ouvrez [la console de gestion de stratégie de](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))groupe, cliquez à droite sur l’objet de stratégie de groupe que vous souhaitez configurer et sélectionner **Modifier**.

2. Dans le **Group Policy Management Editor**, aller à la configuration **informatique**.

3. Sélectionnez **Modèles administratifs**.

4. Étendre l’arbre **aux Windows composants > Antivirus Microsoft Defender > MAPS**

5. Double-cliquez **sur Rejoindre Microsoft MAPS**. Assurez-vous que l’option est activée et réglée **sur maps de base** ou cartes **avancées.** Sélectionnez **OK**.

6. Double-cliquez envoyer **des échantillons de fichiers lorsque d’autres analyses sont nécessaires**. Assurez-vous que la première option est définie sur **Activé et** que les autres options sont définies sur l’une ou l’autre :

    1. **Envoyer des échantillons sûrs** (1)
    2. **Envoyer tous les échantillons** (3)

        >[!NOTE]
        > **L’option Envoyer des échantillons** sûrs (1) signifie que la plupart des échantillons seront envoyés automatiquement. Les fichiers susceptibles de contenir des renseignements personnels seront toujours rapides et nécessiteront une confirmation supplémentaire.
        > Définir l’option de **Toujours prompt** (0) abaissera l’état de protection de l’appareil. Le définir pour **ne jamais envoyer** (2) signifie que la fonction Block at First [Sight](configure-block-at-first-sight-microsoft-defender-antivirus.md) de Microsoft Defender pour Endpoint ne fonctionnera pas.

7. Sélectionnez **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-delivered-protection"></a>Utilisez des cmdlets PowerShell pour activer la protection fournie par le cloud

Les cmdlets suivants peuvent activer la protection fournie par le cloud :

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Pour plus d’informations sur la façon d’utiliser PowerShell avec Antivirus Microsoft Defender, [consultez les cmdlets PowerShell pour configurer et exécuter Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets Defender](/powershell/module/defender/). [Politique CSP - Defender a](/windows/client-management/mdm/policy-csp-defender) également plus d’informations spécifiquement sur [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

>[!NOTE]
> Vous pouvez également définir **-SubmitSamplesConsent à** `SendSafeSamples` (le paramètre par défaut), `NeverSend` ou `AlwaysPrompt` . Le `SendSafeSamples` paramètre signifie que la plupart des échantillons seront envoyés automatiquement. Les fichiers susceptibles de contenir des renseignements personnels seront toujours rapides et nécessiteront une confirmation supplémentaire.

>[!WARNING]
> Réglage **-SubmitSamplesConsent ou** `NeverSend` `AlwaysPrompt` abaissera le niveau de protection de l’appareil. En outre, le définir signifie `NeverSend` que la fonction Block at First [Sight](configure-block-at-first-sight-microsoft-defender-antivirus.md) de Microsoft Defender pour Endpoint ne fonctionnera pas.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-delivered-protection"></a>Utilisez Windows instruction de gestion des systèmes (WMI) pour activer la protection fournie par le cloud

Utilisez la [ **méthode** Set de la **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) classe pour les propriétés suivantes :

```WMI
MAPSReporting
SubmitSamplesConsent
```

Pour plus d’informations sur les paramètres autorisés, [Windows Defender les API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-delivered-protection-on-individual-clients-with-the-windows-security-app"></a>Activez la protection fournie par le cloud sur les clients individuels avec l’application Sécurité Windows cloud

> [!NOTE]
> Si le **paramètre local Configure remplace le paramètre de stratégie de groupe Microsoft MAPS** est défini sur **Désactivé,** le **paramètre de protection basé sur le Cloud** en Windows Paramètres sera grisé et indisponible. Les modifications apportées via un objet de stratégie de groupe doivent d’abord être déployées vers les points de terminaison individuels avant que le paramètre soit mis à jour dans les Paramètres Windows.

1. Ouvrez l Sécurité Windows appe en sélectionnant l’icône bouclier dans la barre des tâches, ou en recherchant le menu de démarrage pour **Defender**.

2. Sélectionnez **la vignette de protection contre & virus** (ou l’icône bouclier sur la barre de menu gauche) puis **l’étiquette paramètres de protection contre les menaces virus &** :

    ![Capture d’écran de l’étiquette des paramètres de protection contre les virus et les menaces dans l’application Sécurité Windows](images/defender/wdav-protection-settings-wdsc.png)

3. Confirmez que **la protection basée sur le Cloud** et la soumission automatique **de** l’échantillon sont commutées **à On**.

> [!NOTE]
> Si la soumission automatique de l’échantillon a été configurée avec la stratégie de groupe, le paramètre sera grisé et indisponible.

## <a name="related-articles"></a>Articles connexes

- [Configurer le délai de blocage du cloud](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)
- [Configurer le bloc à première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Utiliser des cmdlets PowerShell pour gérer l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Aider à sécuriser Windows PC avec Endpoint Protection pour Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)]
- [Cmdlets defender](/powershell/module/defender/)
- [Utilisez la protection microsoft cloud livrée dans Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)
- [Comment créer et déployer des stratégies antimalware : service de protection contre le Cloud](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
