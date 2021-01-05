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
description: In-Place la conservation de la découverte électronique et de In-Place (et les cmdlets PowerShell correspondantes) dans Exchange Online seront supprimées au cours de la première moitié de 2020. Les applets de commande Search-Mailbox et Advanced eDiscovery v 1.0 sont également retirées au cours de la même période.
ms.openlocfilehash: a40cc67b29e33d61d6750792f6a773622a73f678
ms.sourcegitcommit: 98b889e674ad1d5fa37d4b6c5fc3eda60a1d67f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49750877"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Retrait des outils eDiscovery hérités

> [!IMPORTANT]
> Microsoft a évalué la situation de l’État public, et nous comprenons l’impact que cela a sur nos clients. Nous souhaitons être des partenaires forts et des citoyens généraux responsables. Pour faciliter l’une des nombreuses charges que vous rencontrez, nous allons retarder la retraite planifiée pour les outils eDiscovery hérités décrits dans cet article de trois mois. **Les dates de déclassement mises à jour sont reflétées ci-dessous.**

Au fil des années, Microsoft a fourni des outils eDiscovery qui vous permettent de rechercher, de prévisualiser et d’exporter du contenu de courrier électronique à partir d’Exchange Online. Toutefois, ces outils ne vous offrent plus une méthode efficace pour rechercher du contenu non-Exchange dans d’autres services Microsoft 365, tels que les groupes SharePoint Online et Microsoft 365. Pour résoudre ce cas, Microsoft propose d’autres outils eDiscovery qui vous aident à rechercher un large éventail de contenu Microsoft 365. Nous travaillons et nous avons difficilement incorporer les fonctionnalités eDiscovery les plus récentes et les plus puissantes dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com). Cela permet aux organisations de répondre aux demandes juridiques, internes et autres documents pour le contenu de nombreux services Microsoft 365, dont Exchange Online.

À la suite de cette nouvelle fonctionnalité eDiscovery améliorée dans le centre de conformité Microsoft 365, nous retirons les fonctionnalités et fonctionnalités liées à la découverte électronique suivantes liées à la recherche de contenu de messagerie dans Exchange Online et Microsoft 365 :

