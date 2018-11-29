---
title: Protéger les documents d’entreprise exécutant des compléments Microsoft Office - Microsoft 365 entreprise | Documents Microsoft
description: Décrit comment utiliser les travaux en cours et Intune pour protéger les données d’entreprise dans les documents en cours d’exécution des compléments Office.
author: barlanmsft
manager: angrobe
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/14/2017
ms.author: barlan
ms.reviewer: jsnow
ms.custom: it-pro
ms.openlocfilehash: 6871f288a7e5849b147cbf0aedb056f84575f376
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867133"
---
# <a name="use-wip-and-intune-to-protect-enterprise-data-in-documents-running-office-add-ins"></a>Utiliser la Protection des informations Windows et Intune pour protéger les données d’entreprise dans des documents en exécutant des compléments Office
Quand les utilisateurs d’une organisation utilisent des compléments Office pour interagir avec les données de l’organisation, ceci introduit un risque potentiel de divulgation de certaines données. Vous pouvez utiliser la Protection des informations Windows et Microsoft Intune pour protéger les données d’entreprise quand des utilisateurs exécutent des compléments Office.

La [Protection des informations Windows](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip), précédemment appelée « Protection des données d’entreprise », permet aux entreprises de protéger les droits de propriété intellectuelle et les données d’entreprise. La Protection des informations Windows permet de protéger les données et les applications d’entreprise contre des fuites accidentelles de données sur les appareils d’entreprise et les appareils personnels que les employés amènent sur leur lieu de travail, sans que cela entraîne nécessairement une modification de votre environnement ou d’autres applications.

[Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) offre un ensemble diversifié d’outils pour gérer votre environnement mobile complexe. La combinaison des options de gestion des applications mobiles et de gestion des appareils mobiles d’Intune donne aux administrateurs informatiques et aux utilisateurs finaux la flexibilité nécessaire pour gérer et sécuriser la productivité mobile.

Vous pouvez utiliser Intune pour [créer et déployer votre stratégie de Protection des informations Windows](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/overview-create-wip-policy). Avec Intune, vous pouvez choisir vos applications protégées et le niveau de protection de la Protection des informations Windows, et trouver des données d’entreprise sur le réseau.

Avec la Protection des informations Windows et Intune :

-   Les entreprises peuvent appliquer une stratégie raisonnable aux données d’entreprise, même quand les données sont téléchargées sur des appareils personnels.

-   Les entreprises peuvent utiliser des fonctionnalités permettant d’expliquer de façon contextuelle les stratégies aux utilisateurs, pour les informer sur la façon de se protéger contre la divulgation accidentelle de données via des applications et des services non gérés.

-   Les utilisateurs finaux peuvent se conformer aux stratégies de données d’entreprise sans introduire de rupture dans leur flux de travail habituel.

-   Les utilisateurs finaux peuvent passer sans heurts entre leur productivité professionnelle et personnelle.

La Protection des informations Windows et Intune s’exécutent en mode silencieux en arrière-plan et sont pratiquement invisibles quand les utilisateurs ne mélangent pas le contenu personnel et le contenu d’entreprise.

Les [compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins) s’appuient sur des technologies web. Ils apportent la puissance et les informations provenant du web aux applications Office. Les compléments interagissent avec le contenu d’une application Office via les API disponibles dans Office.js. Les principes de base des compléments Office sont :

-   **Sécurité** : l’architecture de la plateforme JavaScript Office garantit que le code du complément est placé dans un bac à sable et qu’il s’exécute dans un processus distinct de celui de l’application Office hôte. Ainsi, la plateforme peut entreprendre une action corrective quand un complément ne répond pas aux standards en matière de performances ou s’il est potentiellement malveillant, en avertissant l’utilisateur et, dans certains cas, en désactivant le complément. Cette architecture fonctionne sur toutes les plateformes qui prennent en charge les compléments Office.

-   **Résilience** : la nature « hors processus » de la plateforme du complément garantit que le complément lui-même n’affecte pas l’expérience utilisateur ou les performances de l’application Office hôte. Ceci est essentiel pour qu’Office reste rapide et réactif aux actions de l’utilisateur.

-   **Multiplateforme** : écrit une seule fois, mais exécuté partout où Office fonctionne. Les compléments sont actuellement pris en charge sur Windows, Office Online, Mac et iPad. La prise en charge des compléments sur la plateforme Android et Universal sera bientôt disponible.

