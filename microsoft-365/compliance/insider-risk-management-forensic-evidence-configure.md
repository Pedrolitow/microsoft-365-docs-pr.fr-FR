---
title: Prise en main des preuves forensiques de gestion des risques internes (préversion)
description: Prise en main des preuves forensiques de gestion des risques internes dans Microsoft Purview. La preuve forensique est un outil d’investigation permettant d’afficher l’activité des utilisateurs liés à la sécurité capturée afin de déterminer si les actions de l’utilisateur posent un risque et peuvent entraîner un incident de sécurité.
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
ms.openlocfilehash: 38dd4b4ee3908da144b1e55d8efbc0af30a39dc9
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68814382"
---
# <a name="get-started-with-insider-risk-management-forensic-evidence-preview"></a>Prise en main des preuves forensiques de gestion des risques internes (préversion)

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

## <a name="configure-forensic-evidence"></a>Configurer les preuves d’investigation

La configuration des preuves forensiques dans votre organisation est similaire à la configuration d’autres stratégies à partir de modèles de stratégie de gestion des risques internes. En général, vous allez suivre les mêmes étapes de configuration de base pour configurer les preuves d’investigation, mais il existe quelques domaines qui nécessitent des actions de configuration spécifiques aux fonctionnalités avant de commencer avec les étapes de configuration de base.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

### <a name="step-1-confirm-your-subscription-and-configure-data-storage-access"></a>Étape 1 : Confirmer votre abonnement et configurer l’accès au stockage des données

Avant de commencer à utiliser les preuves forensiques, vous devez confirmer votre [abonnement à la gestion des risques internes](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-insider-risk-management) et tous les modules complémentaires.

En outre, vous devez ajouter le domaine suivant à votre liste d’autorisation de pare-feu pour prendre en charge le stockage de capture de preuves forensiques pour votre organisation :

- *compliancedrive.microsoft.com*

Les captures et les données de capture sont stockées dans ce domaine et sont affectées uniquement à votre organisation. Aucune autre organisation Microsoft 365 n’a accès aux captures de preuves forensiques pour votre organisation.

### <a name="step-2-configure-supported-devices"></a>Étape 2 : Configurer les appareils pris en charge

Les appareils utilisateur éligibles à la capture de preuves forensiques doivent être intégrés au [portail de conformité Microsoft Purview](/microsoft-365/compliance/microsoft-365-compliance-center) et le client Microsoft Purview doit être installé. 

