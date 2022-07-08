---
title: Activer les étiquettes de confidentialité pour les fichiers Office
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Les administrateurs peuvent activer la prise en charge des étiquettes de confidentialité pour les fichiers Word, Excel et PowerPoint dans SharePoint et OneDrive.
ms.openlocfilehash: 15985ea95c3e4a562a4cbc51f84a10af2592d53f
ms.sourcegitcommit: ebaa70d0da4a600efe52b5008eaddb511d36df8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66687693"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Activez l’étiquetage intégré pour [les fichiers Office pris en charge](sensitivity-labels-office-apps.md#office-file-types-supported) dans SharePoint et OneDrive afin que les utilisateurs puissent appliquer vos [étiquettes de confidentialité](sensitivity-labels.md) dans Office sur le Web. Lorsque cette fonctionnalité est activée, les utilisateurs voient le bouton **Sensibilité** dans le ruban afin qu’ils puissent appliquer des étiquettes et voir n’importe quel nom d’étiquette appliqué dans la barre d’état.

L’activation de cette fonctionnalité permet également à SharePoint et OneDrive de traiter le contenu des fichiers Office chiffrés à l’aide d’une étiquette de confidentialité. L’étiquette peut être appliquée dans Office sur le Web, ou dans des applications de bureau Office et chargée ou enregistrée dans SharePoint et OneDrive. Tant que vous n’activez pas cette fonctionnalité, ces services ne peuvent pas traiter les fichiers chiffrés, ce qui signifie que la co-création, la découverte électronique, la protection contre la perte de données Microsoft Purview, la recherche et d’autres fonctionnalités collaboratives ne fonctionneront pas pour ces fichiers.

