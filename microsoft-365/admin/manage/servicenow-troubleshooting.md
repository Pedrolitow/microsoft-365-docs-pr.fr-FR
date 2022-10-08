---
title: Résoudre les problèmes d’intégration de la prise en charge Microsoft 365 avec ServiceNow
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide de configuration et d’installation d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: 66cab6fe21f39b4db2207d78b8b0b1239df2b0d1
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68208389"
---
# <a name="troubleshooting-microsoft-365-support-integration-with-servicenow"></a>Résoudre les problèmes d’intégration de la prise en charge Microsoft 365 avec ServiceNow

| \#  | Problème  | Action de diagnostic     |
|-----|--------------------------------|----------------------|
| 1   | Impossible de voir l’onglet **Support Microsoft 365**                                                                                                                                                                                    | Vérifier l’affichage actuel et **les** &gt; journaux système **avec** filter x\_mioms\_m365\_assit                        |
| 2   | Sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et lui demander d’effectuer les étapes de configuration de l’application ».                                                                      | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 3   | Sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et lui demander de terminer l’étape de configuration finale de l’application ».                                                                | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 4   | Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et lui demander d’effectuer les étapes de configuration de l’application ».                                   | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 5   | Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et lui demander de terminer l’étape de configuration finale de l’application ».                                 | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 6   | Sélectionnez **Contacter le support Microsoft**, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et lui demander d’effectuer les étapes de configuration de l’application ».                                                                       | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 7    | Sélectionnez **Contacter le support Microsoft**, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et lui demander de terminer l’étape de configuration finale de l’application ».                                                                 | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 8    | Sélectionnez **Contacter le support Microsoft** , mais obtenez l’erreur « {EmailAddress} n’est pas un compte d’administrateur Microsoft 365 valide. Vous avez besoin de privilèges d’administrateur Microsoft 365 pour ouvrir une demande de service. Dans l’application, liez le compte d’administrateur. » | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 9    | Sélectionner **les solutions recommandées par Microsoft** , mais rien ne s’affiche                                                                                                                                                            | Vérifier **les journaux système – Journaux HTTP sortants** avec login.microsoftonline.com de filtre et connector.rave.microsoft.com |
| 10  | Sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter le support de l’application ».                                                                                                                                     | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 11  | Problème de type dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais rien ne s’affiche                                                                                                                             | Vérifier **les journaux système – Journaux HTTP sortants** avec login.microsoftonline.com de filtre et connector.rave.microsoft.com |
| 12   | Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter le support de l’application ».                                                                                                      | Vérifier le message d’erreur au-dessus du formulaire et **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit     |
| 13  | L’utilisateur sélectionne **Contacter le support Microsoft**, mais rien ne se passe                                                                                                                                                            | Vérifier **les journaux système – Journaux HTTP sortants** avec login.microsoftonline.com de filtre et connector.rave.microsoft.com |
| 14  | Impossible de voir la solution recommandée par Microsoft après la réouverture de l’incident                                                                                                                                                      | Vérifier les **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit                                              |
| 15  | Impossible de voir les cas Microsoft lors de la réouverture de l’incident qui a été transféré au support Microsoft                                                                                                                            | Vérifier les **journaux** &gt; système **tous** avec filtre x\_mioms\_m365\_assit                                              |
| 16  | Impossible d’enregistrer les détails du ticket, obtenez l’erreur « Impossible d’enregistrer les détails du ticket. Veuillez contacter le support de l’application. »                                                                                                                          | Vérifier le message d’erreur au-dessus du formulaire                                                                            |
