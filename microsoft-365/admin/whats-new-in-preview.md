---
title: Nouveautés du Centre d'administration Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- MET150
- MOE150
- FRP150
ms.custom:
- MACDashWhatsNew
- AdminSurgePortfolio
- admindeeplinkMAC
description: Le Centre d'administration Microsoft 365 - découvrez les fonctionnalités qui ont été ajoutées ce mois-ci.
ms.openlocfilehash: fe801e913e227239b53eb7f1166a3f802f4217ce
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602577"
---
# <a name="whats-new-in-the-microsoft-365-admin-center"></a>Nouveautés du Centre d'administration Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Certaines des informations contenues dans cet article peuvent ne pas s’appliquer à Office 365 géré par 21Vianet.

::: moniker-end

Nous ajoutons en permanence de nouvelles fonctionnalités à [la Centre d'administration Microsoft 365](Vue d’ensemble du Centre d'administration Microsoft 365](admin-overview/admin-center-overview.md), corrigeant les problèmes que nous apprenons et apportant des modifications en fonction de vos commentaires. Certaines fonctionnalités sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, [essayez de vous ajouter à une version ciblée](manage/release-options-in-office-365.md).

Et si vous souhaitez savoir ce qui est nouveau avec d’autres services cloud Microsoft :

- [Nouveautés d’Azure Active Directory](/azure/active-directory/fundamentals/whats-new)
- [Nouveautés du Centre d’administration Exchange](/Exchange/whats-new)
- [Nouveautés de Microsoft Intune](/mem/intune/fundamentals/whats-new)
- [Nouveautés du portail de conformité Microsoft Purview](/Office365/SecurityCompliance/whats-new)
- [Nouveautés de Microsoft 365 Defender](../security/mtp/whats-new.md)
- [Nouveautés du Centre d’administration SharePoint](/sharepoint/what-s-new-in-admin-center)
- [Mises à jour Office](/OfficeUpdates/)
- [Comment vérifier l’intégrité des versions de Windows](/windows/deployment/update/check-release-health)

## <a name="may-2022"></a>Mai 2022

### <a name="role-based-access-controls-rbac"></a>Contrôles d’accès en fonction du rôle (RBAC)

Il existe quatre nouveaux rôles dans le Centre d'administration Microsoft 365 pour la gestion des attributs de sécurité personnalisés. Ces rôles sont disponibles pour tous les utilisateurs dans le Centre d'administration Microsoft 365 sous **Rôles**.

- **Administrateur d’affectation d’attributs**   Affectez des clés et des valeurs d’attribut de sécurité personnalisées aux objets Azure AD pris en charge.

- **Lecteur d’affectation d’attributs**   Lit les valeurs et les clés d’attribut de sécurité personnalisées pour les objets Azure AD pris en charge.

- **Administrateur de définition d’attribut**   Définissez et gérez la définition d’attributs de sécurité personnalisés.

- **Lecteur de définition d’attribut**   Lit la définition des attributs de sécurité personnalisés.

Il existe également un nouveau rôle qui vous permet de donner aux administrateurs uniquement l’accès dont ils ont besoin pour gérer les visites virtuelles.

- **Administrateur des visites virtuelles**   Gérez et partagez les informations et les métriques des visites virtuelles à partir de centres d’administration ou de l’application Visites virtuelles.

Pour plus d’informations sur ces rôles, consultez [les rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).

### <a name="quick-assist"></a>Assistance rapide

Nous avons déplacé Assistance rapide vers le Windows Store pour améliorer les performances et la sécurité de l’application. L’application Windows Assistance rapide vous permet, ainsi qu’à vos utilisateurs finaux, de recevoir ou de fournir une assistance SUR PC via une connexion à distance.

Avec la nouvelle application Assistance rapide Store, vous devriez constater une amélioration significative des temps de génération de code secret et une réduction des erreurs d’application.

