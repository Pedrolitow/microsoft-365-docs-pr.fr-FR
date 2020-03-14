---
title: Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 3/11/2020
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Les administrateurs peuvent activer la prise en charge de l’étiquette de sensibilité pour les fichiers Word, Excel et PowerPoint dans SharePoint et OneDrive.
ms.openlocfilehash: ef97215480949c8dec841fc857bed8945e26cacc
ms.sourcegitcommit: 08a4ee7765f3eba42f0c037c5c564c581e45df3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "42637277"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive-public-preview"></a>Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)

Avant cet aperçu, lorsque vous avez appliqué des étiquettes de confidentialité incluant le chiffrement aux fichiers Office stockés dans SharePoint et OneDrive, le service n’a pas pu traiter le contenu de ces fichiers. La co-création, la découverte électronique, la protection contre la perte de données, la recherche, l’Delve et d’autres fonctionnalités collaboratives ne fonctionnaient pas dans ces circonstances. Cet aperçu active ces fonctionnalités pour les fichiers nouveaux et modifiés pour lesquels une étiquette de sensibilité appliquée inclut le chiffrement avec une clé basée sur le Cloud :

- SharePoint reconnaît les étiquettes de confidentialité appliquées aux fichiers Word, Excel et PowerPoint dans SharePoint et OneDrive : lorsque le fichier est stocké dans SharePoint, le chiffrement à partir d’Azure information protection est supprimé afin que le contenu du fichier puisse être traité. Pour plus d’informations sur la façon dont les documents sont protégés pendant qu’ils sont stockés dans SharePoint, consultez la rubrique [chiffrement des données dans OneDrive entreprise et SharePoint Online](data-encryption-in-odb-and-spo.md).

