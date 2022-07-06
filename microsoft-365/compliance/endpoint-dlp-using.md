---
title: Utilisation de la DLP pour point de terminaison
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Découvrez comment configurer les stratégies de protection contre la perte de données (DLP) en utilisant les emplacements de protection contre la perte de données de point de terminaison.
ms.openlocfilehash: 9107759e137d7b8dd86253f9c6567b76686d2518
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632374"
---
# <a name="using-endpoint-data-loss-prevention"></a>Utilisation de la protection contre la perte de données de point de terminaison

Pour vous familiariser avec les fonctionnalités de point de terminaison DLP et la manière dont elles se trouvent dans les stratégies DLP, nous avons rassemblé certains scénarios que vous pouvez suivre.

> [!IMPORTANT]
> Ces scénarios de points de terminaison DLP ne sont pas les procédures officielles pour la création et le réglage des stratégies DLP. Reportez-vous aux rubriques ci-dessous lorsque vous devez utiliser les stratégies DLP dans les situations générales suivantes :
>
>- [En savoir plus sur la protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md)
>- [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)
>- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
>- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)

## <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scénario 1 : créer une stratégie à partir d’un modèle, audit uniquement

Ces scénarios nécessitent que les appareils soient déjà intégrés et reportés dans l’Explorateur d’activités. Si vous n’avez pas encore intégré d’appareils, consultez l’article [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md).

