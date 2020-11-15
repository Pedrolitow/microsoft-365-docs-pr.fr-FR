---
title: Utilisation de la protection contre la perte de données de point de terminaison
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Découvrez comment configurer les stratégies de protection contre la perte de données (DLP) pour utiliser les emplacements de protection contre la perte de données de point de terminaison (EPDLP) Microsoft 365.
ms.openlocfilehash: 64cdfeab4b527dd3b84e7586d1419e5bf8b383df
ms.sourcegitcommit: fcc1b40732f28f075d95faffc1655473e262dd95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2020
ms.locfileid: "49073103"
---
# <a name="using-endpoint-data-loss-prevention"></a>Utilisation de la protection contre la perte de données de point de terminaison

Cet article décrit trois scénarios dans lesquels vous créez et modifiez une stratégie DLP qui utilise des appareils comme emplacements.

## <a name="dlp-settings"></a>Paramètres DLP

Avant de commencer, vous devez configurer vos paramètres DLP appliqués à toutes les stratégies DLP pour les appareils. Vous devez les configurer si vous envisagez de créer des stratégies qui appliquent :

- des restrictions de sortie dans le cloud
- restrictions relatives aux applications non autorisées

Ou

- Si vous souhaitez exclure l’analyse des chemins d’accès aux fichiers bruyants

  > [!div class="mx-imgBorder"]
  > ![Paramètres DLP](../media/endpoint-dlp-1-using-dlp-settings.png)

### <a name="file-path-exclusions"></a>Exclusions de chemin d’accès de fichier

Vous souhaiterez peut-être exclure certains chemins d’accès de la surveillance DLP, des alertes DLP et de l’application de la stratégie DLP sur vos appareils, car ils sont trop brouillons ou ne contiennent pas de fichiers intéressants. Les fichiers situés à ces emplacements ne seront pas audités et les fichiers qui sont créés ou modifiés dans ces emplacements ne seront pas soumis à l’application de la stratégie DLP. Vous pouvez configurer des exclusions de chemin d’accès dans les paramètres DLP.

Vous pouvez utiliser cette logique pour construire vos chemins d’exclusion :

- Chemin d’accès de fichier valide se terminant par « \ », ce qui signifie uniquement les fichiers directement sous dossier. <br/>Par exemple: C:\Temp\

- Chemin d’accès de fichier valide se terminant par « \* », ce qui signifie uniquement les sous-dossiers directement sous dossier. <br/>Par exemple: C:\Temp\*

- Chemin d’accès de fichier valide se terminant par « \ » ou «\*», ce qui signifie uniquement les fichiers directement sous dossier et tous les sous-dossiers. <br/>Par exemple: C:\Temp

- Un chemin d’accès avec un caractère générique entre' \ 'de chaque côté. <br/>Par exemple : C:\Users\*\Desktop\

- Un chemin d’accès comportant le caractère générique entre « \» de chaque côté et «(nombre)» pour indiquer le nombre exact de sous-dossiers. <br/>Par exemple : C:\Users\*(1) \Downloads\

- Un chemin d’accès avec des variables d’environnement système. <br/>Par exemple :%SystemDrive%\Test\*

- Un mélange de tous les éléments ci-dessus. <br/>Par exemple :%SystemDrive%\Users\*\Documents\*(2) \Sub\

### <a name="service-domains"></a>Domaines de service

Vous pouvez ajouter à cette liste des domaines auxquels Edge Chromium fera référence lors de l’application de la restriction d’accès au téléchargement de la stratégie DLP pour point de terminaison. 

Si le mode liste est défini sur **Bloquer** , l’utilisateur ne pourra pas télécharger les éléments sensibles vers ces domaines. Lorsqu’une action de téléchargement est bloquée car un élément correspond à une stratégie DLP, DLP génère un avertissement ou bloque le téléchargement de l’élément sensible.

Si le mode de liste est paramétré sur **Autoriser** , les utilisateurs pourront charger des éléments sensibles * *_uniquement_* dans ces domaines, et l’accès de chargement à tous les autres domaines n’est pas autorisé.

### <a name="unallowed-apps"></a>Applications non autorisées

Lorsque le paramètre _ *Accès par des applications et navigateurs non autorisés* * d’une stratégie est activé et que les utilisateurs tentent d’utiliser ces applications pour accéder à un fichier protégé, l’activité est autorisée, bloquée ou bloquée, mais les utilisateurs peuvent ignorer la restriction. Toutes les activités sont auditées et peuvent être consultées dans l’explorateur d’activités.