>[!IMPORTANT]
>Le client Microsoft Purview collecte automatiquement des données de diagnostic générales relatives à la configuration de l’appareil et aux métriques de performances. Cela inclut les données sur les erreurs critiques, la consommation de RAM, les échecs de processus et d’autres données. Ces données nous aident à évaluer l’intégrité du client et à identifier les éventuels problèmes. Pour plus d’informations sur la façon dont les données de diagnostic peuvent être utilisées, consultez utilisation de logiciels avec les services en ligne dans les [Conditions du produit Microsoft](https://www.microsoft.com/licensing/product-licensing/products).

Pour obtenir la liste des exigences en matière d’appareil et de configuration, consultez [En savoir plus sur les preuves forensiques (préversion).](insider-risk-management-forensic-evidence.md#device-and-configuration-requirements) Pour intégrer des appareils pris en charge, effectuez les étapes décrites dans l’article [Vue d’ensemble Intégrer Windows 10 et Windows 11 appareils dans Microsoft 365](/microsoft-365/compliance/device-onboarding-overview). 

Pour installer le client Microsoft Purview, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à **Gestion des** >  risques internes **Preuves forensiques (préversion)** > **Installation du client**.
2. Sélectionnez **Télécharger le package d’installation (version x64)** pour télécharger le package d’installation pour Windows.
3. Après avoir téléchargé le package d’installation, utilisez votre méthode préférée pour installer le client sur les appareils des utilisateurs. Ces options peuvent inclure l’installation manuelle du client sur des appareils ou des outils pour automatiser l’installation du client :

    - **Microsoft Endpoint Manager** : [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) est une solution intégrée pour la gestion de tous vos appareils. Microsoft réunit [Configuration Manager](/mem/configmgr/core/understand/introduction) et [Intune](/mem/intune/fundamentals/what-is-intune), sans migration complexe et avec des licences simplifiées.
    - **Solutions de gestion d’appareils tierces** : si votre organisation utilise des solutions de gestion des appareils tierces, consultez la documentation de ces outils pour installer le client.


### <a name="step-3-configure-settings"></a>Étape 3 : Configurer les paramètres

La preuve d’investigation comporte plusieurs paramètres de configuration qui offrent une flexibilité pour les types d’activités utilisateur liées à la sécurité capturées, les paramètres de capture, les limites de bande passante et les options de capture hors connexion. La capture de preuves forensiques vous permet de créer des stratégies en fonction de vos besoins en quelques étapes seulement, et l’ajout d’utilisateurs à une stratégie nécessite une double autorisation.

Pour configurer les paramètres de preuve d’investigation, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à **Gestion des** >  risques internes **Preuves forensiques (préversion)** > **Paramètres des preuves d’investigation**.
2. Sélectionnez **Capture des preuves forensiques** pour activer la prise en charge de la capture dans vos stratégies de preuve d’investigation. Si cette option est désactivée ultérieurement, cela supprimera tous les utilisateurs précédemment ajoutés pour les stratégies de preuve d’investigation.

    >[!IMPORTANT]
    >Le client Microsoft Purview utilisé pour capturer l’activité sur les appareils des utilisateurs est concédé sous licence utilisation du logiciel avec les services en ligne dans les [Conditions du produit Microsoft](https://www.microsoft.com/licensing/product-licensing/products). Notez que les clients sont seuls responsables de l’utilisation de la solution de gestion des risques internes, y compris le client Microsoft Purview, conformément à toutes les lois applicables.
 
1. Dans la section **Fenêtre capture** , définissez quand démarrer et arrêter la capture d’activité. Les valeurs disponibles sont *10 secondes*, *30 secondes*, *1 minute*, *3 minutes* ou *5 minutes*.
1. Dans la section **Limite de bande passante** de chargement, définissez la quantité de données de capture à charger dans votre compte de stockage de données par utilisateur et par jour. Les valeurs disponibles sont *100 Mo*, *250 Mo*, *500 Mo*, *1 Go* ou *2 Go*.
1. Dans la section **Capture hors connexion** , activez la capture hors connexion si nécessaire. Lorsqu’elle est activée, l’activité hors connexion des utilisateurs est capturée et chargée sur votre compte de stockage de données la prochaine fois qu’ils sont en ligne.
1. Dans la section **Limite du cache de capture hors connexion** , définissez la taille maximale du cache à stocker sur les appareils des utilisateurs lorsque la capture hors connexion est activée. Les valeurs disponibles sont *100 Mo*, *250 Mo*, *500 Mo*, *1 Go* ou *2 Go*.
1. Sélectionnez **Enregistrer**.

### <a name="step-4-create-a-policy"></a>Étape 4 : Créer une stratégie

Les stratégies de preuve d’investigation définissent l’étendue de l’activité utilisateur liée à la sécurité à capturer sur les appareils configurés. Vous pouvez avoir une stratégie qui capture toutes les activités que les utilisateurs approuvés effectuent sur leurs appareils (toutes les séquences de touches, mouvements de souris, etc.) et des stratégies supplémentaires qui capturent uniquement des activités spécifiques (telles que l’impression ou l’exfiltation de fichiers). Une fois créées, vous incluez ces stratégies dans les demandes de preuves forensiques pour contrôler l’activité à capturer pour les utilisateurs dont les demandes sont approuvées.

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à **Gestion des** >  risques internes **Preuves forensiques (préversion)** > **Stratégies de preuve d’investigation**.
2. Sélectionnez **Créer une stratégie de preuve d’investigation**.
3. Dans la page **Étendue** , vous allez choisir l’étendue de l’activité utilisateur liée à la sécurité à capturer. Sélectionnez l’une des options suivantes :

    - **Activités spécifiques** : cette option capture uniquement les activités détectées par les stratégies auxquelles les utilisateurs sont inclus. Ces activités sont définies par les indicateurs sélectionnés dans les stratégies de preuves forensiques. Les captures de cette option peuvent être examinées sous l’onglet **Preuves judiciaires (préversion)** du tableau de bord **Alertes** ou **Cas** .
    - **Toutes les activités** : cette option capture toutes les activités effectuées par les utilisateurs. Cela inclut le déplacement de la souris, les séquences de touches et toutes les activités définies par les indicateurs de risque interne. Les captures de cette option seront disponibles pour révision sous l’onglet **Preuves d’investigation (préversion)** du tableau de bord **Rapports d’activité utilisateur (préversion).**
4. Sélectionnez **Suivant**.
5. Dans la page **Nom et description**, complétez les champs suivants :
    - **Nom (obligatoire)** : entrez un nom convivial pour la stratégie de preuve d’investigation. Ce nom ne peut pas être modifié après la création de la stratégie.
    - **Description (facultatif)** : entrez une description pour la stratégie de preuve d’investigation.
6. Sélectionnez **Suivant**.
7. Si vous avez sélectionné l’option **Toutes les activités** à l’étape 3, la page **Activités de l’appareil** vous dirige vers la dernière étape de l’Assistant Stratégie. Il n’y a aucune activité d’appareil à configurer lorsque l’option **Toutes les activités** est sélectionnée.

    Si vous avez sélectionné l’option **Activités spécifiques** à l’étape 3, vous allez sélectionner les activités de l’appareil à capturer dans la page **Activités de l’appareil** . Seules les activités sélectionnées sont capturées par la stratégie. Si les indicateurs ne sont pas sélectionnables, vous devez activer ces indicateurs pour votre organisation avant de pouvoir sélectionner ces indicateurs dans la stratégie de preuve d’investigation. 

    Une fois que vous avez sélectionné les indicateurs, sélectionnez **Suivant**.
8. Dans la page **Terminer** , passez en revue les paramètres que vous avez choisis pour la stratégie et les suggestions ou avertissements pour vos sélections. Sélectionnez **Modifier** pour changer toute valeur de stratégie ou **Soumettre** pour créer et activer la stratégie.

Une fois que vous avez terminé les étapes de configuration de la stratégie, passez à l’étape 5.

### <a name="step-5-define-and-approve-users-for-capturing"></a>Étape 5 : Définir et approuver les utilisateurs pour la capture

Avant que les activités des utilisateurs liées à la sécurité puissent être capturées, les administrateurs doivent suivre le processus de double autorisation dans la preuve d’investigation. Ce processus impose que l’activation de la capture visuelle pour des utilisateurs spécifiques soit définie et approuvée par les personnes concernées de votre organisation.

>[!IMPORTANT]
>Pour la préversion, un maximum de 5 utilisateurs simultanés sont éligibles pour la capture de preuves forensiques. La capture pour les groupes n’est pas prise en charge dans la préversion.

Vous devez demander que la capture des preuves forensiques soit activée pour des utilisateurs spécifiques. Lorsqu’une demande est envoyée, les approbateurs de votre organisation sont avertis par e-mail et peuvent approuver ou rejeter la demande. S’il est approuvé, l’utilisateur s’affiche sous l’onglet **Utilisateurs approuvés** et peut être capturé.

- Pour demander l’approbation de la capture de preuves forensiques pour les utilisateurs, effectuez [ces étapes de configuration](/microsoft-365/compliance/insider-risk-management-forensic-evidence-manage#request-capturing-approvals).
- Pour approuver (ou rejeter) les demandes de capture de preuves forensiques pour les utilisateurs, effectuez [ces étapes de configuration](/microsoft-365/compliance/insider-risk-management-forensic-evidence-manage#approve-capturing-requests).

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez configuré votre stratégie de preuve d’investigation, jusqu’à 48 heures peuvent être nécessaires pour que les premières captures clip éligibles soient disponibles pour être examinées dans les alertes pour d’autres stratégies ou en tant qu’activité dans **les rapports d’activité utilisateur**. Pour plus d’informations sur la gestion des preuves d’investigation et l’examen des captures clip, consultez l’article [Gérer les preuves forensiques de gestion des risques des informations](/microsoft-365/compliance/insider-risk-management-forensic-evidence-manage) .
