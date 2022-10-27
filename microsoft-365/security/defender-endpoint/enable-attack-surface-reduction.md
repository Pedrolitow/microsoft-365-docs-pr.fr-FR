---
title: Activer les règles de réduction de la surface d’attaque
description: Activez les règles de réduction de la surface d’attaque (ASR) pour protéger vos appareils contre les attaques qui utilisent des macros, des scripts et des techniques d’injection courantes.
keywords: Réduction de la surface d’attaque, hanches, système de prévention des intrusions hôtes, règles de protection, anti-exploit, antiexploit, exploit, prévention des infections, activer, activer
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde
manager: dansimp
ms.subservice: mde
ms.topic: how-to
ms.collection:
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.date: 1/18/2022
search.appverid: met150
ms.openlocfilehash: 452c1b11f7a283a91b03982a2e660730c9caac8c
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68733106"
---
# <a name="enable-attack-surface-reduction-rules"></a>Activer les règles de réduction de la surface d’attaque

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> [!TIP]
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Les règles de réduction de la surface d’attaque](attack-surface-reduction.md) (règles ASR) aident à empêcher les actions que les programmes malveillants abusent souvent pour compromettre les appareils et les réseaux.

## <a name="requirements"></a>Conditions requises

Fonctionnalités de réduction de la surface d’attaque dans les versions de Windows

Vous pouvez définir des règles de réduction de la surface d’attaque pour les appareils qui exécutent l’une des éditions et versions suivantes de Windows :

- [Windows 11 Professionnel](/windows/whats-new/windows-11-overview)
- [Windows 11 Entreprise](https://www.microsoft.com/microsoft-365/windows/windows-11-enterprise)
- Windows 10 Professionnel, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) ou ultérieure
- Windows 10 Entreprise, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) ou ultérieure
- Windows Server, [version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2022](/windows-server/get-started/whats-new-in-windows-server-2022)

Pour utiliser l’ensemble des fonctionnalités des règles de réduction de la surface d’attaque, vous avez besoin des éléments suivants :

- antivirus Microsoft Defender en tant qu’antivirus principal (protection en temps réel activé)
- [Cloud-Delivery Protection](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) sur (certaines règles l’exigent)
- licence Windows 10 Entreprise E5 ou E3

Bien que les règles de réduction de la surface d’attaque ne nécessitent pas de [licence Windows E5](/windows/deployment/deploy-enterprise-licenses), avec une licence Windows E5, vous bénéficiez de fonctionnalités de gestion avancées, notamment la surveillance, l’analytique et les workflows disponibles dans Defender pour point de terminaison, ainsi que des fonctionnalités de création de rapports et de configuration dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. Ces fonctionnalités avancées ne sont pas disponibles avec une licence E3, mais vous pouvez toujours utiliser observateur d'événements pour passer en revue les événements de règle de réduction de la surface d’attaque.

Chaque règle ASR contient l’un des quatre paramètres suivants :

- **Non configuré** |  **Désactivé** : désactiver la règle ASR
- **Bloquer** : activer la règle ASR
- **Audit** : Évaluer l’impact de la règle ASR sur votre organisation si elle est activée
- **Avertissement** : activez la règle ASR, mais autorisez l’utilisateur final à contourner le bloc

Nous vous recommandons d’utiliser des règles ASR avec une licence Windows E5 (ou une référence SKU de licence similaire) pour tirer parti des fonctionnalités avancées de surveillance et de création de rapports disponibles dans [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md) (Defender pour point de terminaison). Toutefois, si vous disposez d’une autre licence, telle que Windows Professionnel ou Windows E3, qui n’inclut pas de fonctionnalités avancées de surveillance et de création de rapports, vous pouvez développer vos propres outils de surveillance et de création de rapports en plus des événements générés à chaque point de terminaison lorsque des règles ASR sont déclenchées (par exemple, transfert d’événements).

> [!TIP]
> Pour en savoir plus sur les licences Windows, consultez [licences Windows 10](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) et consultez le [guide de gestion des licences en volume pour Windows 10](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf).

