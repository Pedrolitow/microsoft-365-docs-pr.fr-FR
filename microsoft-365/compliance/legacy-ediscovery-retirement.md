---
title: Suppression des outils eDiscovery hérités
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: In-Place eDiscovery et In-Place Hold (et les applets de commande PowerShell correspondantes) dans Exchange Online seront mises hors service au cours du premier semestre 2020. L’applet de commande Search-Mailbox et Microsoft Purview eDiscovery (Premium) v1.0 sont également mises hors service au cours de la même période.
ms.openlocfilehash: 630d72c75f318e6d4f9e68b01c61d5069958a0a1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636070"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Retrait des outils eDiscovery hérités

> [!IMPORTANT]
> Les fonctionnalités des outils eDiscovery hérités décrits dans cet article ont été supprimées du service Microsoft 365 ou sont toujours disponibles, mais ne sont plus prises en charge. Toutes les fonctionnalités toujours disponibles peuvent être supprimées sans préavis. Si vous utilisez toujours l’un de ces outils hérités, envisagez de migrer vers les outils eDiscovery dans le portail de conformité Microsoft Purview ou l’une des alternatives décrites dans cet article.

Au fil des ans, Microsoft a fourni des outils eDiscovery qui vous permettent de rechercher, d’afficher un aperçu et d’exporter du contenu de messagerie à partir de Exchange Online. Toutefois, ces outils n’offrent plus un moyen efficace de rechercher du contenu non Exchange dans d’autres services Microsoft 365, tels que SharePoint Online et Groupes Microsoft 365. Pour résoudre ce problème, Microsoft propose d’autres outils eDiscovery qui vous aident à rechercher un large éventail de contenu Microsoft 365. Et nous avons travaillé dur pour incorporer les fonctionnalités eDiscovery les plus actuelles et les plus puissantes dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a>. Cela permet aux organisations de répondre aux demandes de contenu légales, internes et autres concernant du contenu dans de nombreux services Microsoft 365, y compris Exchange Online.

À la suite de cette fonctionnalité eDiscovery nouvelle et améliorée dans le portail de conformité, nous retirons les fonctionnalités et fonctionnalités liées à eDiscovery suivantes liées à la recherche de contenu de messagerie dans Exchange Online et Microsoft 365 :

- [eDiscovery inaltérable](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) et [les conservations sur place](/exchange/security-and-compliance/create-or-remove-in-place-holds) dans le centre d’administration Exchange.

- Les Exchange Online applets de commande PowerShell qui prennent en charge In-Place eDiscovery et In-Place Holds (ces applets de commande sont collectivement identifiées en tant que cmdlets **-MailboxSearch*). Cela inclut les applets de commande suivantes :

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Les applets de commande [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) et [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) seront disponibles après la mise hors service des autres applets de commande ***-MailboxSearch*** afin que vous puissiez les utiliser pour faciliter votre transition vers d’autres outils eDiscovery et hold. Toutefois, après une certaine date (citée ci-dessous), Support Microsoft ne prend plus en charge ces deux applets de commande.

- [Applet de commande Search-Mailbox](/powershell/module/exchange/search-mailbox) dans Exchange Online PowerShell.

- Les opérations suivantes dans l’API Exchange Web Services :

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Microsoft Purview eDiscovery (Premium) v1.0](./overview-ediscovery-20.md), qui est la première version d’eDiscovery (Premium) accessible via un cas Microsoft Purview eDiscovery (Standard) dans le portail de conformité. La mise hors service d’eDiscovery (Premium) v1.0 n’affecte pas votre capacité à créer et gérer des cas eDiscovery (Standard).

> [!NOTE]
> La fonctionnalité eDiscovery mise hors service s’applique uniquement aux versions cloud de Microsoft 365 et Office 365. Les fonctionnalités eDiscovery dans les versions locales d’Exchange et sharePoint seront toujours prises en charge jusqu’à nouvel ordre.