Pour plus d’informations, consultez [Résoudre les problèmes de PC via une connexion à distance](https://support.microsoft.com/windows/solve-pc-problems-over-a-remote-connection-b077e31a-16f4-2529-1a47-21f6a9040bf3) et [installer Assistance rapide](https://support.microsoft.com/windows/install-quick-assist-c17479b7-a49d-4d12-938c-dbfb97c88bca)

## <a name="april-2022"></a>Avril 2022

### <a name="nps-sentiment-insights"></a>NPS Sentiment Insights

NPS Survey Insights est un tableau de bord piloté par l’IA disponible dans le Centre d'administration Microsoft 365.

Dans le Centre d’administration, **accédez aux** > **insights d’enquête NPS** **de commentaires sur les produits** >  d’intégrité.

Cette fonctionnalité permet aux administrateurs comme vous d’obtenir des insights exploitables dérivés des enquêtes Microsoft NPS auxquelles vos utilisateurs ont répondu. Pour en savoir plus, consultez [les commentaires et insights NPS du produit Microsoft pour votre organisation](manage/manage-feedback-product-insights.md).

En fonction de vos commentaires, nous introduisons une nouvelle fonctionnalité qui identifie le sentiment de chaque commentaire détaillé NPS, afin que vous puissiez découvrir ce que vos utilisateurs ressentent concernant les produits Microsoft 365. Les étiquettes de sentiment telles que **Positive**, **Negative** et **Other** sont affectées aux commentaires détaillés NPS.

:::image type="content" source="../media/product-feedback-nps-verbatims.png" alt-text="Capture d’écran : Tableau de bord de commentaires sur les produits sous l’onglet Insights des enquêtes NPS":::

Avec la fonctionnalité sentiment dans le tableau de bord des insights d’enquête NPS, vous pouvez :

- Visualisez la tendance des sentiments au cours des 12 derniers mois en fonction des commentaires détaillés NPS.

- Identifiez le sentiment par application et plateforme.

Trois sentiments sont disponibles :

:::image type="content" source="../media/sentiment-examples.png" alt-text="Capture d’écran : Exemples et descriptions de sentiments":::

Pour vous offrir une meilleure expérience à l’aide du tableau de bord d’insights d’enquête NPS, nous vous suggérons de vérifier les éléments suivants :

- Encouragez vos utilisateurs à envoyer des commentaires.

- Vérifiez que [les stratégies d’enquête dans le produit](https://config.office.com) sont activées.

- Améliorez le diagnostic en activant [Rapport d'erreurs Windows](/windows/win32/wer/windows-error-reporting).

> [!NOTE]
> Si vous êtes un client d’entreprise et que vous souhaitez participer à nos sessions de conception, envoyez-nous un e-mail à l’adresse suivante : prosight@microsoft.com

### <a name="microsoft-365-admin-center-search"></a>recherche Centre d'administration Microsoft 365

Vous pouvez maintenant afficher tous les résultats de la recherche dans une page de navigateur distincte en effectuant une recherche dans recherche globale et en sélectionnant **Entrée**.

Avec notre nouvelle page distincte de résultats de recherche, vous pouvez explorer une liste plus complète des résultats et revenir facilement à la page du navigateur pour une expérience de recherche plus efficace.

:::image type="content" source="../media/whats-new-search-page.png" alt-text="Capture d’écran : Nouvelle page de recherche de navigateur Centre d'administration Microsoft 365":::

### <a name="search-in-distribution-lists-to-add-priority-accounts"></a>Rechercher dans les listes de distribution pour ajouter des comptes prioritaires

Auparavant, vous ne pouviez marquer les comptes de priorité qu’en les recherchant à l’aide du nom de la personne, de l’adresse de messagerie ou du titre du travail. Avec cette mise à jour, vous pouvez désormais rechercher des personnes à ajouter aux comptes prioritaires dans une liste de distribution. Cela vous permet d’ajouter des personnes en bloc de manière efficace et réduit le temps nécessaire pour marquer des personnes individuelles dans votre organisation.

:::image type="content" source="../media/search-by-distribution-list-priority-accounts.png" alt-text="Capture d’écran : Rechercher des comptes prioritaires à ajouter à l’aide d’une liste de distribution":::

- Vous pouvez marquer jusqu’à 50 utilisateurs d’une liste de distribution en tant que comptes prioritaires en une seule action.

- Des informations supplémentaires sur l’utilisateur, telles que le service et le titre du travail, ont été introduites sur la page Comptes prioritaires.

- Vous pouvez uniquement baliser les comptes d’utilisateur dans les listes de distribution, et non la liste elle-même. Les utilisateurs qui ont déjà été marqués ne s’affichent pas dans votre recherche de liste de distribution.

## <a name="march-2022"></a>Mars 2022

### <a name="microsoft-365-lighthouse-ga"></a>Microsoft 365 Lighthouse GA

Les petites et moyennes entreprises s’appuient souvent sur des partenaires informatiques approuvés pour gérer leurs environnements informatiques. Nous faciliteons la sécurisation des clients à grande échelle par les partenaires grâce à la disponibilité générale de [Microsoft 365 Lighthouse](https://aka.ms/March1SMBPartnerBlog), un portail d’administration multilocataire pour les fournisseurs de services gérés (MSP). Microsoft 365 Lighthouse offre une expérience complète aux clients en permettant à leurs partenaires d’identifier et d’agir rapidement contre les menaces, les connexions anormales et les alertes de conformité des appareils pour les protéger.

:::image type="content" source="../media/lighthouse.png" alt-text="Capture d’écran : tableau de bord Microsoft 365 Lighthouse":::

Microsoft 365 Lighthouse est un service partenaire informatique uniquement, et il est disponible pour les partenaires inscrits au programme Fournisseur de solutions Cloud (CSP) et gérant des clients qui ont jusqu’à 1 000 utilisateurs sous licence avec Microsoft 365 Business Premium, Microsoft 365 E3 ou Microsoft Defender pour entreprises abonnements (en préversion). Si vous êtes un partenaire informatique inscrit au programme Fournisseur de solutions Cloud Microsoft, Microsoft 365 Lighthouse est disponible gratuitement pour votre organisation et est conçu pour aider votre entreprise à évoluer et à croître. Pour plus d’informations, consultez la [bibliothèque d’aide Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-overview.md).

Pour commencer à utiliser Microsoft 365 Lighthouse, consultez [S’inscrire à Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-sign-up.md). Pour en savoir plus sur Microsoft 365 Lighthouse, Defender Entreprise et Microsoft 365 Business Premium, [rejoignez-nous pour notre série de webinaires partenaires](https://aka.ms/M365MDBSeries).

## <a name="february-2022"></a>Février 2022

### <a name="net-promoter-score-nps-survey-insights"></a>Aperçus de l’enquête NPS (Net Promoter Score)

Vous pouvez désormais afficher les données d’enquête NPS et les insights de vos utilisateurs dans le Centre d'administration Microsoft 365. Avec cette nouvelle fonctionnalité, vous pouvez obtenir des insights exploitables à partir des réponses d’enquête NPS de vos utilisateurs finaux et obtenir un plus grand plaisir des utilisateurs finaux en traitant les problèmes et les préoccupations.

Dans le Centre d’administration, **accédez aux** > **insights d’enquête NPS** **de commentaires sur les produits** >  d’intégrité.

:::image type="content" source="../media/feedback-whatsnew.png" alt-text="Capture d’écran : affichage de la page Commentaires dans le Centre d'administration Microsoft 365":::

Nous avons identifié les thèmes courants des commentaires des utilisateurs. Ensuite, nous avons utilisé des techniques de modèles Machine Learning pour entraîner les jeux de données et organiser automatiquement les commentaires en rubriques principales.

Neuf rubriques sont disponibles. Recherchez d’autres rubriques dans les futures mises à jour.

:::image type="content" source="../media/feedback-nine-topics.png" alt-text="Capture d’écran : Affichage des 9 nouvelles rubriques de commentaires":::

Le tableau de bord d’insight d’enquête NPS contient également les trois nouveaux rapports et tableaux croisés dynamiques suivants :

- Volume de tendanceS NPS mensuel pour les 12 derniers mois
- Capable d’identifier les passifs, les promoteurs et les opposants
- Volume NPS par plateforme et application

Pour vous offrir une meilleure expérience à l’aide du tableau de bord d’insights d’enquête NPS :

- Encourager vos utilisateurs finaux à envoyer des commentaires
- Vérifier que les stratégies d’enquête dans le produit sont activées
- Améliorer le diagnostic en activant Rapport d'erreurs Windows

Pour en savoir plus, consultez [les commentaires et insights NPS du produit Microsoft pour votre organisation](manage/manage-feedback-product-insights.md).  

> [!NOTE]
> Si vous souhaitez participer à nos sessions de conception, envoyez-nous un e-mail à l’adresse suivante : prosight@microsoft.com

### <a name="microsoft-365-admin-center-video-training"></a>formation vidéo Centre d'administration Microsoft 365

Nous avons mis à jour notre formation vidéo Centre d'administration Microsoft 365. Accédez à la page [Administration bibliothèque de vidéos de formation](https://go.microsoft.com/fwlink/?linkid=2197659) pour découvrir comment configurer et gérer Microsoft 365 pour votre entreprise.

:::image type="content" source="../media/admin-library-vid-training.png" alt-text="Capture d’écran : Affichage de la bibliothèque de formation vidéo du Centre d’administration":::

## <a name="july-2021"></a>Juillet 2021

### <a name="microsoft-365-admin-center-search"></a>recherche Centre d'administration Microsoft 365

Vous pouvez maintenant rechercher des ID d’incident dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2091030" target="_blank">Centre d'administration Microsoft 365</a>. Vous pouvez en savoir plus sur les incidents actuels via les médias sociaux, les publications du secteur ou d’autres administrateurs. Vous pouvez maintenant accéder au Centre d’administration pour rechercher plus de détails sur l’incident et comprendre l’impact sur votre organisation. Recherchez simplement l’ID d’incident dans le centre d’administration.

:::image type="content" source="../media/incident-id.png" alt-text="Capture d’écran : Recherche de l’ID d’incident dans le Centre d’administration":::

### <a name="support-ticket-insight-for-premier-organizations"></a>Informations sur les tickets de support pour les organisations Premier

Nous avons ajouté 2 graphiques appelés **Tendance du volume** et **Tendance du volume par produit** pour vous fournir des insights visuels sur votre volume de support.

Le graphique en courbes sous l’onglet **Tendance du volume** met en évidence la tendance si les cas de support augmentent ou diminuent pour votre organisation d’un mois à l’autre. Vous pouvez pointer sur le graphique pour vérifier le nombre de cas de support créés chaque mois.

:::image type="content" source="../media/SuppInsight-voltrnd.PNG" alt-text="Capture d’écran : Graphique qui met en évidence la tendance si les cas de support augmentent ou diminuent pour votre organisation mois après mois":::

La **tendance du volume par graphique produit** affiche les 3 premiers produits de chaque mois avec les cas de support les plus élevés. Nous avons activé le filtrage dans la table et vous pouvez désormais filtrer les résultats par **produit**, **gravité** et **date**.

:::image type="content" source="../media/SuppInsight-voltrndproduct.PNG" alt-text="Capture d’écran : Graph affiche les 3 premiers produits de chaque mois avec les cas de support les plus élevés":::

Nous avons également ajouté 2 nouveaux champs, **Gravité** et **Date de fermeture** dans la table **Afficher la demande de service** pour vous donner plus d’informations sur vos tickets.

:::image type="content" source="../media/SuppInsight-date-sev.PNG" alt-text="Capture d’écran : Tableau qui montre le tri des tickets de prise en charge par gravité et date.":::

Pour consulter ces mises à jour dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2166757" target="_blank">Centre d'administration Microsoft 365</a>, accédez à **Support** > **View Service requests** in left navigation pane.

## <a name="june-2021"></a>Juin 2021

### <a name="microsoft-365-admin-center-search"></a>recherche Centre d'administration Microsoft 365

Nous avons ajouté deux nouvelles catégories à la fonctionnalité de recherche.

- Vous pouvez désormais rechercher des rôles d’administrateur Microsoft 365 dans recherche globale et afficher et gérer rapidement les attributions de rôles à partir de n’importe quelle page. Par exemple, recherchez **Intune administrateur**.

- Vous pouvez désormais trouver des expériences d’installation simplifiées via recherche globale. Cela peut vous aider, vous et votre équipe, à prendre rapidement en main l’utilisation de nouvelles fonctionnalités. Par exemple, recherchez **le mot de passe défini pour ne jamais expirer**.

Pour en savoir plus sur la recherche dans le Centre d’administration, consultez [Rechercher dans le Centre d'administration Microsoft 365](manage/search-in-the-mac.md).
