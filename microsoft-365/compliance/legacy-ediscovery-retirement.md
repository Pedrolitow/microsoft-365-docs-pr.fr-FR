---
title: Retrait des outils eDiscovery hérités
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: In-Place eDiscovery et In-Place Hold (et les cmdlets PowerShell correspondantes) dans Exchange Online seront retirés au cours du premier semestre 2020. Les Search-Mailbox cmdlet et Advanced eDiscovery v1.0 sont également retirés au cours de la même période.
ms.openlocfilehash: 16a43122ce16a134a6068f78dadea02ac8605625
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59179940"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Retrait des outils eDiscovery hérités

> [!IMPORTANT]
> La fonctionnalité des outils eDiscovery hérités décrits dans cet article a été supprimée du service Microsoft 365 ou est toujours disponible, mais n’est plus prise en charge. Toutes les fonctionnalités encore disponibles peuvent être supprimées sans préavis. Si vous utilisez toujours l’un de ces outils hérités, envisagez de migrer vers les outils eDiscovery du Centre de conformité Microsoft 365 ou l’une des solutions de remplacement décrites dans cet article.

Au fil des ans, Microsoft a fourni des outils eDiscovery qui vous permettent de rechercher, d’afficher un aperçu et d’exporter du contenu de courrier à partir de Exchange Online. Toutefois, ces outils ne sont plus un moyen efficace de rechercher du contenu non Exchange dans d’autres services Microsoft 365, tels que SharePoint Online et Microsoft 365 Groups. Pour résoudre ce problème, Microsoft propose d’autres outils eDiscovery qui vous aident à rechercher un large éventail de Microsoft 365 contenu. Et nous avons travaillé dur pour incorporer la fonctionnalité eDiscovery la plus actuelle et la plus puissante dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com). Cela permet aux organisations de répondre à des demandes de documents juridiques, internes et autres pour du contenu dans de nombreux services Microsoft 365, y compris Exchange Online.

En raison de cette fonctionnalité eDiscovery nouvelle et améliorée dans le Centre de conformité Microsoft 365, nous allons retirer les fonctionnalités et fonctionnalités liées à eDiscovery suivantes liées à la recherche de contenu de messagerie dans Exchange Online et Microsoft 365 :

- [EDiscovery in-Place](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) et [In-Place Holds](/exchange/security-and-compliance/create-or-remove-in-place-holds) dans le centre Exchange’administration.

- Les cmdlets Exchange Online PowerShell qui prend en charge In-Place eDiscovery et les In-Place Holds (ces cmdlets sont identifiées collectivement en tant que cmdlets **-MailboxSearch).* Cela inclut les cmdlets suivantes :

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Les cmdlets [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) et [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) seront disponibles une fois les autres cmdlets ****-MailboxSearch*** supprimées afin que vous pouvez les utiliser pour faciliter votre transition vers d’autres outils eDiscovery et hold. Toutefois, après une date précise (mentionnée ci-dessous), le Support Microsoft ne prend plus en charge ces deux cmdlets.

- Cmdlet [Search-Mailbox](/powershell/module/exchange/search-mailbox) dans Exchange Online PowerShell.

- Les opérations suivantes dans l’API Exchange Services Web :

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Office 365 Advanced eDiscovery version 1.0,](./overview-ediscovery-20.md)qui est la première version de Advanced eDiscovery accessible via un cas core eDiscovery dans le Centre de conformité Microsoft 365. Le retrait de Advanced eDiscovery v1.0 n’a pas d’impact sur votre capacité à créer et gérer des cas eDiscovery principaux.

> [!NOTE]
> La fonctionnalité eDiscovery retirée s’applique uniquement aux versions cloud de Microsoft 365 et Office 365. La fonctionnalité eDiscovery dans les versions sur site de Exchange et SharePoint sera toujours prise en charge jusqu’à nouvel ordre.

Les sections suivantes de cet article fournissent des conseils sur chaque fonctionnalité retirée. Ces informations, y compris les chronologies et les outils de remplacement que vous pouvez utiliser à la place de l’outil retiré.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place eDiscovery et les In-Place dans le Centre d’administration Exchange’administration 