Après avoir activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive, pour les fichiers nouveaux et modifiés qui ont une étiquette de confidentialité qui applique le chiffrement avec une clé cloud (et n’utilise pas [le chiffrement à double clé](double-key-encryption.md) :

- Pour les fichiers Word, Excel et PowerPoint, SharePoint et OneDrive reconnaissent l’étiquette et peuvent désormais traiter le contenu du fichier chiffré.

- Lorsque les utilisateurs téléchargent ou accèdent à ces fichiers à partir de SharePoint ou OneDrive, l’étiquette de confidentialité et les paramètres de chiffrement de l’étiquette sont appliqués et restent avec le fichier, où qu’il soit stocké. Veillez à fournir des conseils aux utilisateurs pour utiliser uniquement des étiquettes pour protéger les documents. Pour plus d’informations, consultez les [options de gestion des droits relatifs à l’information (IRM) et les étiquettes de confidentialité](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- Lorsque les utilisateurs chargent des fichiers étiquetés et chiffrés dans SharePoint ou OneDrive, ils doivent avoir au moins des droits d’affichage sur ces fichiers. Par exemple, ils peuvent ouvrir les fichiers en dehors de SharePoint. S’ils n’ont pas ce droit d’utilisation minimal, le chargement réussit, mais le service ne reconnaît pas l’étiquette et ne peut pas traiter le contenu du fichier.

- Utilisez Office sur le Web (Word, Excel, PowerPoint) pour ouvrir et modifier des fichiers Office qui ont des étiquettes de confidentialité qui appliquent le chiffrement. Les autorisations qui ont été attribuées avec le chiffrement sont appliquées. Vous pouvez également utiliser [l’étiquetage automatique](apply-sensitivity-label-automatically.md) pour ces documents.

- Les utilisateurs externes peuvent accéder aux documents étiquetés avec le chiffrement à l’aide de comptes invités. Pour plus d’informations, consultez [Support pour les utilisateurs externes et le contenu étiqueté](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Office 365 eDiscovery prend en charge la recherche en texte intégral pour ces fichiers et les stratégies de protection contre la perte de données prennent en charge le contenu de ces fichiers.

> [!NOTE]
> Si le chiffrement a été appliqué avec une clé locale (topologie de gestion des clés souvent appelée « conserver votre propre clé » ou HYOK), ou à l’aide du [chiffrement à double clé](double-key-encryption.md), le comportement du service pour le traitement du contenu du fichier ne change pas. Par conséquent, pour ces fichiers, la co-création, la découverte électronique, la protection contre la perte de données, la recherche et d’autres fonctionnalités collaboratives ne fonctionneront pas.
>
> Le comportement de SharePoint et OneDrive ne change pas non plus pour les fichiers existants dans ces emplacements qui sont étiquetés avec le chiffrement à l’aide d’une seule clé Azure. Pour que ces fichiers bénéficient des nouvelles fonctionnalités après avoir activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive, les fichiers doivent être téléchargés et chargés à nouveau ou modifiés.

Une fois que vous avez activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive, trois nouveaux [événements d’audit sont disponibles](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) pour la surveillance des étiquettes de confidentialité appliquées aux documents dans SharePoint et OneDrive :

- **Étiquette de confidentialité appliquée au fichier**
- **Étiquette de confidentialité modifiée appliquée au fichier**
- **Suppression de l'étiquette de confidentialité sur le document**

Regardez la vidéo suivante (sans audio) pour voir les nouvelles fonctionnalités en action :

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

Vous avez toujours le choix de désactiver les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive ([désactivation](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)) à tout moment.

Si vous protégez actuellement des documents dans SharePoint à l’aide de la Gestion des droits relatifs à l’information SharePoint (IRM), veillez à consulter la section Gestion [des droits relatifs à l’information (IRM) et les étiquettes de confidentialité](#sharepoint-information-rights-management-irm-and-sensitivity-labels) de cette page.

## <a name="requirements"></a>Configuration requise

Ces nouvelles fonctionnalités fonctionnent uniquement avec [les étiquettes de confidentialité](sensitivity-labels.md) . Si vous avez actuellement des étiquettes Azure Information Protection, commencez par les migrer vers des étiquettes de confidentialité afin de pouvoir activer ces fonctionnalités pour les nouveaux fichiers que vous chargez. Pour voir les instructions, consultez [Migration des étiquettes Azure Information Protection vers des étiquettes de confidentialité unifiées](/azure/information-protection/configure-policy-migrate-labels).

Utilisez l’application de synchronisation OneDrive version 19.002.0121.0008 ou ultérieure sur Windows et la version 19.002.0107.0008 ou ultérieure sur Mac. Ces deux versions ont été publiées le 28 janvier 2019 et sont actuellement publiées sur tous les anneaux. Pour plus d’informations, consultez les [notes de publication de OneDrive](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). Une fois que vous avez activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive, les utilisateurs qui exécutent une version antérieure de l’application de synchronisation sont invités à la mettre à jour.

## <a name="limitations"></a>Limites

- SharePoint et OneDrive ne peuvent pas traiter certains fichiers étiquetés et chiffrés à partir d’applications de bureau Office lorsque ces fichiers contiennent des données PowerQuery, des données stockées par des compléments personnalisés ou des composants XML personnalisés tels que les propriétés de page de garde, les schémas de type de contenu, le panneau Informations sur les documents personnalisés et le XSN personnalisé. Cette limitation s’applique également aux fichiers qui incluent une [bibliographie](https://support.microsoft.com/en-us/office/create-a-bibliography-citations-and-references-17686589-4824-4940-9c69-342c289fa2a5) et aux fichiers qui ont un [ID de document](https://support.microsoft.com/office/enable-and-configure-unique-document-ids-ea7fee86-bd6f-4cc8-9365-8086e794c984) ajouté lors du chargement.

    Pour ces fichiers, appliquez une étiquette sans chiffrement afin qu’elles puissent être ouvertes ultérieurement dans Office sur le web, ou demandez aux utilisateurs d’ouvrir les fichiers dans leurs applications de bureau. Les fichiers étiquetés et chiffrés uniquement dans Office sur le web ne sont pas affectés.

- SharePoint et OneDrive n’appliquent pas automatiquement des étiquettes de confidentialité aux fichiers existants que vous avez déjà chiffrés à l’aide d’étiquettes Azure Information Protection. Au lieu de cela, pour que les fonctionnalités fonctionnent après avoir activé des étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive, effectuez les tâches suivantes :

    1. Assurez-vous d’avoir [migré les étiquettes Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels) vers des étiquettes de [confidentialité et de les avoir publiées](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) à partir du portail de conformité Microsoft Purview.
    2. Téléchargez les fichiers étiquetés, puis chargez-les à leur emplacement d’origine dans SharePoint ou OneDrive.

- SharePoint et OneDrive ne peuvent pas traiter les fichiers chiffrés lorsque l’étiquette qui a appliqué le chiffrement a l’une [des configurations suivantes pour le chiffrement](encryption-sensitivity-labels.md#configure-encryption-settings) :
  - **Permettre aux utilisateurs d'attribuer des autorisations lorsqu’ils appliquent l’étiquette** et la case à cocher **Dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier des autorisations** est sélectionnée. Ce paramètre est parfois appelé « autorisations définies par l’utilisateur ».
  - **L’expiration de l'accès des utilisateurs au contenu** est définie sur une valeur autre que **Jamais**.
  - **Chiffrement à double clé** est sélectionnée.

    Pour les étiquettes avec l’une de ces configurations de chiffrement, les étiquettes ne sont pas affichées aux utilisateurs dans Office sur le Web. En outre, les nouvelles fonctionnalités ne peuvent pas être utilisées avec des documents étiquetés qui ont déjà ces paramètres de chiffrement. Par exemple, ces documents ne seront pas retournés dans les résultats de la recherche, même s’ils sont mis à jour.

- Pour des raisons de performances, lorsque vous chargez ou enregistrez un document dans SharePoint et que l’étiquette du fichier n’applique pas le chiffrement, la colonne **Sensibilité** dans la bibliothèque de documents peut prendre un certain temps pour afficher le nom de l’étiquette. Prenez en compte ce délai si vous utilisez des scripts ou une automatisation qui dépendent du nom de l’étiquette dans cette colonne.

- Si un document est étiqueté alors qu’il est [extrait dans SharePoint](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de), la colonne **Sensibilité** de la bibliothèque de documents n’affiche pas le nom de l’étiquette tant que le document n’est pas archivé et ouvert ensuite dans SharePoint.

- Si un document étiqueté et chiffré est téléchargé à partir de SharePoint ou OneDrive par une application ou un service qui utilise un nom de principal de service, puis chargé à nouveau avec une étiquette qui applique différents paramètres de chiffrement, le chargement échoue. Un exemple de scénario est Microsoft Defender for Cloud Apps modifie une étiquette de confidentialité d’un fichier de **Confidentiel** à **Hautement confidentiel** ou de **Confidentiel** en **Général**.

    Le chargement n’échoue pas si l’application ou le service exécute d’abord l’applet de commande [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) , comme expliqué dans la section [Supprimer le chiffrement d’un document étiqueté](#remove-encryption-for-a-labeled-document) . Ou, avant le chargement, le fichier d’origine est supprimé ou le nom du fichier est modifié.

- Les utilisateurs peuvent rencontrer des retards dans la possibilité d’ouvrir des documents chiffrés dans le scénario d’enregistrement suivant : à l’aide d’une version de bureau d’Office, un utilisateur choisit Enregistrer sous pour un document qui a une étiquette de confidentialité qui applique le chiffrement. L’utilisateur sélectionne SharePoint ou OneDrive pour l’emplacement, puis tente immédiatement d’ouvrir ce document dans Office sur le Web. Si le service traite toujours le chiffrement, l’utilisateur voit un message indiquant que le document doit être ouvert dans son application de bureau. S’ils réessayent dans quelques minutes, le document s’ouvre correctement dans Office sur le Web.

- Pour les documents chiffrés, l’impression n’est pas prise en charge dans Office sur le Web.

- Pour les documents chiffrés dans Office sur le Web, la copie dans le Presse-papiers et les captures d’écran ne sont pas empêchées. Pour plus d’informations, consultez [La gestion des droits peut-elle empêcher les captures d’écran ?](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- Par défaut, les applications de bureau et les applications mobiles Office ne prennent pas en charge la co-création de fichiers étiquetés avec chiffrement. Ces applications continuent d’ouvrir des fichiers étiquetés et chiffrés en mode édition exclusif.

    > [!NOTE]
    > La co-édition est désormais prise en charge pour Windows et macOS, et en préversion pour iOS et Android. Pour plus d’informations, consultez [Activer la co-création pour les fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md).

- Si un administrateur modifie les paramètres d’une étiquette publiée déjà appliquée aux fichiers téléchargés sur le client de synchronisation des utilisateurs, il se peut que les utilisateurs ne puissent pas enregistrer les modifications qu’ils apportent au fichier dans leur dossier De synchronisation OneDrive. Ce scénario s’applique aux fichiers étiquetés avec chiffrement, ainsi qu’à la modification de l’étiquette à partir d’une étiquette qui n’a pas appliqué de chiffrement à une étiquette qui applique le chiffrement. Les utilisateurs voient un [cercle rouge avec une erreur d’icône de croix blanche](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3) et sont invités à enregistrer les nouvelles modifications sous la forme d’une copie distincte. Au lieu de cela, ils peuvent fermer et rouvrir le fichier, ou utiliser Office sur le Web.

- Les utilisateurs peuvent rencontrer des problèmes d’enregistrement après être passés en mode veille ou hors connexion lorsque, au lieu d’utiliser Office sur le Web, ils utilisent les applications de bureau et mobiles pour Word, Excel ou PowerPoint. Pour ces utilisateurs, lorsqu’ils reprennent leur session d’application Office et essaient d’enregistrer les modifications, ils voient un message d’échec de chargement avec une option permettant d’enregistrer une copie au lieu d’enregistrer le fichier d’origine.

- Les documents chiffrés de la manière suivante ne peuvent pas être ouverts dans Office sur le Web :
  - Chiffrement qui utilise une clé locale (« conserver votre propre clé » ou HYOK)
  - Chiffrement appliqué à l’aide du [chiffrement à double clé](double-key-encryption.md)
  - Chiffrement appliqué indépendamment d’une étiquette, par exemple, en appliquant directement un modèle de protection Rights Management.

- Les étiquettes configurées pour [d’autres langues](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell) ne sont pas prises en charge et affichent uniquement la langue d’origine.

- Si vous supprimez une étiquette qui a été appliquée à un document dans SharePoint ou OneDrive, au lieu de supprimer l’étiquette de la stratégie d’étiquette applicable, le document téléchargé ne sera ni étiqueté ni chiffré. En comparaison, si le document étiqueté est stocké en dehors de SharePoint ou OneDrive, le document reste chiffré si l’étiquette est supprimée. Notez que même si vous pouvez supprimer des étiquettes pendant une phase de test, il est très rare de supprimer une étiquette dans un environnement de production.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>Comment activer les étiquettes de confidentialité pour SharePoint et OneDrive (opt-in)

Vous pouvez activer les nouvelles fonctionnalités à l’aide du portail de conformité Microsoft Purview ou de PowerShell. Pour obtenir des instructions, consultez les sections suivantes.

Comme avec toutes les modifications de configuration au niveau du locataire pour SharePoint et OneDrive, il faut environ 15 minutes pour que la modification prenne effet.

### <a name="use-the-microsoft-purview-compliance-portal-to-enable-support-for-sensitivity-labels"></a>Utiliser le portail de conformité Microsoft Purview pour activer la prise en charge des étiquettes de confidentialité

Cette option est le moyen le plus simple d’activer les étiquettes de confidentialité pour SharePoint et OneDrive, mais vous devez vous connecter en tant qu’administrateur général pour votre locataire.

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com/) en tant qu’administrateur général et accédez aux **étiquettes** **de** protection  > **des informations** de solutions  > 

2. Si vous voyez un message pour activer la possibilité de traiter le contenu dans les fichiers en ligne Office, sélectionnez **Activer maintenant** :

    ![Activez maintenant le bouton pour activer les étiquettes de confidentialité pour Office Online.](../media/sensitivity-labels-turn-on-banner.png)

    La commande s’exécute immédiatement et lorsque la page est actualisée, vous ne voyez plus le message ou le bouton.

> [!NOTE]
> Si vous avez Microsoft 365 Multi-Geo, vous devez utiliser PowerShell pour activer ces fonctionnalités pour tous vos emplacements géographiques. Pour plus d’informations, voir la section suivante.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>Utiliser PowerShell pour activer la prise en charge des étiquettes de confidentialité

En guise d’alternative à l’utilisation du portail de conformité Microsoft Purview, vous pouvez activer la prise en charge des étiquettes de confidentialité à l’aide de l’applet de commande [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) de SharePoint Online PowerShell.

Si vous avez Microsoft 365 Multi-Geo, vous devez utiliser PowerShell pour activer cette prise en charge de tous vos géolocalisations.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>Préparer SharePoint Online Management Shell

Avant d’exécuter la commande PowerShell pour activer les étiquettes de confidentialité des fichiers Office dans SharePoint et OneDrive, veillez à exécuter SharePoint Online Management Shell version 16.0.19418.12000 ou ultérieure. Si vous disposez déjà de la dernière version, vous pouvez passer à la [procédure suivante](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) pour exécuter la commande PowerShell.

1. Si vous avez installé une version antérieure de SharePoint Online Management Shell à partir de la Galerie PowerShell, vous pouvez mettre à jour le module en exécutant l’applet de commande suivante.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. Si vous avez installé une version antérieure de SharePoint Online Management Shell à partir du Centre de téléchargement Microsoft, vous pouvez également accéder à **Ajouter ou supprimer des programmes** et désinstaller SharePoint Online Management Shell.

3. Dans un navigateur web, accédez à la page du Centre de téléchargement et [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. Sélectionnez votre langue, puis cliquez sur **Télécharger**.

5. Choisissez entre le fichier x64 et x86 .msi. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. Si vous ne savez pas, voir [quelle version du système d’exploitation Windows suis-je en cours d’exécution ?](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. Une fois que vous avez téléchargé le fichier, exécutez le fichier et suivez les étapes de l’Assistant Installation.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>Exécutez la commande PowerShell pour activer la prise en charge des étiquettes de confidentialité

Pour activer les nouvelles fonctionnalités, utilisez l’applet de commande [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) avec le paramètre *EnableAIPIntegration* :

1. À l’aide d’un compte professionnel ou scolaire disposant de privilèges d’administrateur général ou d’administrateur SharePoint dans Microsoft 365, connectez-vous à SharePoint. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

    > [!NOTE]
    > Si vous avez Microsoft 365 Multi-Geo, utilisez le paramètre -URL avec [Connect-SPOService](/powershell/module/sharepoint-online/connect-sposervice) et spécifiez l’URL du site centre d’administration SharePoint Online pour l’un de vos emplacements géographiques.

2. Exécutez la commande suivante et appuyez sur **Y** pour confirmer :

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. Pour Microsoft 365 Multi-Geo : Répétez les étapes 1 et 2 pour chacun de vos emplacements géographiques restants.

## <a name="publishing-and-changing-sensitivity-labels"></a>Publication et modification d’étiquettes de confidentialité

Lorsque vous utilisez des étiquettes de confidentialité avec SharePoint et OneDrive, gardez à l’esprit que vous devez autoriser le temps de réplication lorsque vous publiez de nouvelles étiquettes de confidentialité ou mettez à jour les étiquettes de confidentialité existantes. Cela est particulièrement important pour les nouvelles étiquettes qui appliquent le chiffrement.

Par exemple : vous créez et publiez une étiquette de confidentialité qui applique le chiffrement et qui apparaît très rapidement dans l’application de bureau d’un utilisateur. L’utilisateur applique cette étiquette à un document, puis la charge sur SharePoint ou OneDrive. Si la réplication d’étiquette n’est pas terminée pour le service, les nouvelles fonctionnalités ne seront pas appliquées à ce document lors du chargement. Par conséquent, le document ne sera pas retourné dans la recherche ou pour eDiscovery et le document ne peut pas être ouvert dans Office sur le Web.

Pour plus d’informations sur le minutage des étiquettes, consultez [Quand s’attendre à ce que les nouvelles étiquettes et modifications prennent effet](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect).

Par mesure de protection, nous vous recommandons de publier de nouvelles étiquettes pour quelques utilisateurs de test, d’attendre au moins une heure, puis de vérifier le comportement de l’étiquette sur SharePoint et OneDrive. Attendez au moins un jour avant de mettre l’étiquette à la disposition d’un plus grand nombre d’utilisateurs en ajoutant plus d’utilisateurs à la stratégie d’étiquette existante ou en ajoutant l’étiquette à une stratégie d’étiquette existante pour vos utilisateurs standard. Au moment où vos utilisateurs standard voient l’étiquette, elle est déjà synchronisée avec SharePoint et OneDrive.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>Gestion des droits relatifs à l’information SharePoint (IRM) et étiquettes de confidentialité

[La gestion des droits relatifs à l’information SharePoint (IRM)](set-up-irm-in-sp-admin-center.md) est une technologie plus ancienne qui permet de protéger les fichiers au niveau de la liste et de la bibliothèque en appliquant le chiffrement et les restrictions lors du téléchargement des fichiers. Cette ancienne technologie de protection est conçue pour empêcher les utilisateurs non autorisés d’ouvrir le fichier en dehors de SharePoint.

En comparaison, les étiquettes de sensibilité fournissent les paramètres de protection des marquages visuels (en-têtes, pieds de page, filigranes) en plus du chiffrement. Les paramètres de chiffrement prennent en charge la gamme complète des [droits d’utilisation](/azure/information-protection/configure-usage-rights) pour restreindre ce que les utilisateurs peuvent faire avec le contenu, et les mêmes étiquettes de confidentialité sont prises en charge pour [de nombreux scénarios](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). L’utilisation de la même méthode de protection avec des paramètres cohérents entre les charges de travail et les applications entraîne une stratégie de protection cohérente.

Toutefois, vous pouvez utiliser les deux solutions de protection ensemble et le comportement est le suivant :

- Si vous chargez un fichier avec une étiquette de confidentialité qui applique le chiffrement, SharePoint ne peut pas traiter le contenu de ces fichiers afin que la co-création, eDiscovery, DLP et la recherche ne soient pas prises en charge pour ces fichiers.

- Si vous étiquetez un fichier à l’aide de Office sur le Web, tous les paramètres de chiffrement de l’étiquette sont appliqués. Pour ces fichiers, la co-création, eDiscovery, DLP et la recherche sont prises en charge.

- Si vous téléchargez un fichier étiqueté à l’aide de Office sur le Web, l’étiquette est conservée et tous les paramètres de chiffrement de l’étiquette sont appliqués plutôt que les paramètres de restriction IRM.

- Si vous téléchargez un fichier Office ou PDF qui n’est pas chiffré avec une étiquette de confidentialité, les paramètres IRM sont appliqués.

- Si vous avez activé l’un des paramètres de bibliothèque IRM supplémentaires, notamment empêcher les utilisateurs de charger des documents qui ne prennent pas en charge la gestion des droits relatifs à l’information ( IRM), ces paramètres sont appliqués.

Avec ce comportement, vous pouvez être assuré que tous les fichiers Office et PDF sont protégés contre tout accès non autorisé s’ils sont téléchargés, même s’ils ne sont pas étiquetés. Toutefois, les fichiers étiquetés qui sont chargés ne bénéficieront pas des nouvelles fonctionnalités.

## <a name="search-for-documents-by-sensitivity-label"></a>Rechercher des documents par étiquette de confidentialité

Utilisez la propriété managée **InformationProtectionLabelId** pour rechercher tous les documents dans SharePoint ou OneDrive qui ont une étiquette de confidentialité spécifique. Utilisez la syntaxe suivante : `InformationProtectionLabelId:<GUID>`

Par exemple, pour rechercher tous les documents qui ont été étiquetés comme « Confidentiel » et que cette étiquette a un GUID « 8faca7b8-8d20-48a3-8ea2-0f96310a848e », dans la zone de recherche, tapez :

```
InformationProtectionLabelId:8faca7b8-8d20-48a3-8ea2-0f96310a848e
```

La recherche ne trouve pas de documents étiquetés dans un fichier compressé, tel qu’un fichier .zip.

Pour obtenir les GUID de vos étiquettes de confidentialité, utilisez l’applet [de commande Get-Label](/powershell/module/exchange/get-label) :

1. Tout d’abord, [connectez-vous à Office 365 Security & Compliance PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    Par exemple, dans une session PowerShell exécutée en tant qu’administrateur, connectez-vous à l’aide d’un compte d’administrateur général.

2. Exécutez ensuite la commande suivante :

    ```powershell
    Get-Label |ft Name, Guid
    ```

Pour plus d’informations sur l’utilisation des propriétés gérées, consultez [Gérer le schéma de recherche dans SharePoint](/sharepoint/manage-search-schema).

## <a name="remove-encryption-for-a-labeled-document"></a>Supprimer le chiffrement d’un document étiqueté

Il peut y avoir de rares occasions où un administrateur SharePoint doit supprimer le chiffrement d’un document stocké dans SharePoint. Tout utilisateur disposant du [droit d’utilisation Rights Management](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) d’exporter ou de contrôle total qui lui est attribué pour ce document peut supprimer le chiffrement appliqué par le service Azure Rights Management d’Azure Information Protection. Par exemple, les utilisateurs disposant de l’un de ces droits d’utilisation peuvent remplacer une étiquette qui applique le chiffrement par une étiquette sans chiffrement. Un [super utilisateur](/azure/information-protection/configure-super-users) peut également télécharger le fichier et enregistrer une copie locale sans chiffrement.

En guise d’alternative, un administrateur général ou un [administrateur SharePoint](/sharepoint/sharepoint-admin-role) peut exécuter l’applet de commande [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) , qui supprime à la fois l’étiquette de confidentialité et le chiffrement. Cette applet de commande s’exécute même si l’administrateur ne dispose pas des autorisations d’accès au site ou au fichier, ou si le service Azure Rights Management n’est pas disponible.

Par exemple :

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

Conditions préalables :

- SharePoint Online Management Shell version 16.0.20616.12000 ou ultérieure.

- Le chiffrement a été appliqué par une étiquette de confidentialité avec des paramètres de chiffrement définis par l’administrateur (les [autorisations Affectez maintenant les paramètres](encryption-sensitivity-labels.md#assign-permissions-now) d’étiquette). [Le chiffrement à double clé](encryption-sensitivity-labels.md#double-key-encryption) n’est pas pris en charge pour cette applet de commande.

Le texte de justification est ajouté à [l’événement d’audit](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) de **suppression de l’étiquette de confidentialité du fichier**, et l’action de déchiffrement est également enregistrée dans la [journalisation de l’utilisation de la protection pour Azure Information Protection](/azure/information-protection/log-analyze-usage).

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>Comment désactiver les étiquettes de confidentialité pour SharePoint et OneDrive (désactivation)

Si vous désactivez ces nouvelles fonctionnalités, les fichiers que vous avez chargés après avoir activé les étiquettes de confidentialité pour SharePoint et OneDrive continuent d’être protégés par l’étiquette, car les paramètres d’étiquette continuent d’être appliqués. Lorsque vous appliquez des étiquettes de confidentialité à de nouveaux fichiers après avoir désactivé ces nouvelles fonctionnalités, la recherche en texte intégral, la découverte électronique et la co-création ne fonctionnent plus.

Pour désactiver ces nouvelles fonctionnalités, vous devez utiliser PowerShell. À l’aide de SharePoint Online Management Shell et de l’applet de commande [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) , spécifiez le même paramètre *EnableAIPIntegration* que celui décrit dans la section [Utiliser PowerShell pour activer la prise en charge des étiquettes de confidentialité](#use-powershell-to-enable-support-for-sensitivity-labels) . Mais cette fois, définissez la valeur du paramètre sur false et appuyez sur **Y** pour confirmer :

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

Si vous avez Microsoft 365 Multi-Geo, vous devez exécuter cette commande pour chacun de vos emplacements géographiques.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive, envisagez d’étiqueter automatiquement ces fichiers à l’aide de stratégies d’étiquetage automatique. Pour plus d'informations, voir [Appliquer automatiquement une étiquette de sensibilité au contenu](apply-sensitivity-label-automatically.md).

Vous avez besoin de partager vos documents étiquetés et chiffrés avec des personnes extérieures à votre organisation ?  Consultez [Partage de documents chiffrés avec des utilisateurs externes dans](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