Les compléments Office peuvent fonctionner avec du contenu d’entreprise et potentiellement sensible dans un document. Dans le cadre de l’extensibilité des applications, les compléments héritent leur accès de la stratégie d’application hôte. Par exemple, si les paramètres de la Protection des informations Windows empêchent Word d’accéder à du contenu d’entreprise, les compléments ne pourront pas non plus accéder au contenu d’entreprise d’un document Word.

Un des objectifs pour les compléments est de supprimer tout problème bloquant pour les utilisateurs finaux, tout en garantissant que les administrateurs d’entreprise peuvent bloquer les compléments si nécessaire. Les principes fondamentaux des compléments Office concernant l’activation de la protection données sont :

-   Fournir un moyen aux administrateurs informatiques de bloquer le chargement des compléments.

-   Réduire ou éliminer le travail des administrateurs nécessaire à la préparation des compléments pour l’entreprise.

-   Réduire les invites et les messages aux utilisateurs finaux lors de l’utilisation des compléments.

-   Éliminer les invites pour les utilisateurs finaux quand le document et le complément ont le même contexte.

## <a name="add-ins-and-wip"></a>Compléments et Protection des informations Windows

Quand vous activez la Protection des informations Windows (WIP, Windows Information Protection) dans votre environnement, les scénarios suivants sont possibles pour vos compléments Office :

-   Les compléments Office sont activés avec le contexte du document. Pour Outlook, le contexte pour le complément est basé sur la boîte aux lettres active. Les autorisations des compléments sont clairement définies dans l’invite d’approbation avant l’activation du complément. L’utilisateur décide si le complément est approprié dans un document spécifique et s’il faut autoriser l’exécution du complément.