- [Découverte électronique inaltérable](https://docs.microsoft.com/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) et [conservation](https://docs.microsoft.com/exchange/security-and-compliance/create-or-remove-in-place-holds) inaltérable dans le centre d’administration Exchange.

- Les cmdlets Exchange Online PowerShell qui prennent en charge les blocages eDiscovery et In-Place de In-Place (ces cmdlets sont collectivement identifiées comme des applets de commande **-MailboxSearch* ). Cela inclut les applets de commande suivantes :

  - [New-MailboxSearch](https://docs.microsoft.com/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](https://docs.microsoft.com/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](https://docs.microsoft.com/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](https://docs.microsoft.com/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Les cmdlets [Get-MailboxSearch](https://docs.microsoft.com/powershell/module/exchange/get-mailboxsearch) et [Remove-MailboxSearch](https://docs.microsoft.com/powershell/module/exchange/remove-mailboxsearch) seront disponibles une fois que les autres cmdlets * * * *-MailboxSearch * * _ sont déclassées afin que vous puissiez les utiliser pour vous aider dans la transition vers d’autres outils de découverte électronique et de conservation. Toutefois, après une certaine date (citée ci-dessous), le support Microsoft ne prend plus en charge ces deux cmdlets.

- Cmdlet [Search-Mailbox](https://docs.microsoft.com/powershell/module/exchange/search-mailbox) dans Exchange Online PowerShell.

- Les opérations suivantes dans l’API des services Web Exchange :

   - [GetSearchableMailboxes](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](https://docs.microsoft.com/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](https://docs.microsoft.com/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](https://docs.microsoft.com/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Office 365 Advanced eDiscovery v 1.0](office-365-advanced-ediscovery.md), qui est la première version de Advanced eDiscovery accessible via un cas de découverte électronique de base dans le centre de sécurité & Office 365 Security. Le retrait de Advanced eDiscovery v 1.0 n’a pas d’impact sur votre capacité à créer et gérer des cas de découverte électronique de base.

> [!NOTE]
> La fonctionnalité de découverte électronique en retrait ne s’applique qu’aux versions Cloud de Microsoft 365 et Office 365. la fonctionnalité eDiscovery dans les versions locales d’Exchange et de SharePoint sera toujours prise en charge jusqu’à l’avertissement.

Les sections suivantes de cet article fournissent des instructions sur chaque fonctionnalité déclassée. Ces informations, y compris les chronologies et les outils de remplacement, que vous pouvez utiliser à la place de l’outil retiré.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place eDiscovery et des In-Place conservations dans le centre d’administration Exchange 

Conformément à l’annonce d’origine le 1er juillet 2017, la fonctionnalité de blocage de la In-Place eDiscovery & dans le centre d’administration Exchange est en cours de retrait. La page In-Place eDiscovery & conservation du centre d’administration Exchange vous permet de rechercher, de mettre en attente et d’exporter du contenu à partir d’Exchange Online. In-Place eDiscovery vous permet également de copier les résultats de la recherche dans une boîte aux lettres de découverte afin que vous-même ou d’autres gestionnaires eDiscovery puissiez consulter le contenu et le mettre à la disposition des demandes juridiques, réglementaires et publiques.

Étant donné que toutes ces fonctionnalités (à l’exception de la copie des résultats de la recherche dans une boîte aux lettres de découverte) sont désormais disponibles dans les outils de recherche de contenu, eDiscovery et eDiscovery dans le [Centre de conformité microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/microsoft-365-compliance-center) (avec des fonctionnalités améliorées, une fiabilité et une prise en charge pour une large gamme de services Microsoft 365 Pour vous aider lors de la transition vers ces autres outils eDiscovery, le tableau ci-dessous répertorie les outils que vous pouvez utiliser au lieu de In-Place la découverte électronique et la conservation de In-Place.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- Organisations Office 365 et Microsoft 365 entreprise

- Organisations Office 365 et Microsoft 365 éducation

- Organisations gouvernementales Office 365 et Microsoft 365 ; Cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline-for-retirement"></a>Chronologie de la retraite

- 1er juillet 2020 : vous ne serez pas en mesure de créer des recherches et des suspensions, mais vous pouvez toujours exécuter, modifier et supprimer des recherches existantes à vos propres risques. Le support Microsoft ne pourra plus In-Place & eDiscovery dans le centre d’administration Exchange.

- 1er octobre 2020 : les fonctionnalités de In-Place eDiscovery & de conservation dans le centre d’administration Exchange sont placées en mode lecture seule. Cela signifie que vous pourrez uniquement supprimer des recherches et des suspensions existantes.

### <a name="alternative-tools"></a>Outils de remplacement

Le tableau suivant décrit les autres outils que vous pouvez utiliser pour remplacer la fonctionnalité existante en cours de retrait.

<table>
<thead>
<tr class="header">
<th>Les fonctionnalités</th>
<th>Outil de remplacement</th>
<th>Commentaires</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Recherche, exportation et conservation à des fins juridiques</td>
<td>Cas de découverte électronique de base dans le centre de conformité Microsoft 365 </td>
<td><p>L’utilisation des fonctionnalités des cas de découverte électronique de base fournit la parité fonctionnelle pour In-Place les conservations eDiscovery et In-Place. Les voici :</p>
<ul>
<li>
<p>La recherche s’adapte à des millions d’emplacements</p>
</li>
<li>
<p>Meilleure fiabilité de recherche, d’exportation et de mise en attente du contenu</p>
</li>
<li>
<p>Recherche de contenu dans pour Exchange Online, SharePoint Online, OneDrive entreprise, Skype entreprise, Microsoft Teams, groupes Yammer, groupes Microsoft 365 et d’autres contenus stockés dans les applications Office 365</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Conservation à des fins de rétention</td>
<td>Stratégies de rétention dans le centre de conformité Microsoft 365</td>
<td><p>Vous pouvez utiliser des stratégies de rétention pour conserver le contenu et, si vous le souhaitez, le supprimer une fois la période de rétention expirée. Autres fonctionnalités :</p>
<ul>
<li>
<p>Application des stratégies à l’ensemble de votre organisation </p>
</li><li>
<p>Application de stratégies à des emplacements de contenu spécifiques, tels que les groupes Exchange Online, SharePoint Online, OneDrive entreprise, Skype entreprise, Microsoft teams et Office 365</p></li>
<li>
<p>Application de stratégies à des utilisateurs spécifiques</p></li></ul>
<p>Pour plus d’informations, voir <a href="https://docs.microsoft.com/microsoft-365/compliance/retention-policies"> en savoir plus sur les stratégies de rétention et les étiquettes de rétention</a>.</td>
</tr>
<tr class="odd">
<td>Copier les résultats de la recherche de messagerie vers une boîte aux lettres de découverte pour révision</td><td>Examiner les ensembles dans Advanced eDiscovery v 2.0</td>
<td><p>L’examen du contenu dans Microsoft 365 n’a jamais été aussi simple. Les ensembles de révision disposent de nombreuses fonctionnalités très intéressantes pour vous aider à réduire le temps et les données nécessaires à la révision, notamment :</p>
<ul>
<li><p>Effectuer des requêtes de recherche rapides et filtrer le contenu dans un jeu de révision</p></li>
<li><p>Analyser le contenu d’un ensemble de révision ; Cela inclut le Threading de messagerie, la détection de quasi-duplication, l’analyse des thèmes et le codage prédictif</p></li>
<li><p>Étiqueter les documents d’un jeu à réviser</p></li>
<li><p>Suggestions de marquage pour identifier le contenu du privilège client des avocats</p></li></ul>
<p>Pour plus d’informations, voir <a href="https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20">vue d’ensemble de la solution avancée d'eDiscovery dans Microsoft 365</a>.</p>
<p>
<p>Vous pouvez également exporter les résultats de recherche vers des fichiers PST, puis utiliser le service d’importation Microsoft 365 pour importer les fichiers PST dans une boîte aux lettres de découverte. Pour obtenir des instructions pas à pas, reportez-vous à la rubrique <a href="https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files">utiliser le chargement réseau pour importer des fichiers PST vers Office 365</a>.
</tr>
<tr class=even>
  <td>Copier des messages à partir d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour accorder à une personne l’accès à la messagerie d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez lui donner accès à l’e-mail de l’ancien employé), nous vous recommandons de lui attribuer des autorisations d’accès à la boîte aux lettres de l’ancien employé. Par conséquent, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres d’utilisateur ou une boîte aux lettres partagée, affectez simplement des autorisations utilisateur pour accéder à la boîte aux lettres source.</td>
  
  </tr>
<tr class="odd">
<td>Restaurer des éléments à partir du dossier éléments récupérables</td>
  <td><a href="https://docs.microsoft.com/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>Vous pouvez restaurer des éléments supprimés définitivement (également appelés éléments <i>supprimés</i> ) dans les boîtes aux lettres, tant que la période de rétention des éléments supprimés d’un élément n’a pas expiré. Pour plus d’informations, consultez la rubrique <a href="https://docs.microsoft.com/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">dossier éléments récupérables dans Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>FAQ sur les conservations eDiscovery et In-Place de In-Place

_ *J’utilise la fonctionnalité copier les résultats de recherche d' In-Place & eDiscovery dans le centre d’administration Exchange pour copier les résultats de la recherche dans une boîte aux lettres de découverte pour révision par les avocats. Quelles sont les options disponibles ?**

Il existe deux façons de répliquer cette fonctionnalité dès à présent. La première consiste à utiliser [des ensembles de révision dans Advanced eDiscovery v 2.0](https://docs.microsoft.com/microsoft-365/compliance/view-documents-in-review-set). Les ensembles de révisions disposent de la plupart des fonctionnalités que vous voyez dans un outil de révision classique, comme la recherche rapide de documents, le marquage, le Threading de messagerie, le regroupement en double, l’analyse des thèmes et le codage prédictif. Si vous souhaitez toujours utiliser des boîtes aux lettres de découverte pour révision, la deuxième option consiste à exporter les résultats de recherche vers des fichiers PST, puis à importer les fichiers PST dans une boîte aux lettres de découverte à l’aide de la [fonctionnalité d’importation PST](use-network-upload-to-import-pst-files.md) dans le centre de conformité Microsoft.

**Comment puis-je contrôler les emplacements de contenu (par exemple, les boîtes aux lettres ou les sites) pouvant être recherchés par un gestionnaire eDiscovery en utilisant les nouveaux outils ?**

Le centre de conformité Microsoft 365 utilise également des [limites de conformité](set-up-compliance-boundaries.md) pour contrôler les emplacements de contenu qu’un gestionnaire eDiscovery peut rechercher. Les limites de conformité sont utiles dans les entités gouvernementales qui doivent rester au sein des frontières des agences ou des sociétés multinationales requises pour respecter les cartes géographiques.

**Comment puis-je déplacer mes recherches et conservations en cours vers le centre de conformité Microsoft 365 ?**

Il est possible de migrer les In-Place les recherches de découverte électronique à partir du centre d’administration Exchange à l’aide de PowerShell. Pour obtenir des instructions, voir [migrer des recherches et des suspensions du centre d’administration Exchange vers le centre de conformité Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2114224).

## <a name="-mailboxsearch-cmdlets"></a>\*-Cmdlets MailboxSearch

Conformément à l’avis d’origine annoncé le 1er juillet 2017 dans le centre d’administration Exchange, la fonctionnalité de blocage de la In-Place eDiscovery & et les cmdlets **\* MailboxSearch** correspondantes sont en cours de retrait. Ces applets de commande permettent aux utilisateurs de rechercher, de mettre en attente et d’exporter du contenu de boîtes aux lettres pour des demandes juridiques, réglementaires et publiques.

Étant donné que ces fonctionnalités sont désormais disponibles dans le centre de [<span class="underline">conformité Microsoft 365</span>](https://docs.microsoft.com/microsoft-365/compliance/microsoft-365-compliance-center) et Office 365 Security & PowerShell avec des performances et une évolutivité accrues, vous devez utiliser ces cmdlets améliorées. Ces applets de commande incluent [<span class="underline"> \* -ComplianceCase</span>](https://docs.microsoft.com/powershell/module/exchange/get-compliancecase), [<span class="underline"> \* -ComplianceSearch</span>](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch), [<span class="underline"> \* -CaseHoldPolicy</span>](https://docs.microsoft.com/powershell/module/exchange/get-caseholdpolicy), [<span class="underline"> \* -CaseHoldRule</span>](https://docs.microsoft.com/powershell/module/exchange/get-caseholdrule)et [<span class="underline"> \* -ComplianceSearchAction</span>](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- Organisations Office 365 et Microsoft 365 entreprise

- Organisations Office 365 et Microsoft 365 éducation

- Organisations gouvernementales Office 365 et Microsoft 365 ; Cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : vous ne pourrez pas utiliser **New-MailboxSearch** pour créer de nouvelles recherches de découverte électronique In-Place et In-Place conservations, mais vous pouvez toujours utiliser des applets de commande pour exécuter, modifier et supprimer des recherches et des suspensions existantes à vos propres risques. Le support Microsoft ne fournira plus d’aide pour ces types de recherches et de suspensions.

- Le 1er octobre 2020 : comme indiqué précédemment, le In-Place eDiscovery & conserve les fonctionnalités du centre d’administration Exchange en mode lecture seule. Cela signifie également que vous ne pourrez pas utiliser les cmdlets **New-MailboxSearch**, **Start-MailboxSearch** ou **Set-MailboxSearch** . Vous ne pourrez obtenir et supprimer que les recherches et les suspensions existantes.

### <a name="alternative-tools"></a>Outils de remplacement

Le tableau suivant décrit les autres outils que vous pouvez utiliser pour remplacer la fonctionnalité existante en cours de retrait.

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
<td>Recherche et exportation</td>
<td><p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Les cmdlets ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et exporter du contenu. Vous pouvez créer une recherche et afficher l’estimation de la recherche à l’aide des cmdlets <strong>New-</strong>, <strong>Get-</strong>et <strong>Start-ComplianceSearch</strong> . Vous pouvez ensuite utiliser la cmdlet <strong>New-ComplianceSearchAction</strong> pour exporter les résultats de la recherche. Vous devrez toujours utiliser l’outil eDiscovery principal dans le centre de conformité Microsoft 365 pour télécharger ces résultats de recherche sur votre ordinateur local.</p>
<p>
<p><strong>Remarque :</strong> Si vous utilisez ces applets de commande pour créer des recherches qui ne sont pas associées à un cas de découverte électronique de base, ces recherches se situent sur la page de <strong>recherche de contenu</strong> dans le centre de conformité Microsoft 365.</p></td>
</tr>
<tr class="even">
<td>Conserver le contenu d’une boîte aux lettres</td>
<td><p><a href="https://docs.microsoft.com/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="https://docs.microsoft.com/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Les suspensions dans le centre de conformité Microsoft 365 doivent être associées à un ComplianceCase. Tout d’abord, créez le cas de conformité, puis créez un CaseHoldPolicy et un CaseHoldRule.</p>
<p><strong>Remarque :</strong> La création d’un CaseHoldPolicy sans CaseHoldRule de création rend le blocage inutilisable jusqu’à la création de l’CaseHoldRule et son association à l’CaseHoldPolicy. Pour plus d’informations, consultez la documentation de l’applet de commande.</p></td>
</tr>
<tr class="odd">
<td>Copier les résultats de la recherche dans une boîte aux lettres de découverte</td>
<td>Aucun</td>
<td>Il n’existe pas de remplacement direct de cette fonctionnalité, car elle ne fournit pas d’accès à tous les services Microsoft 365. Consultez le Forum aux questions ci-dessous pour obtenir d’autres solutions.</td>
</tr>
  <tr class=even>
  <td>Copier des messages à partir d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour accorder à une personne l’accès à la messagerie d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez lui donner accès à l’e-mail de l’ancien employé), nous vous recommandons de lui attribuer des autorisations d’accès à la boîte aux lettres de l’ancien employé. Par conséquent, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres d’utilisateur ou une boîte aux lettres partagée, affectez simplement des autorisations utilisateur pour accéder à la boîte aux lettres source.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>FAQ sur les applets de commande ***-MailboxSearch**

**Nous utilisons la fonctionnalité de recherche de copie pour exporter des messages électroniques ou des messages instantanés à des fins autres enquêtes juridiques et eDiscovery. Quelles sont les autres options dont nous disposons après avoir retiré ces applets de commande ?**

Les [<span class="underline">API Microsoft Graph</span>](https://developer.microsoft.com/en-us/graph) fournissent un certain nombre de méthodes pour extraire des données à des fins d’analyse et d’autres objectifs qui sont beaucoup plus résilientes et évolutives que l’utilisation des cmdlets **\* -MailboxSearch** .

**Comment puis-je migrer mes recherches et conservations vers le centre de conformité Microsoft 365 ?**

Il est possible de migrer les In-Place les recherches de découverte électronique à partir du centre d’administration Exchange à l’aide d’un script PowerShell. Pour plus d’informations, reportez-vous [à la rubrique Migrate Legacy eDiscovery Searches and holds to the Microsoft 365 Compliance Center](migrate-legacy-eDiscovery-searches-and-holds.md).

**Une fois que les applets de commande sont déclassées, est-ce que je peux toujours supprimer ou récupérer les recherches ?**

Oui, bien que nous supprimions la possibilité de créer et de modifier des recherches, vous pourrez toujours utiliser **Get-MailboxSearch** et **Remove-MailboxSearch** jusqu’à ce qu’il en soit informé. Toutefois, l’utilisation de ces applets de commande se fera à vos propres risques une fois que les dates de retraite et le support Microsoft ne pourront plus fournir d’assistance.

## <a name="search-mailbox-cmdlet"></a>Cmdlet Search-Mailbox

La cmdlet **Search-Mailbox** dans Exchange Online PowerShell est en cours de retrait à l’origine dans un avertissement de la sortie de la cmdlet en commençant dans 2018. La cmdlet **Search-Mailbox** a été initialement utilisée pour rechercher la boîte aux lettres d’un utilisateur et vider son contenu malveillant. Nous vous recommandons de commencer à utiliser les applets de commande **New-ComplianceSearch** et **New-ComplianceSearchAction** dans Office 365 Security & PowerShell Center PowerShell pour rechercher et purger le contenu. Pour une expérience de sécurité intégrée, les [<span class="underline">fonctionnalités de sécurité de microsoft 365</span>](https://docs.microsoft.com/microsoft-365/security/) fournissent une protection robuste contre les menaces pour le courrier électronique et de nombreux autres services Microsoft.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- Organisations Office 365 et Microsoft 365 entreprise

- Organisations Office 365 et Microsoft 365 éducation

- Organisations gouvernementales Office 365 et Microsoft 365 ; Cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

-  1er juillet 2020 : la cmdlet **Search-Mailbox** ne sera plus disponible et le support Microsoft ne fournira plus d’aide.

### <a name="alternative-tools"></a>Outils de remplacement

Le tableau suivant décrit les autres outils que vous pouvez utiliser pour remplacer la fonctionnalité existante en cours de retrait.

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
<td>Rechercher une boîte aux lettres</td>
<td><p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>Les cmdlets ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et exporter du contenu. Vous pouvez créer une recherche et afficher l’estimation de la recherche à l’aide des cmdlets <strong>New-</strong>, <strong>Get-</strong>et <strong>Start-ComplianceSearch</strong> . Vous pouvez ensuite utiliser la commande <strong>New-ComplianceSearchAction-Export</strong> pour exporter les résultats de la recherche. Vous devrez toujours utiliser l’outil eDiscovery principal dans le centre de conformité Microsoft 365 pour télécharger ces résultats de recherche sur votre ordinateur local.</p></p>
</td>
</tr>
<tr class="even">
<td>Supprimer les messages électroniques en masse d’une boîte aux lettres</td>
<td><p><a href="https://docs.microsoft.com/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes?view=o365-worldwide"><span class="underline">Configurer une stratégie d’archivage et de suppression de boîtes aux lettres</span></a></p>
<p></p></td>
<td><p>Les administrateurs peuvent créer une stratégie d’archivage et de suppression qui déplace automatiquement les éléments vers la boîte aux lettres d’archivage d’un utilisateur et supprime automatiquement les éléments de la boîte aux lettres.</p>
</td>
</tr>
<tr class="even">
<td>Copier les résultats de la recherche dans une boîte aux lettres de découverte</td>
<td> </td>
<td>Il n’existe pas de remplacement direct de cette fonctionnalité, car elle ne fournit pas d’accès à tous les services Microsoft 365. Consultez la FAQ dans la section <strong>*-MailboxSearch cmdlets</strong> pour obtenir d’autres solutions. </td>
</tr>
<tr class=odd>
  <td>Copier des messages à partir d’une boîte aux lettres vers une autre boîte aux lettres</td>
  <td><a href="https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
  <td>Pour accorder à une personne l’accès à la messagerie d’un autre utilisateur (par exemple, lorsqu’un employé quitte votre organisation et que vous devez lui donner accès à l’e-mail de l’ancien employé), nous vous recommandons de lui attribuer des autorisations d’accès à la boîte aux lettres de l’ancien employé. Par conséquent, au lieu de copier des éléments de boîte aux lettres vers une autre boîte aux lettres d’utilisateur ou une boîte aux lettres partagée, affectez simplement des autorisations utilisateur pour accéder à la boîte aux lettres source.</td>
</tr>
<tr class=even>
  <td>Purger les messages d’une boîte aux lettres</td>
<td><p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>Les cmdlets ComplianceSearch et ComplianceSearchAction fonctionnent ensemble pour vous aider à rechercher et à purger le contenu. Vous pouvez créer et exécuter une recherche à l’aide des cmdlets <strong>New-ComplianceSearch</strong> et <strong>New-ComplianceSearch</strong> , puis purger le contenu à l’aide de la commande <strong>New-ComplianceSearchAction-purge-PurgeType permet</strong> . Pour plus d’informations, consultez la rubrique <a href="https://docs.microsoft.com/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">Rechercher et supprimer des messages</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>Purger les messages d’une boîte aux lettres</td>
<td><a href="https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Attribuer des autorisations à une boîte aux lettres</a></td>
<td>Pour purger les messages d’une boîte aux lettres, attribuez aux administrateurs des autorisations d’accès à la boîte aux lettres de l’employé. Les messages peuvent être supprimés et recyclés selon les besoins en tirant parti des fonctionnalités de recherche et d’affichage intégrées dans Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Opérations de l’API des services Web Exchange

Ces opérations dans l’API des services Web Exchange sont utilisées par la fonctionnalité In-Place eDiscovery & suspensions dans le centre d’administration Exchange et les cmdlets **\* MailboxSearch** correspondantes dans Exchange Online PowerShell. Elles seront également supprimées dans le cadre de la suppression des autres outils eDiscovery hérités.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- Organisations Office 365 et Microsoft 365 entreprise

- Organisations Office 365 et Microsoft 365 éducation

- Organisations gouvernementales Office 365 et Microsoft 365 ; Cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : les opérations GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes et GetHoldOnMailboxes ne seront plus disponibles et le support Microsoft ne fournira plus d’aide.

## <a name="advanced-ediscovery-v10"></a>Advanced eDiscovery v 1.0

Advanced eDiscovery v 1.0, qui est la version de Advanced eDiscovery disponible dans un cas de découverte électronique fondamentale en cliquant sur **basculer vers Advanced eDiscovery**, est en cours de retrait. Sa fonctionnalité a été remplacée par la nouvelle [solution EDiscovery avancée](https://aka.ms/edisco) dans le centre de conformité Microsoft 365.

Pour déterminer si votre organisation utilise Advanced eDiscovery v 1.0 :

1. Accédez au [Centre de sécurité & conformité d’Office 365](https://protection.office.com).

2. Dans le volet de navigation de gauche du centre de sécurité & conformité, cliquez sur **ediscovery > eDiscovery**, puis ouvrez un cas de découverte électronique de base.

3. Si vous voyez le bouton **basculer vers Advanced eDiscovery** , le fait de cliquer dessus vous permettra d’accéder à la version 1,0 de Advanced eDiscovery, qui est en cours de retrait. La possibilité de créer et de gérer des cas dans la découverte électronique centrale n’est pas affectée. Seule la possibilité d’ajouter et d’analyser des données de cas dans Advanced eDiscovery v 1.0 (en cliquant sur **basculer vers Advanced eDiscovery**) est supprimée.

La nouvelle solution eDiscovery avancée de Microsoft 365 (également appelée *Advanced eDiscovery v 2.0*) offre toutes les fonctionnalités de la solution d’origine, mais inclut désormais une approche basée sur le dépositaire pour identifier le contenu dans d’autres services Microsoft 365, recueillir ce contenu, puis l’ajouter à un ensemble de révisions où les réviseurs peuvent tirer parti des requêtes de recherche rapide, des balises et des fonctionnalités d’analyse pour vous aider à rechercher des documents pertinents. Advanced eDiscovery inclut désormais un traitement amélioré et des visionneuses natives pour les types de fichier Microsoft et non-Microsoft, une liste complète des types de fichiers est [ici](https://docs.microsoft.com/microsoft-365/compliance/supported-filetypes-ediscovery20) et les champs de métadonnées pris en charge sont présents [ici](https://docs.microsoft.com/microsoft-365/compliance/document-metadata-fields-in-advanced-ediscovery). Par ailleurs, la nouvelle solution eDiscovery avancée fournit une fonctionnalité de gestion des blocages de gestion puissante qui vous permet d’appliquer des suspensions au contenu dans différents services, d’avertir les utilisateurs des suspensions et de suivre les réponses des dépositaires, tout cela dans un cas avancé de découverte électronique.

Pour accéder à eDiscovery avancée v 2.0 :

1. Accédez au [centre de conformité Microsoft 365](https://compliance.microsoft.com).

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Tout afficher**, puis cliquez sur **eDiscovery >avancée**.

Pour l’instant, nous vous recommandons de commencer la transition de votre flux de travail eDiscovery vers la nouvelle fonctionnalité eDiscovery avancée. Si nécessaire, vous pouvez archiver vos cas Advanced eDiscovery 1,0 en exportant le contenu et en le stockant hors connexion. Bien que vous puissiez toujours accéder à Advanced eDiscovery v 1.0 dans les cas existants jusqu’au 31 décembre 2020, le support Microsoft ne fournira aucune assistance après le 1er octobre 2020. Pour plus d’informations, consultez la chronologie suivante.

### <a name="scope-of-affected-organizations"></a>Étendue des organisations affectées

- Organisations Office 365 et Microsoft 365 entreprise

- Organisations Office 365 et Microsoft 365 éducation

- Organisations gouvernementales Office 365 et Microsoft 365 ; Cela inclut GCC, GCC High et DoD

- Office 365 Allemagne

### <a name="timeline"></a>Chronologie

- 1er juillet 2020 : vous ne pourrez pas créer de nouveaux cas de découverte électronique avancée v 1.0.

- 1er octobre 2020 : vous ne pourrez pas ajouter de nouvelles données (préparer les résultats de recherche pour Advanced eDiscovery) dans n’importe quel cas. Vous pourrez continuer à travailler avec des données dans les cas existants à vos risques et périls. Le support Microsoft ne fournira plus d’assistance. 

- 31 décembre 2020 : vous ne serez pas en mesure d’accéder aux cas avancés de la version 1.0 de eDiscovery.

### <a name="alternative-tools"></a>Outils de remplacement

La [solution EDiscovery avancée](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20) dans le centre de conformité Microsoft 365.