1. Ouvrez la [page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez **Créer une stratégie**.

3. Dans le cadre de ce scénario, sélectionnez **Confidentialité**, **Données d’informations d’identification personnelles (PII) pour les États-Unis** puis sélectionnez **Suivant**.

4. Désactivez le champ **État** pour tous les emplacements, à l’exception de **Appareils**. Sélectionnez **Suivant**.

5. Acceptez la sélection par défaut **Vérifier et personnaliser les paramètres du modèle**, puis sélectionnez **Suivant**.

6. Acceptez les valeurs par défaut **Actions de protection** et choisissez **Suivant**.

7. Sélectionnez **Auditer ou restreindre les activités sur les appareils Windows** et laissez les actions définies sur **Audit uniquement**. Sélectionnez **Suivant**.

8. Acceptez la valeur par défaut, **Je veux d’abord tester** et sélectionnez **Afficher les conseils de stratégie en mode de test**. Sélectionnez **Suivant**.

9. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

10. La nouvelle stratégie DLP s’affiche dans la liste de stratégies.

11. Recherchez dans l’explorateur d’activité les données des points de terminaison surveillés. Définissez le filtre d’emplacement pour les appareils et ajoutez la stratégie. Ensuite, filtrez par nom de stratégie pour voir l’impact de cette stratégie ; consultez l’article [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md) si nécessaire.

12. Essayez de partager un élément de test dont le contenu déclenchera la condition relative aux données américaines d'informations personnelles identifiables (PII) avec une personne extérieure à votre organisation. Cela devrait déclencher la politique.

13. Consultez l’Explorateur d’activités pour l’événement.

## <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Scénario 2 : modifier la stratégie existante, créer une alerte

1. Ouvrir[Page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez la stratégie **Données d’informations d’identification personnelle (PII) pour les États-Unis** que vous avez créées dans le scénario 1.

3. Sélectionnez **Modifier la stratégie**.

4. Accédez à la page **Règles DLP avancées** et modifiez la **Faible quantité de contenu détectée pour les informations d’identification personnelle**.

5. Faites défiler vers le bas jusqu’à la section **Rapports d’incident** et configurez **Envoyer une alerte aux administrateurs lorsqu’une correspondance de règle se produit** sur **Activé**. Les alertes par courrier électronique sont envoyées automatiquement à l’administrateur et à toute autre personne que vous ajoutez à la liste des destinataires. 

![activer les rapports d’incident.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. Dans le cadre de ce scénario, sélectionnez **Envoyer une alerte chaque fois qu’une activité correspond à la règle**.

7. Cliquez sur **Enregistrer**.

8. Conservez tous vos paramètres précédents en choisissant **suivant** puis **Envoyer** les modifications apportées à la stratégie.

9. Essayez de partager un élément de test dont le contenu déclenchera la condition relative aux données américaines d'informations personnelles identifiables (PII) avec une personne extérieure à votre organisation. Cela devrait déclencher la politique.

10. Consultez l’Explorateur d’activités pour l’événement.

## <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Scénario 3 : modifier la stratégie existante, bloquer l’action avec l’option autoriser le remplacement

1. Ouvrir[Page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez la stratégie **Données d’informations d’identification personnelle (PII) pour les États-Unis** que vous avez créées dans le scénario 1.

3. Sélectionnez **Modifier la stratégie**.

4. Accédez à la page **Règles DLP avancées** et modifiez la **Faible quantité de contenu détectée pour les informations d’identification personnelle**.

5. Faites défiler vers le bas jusqu’à la section **Audit ou restreindre les activités sur les appareils Windows** et pour chaque activité définissez l’action correspondante sur **Bloquer avec remplacement**.

   > [!div class="mx-imgBorder"]
   > ![définir un blocage avec une action de remplacement.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. Cliquez sur **Enregistrer**.

7. Répétez les étapes 4-7 pour **Quantité de contenu élevé détectée le fichier INF (INF) US**.

8. Conservez tous vos paramètres précédents en choisissant **suivant** puis **Envoyer** les modifications apportées à la stratégie.

9. Essayez de partager un élément de test dont le contenu déclenchera la condition relative aux données américaines d'informations personnelles identifiables (PII) avec une personne extérieure à votre organisation. Cela devrait déclencher la politique.

   Une fenêtre contextuelle semblable à celle-ci s’affiche sur l’appareil client :

   > [!div class="mx-imgBorder"]
   > ![blocage de la notification de remplacement par le client dlp de point de terminaison.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Consultez l’Explorateur d’activités pour l’événement.

## <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Scénario 4 : évitez de boucler les notifications DLP à partir d’applications de synchronisation cloud avec mise en quarantaine automatique (préversion).

### <a name="before-you-begin"></a>Avant de commencer

Dans ce scénario, la synchronisation des fichiers avec l’étiquette de confidentialité **Hautement confidentiel** sur OneDrive est bloquée. Il s’agit d’un scénario complexe avec plusieurs composants et procédures. Vous aurez besoin de :

- Un compte d’utilisateur AAD à cibler et un ordinateur Windows 10 intégré qui synchronise déjà un dossier OneDrive local avec le stockage cloud OneDrive.
- Microsoft Word installé sur l’ordinateur Windows 10 cible
- Étiquettes de confidentialité configurées et publiées : consultez [Démarrer avec les étiquettes de confidentialité](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) et [Créer et configurer des étiquettes de confidentialité et leurs stratégies](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Il existe trois procédures.

1. Configurez les paramètres de mise en quarantaine automatique DLP du point de terminaison.
2. Créez une stratégie qui bloque les éléments sensibles qui ont l’étiquette de confidentialité **Hautement confidentiel** .
3. Créez un document Word sur l’appareil Windows 10 cible de la stratégie, appliquez l’étiquette et copiez-le dans le dossier OneDrive local des comptes d’utilisateurs en cours de synchronisation.  

### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Configurer l’application DLP de point de terminaison non autorisée et les paramètres de mise en quarantaine automatique

1. Ouvrir [Paramètres DLP de point de terminaison](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. Développez **Applications non autorisées**.

3. Choisissez **Ajouter ou** modifier des applications non autorisé et ajouter des *OneDrive* en tant que nom d’affichage et le nom exécutableonedrive.exepour que les *onedrive.exe* n’accèdent pas aux **éléments de l’étiquette** Hautement confidentiel.

4. Sélectionnez **Mise en quarantaine automatique** et **Enregistrer**.

5. Sous **Paramètres de mise en quarantaine automatique** choisissez **Modifier les paramètres de mise en quarantaine automatique**.

6. Activez **Mise en quarantaine automatique pour les applications non autorisées**.

7. Entrez le chemin d’accès au dossier sur les ordinateurs locaux dans lequel vous souhaitez déplacer les fichiers sensibles d’origine. Par exemple:
   
    **« %homedrive%%homepath%\Microsoft DLP\Quarantine »** pour le nom d’utilisateur *Isaiah langer* placera les éléments déplacés dans un dossier nommé :  

    *C:\Users\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive*

    et ajoutez une date et une heure au nom de fichier d’origine.
    
    > [!NOTE]
    > La mise en quarantaine automatique DLP crée des sous-dossiers pour les fichiers de chaque application non autorisée. Par conséquent, si vous avez le *Bloc-notes* et *OneDrive* dans votre liste d’applications non autorisées, un sous-dossier sera créé pour **\OneDrive** et un autre sous-dossier pour **\Bloc-notes**.

8. Choisissez **Remplacer les fichiers par un fichier .txt qui contient le texte suivant**, puis entrez le texte souhaité dans le fichier d’espace réservé. Par exemple, pour un fichier appelé *auto quar 1.docx* :
    
    > %%FileName%% contient des informations sensibles que votre organisation protège avec la stratégie de protection contre la perte de données (DLP) %%PolicyName%% et a été déplacée vers le dossier de mise en quarantaine : %%QuarantinePath%%
    
    laisse un fichier texte qui contient ce message :
    
    > auto quar 1.docx contient des informations sensibles que votre organisation protège avec la stratégie de protection contre la perte de données (DLP) et a été déplacée vers le dossier de quarantaine : C:\Users\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive\auto quar 1_20210728_151541.docx.

9. Cliquez sur **Enregistrer**.

### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Configurer une stratégie pour bloquer la synchronisation OneDrive des fichiers avec l’étiquette de confidentialité Hautement confidentiel

1. Ouvrez la [page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez **Créer une stratégie**.

3. Pour ce scénario, choisissez **Personnaliser**, puis **Stratégie personnalisée**, puis choisissez **Suivant**.

4. Renseignez les champs **Nom** et **Description**, choisissez **Suivant**.

5. Désactivez la case à cocher **État** pour tous les emplacements, sauf pour les **Appareils**. Si vous disposez d’un compte d’utilisateur final spécifique à partir duquel vous souhaitez le tester, veillez à le sélectionner dans l’étendue. Cliquez sur **Suivant**.

6. Acceptez la sélection par défaut **Créer ou personnaliser des règles DLP avancées**, puis choisissez **Suivant**.

7. Créez une règle avec les valeurs suivantes :
    1. **Nom**  >  *Scénario 4 Mise en quarantaine automatique*.
    1. **Conditions**  >  **Le contenu contient**  >  **Étiquettes de sensibilité**  >  **Hautement confidentiel**.
    1.  **Actions** > **Auditer ou restreindre les activités sur les appareils Windows** > **Accès par les applications non autorisées** > **Bloquer**. Pour les besoins de ce scénario, effacez toutes les autres activités.
    1. **Notifications de l’utilisateur**  >  **Activé**.
    1. **Périphériques de point de terminaison** > Choisissez **Afficher aux utilisateurs une notification de conseil de stratégie lorsqu’une activité** si elle n’est pas déjà activée.
    
8. Choisissez **Enregistrer** et **Suivant**.

9. Choisissez **L’activer immédiatement**. Choisissez **Suivant**.

10. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

    > [!NOTE]
    > Autorisez au moins une heure pour que la nouvelle stratégie soit répliquée et appliquée à l’ordinateur Windows 10 cible.

11. La nouvelle stratégie DLP s’affiche dans la liste des stratégies.

### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Tester la mise en quarantaine automatique sur l’appareil Windows 10

1. Connectez-vous à l’ordinateur Windows 10 avec le compte d’utilisateur que vous avez spécifié dans [Configurez une stratégie pour bloquer la synchronisation OneDrive des fichiers avec l’étiquette de confidentialité Hautement confidentiel](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential) à l’étape 5.

2. Créer un dossier dont le contenu ne sera pas synchronisé avec OneDrive.

    *Dossier source C:\ mise en quarantaine automatique*

3. Ouvrez Microsoft Word et créez un fichier dans le dossier source de mise en quarantaine automatique. Appliquer l’étiquette de confidentialité **hautement confidentiel** ; consultez [Appliquer des étiquettes de confidentialité à vos fichiers et courriers électroniques dans Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Copiez le fichier que vous venez de créer dans votre dossier de synchronisation OneDrive. Une pastille de notification utilisateur doit apparaître vous indiquant que l’action n’est pas autorisée et que le fichier sera mis en quarantaine. Par exemple, pour le nom d’utilisateur *Isaiah Langer* et un document intitulé *document de mise en quarantaine automatique 1.docx* ce message s’affiche :

    ![Fenêtre contextuelle de notification utilisateur de protection contre la perte de données indiquant que l’action de synchronisation OneDrive n’est pas autorisée pour le fichier spécifié et que le fichier sera mis en quarantaine.](../media/auto-quarantine-user-notification-toast.png)
    
    Le message indique :
    
    > L’ouverture du document de mise en quarantaine automatique 1.docx avec cette application n’est pas autorisée. Le fichier sera mis en quarantaine dans « C:\Users\IsaiahLanger\Microsoft DLP\OneDrive »

5. Choisissez **Ignorer**.

6. Ouvrez le fichier texte de l’espace réservé. Il sera nommé **document de mise en quarantaine automatique 1.docx_ *date_time*.txt**. 

7. Ouvrez le dossier de quarantaine et vérifiez que le fichier d’origine existe.
 
8. Recherchez dans l’explorateur d’activité les données des points de terminaison surveillés. Définissez le filtre d’emplacement pour les appareils et ajoutez la stratégie. Ensuite, filtrez par nom de stratégie pour voir l’impact de cette stratégie ; consultez l’article [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md) si nécessaire.

9. Consultez l’Explorateur d’activités pour l’événement.

## <a name="scenario-5-restrict-unintentional-sharing-to-unallowed-cloud-apps-and-services"></a>Scénario 5 : Limiter le partage involontaire à des applications et services en nuage non autorisés.

Avec Endpoint DLP et le navigateur Web Edge, vous pouvez restreindre le partage involontaire d'éléments sensibles vers des applications et services en nuage non autorisés. Edge comprend quand un élément est restreint par une politique DLP et applique les restrictions d'accès.

Lorsque vous sélectionnez **Appareils** comme emplacement dans une politique DLP correctement configurée et que vous utilisez le navigateur Microsoft Edge, les navigateurs non autorisés que vous avez définis dans ces paramètres ne pourront pas accéder aux éléments sensibles qui correspondent aux contrôles de votre politique DLP. Au lieu de cela, les utilisateurs sont redirigés vers des Microsoft Edge qui, avec leur compréhension des restrictions DLP imposées, peuvent bloquer ou restreindre les activités lorsque les conditions de la stratégie DLP sont remplies.

Pour utiliser cette restriction, vous devrez configurer trois éléments importants :

1. Spécifier les emplacements ,services, domaines, adresses IP, avec lesquels vous ne souhaitez pas partager les éléments sensibles.

2. Ajoutez les navigateurs qui ne sont pas autorisés à accéder à certains éléments sensibles lorsqu’une correspondance de la stratégie DLP se produit.

3. Configurez les stratégies DLP pour définir les types d’éléments sensibles pour lesquels le téléchargement doit être limité à ces emplacements en activant **Télécharger vers les services Cloud** et **Accès à partir d’un navigateur non autorisé**.

Vous pouvez continuer à ajouter de nouveaux services, applications et stratégies pour développer et augmenter vos restrictions afin de répondre aux besoins de votre entreprise et de protéger les données sensibles. 

Cette configuration vous permet de garantir la sécurité de vos données tout en évitant les restrictions inutiles qui empêchent les utilisateurs d’accéder aux éléments non sensibles et de les empêcher de les partager.
## <a name="see-also"></a>Voir aussi

- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
- [Prise en main la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)
- [Intégrer les appareils Windows 10 et Windows 11 dans la vue d’ensemble de Microsoft Purview](/microsoft-365/compliance/device-onboarding-overview)
- [Abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (ADD) adhésion](/azure/active-directory/devices/concept-azure-ad-join)
- [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
