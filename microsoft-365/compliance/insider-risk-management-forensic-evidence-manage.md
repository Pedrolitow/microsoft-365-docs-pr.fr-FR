---
title: Gérer les preuves forensiques de gestion des risques internes (préversion)
description: Gérer les preuves forensiques de gestion des risques internes dans Microsoft Purview. La preuve forensique est un outil d’investigation permettant d’afficher l’activité des utilisateurs liés à la sécurité capturée afin de déterminer si les actions de l’utilisateur posent un risque et peuvent entraîner un incident de sécurité.
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
ms.openlocfilehash: 6d35faf52b03afd6189e869da38e2b6f20255ec4
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68815086"
---
# <a name="manage-insider-risk-management-forensic-evidence-preview"></a>Gérer les preuves forensiques de gestion des risques internes (préversion)

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Une fois que vous avez terminé les étapes de configuration et créé votre stratégie de preuve d’investigation, vous commencez à voir des alertes pour les activités potentiellement risquées des utilisateurs liées à la sécurité qui répondent aux conditions pour les indicateurs définis dans la stratégie.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="dashboard"></a>Tableau de bord

Le tableau de bord des preuves forensiques est la vue récapitulative des domaines clés de la configuration des preuves d’investigation dans votre organisation. Pour la préversion, le tableau de bord inclut uniquement une section **Relative à l’intégrité de l’appareil des preuves judiciaires** . Sélectionnez **Afficher le rapport d’intégrité de l’appareil** pour ouvrir l’onglet **État de l’appareil** et le rapport. D’autres sections seront incluses dans les versions ultérieures.

## <a name="managing-users"></a>Gestion des utilisateurs

Vous devez demander et approuver des utilisateurs spécifiques avant qu’ils ne soient éligibles à la capture de preuves forensiques. Le simple fait d’ajouter des utilisateurs à une stratégie de preuve d’investigation ne rend pas automatiquement ces utilisateurs éligibles pour la capture. Vous pouvez demander et approuver des utilisateurs avant ou après la création de stratégies de preuve d’investigation, mais les captures de clip associées aux indicateurs de stratégie ne seront créées et disponibles pour révision qu’une fois les utilisateurs approuvés.

Les utilisateurs affectés aux groupes de rôles *Gestion des risques internes* ou *Administrateurs de gestion des risques internes* peuvent envoyer des demandes d’approbation aux utilisateurs affectés au groupe de rôles *Approbateurs de gestion des risques internes* .

### <a name="request-capturing-approvals"></a>Demande d’approbations de capture

Vous devez demander que la capture des preuves d’investigation soit activée pour des utilisateurs spécifiques. Lorsqu’une demande est envoyée, les approbateurs de votre organisation sont avertis par e-mail et peuvent approuver ou rejeter la demande. S’il est approuvé, l’utilisateur ou s’affiche sous l’onglet **Utilisateurs approuvés** et peut être capturé. Si elle n’est pas traitée, la demande expirera 6 mois à compter du jour où elle a été envoyée.

Pour configurer des utilisateurs approuvés pour la capture de preuves forensiques, procédez comme suit :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à **Gestion des** >  risques internes **Preuves forensiques (préversion)** > **Gestion des utilisateurs**.
2. Sélectionnez l’onglet **Gérer les demandes de preuves forensiques** .
3. Sélectionnez **Créer une demande**.
4. Dans la page **Utilisateurs** , sélectionnez **Ajouter des utilisateurs**.
5. Utilisez **La recherche** pour localiser un utilisateur spécifique ou sélectionnez un ou plusieurs utilisateurs dans la liste. Sélectionnez **Ajouter**, puis **Suivant**.
6. Dans la page **Stratégie de preuve d’investigation** , sélectionnez une stratégie de preuve d’investigation pour les utilisateurs ajoutés. La stratégie que vous choisissez détermine l’étendue de l’activité à capturer pour les utilisateurs.
7. Sélectionnez **Suivant**.
8. Dans la page **Justification** , indiquez au réviseur pourquoi vous demandez que la capture soit activée pour les utilisateurs que vous avez ajoutés dans la zone de texte **Justification de l’activation de la capture des preuves d’investigation** . Ce champ est obligatoire. Une fois terminé, sélectionnez **Suivant**.
9. Dans la page **notifications Email**, vous pouvez utiliser un modèle de notification pour envoyer un e-mail aux utilisateurs leur informant que la capture de preuves forensiques sera activée pour leur appareil conformément aux stratégies de votre organisation. L’e-mail est envoyé aux utilisateurs uniquement si leur demande est approuvée.

    Cochez la case **Envoyer une notification par e-mail aux utilisateurs approuvés** . Choisissez un modèle existant o créez-en un. Pour créer un modèle, sélectionnez **Créer un modèle de notification** et renseignez les champs obligatoires suivants dans le volet **Nouveau modèle de notification par e-mail** .