Vous pouvez activer les règles de réduction de la surface d’attaque à l’aide de l’une des méthodes suivantes :

- [Microsoft Intune](#intune)
- [Gestion des périphériques mobiles (GPM)](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Stratégie de groupe](#group-policy)
- [PowerShell](#powershell)

La gestion au niveau de l’entreprise, telle que Intune ou Microsoft Endpoint Manager, est recommandée. La gestion au niveau de l’entreprise remplace tout stratégie de groupe ou paramètres PowerShell en conflit au démarrage.

## <a name="exclude-files-and-folders-from-asr-rules"></a>Exclure des fichiers et des dossiers des règles ASR

Vous pouvez exclure les fichiers et les dossiers de l’évaluation par la plupart des règles de réduction de la surface d’attaque. Cela signifie que même si une règle ASR détermine que le fichier ou le dossier contient un comportement malveillant, elle n’empêche pas l’exécution du fichier. Cela peut potentiellement permettre à des fichiers non sécurisés de s’exécuter et d’infecter vos appareils.

Vous pouvez également exclure le déclenchement des règles ASR en fonction des hachages de certificat et de fichier en autorisant les indicateurs de certificat et de fichier Defender pour point de terminaison spécifiés. (Voir [Gérer les indicateurs](manage-indicators.md).)

> [!IMPORTANT]
> L’exclusion de fichiers ou de dossiers peut réduire considérablement la protection fournie par les règles ASR. Les fichiers exclus sont autorisés à s’exécuter, et aucun rapport ou événement n’est enregistré.
> Si les règles ASR détectent les fichiers qui, selon vous, ne doivent pas être détectés, vous devez [d’abord utiliser le mode audit pour tester la règle](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit).

Vous pouvez spécifier des fichiers ou dossiers individuels (à l’aide de chemins d’accès aux dossiers ou de noms de ressources complets), mais vous ne pouvez pas spécifier les règles auxquelles les exclusions s’appliquent. Une exclusion est appliquée uniquement lorsque l’application ou le service exclus démarre. Par exemple, si vous ajoutez une exclusion pour un service de mise à jour qui est déjà en cours d’exécution, le service de mise à jour continue à déclencher des événements jusqu’à ce que le service soit arrêté et redémarré.

Les règles ASR prennent en charge les variables d’environnement et les caractères génériques. Pour plus d’informations sur l’utilisation de caractères génériques, consultez [Utiliser des caractères génériques dans les listes d’exclusion de nom de fichier et de dossier ou d’extension](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>Conflit de stratégie

1. Si une stratégie en conflit est appliquée via GPM et GP, le paramètre appliqué à partir de GPM est prioritaire.

2. Les règles de réduction de la surface d’attaque pour les appareils gérés par MEM prennent désormais en charge le comportement de fusion des paramètres de différentes stratégies, afin de créer un sur-ensemble de stratégies pour chaque appareil. Seuls les paramètres qui ne sont pas en conflit sont fusionnés, tandis que ceux qui sont en conflit ne sont pas ajoutés au sur-ensemble de règles. Auparavant, si deux stratégies incluaient des conflits pour un seul paramètre, les deux stratégies étaient marquées comme étant en conflit et aucun paramètre de l’un ou l’autre profil n’était déployé. Le comportement de fusion des règles de réduction de la surface d’attaque est le suivant :
   - Les règles de réduction de la surface d’attaque des profils suivants sont évaluées pour chaque appareil auquel les règles s’appliquent :
     - Appareils > Stratégie de configuration > profil Endpoint Protection > Microsoft Defender Réduction de la [surface d’attaque](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules) **Exploit Guard** > .
     - Sécurité des points de terminaison > **stratégie de réduction de la surface d’attaque** > [Règles de réduction de la surface d’attaque](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - Sécurité des points de terminaison > Bases de référence de sécurité > Microsoft Defender règles de réduction de la [surface d’attaque](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules) **de base** >  ATP.
   - Les paramètres qui n’ont pas de conflits sont ajoutés à un sur-ensemble de stratégie pour l’appareil.
   - Lorsque plusieurs stratégies ont des paramètres en conflit, les paramètres en conflit ne sont pas ajoutés à la stratégie combinée, tandis que les paramètres qui ne sont pas en conflit sont ajoutés à la stratégie de sur-ensemble qui s’applique à un appareil.
   - Seules les configurations pour les paramètres en conflit sont retenues.

## <a name="configuration-methods"></a>Méthodes de configuration

Cette section fournit des détails de configuration pour les méthodes de configuration suivantes :

- [Intune](#intune)
- [Mem](#mem)
- [GPM](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Stratégie de groupe](#group-policy)
- [PowerShell](#powershell)

Les procédures suivantes pour l’activation des règles ASR incluent des instructions pour exclure des fichiers et des dossiers.

### <a name="intune"></a>Intune

#### <a name="device-configuration-profiles"></a>Profils de configuration d’appareil

1. Sélectionnez **Profils de configuration** \> de **l’appareil**. Choisissez un profil Endpoint Protection existant ou créez-en un. Pour en créer un, sélectionnez **Créer un profil** et entrez des informations pour ce profil. Pour **Type de profil**, sélectionnez **Endpoint Protection**. Si vous avez choisi un profil existant, sélectionnez **Propriétés** , puis **Paramètres**.

2. Dans le volet **Endpoint Protection**, sélectionnez **Windows Defender Exploit Guard**, puis sélectionnez **Réduction de la surface d’attaque**. Sélectionnez le paramètre souhaité pour chaque règle ASR.

3. Sous **Exceptions de réduction de la surface d’attaque**, entrez des fichiers et dossiers individuels. Vous pouvez également sélectionner **Importer** pour importer un fichier CSV qui contient des fichiers et des dossiers à exclure des règles ASR. Chaque ligne du fichier CSV doit être mise en forme comme suit :

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Sélectionnez **OK** dans les trois volets de configuration. Sélectionnez ensuite **Créer** si vous créez un fichier Endpoint Protection ou **Enregistrer** si vous modifiez un fichier existant.

#### <a name="endpoint-security-policy"></a>Stratégie de sécurité des points de terminaison

1. Sélectionnez Réduction de **la surface d’attaque de** **sécurité** \> du point de terminaison. Choisissez une règle ASR existante ou créez-en une. Pour en créer un, sélectionnez **Créer une stratégie** et entrez des informations pour ce profil. Pour **Type de profil**, sélectionnez **Règles de réduction de la surface d’attaque**. Si vous avez choisi un profil existant, sélectionnez **Propriétés** , puis **Paramètres**.

2. Dans le volet **Paramètres de configuration** , sélectionnez Réduction de la **surface d’attaque** , puis sélectionnez le paramètre souhaité pour chaque règle ASR.

3. Sous **Liste des dossiers supplémentaires à protéger**, **Liste des applications ayant accès aux dossiers protégés** et **Exclure les fichiers et les chemins d’accès des règles de réduction de la surface d’attaque**, entrez les fichiers et dossiers individuels. Vous pouvez également sélectionner **Importer** pour importer un fichier CSV qui contient des fichiers et des dossiers à exclure des règles ASR. Chaque ligne du fichier CSV doit être mise en forme comme suit :

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Sélectionnez **Suivant** dans les trois volets de configuration, puis sélectionnez **Créer** si vous créez une stratégie ou **Enregistrer** si vous modifiez une stratégie existante.

### <a name="mem"></a>Mem

Vous pouvez utiliser l’OMA-URI microsoft Endpoint Manager (MEM) pour configurer des règles ASR personnalisées. La procédure suivante utilise la règle [Bloquer l’abus de pilotes signés vulnérables exploités](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) pour l’exemple.

1. Ouvrez le Centre d’administration Microsoft Endpoint Manager (MEM). Dans le menu **Accueil** , cliquez sur  **Appareils**, sélectionnez **Profils de configuration**, puis cliquez sur **Créer un profil**.

   > [!div class="mx-imgBorder"]
   >  :::image type="content" source="images/mem01-create-profile.png" alt-text="Page Créer un profil dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/mem01-create-profile.png":::

2. Dans **Créer un profil**, dans les deux listes déroulantes suivantes, sélectionnez les éléments suivants :

   - Dans **Plateforme**, sélectionnez **Windows 10 et versions ultérieures**
   - Dans **Type de profil**, sélectionnez **Modèles**
   - Si les règles ASR sont déjà définies via Sécurité du point de terminaison, dans **Type de profil**, sélectionnez **Catalogue de paramètres**.

   Sélectionnez **Personnalisé**, puis **Créer**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem02-profile-attributes.png" alt-text="Attributs de profil de règle dans le portail du Centre d’administration Microsoft Endpoint Manager" lightbox="images/mem02-profile-attributes.png":::

3. L’outil Modèle personnalisé s’ouvre à l’étape **1 Informations de base**. Dans **1 Informations de base**, dans **Nom**, tapez un nom pour votre modèle, et dans **Description** , vous pouvez taper une description (facultatif).

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem03-1-basics.png" alt-text="Attributs de base dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/mem03-1-basics.png":::

4. Cliquez sur **Suivant**. Étape **2 Les paramètres de configuration s’ouvrent** . Pour Paramètres OMA-URI, cliquez sur **Ajouter**. Deux options s’affichent désormais : **Ajouter** et **Exporter**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem04-2-configuration-settings.png" alt-text="Les paramètres de configuration dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/mem04-2-configuration-settings.png":::

5. Cliquez à nouveau sur **Ajouter** . Ajouter **des paramètres OMA-URI de ligne** s’ouvre. Dans **Ajouter une ligne**, procédez comme suit :

   - Dans **Nom**, tapez un nom pour la règle.
   - Dans **Description**, tapez une brève description.
   - Dans **OMA-URI**, tapez ou collez le lien OMA-URI spécifique pour la règle que vous ajoutez. Reportez-vous à la section GPM de cet article pour l’OMA-URI à utiliser pour cet exemple de règle. Pour les GUID de règle de réduction de la surface d’attaque, consultez [Descriptions des règles par règle](attack-surface-reduction-rules-reference.md#per-rule-descriptions) dans la rubrique : Règles de réduction de la surface d’attaque.
   - Dans **Type de données**, sélectionnez **Chaîne**.
   - Dans **Valeur**, tapez ou collez la valeur GUID, le \= signe et la valeur d’état sans espaces (_GUID=StateValue_). Où :

     - 0 : Désactiver (désactiver la règle ASR)
     - 1 : Bloquer (activer la règle ASR)
     - 2 : Audit (Évaluer l’impact de la règle ASR sur votre organisation si elle est activée)
     - 6 : Avertir (Activer la règle ASR, mais autoriser l’utilisateur final à contourner le blocage)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem05-add-row-oma-uri.png" alt-text="Configuration de l’URI OMA dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/mem05-add-row-oma-uri.png":::

6. Sélectionnez **Enregistrer**. **Ajouter une ligne** ferme. Dans **Personnalisé**, sélectionnez **Suivant**. À l’étape **3 Balises d’étendue**, les balises d’étendue sont facultatives. Effectuez l'une des opérations suivantes :

   - Sélectionnez **Sélectionner les balises d’étendue**, sélectionnez la balise d’étendue (facultatif), puis sélectionnez **Suivant**.
   - Ou sélectionnez **Suivant.**

7. À l’étape **4 Affectations**, dans **Groupes inclus**, pour les groupes que vous souhaitez appliquer cette règle, sélectionnez l’une des options suivantes :

   - **Ajouter des groupes**
   - **Ajouter tous les utilisateurs**
   - **Ajouter tous les appareils**

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem06-4-assignments.png" alt-text="Affectations dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/mem06-4-assignments.png":::

8. Dans **Groupes exclus**, sélectionnez les groupes que vous souhaitez exclure de cette règle, puis sélectionnez **Suivant**.

9. À l’étape **5 Règles d’applicabilité** pour les paramètres suivants, procédez comme suit :

   - Dans **Règle**, sélectionnez **Attribuer un profil si**, ou **Ne pas attribuer de profil si**
   - Dans **Propriété**, sélectionnez la propriété à laquelle vous souhaitez que cette règle s’applique.
   - Dans **Valeur**, entrez la valeur ou la plage de valeurs applicable.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem07-5-applicability-rules.png" alt-text="Règles d’applicabilité dans le portail du centre d’administration Microsoft Endpoint Manager" lightbox="images/mem07-5-applicability-rules.png":::

10. Sélectionnez **Suivant**. À l’étape **6 Vérifier + créer**, passez en revue les paramètres et les informations que vous avez sélectionnés et entrés, puis sélectionnez **Créer**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mem08-6-review-create.png" alt-text="L’option Vérifier et créer dans le portail du Centre d’administration Microsoft Endpoint Manager" lightbox="images/mem08-6-review-create.png":::

    > [!NOTE]
    > Les règles sont actives et actives en quelques minutes.

> [!NOTE]
> Gestion des conflits :
>
> Si vous attribuez à un appareil deux stratégies ASR différentes, la façon dont les conflits sont gérés est des règles qui se voient attribuer des états différents, il n’y a pas de gestion des conflits en place et le résultat est une erreur.
>
> Les règles non conflictuelles n’entraînent pas d’erreur et la règle est appliquée correctement. Le résultat est que la première règle est appliquée et que les règles suivantes non conflictuelles sont fusionnées dans la stratégie.

### <a name="mdm"></a>GPM

Utilisez le fournisseur de services de configuration (CSP) [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) pour activer et définir individuellement le mode pour chaque règle.

Voici un exemple de référence, utilisant des valeurs GUID pour la [référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

Les valeurs à activer (Bloquer), désactiver, avertir ou activer en mode audit sont les suivantes :

- 0 : Désactiver (désactiver la règle ASR)
- 1 : Bloquer (activer la règle ASR)
- 2 : Audit (Évaluer l’impact de la règle ASR sur votre organisation si elle est activée)
- 6 : Avertir (activez la règle ASR, mais autorisez l’utilisateur final à contourner le bloc). Le mode d’avertissement est disponible pour la plupart des règles ASR.

Utilisez le fournisseur de services de configuration (CSP) [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) pour ajouter des exclusions.

Exemple :

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> Veillez à entrer des valeurs OMA-URI sans espaces.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Dans Microsoft Endpoint Configuration Manager, accédez à **Ressources et conformité**\>**Endpoint Protection**\>**Windows Defender Exploit Guard**.

2. Sélectionnez **Accueil**\>**Créer une stratégie Exploit Guard**.

3. Entrez un nom et une description, sélectionnez **Réduction de la surface d’attaque**, puis sélectionnez **Suivant**.

4. Choisissez les règles qui bloquent ou auditent les actions, puis sélectionnez **Suivant**.

5. Passez en revue les paramètres et sélectionnez **Suivant** pour créer la stratégie.

6. Une fois la stratégie créée, sélectionnez **Fermer**.

> [!WARNING]
> Il existe un problème connu lié à l’applicabilité de la réduction de la surface d’attaque sur les versions du système d’exploitation du serveur, qui est marqué comme conforme sans aucune application réelle. Actuellement, il n’y a pas d’ETA pour le moment où cela sera résolu.

### <a name="group-policy"></a>Stratégie de groupe

> [!WARNING]
> Si vous gérez vos ordinateurs et appareils avec Intune, Configuration Manager ou une autre plateforme de gestion au niveau de l’entreprise, le logiciel de gestion remplace les paramètres de stratégie de groupe en conflit au démarrage.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console de gestion des stratégies de groupe](https://technet.microsoft.com/library/cc731212.aspx), faites un clic droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier**.

2. Dans l’**Éditeur de gestion des stratégies de groupe**, accédez à **Configuration ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence **des composants** \> Windows **Microsoft Defender Antivirus** \> **Microsoft Defender Exploit Guard** \> **Réduction de la surface d’attaque**.

4. Sélectionnez **Configurer les règles de réduction de la surface** d’attaque, puis sélectionnez **Activé**. Vous pouvez ensuite définir l’état individuel de chaque règle dans la section options. Sélectionnez **Afficher...** et entrez l’ID de règle dans la colonne Nom de la **valeur** et l’état que vous avez choisi dans la colonne **Valeur** comme suit :

   - 0 : Désactiver (désactiver la règle ASR)
   - 1 : Bloquer (activer la règle ASR)
   - 2 : Audit (Évaluer l’impact de la règle ASR sur votre organisation si elle est activée)
   - 6 : Avertir (Activer la règle ASR, mais autoriser l’utilisateur final à contourner le blocage)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="Règles ASR dans stratégie de groupe" lightbox="images/asr-rules-gp.png":::

5. Pour exclure des fichiers et des dossiers des règles ASR, sélectionnez le paramètre **Exclure les fichiers et les chemins des règles de réduction** de la surface d’attaque et définissez l’option **sur Activé**. Sélectionnez **Afficher** et entrez chaque fichier ou dossier dans la colonne **Nom de la valeur** . Entrez **0** dans la colonne **Valeur** pour chaque élément.

   > [!WARNING]
   > N’utilisez pas de guillemets, car ils ne sont pas pris en charge pour la colonne Nom de la **valeur** ou la colonne **Valeur** .
   > L’ID de règle ne doit pas avoir d’espaces de début ou de fin.

### <a name="powershell"></a>PowerShell

> [!WARNING]
> Si vous gérez vos ordinateurs et appareils avec Intune, Configuration Manager ou une autre plateforme de gestion au niveau de l’entreprise, le logiciel de gestion remplace tous les paramètres PowerShell en conflit au démarrage. Pour permettre aux utilisateurs de définir la valeur à l’aide de PowerShell, utilisez l’option « Défini par l’utilisateur » pour la règle dans la plateforme de gestion.
> « Défini par l’utilisateur » permet à un utilisateur administrateur local de configurer la règle.
> Le paramètre d’option Défini par l’utilisateur est illustré dans la figure suivante.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-user-defined.png" alt-text="Option Activer pour la sécurité des informations d’identification" lightbox="images/asr-user-defined.png":::

1. Tapez **powershell** dans le menu Démarrer, cliquez avec le bouton droit sur **Windows PowerShell** et sélectionnez **Exécuter en tant qu’administrateur**.

2. Tapez l’une des applets de commande suivantes. (Reportez-vous aux [informations de référence sur les règles de réduction de la surface](attack-surface-reduction-rules-reference.md) d’attaque pour plus d’informations, telles que l’ID de règle.)

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    Pour activer les règles ASR en mode audit, utilisez l’applet de commande suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    Pour activer les règles ASR en mode avertissement, utilisez l’applet de commande suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Warn
    ```

    Pour activer l’utilisation abusive par blocage ASR des pilotes signés vulnérables exploités, utilisez l’applet de commande suivante :

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    Pour désactiver les règles ASR, utilisez l’applet de commande suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > Vous devez spécifier l’état individuellement pour chaque règle, mais vous pouvez combiner des règles et des états dans une liste séparée par des virgules.
    >
    > Dans l’exemple suivant, les deux premières règles sont activées, la troisième règle est désactivée et la quatrième règle est activée en mode audit :
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    Vous pouvez également utiliser le `Add-MpPreference` verbe PowerShell pour ajouter de nouvelles règles à la liste existante.

    > [!WARNING]
    > `Set-MpPreference` remplace toujours l’ensemble de règles existant. Si vous souhaitez ajouter à l’ensemble existant, utilisez `Add-MpPreference` à la place.
    > Vous pouvez obtenir la liste des règles et leur état actuel à l’aide `Get-MpPreference`de .

3. Pour exclure des fichiers et des dossiers des règles ASR, utilisez l’applet de commande suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Continuez à utiliser `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` pour ajouter d’autres fichiers et dossiers à la liste.

    > [!IMPORTANT]
    > Utilisez `Add-MpPreference` pour ajouter ou ajouter des applications à la liste. L’utilisation de l’applet `Set-MpPreference` de commande remplace la liste existante.

## <a name="related-articles"></a>Articles connexes

- [Informations de référence sur les règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)
- [Évaluer la réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
- [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction.md)
