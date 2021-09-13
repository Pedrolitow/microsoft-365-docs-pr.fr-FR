---
title: Utiliser Microsoft Teams classes avec Blackboard Learn Ultra
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Utiliser Microsoft Teams classes avec Blackboard Learn Ultra
ms.openlocfilehash: 30ab28c4a9c2431a63db976df13748de6b843fdc
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59165233"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Utiliser Microsoft Teams classes avec Blackboard Learn Ultra

Le travail d’équipe est au cœur de chaque organisation moderne. En favorisant la collaboration, il s’agit d’une caractéristique de définition de chaque établissement réussi. Vous pouvez améliorer toutes les fonctionnalités de Blackboard Learn Ultra en les couplant avec Microsoft Teams classes.

Vos classes peuvent inclure des conversations en temps réel, des réunions vidéo ou des interactions asynchrones. Vous pouvez ajouter des expériences de partage de fichiers et de cocréation pour vos étudiants, le tout au même endroit. Microsoft Teams classes avec Learn Ultra redéfinissent la dynamique de l’enseignement et ce que signifie un apprentissage efficace.

> [!IMPORTANT]
> Assurez-vous que vous avez correctement installé le champ Courrier de l’établissement dans votre système d’information sur les [étudiants (SIS)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>L’intégration Microsoft Teams classes s’appuie sur le champ de messagerie de l’établissement dans votre SIS pour ma Microsoft Azure Active Directory le nom d’utilisateur principal [(UPN)](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)(AAD) de l’Microsoft Azure Active Directory correct. Si aucun courrier électronique de l’établissement n’a été mis en service, il s’adresse par défaut au courrier électronique existant. Il est recommandé de définir ce champ pour que chaque utilisateur s’assure que ses données sont synchronisées correctement et qu’il n’existe aucun conflit de données de courrier entre AAD et Blackboard Learn Ultra.
>
> Si vous n’avez pas correctement définie ce champ dans votre mappage SIS, l’intégration continue de fonctionner, mais les utilisateurs peuvent ne pas apparaître dans les classes Teams créées et des erreurs peuvent se produire.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Prise en charge du mappage de données institutionnalisé : champ SIS de messagerie de l’établissement

Dans le cadre de l’évolution avec les intégrations  de fournisseurs cloud, Blackboard Learn Ultra a créé un nouveau champ Courrier électronique de l’établissement, à la fois dans l’intégration de Student Information System Framework et dans les API REST publiques, ce qui permet aux établissements de gérer efficacement le processus de synchronisation des données entre Blackboard Learn Ultra et AAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Que signifie le courrier électronique de l’établissement et qu’est-ce qu’il prend en charge ?

Le **champ Courrier électronique** de l’établissement permet de personnaliser les mappages de champs entre les sources de données d’un client pris en charge en externe et blackboard Learn Ultra. Si les sources de données sont des fournisseurs cloud, tels que Microsoft, le nom d’utilisateur principal (UPN) est un identificateur unique principal pour chaque utilisateur constitué d’un préfixe UPN (nom de compte de l’utilisateur) et d’un suffixe UPN (un nom de domaine DNS) associé à un symbole @. Cela crée une adresse e-mail unique pour chaque utilisateur spécifique au sein du Microsoft Azure Active Directory.

Pour garantir que les données sont exactes et que les inscriptions ou appartenances entre les classes Blackboard Learn Ultra et Microsoft Teams sont correctement obtenues, l’adresse e-mail d’un utilisateur doit correspondre entre les deux systèmes. Dans Blackboard Learn Ultra, les utilisateurs peuvent modifier ou remplacer leur adresse de messagerie existante dans l’interface utilisateur, ce qui peut entraîner des erreurs de synchronisation et l’ajout de l’utilisateur à une équipe de classe. Le **mappage** de champ Courrier électronique de l’établissement garantit que ce niveau de vérification de la sécurité et de la validation peut être géré correctement, que les utilisateurs ont modifié leur courrier électronique dans Blackboard Learn Ultra ou non.

 Lorsque deux adresses de messagerie sont différentes, l’une ou l’autre :

- Une décision doit être prise quant à la source qui est prioritaire et qui sera prise à la fois comme courrier électronique de la personne et de l’établissement.
  Ou
- Un établissement peut définir un mappage de champ personnalisé dans son courrier électronique d’établissement, ce qui peut résoudre un conflit potentiel.

Le **mappage de** champ Courrier électronique de l’établissement est désormais disponible pour tous les types d’intégration SIS existants dans advanced **Configuration Paramètres** Users Learn  >  **Object Type** Field  >  **Mapping**.

> [!NOTE]
> Il est important de noter que, par défaut,  la messagerie de **l’établissement** est définie sur Courrier de la personne pour tous les formats SIS et doit être unique pour chaque personne. Toutes les intégrations existantes qui sont définies et en cours d’exécution auront ce mappage de données en place, car SIS ne pourra pas importer les utilisateurs si leur courrier électronique est dupliqué. Si un établissement a besoin de la possibilité de modifier le courrier  électronique de l’établissement en courrier **personnalisé,** il devra le gérer via la configuration avancée Paramètres dans le SIS.

## <a name="requirements"></a>Conditions requises

L Microsoft Teams des classes est disponible uniquement pour les cours **Ultra Course View.** Votre établissement doit remplir les conditions requises pour l’utiliser :

- Faire en savoir plus sur Blackboard Learn SaaS avec la navigation de base Ultra activée

  ![un exemple de fonctionnalité est activé dans les cours.](media/feature-availability.png)

- Activez LTI pour une utilisation dans les cours.

  a. Go to the **Administrator Panel**  >  **LTI Tool Providers**  >  **Manage Global Properties**.

  b. Sélectionnez **LTI activé dans les cours** et éventuellement Activé dans les **organisations.**

  c. Sélectionnez **Envoyer**.

- Doit avoir configuré LTI

- Ajouter Blackboard Learn Ultra Teams Classes LTI Integration

- Ajouter Microsoft Teams l’outil Classes LTI 1.3

- Ajouter l’outil API REST et le partage de ressources d’origine croisée

- Configurer et approuver l’intégration Microsoft Teams classes

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Ajouter l’outil Blackboard Learn Ultra Teams Classes LTI 1.3

1. Dans le **Panneau d’administration,** sélectionnez **Fournisseurs d’outils LTI.**

2. Sélectionnez **inscrire l’outil LTI 1.3.**

3. Dans le **champ ID client,** tapez ou copiez-collez cet ID :

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Examinez tous les paramètres qui ont été pré-remplis et dans l’état de l’outil, puis sélectionnez **Activé.**

5. Dans **Stratégies d’établissement,** **sélectionnez Rôle dans le cours,** le nom et l’adresse e-mail, puis sélectionnez **Oui** pour les deux.

6. Sélectionnez **Autoriser l’accès au service de qualité et** Autoriser **l’accès au service d’appartenance.**

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Ajouter l’Microsoft Teams Classes LTI 1.3

1. Dans le **Panneau d’administration,** sélectionnez **Fournisseurs d’outils LTI.**

2. Sélectionnez **inscrire l’outil LTI 1.3.**

3. Dans le **champ ID client,** tapez ou copiez-collez cet ID :

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Examinez tous les paramètres pré-remplis et dans État de *l’outil,* puis *sélectionnez Activé.*

5. Dans **les stratégies d’établissement,** **sélectionnez Le rôle dans le cours, le nom** et **l’adresse e-mail.** Sélectionnez **Oui** pour les deux.

6. Sélectionnez **Autoriser l’accès au service de qualité et** Autoriser **l’accès au service d’appartenance.**

## <a name="add-the-rest-api-tool"></a>Ajouter l’outil API REST

1. Dans le Panneau **d’administration,** accédez à **Intégrations** et sélectionnez **Intégrations de l’API Rest.**

2. Sélectionnez **Créer une intégration.**

3. Dans le **champ ID de** l’application, tapez ou copiez-collez cet ID :

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Tapez un utilisateur pour cette intégration.

   Cet utilisateur est celui qui a accès à l’API d’accueil à partir de laquelle l’application est associée.

5. Sélectionnez **Envoyer**.

## <a name="add-the-cross-origin-resource-sharing"></a>Ajouter le partage de ressources d’origine croisée

1. Dans le **panneau Administrateur,** accédez à **Intégrations** et sélectionnez **Partage de ressources d’origine croisée.*

2. Sélectionnez **Créer une configuration.**

3. Dans le **champ Origine,** type de copie et coller cette URL :

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. Dans le **champ En-têtes autorisés,** tapez **Autorisation**.

5. Définir **Disponible** sur **Oui**.

6. Sélectionnez **Envoyer**.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Configurer et approuver l’intégration Microsoft Teams classes

Pour intégrer correctement votre instance Blackboard Learn Ultra à des classes Microsoft Teams, vous devez vous assurer que l’application Blackboard Learn Ultra est approuvée pour l’accès au sein de votre client Microsoft Azure. Il s’agit d’un processus qui devra être effectué par l’administrateur Microsoft 365 de votre établissement.

Ce processus peut être effectué avant ou après avoir configuré les applications LTI dans votre tableau noir Learn Ultra Instance.

### <a name="before-configuring-the-lti-applications"></a>Avant de configurer les applications LTI

Si vous choisissez d’approuver l’application Azure Blackboard Learn Ultra Teams Classes avant de configurer les intégrations LTI, vous devez rediriger vers le point de terminaison de consentement de l’administrateur de la plateforme d’identités **Microsoft.** L’URL s’affiche :

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> Vous remplacerez **{Tenant}** par votre ID Microsoft Azure client spécifique.

Vous verrez une fenêtre d’autorisations qui explique que vous accordez l’autorisation à Blackboard Learn Ultra pour accéder à Microsoft Teams.

![fenêtre d’autorisations pour Microsoft et Tableau noir.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>Après avoir configuré les applications LTI

1. Dans le **Panneau d’administration,** accédez à Outils et **utilitaires** et sélectionnez **Microsoft Teams’intégration.**

2. Sélectionnez **Activer Microsoft Teams**.

3. Ajoutez **votre ID de client Microsoft** dans le champ de texte disponible.

4. Choisissez l’une des options suivantes :

   - Si l’application dispose d’un consentement préalable, elle affiche une petite coche. Si la coche s’affiche, sélectionnez **Envoyer.**

   - Si le consentement n’a pas été approuvé, suivez les étapes décrites pour générer l’URL de consentement et envoyez-la à l’administrateur Microsoft 365 pour approbation.

5. Une fois que vous avez confirmé l’approbation, sélectionnez **Retenter** pour confirmer, puis sélectionnez **Envoyer.**
