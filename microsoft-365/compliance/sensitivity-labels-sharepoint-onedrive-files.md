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
description: Les administrateurs peuvent activer la prise en charge des étiquettes de sensibilité pour Word, Excel et PowerPoint fichiers SharePoint et OneDrive.
ms.openlocfilehash: c3d4320937b441510424454197c4eb4ffa46d9fe
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52245635"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Activez les étiquettes de niveau de Office pour les fichiers SharePoint et [](sensitivity-labels.md) OneDrive afin que les utilisateurs peuvent appliquer vos étiquettes de niveau de Office sur le Web. Lorsque cette fonctionnalité est activée,  les utilisateurs voient le bouton Sensibilité sur le ruban afin de pouvoir appliquer des étiquettes, et voient tout nom d’étiquette appliqué dans la barre d’état.

L’activation de cette fonctionnalité permet également SharePoint et OneDrive de traiter le contenu des fichiers qui ont été chiffrés à l’aide d’une étiquette de niveau de sensibilité. L’étiquette peut être appliquée dans Office sur le Web ou dans Office applications de bureau et téléchargée ou enregistrée dans SharePoint et OneDrive. Tant que vous n’avez pas activé cette fonctionnalité, ces services ne peuvent pas traiter les fichiers chiffrés, ce qui signifie que la co-création, la découverte électronique, la protection contre la perte de données, la recherche et d’autres fonctionnalités collaboratives ne fonctionneront pas pour ces fichiers.

Après avoir activé les étiquettes de niveau de sensibilité pour les fichiers Office dans SharePoint et OneDrive, pour les fichiers nouveaux et modifiés [](double-key-encryption.md)qui ont une étiquette de niveau de sensibilité qui applique le chiffrement avec une clé informatique (et n’utilise pas le chiffrement à double clé) :

- Pour les fichiers Word, Excel et PowerPoint, SharePoint et OneDrive reconnaissent l’étiquette et peuvent désormais traiter le contenu du fichier chiffré.

- Lorsque les utilisateurs téléchargent ou accèdent à ces fichiers à partir de SharePoint ou OneDrive, l’étiquette de niveau de sensibilité et les paramètres de chiffrement de l’étiquette sont appliqués et restent avec le fichier, où qu’il soit stocké. Veillez à fournir des conseils aux utilisateurs pour utiliser uniquement des étiquettes pour protéger les documents. Pour plus d’informations, consultez les options de gestion des droits de l’information [(IRM) et les étiquettes de sensibilité.](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels)

- Lorsque les utilisateurs téléchargent des fichiers étiquetés et chiffrés vers SharePoint ou OneDrive, ils doivent au moins avoir des droits d’affichage sur ces fichiers. Par exemple, ils peuvent ouvrir les fichiers en dehors SharePoint. S’ils n’ont pas ce droit d’utilisation minimum, le téléchargement réussit, mais le service ne reconnaît pas l’étiquette et ne peut pas traiter le contenu du fichier.

- Utilisez Office sur le Web (Word, Excel, PowerPoint) pour ouvrir et modifier Office fichiers qui ont des étiquettes de niveau de sensibilité qui appliquent le chiffrement. Les autorisations affectées au chiffrement sont appliquées. Vous pouvez également utiliser [l’étiquetage automatique](apply-sensitivity-label-automatically.md) pour ces documents.

- Les utilisateurs externes peuvent accéder aux documents étiquetés avec chiffrement à l’aide de comptes invités. Pour plus d’informations, voir [Prise en charge des utilisateurs externes et du contenu étiqueté.](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content) 

- Office 365 eDiscovery prend en charge la recherche en texte intégral pour ces fichiers et les stratégies de protection contre la perte de données (DLP) le contenu de ces fichiers.