Comme indiqué dans l’annonce initiale du 1er juillet 2017, la fonctionnalité de In-Place eDiscovery & Hold dans le Centre d’administration Exchange (EAC) est retirée. La page In-Place'eDiscovery & de l’EAC vous a permis de rechercher, de conserver et d’exporter du contenu à partir Exchange Online. In-Place eDiscovery vous permet également de copier les résultats de la recherche dans une boîte aux lettres de découverte afin que vous ou d’autres responsables eDiscovery pouvez examiner le contenu et le rendre disponible pour les demandes légales, réglementaires et publiques.

Étant donné que toutes ces fonctionnalités (à l’exception de la copie des résultats de recherche dans une boîte aux lettres de découverte) sont désormais disponibles dans la recherche de contenu, les outils eDiscovery et Advanced eDiscovery dans le [Centre de conformité Microsoft 365](./microsoft-365-compliance-center.md) (avec des fonctionnalités améliorées, la fiabilité et la prise en charge d’un large éventail de services Microsoft 365), nous vous recommandons de commencer à utiliser ces outils dès que possible. Pour vous aider dans la transition vers ces autres outils eDiscovery, le tableau ci-dessous répertorie les outils que vous pouvez utiliser au lieu de In-Place eDiscovery et In-Place Hold.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations concernées

- Office 365 et Microsoft 365 Entreprise organisations

- Office 365 et Microsoft 365 Éducation organisations

- Office 365 et Microsoft 365 secteurs publics ; cela inclut Cloud de la communauté du secteur public, Cloud de la communauté du secteur public Élevé et DoD

- Office 365 Allemagne

### <a name="timeline-for-retirement"></a>Chronologie du retrait

- 1er juillet 2020 : vous ne pourrez pas créer de nouvelles recherches et de nouvelles recherches, mais vous pouvez toujours exécuter, modifier et supprimer des recherches existantes à vos propres risques. Le support Microsoft n'In-Place plus &'eDiscovery dans le EAC.

- 1er octobre 2020 : la fonctionnalité In-Place eDiscovery & Holds dans leAC sera placée en mode lecture seule. Cela signifie que vous ne pourrez supprimer que les recherches et les recherches existantes.

### <a name="alternative-tools"></a>Outils de remplacement

