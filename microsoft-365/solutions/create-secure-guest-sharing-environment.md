---
title: Créer un environnement de partage d’invités sécurisé
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-security-compliance
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Découvrez les options disponibles pour créer un environnement de partage d’invités sécurisé dans Microsoft 365, offrant un accès invité pour une collaboration améliorée.
ms.openlocfilehash: ae616bcaa78aa759ca5b1f1be4b1beaf8d709a00
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62807607"
---
# <a name="create-a-secure-guest-sharing-environment"></a>Créer un environnement de partage d’invités sécurisé

Dans cet article, nous allons découvrir de nombreuses options permettant de créer un environnement de partage d’invités sécurisé dans Microsoft 365. Voici des exemples pour vous donner une idée des options disponibles. Vous pouvez utiliser ces procédures dans différentes combinaisons pour répondre aux besoins de sécurité et de conformité de votre organisation.

Cet article contient les rubriques suivantes :

- Configuration de l'authentification multifacteur pour les invités.
- Configuration des conditions d’utilisation pour les invités.
- Configuration des révisions trimestrielles d’accès invité pour vérifier régulièrement si les invités ont toujours besoin d’autorisations pour les équipes et les sites.
- Limitation de l’accès des invités au Web uniquement pour les appareils non gérés.
- Configuration d’une stratégie de délai d’expiration de session pour assurer l’authentification quotidienne des invités.
- Création d’un type d’informations sensibles pour un projet hautement sensible.
- Attribution automatique d’une étiquette de confidentialité aux documents contenant un type d’informations sensibles.
- Suppression automatique de l’accès invité aux fichiers avec une étiquette de confidentialité.

Certaines des options décrites dans cet article exigent que les invités disposent d’un compte dans Azure Active Directory. Pour vous assurer que les invités sont bien inclus dans le répertoire lorsque vous partagez des fichiers et des dossiers avec eux, utilisez l’[intégration de SharePoint et OneDrive avec Azure AD B2B Préversion](/sharepoint/sharepoint-azureb2b-integration-preview).

Notez que nous n'aborderons pas l'activation des paramètres de partage des invités dans cet article. Consultez la rubrique [Collaborer avec des personnes extérieures à votre organisation](collaborate-with-people-outside-your-organization.md) pour plus d’informations sur l'activation du partage des invités pour différents scénarios.

## <a name="set-up-multi-factor-authentication-for-guests"></a>Configurer l'authentification multifacteur pour les invités.

L’authentification multifacteur réduit considérablement les risques de compromission d’un compte. Puisque les invités peuvent utiliser des comptes d’e-mail personnels qui n’adhère à aucune stratégie de gouvernance ou bonne pratique, il est particulièrement important d’exiger une authentification multifacteur pour les invités. En cas de vol du nom d'utilisateur et du mot de passe d’un invité, la nécessité d’un second facteur d'authentification réduit considérablement les chances de voir des inconnus accéder à vos sites et fichiers.

Dans cet exemple, nous allons configurer l’authentification multifacteur pour les invités à l’aide d’une stratégie d’accès conditionnel dans Azure Active Directory.

Pour configurer l'authentification multifacteur pour les invités, procédez comme suit :

