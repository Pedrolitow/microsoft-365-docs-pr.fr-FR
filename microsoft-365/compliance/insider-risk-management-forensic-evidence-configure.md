---
title: Prise en main des preuves légales de gestion des risques internes (préversion)
description: Commencez à utiliser les preuves légales de gestion des risques internes dans Microsoft Purview. La preuve légale est un outil d’investigation permettant d’afficher l’activité de l’utilisateur liée à la sécurité capturée afin de déterminer si les actions de l’utilisateur présentent un risque et peuvent entraîner un incident de sécurité.
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 1d4406ea6372786fda542d2a9b4e83f2ede9abac
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68623894"
---
# <a name="get-started-with-insider-risk-management-forensic-evidence-preview"></a>Prise en main des preuves légales de gestion des risques internes (préversion)

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou involontaires, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Créés avec la confidentialité par conception, les utilisateurs sont pseudonymes par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

## <a name="configure-forensic-evidence"></a>Configurer des preuves légales

La configuration des preuves légales dans votre organisation est similaire à la configuration d’autres stratégies à partir de modèles de stratégie de gestion des risques internes. En général, vous allez suivre les mêmes étapes de configuration de base pour configurer des preuves légales, mais il existe quelques domaines qui nécessitent des actions de configuration spécifiques aux fonctionnalités avant de commencer à utiliser les étapes de configuration de base.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

### <a name="step-1-confirm-your-subscription-and-configure-data-storage-access"></a>Étape 1 : Confirmer votre abonnement et configurer l’accès au stockage de données

Avant de commencer à utiliser des preuves judiciaires, vous devez confirmer votre [abonnement à la gestion des risques internes](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-insider-risk-management) et tous les modules complémentaires.

En outre, vous devez ajouter le domaine suivant à votre liste verte de pare-feu pour prendre en charge le stockage de capture de preuves légales pour votre organisation :

- *compliancedrive.microsoft.com*

Les captures et les données de capture sont stockées dans ce domaine et sont affectées uniquement à votre organisation. Aucune autre organisation Microsoft 365 n’a accès aux captures de preuves légales pour votre organisation.

### <a name="step-2-configure-supported-devices"></a>Étape 2 : Configurer les appareils pris en charge

Les appareils utilisateur éligibles à la capture de preuves légales doivent être intégrés au [portail de conformité Microsoft Purview](/microsoft-365/compliance/microsoft-365-compliance-center) et le client Microsoft Purview doit être installé. 