10. Sélectionnez **Suivant**.
11. Dans la page **Terminer** , passez en revue vos paramètres avant d’envoyer la demande. Sélectionnez **Modifier les utilisateurs** ou **Modifier la justification** pour modifier l’une des valeurs de la demande ou sélectionnez **Envoyer** pour créer et envoyer la demande aux réviseurs.

Pour afficher les demandes d’approbation en attente, accédez à **Gestion des** >  risques internes **Preuves forensiques (préversion)** > **Demandes en attente**. Ici, vous verrez les utilisateurs avec les demandes en attente, leur adresse e-mail, la date d’envoi de la demande et qui a envoyé la demande d’approbation. Si aucun utilisateur n’est affiché, aucune demande d’approbation n’est en attente pour les utilisateurs.

Les utilisateurs affectés au groupe de rôles *Approbateurs de gestion des risques internes* peuvent sélectionner un utilisateur sous l’onglet **Demande de preuve forensique (préversion)** et examiner la demande. Après avoir examiné la demande, ces utilisateurs peuvent approuver ou rejeter la demande de capture de preuves forensiques. L’approbation ou le rejet de la demande de capture supprime la demande en attente pour les utilisateurs de cette vue.

### <a name="approve-or-reject-capturing-requests"></a>Approuver ou rejeter les demandes de capture

Une fois les demandes terminées, les utilisateurs affectés au groupe de rôles *Approbateurs de gestion des risques internes* reçoivent une notification par e-mail pour la demande d’approbation. Pour approuver ou rejeter des demandes, les réviseurs doivent effectuer les étapes suivantes :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à **Gestion des** >  risques internes **Preuves judiciaires (préversion)** > **Demandes en attente**.
2. Sélectionnez un utilisateur à réviser.
3. Dans le volet **Examiner la demande de preuve d’investigation (préversion),** passez en revue la justification soumise par le demandeur. Sélectionnez **Approuver** ou **Rejeter** le cas échéant.
4. Dans la page **Demande approuvée** ou **Demande rejetée** , sélectionnez **Fermer**.

![Approbation des preuves forensiques de gestion des risques internes.](../media/insider-risk-forensic-evidence-approval.png)

### <a name="revoke-capturing-approvals"></a>Révoquer les approbations de capture

Si nécessaire, vous pouvez révoquer l’approbation d’utilisateurs spécifiques et les exclure de la capture de preuves forensiques. La révocation de l’approbation ne supprime pas ou ne supprime pas les captures existantes pour ces utilisateurs. Seule la capture future de l’activité pour ces utilisateurs est désactivée.

Pour révoquer les approbations des utilisateurs, les utilisateurs affectés au groupe de rôles *Approbateurs de gestion des risques internes* doivent effectuer les étapes suivantes :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à **Gestion des** >  risques internes **Preuves forensiques (préversion)** > **Gestion des utilisateurs**.
2. Sélectionnez l’onglet **Utilisateurs approuvés** .
3. Sélectionnez un utilisateur, puis **sélectionnez Supprimer**.
4. Dans la page de confirmation de suppression, sélectionnez **Supprimer** pour révoquer l’approbation de capture ou sélectionnez **Annuler** pour fermer la page de confirmation.

## <a name="creating-and-managing-notification-templates"></a>Création et gestion de modèles de notification

Vous pouvez créer et utiliser un modèle de notification pour envoyer un e-mail aux utilisateurs leur informant que la capture des preuves forensiques sera activée pour leur appareil conformément aux stratégies de votre organisation. L’e-mail est envoyé aux utilisateurs uniquement si leur demande est approuvée.