- Lorsque vous téléchargez ou accédez à ce fichier à partir de SharePoint ou de OneDrive, l’étiquette de sensibilité et tous les paramètres de chiffrement de l’étiquette sont réappliqués avec le fichier, et ces paramètres restent en vigueur chaque fois que le fichier est enregistré. En raison de ce comportement, assurez-vous que vous fournissez une aide aux utilisateurs pour n’utiliser que des étiquettes pour protéger des documents. Pour plus d’informations, consultez la rubrique [options de gestion des droits relatifs à l’information (IRM) et les étiquettes de confidentialité](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- Pour que SharePoint supprime le chiffrement du fichier lors du chargement, l’utilisateur qui télécharge le fichier étiqueté et chiffré doit disposer des droits d’utilisation pour afficher au moins le fichier. SharePoint ne supprime pas le chiffrement des fichiers si l’utilisateur ne peut pas les ouvrir en dehors de SharePoint.

- Utilisez Office sur le Web (Word, Excel, PowerPoint) pour ouvrir et modifier les fichiers Office dont les étiquettes de confidentialité appliquent le chiffrement. Les autorisations qui ont été affectées au chiffrement sont appliquées. Avec Word sur le Web, vous pouvez également utiliser l’étiquetage automatique lorsque vous modifiez ces documents.

- Office 365 eDiscovery prend en charge la recherche de texte intégral pour ces fichiers. Les stratégies de protection contre la perte de données couvrent le contenu de ces fichiers.

- Trois nouveaux [événements d’audit](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) sont disponibles pour la surveillance des étiquettes de confidentialité qui sont appliquées à l’aide d’Office sur le Web :
  - **Étiquette de confidentialité appliquée au fichier**
  - **Étiquette de confidentialité modifiée appliquée au fichier**
  - **Suppression de l'étiquette de confidentialité sur le document**

> [!NOTE]
> Si le chiffrement n’a pas été appliqué avec une clé basée sur le Cloud, mais une clé locale, une topologie de gestion de clés est souvent appelée « conserver votre propre clé » (HYOK), le comportement de SharePoint ne change pas avec cet aperçu.
>
> Le comportement de SharePoint n’est pas modifié pour les fichiers étiquetés et chiffrés existants dans SharePoint avant l’activation de l’aperçu. Pour que ces fichiers bénéficient des nouvelles fonctionnalités, vous devez les télécharger et les charger ou les modifier après avoir activé l’aperçu. Par exemple, ils seront renvoyés dans les résultats de recherche et de découverte électronique.

Vous pouvez également appliquer des étiquettes de confidentialité à Microsoft Teams, aux groupes Office 365 et aux sites SharePoint. Pour plus d’informations sur cet aperçu distinct, voir [use sensitive labels with Microsoft Teams, Office 365 Groups et SharePoint sites (public Preview)](sensitivity-labels-teams-groups-sites.md).

Vous pouvez toujours choisir de désactiver cet aperçu à tout moment.

Regardez la vidéo suivante (pas de son) pour voir ces nouvelles fonctionnalités en action :

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

## <a name="requirements"></a>Configuration requise

Ces fonctionnalités fonctionnent avec les [étiquettes de confidentialité](sensitivity-labels.md) uniquement. Si vous disposez actuellement d’étiquettes Azure information protection, commencez par les migrer vers les étiquettes de confidentialité afin de pouvoir activer ces fonctionnalités pour les nouveaux fichiers que vous téléchargez. Pour obtenir des instructions, voir [Comment migrer des étiquettes Azure information protection vers des étiquettes de confidentialité unifiée](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)

Pour cet aperçu, utilisez la version 19.002.0121.0008 ou une version ultérieure de l’application de synchronisation OneDrive sur Windows et la version 19.002.0107.0008 ou ultérieure sur Mac. Ces deux versions ont été publiées le 28 janvier 2019 et sont actuellement publiées sur toutes les sonneries. Pour plus d’informations, consultez les [notes de publication de OneDrive](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). Une fois cet aperçu activé, les utilisateurs qui exécutent une version plus ancienne de l’application de synchronisation sont invités à les mettre à jour.

## <a name="limitations"></a>Limites

- Lorsque vous activez cet aperçu, les utilisateurs qui modifient une étiquette sur un fichier dans un dossier de synchronisation OneDrive peuvent ne pas être en mesure d’enregistrer les autres modifications qu’ils ont apportées au fichier.  Les utilisateurs voient un [cercle rouge avec une erreur d’icône en croix blanche](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3)et ils sont invités à enregistrer les nouvelles modifications en tant que copie distincte.  En plus des modifications apportées aux étiquettes par les utilisateurs, le même comportement peut se produire si un administrateur modifie les paramètres d’une étiquette publiée qui est déjà appliquée aux fichiers téléchargés sur le client de synchronisation des utilisateurs.
    
    Pour éviter de perdre le travail de ces scénarios, effectuez l’une des actions suivantes :
    - Pour appliquer des étiquettes, utilisez les versions Web des applications Office.
    - Fermez un fichier après avoir appliqué une étiquette, puis rouvrez le fichier pour effectuer d’autres modifications.

- SharePoint n’applique pas automatiquement les étiquettes de confidentialité aux fichiers existants que vous avez déjà chiffrés à l’aide des étiquettes Azure information protection. À la place, pour que les fonctionnalités fonctionnent après avoir activé cet aperçu, effectuez les tâches suivantes :
    
    1. Assurez-vous que vous avez déplacé les étiquettes Azure information protection sur les étiquettes de confidentialité et les avez publiées à partir du centre de conformité Microsoft 365 ou du centre d’administration des étiquettes équivalent.
    
    2. Téléchargez les fichiers, puis téléchargez-les vers SharePoint.

- SharePoint ne peut pas traiter les fichiers chiffrés lorsque l’étiquette qui a appliqué le chiffrement a l’une des configurations suivantes pour le chiffrement :
    - **Autoriser les utilisateurs à attribuer des autorisations lorsqu’ils appliquent l’étiquette** et la case à cocher **dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier des autorisations** est sélectionné. Ce paramètre est parfois appelé « autorisations définies par l’utilisateur ».
    - **L’accès des utilisateurs au contenu expire** est défini sur une valeur autre que **jamais**.
    
    Pour les étiquettes avec l’une de ces configurations de chiffrement, les étiquettes ne sont pas affichées pour les utilisateurs dans Office sur le Web. En outre, les nouvelles fonctionnalités de cet aperçu ne peuvent pas être utilisées avec des documents étiquetés qui possèdent déjà ces paramètres de chiffrement. Par exemple, ces documents ne seront pas renvoyés dans les résultats de recherche, même s’ils sont mis à jour.

- Pour un document chiffré qui accorde des autorisations de modification à un utilisateur, la copie ne peut pas être bloquée dans les versions Web des applications Office.

- Le site de suivi des documents Azure information protection n’est pas pris en charge.

- Les applications de bureau Office et les applications mobiles ne prennent pas en charge la co-création. Au lieu de cela, ces applications continuent à ouvrir des fichiers en mode d’édition exclusive.

- Si un document étiqueté est téléchargé vers SharePoint et que l’étiquette a été appliquée à l’aide d’un compte d’un nom principal de service, le document ne peut pas être ouvert dans Office sur le Web. Les exemples de scénarios incluent Microsoft Cloud App Security et un fichier envoyé à teams par courrier électronique.

- Les utilisateurs peuvent rencontrer des problèmes d’enregistrement après avoir effectué une mise hors connexion ou en mode veille quand, au lieu d’utiliser Office pour le Web, ils utilisent le bureau et les applications mobiles pour Word, Excel ou PowerPoint. Pour ces utilisateurs, lorsqu’ils reprennent leur session d’application Office et essaient d’enregistrer les modifications, ils voient s’afficher un message d’échec de téléchargement avec une option permettant d’enregistrer une copie au lieu d’enregistrer le fichier d’origine. 

- Les documents qui ont été chiffrés de la manière suivante ne peuvent pas être ouverts dans Office sur le Web :
    - Chiffrement qui utilise une clé locale (« conserver votre propre clé » ou HYOK)
    - Chiffrement appliqué indépendamment d’une étiquette, par exemple, en appliquant directement un modèle de protection des droits de gestion des droits.

- Si vous supprimez une étiquette qui a été appliquée à un document dans SharePoint, au lieu de supprimer l’étiquette de la stratégie d’étiquette applicable, le document lorsqu’il est téléchargé ne sera pas étiqueté ou chiffré. En comparaison, si le document étiqueté est stocké en dehors de SharePoint, le document reste chiffré si l’étiquette est supprimée. Notez que même si vous pouvez supprimer des étiquettes pendant une phase de test, il est très rare de supprimer une étiquette dans un environnement de production.

## <a name="prepare-the-sharepoint-online-management-shell-for-the-preview"></a>Préparer SharePoint Online Management Shell pour l’aperçu

Avant d’activer l’aperçu, vérifiez que vous exécutez SharePoint Online Management Shell version 16.0.19418.12000 ou supérieure. Si vous disposez déjà de la dernière version, vous pouvez activer l’aperçu.

1. Si vous avez installé une version antérieure de SharePoint Online Management Shell à partir de la Galerie PowerShell, vous pouvez mettre à jour le module en exécutant l’applet de commande suivante.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. Par ailleurs, si vous avez installé une version antérieure de SharePoint Online Management Shell à partir du centre de téléchargement Microsoft, vous pouvez également accéder à la console **Ajout/suppression de programmes** et désinstaller SharePoint Online Management Shell.

3. Dans un navigateur web, accédez à la page du Centre de téléchargement et [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. Sélectionnez votre langue, puis cliquez sur **Télécharger**.

5. Choisissez entre le fichier x64 et x86 .msi. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. Si vous ne le Sachez pas, consultez [la version du système d’exploitation Windows que je suis en cours d’exécution ?](https://support.microsoft.com/help/13443/windows-which-operating-system)


6. Une fois que vous avez téléchargé le fichier, exécutez le fichier et suivez les étapes de l’Assistant d’installation.

## <a name="enable-the-preview-by-using-microsoft-powershell-opt-in"></a>Activer l’aperçu à l’aide de Microsoft PowerShell (opt-in)

Pour activer l’aperçu, utilisez l’applet de commande Set-SPOTenant :

1. À l’aide d’un compte professionnel ou scolaire disposant de privilèges d’administrateur général ou d’administrateur SharePoint dans Office 365, connectez-vous à SharePoint. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

2. Exécutez la commande suivante :

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true  
    ```

## <a name="schedule-roll-out-after-you-create-or-change-a-sensitivity-label"></a>Planifier le déploiement après la création ou la modification d’une étiquette de sensibilité

Une fois que vous avez créé ou modifié une étiquette de sensibilité dans le centre de conformité Microsoft 365, publiez-le par étapes. Si vous publiez des étiquettes qui n’ont pas été entièrement synchronisées, lorsque les utilisateurs appliquent les étiquettes aux fichiers et les chargent sur SharePoint, les fichiers ne peuvent pas être ouverts dans les versions Web des applications Office. La recherche et eDiscovery ne fonctionnent pas non plus pour les fichiers.

Nous vous recommandons de suivre les étapes suivantes :

1. Publiez l’étiquette de confidentialité nouvelle ou modifiée uniquement sur une ou deux personnes.

2. Patientez pendant au moins 24 heures après la publication initiale. Vérifiez que l’étiquette est entièrement synchronisée.

3. Publiez l’étiquette plus largement.

## <a name="disable-the-preview-by-using-microsoft-powershell-opt-out"></a>Désactiver l’aperçu à l’aide de Microsoft PowerShell (opt-out)

Si vous désactivez cet aperçu, les fichiers que vous avez téléchargés pendant l’aperçu continueront à être protégés par l’étiquette. Les paramètres correspondants continuent à être appliqués. Lorsque vous appliquez des étiquettes à de nouveaux fichiers après avoir désactivé l’aperçu, la recherche de texte intégral, la découverte électronique et la co-création ne fonctionneront plus.

Pour désactiver l’aperçu, utilisez l’applet de commande Set-SPOTenant :

1. À l’aide d’un compte professionnel ou scolaire disposant de privilèges d’administrateur général ou d’administrateur SharePoint dans Office 365, connectez-vous à SharePoint. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

2. Exécutez la commande suivante :

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $false
    ```