Les sections suivantes de cet article fournissent des conseils sur chaque fonctionnalité en cours de mise hors service. Ces informations, notamment les chronologies et les autres outils que vous pouvez utiliser au lieu de l’outil mis hors service.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place les conservations eDiscovery et In-Place dans le Centre d’administration Exchange 

Conformément à l’annonce initiale du 1er juillet 2017, la fonctionnalité In-Place eDiscovery & Hold dans le Centre d’administration Exchange (CAE) est en cours de mise hors service. La page In-Place eDiscovery & Hold dans le CAE vous a permis de rechercher, de conserver et d’exporter du contenu à partir de Exchange Online. In-Place eDiscovery vous permet également de copier les résultats de recherche dans une boîte aux lettres de découverte afin que vous ou d’autres responsables eDiscovery puissiez examiner le contenu et le rendre disponible pour les demandes légales, réglementaires et publiques.

Étant donné que toutes ces fonctionnalités (à l’exception de la copie des résultats de recherche dans une boîte aux lettres de découverte) sont désormais disponibles dans les outils de recherche de contenu, eDiscovery et eDiscovery (Premium) dans le [portail de conformité](./microsoft-365-compliance-center.md) (avec des fonctionnalités, une fiabilité et une prise en charge améliorées pour un large éventail de services Microsoft 365), nous vous recommandons de commencer à utiliser ces outils dès que possible. Pour vous aider dans la transition vers ces autres outils eDiscovery, le tableau ci-dessous répertorie les outils que vous pouvez utiliser au lieu de In-Place eDiscovery et In-Place Hold.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- organisations Office 365 et Microsoft 365 Entreprise

- organisations Office 365 et Microsoft 365 Éducation

- Office 365 et les organisations Microsoft 365 Government ; cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline-for-retirement"></a>Chronologie de la mise hors service

- 1er juillet 2020 : Vous ne pourrez pas créer de recherches et de conservations, mais vous pouvez toujours exécuter, modifier et supprimer des recherches existantes à vos propres risques. Support Microsoft ne In-Place plus les & eDiscovery dans le CAE.

- 1er octobre 2020 : La fonctionnalité In-Place eDiscovery & Holds dans le CAE sera placée en mode lecture seule. Cela signifie que vous ne pourrez supprimer que les recherches et conservations existantes.

### <a name="alternative-tools"></a>Autres outils

Le tableau suivant décrit d’autres outils que vous pouvez utiliser pour remplacer les fonctionnalités existantes en cours de mise hors service.

