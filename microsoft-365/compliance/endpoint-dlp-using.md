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
- tier1
- highpri
- purview-compliance
- SPO_Content
search.appverid:
- MET150
description: Découvrez comment configurer les stratégies de protection contre la perte de données (DLP) en utilisant les emplacements de protection contre la perte de données de point de terminaison.
ms.openlocfilehash: f8e74219a796b46f681caceefdb532e1678f0a74
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537003"
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


[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Pour obtenir des détails complets sur les licences, consultez [Conseils Microsoft 365 sur les licences pour Information Protection](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Scénario 1 : créer une stratégie à partir d’un modèle, audit uniquement

Ces scénarios nécessitent que les appareils soient déjà intégrés et reportés dans l’Explorateur d’activités. Si vous n’avez pas encore intégré d’appareils, consultez l’article [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md).

1. Ouvrez la [page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Sélectionnez **Créer une stratégie**.

3. Dans le cadre de ce scénario, sélectionnez **Confidentialité**, **Données d’informations d’identification personnelles (PII) pour les États-Unis** puis sélectionnez **Suivant**.

4. Toggle the **Status** field to off for all locations except **Devices**. Choose **Next**.

5. Acceptez la sélection par défaut **Vérifier et personnaliser les paramètres du modèle**, puis sélectionnez **Suivant**.

6. Acceptez les valeurs par défaut **Actions de protection** et choisissez **Suivant**.

7. Select **Audit or restrict activities on Windows devices** and leave the actions set to **Audit only**. Choose **Next**.

8. Accept the default **I'd like to test it out first** value and choose **Show policy tips while in test mode**. Choose **Next**.

9. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

10. La nouvelle stratégie DLP s’affiche dans la liste de stratégies.

11. Check Activity explorer for data from the monitored endpoints. Set the location filter for devices and add the policy, then filter by policy name to see the impact of this policy; see [Get started with activity explorer](data-classification-activity-explorer.md), if needed.

12. Attempt to share a test item that contains content that will trigger the U.S. Personally Identifiable Information (PII) Data condition with someone outside your organization. This should trigger the policy.

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

9. Attempt to share a test item that contains content that will trigger the U.S. Personally Identifiable Information (PII) Data condition with someone outside your organization. This should trigger the policy.

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

9. Attempt to share a test item that contains content that will trigger the U.S. Personally Identifiable Information (PII) Data condition with someone outside your organization. This should trigger the policy.

   Une fenêtre contextuelle semblable à celle-ci s’affiche sur l’appareil client :

   > [!div class="mx-imgBorder"]
   > ![blocage de la notification de remplacement par le client dlp de point de terminaison.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Consultez l’Explorateur d’activités pour l’événement.

## <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Scénario 4 : évitez de boucler les notifications DLP à partir d’applications de synchronisation cloud avec mise en quarantaine automatique (préversion).

## <a name="before-you-begin-scenario-4"></a>Avant de commencer le scénario 4

Dans ce scénario, la synchronisation des fichiers avec l’étiquette de confidentialité **Hautement confidentiel** sur OneDrive est bloquée. Il s’agit d’un scénario complexe avec plusieurs composants et procédures. Vous aurez besoin de :

- Un compte d’utilisateur AAD à cibler et un ordinateur Windows 10 intégré qui synchronise déjà un dossier OneDrive local avec le stockage cloud OneDrive.
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

7. Enter the path to the folder on local machines where you want the original sensitive files to be moved to. For example:
   
    **« %homedrive%%homepath%\Microsoft DLP\Quarantine »** pour le nom d’utilisateur *Isaiah langer* placera les éléments déplacés dans un dossier nommé :  

    *C:\Users\IsaiahLanger\Microsoft DLP\Quarantine\OneDrive*

    et ajoutez une date et une heure au nom de fichier d’origine.
    
    > [!NOTE]
    > La mise en quarantaine automatique DLP crée des sous-dossiers pour les fichiers de chaque application non autorisée. Par conséquent, si vous avez le *Bloc-notes* et *OneDrive* dans votre liste d’applications non autorisées, un sous-dossier sera créé pour **\OneDrive** et un autre sous-dossier pour **\Bloc-notes**.

8. Choose **Replace the files with a .txt file that contains the following text** and enter the text you want in the placeholder file. For example for a file named *auto quar 1.docx*:
    
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

9. Choose **Turn it on right away**. Choose **Next**.

10. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

    > [!NOTE]
    > Autorisez au moins une heure pour que la nouvelle stratégie soit répliquée et appliquée à l’ordinateur Windows 10 cible.

11. La nouvelle stratégie DLP s’affiche dans la liste des stratégies.

### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Tester la mise en quarantaine automatique sur l’appareil Windows 10

1. Connectez-vous à l’ordinateur Windows 10 avec le compte d’utilisateur que vous avez spécifié dans [Configurez une stratégie pour bloquer la synchronisation OneDrive des fichiers avec l’étiquette de confidentialité Hautement confidentiel](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential) à l’étape 5.

2. Create a folder whose contents will not be synchronized to OneDrive. For example:

    *Dossier source C:\ mise en quarantaine automatique*

3. Ouvrez Microsoft Word et créez un fichier dans le dossier source de mise en quarantaine automatique. Appliquer l’étiquette de confidentialité **hautement confidentiel** ; consultez [Appliquer des étiquettes de confidentialité à vos fichiers et courriers électroniques dans Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Copiez le fichier que vous venez de créer dans votre dossier de synchronisation OneDrive. Une pastille de notification utilisateur doit apparaître vous indiquant que l’action n’est pas autorisée et que le fichier sera mis en quarantaine. Par exemple, pour le nom d’utilisateur *Isaiah Langer* et un document intitulé *document de mise en quarantaine automatique 1.docx* ce message s’affiche :

    ![Fenêtre contextuelle de notification utilisateur de protection contre la perte de données indiquant que l’action de synchronisation OneDrive n’est pas autorisée pour le fichier spécifié et que le fichier sera mis en quarantaine.](../media/auto-quarantine-user-notification-toast.png)
    
    Le message indique :
    
    > L’ouverture du document de mise en quarantaine automatique 1.docx avec cette application n’est pas autorisée. Le fichier sera mis en quarantaine dans « C:\Users\IsaiahLanger\Microsoft DLP\OneDrive »

5. Choisissez **Ignorer**.

6. Ouvrez le fichier texte de l’espace réservé. Il sera nommé **document de mise en quarantaine automatique 1.docx_ *date_time*.txt**. 

7. Ouvrez le dossier de quarantaine et vérifiez que le fichier d’origine existe.
 
8. Check Activity explorer for data from the monitored endpoints. Set the location filter for devices and add the policy, then filter by policy name to see the impact of this policy; see [Get started with activity explorer](data-classification-activity-explorer.md), if needed.

9. Consultez l’Explorateur d’activités pour l’événement.

## <a name="scenario-5-restrict-unintentional-sharing-to-unallowed-cloud-apps-and-services"></a>Scénario 5 : Limiter le partage involontaire à des applications et services en nuage non autorisés.

Avec Endpoint DLP et le navigateur web Microsoft Edge, vous pouvez limiter le partage involontaire d’éléments sensibles aux applications et services cloud non autorisés. Edge comprend quand un élément est restreint par une politique DLP et applique les restrictions d'accès.

Lorsque vous sélectionnez **Appareils** comme emplacement dans une politique DLP correctement configurée et que vous utilisez le navigateur Microsoft Edge, les navigateurs non autorisés que vous avez définis dans ces paramètres ne pourront pas accéder aux éléments sensibles qui correspondent aux contrôles de votre politique DLP. Au lieu de cela, les utilisateurs sont redirigés vers des Microsoft Edge qui, avec leur compréhension des restrictions DLP imposées, peuvent bloquer ou restreindre les activités lorsque les conditions de la stratégie DLP sont remplies.

Pour utiliser cette restriction, vous devrez configurer trois éléments importants :

1. Spécifier les emplacements ,services, domaines, adresses IP, avec lesquels vous ne souhaitez pas partager les éléments sensibles.

2. Ajoutez les navigateurs qui ne sont pas autorisés à accéder à certains éléments sensibles lorsqu’une correspondance de la stratégie DLP se produit.

3. Configurez les stratégies DLP pour définir les types d’éléments sensibles pour lesquels le téléchargement doit être limité à ces emplacements en activant **Télécharger vers les services Cloud** et **Accès à partir d’un navigateur non autorisé**.

Vous pouvez continuer à ajouter de nouveaux services, applications et stratégies pour développer et augmenter vos restrictions afin de répondre aux besoins de votre entreprise et de protéger les données sensibles. 

Cette configuration vous permet de garantir la sécurité de vos données tout en évitant les restrictions inutiles qui empêchent les utilisateurs d’accéder aux éléments non sensibles et de les empêcher de les partager.

## <a name="scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains"></a>Scénario 6 : Surveiller ou restreindre les activités des utilisateurs sur des domaines de service sensibles

Utilisez ce scénario lorsque vous souhaitez auditer, bloquer avec neutralisation ou bloquer ces activités d'utilisateur sur un site Web.

- imprimer à partir d’un site web
- copier des données à partir d’un site web
- enregistrer un site web en tant que fichiers locaux

L’utilisateur doit accéder au site web via Microsoft Edge.

### <a name="supported-syntax-for-designating-websites-in-a-website-group"></a>Syntaxe prise en charge pour désigner des sites web dans un groupe de sites web

Vous pouvez utiliser une syntaxe flexible pour inclure et exclure des domaines, sous-domaines, sites web et sous-sites dans vos groupes de sites web.

- utiliser `*` comme caractère générique pour spécifier tous les domaines ou tous les sous-domaines
- utiliser `/` comme terminateur à la fin d’une URL pour étendre uniquement à ce site spécifique.

Lorsque vous ajoutez une URL sans fin, `/`cette URL est limitée à ce site et à tous les sous-sites.

Cette syntaxe s’applique à tous les sites web http/https.

Voici quelques exemples :


|URL que vous ajoutez au groupe de sites web  |L’URL correspondra  | L’URL ne correspond pas|
|---------|---------|---------|
|contoso.com  | //<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/ </br> //<!--nourl-->contoso.com/allsubsites1 </br> //<!--nourl-->contoso.com/allsubsites1/allsubsites2|        //<!--nourl-->allsubdomains.contoso.com </br> //<!--nourl-->allsubdomains.contoso.com.au    |
|contoso.com/     |//<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/         |//<!--nourl-->contoso.com/allsubsites1 </br> //<!--nourl-->contoso.com/allsubsites1/allsubsites2 </br> //<!--nourl-->allsubdomains.contoso.com </br> //<!--nourl-->allsubdomains.contoso.com/au   |
|*.contoso.com   | //<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/allsubsites </br> //<!--nourl-->contoso.com/allsubsites1/allsubsites2 </br> //<!--nourl-->allsubdomains.contoso.com </br> //<!--nourl-->allsubdomains.contoso.com/allsubsites </br> //<!--nourl-->allsubdomains1/allsubdomains2/contoso.com/allsubsites1/allsubsites2         | //<!--nourl-->allsubdomains.contoso.com.au|
|*.contoso.com/xyz     |//<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/xyz </br> //<!--nourl-->contoso.con/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains.contoso.com/xyz </br> //<!--nourl-->allsubdomains.contoso.com/xyz/allsubsites </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites1/allsubsites2         | //<!--nourl-->contoso.com/xyz </br> //<!--nourl-->allsubdomains.contoso.com/xyz/|
|*.contoso.com/xyz/     |//<!--nourl-->contoso.com/xyz </br> //<!--nourl-->allsubdomains.contoso.com/xyz         |//<!--nourl-->contoso.com </br> //<!--nourl-->contoso.com/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains.contoso.com/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites/ </br> //<!--nourl-->allsubdomains1.allsubdomains2.contoso.com/xyz/allsubsites1/allsubsites2|


### <a name="configure-sensitive-service-domains"></a>Configurer des domaines de service sensibles

1. Dans le portail de conformité Microsoft Purview, ouvrez **Prévention des pertes de données** > **Paramètres Endpoint DLP** > **Restrictions de navigateur et de domaine aux données sensibles** > **Domaines de service sensibles** .
1. Sélectionnez **Ajouter un nouveau groupe de domaines de service sensibles**.
1. Nommez le groupe.
1. Sélectionnez le **type de correspondance** que vous souhaitez. Vous pouvez sélectionner **l’URL**, **l’adresse IP** et la **plage d’adresses IP**.
1. Tapez la valeur appropriée dans l’option **Ajouter de nouveaux domaines de service à ce groupe**. Vous pouvez ajouter plusieurs sites web à un groupe et utiliser des caractères génériques pour couvrir les sous-domaines.  Par exemple, `www.contoso.com` pour le site web de niveau supérieur ou \*.contoso.com pour corp.contoso.com, hr.contoso.com, fin.contoso.com
1. Sélectionnez **Enregistrer**.
1. Sélectionnez **Stratégies**.
1. Créez et définissez une politique qui s'applique uniquement aux **dispositifs**. Pour plus d’informations sur la création [d’une stratégie, consultez, créez, testez et paramétrez une stratégie DLP](create-test-tune-dlp-policy.md) .
1. Créez une règle qui utilise **l’utilisateur qui a accédé à un site sensible à partir de Edge**, et l’action **Auditer ou restreindre les activités sur les appareils**.
1. Dans **le domaine de service et les activités de navigateur,** **sélectionnez Charger vers un domaine de service cloud restreint ou l’accès à partir d’un navigateur non autorisé** , puis définissez l’action **sur Audit uniquement**. Cela définit l’action globale pour tous les groupes de sites.
1. Sélectionnez les **groupes de sites sensibles** souhaités.
1. Sélectionnez **Ajouter**.
1. FACULTATIF : si vous souhaitez créer une exception (généralement une liste verte) à l’action globale pour un ou plusieurs groupes de sites, sélectionnez **Configurer les exceptions de domaine de service sensibles**, ajoutez le groupe de sites pour lequel vous souhaitez l’exception, configurez l’action souhaitée et **enregistrez** la configuration.
1. Sélectionnez les activités de l'utilisateur que vous souhaitez surveiller ou restreindre et les actions que la DLP doit entreprendre en réponse à ces activités.
1. Terminez la configuration de la règle et de la stratégie et appliquez-la.

## <a name="scenario-7-authorization-groups-preview"></a>Scénario 7 Groupes d’autorisation (préversion)

> [!IMPORTANT]
> Avant de pouvoir utiliser des **groupes d’imprimantes**, des **groupes d’appareils de stockage amovibles**, des **groupes de partage réseau** et **des exceptions réseau/VPN** , vous devez vous inscrire [ici](https://forms.office.com/r/GNVTFvxuZv).

Ces scénarios nécessitent que les appareils soient déjà intégrés et reportés dans l’Explorateur d’activités. Si vous n’avez pas encore intégré d’appareils, consultez l’article [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md).

Les groupes d’autorisation sont principalement utilisés comme listes d’autorisation. Vous avez affecté des actions de stratégie au groupe qui sont différentes des actions de stratégie globales. Dans ce scénario, nous allons définir un groupe d’imprimantes, puis configurer une stratégie avec des actions de blocage pour toutes les activités d’impression, à l’exception des imprimantes du groupe. Ces procédures sont essentiellement les mêmes pour les **groupes d’appareils de stockage amovibles** et les **groupes de partage réseau**.

Dans ce scénario, nous allons définir un groupe d’imprimantes que le service juridique utilise pour les contrats d’impression. Les contrats d’impression sur d’autres imprimantes sont bloqués.

### <a name="create-and-use-printer-groups"></a>Créer et utiliser des groupes d’imprimantes

1. Dans le portail de conformité Microsoft Purview ouvrir les **groupes d’imprimantes** **des paramètres DLP** du point de terminaison de **protection contre la** >  perte de  >  données.
1. Sélectionnez **Créer un groupe d’imprimantes** et donnez un nom au groupe. Dans ce scénario, nous allons utiliser `Legal printers`.
1. Sélectionnez **Ajouter une imprimante** et indiquez un nom. Vous pouvez définir des imprimantes en :
    1. Nom de l’imprimante conviviale 
    1. ID de produit USB
    1. ID du fournisseur USB
    1. Plage d’adresses IP
    1. Imprimer dans un fichier
    1. Impression universelle déployée sur une imprimante
    1. Imprimante d’entreprise
    1. Imprimer sur local
1. Sélectionnez **Fermer**.

### <a name="configure-policy-printing-actions"></a>Configurer les actions d’impression de stratégie

1. Ouvrez l’onglet **Stratégies** .

1. Sélectionnez **Créer une stratégie** et sélectionnez le modèle de stratégie personnalisé.
1. Étendue de l’emplacement uniquement aux **appareils**.

1. Créez une règle dans laquelle :
    1. **Le contenu contient** =  **Classifieurs pouvant être formés**, **Affaires juridiques**
    1. **Actions** =  **Auditer ou restreindre les activités sur les appareils**
    1. Sélectionnez ensuite **les activités de fichier sur toutes les applications**
    1. Sélection **Appliquer des restrictions à une activité spécifique**
    1. Sélectionner **Bloc d’impression** = 
1. **Sélectionnez Choisir différentes restrictions d’impression**
1. Sous **Restrictions de groupe d’imprimantes**, **sélectionnez Ajouter un groupe** , puis Les **imprimantes légales**.
1. Définir **l’action** = **Autoriser**.
    > [!TIP]
    > L’événement **Autoriser** l’enregistrement et l’audit de l’action dans le journal d’audit, mais ne génère pas d’alerte ou de notification. 
10. Sauvegarder.
11. Accepter la valeur par défaut **Je veux tester le contenu tout d’abord** et choisir **Afficher les conseils de stratégie en mode test**. Cliquez sur **Suivant**.

12. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

13. La nouvelle stratégie DLP s’affiche dans la liste de stratégies.

## <a name="scenario-8-network-exceptions-preview"></a>Scénario 8 Exceptions réseau (préversion)

> [!IMPORTANT]
> Avant de pouvoir utiliser des **groupes d’imprimantes**, des **groupes d’appareils de stockage amovibles**, des **groupes de partage réseau** et **des exceptions réseau/VPN** , vous devez vous inscrire [ici](https://forms.office.com/r/GNVTFvxuZv).

Ces scénarios nécessitent que les appareils soient déjà intégrés et reportés dans l’Explorateur d’activités. Si vous n’avez pas encore intégré d’appareils, consultez l’article [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md).

Dans ce scénario, nous allons définir une liste de VPN utilisés par les workers hybrides pour accéder aux ressources de l’organisation.

### <a name="create-and-use-a-network-exception"></a>Créer et utiliser une exception réseau

Les exceptions réseau vous permettent de configurer autoriser, auditer uniquement, bloquer avec remplacement et bloquer les actions de fichiers en fonction du réseau à partir de lequel les utilisateurs accèdent au fichier. Vous pouvez sélectionner dans la liste [des paramètres VPN](dlp-configure-endpoint-settings.md#vpn-settings-preview) que vous avez définie et l’option **Réseau d’entreprise** . Les actions peuvent être appliquées individuellement ou collectivement à ces activités utilisateur :

- Copier dans le Presse-papiers
- Copier sur un appareil amovible USB
- Copier vers un partage réseau
- Imprimer
- Copier ou déplacer à l'aide d'une application Bluetooth non autorisée
- Copier ou déplacer à l’aide de RDP

#### <a name="get-the-server-address-or-network-address"></a>Obtenir l’adresse du serveur ou l’adresse réseau

1. Sur un appareil Windows surveillé par DLP, ouvrez une fenêtre **Windows PowerShell** en tant qu’administrateur.
1. Exécuter cette applet de commande

```powershell-interactive
Get-VpnConnection
```

3. L’exécution de cette applet de commande retourne plusieurs champs et valeurs.
1. Recherchez le champ **ServerAddress** et enregistrez cette valeur. Vous l’utiliserez lorsque vous créerez une entrée VPN dans la liste VPN.
1. Recherchez le champ **Nom** et enregistrez cette valeur. Le champ **Nom** correspond au champ **Adresse réseau** lorsque vous créez une entrée VPN dans la liste VPN.

#### <a name="add-a-vpn"></a>Ajouter un VPN

1. Ouvrez [portail de conformité Microsoft Purview](https://compliance.microsoft.com) >  **Paramètres VPN des paramètres** >  DLP du point de terminaison de **protection contre la** >  perte **de données**.
1. Sélectionnez **Ajouter ou modifier des adresses VPN**.
1. Indiquez **l’adresse du serveur** ou **l’adresse réseau** à partir de l’exécution de Get-VpnConnection.
1. Sélectionnez **Enregistrer**.
1. Fermez l’élément.

#### <a name="configure-policy-actions"></a>Configurer des actions de stratégie

1. Ouvrez l’onglet **Stratégies** .

1. Sélectionnez **Créer une stratégie** et sélectionnez le modèle de stratégie personnalisé.
1. Étendue de l’emplacement uniquement aux **appareils**.

1. Créez une règle dans laquelle :
    1. **Le contenu contient** =  **Classifieurs pouvant être formés**, **Affaires juridiques**
    1. **Actions** =  **Auditer ou restreindre les activités sur les appareils**
    1. Sélectionnez ensuite **les activités de fichier sur toutes les applications**
    1. Sélection **Appliquer des restrictions à une activité spécifique**
    1. Sélectionnez les actions pour lesquelles vous souhaitez configurer **les exceptions réseau** .
1. Sélectionnez **Copier dans le Presse-papiers** et l’action **Audit uniquement**
1. **Sélectionnez Choisir une autre copie dans les restrictions du Presse-papiers**.
1. Sélectionnez **VPN** et définissez l’action sur **Bloquer avec remplacement**.

> [!IMPORTANT]
> Lorsque vous souhaitez contrôler les activités d’un utilisateur lorsqu’il est connecté via un VPN, *vous devez* sélectionner le VPN et faire du VPN la priorité absolue dans la configuration **des exceptions réseau** . Sinon, si l’option **Réseau d’entreprise** est sélectionnée, cette action définie pour l’entrée **réseau d’entreprise** sera appliquée.

> [!CAUTION]
> L’option **Appliquer à toutes les activités** copie les exceptions réseau définies ici et les applique à toutes les autres activités spécifiques configurées, telles que **Imprimer** et **Copier sur un partage réseau**. **_Cela remplacera les exceptions réseau sur les autres activités La dernière configuration enregistrée l’emporte._**  

8. Sauvegarder.
1. Accepter la valeur par défaut **Je veux tester le contenu tout d’abord** et choisir **Afficher les conseils de stratégie en mode test**. Cliquez sur **Suivant**.

1. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

1. La nouvelle stratégie DLP s’affiche dans la liste de stratégies.
 
 
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