1. Accédez à [Stratégies d’accès conditionnel Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Dans le panneau **Accès conditionnel | Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans le champ **Nom** , tapez un nom.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**.
6. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
7. Dans le panneau **Actions ou applications Cloud**, sélectionnez **Toutes les applications Cloud** sous l’onglet **Inclure**.
8. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
9. Dans le panneau **Accorder**, activez la case à cocher **Exiger une authentification multifacteur**, puis cliquez sur **Sélectionner**.
10. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

Les invités doivent maintenant s'inscrire à l'authentification multifacteur avant de pouvoir accéder au contenu, aux sites ou aux équipes partagés.

### <a name="more-information"></a>Plus d’informations

[Planifier le déploiement d’une authentification multifacteur Azure AD](/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a>Configurer les conditions d’utilisation pour les invités

Dans certains cas, Il arrive souvent que des invités n'aient pas signé de contrat de non-divulgation ou d’autres accords juridiques avec votre organisation. Vous pouvez demander aux invités d’accepter les conditions d’utilisation avant d’accéder aux fichiers partagés avec eux. Les conditions d’utilisation peuvent s’afficher lors de la première tentative d’accès à un fichier ou à un site partagé.

Pour créer des conditions d’utilisation, vous devez commencer par créer le document dans Word ou dans un autre logiciel de création, puis l’enregistrer sous forme de fichier .pdf. Ce fichier peut alors être chargé dans Azure AD.

Pour créer des conditions d’utilisation d’Azure AD, procédez comme suit :

1. Connectez-vous à Azure en tant qu’administrateur général, administrateur de sécurité ou administrateur d’accès conditionnel.
2. Accédez aux [Conditions d’utilisation](https://aka.ms/catou).
3. Cliquez sur **Nouvelles conditions d’utilisation**.

   ![Capture d'écran des paramètres des nouvelles conditions d'utilisation d'Azure AD.](../media/azure-ad-guest-terms-of-use.png)

4. Tapez un **Nom** et **Nom d'affichage**.
6. Pour le **document Conditions d'utilisation**, accédez au fichier PDF que vous avez créé et sélectionnez-le.
7. Sélectionnez la langue de votre document Conditions d’utilisation.
8. Validez l'option **Demander aux utilisateurs d'étendre les conditions d'utilisation** en la définissant sur **ACTIVÉ**.
9. Sous **Accès conditionnel**, dans la liste **Appliquer le modèle de stratégie sur l'accès conditionnel**, choisissez **Créer une stratégie d'accès conditionnel ultérieurement**.
10. Cliquez sur **Créer**.

Une fois que vous avez créé les conditions d’utilisation, l’étape suivante consiste à créer une stratégie d’accès conditionnel qui affiche les conditions d’utilisation sur les systèmes des utilisateurs invités.

Pour créer une stratégie d’accès conditionnel, procédez comme suit :

1. Accédez à [Stratégies d’accès conditionnel Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Dans le panneau **Accès conditionnel | Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans le champ **Nom**, tapez un nom.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**.
6. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
7. Sous l'onglet **Inclure**, sélectionnez **Sélectionner les applications**, puis cliquez sur **Sélectionner**.
8. Dans le panneau **Sélectionner**, sélectionnez **Microsoft Teams**, **Office 365 SharePoint Online** et **Outlook Groups**, puis cliquez sur **Sélectionner**.
9. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
10. Dans le panneau **Accorder**, sélectionnez **Conditions d’utilisation de l’invité**, puis cliquez sur **Sélectionner**.
11. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

À présent, la première fois qu’un invité tente d’accéder au contenu, à une équipe ou à un site de votre organisation, il est tenu d’accepter les conditions d’utilisation.

> [!NOTE]
> L’utilisation de l’accès conditionnel nécessite une licence Azure AD Premium P1. Pour en savoir plus, consultez l'article [Qu’est-ce que l’accès conditionnel ?](/azure/active-directory/conditional-access/overview).

### <a name="more-information"></a>Plus d’informations

[Conditions d’utilisation d’Azure Active Directory](/azure/active-directory/conditional-access/terms-of-use).

## <a name="set-up-guest-access-reviews"></a>Configurer les révisions d’accès invité

Avec les révisions d’accès dans Azure AD, vous pouvez automatiser une révision périodique de l’accès des utilisateurs à plusieurs équipes et groupes. En exigeant spécifiquement une révision d’accès pour les invités, vous pouvez veiller à ce que les invités ne conservent pas l’accès aux informations sensibles de votre organisation plus longtemps que nécessaire.

Configurer une révision d’accès des invités

1. Sur la [Page de Gouvernance d’identité](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade), dans le menu de gauche, cliquez sur **Révisions d’accès**.
2. Cliquez sur **Nouvelle révision d’accès**.
3. Sélectionnez l’option **Équipes + groupes**.
4. Sélectionnez l'option **Tous les groupes Microsoft 365 avec des utilisateurs invités**. Cliquez sur **Sélectionner les groupes à exclure** si vous voulez exclure des groupes.
5. Sélectionnez l'option **Uniquement les utilisateurs invités**, puis cliquez sur **Suivant : Révisions**.
6. Sous **Sélectionner les réviseurs**, sélectionnez **Propriétaires du groupe**.
7. Cliquez sur **Sélectionner les réviseurs de secours**, choisissez les réviseurs, puis cliquez sur **Sélectionner**.
8. Sous **Spécifier la périodicité de l'évaluation**, choisissez **Trimestriel**.
9. Sélectionnez une date de début et une durée.
10. Pour **Fin**, sélectionnez **Jamais**, puis cliquez sur **Suivant : Paramètres**.

    ![Capture d’écran de l’onglet Révision de l’accès à Azure AD.](../media/azure-ad-create-access-review.png)

11. Sous l’onglet **Paramètres**, examinez les paramètres de conformité aux règles de votre entreprise.

    ![Capture d’écran de l’onglet des paramètres de révision d’accès d’Azure AD.](../media/azure-ad-create-access-review-settings.png)

12. Cliquez sur **Suivant : Révision + Créer**.
13. Tapez un **nom de révision**, puis examinez les paramètres.
14. Cliquez sur **Créer**.

Il est important de noter que pour les emplacements SharePoint et OneDrive, les documents sont bloqués de manière proactive juste après la détection d’informations sensibles, que le document soit partagé ou non, pour tous les utilisateurs externes, tandis que les utilisateurs internes continueront d’avoir accès au document.

### <a name="more-information"></a>Plus d’informations

[Gérer l’accès invité avec les révisions d’accès Azure AD](/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[Créer une révision d'accès de groupes ou d'applications dans les révisions d'accès Azure AD](/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guests"></a>Configurer l’accès Web uniquement pour les invités

Vous pouvez réduire votre surface d'attaque, puis simplifier l'administration en demandant aux invités d'accéder à vos équipes, sites et fichiers en utilisant uniquement un navigateur Web.

Pour les groupes et équipes Microsoft 365, cette opération s’effectue à l’aide d’une stratégie d’accès conditionnel Azure AD. Pour SharePoint, celui-ci est configuré dans le centre d’administration SharePoint. (Vous pouvez également [utiliser des étiquettes de confidentialité pour restreindre l’accès web uniquement aux invités](../compliance/sensitivity-labels-teams-groups-sites.md).)

Pour restreindre l'accès des invités au web uniquement pour les groupes et Microsoft Teams :

1. Accédez à [Stratégies d’accès conditionnel Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Dans le panneau **Accès conditionnel – Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans le champ **Nom**, tapez un nom.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**.
6. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
7. Sous l'onglet **Inclure**, sélectionnez **Sélectionner les applications**, puis cliquez sur **Sélectionner**.
8. Dans le panneau **Sélectionner**, sélectionnez **Microsoft Teams**, et **Outlook Groups**, puis cliquez sur **Sélectionner**.
9. Sous **Affectations**, cliquez sur **Conditions**.
10. Dans le panneau **Conditions**, cliquez sur **Applications clientes**.
11. Dans le panneau **Applications clientes**, cliquez sur **Oui** pour **Configurer**, puis sélectionnez les paramètres **Applications mobiles et clients de bureau**, **Clients Exchange ActiveSync**, et **Autres clients**. Décochez la case **Navigateur**.

    ![Capture d'écran des paramètres des applications clientes à accès conditionnel d'Azure AD.](../media/azure-ad-conditional-access-client-mobile.png)

12. Cliquez sur **Terminé**.
13. Sous **Contrôles d’accès**, cliquez sur **Accorder**.
14. Sur le panneau **Accorder**, sélectionnez les options **Exige que l’appareil soit marqué comme conforme** et **Exige un appareil joint Azure AD Hybride**.
15. Sous **Pour plusieurs contrôles**, sélectionnez **Exige l’un des contrôles sélectionnés**, puis cliquez sur **Sélectionner**.
16. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

Pour limiter l'accès web uniquement aux invités pour SharePoint

1. Dans le [Centre d’administration SharePoint](https://admin.microsoft.com/sharepoint), développez **Stratégies** et cliquez sur **Contrôle d’accès**.
2. Cliquez **Appareils non gérés**.
3. Sélectionnez l’option **Autoriser un accès limité, uniquement sur le web**, puis cliquez sur **Enregistrer**.

Notez que ce paramètre dans le Centre d’administration SharePoint crée une stratégie d’accès conditionnel de prise en charge dans Azure AD.

## <a name="configure-a-session-timeout-for-guests"></a>Configurer une stratégie de délai d’expiration de session pour les invités

Exiger des invités qu’ils s’authentifient régulièrement peut réduire le risque que des utilisateurs inconnus accèdent au contenu de votre organisation si l'appareil d'un invité n'est pas sécurisé. Vous pouvez configurer une stratégie d’accès conditionnel de délai d’expiration de session pour les invités dans Azure AD.

Pour configurer une stratégie de délai d’expiration de session d’invité, procédez comme suit :

1. Accédez à [Stratégies d’accès conditionnel Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Dans le panneau **Accès conditionnel – Stratégies**, cliquez sur **Nouvelle stratégie**.
3. Dans la zone **Nom**, tapez *Délai d’expiration de session des invités*.
4. Sous **Affectations**, cliquez sur **Utilisateurs et groupes**.
5. Dans le panneau **Utilisateurs et groupes**, sélectionnez **Sélectionner Utilisateurs et groupes**, activez la case à cocher **Tous les invités et utilisateurs externes**.
6. Sous **Affectations**, cliquez sur **Actions ou applications Cloud**.
7. Sous l'onglet **Inclure**, sélectionnez **Sélectionner les applications**, puis cliquez sur **Sélectionner**.
8. Dans le panneau **Sélectionner**, sélectionnez **Microsoft Teams**, **Office 365 SharePoint Online** et **Outlook Groups**, puis cliquez sur **Sélectionner**.
9. Sous **Contrôles d’accès**, cliquez sur **Session**.
10. Dans le panneau **Session**, sélectionnez **Fréquence de connexion**.
11. Sélectionnez **1** et **Jours** pour la période, puis cliquez sur **Sélectionner**.
12. Dans le panneau **Nouveau**, sous **Activer la stratégie**, cliquez sur **Activer**, puis sur **Créer**.

## <a name="create-a-sensitive-information-type-for-a-highly-sensitive-project"></a>Créer un type d’informations sensibles pour un projet hautement sensible

Les types d’informations sensibles sont des chaînes prédéfinies qui peuvent être utilisées dans les flux de travail de stratégie afin d’appliquer les exigences de conformité. Le Centre de conformité Microsoft 365 est fourni avec plus d’une centaine de types d’informations sensibles, y compris les numéros de permis de conduire, les numéros de cartes de crédit, les numéros de comptes bancaires, etc.

Vous pouvez créer des types d'informations sensibles personnalisés pour vous aider à gérer le contenu propre à votre organisation. Dans cet exemple, vous allez créer un type d’informations sensibles personnalisé pour un projet hautement sensible. Vous pouvez ensuite utiliser ce type d’informations sensibles pour appliquer automatiquement une étiquette de confidentialité.

Pour créer un type d’informations sensibles personnalisé, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), dans le volet de navigation gauche, développez **Classification**, puis cliquez sur **Types d’informations sensibles**.
2. Cliquez sur **Créer**.
3. Pour **Nom** et **Description**, tapez **Projet Saturne**, puis cliquez sur **Suivant**.
4. Cliquez sur **Ajouter un élément**.
5. Dans la liste **Détecter le contenu contenant**, sélectionnez **Mots clés**, puis tapez *Projet Saturne* dans la zone de mot clé.
6. Cliquez sur **Suivant**, puis sur **Terminer**.
7. Si vous êtes invité à tester le type d’informations sensibles, cliquez sur **Non**.

### <a name="more-information"></a>Plus d’informations

[Types d’informations sensibles personnalisés](/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-an-auto-labeling-policy-to-assign-a-sensitivity-label-based-on-a-sensitive-information-type"></a>Créer une stratégie d’attribution automatique d’étiquette pour affecter une étiquette de confidentialité sur la base d’un type d’informations sensibles

Si vous utilisez des étiquettes de confidentialité au sein de votre organisation, vous pouvez appliquer automatiquement une étiquette aux fichiers qui contiennent des types d’informations sensibles définis. 

Pour créer une stratégie d’étiquetage automatique :

1. Ouvrez le [centre d’administration de la conformité Microsoft 365](https://compliance.microsoft.com).
2. Dans le volet de navigation gauche, cliquez sur **Protection des informations**.
3. Sous l’onglet **Étiquetage automatique**, cliquez sur **Créer une stratégie d’étiquetage automatique**.
4. Sur la page **Sélectionnez les informations que vous voulez appliquer à**, sélectionnez **Personnaliser** , puis cliquez sur **Suivant**.
5. Entrez le nom et une description de la stratégie, puis cliquez sur **Suivant**.
6. Dans la page **Sélectionnez l’emplacement où vous voulez appliquer l’étiquette**, activez **Sites SharePoint** , puis cliquez sur **Choisir le sites**.
7. Ajoutez les URL des sites sur lesquels vous voulez activer l’étiquetage automatique, puis cliquez sur **Terminé**.
8. Cliquez sur **Suivant**.
9. Dans la page **Configurer les règles courantes ou avancées** , sélectionnez **Règles courantes** et cliquez sur **Suivant**.
10. Dans la page **Définir des règles pour le contenu de tous les emplacements** , cliquez sur **Nouvelle règle**.
11. Dans la page **Nouvelle règle** , attribuez un nom à la règle, cliquez sur **Ajouter une condition**, puis cliquez sur **Le contenu contient des types d’informations sensibles**.
12. Cliquez sur **Ajouter**, cliquez sur **Types d’informations sensibles**, sélectionnez les types d’informations sensibles que vous souhaitez utiliser, cliquez sur **Ajouter**, puis sur **Enregistrer**.
13. Cliquez sur **Suivant**.
14. Cliquez sur **Sélectionner une étiquette**, sélectionnez l’étiquette que vous voulez utiliser, puis cliquez sur **Ajouter**.
15. Cliquez sur **Suivant**.
16. Laissez la stratégie en mode de simulation, puis cliquez sur **Suivant**.
17. Cliquez sur **Créer une stratégie**, puis cliquez sur **Terminé**.

Une fois la stratégie en place, lorsqu’un utilisateur tape « Projet Saturne » dans un document, la stratégie d’étiquetage automatique applique automatiquement l’étiquette spécifiée lors de l’analyse du fichier.

### <a name="more-information"></a>Plus d’informations

[Appliquer automatiquement une étiquette de confidentialité au contenu](../compliance/apply-sensitivity-label-automatically.md)

## <a name="create-a-dlp-policy-to-remove-guest-access-to-highly-sensitive-files"></a>Créer une stratégie DLP pour supprimer l’accès invité aux fichiers hautement sensibles

Vous pouvez utiliser la [protection contre la perte de données (DLP)](../compliance/dlp-learn-about-dlp.md) pour empêcher le partage de contenu sensible indésirable. La protection contre la perte de données peut prendre des mesures basées sur l’étiquette de confidentialité d’un fichier et supprimer l’accès invité.

Création d’une stratégie DLP

1. Dans le Centre de conformité Microsoft 365, accédez à la [page de protection contre la perte de données](https://compliance.microsoft.com/datalossprevention).
2. Cliquez sur la stratégie **Créer**.
3. Sélectionnez **Personnaliser**, puis cliquez sur **Suivant**.
4. Tapez un nom pour la stratégie, puis cliquez sur **Suivant**.
5. Dans la page **Emplacements pour appliquer la stratégie**, désactivez tous les paramètres, sauf **Sites SharePoint** et **Comptes OneDrive**, puis cliquez sur **Suivant**.
6. Sur la page **Définir les paramètres de stratégie**, cliquez sur **Suivant**.
7. Sur la page **Personnaliser les règles avancées de protection contre la perte de données** , cliquez sur **Créer une règle**, puis tapez un nom pour la règle.
8. Sous **Conditions**, cliquez sur **Ajouter une condition**, puis sélectionnez **Le contenu contient**.
9. Cliquez sur **Ajouter**, sélectionnez **Étiquettes de confidentialité**, sélectionnez les étiquettes à utiliser, puis cliquez sur **Ajouter**.

   ![Capture d’écran des options de conditions, types d’informations sensibles, étiquettes de confidentialité et étiquettes de rétention.](../media/limit-accidental-exposure-dlp-conditions.png)

10. Sous **Actions** cliquez sur **Ajouter une action**, puis sélectionnez **Restreindre l’accès ou chiffrer le contenu dans des emplacements Microsoft 365**.
11. Activez la case à cocher **Restreindre l’accès ou chiffrer le contenu dans les emplacements Microsoft 365** , puis sélectionnez l’option **Uniquement les personnes extérieures à votre organisation**.

      ![Capture d’écran des options d’action de règle de protection contre la perte de données.](../media/dlp-remove-guest-access-sensitive-files.png)

12. Cliquez sur **Enregistrer**, puis sur **Suivant**.
13. Sélectionnez vos options de test, puis cliquez sur **Suivant**.
14. Cliquez sur **Envoyer**, puis sur **Terminé**.

Il est important de noter que cette stratégie ne supprime pas l’accès si l’invité est membre du site ou de l’équipe. Si vous comptez utiliser des documents hautement sensibles dans un site ou une équipe comptant des membres invités, envisagez d'utiliser des c[anaux privés dans Teams ](https://support.microsoft.com/office/de3e20b0-7494-439c-b7e5-75899ebe6a0e)et d'autoriser uniquement les membres de votre organisation dans les canaux privés.

## <a name="additional-options"></a>Options supplémentaires

D'autres options existent dans Microsoft 365 et Azure Active Directory vous permettant de sécuriser votre environnement de partage d'invités.

- Vous pouvez créer une liste de domaines de partage autorisés ou refusés pour limiter les personnes avec lesquelles les utilisateurs peuvent effectuer des partages. Pour plus d’informations, consultez [Restreindre le partage de contenu SharePoint et OneDrive par domaine](/sharepoint/restricted-domains-sharing) et [Autoriser ou bloquer des invitations à des utilisateurs B2B d’organisations spécifiques](/azure/active-directory/b2b/allow-deny-list).
- Vous pouvez également limiter d'autres locataires Azure Active Directory avec lesquels vos utilisateurs peuvent se connecter. Pour plus d'informations, voir [Utilisez les restrictions liées au locataire pour gérer l’accès aux applications cloud SaaS](/azure/active-directory/manage-apps/tenant-restrictions).
- Vous pouvez créer un environnement géré dans lequel vos partenaires peuvent vous aider à gérer des comptes d'invités. Pour plus d’informations, voir [Créer un extranet B2B avec des invités gérés](/Office365/Enterprise/b2b-extranet).

## <a name="see-also"></a>Voir aussi

[Limiter l’exposition accidentelle aux fichiers lors du partage avec des invités](share-limit-accidental-exposure.md)

[Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)

[Créer un extranet B2B avec des invités gérés](b2b-extranet.md)
