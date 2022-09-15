---
title: Activer Bloquer à la première consultation pour la détection d’un programme malveillant en quelques secondes
description: Activer la fonctionnalité Bloquer à la première consultation pour la détection et le blocage d’un programme malveillant en quelques secondes.
keywords: analyser, bloquer à la première consultation, programme malveillant, à la première consultation, cloud, defender, antivirus
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.reviewer: marcmcc
manager: dansimp
ms.custom: nextgen
ms.date: 07/11/2022
ms.subservice: mde
ms.topic: article
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 63fe41d327d39c15f383c8a70c0b46d5f5d03afd
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67703135"
---
# <a name="turn-on-block-at-first-sight"></a>Activer Bloquer à la première consultation

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender 

**Plateformes**
- Windows

Cet article présente la fonctionnalité antivirus/logiciel anti-programme malveillant appelée « Bloquer à la première consultation » et décrit la façon d’activer Bloquer à la première consultation pour votre organisation.

> [!TIP]
> Cet article est destiné aux administrateurs d’entreprise et aux professionnels de l’informatique qui gère les paramètres de sécurité pour des organisations. Si vous n’êtes pas un administrateur d’entreprise ou un professionnel de l’informatique, mais que vous avez des questions à propos de Bloquer à la première consultation, consultez la section [Vous n’êtes pas un administrateur d’entreprise ou un professionnel de l’informatique ?](#not-an-enterprise-admin-or-it-pro).

## <a name="what-is-block-at-first-sight"></a>Qu’est-ce que « Bloquer à la première consultation » ?

Bloquer à la première consultation est une fonctionnalité de protection de nouvelle génération de protection contre les menaces qui détecte un nouveau programme malveillant et le bloque en quelques secondes. La fonctionnalité Bloquer à la première consultation est activée lorsque certains paramètres de sécurité sont activés. Ces paramètres sont les suivants :

- [Protection cloud](cloud-protection-microsoft-defender-antivirus.md) :
- Un échantillon spécifique d’expiration de l'envoi (tel que 50 secondes) et
- Un blocage des fichiers de niveau élevé.

Dans la plupart des entreprises, les paramètres nécessaires pour activer Bloquer à la première consultation sont configurés avec les déploiements de l’Antivirus Microsoft Defender.

## <a name="how-it-works"></a>Mode de fonctionnement

Lorsque l’Antivirus Microsoft Defender rencontre un fichier suspect, mais non détecté, il interroge notre serveur principal de protection cloud. Le serveur principal de protection cloud applique la méthode heuristique, l’apprentissage automatique et l’analyse automatisée de fichier pour déterminer si les fichiers sont suspects ou s’ils ne sont pas une menace.

L’Antivirus Microsoft Defender utilise plusieurs technologies de prévention et de détection pour fournir une protection exacte, intelligente et en temps réel.

:::image type="content" source="images/microsoft-defender-atp-next-generation-protection-engines.png" alt-text="Liste des moteurs antivirus Microsoft Defender" lightbox="images/microsoft-defender-atp-next-generation-protection-engines.png":::

> [!TIP]
> Pour en savoir plus, consultez [(Blog) Découvrir les technologies avancées au cœur de la protection de nouvelle génération de Microsoft Defender pour point de terminaison](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>Quelques éléments à connaître à propos de la fonctionnalité Bloquer à la première consultation

- Dans Windows 10, version 1803 ou ultérieure, Bloquer à la première consultation peut bloquer des fichiers exécutables non portables (tels que JS, VBS ou les macros) et des fichiers exécutables.

- Bloquer à la première consultation utilise uniquement le serveur principal de protection cloud pour les fichiers exécutables et les fichiers exécutables non portables qui sont téléchargés à partir d’Internet ou qui sont issus de la zone Internet. Une valeur de hachage du fichier .exe est vérifiée via le serveur principal de protection cloud pour déterminer s’il s’agit d’un fichier précédemment non détecté.

- Si le serveur principal cloud ne peut pas se prononcer, l’Antivirus Microsoft Defender bloque le fichier et télécharge une copie dans le cloud. Le cloud effectue d’autres analyses pour se prononcer avant d’autoriser le fichier à s’exécuter ou de le bloquer dans toutes les autres occurrences, selon qu’il détermine que le fichier est suspect ou qu’il n’est pas une menace.

- Dans de nombreux cas, ce processus peut diminuer le temps de réponse de plusieurs heures à quelques secondes pour un nouveau programme malveillant.

- Vous pouvez [spécifier la durée d’interdiction d’exécution d’un fichier](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) pendant que le service de protection dans le cloud analyse le fichier. Vous pouvez également [personnaliser le message affiché sur les bureaux des utilisateurs](/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) lorsqu’un fichier est bloqué. Vous pouvez modifier le nom de l’entreprise, les informations de contact et l’URL du message.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Activer la fonctionnalité Bloquer à la première consultation avec Microsoft Intune

> [!TIP]
> Microsoft Intune fait désormais partie de Microsoft Endpoint Manager.

1. Dans le Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>), naviguez vers **Appareils** \> **Profils de configuration**.

2. Sélectionnez ou créez un profil à l’aide du type de profil **Restrictions d’appareil**.

3. Dans **Paramètres de configuration** pour le profil des Restrictions d’appareil, configurez ou confirmez les paramètres suivants sous **Antivirus Microsoft Defender** :

   - **Protection fournie par le cloud** : Activée
   - **Niveau de blocage des fichiers** : Élevé
   - **Extension de temps pour l’analyse des fichiers dans le cloud** : 50
   - **Demander aux utilisateurs avant la soumission d’échantillons** : Envoyer tous les données sans demande

   :::image type="content" source="../../media/intune-block-at-first-sight.png" alt-text="Bloc de configuration Intune à la première consultation" lightbox="../../media/intune-block-at-first-sight.png":::

4. Enregistrez vos paramètres.

> [!TIP]
>
> - Le paramétrage du niveau de blocage des fichiers sur **Élevé** applique un niveau fort de détection. Dans le cas peu probable où le blocage du fichier entraîne la détection de faux positif de fichiers légitimes, votre équipe des opérations de sécurité peut [restaurer les fichiers mis en quarantaine](./restore-quarantined-files-microsoft-defender-antivirus.md).
> - Pour plus d’informations sur la configuration de restriction d’appareils de l’Antivirus Microsoft Defender dans Microsoft Intune, voir [Configurer les paramètres de restriction d’appareil de dans Microsoft Intune](/intune/device-restrictions-configure).
> - Pour une liste des restrictions d’appareils de l’Antivirus Microsoft Defender dans Intune, voir [Paramètres de restriction d’appareil pour Windows 10 (et versions ultérieures) dans Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Activer la fonctionnalité Bloquer à la première consultation avec Microsoft Endpoint Manager

> [!TIP]
> Si vous recherchez Microsoft Endpoint Configuration Manager, il fait désormais partie de Microsoft Endpoint Manager.

1. Dans Microsoft Endpoint Manager (<https://endpoint.microsoft.com>), accédez à **Sécurité des points de terminaison** \> **Antivirus**.

2. Sélectionnez une stratégie existante ou créez-en une nouvelle à l’aide du type de profil **Antivirus Microsoft Defender**.

3. Configurez ou confirmez les paramètres de configuration suivants :

   - **Activer la protection par le cloud** : Oui
   - **Niveau de protection par le cloud** : Élevé
   - **Antivirus Microsoft Defender délai d’Antivirus Microsoft Defender** en secondes : 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Paramètres de Bloquer à la première consultation dans le portail Microsoft Endpoint Manager" lightbox="images/endpointmgr-antivirus-cloudprotection.png":::

4. Appliquer un profil Antivirus Microsoft Defender à un groupe, tel que **Tous les utilisateurs**, **Tous les appareils** ou **Tous les utilisateurs et tous les appareils**.

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>Activer la fonctionnalité Bloquer à la première consultation avec une stratégie de groupe

> [!NOTE]
> Nous vous recommandons d’utiliser Intune ou Microsoft Endpoint Manager pour activer Bloquer à la première consultation.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. À l’aide de l'**Éditeur de gestion des stratégies de groupe** accédez à **Configuration de l’ordinateur** \> **Modèles d’administration** \> **Composants Windows** \> **Antivirus Microsoft Defender** \> **MAPS**.

3. Dans la section CARTES, cliquez deux fois sur **Configurer la fonctionnalité « Bloquer à la première consultation »**, puis configurez-la sur **Activé**, puis sélectionnez **OK**.

    > [!IMPORTANT]
    > La configuration sur **Toujours demander (0)** diminuera l’état de protection de l’appareil. La configuration sur **Ne jamais envoyer (2)** signifie que Bloquer à la première consultation ne fonctionnera pas.

4. Dans la section CARTES, cliquez deux fois sur **Envoyer des échantillons de fichier lorsqu'une analyse supplémentaire est nécessaire**, puis configurez l’option sur **Activé**. Sous **Envoyer des exemples de fichier lorsqu'une analyse supplémentaire est nécessaire**, sélectionnez **Envoyer tous les échantillons**, puis **OK**.

5. Redéployez votre objet de stratégie de groupe sur votre réseau comme vous le faites habituellement.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>Confirmer que la fonctionnalité Bloquer à la première consultation est activée sur les appareils client individuels

Vous pouvez confirmer que Bloquer à la première consultation est activé sur des appareils client individuels en utilisant l’application Sécurité Windows. La fonctionnalité Bloquer à la première consultation est automatiquement activée tant que les options **Protection assurée par le cloud** et **Envoi automatique d’un échantillon** sont activées.

1. Ouvrez l’application Sécurité Windows.

2. Sélectionnez **Protection contre les virus et les menaces**, puis sous **Paramètres de protection contre les virus et les menaces**, sélectionnez **Gérer les paramètres**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Paramètres de protection contre les menaces et les virus dans l’application Sécurité Windows" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Confirmez que les options **Protection assurée par le cloud** et **Envoi automatique d’un échantillon** sont activées.

> [!NOTE]
>
> - Si les paramètres de condition préalable sont configurés et déployés à l’aide d’une stratégie de groupe, les paramètres décrits dans cette section seront grisés et non disponibles pour une utilisation sur des points de terminaison individuels.
> - Les modifications apportées via un objet de stratégie de groupe doivent d’abord être déployées vers les points de terminaison individuels avant que le paramètre soit mis à jour dans les Paramètres Windows.

## <a name="turn-off-block-at-first-sight"></a>Désactiver la fonctionnalité Bloquer à la première consultation

> [!CAUTION]
> La désactivation de Bloquer à la première consultation diminue le niveau de protection de votre ou vos appareils et de votre réseau.

Vous pouvez peut-être décider de désactiver Bloquer à la première consultation si vous souhaitez retenir les paramètres de condition préalable sans utiliser réellement la protection Bloquer à la première consultation. Vous pouvez peut-être désactiver temporairement Bloquer à la première consultation pour voir comment cette fonctionnalité affecte votre réseau. Cependant, nous vous déconseillons de désactiver la protection Bloquer à la première consultation de manière permanente.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Désactiver la fonctionnalité Bloquer à la première consultation avec Microsoft Endpoint Manager

1. Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com>), puis connectez-vous.

2. Accédez à **Sécurité des points de terminaison** \> **Antivirus**, puis sélectionnez votre stratégie Antivirus Microsoft Defender.

3. Sous **Gérer**, choisissez **Propriétés**.

4. Près de **Paramètres de configuration**, choisissez **Modifier**.

5. Modifiez un ou plusieurs des paramètres suivants :

   - Définissez **Activer la protection assurée par le cloud** sur **Non** ou sur **Non configuré**.
   - Définissez **Niveau de protection assuré par le cloud** sur **Non configuré**.
   - Désactivez la case à cocher pour **Antivirus Microsoft Defender délai d’expiration étendu en secondes**.

6. Évaluez et enregistrez vos paramètres.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>Désactiver Bloquer à la première consultation à l’aide d’une stratégie de groupe

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. En utilisant l’**Éditeur de gestion des stratégies de groupe**, accédez à **Configuration ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence **Windows composants** \> **Antivirus Microsoft Defender** \> **MAPS**.

4. Cliquez deux fois sur **Configurer la fonctionnalité « Bloquer à la première consultation »**, puis définissez l’option sur **Désactivé**.

    > [!NOTE]
    > La désactivation de la fonctionnalité Bloquer à la première consultation ne désactive pas ou n’altère pas les stratégies de groupe de condition préalable.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Vous n’êtes pas un administrateur d’entreprise ou un professionnel de l’informatique ?

Si vous n’êtes pas un administrateur d’entreprise ou un professionnel de l’informatique, mais que vous avez des questions à propos de Bloquer à la première consultation, cette section s’adresse à vous. Bloquer à la première consultation est une fonctionnalité de protection de contre les menaces qui détecte et bloque un programme malveillant en quelques secondes. Bien qu’il n’existe aucun paramètre spécifique appelé « Bloquer à la première consultation », la fonctionnalité est activée lorsque certains paramètres sont configurés sur votre appareil.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Comment gérer l’activation ou la désactivation de Bloquer à la première consultation sur votre appareil

Si vous disposez d’un appareil personnel qui n’est pas géré par une organisation, vous n’aurez peut-être pas à vous demander comment activer ou désactiver la fonctionnalité Bloquer à la première consultation. Vous pouvez utiliser l’application Sécurité Windows pour gérer la fonctionnalité Bloquer à la première consultation.

1. Sur votre ordinateur Windows 10 ou Windows 11, ouvrez l’application Sécurité Windows.

2. Sélectionnez **Protection contre les virus et les menaces**.

3. Sous **Paramètres de protection contre les virus et les menaces**, sélectionnez **Gérer les paramètres**.

4. Effectuez l’une des étapes suivantes :

   - Pour activer la fonctionnalité Bloquer à la première consultation, vérifiez que les options **Protection assurée par le cloud** et **Envoi automatique d’un échantillon** sont activées.

   - Pour désactiver la fonctionnalité Bloquer à la première consultation, désactivez **Protection assurée par le cloud** ou **Envoi automatique d’un échantillon**.

     > [!CAUTION]
     > La désactivation de la fonctionnalité Bloquer à la première consultation diminue le niveau de protection de votre appareil. Nous vous déconseillons de désactiver définitivement la fonctionnalité Bloquer à la première consultation.

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

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Restez protégé grâce à la sécurité Windows](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)