>[!IMPORTANT]
>Le client Microsoft Purview collecte automatiquement des données de diagnostic générales liées à la configuration de l’appareil et aux métriques de performances. Cela inclut les données sur les erreurs critiques, la consommation de RAM, les échecs de processus et d’autres données. Ces données nous aident à évaluer l’intégrité du client et à identifier les problèmes éventuels. Pour plus d’informations sur la façon dont les données de diagnostic peuvent être utilisées, consultez l’utilisation de logiciels avec les services en ligne dans les [conditions du produit Microsoft](https://www.microsoft.com/licensing/product-licensing/products).

Les captures visuelles dans les preuves légales sont prises en charge pour les appareils/configurations suivants :

- Dernière version Windows 10 ou Windows 11 x64
- Un maximum de 4 moniteurs par appareil

Pour intégrer des appareils, suivez les étapes décrites dans l’article [De présentation de Microsoft 365 sur l’intégration Windows 10 et les appareils Windows 11](/microsoft-365/compliance/device-onboarding-overview).

Pour installer le client Microsoft Purview, procédez comme suit :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à l’installation du client insider **risk management** > **forensic evidence (préversion).** > 
2. Sélectionnez **Télécharger le package d’installation (version x64)** pour télécharger le package d’installation pour Windows.
3. Après avoir téléchargé le package d’installation, utilisez votre méthode préférée pour installer le client sur les appareils des utilisateurs. Ces options peuvent inclure l’installation manuelle du client sur des appareils ou des outils pour automatiser l’installation du client :

    - **Microsoft Endpoint Manager** : [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) est une solution intégrée pour gérer tous vos appareils. Microsoft réunit [Configuration Manager](/mem/configmgr/core/understand/introduction) et [Intune](/mem/intune/fundamentals/what-is-intune), sans migration complexe et avec des licences simplifiées.
    - **Solutions de gestion d’appareils tierces** : si votre organisation utilise des solutions tierces de gestion des appareils, consultez la documentation relative à ces outils pour installer le client.


### <a name="step-3-configure-settings"></a>Étape 3 : Configurer les paramètres

Les preuves légales ont plusieurs paramètres de configuration qui offrent une flexibilité pour les types d’activités utilisateur liées à la sécurité capturées, la capture de paramètres, les limites de bande passante et les options de capture hors connexion. La capture de preuves légales vous permet de créer des stratégies en fonction de vos besoins en quelques étapes et l’ajout d’utilisateurs à une stratégie nécessite une double autorisation.

Pour configurer les paramètres de preuve légale, effectuez les étapes suivantes :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez aux paramètres de **preuves légales de** gestion  >  des **risques internes**(**préversion**) > .
2. Sélectionnez **La capture de preuves légales** pour permettre la capture de la prise en charge dans vos stratégies de preuves légales. Si cette option est désactivée ultérieurement, tous les utilisateurs précédemment ajoutés pour les stratégies de preuves légales seront supprimés.

    >[!IMPORTANT]
    >Le client Microsoft Purview utilisé pour capturer l’activité sur les appareils des utilisateurs est concédé sous licence dans le cadre de l’utilisation de logiciels avec les services en ligne selon les [termes du produit Microsoft](https://www.microsoft.com/licensing/product-licensing/products). Notez que les clients sont seuls responsables de l’utilisation de la solution de gestion des risques internes, y compris le client Microsoft Purview, conformément à toutes les lois applicables.
 
1. Dans la section **Capture de la fenêtre** , définissez quand démarrer et arrêter la capture d’activité. Les valeurs disponibles sont *10 secondes*, *30 secondes*, *1 minute*, *3 minutes* ou *5 minutes*.
1. Dans la section **Charger la limite de bande passante** , définissez la quantité de données de capture à charger dans votre compte de stockage de données par utilisateur et par jour. Les valeurs disponibles sont *100 Mo*, *250 Mo*, *500 Mo*, *1 Go* ou *2 Go*.
1. Dans la section **Capture hors connexion** , activez la capture hors connexion si nécessaire. Quand elle est activée, l’activité hors connexion des utilisateurs est capturée et chargée sur votre compte de stockage de données la prochaine fois qu’elles sont en ligne.
1. Dans la section **Limite du cache de capture hors connexion** , définissez la taille maximale du cache à stocker sur les appareils des utilisateurs lorsque la capture hors connexion est activée. Les valeurs disponibles sont *100 Mo*, *250 Mo*, *500 Mo*, *1 Go* ou *2 Go*.
1. Sélectionnez **Enregistrer**.

### <a name="step-4-create-a-policy"></a>Étape 4 : Créer une stratégie

Les stratégies de preuve légale définissent l’étendue de l’activité utilisateur liée à la sécurité à capturer sur les appareils configurés. Vous pouvez avoir une stratégie qui capture toutes les activités que les utilisateurs approuvés effectuent sur leurs appareils (toutes les séquences de touches, mouvements de la souris, etc.) et des stratégies supplémentaires qui capturent uniquement des activités spécifiques (telles que l’impression ou l’exfiltration de fichiers). Une fois créées, vous incluez ces stratégies dans les demandes de preuves légales pour contrôler l’activité à capturer pour les utilisateurs dont les demandes sont approuvées.

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez aux stratégies de preuves légales de **gestion des** >  risques **internes (préversion)** > **.**
2. Sélectionnez **Créer une stratégie de preuve légale**.
3. Dans la page **Étendue** , vous allez choisir l’étendue de l’activité utilisateur liée à la sécurité à capturer. Sélectionnez l’une des options suivantes :

    - **Activités spécifiques** : cette option capture uniquement les activités détectées par les stratégies dans lesquelles les utilisateurs sont inclus. Ces activités sont définies par les indicateurs sélectionnés dans les stratégies de preuve légale. Les captures de cette option seront disponibles pour examen sous l’onglet **Preuves légales (préversion)** du tableau de bord **Alertes** ou **Cas** .
    - **Toutes les activités** : cette option capture toutes les activités effectuées par les utilisateurs. Cela inclut le mouvement de la souris, les séquences de touches et toutes les activités définies par les indicateurs de risque interne. Les captures de cette option seront disponibles pour examen sous l’onglet **Preuves légales (préversion)** du tableau de bord **Rapports d’activité utilisateur (préversion** ).
4. Sélectionnez **Suivant**.
5. Dans la page **Nom et description**, complétez les champs suivants :
    - **Nom (obligatoire)** : entrez un nom convivial pour la stratégie de preuve légale. Ce nom ne peut pas être modifié après la création de la stratégie.
    - **Description (facultatif)** : entrez une description de la stratégie de preuve légale.
6. Sélectionnez **Suivant**.
7. Si vous avez sélectionné l’option **Toutes les activités** à l’étape 3, la page **Activités de l’appareil** vous dirige vers la dernière étape de l’Assistant Stratégie. Il n’existe aucune activité d’appareil à configurer lorsque l’option **Toutes les activités** est sélectionnée.

    Si vous avez sélectionné l’option **Activités spécifiques** à l’étape 3, vous allez sélectionner les activités de l’appareil à capturer dans la page **Activités de l’appareil** . Seules les activités sélectionnées seront capturées par la stratégie. Si les indicateurs ne sont pas sélectionnables, vous devez activer ces indicateurs pour votre organisation avant de pouvoir sélectionner ces indicateurs dans la stratégie de preuve légale. 

    Une fois que vous avez sélectionné les indicateurs, sélectionnez **Suivant**.
8. Dans la page **Terminer** , passez en revue les paramètres que vous avez choisis pour la stratégie, ainsi que les suggestions ou avertissements pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

Une fois que vous avez terminé les étapes de configuration de la stratégie, passez à l’étape 5.

### <a name="step-5-define-and-approve-users-for-capturing"></a>Étape 5 : Définir et approuver des utilisateurs pour la capture

Avant de pouvoir capturer les activités des utilisateurs liées à la sécurité, les administrateurs doivent suivre le processus d’autorisation double dans les preuves légales. Ce processus exige que l’activation de la capture visuelle pour des utilisateurs spécifiques soit à la fois définie et approuvée par les personnes applicables de votre organisation.

>[!IMPORTANT]
>Pour la préversion, un maximum de 5 utilisateurs simultanés sont éligibles pour la capture de preuves légales. La capture pour les groupes n’est pas prise en charge dans la préversion.

Vous devez demander que la capture de preuves légales soit activée pour des utilisateurs spécifiques. Lorsqu’une demande est envoyée, les approbateurs de votre organisation sont avertis par e-mail et peuvent approuver ou rejeter la demande. S’il est approuvé, l’utilisateur apparaît sous l’onglet **Utilisateurs approuvés** et peut être capturé.

- Pour demander l’approbation de la capture de preuves légales pour les utilisateurs, effectuez [ces étapes de configuration](/microsoft-365/compliance/insider-risk-management-forensic-evidence-manage#request-capturing-approvals).
- Pour approuver (ou rejeter) les demandes de capture de preuves légales pour les utilisateurs, effectuez [ces étapes de configuration](/microsoft-365/compliance/insider-risk-management-forensic-evidence-manage#approve-capturing-requests).

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez configuré votre stratégie de preuves légales, il peut prendre jusqu’à 48 heures pour que les premières captures d’images éligibles soient disponibles pour examen dans les alertes d’autres stratégies ou comme activité dans **les rapports d’activité des utilisateurs**. Pour plus d’informations sur la gestion des preuves judiciaires et l’examen des captures d’images, consultez l’article [Gérer les preuves légales de gestion des risques d’information](/microsoft-365/compliance/insider-risk-management-forensic-evidence-manage) .