-   Les administrateurs peuvent utiliser la stratégie de groupe pour bloquer tous les compléments Office Store ou tous les compléments Office. Ceci signifie que les utilisateurs peuvent activer seulement les compléments approuvés d’un [catalogue d’entreprise SharePoint ou Office 365](https://dev.office.com/docs/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog).

-   Les administrateurs peuvent bloquer les compléments au niveau du pare-feu à l’aide de la gestion des appareils mobiles (MDM). Notez que ceci ne fonctionne pas pour les scénarios mobiles ou BYOD (Bring Your Own Device).

-   Les compléments appliquent l’opération de copier-coller entre le contexte d’entreprise et le contexte personnel. Par exemple, quand un utilisateur copie du contenu depuis un complément de contexte de l’entreprise et le colle dans un document personnel, l’invite par défaut du copier-coller entre contextes s’affiche.

Le tableau suivant répertorie les comportements attendus des compléments dans les contextes et les documents d’entreprise et personnels quand la Protection des informations Windows est activée.

> [!NOTE]
> - Les opérations de couper, copier et coller au sein de et à l’extérieur de l’application hôte fonctionnent comme attendu dans tous les scénarios.
> - Le transfert de données à des services de compléments n’est protégé dans aucun scénario.

|**Type de document ou de boîte aux lettres**|**Complément dans un contexte personnel**|**Complément dans un contexte d’entreprise**|
|:----------------|:-------------------------------------------------|:---------------------------------------------------|
|**Personnel**     |Le complément se charge dans un contexte personnel.<br><br>La navigation vers les URL de l’entreprise n’est pas autorisée (même si elles sont dans son propre domaine d’application).<br><br>La navigation vers les URL personnelles est autorisée.|Le chargement ou l’activation du complément échoue.<br><br>Si le contexte du document est élevé (par exemple s’il est enregistré à un emplacement d’entreprise) :<br><br>- La navigation vers les URL d’entreprise est autorisée.<br><br>- La navigation vers les URL personnelles est autorisée.|
|**Entreprise**   |Le complément se charge dans un contexte d’entreprise.<br><br>La navigation vers les URL d’entreprise est autorisée.<br><br>La navigation vers les URL personnelles est autorisée.|Le complément se charge dans un contexte d’entreprise.<br><br>La navigation vers les URL d’entreprise est autorisée.<br><br>La navigation vers les URL personnelles est autorisée.|
|**Non enregistré**      |Le complément se charge dans un contexte personnel.<br><br>La navigation vers les URL de l’entreprise n’est pas autorisée (même si elles sont dans son propre domaine d’application).<br><br>La navigation vers les URL personnelles est autorisée.|Le complément se charge dans le contexte d’entreprise, et le document est converti en mode silencieux au contexte d’entreprise. Cela signifie que le document doit être enregistré à un emplacement d’entreprise.<br><br>La navigation vers les URL d’entreprise est autorisée. La navigation vers les URL personnelles est autorisée.            |


## <a name="add-ins-and-intune"></a>Compléments et Intune

Sur Office pour iPad, les compléments Office sont actuellement pris en charge pour Word, Excel et PowerPoint. Outlook prend actuellement en charge les compléments sur iOS (iPad et iPhone). Les administrateurs Outlook peuvent désactiver les compléments par défaut, notamment les compléments installés par les développeurs, et activer seulement les compléments spécifiques approuvés par leur organisation. Le tableau suivant décrit la prise en charge des scénarios de protection des données pour les compléments s’exécutant sur Office pour les appareils iOS qui utilisent les outils de protection des applications d’Intune.

> [!NOTE]
> Pour plus d’informations sur les compléments Outlook s’exécutant sur les appareils Android et iOS, consultez [Gérer l’accès des utilisateurs aux compléments pour Outlook](https://technet.microsoft.com/library/jj943757(v=exchg.150).aspx) et [Compléments pour Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).

|**Type de document ou de boîte aux lettres**|**Compléments dans un contexte personnel pour iOS avec Intune App Protection<sup>*</sup>**|**Compléments dans un contexte d’entreprise pour iOS avec Intune App Protection<sup>*</sup>**|
|:-----|:-----|:-----|
|**Personnel**|L’utilisation des compléments n’est pas affectée par la protection d’application Intune dans vos documents personnels.|L’utilisation des compléments n’est pas affectée par la protection d’application Intune dans vos documents personnels.|
|**Entreprise**|L’activation des compléments personnels est autorisée.<br><br>Les stratégies de protection des applications Intune peuvent protéger les scénarios des opérations couper, copier, coller et transférer des données entre le complément et d’autres applications sur l’appareil.<br><br>Le transfert de données à des services de compléments n’est pas protégé.|L’activation des compléments d’entreprise est autorisée. Les administrateurs peuvent contrôler quels compléments sont publiés via les outils de gestion Office [(Déploiement centralisé d’Office 365)](https://support.office.com/article/Deploy-Office-add-ins-in-the-Office-365-admin-center-737e8c86-be63-44d7-bf02-492fa7cd9c3f).<br><br>Les stratégies de protection des applications Intune peuvent protéger les scénarios des opérations couper, copier, coller et transférer des données entre le complément et d’autres applications sur l’appareil.<br><br>Le transfert de données à des services de compléments n’est pas protégé.|

>**<sup>*</sup>** Les administrateurs peuvent utiliser le [déploiement centralisé d’Office 365](https://support.office.com/article/Deploy-Office-add-ins-in-the-Office-365-admin-center-737e8c86-be63-44d7-bf02-492fa7cd9c3f) pour déployer des compléments Word, Excel et PowerPoint auprès d’utilisateurs individuels, de groupes, ou d’une organisation directement à partir du Centre d’administration Office 365 ou à l’aide de scripts PowerShell. Quand les utilisateurs ouvrent une application Office sur Windows, Mac ou Office Online, le complément est automatiquement installé sur leur ruban.

## <a name="summary"></a>Résumé

Étant donné les principes concernant les compléments Office, la Protection des informations Windows et Intune permettent aux administrateurs de gérer les données d’entreprise et de fournir les outils dont les utilisateurs finaux ont besoin pour effectuer leur travail. Ceci crée un risque de fuite des données d’entreprise à l’extérieur des limites de l’organisation. Les API JavaScript d’Office ne fournissent actuellement pas de moyen pour les développeurs de reconnaître le type de données transmises entre le document Office et le complément. Ceci oblige les développeurs à afficher plusieurs invites à l’utilisateur et, dans certains cas, des fichiers personnels sont marqués comme fichiers d’entreprise, ce qui peut avoir un effet négatif sur l’expérience utilisateur et ne respecte pas les principes de la protection des données.

Microsoft s’efforce de protéger les données des clients, et continuera à s’investir pour améliorer les technologies et l’expérience d’Intune et de la Protection des informations Windows pour ses clients.

## <a name="learn-more"></a>En savoir plus

-   [Conseils généraux et bonnes pratiques pour la Protection des informations Windows](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/guidance-and-best-practices-wip)

-   [Qu’est-ce qu’Intune ?](https://docs.microsoft.com/intune/introduction-intune)

-   [Présentation des méthodes d’inscription des appareils](https://docs.microsoft.com/sccm/mdm/plan-design/device-enrollment-methods)

-   [Modifier votre autorité de gestion des appareils mobiles](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority)

-   [Préparer la configuration des stratégies de protection d’application pour Windows 10](https://docs.microsoft.com/intune-classic/deploy-use/get-ready-to-configure-app-protection-policies-for-windows-10)