### <a name="unallowed-browsers"></a>Navigateurs non autorisés

Vous ajoutez des navigateurs, identifiés par leurs noms de fichiers exécutables, qui ne pourront pas accéder aux fichiers qui correspondent aux conditions d’une stratégie DLP appliquée dans laquelle la restriction de téléchargement vers les services cloud est définie sur bloquer ou bloquer le remplacement. Lorsque ces navigateurs ne peuvent pas accéder à un fichier, les utilisateurs finaux verront une notification toast leur demandant d’ouvrir le fichier via Edge Chromium.

[!IMPORTANT]
N’incluez pas le chemin d’accès du fichier exécutable, mais uniquement le nom du fichier exécutable (par exemple, browser.exe).

## <a name="tying-dlp-settings-together"></a>Lier les paramètres DLP

Avec le navigateur web Edge Chromium et la DLP pour point de terminaison, vous pouvez limiter le partage involontaire d’éléments sensibles aux applications et services cloud non autorisés. Edge Chromium comprend quand un élément est restreint par une stratégie DLP pour point de terminaison et applique des restrictions d’accès.

Lorsque vous utilisez DLP pour point de terminaison comme emplacement dans une stratégie DLP correctement configurée et le navigateur Edge Chromium, les navigateurs non autorisés que vous avez définis dans ces paramètres ne pourront pas accéder aux éléments sensibles qui correspondent à vos contrôles de stratégie DLP. Les utilisateurs seront plutôt redirigés pour utiliser Edge Chromium qui, avec sa compréhension des restrictions imposées par DLP, peut bloquer ou restreindre les activités lorsque les conditions de la stratégie DLP sont remplies.

Pour utiliser cette restriction, vous devez configurer trois éléments importants :

1. Spécifier les emplacements ,services, domaines, adresses IP, avec lesquels vous ne souhaitez pas partager les éléments sensibles.

2. Ajouter les navigateurs qui ne sont pas autorisés à accéder à certains éléments sensibles lorsqu’une correspondance de la stratégie DLP se produit.

3. Configurez les stratégies DLP pour définir les types d’éléments sensibles pour lesquels le téléchargement doit être limité à ces emplacements en activant **Télécharger vers les services Cloud** et **Accès à partir d’un navigateur non autorisé**.

Vous pouvez continuer à ajouter de nouveaux services, applications et stratégies pour développer et augmenter vos restrictions afin de répondre aux besoins de votre entreprise et de protéger les données sensibles. 

Cette configuration vous permet de garantir la sécurité de vos données tout en évitant les restrictions inutiles qui empêchent les utilisateurs d’accéder aux éléments non sensibles et de les empêcher de les partager.

## <a name="endpoint-dlp-policy-scenarios"></a>Scénarios de stratégie DLP pour point de terminaison

Pour vous aider à vous familiariser avec les fonctionnalités DLP pour point de terminaison et la manière dont elles apparaissent dans les stratégies DLP, nous avons rassemblé quelques scénarios à suivre. Tout le contenu DLP pour point de terminaison sera intégré à l’ensemble de contenu DLP principal lorsque DLP pour point de terminaison sera disponible pour le grand public.

> [!IMPORTANT]
> Ces scénarios DLP pour point de terminaison ne sont pas les procédures officielles de création et de configuration des stratégies DLP. Reportez-vous aux rubriques ci-dessous lorsque vous devez travailler avec des stratégies DLP dans des situations générales :
>- [Vue d’ensemble de la protection contre la perte de données](data-loss-prevention-policies.md)
>- [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)
>- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
>- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)

### <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scénario 1 : créer une stratégie à partir d’un modèle, audit uniquement

Ces scénarios nécessitent que vous ayez déjà des appareils intégrés et des rapports dans l’explorateur d’activité. Si vous n’avez pas encore intégré d’appareils, consultez l’article [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md).

