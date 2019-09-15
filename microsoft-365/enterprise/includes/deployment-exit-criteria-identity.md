Voir également les [Conditions préalables](https://docs.microsoft.com/microsoft-365-enterprise/identity-access-policies#prerequisites) pour consulter d’autre suggestions sur l’infrastructure d’identité.

<a name="crit-identity-user-groups"></a>
### <a name="required-your-users-groups-and-group-memberships-have-been-created"></a>Obligatoire : vos utilisateurs, groupes et appartenances aux groupes ont été créés

Vous avez créé des groupes et des comptes d’utilisateur afin que :

- Les employés au sein de votre organisation et les fournisseurs, entrepreneurs et partenaires qui travaillent pour ou avec votre organisation aient un compte d’utilisateur correspondant dans Azure Active Directory (AD) ;
- les groupes Azure AD et leurs membres contiennent des comptes d’utilisateur et d’autres groupes à des fins diverses (attribution de paramètres de sécurité pour les services de cloud computing Microsoft, attribution automatique de licences et autres utilisations).

Si nécessaire, l’[Étape 1](../identity-plan-users-groups.md) peut vous aider à répondre à cette exigence.

<a name="crit-identity-global-admin"></a>
### <a name="required-your-global-administrator-accounts-are-protected"></a>Obligatoire : vos comptes d’administrateur général sont protégés 

Vous avez [protégé vos comptes d’administrateur général Office 365](https://docs.microsoft.com/office365/enterprise/protect-your-global-administrator-accounts) pour empêcher que des attaques ne compromettent l'intégrité des informations d'identification, ce qui peut entraîner des violations de votre abonnement Microsoft 365.

Si vous ignorez cette exigence, vos comptes d’administrateur général peuvent être attaqués et compromis, autorisant un utilisateur à accéder à vos données à l’échelle du système à des fins de collecte, destruction ou prise en otage des données.

Si nécessaire, l’[Étape 2](../identity-designate-protect-admin-accounts.md#identity-global-admin) peut vous aider à répondre à cette exigence.

#### <a name="how-to-test"></a>Procédure de test

Suivez ces étapes pour vérifier que vous avez protégé vos comptes d’administrateur général :

1. Exécutez la commande Azure Active Directory PowerShell pour Graph suivante à l’invite de commandes PowerShell. Vous devriez voir uniquement la liste des comptes d’administrateur général dédiés.
   ```
   Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
   ```
2. Connectez-vous à Office 365 à l’aide de chacun des comptes de l’étape 1. Chaque connexion doit exiger l’authentification multifacteur et la forme la plus forte d’authentification secondaire disponible dans votre organisation.

> [!Note]
> Reportez-vous à [Se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell) pour obtenir des instructions sur l’installation du module Azure AD PowerShell pour Graph et la connexion à Office 365.

<a name="crit-identity-pim"></a>
### <a name="optional-you-have-set-up-privileged-identity-management-to-support-on-demand-assignment-of-the-global-administrator-role"></a>Facultatif : vous avez configuré Privileged Identity Management pour prendre en charge l’affectation à la demande du rôle Administrateur général

Vous avez déjà suivi les instructions de la rubrique [Configuration d’Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) pour activer PIM dans votre client Azure AD et configuré vos comptes d’administrateur général comme administrateurs éligibles.

Vous avez également suivi les recommandations de la rubrique relative à la [sécurisation de l’accès privilégié pour les déploiements hybrides et cloud dans Azure AD](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices) pour développer une feuille de route qui sécurise l’accès privilégié contre les cyber-attaquants.

Si vous ignorez cette option, vos comptes Administrateur général sont soumis à des attaques en ligne en continu et, en cas de compromission, peuvent autoriser un utilisateur à recueillir, détruire ou conserver vos informations sensibles contre rançon.

Si nécessaire, l’[Étape 2](../identity-designate-protect-admin-accounts.md#identity-pim) peut vous aider avec cette option.


<a name="crit-identity-sync"></a>
### <a name="required-users-and-groups-are-synchronized-with-azure-ad"></a>Obligatoire : les utilisateurs et les groupes sont synchronisés avec Azure AD

Si vous disposez déjà des services de domaine Active Directory (AD DS) locaux, vous avez utilisé Azure AD Connect pour synchroniser les comptes et groupes d'utilisateurs depuis vos services AD DS locaux vers votre client Azure AD.

Avec la synchronisation d’annuaires, vos utilisateurs peuvent se connecter à Office 365 et à d’autres services de cloud computing Microsoft à l’aide des mêmes informations d’identification qu’ils utilisent pour se connecter à leurs ordinateurs et accéder aux ressources locales.

Si nécessaire, l’[Étape 3](../identity-azure-ad-connect.md#identity-sync) peut vous aider à répondre à cette exigence.

Si vous ignorez cette exigence, vous aurez deux ensembles de groupes et comptes d’utilisateur :

- Groupes et comptes d’utilisateur qui existent dans vos services AD DS
- Groupes et comptes d’utilisateur qui existent dans votre client Azure AD

Dans cet état, les deux ensembles de groupes et comptes d’utilisateur doivent être gérés manuellement par les administrateurs informatiques et les utilisateurs. Cela entraînera inévitablement des groupes, leurs mots de passe et comptes non synchronisés.

#### <a name="how-to-test"></a>Procédure de test
Pour vérifier que l’authentification avec les informations d’identification locales fonctionne correctement, connectez-vous au portail Office avec vos informations d’identification locales.

Pour vérifier que la synchronisation d’annuaires fonctionne correctement, procédez comme suit :

1.  Créez un groupe de test dans AD DS.
2.  Attendez l’heure de synchronisation.
3.  Vérifiez votre client Azure AD pour vous assurer que le nouveau nom du groupe de test apparaît.

<a name="crit-identity-sync-health"></a>
### <a name="optional-directory-synchronization-is-monitored"></a>Facultatif : la synchronisation d’annuaires est surveillée

Vous avez utilisé [Utilisation d’Azure AD Connect Health pour la synchronisation](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) (pour la synchronisation de mot de passe) ou [Utilisation d’Azure AD Connect Health avec AD FS](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) (pour l’authentification fédérée) et avez déployé Azure AD Connect Health, ce qui implique :

- L’installation de l’agent Azure AD Connect Health sur chacun de vos serveurs d’identités local.
- L’utilisation du portail Azure AD Connect Health pour surveiller l’état de synchronisation en cours.

Si vous ignorez cette option, vous pouvez évaluer plus précisément l’état de votre infrastructure d’identités basée sur le cloud.

Si nécessaire, l’[Étape 3](../identity-azure-ad-connect.md#identity-sync-health) peut vous aider avec cette option.

#### <a name="how-to-test"></a>Procédure de test
Le portail Azure AD Connect Health affiche l’état actuel et correct de vos contrôleurs de domaine locaux et la synchronisation en cours.

<a name="crit-identity-mfa"></a>
### <a name="optional-multi-factor-authentication-is-enabled-for-your-users"></a>Facultatif : l’authentification multifacteur est activée pour vos utilisateurs

Vous avez utilisé [Offre pour l’authentification multifacteur ](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted) et les [stratégies d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted#enable-multi-factor-authentication-with-conditional-access) pour activer l’authentification multifacteur (MFA) pour vos comptes utilisateurs.

Si vous ignorez cette option, vos comptes d’utilisateur sont vulnérables à la compromission des informations d’identification par des cyber-attaquants. Si le mot de passe d’un compte d’utilisateur est compromis, toutes les ressources et les fonctionnalités du compte, telles que les rôles d’administrateur, sont disponibles pour l’utilisateur malveillant. Ainsi, ce dernier peut copier, détruire ou conserver des documents internes et d’autres données contre rançon.

Si nécessaire, l’[Étape 4](../identity-multi-factor-authentication.md#identity-mfa) peut vous aider avec cette option.

#### <a name="how-to-test"></a>Procédure de test

1.  Créez un compte utilisateur test et attribuez-lui une licence. 
2.  Configurez l’authentification multifacteur pour le compte utilisateur test avec la méthode de vérification supplémentaire que vous utilisez pour les comptes utilisateur réels, comme l’envoi d’un message texte sur votre téléphone. 
3.  Connectez-vous au portail Office 36 avec le compte utilisateur test.
4.  Vérifiez que l’authentification multifacteur vous invite à saisir les informations de vérification supplémentaires et que l’authentification s’effectue sans problèmes. 
5.  Supprimez le compte d’utilisateur test.

<a name="crit-password-prot"></a>
### <a name="optional-azure-ad-password-protection-is-banning-the-use-of-weak-passwords"></a>Facultatif : la protection de mot de passe Azure AD interdit l'utilisation de mots de passe faibles

Vous avez activé l'interdiction des mauvais mots de passe [dans le cloud](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad) et pour vos [services de domaine Active Directory (AD DS) locaux](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad-on-premises) pour les mots de passe généraux interdits et, éventuellement, pour les termes personnalisés.

Si nécessaire, l’[Étape 4](../identity-multi-factor-authentication.md#identity-password-prot) peut vous aider avec cette option.

<a name="crit-identity-ident-prot"></a>
### <a name="optional-azure-ad-identity-protection-is-enabled-to-protect-against-credential-compromise-microsoft-365-enterprise-e5-only"></a>Facultatif : Azure AD Identity Protection est activé pour vous protéger contre la compromission d’informations d’identification (Microsoft 365 Entreprise E5 uniquement)

Vous avez activé Azure AD Identity Protection pour :

- résoudre les vulnérabilités d’identités potentielles ;
- détecter les tentatives de compromission d’informations d’identification possibles ;
- examiner et résoudre des incidents d’identités suspects en cours.

Si vous ignorez cette option, vous ne pourrez pas détecter ou empêcher automatiquement les tentatives de compromission d’informations d’identification ni examiner des incidents de sécurité liés à l’identité. Cela rend votre organisation potentiellement vulnérable à une compromission d’informations d’identification réussie et à la menace qui en résulte pour les données sensibles de votre organisation.

Si nécessaire, l’[Étape 4](../identity-multi-factor-authentication.md#identity-ident-prot) peut vous aider avec cette option.

<a name="crit-identity-pw-reset"></a>
### <a name="optional-users-can-reset-their-own-passwords"></a>Facultatif : les utilisateurs peuvent réinitialiser leurs mots de passe

Vous avez utilisé la rubrique relative au [déploiement rapide de la réinitialisation du mot de passe libre-service Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started) pour configurer la réinitialisation du mot de passe pour vos utilisateurs.

Si vous ne remplissez pas cette condition, les utilisateurs dépendront des administrateurs de compte d’utilisateur pour réinitialiser leurs mots de passe, entraînant une surcharge d’administration informatique supplémentaire.

Si nécessaire, l’[Étape 5](../identity-password-reset.md#identity-pw-reset) peut vous aider avec cette option.

#### <a name="how-to-test"></a>Procédure de test

1. Créez un compte d’utilisateur test avec un mot de passe initial.
2. Suivez les étapes décrites dans [Autoriser les utilisateurs à réinitialiser leur mot de passe dans Office 365](https://docs.microsoft.com/office365/admin/add-users/let-users-reset-passwords) pour réinitialiser le mot de passe sur le compte d’utilisateur test.
3. Déconnectez-vous, puis connectez-vous au compte d’utilisateur test à l’aide du mot de passe réinitialisé.
4. Supprimez le compte d’utilisateur test.

<a name="crit-identity-pw-writeback"></a>
### <a name="optional-password-writeback-is-enabled-for-your-users"></a>Facultatif : l’écriture différée du mot de passe est activée pour vos utilisateurs

Vous avez déjà consulté les instructions de la rubrique relative à la [réinitialisation du mot de passe libre-service d’Azure AD (SSPR) avec l’écriture différée du mot de passe](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started) pour activer l’écriture différée du mot de passe pour le client Azure AD de votre abonnement Microsoft 365 Entreprise.

Si vous ignorez cette option, les utilisateurs qui ne sont pas connectés à votre réseau local doivent réinitialiser ou déverrouiller leurs mot de passe AD DS en faisant appel à un administrateur informatique.

Si nécessaire, l’[Étape 5](../identity-password-reset.md#identity-pw-writeback) peut vous aider avec cette option.

>[!Note]
>L’écriture différée du mot de passe est requise pour exploiter pleinement les fonctionnalités d’Azure AD Identity Protection, comme l’obligation pour les utilisateurs de modifier leurs mots de passe locaux lorsque Azure AD a détecté un risque élevé de compromission de compte.
>

#### <a name="how-to-test"></a>Procédure de test

Vous testez l’écriture différée de votre mot de passe en changeant votre mot de passe Office 365. Vous devriez pouvoir utiliser votre compte et le nouveau mot de passe pour accéder aux ressources AD DS locales.

1. Créez un compte utilisateur test dans votre version locale AD DS, autorisez la synchronisation d’annuaires, puis accordez-lui une licence Microsoft 365 Entreprise dans le Centre d’administration Microsoft 365.
2. Sur un ordinateur distant qui est relié à votre domaine Server AD DS local, connectez-vous à l’ordinateur et au portail Office à l’aide des informations d’identification du compte d’utilisateur test.
3. Sélectionnez **Paramètres > Paramètres Office 365 > Mot de passe > Changer le mot de passe**.
4. Tapez le mot de passe actuel, tapez un nouveau mot de passe, puis confirmez-le.
5. Déconnectez-vous du portail Office et de l’ordinateur distant, puis connectez-vous à l’ordinateur à l’aide du compte d’utilisateur de test et son nouveau mot de passe. Cela prouve que vous avez été en mesure de modifier le mot de passe d’une version locale de compte d’utilisateur AD DS à l’aide du client Azure AD.

<a name="crit-identity-sso"></a>
### <a name="optional-users-can-sign-in-using-azure-ad-seamless-single-sign-on"></a>Facultatif : les utilisateurs peuvent se connecter à l’aide de l’authentification unique Azure AD Single Sign-on

Vous avez activé l’[authentification unique transparente Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start) pour que votre organisation simplifie la manière dont les utilisateurs se connectent aux applications basées sur le cloud, comme Office 365.

Si vous ignorez cette option, vos utilisateurs peuvent être invités à fournir des informations d’identification lorsqu’ils accèdent à d’autres applications qui utilisent votre client Azure AD.

Si nécessaire, l’[Étape 5](../identity-password-reset.md#identity-sso) peut vous aider avec cette option.

<a name="crit-identity-custom-sign-in"></a>
### <a name="optional-the-office-365-sign-in-screen-is-personalized-for-your-organization"></a>Facultatif : l’écran de connexion Office 365 est personnalisé pour votre organisation

Vous avez utilisé [Ajouter la marque de votre organisation à votre page de connexion et aux pages du Panneau d’accès](http://aka.ms/aadpaddbranding) pour ajouter la marque de votre organisation à la page de connexion Office 365.

Si vous ignorez cette option, vos utilisateurs verront un écran de connexion Office 365 générique et peuvent ne pas être certains de se connecter au site de votre organisation.

Si nécessaire, l’[Étape 5](../identity-password-reset.md#identity-custom-sign-in) peut vous aider avec cette option.

#### <a name="how-to-test"></a>Procédure de test

Connectez-vous au portail Office 365 avec votre nom de compte d’utilisateur et l’authentification multifacteur. Vos éléments de marque personnalisés apparaissent sur la page de connexion.

<a name="crit-identity-self-service-groups"></a>
### <a name="optional-self-service-group-management-is-enabled-for-specific-azure-ad-security-and-office-365-groups"></a>Facultatif : la gestion des groupes en libre-service est activée pour des groupes Office 365 et de sécurité Azure AD spécifiques

Vous avez déterminé les groupes qui sont appropriés pour la gestion en libre service, décrit à leurs propriétaires les responsabilités et le workflow de gestion des groupes et [configuré la gestion en libre-service dans Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-self-service-group-management) pour ces groupes.

Si vous ignorez cette option, toutes les tâches de gestion des groupes Azure AD doivent être effectuées par des administrateurs informatiques.

Si nécessaire, l’[Étape 6](../identity-self-service-group-management.md#identity-self-service-groups) peut vous aider avec cette option.

#### <a name="how-to-test"></a>Procédure de test
1.  Créez un compte d’utilisateur test dans Azure AD avec le portail Azure.
2.  Connectez-vous comme avec le compte d’utilisateur test et créez un groupe de sécurité Azure AD test.
3.  Déconnectez-vous, puis connectez-vous avec votre compte Administrateur informatique.
4.  Configurez le groupe de sécurité test pour la gestion en libre service pour le compte d’utilisateur test.
5.  Déconnectez-vous, puis connectez-vous avec votre compte d’utilisateur test.
6.  Utilisez le portail Azure pour ajouter des membres au groupe de sécurité test.
7.  Supprimez le groupe de sécurité test et le compte d’utilisateur test.

<a name="crit-identity-dyn-groups"></a>
### <a name="optional-dynamic-group-membership-settings-automatically-add-user-accounts-to-groups-based-on-user-account-attributes"></a>Facultatif : les paramètres d’appartenance à un groupe dynamique ajoutent automatiquement des comptes d’utilisateur à des groupes en fonction des attributs de compte d’utilisateur

Vous avez déterminé l’ensemble des groupes dynamiques Azure AD et utilisé les instructions décrites dans la rubrique relative à l’[appartenance à un groupe dynamique en fonction des attributs dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal) pour créer les groupes et les règles qui déterminent l’ensemble des attributs de compte d’utilisateur et des valeurs pour l’appartenance à un groupe.

Si vous ignorez cette option, l’appartenance à un groupe doit être effectuée manuellement lorsque de nouveaux comptes sont ajoutés ou que les attributs de compte d’utilisateur changent au fil du temps. Par exemple, si une personne est mutée du service des ventes au service de comptabilité, vous devez :

- mettre à jour la valeur de l’attribut Service pour ce compte d’utilisateur ;
- le supprimer manuellement du groupe Ventes ;
- l’ajouter manuellement au groupe Comptabilité.

Si les groupes Ventes et Comptabilité sont dynamiques, vous devez uniquement modifier la valeur Service du compte d’utilisateur.

Si nécessaire, l’[Étape 6](../identity-self-service-group-management.md#identity-dyn-groups) peut vous aider avec cette option.

#### <a name="how-to-test"></a>Procédure de test

1. Créez un groupe dynamique test dans Azure AD avec le portail Azure et configurez une règle pour que Service soit égal à « test1 ».
2. Créez un compte d’utilisateur test dans Azure AD et définissez la propriété Service sur « test1 ».
3. Examinez les propriétés du compte d’utilisateur pour vous assurer qu’il a été défini comme membre du groupe dynamique test.
4. Modifiez la valeur de la propriété Service pour le compte d’utilisateur test et définissez-la sur « test2 ».
5. Examinez les propriétés du compte d’utilisateur pour vous assurer qu’il n’est plus membre du groupe dynamique test.
6. Supprimez le groupe dynamique test et le compte d’utilisateur test.

<a name="crit-identity-group-license"></a>
### <a name="optional-group-based-licensing-to-automatically-assign-and-remove-licenses-to-user-accounts-based-on-group-membership"></a>Facultatif : gestion des licences par groupes pour attribuer des licences aux comptes d’utilisateur et les supprimer automatiquement en fonction de l’appartenance au groupe

Vous [avez activé l'attribution de licences par groupe](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal) pour les groupes de sécurité Azure AD appropriés afin que des licences pour Microsoft 365 Entreprise soient automatiquement attribuées ou supprimées.

Si vous ignorez cette option, vous devez effectuer les opérations suivantes manuellement :

- Attribuer des licences aux nouveaux utilisateurs auxquels vous avez l'intention d'accéder.
- Supprimer les licences des utilisateurs qui ne font plus partie de votre organisation ou qui n'y ont pas accès.

Si nécessaire, l’[Étape 6](../identity-self-service-group-management.md#identity-group-license) peut vous aider avec cette option.

#### <a name="how-to-test"></a>Procédure de test

1. Créez un groupe de sécurité test dans Azure AD à l’aide du portail Azure et configurez l’attribution de licences par groupes pour attribuer des licences Microsoft 265 Enterprise.
2. Créez un compte d’utilisateur test dans Azure AD et ajoutez-le au groupe de sécurité test.
3. Examinez les propriétés du compte utilisateur dans le Centre d’administration Microsoft 365 pour vous assurer que les licences Microsoft 265 Enterprise lui ont été attribuées.
4. Supprimez le compte d’utilisateur test du groupe de sécurité test.
5. Examinez les propriétés du compte d’utilisateur pour vous assurer que les licences Microsoft 265 Enterprise ne lui sont plus attribuées.
6. Supprimez le groupe de sécurité test et le compte d’utilisateur test.

<a name="crit-identity-access-reviews"></a>
### <a name="optional-access-reviews-configured-and-being-used-to-monitor-access"></a>Facultatif : révisions d'accès configurés et utilisés pour contrôler l'accès

Vous avez utilisé ces articles pour configurer différents types de révisions d’accès afin de contrôler les appartenances aux groupes, l’accès aux applications d’entreprise et les attributions de rôle :

- [Groupes et applications](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)
- [Rôles Azure AD](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Rôles de ressources Azure](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

Si nécessaire, l’[Étape 7](../identity-governance.md#identity-access-reviews) peut vous aider avec cette option.