![Notification des preuves forensiques de gestion des risques internes.](../media/insider-risk-forensic-evidence-notification.png)

Pour créer un modèle de notification, procédez comme suit :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com/), accédez à **Gestion des** >  risques internes **Preuves d’investigation (préversion)** > **Modèles de notification**.
2. Sélectionnez **Créer un modèle de notification**.
3. Dans le volet **Nouveau modèle de notification par e-mail** , renseignez les champs obligatoires suivants :
    - Nom du modèle
    - Envoyer à partir de
    - Subject
    - Corps du message
4. Sélectionnez **Enregistrer**.

Pour supprimer un modèle de notification existant, sélectionnez un modèle, puis **sélectionnez Supprimer**.

## <a name="viewing-capture-clips"></a>Affichage des clips de capture

Si vous avez sélectionné l’option permettant de capturer uniquement les activités définies par les indicateurs sélectionnés dans les stratégies de preuve forensique, les clips de capture sont disponibles dans le cadre de l’alerte et sont accessibles sous l’onglet **Preuves forensiques (préversion)** du **tableau de bord Alertes**. Si les alertes sont ensuite remontées vers des cas, les clips associés sont accessibles sous l’onglet **Preuves forensiques (préversion)** du tableau de bord **Cas** .

Si vous avez sélectionné l’option permettant de capturer toute activité liée à la sécurité effectuée par les utilisateurs inclus dans les stratégies de preuve d’investigation, vous allez afficher les clips pour les utilisateurs individuels dans le tableau de bord **rapport d’activité des** utilisateurs.

>[!IMPORTANT]
>Les clips de preuve d’investigation sont supprimés 120 jours après leur capture ou à la fin de la période de préversion, selon la date la plus précoce. Vous pouvez télécharger ou transférer des extraits de preuve d’investigation avant qu’ils ne soient supprimés.

### <a name="reviewing-capture-clips-included-with-alerts"></a>Examen des clips de capture inclus avec les alertes

Pour les alertes générées par les stratégies, les captures de preuves forensiques pour les utilisateurs peuvent être examinées sous l’onglet **Preuves judiciaires (préversion)** du tableau de bord **Alertes** . Si une ou plusieurs captures sont disponibles pour l’alerte, vous verrez également une notification **Afficher les preuves forensiques** dans la section Activité qui a généré cet en-tête d’alerte. Vous pouvez sélectionner le lien de notification ou l’onglet **Preuve d’investigation (préversion)** pour passer en revue les captures d’activité.

![Activité de l’utilisateur en matière de preuves forensiques de gestion des risques internes.](../media/insider-risk-forensic-evidence-user-activity.png)

Dans l’ensemble, l’examen d’une alerte pour une activité potentiellement risquée qui peut contenir des captures de preuves judiciaires est essentiellement la même chose que l’examen d’une alerte sans captures de preuves judiciaires. La différence significative est l’inclusion de toutes les captures applicables. **L’onglet Preuve légale (préversion)** permet d’accéder à toutes les captures disponibles associées à l’alerte. Chaque capture s’affiche et inclut les informations suivantes :

- **Date/heure (UTC)** : date, heure (UTC) et durée de la capture.
- **Appareil** : nom de l’appareil dans Windows 10/11.
- **Type d’activité** : type d’activité de gestion des risques internes inclus dans la capture. Ces activités sont basées sur des indicateurs globaux et de stratégie attribués à la stratégie associée.
- **Événements de capture** : chaque capture contient des événements dans la capture pour vous aider à concentrer votre révision sur des activités spécifiques pour la session de capture.

Pour afficher un clip de capture, procédez comme suit :

1. Si nécessaire, configurez les filtres pour les captures disponibles. Vous pouvez filtrer par **dates (UTC)** ou par **activité**.
2. Sélectionnez un clip à réviser.
3. Sélectionnez le moniteur d’appareil à examiner. Chaque moniteur connecté à l’appareil (jusqu’à 4) est éligible pour la capture de preuves d’investigation et sont répertoriés comme *Affichage 1*, *Affichage 2*, etc.
4. À l’aide des contrôles du lecteur vidéo, sélectionnez le *contrôle Lire* pour passer en revue l’intégralité du clip du début à la fin.
5. Si vous souhaitez limiter la révision à un événement spécifique dans le clip, sélectionnez l’événement dans les listes **Capturer les événements** à droite du lecteur vidéo.