<table>
<thead>
<tr class="header">
<th>Les fonctionnalités</th>
<th>Autre outil</th>
<th>Commentaires</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Rechercher, exporter et conserver à des fins légales</td>
<td>Cas eDiscovery (Standard) dans le portail de conformité </td>
<td><p>L’utilisation des fonctionnalités des cas eDiscovery (Standard) fournit la parité fonctionnelle pour In-Place eDiscovery et In-Place Holds. Les voici :</p>
<ul>
<li>
<p>La recherche s’adapte à des millions d’emplacements</p>
</li>
<li>
<p>Fiabilité plus élevée pour la recherche, l’exportation et la mise en attente du contenu</p>
</li>
<li>
<p>Recherche de contenu dans Exchange Online, SharePoint Online, OneDrive Entreprise, Skype Entreprise, Microsoft Teams, groupes Yammer, Groupes Microsoft 365 et autres contenus stockés dans Office 365 applications</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Conservation à des fins de rétention</td>
<td>Stratégies de rétention dans le portail de conformité</td>
<td><p>Vous pouvez utiliser des stratégies de rétention pour conserver le contenu et, si vous le souhaitez, le supprimer après l’expiration de la période de rétention. Voici d’autres fonctionnalités :</p>
<ul>
<li>
<p>Application de stratégies à l’ensemble de votre organisation </p>
</li><li>
<p>Application de stratégies à des emplacements de contenu spécifiques tels que Exchange Online, SharePoint Online, OneDrive Entreprise, Skype Entreprise, Microsoft Teams et Office 365 Groups</p></li>
<li>
<p>Application de stratégies à des utilisateurs spécifiques</p></li></ul>
<p>Pour plus d’informations, consultez <a href="/microsoft-365/compliance/retention-policies"> En savoir plus sur les stratégies de rétention et les étiquettes de rétention</a>.</td>
</tr>
<tr class="odd">
<td>Copier les résultats de la recherche par e-mail dans une boîte aux lettres de découverte pour révision</td><td>Passer en revue les ensembles dans eDiscovery (Premium) v2.0</td>
<td><p>L’examen du contenu dans Microsoft 365 n’a jamais été aussi simple. Les ensembles de révision ont de nombreuses fonctionnalités pour réduire le temps et les données nécessaires à la révision, notamment :</p>
<ul>
<li><p>Effectuer des requêtes de recherche rapide et filtrer du contenu dans un ensemble de révisions</p></li>
<li><p>Analyser le contenu d’un ensemble de révisions ; cela inclut le thread de messagerie, la détection en quasi-double, l’analyse des thèmes et le codage prédictif</p></li>
<li><p>Étiqueter les documents d’un jeu à réviser</p></li>
<li><p>Suggestions de balisage pour aider à identifier le contenu des privilèges du client d’avocat</p></li></ul>
<p>Pour plus d’informations, consultez <a href="/microsoft-365/compliance/overview-ediscovery-20">Vue d’ensemble de la solution eDiscovery (Premium) dans Microsoft 365</a>.</p>
<p>
<p>Vous pouvez également exporter les résultats de la recherche vers des fichiers PST, puis utiliser le service d’importation Microsoft 365 pour importer les fichiers PST dans une boîte aux lettres de découverte. Pour obtenir des instructions pas à pas, consultez <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">Utiliser le chargement réseau pour importer des fichiers PST dans Office 365</a>.
</tr>
<tr class=even>
  <td>Copier des messages d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour donner à une personne l’accès à l’e-mail d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez accorder à une autre personne l’accès à l’e-mail de l’ancien employé), nous vous recommandons d’attribuer à cette personne les autorisations nécessaires pour accéder à la boîte aux lettres de l’ancien employé. Par conséquent, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres d’utilisateur ou une boîte aux lettres partagée, affectez simplement à un utilisateur les autorisations nécessaires pour accéder à la boîte aux lettres source.</td>
  
  </tr>
<tr class="odd">
<td>Restaurer des éléments à partir du dossier Éléments récupérables</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>Vous pouvez restaurer des éléments supprimés définitivement (également appelés éléments <i>supprimés de manière réversible</i> ) dans les boîtes aux lettres, tant que la période de rétention des éléments supprimés pour un élément n’a pas expiré. Pour plus d’informations, consultez le <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">dossier Éléments récupérables dans Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>FAQ sur In-Place eDiscovery et In-Place Holds

**J’utilise la fonctionnalité copier les résultats de la recherche de In-Place eDiscovery & détient dans le CAE pour copier les résultats de la recherche dans une boîte aux lettres de découverte pour examen par les avocats. Quelles options ai-je maintenant ?**

Il existe deux façons de répliquer cette fonctionnalité aujourd’hui. La première consiste à utiliser des [ensembles de révision dans eDiscovery (Premium) v2.0](./view-documents-in-review-set.md). Les ensembles de révision ont de nombreuses fonctionnalités semblables à celles que vous voyez dans un outil de révision traditionnel, comme la recherche rapide de documents, l’étiquetage, le thread de messagerie, le regroupement en quasi-double, l’analyse des thèmes et le codage prédictif. Si vous souhaitez toujours utiliser des boîtes aux lettres de découverte à des fins de révision, la deuxième option consiste à exporter les résultats de recherche dans des fichiers PST, puis à importer les fichiers PST dans une boîte aux lettres de découverte à l’aide de la [fonctionnalité d’importation PST](use-network-upload-to-import-pst-files.md) dans le Centre de conformité Microsoft.

**Comment faire contrôler les emplacements de contenu (tels que les boîtes aux lettres ou les sites) qu’un gestionnaire eDiscovery peut rechercher à l’aide des nouveaux outils ?**

