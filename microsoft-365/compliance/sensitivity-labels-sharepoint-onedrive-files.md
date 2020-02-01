---
title: Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Les administrateurs peuvent activer la prise en charge de l’étiquette de sensibilité pour les fichiers Word, Excel et PowerPoint dans SharePoint et OneDrive.
ms.openlocfilehash: a1b42525984080d56a0f95018003cd251bff0122
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41597501"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive-public-preview"></a>Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)

Avant cet aperçu, lorsque vous avez appliqué des étiquettes de confidentialité incluant le chiffrement aux fichiers Office stockés dans SharePoint et OneDrive, le service n’a pas pu traiter le contenu de ces fichiers. La co-création, la découverte électronique, la protection contre la perte de données, la recherche, l’Delve et d’autres fonctionnalités collaboratives ne fonctionnaient pas dans ces circonstances. Cet aperçu active ces fonctionnalités lorsque le chiffrement a été appliqué à l’aide d’une clé basée sur le Cloud :

- SharePoint reconnaît les étiquettes de confidentialité appliquées aux fichiers Word, Excel et PowerPoint dans SharePoint et OneDrive. SharePoint applique également les paramètres qui correspondent à chaque étiquette.

- Lorsque vous téléchargez un fichier à partir de SharePoint ou de OneDrive, l’étiquette de sensibilité se déplace avec le fichier et les paramètres restent appliqués.

- Appliquer des étiquettes de confidentialité aux fichiers Office, et ouvrir et modifier les fichiers sur lesquels des étiquettes de sensibilité sont appliquées (si les autorisations de l’étiquette le permettent) à l’aide des versions Web de Word, Excel et PowerPoint. Avec Word sur le Web, vous pouvez également utiliser l’étiquetage automatique lorsque vous modifiez des documents.

- Office 365 eDiscovery prend en charge la recherche en texte intégral dans les fichiers sur lesquels des étiquettes de sensibilité sont appliquées. Les stratégies de protection contre la perte de données couvrent le contenu de ces fichiers.

- Trois nouveaux événements d’audit sont disponibles pour la surveillance des étiquettes de confidentialité :
  - FileSensitivityApplied
  - FileSensitivityLabelChanged
  - FileSensitivityLabelRemoved

> [!NOTE]
> Si le chiffrement n’a pas été appliqué avec une clé basée sur le Cloud, mais une clé locale, une topologie de gestion de clés est souvent appelée « conserver votre propre clé » (HYOK), le comportement de SharePoint ne change pas avec cet aperçu. 

Vous pouvez également appliquer des étiquettes de confidentialité à Microsoft Teams, aux groupes Office 365 et aux sites SharePoint. Pour plus d’informations sur cet aperçu distinct, voir [use sensitive labels with Microsoft Teams, Office 365 Groups et SharePoint sites (public Preview)](sensitivity-labels-teams-groups-sites.md).

Vous pouvez toujours choisir de désactiver cet aperçu à tout moment.

Regardez la vidéo suivante (pas de son) pour voir ces nouvelles fonctionnalités en action :

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

## <a name="requirements"></a>Configuration requise

Ces fonctionnalités fonctionnent avec les [étiquettes de confidentialité](sensitivity-labels.md) uniquement. Si vous disposez actuellement d’étiquettes Azure information protection, commencez par les migrer vers les étiquettes de confidentialité afin de pouvoir activer ces fonctionnalités pour les nouveaux fichiers que vous téléchargez. Pour obtenir des instructions, voir [Comment migrer des étiquettes Azure information protection vers des étiquettes de confidentialité unifiée](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)

Pour cet aperçu, utilisez la version 19.002.0121.0008 ou une version ultérieure de l’application de synchronisation OneDrive sur Windows et la version 19.002.0107.0008 ou ultérieure sur Mac. Ces deux versions ont été publiées le 28 janvier 2019 et sont actuellement publiées sur toutes les sonneries. Pour plus d’informations, consultez les [notes de publication de OneDrive](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). Une fois cet aperçu activé, les utilisateurs qui exécutent une version plus ancienne de l’application de synchronisation sont invités à les mettre à jour.

## <a name="limitations"></a>Limites

- Lorsque vous activez cet aperçu, les utilisateurs qui modifient une étiquette en un fichier dans un dossier de synchronisation OneDrive peuvent ne pas être en mesure d’enregistrer les autres modifications qu’ils ont apportées au fichier.  Les utilisateurs voient un [cercle rouge avec une erreur d’icône en croix blanche](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3)et ils sont invités à enregistrer les nouvelles modifications en tant que copie distincte.  En plus des modifications apportées aux étiquettes par les utilisateurs, le même comportement peut se produire si un administrateur modifie les paramètres d’une étiquette publiée qui est déjà appliquée aux fichiers téléchargés sur le client de synchronisation des utilisateurs.
    
    Pour éviter de perdre le travail de ces scénarios, effectuez l’une des actions suivantes :
    - Pour appliquer des étiquettes, utilisez les versions Web des applications Office.
    - Fermez un fichier après avoir appliqué une étiquette, puis rouvrez le fichier pour effectuer d’autres modifications.

- SharePoint n’applique pas automatiquement les nouvelles étiquettes aux fichiers existants que vous avez déjà chiffrés à l’aide des étiquettes Azure information protection. À la place, pour que les fonctionnalités fonctionnent après avoir activé cet aperçu, effectuez les tâches suivantes :
    
    1. Assurez-vous que vous avez déplacé les étiquettes Azure information protection sur les étiquettes de confidentialité et les avez publiées à partir du centre de conformité Microsoft 365 ou du centre d’administration des étiquettes équivalent.
    
    2. Téléchargez les fichiers et téléchargez-les sur SharePoint.

- SharePoint ne peut pas traiter les fichiers chiffrés lorsque l’étiquette qui a appliqué le chiffrement a l’une des configurations suivantes pour le chiffrement :
    - **Autoriser les utilisateurs à attribuer des autorisations lors de l’application de l’étiquette** et **dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier des autorisations**
    - **L’accès des utilisateurs au contenu expire** est défini sur une valeur autre que **jamais**.

- Pour un document chiffré qui accorde des autorisations de modification à un utilisateur, la copie ne peut pas être bloquée dans les versions Web des applications Office.

- Le site de suivi des documents Azure information protection n’est pas pris en charge.

- Les applications de bureau Office et les applications mobiles ne prennent pas en charge la co-création. Au lieu de cela, ces applications continuent à ouvrir des fichiers en mode d’édition exclusive.

- Si une étiquette inclut le chiffrement, la sécurité des applications Cloud Microsoft ne peut pas lire les informations d’étiquette pour les fichiers dans SharePoint.

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