Le tableau suivant décrit les autres outils que vous pouvez utiliser pour remplacer les fonctionnalités existantes qui sont en cours de retrait.

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
<td>Rechercher, exporter et conserver à des fins juridiques</td>
<td>Principaux cas eDiscovery dans le Centre de conformité Microsoft 365 </td>
<td><p>L’utilisation des fonctionnalités des cas eDiscovery principaux fournit la parité fonctionnelle pour In-Place eDiscovery et les In-Place de découverte électronique. Les voici :</p>
<ul>
<li>
<p>La recherche s’dimensionnait jusqu’à des millions d’emplacements</p>
</li>
<li>
<p>Plus de fiabilité pour la recherche, l’exportation et la mise en attente du contenu</p>
</li>
<li>
<p>Recherche de contenu dans Exchange Online, SharePoint Online, OneDrive Entreprise, Skype Entreprise, Microsoft Teams, Yammer Groups, Microsoft 365 Groups et autres contenus stockés dans des applications Office 365</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Conservation à des fins de rétention</td>
<td>Stratégies de rétention dans le Centre de conformité Microsoft 365</td>
<td><p>Vous pouvez utiliser des stratégies de rétention pour conserver le contenu et, si vous le souhaitez, le supprimer après l’expiration de la période de rétention. Les autres fonctionnalités sont les suivantes :</p>
<ul>
<li>
<p>Application de stratégies à l’ensemble de votre organisation </p>
</li><li>
<p>Application de stratégies à des emplacements de contenu spécifiques tels que Exchange Online, SharePoint Online, OneDrive Entreprise, Skype Entreprise, Microsoft Teams et Office 365 Groupes</p></li>
<li>
<p>Application de stratégies à des utilisateurs spécifiques</p></li></ul>
<p>Pour plus d’informations, voir <a href="/microsoft-365/compliance/retention-policies">En savoir plus sur les stratégies de rétention et les étiquettes de rétention.</a></td>
</tr>
<tr class="odd">
<td>Copier les résultats de la recherche de courrier électronique dans une boîte aux lettres de découverte pour révision</td><td>Ensembles de révision Advanced eDiscovery v2.0</td>
<td><p>L’examen du contenu Microsoft 365 n’a jamais été aussi simple. Les ensembles de révision ont de nombreuses fonctionnalités pour vous aider à réduire le temps et les données nécessaires à la révision, notamment :</p>
<ul>
<li><p>Effectuer des requêtes de recherche rapide et filtrer le contenu dans un jeu à réviser</p></li>
<li><p>Analyser le contenu d’un jeu à réviser ; cela inclut le thread de messagerie, la détection de quasi-doublons, l’analyse des thèmes et le codage prédictif</p></li>
<li><p>Étiqueter les documents d’un jeu à réviser</p></li>
<li><p>Marquage de suggestions pour vous aider à identifier le contenu du privilège client avocat</p></li></ul>
<p>Pour plus d’informations, voir <a href="/microsoft-365/compliance/overview-ediscovery-20">vue d’ensemble de la solution avancée d'eDiscovery dans Microsoft 365</a>.</p>
<p>
<p>Vous pouvez également exporter les résultats de la recherche vers des fichiers PST, puis utiliser Microsoft 365 service d’importation pour importer les fichiers PST dans une boîte aux lettres de découverte. Pour obtenir des instructions détaillées, voir Utiliser le chargement réseau pour importer des <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">fichiers PST dans Office 365</a>.
</tr>
<tr class=even>
  <td>Copier des messages d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour accorder à une personne l’accès à la messagerie d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez accorder à une autre personne l’accès au courrier de l’ancien employé), nous vous recommandons d’attribuer à cette personne des autorisations pour accéder à la boîte aux lettres de l’ancien employé. Ainsi, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres utilisateur ou une boîte aux lettres partagée, attribuez simplement à un utilisateur les autorisations nécessaires pour accéder à la boîte aux lettres source.</td>
  
  </tr>