1. Ouvrir la [page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez **Créer une stratégie**.

3. Dans le cadre de ce scénario, sélectionnez **Confidentialité** , **Données d’informations d’identification personnelles pour les États-Unis** puis, **Suivant**.

4. Désactivez le champ **État** pour tous les emplacements, à l’exception de **Appareils**. Sélectionnez **Suivant**.

5. Acceptez la sélection par défaut **Vérifier et personnaliser les paramètres du modèle** , puis sélectionnez **Suivant**.

6. Acceptez les valeurs par défaut **Actions de protection** et sélectionnez **Suivant**.

7. Sélectionnez **Auditer ou restreindre les activités sur les appareils Windows** et laissez les actions définies sur **Audit uniquement**. Sélectionnez **Suivant**.

8. Acceptez la valeur par défaut, **Je veux d’abord tester** et sélectionnez **Afficher les conseils de stratégie en mode de test**. Sélectionnez **Suivant**.

9. Vérifiez vos paramètres, puis sélectionnez **Envoyer**.

10. La nouvelle stratégie DLP s’affiche dans la liste des stratégies.

11. Recherchez dans l’explorateur d’activité les données des points de terminaison surveillés. Définissez le filtre d’emplacement pour les appareils et ajoutez la stratégie. Ensuite, filtrez par nom de stratégie pour voir l’impact de cette stratégie. Consultez l’article [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md) si nécessaire.

12. Tenter de partager un test qui contient un contenu qui déclenchera la condition des données des informations personnelles identifiables pour les États-Unis avec une personne extérieure à votre organisation. Cela devrait déclencher la stratégie.

13. Consultez l’Explorateur d’activités pour l’événement.

### <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Scénario 2 : modifier la stratégie existante, créer une alerte

1. Ouvrir[Page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez la stratégie **Données d’informations d’identification personnelle pour les États-Unis** que vous avez créée dans le scénario 1.

3. Sélectionnez **Modifier la stratégie**.

4. Accédez à la page **Règles DLP avancées** et modifiez la **Faible quantité de contenu détectée pour les informations d’identification personnelle**.

5. Faites défiler jusqu’à la section **Rapports d’incident** et définissez **Envoyer une alerte aux administrateurs lorsqu’une correspondance de règle se produit** sur **Activé**. Les alertes par e-mail seront automatiquement envoyées à l’administrateur et aux autres personnes que vous ajoutez à la liste des destinataires. 

   > [!div class="mx-imgBorder"]
   > ![activer les rapports d’incident](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. Dans le cadre de ce scénario, sélectionnez **Envoyer une alerte chaque fois qu’une activité correspond à la règle**.

7. Cliquez sur **Enregistrer**.

8. Conservez tous vos paramètres précédents en choisissant **suivant** puis **Envoyez** les modifications apportées à la stratégie.

9. Tenter de partager un test qui contient un contenu qui déclenchera la condition des données des informations personnelles identifiables pour les États-Unis avec une personne extérieure à votre organisation. Cela devrait déclencher la stratégie.

10. Consultez l’Explorateur d’activités pour l’événement.

### <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Scénario 3 : modifier la stratégie existante, bloquer l’action avec l’option autoriser le remplacement

1. Ouvrir[Page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez la stratégie **Données d’informations d’identification personnelle pour les États-Unis** que vous avez créée dans le scénario 1.

3. Sélectionnez **Modifier la stratégie**.

4. Accédez à la page **Règles DLP avancées** et modifiez la **Faible quantité de contenu détectée pour les informations d’identification personnelle**.

5. Faites défiler vers le bas jusqu’à la section **Audit ou restreindre les activités sur les appareils Windows** et pour chaque activité définissez l’action correspondante sur **Bloquer avec remplacement**.

   > [!div class="mx-imgBorder"]
   > ![définir un blocage avec une action de remplacement](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. Cliquez sur **Enregistrer**.

7. Répétez les étapes 4-7 pour **Quantité de contenu élevé détectée le fichier INF (INF) US**.

8. Conservez tous vos paramètres précédents en choisissant **suivant** puis **Envoyez** les modifications apportées à la stratégie.

9. Tenter de partager un test qui contient un contenu qui déclenchera la condition des données des informations personnelles identifiables pour les États-Unis avec une personne extérieure à votre organisation. Cela devrait déclencher la stratégie.

   Une fenêtre contextuelle semblable à celle-ci s’affiche sur l’appareil client :

   > [!div class="mx-imgBorder"]
   > ![blocage de la notification de remplacement par le client dlp de point de terminaison](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Consultez l’Explorateur d’activités pour l’événement.

## <a name="see-also"></a>Voir aussi

- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
- [Prise en main la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)
- [Vue d’ensemble de la protection contre la perte de données](data-loss-prevention-policies.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/)
- [Outils et méthodes d’intégration pour les appareils Windows 10](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).
- [Abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (ADD) adhésion](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-ad-join)
- [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