### <a name="reviewing-capture-clips-included-with-cases"></a>Examen des clips de capture inclus dans des cas

Si les alertes sont remontées vers des cas, toutes les captures de preuves médico-légales associées sont incluses dans le cadre du cas. L’examen des captures de preuves forensiques pour les cas suit le même processus que lorsque vous examinez les captures dans le cadre de l’examen des alertes.

### <a name="reviewing-capture-clips-without-alerts"></a>Examen des clips de capture sans alertes

Pour afficher les clips d’activité non associées aux alertes, vous allez utiliser [les rapports d’activité des utilisateurs](/microsoft-365/compliance/insider-risk-management-activities#user-activity-reports). Les rapports d’activité des utilisateurs vous permettent d’examiner les activités d’utilisateurs spécifiques pendant une période définie sans avoir à les affecter temporairement ou explicitement à une stratégie de gestion des risques internes. Si ces activités utilisateur incluent des activités prises en charge par la capture de preuves forensiques, les clips sont inclus dans l’activité de l’utilisateur.

Si vous avez configuré des preuves forensiques pour capturer toutes les activités des utilisateurs liées à la sécurité, qu’elles soient incluses ou non dans une stratégie de preuve d’investigation, vous allez examiner ces captures en sélectionnant **Gestion des** >  risques internes Rapports **d’activité utilisateur**, puis en sélectionnant un utilisateur spécifique et en sélectionnant l’onglet **Preuve d’investigation (préversion).**

## <a name="device-health-report-preview"></a>Rapport d’intégrité de l’appareil (préversion)

Une fois que les appareils sont configurés pour prendre en charge les preuves d’investigation, vous pouvez examiner l’état d’intégrité du client Microsoft Purview pour tous les appareils de votre organisation en accédant à **Gestion des** >  risques internes **Preuve d’investigation (préversion)** > **Intégrité de l’appareil**.

![Intégrité de l’appareil de preuve de la gestion des risques internes.](../media/insider-risk-forensic-evidence-device-health.png)

Pour obtenir la liste des conditions minimales requises pour l’appareil et la configuration, consultez [En savoir plus sur les preuves d’investigation (préversion)](insider-risk-management-forensic-evidence.md#device-and-configuration-requirements) . Pour intégrer des appareils pris en charge, effectuez les étapes décrites dans l’article [Vue d’ensemble Intégrer Windows 10 et Windows 11 appareils dans Microsoft 365](/microsoft-365/compliance/device-onboarding-overview). 

Le rapport d’intégrité de l’appareil vous permet d’afficher l’état et l’intégrité de tous les appareils sur lesquels l’agent de preuve d’investigation est installé. Chaque widget de rapport sur le rapport affiche des informations pour les dernières 24 heures.

- **Appareils en ligne** : nombre total d’appareils actuellement en ligne.
- **Appareils hors connexion** : nombre total d’appareils actuellement hors connexion.
- **Appareils avec avertissements** : nombre total d’appareils avec un avertissement.
- **Appareils présentant des erreurs** : nombre total d’appareils présentant une erreur.

La file d’attente d’intégrité de l’appareil répertorie tous les appareils configurés pour les preuves d’investigation dans votre organisation. En outre, le rapport répertorie l’état des attributs d’appareil suivants :

- **Nom** de l’appareil : nom de l’appareil, défini par l’attribut *ComputerName* de l’appareil.
- **État de l’appareil** : état du client Microsoft Purview sur l’appareil. Les valeurs d’état sont les suivantes :
    - ***Sain*** : le client sur l’appareil fonctionne correctement et les fonctionnalités de capture des preuves d’investigation sont entièrement prises en charge.
    - ***Avertissement*** : le client sur l’appareil dispose d’un avertissement et les fonctionnalités de capture des preuves forensiques peuvent ne pas être entièrement prises en charge.
    - ***Erreur*** : le client sur l’appareil présente une erreur et les fonctionnalités de capture des preuves d’investigation sont désactivées ou ne sont pas entièrement prises en charge.
- **Détails de l’état** : plus d’informations sur l’état de l’appareil.
- **Dernière synchronisation (UTC)** : date et heure de la dernière synchronisation d’état de l’appareil.
- **Nom d’utilisateur** : nom d’utilisateur de l’utilisateur connecté à l’appareil lors de la synchronisation de l’état.
- **Version de Windows** : version de Microsoft Windows installée sur l’appareil.
- **Version du client** : version du client Microsoft Purview installée sur l’appareil.

L’état d’intégrité de l’appareil vous donne des informations sur les problèmes potentiels liés à vos appareils et au client Microsoft Purview. La colonne **État** de l’appareil de la page **Intégrité** de l’appareil peut vous avertir des problèmes d’appareil susceptibles d’empêcher la capture de l’activité des utilisateurs ou de la raison pour laquelle le volume de capture de preuves d’investigation est inhabituel. L’état d’intégrité de l’appareil peut également confirmer que les appareils inclus dans la capture des preuves forensiques sont sains et ne nécessitent pas d’attention ou de modification de la configuration. Le tableau suivant répertorie les messages de détails d’état potentiels et les actions recommandées que vous pouvez effectuer pour résoudre les avertissements et les erreurs :

|**Détails de l’état**|**État**|**Action suggérée**|
|:----------|:-------|:-------------------|
| Une erreur serveur interne s'est produite. Par conséquent, les données de capture peuvent être manquantes. | Error | Créer un ticket de support avec Microsoft pour une investigation plus approfondie |
| La bande passante de chargement a atteint 90 % de la limite configurée sur cet appareil. Les captures peuvent bientôt être remplacées.  | Avertissement | Augmentez la limite de bande passante de chargement sur la page [paramètres de preuve d’investigation](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) . |
| La limite de bande passante de chargement configurée a été atteinte sur cet appareil. Plus aucune capture ne sera chargée pour la journée. | Error | Augmentez la limite de bande passante de chargement sur la page [paramètres de preuve d’investigation](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) . |
| Le stockage hors connexion a atteint 90 % de la limite configurée sur cet appareil. Les captures peuvent bientôt être remplacées.  | Avertissement | Augmentez la limite de cache de capture hors connexion dans la page [paramètres des preuves d’investigation](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) . |
| La limite de stockage hors connexion configurée a été atteinte sur cet appareil. Par conséquent, les captures hors connexion sont remplacées. | Error | Augmentez la limite de cache de capture hors connexion dans la page [paramètres des preuves d’investigation](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) . |
| L’utilisation du processeur sur l’appareil a dépassé le seuil maximal. | Error | Le processus de capture a été arrêté et redémarrera dans quelques minutes. |
| L’utilisation de la mémoire sur l’appareil a dépassé le seuil maximal. | Error | Le processus de capture a été arrêté et redémarrera dans quelques minutes. |
| L’utilisation du GPU sur l’appareil a dépassé le seuil maximal. | Error | Le processus de capture a été arrêté et redémarrera dans quelques minutes. |
| Le client Microsoft Purview installé sur l’appareil ne peut pas se synchroniser avec la stratégie de preuve d’investigation. | Avertissement | Se connecter au réseau & réinstaller le client |
| Le client Microsoft Purview installé sur l’appareil n’a pas été synchronisé avec la stratégie de preuve d’investigation depuis plus de 24 heures. | Error | Se connecter au réseau & réinstaller le client |
| Le client Microsoft Purview ne peut pas capturer l’activité, car aucune carte graphique n’est détectée sur cet appareil. | Error | Ajouter une carte graphique ou remplacer l’appareil par une carte graphique |
| Le client Microsoft Purview ne peut pas capturer l’activité, car aucun moniteur d’affichage n’est détecté sur cet appareil. | Error | Ajouter des moniteurs d’affichage pour cet appareil |
| Le client Microsoft Purview ne peut pas capturer l’activité, car les moniteurs d’affichage sur cet appareil ont été désactivés ou déconnectés. | Error | Connecter/activer les moniteurs d’affichage de l’appareil |
| L’appareil ne peut pas accéder au répertoire qui stocke les captures de preuves d’investigation. | Error | Réinstaller le client sur cet appareil |
| Échec de l’initialisation de l’encodeur.  | Error | Réinstallez le client sur cet appareil. |

Contactez Support Microsoft si les actions recommandées ne résolvent pas les problèmes liés au client.