> [!NOTE]
> Si le chiffrement a été appliqué avec une clé sur site (une topologie de gestion des clés souvent appelée « conserver votre propre clé » ou HYOK) ou à l’aide du chiffrement à double [clé,](double-key-encryption.md)le comportement du service pour le traitement du contenu du fichier ne change pas. Ainsi, pour ces fichiers, la co-auteur, eDiscovery, la protection contre la perte de données, la recherche et d’autres fonctionnalités collaboratives ne fonctionnent pas.
>
> Le comportement SharePoint et OneDrive ne change pas non plus pour les fichiers existants à ces emplacements qui sont étiquetés avec le chiffrement à l’aide d’une clé Azure unique. Pour que ces fichiers bénéficient des nouvelles fonctionnalités une fois que vous avez activé les étiquettes de niveau de sensibilité pour les fichiers Office dans SharePoint et OneDrive, les fichiers doivent être téléchargés et téléchargés à nouveau, ou modifiés.

Après avoir activé les étiquettes de niveau de sensibilité pour les fichiers Office dans SharePoint et OneDrive, trois nouveaux événements [d’audit](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) sont disponibles pour la surveillance des étiquettes de niveau de sensibilité appliquées aux documents dans SharePoint et OneDrive :
- **Étiquette de confidentialité appliquée au fichier**
- **Étiquette de confidentialité modifiée appliquée au fichier**
- **Suppression de l'étiquette de confidentialité sur le document**

Regardez la vidéo suivante (sans audio) pour voir les nouvelles fonctionnalités en action :

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

Vous avez toujours le choix de désactiver les étiquettes de niveau de Office pour les fichiers SharePoint et OneDrive[(désactivation)](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)à tout moment.