Le portail de conformité utilise également des [limites de conformité](set-up-compliance-boundaries.md) pour contrôler les emplacements de contenu qu’un gestionnaire eDiscovery peut rechercher. Les limites de conformité sont utiles pour les entités gouvernementales qui doivent rester dans les limites des organismes ou les sociétés multinationales requises pour respecter les administrateurs géographiques.

**Comment puis-je déplacer mes recherches et conservations actuelles vers le portail de conformité Microsoft Purview ?**

Il est possible de migrer In-Place recherches et conservations eDiscovery à partir de l’EAC à l’aide de PowerShell. Pour obtenir des instructions, consultez [Migrer des recherches et des conservations à partir de la CAE vers le portail de conformité](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-Applets de commande MailboxSearch

Conformément à l’avis d’origine annoncé le 1er juillet 2017 dans le Centre d’administration Exchange, la fonctionnalité In-Place eDiscovery & Hold et les applets de commande **-MailboxSearch correspondantes\*** sont en cours de mise hors service. Ces applets de commande permettent aux utilisateurs de rechercher, de conserver et d’exporter du contenu de boîte aux lettres pour les demandes légales, réglementaires et publiques.

Étant donné que ces fonctionnalités sont désormais disponibles dans le [<span class="underline">portail de conformité</span>](./microsoft-365-compliance-center.md) et Office 365 Security & Compliance PowerShell avec des performances et une extensibilité améliorées, vous devez utiliser ces applets de commande améliorées. Ces applets de commande incluent [<span class="underline">\*-ComplianceCase</span>](/powershell/module/exchange/get-compliancecase), [<span class="underline">\*-ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline">\*-CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline">\*-CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule) et [<span class="underline">\*-ComplianceSearchAction</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- organisations Office 365 et Microsoft 365 Entreprise

- organisations Office 365 et Microsoft 365 Éducation

- Office 365 et les organisations Microsoft 365 Government ; cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : Vous ne pourrez pas utiliser **New-MailboxSearch** pour créer des recherches In-Place eDiscovery et des conservations In-Place, mais vous pouvez toujours utiliser des applets de commande pour exécuter, modifier et supprimer des recherches et des conservations existantes à vos propres risques. Support Microsoft ne fournira plus d’aide pour ces types de recherches et de conservations.

- 1er octobre 2020 : Comme indiqué précédemment, la fonctionnalité In-Place eDiscovery & Holds dans le CAE sera placée en mode lecture seule. Cela signifie également que vous ne pourrez pas utiliser les applets de commande **New-MailboxSearch**, **Start-MailboxSearch** ou **Set-MailboxSearch** . Vous ne pourrez obtenir et supprimer que des recherches et des conservations existantes.

### <a name="alternative-tools"></a>Autres outils

Le tableau suivant décrit d’autres outils que vous pouvez utiliser pour remplacer les fonctionnalités existantes en cours de mise hors service.

<table>
<thead>
<tr class="header">
<th>Les fonctionnalités</th>
<th>Autres outils</th>
<th>Commentaires</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Rechercher et exporter</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Les applets de commande ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et exporter du contenu. Vous pouvez créer une recherche et afficher l’estimation de recherche à l’aide des applets de commande <strong>New-</strong>, <strong>Get</strong> et <strong>Start-ComplianceSearch</strong> . Vous pouvez ensuite utiliser l’applet <strong>de commande New-ComplianceSearchAction</strong> pour exporter les résultats de la recherche. Vous devrez toujours utiliser l’outil eDiscovery (Standard) dans le portail de conformité pour télécharger ces résultats de recherche sur votre ordinateur local.</p>
<p>
<p><strong>Note:</strong> Si vous utilisez ces applets de commande pour créer des recherches qui ne sont pas associées à un cas eDiscovery (Standard), ces recherches se trouvent sur la page <strong>Recherche</strong> de contenu dans le portail de conformité.</p></td>
</tr>
<tr class="even">
<td>Conserver le contenu dans une boîte aux lettres</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Les conservations dans le portail de conformité doivent être associées à un ComplianceCase. Tout d’abord, créez le cas de conformité, puis créez une CaseHoldPolicy et une CaseHoldRule.</p>
<p><strong>Note:</strong> La création d’une CaseHoldPolicy sans caseholdRule de création rend la conservation inutilisable jusqu’à ce que CaseHoldRule soit créé et associé à CaseHoldPolicy. Pour plus d’informations, consultez la documentation de l’applet de commande.</p></td>
</tr>
<tr class="odd">
<td>Copier les résultats de la recherche dans une boîte aux lettres de découverte</td>
<td>Aucun</td>
<td>Il n’existe aucun remplacement direct de cette fonctionnalité, car elle ne fournit pas l’accès à tous les services Microsoft 365. Consultez la FAQ suivante ci-dessous pour obtenir d’autres solutions.</td>
</tr>
  <tr class=even>
  <td>Copier des messages d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour donner à une personne l’accès à l’e-mail d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez accorder à une autre personne l’accès à l’e-mail de l’ancien employé), nous vous recommandons d’attribuer à cette personne les autorisations nécessaires pour accéder à la boîte aux lettres de l’ancien employé. Par conséquent, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres d’utilisateur ou une boîte aux lettres partagée, affectez simplement à un utilisateur les autorisations nécessaires pour accéder à la boîte aux lettres source.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>FAQ sur les applets de commande ***-MailboxSearch**

**Nous utilisons la recherche de copie pour exporter des messages électroniques ou des messages instantanés à des fins d’autres enquêtes sur eDiscovery et juridiques. Quelles autres options avons-nous après la mise hors service de ces applets de commande ?**

Les [<span class="underline">API Microsoft Graph</span>](https://developer.microsoft.com/en-us/graph) fournissent un certain nombre de méthodes pour extraire des données à des fins d’analyse et autres qui sont beaucoup plus résilientes et scalables que l’utilisation **\*** des applets de commande -MailboxSearch.

**Comment migrer mes recherches et mes conservations vers le portail de conformité ?**

Il est possible de migrer In-Place recherches et conservations eDiscovery à partir du Centre d’administration Exchange à l’aide d’un script PowerShell. Pour plus d’informations, consultez [Migrer les recherches et conservations eDiscovery héritées vers le portail de conformité](migrate-legacy-eDiscovery-searches-and-holds.md).

**Une fois les applets de commande mises hors service, puis-je toujours supprimer ou récupérer des recherches ?**

Oui, bien que nous supprimions la possibilité de créer et de modifier des recherches, vous pourrez toujours utiliser **Get-MailboxSearch** et **Remove-MailboxSearch** jusqu’à nouvel ordre. Toutefois, l’utilisation de ces applets de commande sera à votre propre risque après les dates de retraite et Support Microsoft ne pourrez plus fournir d’aide.

## <a name="search-mailbox-cmdlet"></a>applet de commande Search-Mailbox

L’applet **de commande Search-Mailbox** dans Exchange Online PowerShell est mise hors service, comme annoncé à l’origine dans un avertissement dans la sortie de l’applet de commande à compter de 2018. L’applet **de commande Search-Mailbox** a été utilisée à l’origine pour rechercher dans la boîte aux lettres d’un utilisateur et vider le contenu malveillant. Nous vous recommandons de commencer à utiliser les applets de commande **New-ComplianceSearch** et **New-ComplianceSearchAction** dans Office 365 Security & Compliance PowerShell pour rechercher et vider le contenu. Pour une expérience de sécurité intégrée, les [<span class="underline">fonctionnalités de sécurité De Microsoft 365</span>](../security/index.yml) offrent une protection robuste contre les menaces pour les e-mails et de nombreux autres services Microsoft.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- organisations Office 365 et Microsoft 365 Entreprise

- organisations Office 365 et Microsoft 365 Éducation

- Office 365 et les organisations Microsoft 365 Government ; cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

-  1er juillet 2020 : L’applet de commande **Search-Mailbox** ne sera plus disponible et Support Microsoft ne fournira plus d’aide.

### <a name="alternative-tools"></a>Autres outils

Le tableau suivant décrit d’autres outils que vous pouvez utiliser pour remplacer les fonctionnalités existantes en cours de mise hors service.

<table>
<thead>
<tr class="header">
<th>Les fonctionnalités</th>
<th>Autres outils</th>
<th>Commentaires</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Rechercher dans une boîte aux lettres</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>Les applets de commande ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et exporter du contenu. Vous pouvez créer une recherche et afficher l’estimation de recherche à l’aide des applets de commande <strong>New-</strong>, <strong>Get</strong> et <strong>Start-ComplianceSearch</strong> . Vous pouvez ensuite utiliser la commande <strong>New-ComplianceSearchAction -Export</strong> pour exporter les résultats de la recherche. Vous devrez toujours utiliser l’outil eDiscovery (Standard) dans le portail de conformité pour télécharger ces résultats de recherche sur votre ordinateur local.</p></p>
</td>
</tr>
<tr class="even">
<td>Supprimer un e-mail en bloc d’une boîte aux lettres</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Configurer une stratégie d’archivage et de suppression de boîtes aux lettres</span></a></p>
<p></p></td>
<td><p>Les administrateurs peuvent créer une stratégie d’archivage et de suppression qui déplace automatiquement les éléments vers la boîte aux lettres d’archivage d’un utilisateur et supprime automatiquement les éléments de la boîte aux lettres.</p>
</td>
</tr>
<tr class="even">
<td>Copier les résultats de la recherche dans une boîte aux lettres de découverte</td>
<td> </td>
<td>Il n’existe aucun remplacement direct de cette fonctionnalité, car elle ne fournit pas l’accès à tous les services Microsoft 365. Consultez les questions fréquentes dans la section <strong>*-MailboxSearch cmdlets</strong> pour découvrir d’autres solutions. </td>
</tr>
<tr class=odd>
  <td>Copier des messages d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour donner à une personne l’accès à l’e-mail d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez accorder à une autre personne l’accès à l’e-mail de l’ancien employé), nous vous recommandons d’attribuer à cette personne les autorisations nécessaires pour accéder à la boîte aux lettres de l’ancien employé. Par conséquent, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres d’utilisateur ou une boîte aux lettres partagée, affectez simplement à un utilisateur l’autorisation d’accéder à la boîte aux lettres source.</td>
</tr>
<tr class=even>
  <td>Vider les messages d’une boîte aux lettres</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>Les applets de commande ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et à vider le contenu. Vous pouvez créer et exécuter une recherche avec les applets de commande <strong>New-ComplianceSearch</strong> et <strong>New-ComplianceSearch</strong> , puis vider le contenu à l’aide de la commande <strong>New-ComplianceSearchAction -Purge -PurgeType</strong> . Pour plus d’informations, consultez <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">Rechercher et supprimer des messages</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>Vider les messages d’une boîte aux lettres</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
<td>Pour vider les messages d’une boîte aux lettres, attribuez à un administrateur les autorisations nécessaires pour accéder à la boîte aux lettres de l’employé. Les messages peuvent être supprimés et recyclés en fonction des besoins en tirant parti des fonctionnalités intégrées de recherche et d’affichage dans Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Opérations de l’API Exchange Web Services

Ces opérations dans l’API services web Exchange sont utilisées par la fonctionnalité In-Place eDiscovery & Holds dans le centre d’administration Exchange et les applets de commande **-MailboxSearch correspondantes\*** dans Exchange Online PowerShell. Ils seront également mis hors service dans le cadre de la mise hors service des autres outils eDiscovery hérités.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- organisations Office 365 et Microsoft 365 Entreprise

- organisations Office 365 et Microsoft 365 Éducation

- Office 365 et les organisations Microsoft 365 Government ; cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : les opérations GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes et GetHoldOnMailboxes ne seront plus disponibles et Support Microsoft ne fourniront plus d’assistance.

## <a name="ediscovery-premium-v10"></a>eDiscovery (Premium) v1.0

eDiscovery (Premium) v1.0, qui est la version d’eDiscovery (Premium) disponible dans un cas eDiscovery (Standard) en cliquant sur **Basculer vers eDiscovery (Premium),** est en cours de mise hors service. Ses fonctionnalités ont été remplacées par la nouvelle [solution eDiscovery (Premium)](./ediscovery.md) dans le portail de conformité.

Pour déterminer si votre organisation utilise eDiscovery (Premium) v1.0 :

1. Accédez au portail de conformité, sélectionnez **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank">**Core**</a> et ouvrez un cas eDiscovery (Standard).

1. Si vous voyez le bouton **Basculer vers eDiscovery (Premium),** cliquez dessus pour accéder à la version 1.0 d’eDiscovery (Premium), qui est en cours de mise hors service. La possibilité de créer et de gérer des cas dans eDiscovery (Standard) n’est pas affectée. Seule la possibilité d’ajouter et d’analyser des données de cas dans eDiscovery (Premium) v1.0 (en cliquant sur **Basculer vers eDiscovery (Premium)**) est en cours de mise hors service.

La nouvelle solution eDiscovery (Premium) dans Microsoft 365 (également appelée *eDiscovery (Premium) v2.0)* fournit toutes les fonctionnalités de la solution d’origine, mais elle inclut désormais une approche basée sur le consignat de l’identification du contenu dans d’autres services Microsoft 365, de la collecte de ce contenu, puis de son ajout à un ensemble de révisions où les réviseurs peuvent tirer parti de requêtes de recherche rapide,  des fonctionnalités d’analyse et de balisage pour aider à éliminer les documents pertinents. eDiscovery (Premium) inclut désormais un traitement amélioré et des visionneuses natives pour les types de fichiers Microsoft et non-Microsoft, une liste complète des types de fichiers est [disponible ici](./supported-filetypes-ediscovery20.md) et les champs de métadonnées pris en charge sont [ici](./document-metadata-fields-in-advanced-ediscovery.md). En outre, la nouvelle solution eDiscovery (Premium) fournit une puissante fonctionnalité de gestion des conservations qui vous permet d’appliquer des conservations au contenu de différents services, d’informer les utilisateurs des conservations et de suivre les réponses des consignatateurs, le tout dans un cas eDiscovery (Premium).

Pour accéder à la découverte électronique (Premium) v 2.0 :

Accédez au portail de conformité, sélectionnez **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank">**Advanced**</a> et ouvrez un cas eDiscovery (Standard).

À ce stade, nous vous recommandons de commencer à migrer votre flux de travail eDiscovery vers la nouvelle fonctionnalité eDiscovery (Premium). Si nécessaire, vous pouvez archiver vos cas eDiscovery (Premium) 1.0 en exportant le contenu et en le stockant hors connexion. Bien que vous puissiez toujours accéder à eDiscovery (Premium) v1.0 dans les cas existants jusqu’au 31 décembre 2020, Support Microsoft ne fournira pas de support après le 1er octobre 2020. Pour plus d’informations, consultez la chronologie suivante.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- organisations Office 365 et Microsoft 365 Entreprise

- organisations Office 365 et Microsoft 365 Éducation

- Office 365 et les organisations Microsoft 365 Government ; cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : Vous ne pourrez pas créer de nouveaux cas eDiscovery (Premium) v1.0.

- 1er octobre 2020 : Vous ne pourrez pas ajouter de nouvelles données (préparer les résultats de recherche pour eDiscovery (Premium)) à aucun cas. Vous pourrez continuer à travailler avec des données dans des cas existants à vos propres risques. Support Microsoft ne fournira plus d’aide. 

- 31 décembre 2020 : Vous ne pourrez pas accéder aux cas eDiscovery (Premium) v1.0.

### <a name="alternative-tools"></a>Autres outils

Solution [eDiscovery (Premium)](./overview-ediscovery-20.md) dans le portail de conformité.