<tr class="odd">
<td>Restaurer des éléments à partir du dossier Éléments récupérables</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>Vous pouvez restaurer des éléments supprimés <i></i> définitivement (également appelés éléments supprimés (supprimés de manière temporaire) dans les boîtes aux lettres, tant que la période de rétention des éléments supprimés d’un élément n’a pas expiré. Pour plus d’informations, <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">voir dossier Éléments récupérables dans Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>FAQ sur les In-Place eDiscovery et les In-Place de découverte électronique

**J’utilise la fonctionnalité de copie des résultats de recherche de In-Place eDiscovery & holds in the EAC to copy search results to a discovery mailbox for review by attorneys. Quelles options ai-je maintenant ?**

Il existe deux façons de répliquer cette fonctionnalité aujourd’hui. La première consiste à utiliser des [ensembles de révision dans Advanced eDiscovery v2.0](./view-documents-in-review-set.md). Les ensembles de révision ont de nombreuses fonctionnalités que vous pouvez voir dans un outil de révision classique, comme la recherche rapide de documents, le marquage, le thread de courrier électronique, le regroupement de quasi-doublons, l’analyse des thèmes et le codage prédictif. Si vous souhaitez toujours utiliser des boîtes aux lettres de découverte pour révision, la deuxième option consiste à exporter les résultats de la recherche dans des fichiers PST, puis à importer les fichiers PST dans une boîte aux lettres de découverte à l’aide de la fonctionnalité d’importation [PST](use-network-upload-to-import-pst-files.md) dans le Centre de conformité Microsoft.

**Comment contrôler les emplacements de contenu (tels que les boîtes aux lettres ou les sites) qu’un gestionnaire eDiscovery peut rechercher à l’aide des nouveaux outils ?**

Le Centre de conformité Microsoft 365 utilise également des limites [de](set-up-compliance-boundaries.md) conformité pour contrôler les emplacements de contenu qu’un gestionnaire eDiscovery peut rechercher. Les limites de conformité sont utiles dans les entités gouvernementales qui doivent rester dans les limites des organismes ou des entreprises multinationales requises pour respecter les réglementations géographiques.

**Comment puis-je déplacer mes recherches et mes réserves actuelles vers le Centre de conformité Microsoft 365 ?**

Il est possible de migrer des recherches In-Place eDiscovery à partir du CAE à l’aide de PowerShell. Pour obtenir des instructions, voir Migrer des recherches et des données en cours à partir du [EAC](./migrate-legacy-ediscovery-searches-and-holds.md)vers le Centre de conformité Microsoft 365 .

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch cmdlets

Comme indiqué dans l’avis initial annoncé le 1er juillet 2017 dans le Centre d’administration Exchange, la fonctionnalité de In-Place eDiscovery & Hold et les cmdlets **\* -MailboxSearch** correspondantes sont supprimées. Ces cmdlets permettent aux utilisateurs de rechercher, de conserver et d’exporter du contenu de boîte aux lettres pour des demandes légales, réglementaires et publiques.

Étant donné que ces fonctionnalités sont désormais disponibles dans le Centre de sécurité et conformité [<span class="underline">& Centre de conformité Microsoft 365</span>](./microsoft-365-compliance-center.md) et Office 365 PowerShell avec des performances et une évolutivité améliorées, vous devez utiliser ces cmdlets améliorées. Ces cmdlets incluent [<span class="underline"> \* -ComplianceCase</span>](/powershell/module/exchange/get-compliancecase), [<span class="underline"> \* -ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline"> \* -CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline"> \* -CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule)et [<span class="underline"> \* -ComplianceSearchAction</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Étendue des organisations concernées

- Office 365 et Microsoft 365 Entreprise organisations

- Office 365 et Microsoft 365 Éducation organisations

- Office 365 et Microsoft 365 secteurs publics ; cela inclut Cloud de la communauté du secteur public, Cloud de la communauté du secteur public Élevé et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : vous ne pourrez pas utiliser **New-MailboxSearch** pour créer des recherches et des In-Place de découverte électronique In-Place, mais vous pouvez toujours utiliser des cmdlets pour exécuter, modifier et supprimer des recherches et des recherches existantes à vos risques et risques. Le support Microsoft ne fournira plus d’assistance pour ces types de recherches et de maintiens en place.

- 1er octobre 2020 : comme indiqué précédemment, la fonctionnalité In-Place eDiscovery & Holds dans leAC sera placée en mode lecture seule. Cela signifie également que vous ne pourrez pas utiliser les cmdlets **New-MailboxSearch,** **Start-MailboxSearch** ou **Set-MailboxSearch.** Vous pourrez uniquement obtenir et supprimer des recherches et des recherches existantes.

### <a name="alternative-tools"></a>Outils de remplacement

Le tableau suivant décrit les autres outils que vous pouvez utiliser pour remplacer les fonctionnalités existantes qui sont en cours de retrait.

<table>
<thead>
<tr class="header">
<th>Les fonctionnalités</th>
<th>Outils de remplacement</th>
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
<td><p>Les cmdlets ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et exporter du contenu. Vous pouvez créer une recherche et afficher l’estimation de la recherche à l’aide des cmdlets <strong>New-</strong>, <strong>Get-</strong>et <strong>Start-ComplianceSearch.</strong> Vous pouvez ensuite utiliser la cmdlet <strong>New-ComplianceSearchAction</strong> pour exporter les résultats de la recherche. Vous devez toujours utiliser l’outil eDiscovery principal dans le Centre de conformité Microsoft 365 pour télécharger ces résultats de recherche sur votre ordinateur local.</p>
<p>
<p><strong>Remarque :</strong> Si vous utilisez ces cmdlets pour créer des recherches qui ne sont pas associées à un cas eDiscovery principal, ces recherches se trouveront sur la <strong>page</strong> de recherche de contenu dans la Centre de conformité Microsoft 365.</p></td>
</tr>
<tr class="even">
<td>Conserver le contenu dans une boîte aux lettres</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Les Centre de conformité Microsoft 365 doivent être associés à un complianceCase. Tout d’abord, créez le cas de conformité, puis créez un CaseHoldPolicy et un CaseHoldRule.</p>
<p><strong>Remarque :</strong> La création d’une caseHoldPolicy sans création de CaseHoldRule rend la mise en attente inopérable jusqu’à ce que CaseHoldRule soit créé et associé à CaseHoldPolicy. Pour plus d’informations, voir la documentation de la cmdlet.</p></td>
</tr>
<tr class="odd">
<td>Copier les résultats de la recherche dans une boîte aux lettres de découverte</td>
<td>Aucun</td>
<td>Cette fonctionnalité ne remplace pas directement cette fonctionnalité, car elle ne permet pas d’accéder à tous Microsoft 365 services. Consultez le FAQ ci-dessous pour obtenir d’autres solutions.</td>
</tr>
  <tr class=even>
  <td>Copier des messages d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour accorder à une personne l’accès à la messagerie d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez accorder à une autre personne l’accès au courrier de l’ancien employé), nous vous recommandons d’attribuer à cette personne des autorisations pour accéder à la boîte aux lettres de l’ancien employé. Ainsi, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres utilisateur ou une boîte aux lettres partagée, il suffit d’attribuer à un utilisateur des autorisations pour accéder à la boîte aux lettres source.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>FAQ sur ***-MailboxSearch** cmdlets

**Nous utilisons la recherche de copie pour exporter des messages électroniques ou instantanés à d’autres fins de découverte électronique et d’enquêtes juridiques. Quelles sont les autres options disponibles une fois ces cmdlets retirées ?**

Les [<span class="underline">API Microsoft Graph</span>](https://developer.microsoft.com/en-us/graph) fournissent un certain nombre de méthodes pour extraire des données à des fins d’analyse et d’autres fins beaucoup plus résilientes et évolutives que l’utilisation des cmdlets **\* -MailboxSearch.**

**Comment puis-je migrer mes recherches et mes opérations de Centre de conformité Microsoft 365 ?**

Il est possible de migrer des recherches In-Place de découverte électronique à partir du centre d’administration Exchange à l’aide d’un script PowerShell. Pour plus d’informations, voir Migrer les recherches de découverte électronique [héritées](migrate-legacy-eDiscovery-searches-and-holds.md)et les Centre de conformité Microsoft 365 .

**Une fois les cmdlets supprimées, puis-je toujours supprimer ou récupérer des recherches ?**

Oui, bien que nous supprimant la possibilité de créer et de modifier des recherches, vous pourrez toujours utiliser **Get-MailboxSearch** et **Remove-MailboxSearch** jusqu’à nouvel ordre. Toutefois, l’utilisation de ces cmdlets sera à vos propres risques après les dates de retrait et le Support Microsoft ne pourra plus fournir d’assistance.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet

La cmdlet De recherche **de** boîte aux lettres dans Exchange Online PowerShell est retirée comme initialement annoncé dans un avertissement dans la sortie de cmdlet à partir de 2018. À l’origine, la cmdlet **Search-Mailbox** était utilisée pour rechercher dans la boîte aux lettres d’un utilisateur et purger le contenu malveillant. Nous vous recommandons de commencer à utiliser les cmd Office 365 lets **New-ComplianceSearch** et **New-ComplianceSearchAction** dans le Centre de sécurité & conformité PowerShell pour rechercher et vider le contenu. Pour une expérience de sécurité [<span class="underline"></span>](../security/index.yml) intégrée, les fonctionnalités de sécurité Microsoft 365 fournissent une protection fiable contre les menaces pour le courrier électronique et de nombreuses autres services Microsoft.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations concernées

- Office 365 et Microsoft 365 Entreprise organisations

- Office 365 et Microsoft 365 Éducation organisations

- Office 365 et Microsoft 365 secteurs publics ; cela inclut Cloud de la communauté du secteur public, Cloud de la communauté du secteur public Élevé et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

-  1er juillet 2020 : la cmdlet **Search-Mailbox** ne sera plus disponible et le support Microsoft ne fournira plus d’assistance.

### <a name="alternative-tools"></a>Outils de remplacement

Le tableau suivant décrit les autres outils que vous pouvez utiliser pour remplacer les fonctionnalités existantes qui sont en cours de retrait.

<table>
<thead>
<tr class="header">
<th>Les fonctionnalités</th>
<th>Outils de remplacement</th>
<th>Commentaires</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Rechercher dans une boîte aux lettres</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>Les cmdlets ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et exporter du contenu. Vous pouvez créer une recherche et afficher l’estimation de la recherche à l’aide des cmdlets <strong>New-</strong>, <strong>Get-</strong>et <strong>Start-ComplianceSearch.</strong> Vous pouvez ensuite utiliser la <strong>commande New-ComplianceSearchAction -Export</strong> pour exporter les résultats de la recherche. Vous devez toujours utiliser l’outil eDiscovery principal dans le Centre de conformité Microsoft 365 pour télécharger ces résultats de recherche sur votre ordinateur local.</p></p>
</td>
</tr>
<tr class="even">
<td>Supprimer des messages électroniques en bloc d’une boîte aux lettres</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Configurer une stratégie d’archivage et de suppression de boîtes aux lettres</span></a></p>
<p></p></td>
<td><p>Les administrateurs peuvent créer une stratégie d’archivage et de suppression qui déplace automatiquement des éléments vers la boîte aux lettres d’archivage d’un utilisateur et supprime automatiquement les éléments de la boîte aux lettres.</p>
</td>
</tr>
<tr class="even">
<td>Copier les résultats de la recherche dans une boîte aux lettres de découverte</td>
<td> </td>
<td>Cette fonctionnalité ne remplace pas directement cette fonctionnalité, car elle ne permet pas d’accéder à tous Microsoft 365 services. Consultez les FAQ de la section <strong>cmdlets *-MailboxSearch</strong> pour obtenir d’autres solutions. </td>
</tr>
<tr class=odd>
  <td>Copier des messages d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour accorder à une personne l’accès à la messagerie d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez accorder à une autre personne l’accès au courrier de l’ancien employé), nous vous recommandons d’attribuer à cette personne des autorisations pour accéder à la boîte aux lettres de l’ancien employé. Ainsi, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres utilisateur ou une boîte aux lettres partagée, il vous suffit d’attribuer à un utilisateur l’autorisation d’accéder à la boîte aux lettres source.</td>
</tr>
<tr class=even>
  <td>Purger des messages d’une boîte aux lettres</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>Les cmdlets ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et vider le contenu. Vous pouvez créer et exécuter une recherche avec les cmdlets <strong>New-ComplianceSearch</strong> et <strong>New-ComplianceSearch,</strong> puis vider le contenu à l’aide de la commande <strong>New-ComplianceSearchAction -Purge -PurgeType.</strong> Pour plus d’informations, <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">voir Rechercher et supprimer des messages.</span></a></p>
</td>
</tr>
<tr class="odd"> 
<td>Purger des messages d’une boîte aux lettres</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
<td>Pour vider les messages d’une boîte aux lettres, attribuez à un administrateur des autorisations pour accéder à la boîte aux lettres de l’employé. Les messages peuvent être supprimés et recyclés selon les besoins en profitant des fonctionnalités de recherche et d’affichage intégrées dans Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange Opérations de l’API des services web

Ces opérations dans l’API Exchange Web Services sont utilisées par la fonctionnalité In-Place eDiscovery & Holds dans le Centre d’administration Exchange et les cmdlets **\* -MailboxSearch** correspondantes dans Exchange Online PowerShell. Ils seront également retirés dans le cadre de la retrait des autres outils eDiscovery hérités.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations concernées

- Office 365 et Microsoft 365 Entreprise organisations

- Office 365 et Microsoft 365 Éducation organisations

- Office 365 et Microsoft 365 secteurs publics ; cela inclut Cloud de la communauté du secteur public, Cloud de la communauté du secteur public Élevé et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : les opérations GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes et GetHoldOnMailboxes ne seront plus disponibles et le support Microsoft ne fournira plus d’assistance.

## <a name="advanced-ediscovery-v10"></a>Advanced eDiscovery v1.0

Advanced eDiscovery version 1.0, qui est la version de Advanced eDiscovery disponible dans un cas eDiscovery principal en cliquant sur Basculer vers **Advanced eDiscovery**, est en cours de retrait. Sa fonctionnalité a été remplacée par la nouvelle [solution Advanced eDiscovery dans](./ediscovery.md) le Centre de conformité Microsoft 365.

Pour déterminer si votre organisation utilise Advanced eDiscovery v1.0 :

1. Accédez au [centre de conformité Microsoft 365](https://compliance.microsoft.com).

2. Dans le volet de navigation gauche du centre de conformité, cliquez sur **eDiscovery > Core** et ouvrez un cas core eDiscovery.

3. Si vous voyez le bouton Basculer vers **Advanced eDiscovery,** cliquez dessus pour passer à la version 1.0 de Advanced eDiscovery, qui est en cours de retrait. La possibilité de créer et de gérer des cas dans Core eDiscovery ne sera pas affectée. Seule la possibilité d’ajouter et d’analyser des données de cas dans Advanced eDiscovery v1.0 (en cliquant sur Basculer vers **Advanced eDiscovery**) est retirée.

La nouvelle solution Advanced eDiscovery dans Microsoft 365 (également appelée *Advanced eDiscovery v2.0*) fournit toutes les fonctionnalités de la solution d’origine, mais inclut désormais une approche basée sur les dépositaires qui consiste à identifier le contenu dans d’autres services Microsoft 365, à collecter ce contenu, puis à l’ajouter à un ensemble de révisions dans lequel les réviseurs peuvent tirer parti des fonctionnalités de recherche rapide, de marquage et d’analyse pour aider à mettre fin aux documents pertinents. Advanced eDiscovery inclut désormais un traitement amélioré et des visionneuses natives pour les types [](./supported-filetypes-ediscovery20.md) de fichiers Microsoft et non-Microsoft, une liste complète des types de fichiers est là et les champs de métadonnées pris en charge sont [ici.](./document-metadata-fields-in-advanced-ediscovery.md) En outre, la nouvelle solution Advanced eDiscovery fournit une fonctionnalité puissante de gestion des conservations des dépositaires qui vous permet d’appliquer des conservations au contenu de différents services, d’informer les utilisateurs des conservations et de suivre les réponses des dépositaires, le tout dans un cas Advanced eDiscovery.

Pour accéder à eDiscovery avancée v 2.0 :

1. Accédez au [centre de conformité Microsoft 365](https://compliance.microsoft.com).

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Tout afficher**, puis cliquez sur **eDiscovery >avancée**.

Pour l’instant, nous vous recommandons de commencer la transition de votre flux de travail eDiscovery vers la nouvelle fonctionnalité Advanced eDiscovery de découverte électronique. Si nécessaire, vous pouvez archiver Advanced eDiscovery cas 1.0 en exportant le contenu et en le stockant hors connexion. Bien que vous soyez toujours en mesure d’accéder à Advanced eDiscovery v1.0 dans les cas existants jusqu’au 31 décembre 2020, le support Microsoft ne fournira pas de support après le 1er octobre 2020. Pour plus d’informations, voir la chronologie suivante.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations concernées

- Office 365 et Microsoft 365 Entreprise organisations

- Office 365 et Microsoft 365 Éducation organisations

- Office 365 et Microsoft 365 secteurs publics ; cela inclut Cloud de la communauté du secteur public, Cloud de la communauté du secteur public Élevé et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : vous ne pourrez pas créer de nouveaux cas Advanced eDiscovery v1.0.

- 1er octobre 2020 : vous ne pourrez pas ajouter de nouvelles données (préparer les résultats de recherche pour Advanced eDiscovery) dans tous les cas. Vous pourrez continuer à travailler avec des données dans des cas existants à vos propres risques. Le support Microsoft ne fournira plus d’assistance. 

- 31 décembre 2020 : vous ne pourrez pas accéder Advanced eDiscovery cas v1.0.

### <a name="alternative-tools"></a>Outils de remplacement

La [Advanced eDiscovery solution](./overview-ediscovery-20.md) dans le Centre de conformité Microsoft 365.