Si vous protégez actuellement des documents dans SharePoint à l’aide de la Gestion des droits relatifs à l’information (IRM) SharePoint, n’oubliez pas de consulter la section gestion des droits relatifs à l’information [(IRM)](#sharepoint-information-rights-management-irm-and-sensitivity-labels) SharePoint et étiquettes de sensibilité sur cette page. 

## <a name="requirements"></a>Configuration requise

Ces nouvelles fonctionnalités fonctionnent uniquement avec [les étiquettes de](sensitivity-labels.md) sensibilité. Si vous disposez actuellement d’étiquettes Azure Information Protection, migrez-les d’abord vers les étiquettes de niveau de sensibilité afin de pouvoir activer ces fonctionnalités pour les nouveaux fichiers que vous téléchargez. Pour voir les instructions, consultez [Migration des étiquettes Azure Information Protection vers des étiquettes de confidentialité unifiées](/azure/information-protection/configure-policy-migrate-labels).

Utilisez la version 19.002.0121.0008 ou ultérieure de l’application de synchronisation Windows OneDrive et la version 19.002.0107.0008 ou ultérieure sur Mac. Ces deux versions ont été publiées le 28 janvier 2019 et sont actuellement publiées sur tous les anneaux. Pour plus d’informations, voir les [OneDrive de publication.](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0) Après avoir activé les étiquettes de niveau de Office pour les fichiers SharePoint et OneDrive, les utilisateurs qui exécutent une version antérieure de l’application de synchronisation sont invités à la mettre à jour.

## <a name="limitations"></a>Limites

- Power Query et les add-ins personnalisés avec Excel sur le Web : si ces fichiers sont chiffrés avec une étiquette de sensibilité, SharePoint et OneDrive ne peuvent pas traiter les fichiers afin que les utilisateurs ne puissent pas les ouvrir dans Office sur le Web. Pour ces fichiers, appliquez une étiquette sans chiffrement afin qu’ils soient ouverts dans Office sur le Web ou demandez aux utilisateurs d’ouvrir les fichiers dans leurs applications de bureau.

- Si vous avez des difficultés à ouvrir des fichiers étiquetés et chiffrés dans Office sur le Web, essayez ce qui suit :
    1. Ouvrez le fichier dans l’Office de bureau.
    2. Supprimez l’étiquette qui applique le chiffrement.
    3. Enregistrez le fichier à l’emplacement d’origine (SharePoint ou OneDrive), puis fermez l’application de bureau.
    4. Ouvrez le fichier dans Office sur le Web et réappliquez l’étiquette d’origine qui applique le chiffrement.

- SharePoint et OneDrive n’appliquent pas automatiquement des étiquettes de niveau de sensibilité aux fichiers existants que vous avez déjà chiffrés à l’aide d’étiquettes Azure Information Protection. Au lieu de cela, pour que les fonctionnalités fonctionnent une fois que vous avez activé les étiquettes de niveau de Office pour les fichiers SharePoint et OneDrive, effectuer les tâches suivantes :
    
    1. Assurez-vous que vous avez migré les étiquettes [Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels) vers des étiquettes de sensibilité et que vous les avez publiées à partir du centre de conformité Microsoft 365 ou du Centre d’administration de l’étiquetage équivalent. [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
    2. Téléchargez les fichiers, puis téléchargez-les sur SharePoint.

- SharePoint et OneDrive ne peuvent pas traiter les fichiers chiffrés lorsque l’étiquette qui a appliqué le chiffrement possède l’une des [configurations suivantes pour le chiffrement](encryption-sensitivity-labels.md#configure-encryption-settings):
    - **Permettre aux utilisateurs d'attribuer des autorisations lorsqu’ils appliquent l’étiquette** et la case à cocher **Dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier des autorisations** est sélectionnée. Ce paramètre est parfois appelé « autorisations définies par l’utilisateur ».
    - **L’expiration de l'accès des utilisateurs au contenu** est définie sur une valeur autre que **Jamais**.
    - **Chiffrement à double clé** est sélectionnée.
    
    Pour les étiquettes avec l’une de ces configurations de chiffrement, les étiquettes ne sont pas affichées pour les utilisateurs Office sur le Web. En outre, les nouvelles fonctionnalités ne peuvent pas être utilisées avec les documents étiquetés qui ont déjà ces paramètres de chiffrement. Par exemple, ces documents ne seront pas renvoyés dans les résultats de la recherche, même s’ils sont mis à jour.

- Les utilisateurs peuvent avoir des retards dans la possibilité d’ouvrir des documents chiffrés dans le scénario Enregistrer sous : à l’aide d’une version de bureau de Office, un utilisateur choisit Enregistrer sous pour un document dont l’étiquette de niveau de sensibilité applique le chiffrement. L’utilisateur sélectionne SharePoint ou OneDrive l’emplacement, puis tente immédiatement d’ouvrir ce document dans Office sur le Web. Si le service continue de traiter le chiffrement, l’utilisateur voit un message qui indique que le document doit être ouvert dans son application de bureau. S’ils essaient à nouveau dans quelques minutes, le document s’ouvre Office sur le Web. 

- Pour les documents chiffrés, l’impression n’est pas prise en charge.

- Pour un document chiffré qui accorde des autorisations de modification à un utilisateur, la copie ne peut pas être bloquée dans les versions web Office applications.

- Par défaut, les Office de bureau et les applications mobiles ne permettent pas la co-auteur pour les fichiers étiquetés avec chiffrement. Ces applications continuent d’ouvrir des fichiers étiquetés et chiffrés en mode édition exclusif.
    
    > [!NOTE]
    > La co-auteur est désormais prise en charge en prévisualisation. Pour plus d’informations, voir [Activer la co-auteur pour les fichiers chiffrés avec des étiquettes de sensibilité.](sensitivity-labels-coauthoring.md)

- Si un administrateur modifie les paramètres d’une étiquette publiée qui est déjà appliquée aux fichiers téléchargés sur le client de synchronisation des utilisateurs, il se peut que les utilisateurs ne soient pas en mesure d’enregistrer les modifications qu’ils ont apportées au fichier dans leur dossier OneDrive Sync. Ce scénario s’applique aux fichiers étiquetés avec le chiffrement, ainsi qu’à la modification de l’étiquette à partir d’une étiquette qui n’a pas appliqué le chiffrement à une étiquette qui applique le chiffrement. Les utilisateurs [voient un cercle](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3)rouge avec une erreur d’icône croisée blanche et sont invités à enregistrer les nouvelles modifications en tant que copie distincte. Au lieu de cela, ils peuvent fermer et rouvrir le fichier ou utiliser Office sur le Web.

- Si un document étiqueté est téléchargé vers SharePoint ou OneDrive et que l’étiquette a appliqué le chiffrement à l’aide d’un compte à partir d’un nom principal de service, le document ne peut pas être ouvert dans Office sur le Web. Les exemples de scénarios incluent Microsoft Cloud App Security et un fichier envoyé Teams par courrier électronique.

- Les utilisateurs peuvent faire face à des problèmes d’économie après avoir été mis hors connexion ou en mode veille lorsque, au lieu d’utiliser Office sur le Web, ils utilisent le bureau et les applications mobiles pour Word, Excel ou PowerPoint. Pour ces utilisateurs, lorsqu’ils reprennent leur session application Office et essaient d’enregistrer les modifications, ils voient un message d’échec de téléchargement avec une option pour enregistrer une copie au lieu d’enregistrer le fichier d’origine. 

- Les documents chiffrés des manières suivantes ne peuvent pas être ouverts Office sur le Web :
    - Chiffrement qui utilise une clé sur site ( « Conserver votre propre clé » ou HYOK)
    - Chiffrement appliqué à l’aide du [chiffrement à double clé](double-key-encryption.md)
    - Chiffrement appliqué indépendamment d’une étiquette, par exemple, en appliquant directement un modèle de protection Rights Management.

- Les étiquettes configurées pour [d’autres langues ne](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-center-powershell) sont pas pris en charge et affichent uniquement la langue d’origine.

- Les captures d’écran ne peuvent pas être empêchées pour les documents chiffrés. Pour plus d’informations, voir [La Gestion des droits peut-elle empêcher les captures d’écran ?](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- Si vous supprimez une étiquette qui a été appliquée à un document dans SharePoint ou OneDrive, plutôt que de supprimer l’étiquette de la stratégie d’étiquette applicable, le document téléchargé ne sera ni étiqueté ni chiffré. En comparaison, si le document étiqueté est stocké en dehors SharePoint ou OneDrive, le document reste chiffré si l’étiquette est supprimée. Notez que même si vous pouvez supprimer des étiquettes pendant une phase de test, il est très rare de supprimer une étiquette dans un environnement de production.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>Comment activer les étiquettes de niveau de SharePoint et OneDrive (opt-in)

Vous pouvez activer les nouvelles fonctionnalités à l’aide du centre de conformité Microsoft 365 ou à l’aide de PowerShell. Comme avec toutes les modifications de configuration au niveau du client pour SharePoint et OneDrive, la modification prend environ 15 minutes pour prendre effet.

### <a name="use-the-compliance-center-to-enable-support-for-sensitivity-labels"></a>Utiliser le centre de conformité pour activer la prise en charge des étiquettes de sensibilité

Cette option est le moyen le plus simple d’activer les étiquettes de sensibilité pour SharePoint et OneDrive, mais vous devez vous connectez en tant qu’administrateur général pour votre client.

1. Connectez-vous au [Centre Microsoft 365 conformité](https://compliance.microsoft.com/) en tant qu’administrateur général et accédez à **Solutions**  >  **Information Protection**
    
    Si vous ne voyez pas immédiatement cette option, sélectionnez tout d’abord **Tout afficher**. 

2. Si vous voyez un message pour activer la possibilité de traiter le contenu dans Office fichiers en ligne, **sélectionnez** Activer maintenant :
    
    ![Activer maintenant le bouton pour activer les étiquettes de niveau de Office Online](../media/sensitivity-labels-turn-on-banner.png)
    
    La commande s’exécute immédiatement et lorsque la page est actualisée, vous ne voyez plus le message ou le bouton.

> [!NOTE]
> Si vous avez Microsoft 365 multigéogé, vous devez utiliser PowerShell pour activer ces fonctionnalités pour tous vos emplacements géographiques. Pour plus d’informations, voir la section suivante.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>Utiliser PowerShell pour activer la prise en charge des étiquettes de sensibilité

Comme alternative à l’utilisation du centre de conformité, vous pouvez activer la prise en charge des étiquettes de sensibilité à l’aide de la cmdlet [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) de SharePoint Online PowerShell. 

Si vous avez Microsoft 365 multigéogé, vous devez utiliser PowerShell pour activer cette prise en charge pour tous vos emplacements géographiques.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>Préparer l’SharePoint Online Management Shell

Avant d’exécuter la commande PowerShell pour activer les étiquettes de sensibilité pour les fichiers Office dans SharePoint et OneDrive, assurez-vous que vous exécutez SharePoint Online Management Shell version 16.0.19418.12000 ou ultérieure. Si vous avez déjà la dernière version, vous pouvez passer à la [procédure](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) suivante pour exécuter la commande PowerShell.

1. Si vous avez installé une version antérieure de SharePoint Online Management Shell à partir de la Galerie PowerShell, vous pouvez mettre à jour le module en exécutant l’applet de commande suivante.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. Par ailleurs, si vous avez installé une version précédente de SharePoint Online Management Shell à  partir du Centre de téléchargement Microsoft, vous pouvez également ajouter ou supprimer des programmes et désinstaller SharePoint Online Management Shell.

3. Dans un navigateur web, accédez à la page du Centre de téléchargement et [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. Sélectionnez votre langue, puis cliquez sur **Télécharger**.

5. Choisissez entre le fichier x64 et x86 .msi. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. Si vous ne le savez pas, quelle version du système [d’Windows’exploitation est-ce que j’exécute ?](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. Après avoir téléchargé le fichier, exécutez-le et suivez les étapes de l’Assistant Installation.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>Exécuter la commande PowerShell pour activer la prise en charge des étiquettes de sensibilité

Pour activer les nouvelles fonctionnalités, utilisez la cmdlet [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) avec le *paramètre EnableAIPIntegration* :

1. À l’aide d’un compte professionnel ou scolaire qui dispose de privilèges d’administrateur général ou SharePoint administrateur général dans Microsoft 365, connectez-vous SharePoint. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).
    
    Remarque : si vous avez Microsoft 365 Multi-Géo, utilisez le paramètre -Url avec [Connecter-SPOService](/powershell/module/sharepoint-online/connect-sposervice)et spécifiez l’URL du site centre d’administration SharePoint Online pour l’un de vos emplacements géographiques.

2. Exécutez la commande suivante et appuyez **sur Y** pour confirmer :

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. Pour Microsoft 365 multigéogé : répétez les étapes 1 et 2 pour chacun de vos emplacements géographiques restants.

## <a name="publishing-and-changing-sensitivity-labels"></a>Publication et modification des étiquettes de sensibilité

Lorsque vous utilisez des étiquettes de sensibilité avec SharePoint et OneDrive, n’oubliez pas que vous devez autoriser le temps de réplication lorsque vous publiez de nouvelles étiquettes de sensibilité ou mettez à jour les étiquettes de sensibilité existantes. Ceci est particulièrement important pour les nouvelles étiquettes qui appliquent le chiffrement.

Par exemple : vous créez et publiez une nouvelle étiquette de sensibilité qui applique le chiffrement et qui apparaît très rapidement dans l’application de bureau d’un utilisateur. L’utilisateur applique cette étiquette à un document, puis la télécharge vers SharePoint ou OneDrive. Si la réplication d’étiquettes n’est pas terminée pour le service, les nouvelles fonctionnalités ne seront pas appliquées à ce document lors du chargement. Par conséquent, le document ne sera pas renvoyé dans la recherche ou pour eDiscovery et le document ne peut pas être ouvert dans Office sur le Web.  

Les modifications suivantes sont répliquées dans un délai d’une heure : les étiquettes de confidentialité nouvelles et supprimées, ainsi que les paramètres de stratégie d’étiquette de confidentialité qui incluent les étiquettes qui figurent dans la stratégie.

Les modifications suivantes sont répliquées dans les 24 heures : modifications apportées aux paramètres des étiquettes de sensibilité pour les étiquettes existantes.

Étant donné que le délai de réplication n’est qu’une heure pour les nouvelles étiquettes de sensibilité, il est peu probable que vous vous pliiez dans le scénario de l’exemple. Toutefois, par mesure de protection, nous vous recommandons de publier d’abord de nouvelles étiquettes pour quelques utilisateurs test, d’attendre une heure, puis de vérifier le comportement des étiquettes sur SharePoint et OneDrive. Pour la dernière étape, rendez l’étiquette accessible à davantage d’utilisateurs en ajoutant davantage d’utilisateurs à la stratégie d’étiquette existante ou ajoutez l’étiquette à une stratégie d’étiquette existante pour vos utilisateurs standard. Au moment où vos utilisateurs standard voient l’étiquette, elle a déjà été synchronisée avec SharePoint et OneDrive.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint Gestion des droits de l’information (IRM) et étiquettes de sensibilité

SharePoint Gestion des droits numériques [(IRM)](set-up-irm-in-sp-admin-center.md) est une technologie plus ancienne qui permet de protéger les fichiers au niveau de la liste et de la bibliothèque en appliquant le chiffrement et les restrictions lors du téléchargement des fichiers. Cette ancienne technologie de protection est conçue pour empêcher les utilisateurs non autorisés d’ouvrir le fichier en dehors de l’SharePoint.

En comparaison, les étiquettes de niveau de sensibilité fournissent les paramètres de protection des marquages visuels (en-têtes, pieds de page, filigranes) en plus du chiffrement. Les paramètres de chiffrement [](/azure/information-protection/configure-usage-rights) prendre en charge l’ensemble des droits d’utilisation pour restreindre ce que les utilisateurs peuvent faire avec le contenu, et les mêmes étiquettes de niveau de sensibilité sont pris en charge dans de nombreux [scénarios.](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels) L’utilisation de la même méthode de protection avec des paramètres cohérents entre les charges de travail et les applications entraîne une stratégie de protection cohérente.

Toutefois, vous pouvez utiliser les deux solutions de protection ensemble et le comportement est le suivant : 

- Si vous chargez un fichier avec une étiquette de niveau de sensibilité qui applique le chiffrement, SharePoint ne peut pas traiter le contenu de ces fichiers de sorte que la co-création, eDiscovery, DLP et la recherche ne sont pas pris en charge pour ces fichiers.

- Si vous étiquetez un fichier à l Office sur le Web, tous les paramètres de chiffrement de l’étiquette sont appliqués. Pour ces fichiers, la co-auteur, eDiscovery, DLP et la recherche sont pris en charge.

- Si vous téléchargez un fichier étiqueté à l’aide de Office sur le Web, l’étiquette est conservée et tous les paramètres de chiffrement de l’étiquette sont appliqués au lieu des paramètres de restriction IRM.

- Si vous téléchargez un fichier Office ou PDF qui n’est pas chiffré avec une étiquette de niveau de sensibilité, les paramètres IRM sont appliqués.

- Si vous avez activé l’un des paramètres de bibliothèque IRM supplémentaires, notamment empêcher les utilisateurs de télécharger des documents qui ne la prisent pas en charge, ces paramètres sont appliqués.

Avec ce comportement, vous pouvez être certain que tous les fichiers Office et PDF sont protégés contre tout accès non autorisé s’ils sont téléchargés, même s’ils ne sont pas étiquetés. Toutefois, les fichiers étiquetés téléchargés ne bénéficieront pas des nouvelles fonctionnalités.


## <a name="search-for-documents-by-sensitivity-label"></a>Rechercher des documents par étiquette de niveau de sensibilité

Utilisez la propriété gérée **InformationProtectionLabelId** pour rechercher tous les documents dans SharePoint ou OneDrive qui ont une étiquette de sensibilité spécifique. Utilisez la syntaxe suivante : `InformationProtectionLabelId:<GUID>`

Par exemple, pour rechercher tous les documents qui ont été étiquetés comme « Confidentiel » et que cette étiquette a un GUID de « 8faca7b8-8d20-48a3-8ea2-0f96310a848e », dans la zone de recherche, tapez :

`InformationProtectionLabelId: 8faca7b8-8d20-48a3-8ea2-0f96310a848e`    

Pour obtenir les GUID de vos étiquettes de sensibilité, utilisez la cmdlet [Get-Label](/powershell/module/exchange/get-label) :    

1. Tout d’abord,[connectez-vous au Centre de sécurité et conformité Office 365 PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell). 
   
    Par exemple, dans une session PowerShell exécutée en tant qu’administrateur, connectez-vous à l’aide d’un compte d’administrateur général.    

2. Exécutez ensuite la commande suivante :  

    ```powershell   
    Get-Label |ft Name, Guid    
    ``` 

Pour plus d’informations sur l’utilisation des propriétés gérées, voir Gérer le schéma [de recherche dans SharePoint](/sharepoint/manage-search-schema).

## <a name="remove-encryption-for-a-labeled-document"></a>Supprimer le chiffrement d’un document étiqueté

Il peut y avoir de rares cas où un administrateur SharePoint doit supprimer le chiffrement d’un document stocké dans SharePoint. Tout utilisateur qui dispose du droit d’utilisation Rights [Management](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) de l’exportation ou du contrôle total qui lui est affecté pour ce document peut supprimer le chiffrement qui a été appliqué par le service Azure Rights Management d’Azure Information Protection. Par exemple, les utilisateurs avec l’un de ces droits d’utilisation peuvent remplacer une étiquette qui applique le chiffrement par une étiquette sans chiffrement. Sinon, un [super utilisateur](/azure/information-protection/configure-super-users) peut télécharger le fichier et enregistrer une copie locale sans chiffrement.

En alternative, un administrateur général ou un administrateur [SharePoint](/sharepoint/sharepoint-admin-role) peut exécuter la cmdlet [Unlock-SPOSensitivityLabelEncryptedFile,](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) qui supprime l’étiquette de sensibilité et le chiffrement. Cette cmdlet s’exécute même si l’administrateur n’a pas d’autorisations d’accès au site ou au fichier, ou si le service Azure Rights Management n’est pas disponible. 

Par exemple :

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

Conditions requises :

- SharePoint Online Management Shell version 16.0.20616.12000 ou ultérieure.

- Le chiffrement a été appliqué par une étiquette de niveau de sensibilité avec des paramètres de chiffrement définis par l’administrateur (les paramètres Attribuer [des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now) les étiquettes). [Le chiffrement à double](encryption-sensitivity-labels.md#double-key-encryption) clé n’est pas pris en charge pour cette cmdlet.

Le texte de justification est ajouté à l’événement [d’audit](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) de l’étiquette de sensibilité Supprimée du fichier **et** l’action de déchiffrement est également enregistrée dans la journalisation de l’utilisation de la protection pour [Azure Information Protection](/azure/information-protection/log-analyze-usage).

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>Comment désactiver les étiquettes de niveau de SharePoint et OneDrive (désactivation)

Si vous désactivez ces nouvelles fonctionnalités, les fichiers que vous avez téléchargés après avoir activé les étiquettes de sensibilité pour SharePoint et OneDrive continuent d’être protégés par l’étiquette, car les paramètres d’étiquette continuent d’être appliqués. Lorsque vous appliquez des étiquettes de niveau de sensibilité aux nouveaux fichiers après avoir désactivé ces nouvelles fonctionnalités, la recherche en texte intégral, eDiscovery et la co-génération ne fonctionneront plus.

Pour désactiver ces nouvelles fonctionnalités, vous devez utiliser PowerShell. À l’aide de SharePoint Online Management Shell et de la cmdlet [Set-SPOTenant,](/powershell/module/sharepoint-online/set-spotenant) spécifiez le même paramètre *EnableAIPIntegration* que décrit dans la section Utiliser [PowerShell](#use-powershell-to-enable-support-for-sensitivity-labels) pour activer la prise en charge des étiquettes de sensibilité. Mais cette fois, définissez la valeur du paramètre sur false et appuyez **sur Y** pour confirmer :

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

Si vous avez Microsoft 365 multigéogé, vous devez exécuter cette commande pour chacun de vos emplacements géographiques.

## <a name="next-steps"></a>Prochaines étapes

Après avoir activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive, envisagez d’étiqueter automatiquement ces fichiers à l’aide de stratégies d’étiquetage automatique. Pour plus d’informations, voir Appliquer automatiquement une étiquette [de niveau de sensibilité au contenu.](apply-sensitivity-label-automatically.md)

Vous avez besoin de partager vos documents étiquetés et chiffrés avec des personnes extérieures à votre organisation ?  Consultez [Partage de documents chiffrés avec des utilisateurs externes dans](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).