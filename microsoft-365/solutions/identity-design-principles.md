---
title: Microsoft 365 planification des ressources d’entreprise - Architecture de sécurité
description: Découvrez les principales stratégies de conception pour l’architecture Enterprise Microsoft d’Alex Shteynberg, architecte principal technique chez Microsoft.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: f61c05608bfb9f3b528cf0a717dbe9effbaf31a5
ms.sourcegitcommit: fac7b4b0095254c87b2a341fa2d53a42193f8957
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2021
ms.locfileid: "58417998"
---
# <a name="to-identity-and-beyondone-architects-viewpoint"></a>Vers l’identité et au-delà : l’identité d’un architecte

Dans cet article, [Alex Shteynberg,](https://www.linkedin.com/in/alex-shteynberg/)architecte technique principal chez Microsoft, décrit les principales stratégies de conception pour les entreprises qui adoptent Microsoft 365 et d’autres services cloud De Microsoft.

## <a name="about-the-author"></a>À propos de l’auteur

![Photo Alex Shteynberg](../media/solutions-architecture-center/identity-and-beyond-alex-shteynberg.jpg)

Je suis architecte technique principal au Microsoft [Technology Center](https://www.microsoft.com/mtc?rtc=1)de New York. Je travaille principalement avec des clients de grande taille et des exigences complexes. Mon opinion et mon opinion sont basés sur ces interactions et peuvent ne pas s’appliquer à toutes les situations. Toutefois, d’après mon expérience, si nous pouvons aider les clients aux défis les plus complexes, nous pouvons aider tous les clients.

Je travaille généralement avec plus de 100 clients chaque année. Bien que chaque organisation possède des caractéristiques uniques, il est intéressant de voir les tendances et les points communs. Par exemple, une tendance est l’intérêt entre secteurs pour de nombreux clients. Après tout, une succursale bancaire peut également être un café et un centre communautaire.

Dans mon rôle, je me concentre sur l’aide des clients à trouver la meilleure solution technique pour répondre à leur ensemble unique d’objectifs professionnels. Officiellement, je me concentre sur l’identité, la sécurité, la confidentialité et la conformité. J’aime le fait que ces touches tout ce que nous faisons. Cela me donne la possibilité de participer à la plupart des projets. Cela me permet de rester occupé et de profiter de ce rôle.

Je vis à New York (la meilleure !) et j’aime vraiment la diversité de sa culture, de sa cuisine et de ses personnes (pas le trafic). J’aime voyager lorsque je peux et j’espére voir la plupart du monde au cours de ma vie. Je suis actuellement à la recherche d’un voyage en Afrique pour en savoir plus sur la famille.

## <a name="guiding-principles"></a>Principes directeurs

- **La simplicité est souvent préférable**: vous pouvez (presque) tout faire avec la technologie, mais cela ne signifie pas que vous devriez le faire. En particulier dans l’espace de sécurité, de nombreux clients surenginent les solutions. [J’aime que cette vidéo](https://www.youtube.com/watch?v=SOQgABDSYZE) de la conférence Stripe de Google souligne ce point.
- **Personnes, processus, technologie** [: concevez pour les](https://en.wikipedia.org/wiki/Human-centered_design) personnes afin d’améliorer les processus, et non pas d’abord les technologies. Il n’existe aucune solution « parfaite ». Nous devons trouver un équilibre entre différents facteurs de risque et les décisions seront différentes pour chaque entreprise. Trop de clients conçoivent une approche que leurs utilisateurs évitent par la suite.
- **Concentrez-vous sur**« pourquoi » tout d’abord et sur « comment » plus tard : soyez l’ennuyeux enfant de 7 ans avec un million de questions. Nous ne pouvons pas trouver la bonne réponse si nous ne connaissez pas les bonnes questions à poser. De nombreux clients se basent sur des hypothèses sur la façon dont les choses doivent fonctionner au lieu de définir le problème de l’entreprise. Il existe toujours plusieurs chemins d’accès qui peuvent être pris.
- **Bonnes pratiques :** reconnaître que les meilleures pratiques changent à la vitesse de la lumière. Si vous avez examiné Azure AD il y a plus de trois mois, vous n’êtes probablement plus à jour. Tout ce qui est ici est sujet à modification après la publication. La « meilleure » option d’aujourd’hui peut ne pas être la même dans six mois.

## <a name="baseline-concepts"></a>Concepts de base

N’ignorez pas cette section. Je trouve souvent que je dois revenir à ces rubriques, même pour les clients qui utilisent les services cloud depuis des années.
La langue n’est pas un outil précis. Nous utilisons assez souvent le même mot pour dire différents concepts ou mots différents pour signifier le même concept. J’utilise souvent ce diagramme ci-dessous pour établir une terminologie de référence et un « modèle hiérarchique ».
<br><br>

![Illustration du client, de l’abonnement, du service et des données](../media/solutions-architecture-center/Identity-and-beyond-tenant-level.png)

<br>

Lorsque vous apprenez à se sentir mieux, il est préférable de commencer dans le pool et non au milieu de l’océan. Je n’essaie pas d’être techniquement précis avec ce diagramme. Il s’agit d’un modèle pour aborder certains concepts de base.

Dans le schéma :

- Client = une instance d’Azure AD. Il se trouve en « haut » d’une hiérarchie ou au niveau 1 dans le diagramme. Nous pouvons considérer qu’il s’agit de la «[limite](/azure/active-directory/users-groups-roles/licensing-directory-independence)» où tout le reste se produit[(Azure AD B2B](/azure/active-directory/b2b/what-is-b2b) mis à part). Tous les services cloud d’entreprise Microsoft font partie de l’un de ces clients. Les services grand public sont distincts. « Client » apparaît dans la documentation sous la forme Office 365 client Azure, client Azure, client WVD, etc. Je trouve souvent que ces variantes sont source de confusion pour les clients.
- Les services/abonnements, niveau 2 dans le diagramme, appartiennent à un seul client. La plupart des services SaaS sont en 1:1 et ne peuvent pas se déplacer sans migration. Azure est différent, vous pouvez déplacer [la facturation](/azure/cost-management-billing/manage/billing-subscription-transfer) et/ou un [abonnement](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) vers un autre client. De nombreux clients doivent déplacer des abonnements Azure. Cela a différentes implications. Les objets qui existent en dehors de l’abonnement ne se déplacent pas (par exemple, le contrôle d’accès basé sur un rôle ou les objets Azure RBAC et Azure AD, y compris les groupes, les applications, les stratégies, et ainsi de suite). En outre, certains services (par exemple, Azure Key Vault, Data Bricks, et ainsi de suite). Ne migrez pas les services sans un bon besoin commercial. Certains scripts qui peuvent être utiles pour la migration sont [partagés sur GitHub](https://github.com/lwajswaj/azure-tenant-migration).
- Un service donné a généralement une sorte de limite de « sous-niveau » ou de niveau 3 (L3). Cela est utile pour comprendre la répartition de la sécurité, des stratégies, de la gouvernance, etc. Malheureusement, il n’existe aucun nom uniforme que je connaisse. Voici quelques exemples de noms pour L3 : Azure Subscription = [ressource](/azure/azure-resource-manager/management/manage-resources-portal); Dynamics 365 CE = [instance](/dynamics365/admin/new-instance-management); Power BI = [espace de travail](/power-bi/service-create-the-new-workspaces); Power Apps = [environnement](/power-platform/admin/environments-overview); et ainsi de suite.
- Le niveau 4 est l’endroit où se trouve les données réelles. Ce « plan de données » est un sujet complexe. Certains services utilisent Azure AD pour RBAC, d’autres non. Je vais aborder ce sujet un peu plus en détail lorsque nous aborderons les sujets de délégation.

Voici quelques concepts supplémentaires que de nombreux clients (et employés de Microsoft) ne comprennent pas ou ont des questions :

- Tout le monde [peut créer](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) de nombreux locataires [sans frais.](https://azure.microsoft.com/pricing/details/active-directory/) Vous n’avez pas besoin d’un service en son sein. J’en ai des dizaines. Chaque nom de client est unique dans le service cloud mondial de Microsoft (en d’autres termes, aucun client ne peut avoir le même nom). Elles sont toutes au format TenantName.onmicrosoft.com. Il existe également des processus qui créent automatiquement des locataires (locataires[nonmanagés).](/azure/active-directory/users-groups-roles/directory-self-service-signup) Par exemple, cela peut se produire lorsqu’un utilisateur s’ad commune à un service d’entreprise avec un domaine de messagerie qui n’existe dans aucun autre client.
- Dans un client géré, de nombreux [domaines DNS](/azure/active-directory/fundamentals/add-custom-domain) peuvent y être inscrits. Cela ne modifie pas le nom du client d’origine. Il n’existe actuellement aucun moyen simple de renommer un client (autre que la migration). Bien que le nom du client ne soit techniquement pas critique ces jours-ci, certains peuvent trouver cela limité.
- Vous devez réserver un nom de client pour votre organisation même si vous ne prévoyez pas encore de déployer de services. Sinon, quelqu’un peut vous le prendre et il n’existe aucun processus simple pour le reprendre (même problème que les noms DNS). J’entends cela trop souvent de la part des clients. Le nom de votre client doit également faire l’objet d’un thème.
- Si vous possédez des espaces de noms DNS, vous devez les ajouter à vos locataires. Dans le cas contraire, [il est possible de](/azure/active-directory/users-groups-roles/directory-self-service-signup) créer un client non géré avec ce nom, ce qui entraîne une perturbation de sa [gestion.](/azure/active-directory/users-groups-roles/domains-admin-takeover)
- L’espace de noms DNS (tel que contoso.com) peut appartenir à un seul client. Cela a des conséquences sur différents scénarios (par exemple, le partage d’un domaine de messagerie lors d’une fusion ou d’une acquisition, et ainsi de suite). Il existe un moyen d’inscrire un sous-DNS (tel que div.contoso.com) dans un autre client, mais cela doit être évité. En enregistrant un nom de domaine de niveau supérieur, tous les sous-domaines sont supposés appartenir au même client. Dans les scénarios multi-locataires (voir ci-dessous), je recommande normalement d’utiliser un autre nom de domaine de niveau supérieur (par exemple, contoso.ch ou ch-contoso.com).
- Qui devez-vous « posséder » un client ? Je vois souvent des clients qui ne savent pas qui est actuellement propriétaire de leur client. Il s’agit d’un grand indicateur rouge. Appelez le support Microsoft DÈS QUE POSSIBLE. Tout aussi problématique est lorsqu’un propriétaire de service (souvent un administrateur Exchange) est désigné pour gérer un client. Le client contiendra tous les services que vous souhaitez peut-être à l’avenir. Le propriétaire du client doit être un groupe qui peut prendre une décision d’activer tous les services cloud d’une organisation. Un autre problème se pose lorsqu’un groupe de propriétaires de client est invité à gérer tous les services. Cela n’est pas à l’échelle pour les grandes organisations.
- Il n’existe pas de concept de sous/super client. Pour une raison quelconque, cette répétition se répète. Cela [s’applique également aux locataires Azure AD B2C.](/azure/active-directory-b2c/) J’entends trop souvent « Mon environnement B2C se trouve dans mon client XYZ » ou « Comment déplacer mon client Azure vers mon client Office 365 client ? »
- Ce document se concentre principalement sur le cloud commercial international, car c’est ce que la plupart des clients utilisent. Il est parfois utile de connaître les [clouds souverains.](/azure/active-directory/develop/authentication-national-cloud) Les clouds souverains ont des implications supplémentaires pour discuter des sujets hors de portée de cette discussion.

## <a name="baseline-identity-topics"></a>Rubriques sur l’identité de base

Il existe une documentation complète sur la plateforme d’identités de Microsoft Azure Active Directory (Azure AD). Pour ceux qui débutent, cela semble souvent difficile à faire. Même après l’avoir appris, il peut être difficile de suivre l’innovation et le changement constants. Dans mes interactions avec le client, je me retrouve souvent en tant que « traducteur » entre les objectifs de l’entreprise et les approches « Bonne, Meilleure, Meilleure » pour résoudre ces problèmes (et les « notes » humaines pour ces rubriques). Il existe rarement une réponse parfaite et la décision « droite » est un équilibre entre différents facteurs de risque. Voici quelques-unes des questions courantes et les domaines de confusion que j’ai tendance à aborder avec les clients.

### <a name="provisioning"></a>Mise en service

Azure AD ne résout pas l’absence de gouvernance dans votre monde de l’identité ! [La gouvernance des identités](/azure/active-directory/governance/identity-governance-overview) doit être un élément critique indépendant des décisions cloud. Les exigences de gouvernance changent au fil du temps, c’est pourquoi il s’agit d’un programme et non d’un outil.

[Azure AD Connecter](/azure/active-directory/hybrid/whatis-azure-ad-connect) par [Microsoft Identity Manager](/microsoft-identity-manager/microsoft-identity-manager-2016) (MIM) et quelque chose d’autre (tiers ou personnalisé) ? Économisez-vous beaucoup de difficultés maintenant et à l’avenir et allez avec Azure AD Connecter. Il existe toutes sortes d’intelligences dans cet outil pour répondre aux configurations client et aux innovations en cours.

Certains cas de périphérie qui peuvent conduire à une architecture plus complexe :

- J’ai plusieurs forêts AD sans connectivité réseau entre celles-ci. Il existe une nouvelle option appelée [Mise en service cloud.](/azure/active-directory/cloud-provisioning/what-is-cloud-provisioning)
- Je n’ai pas Active Directory et je ne souhaite pas l’installer. Azure AD Connecter configurer la synchronisation à partir de [LDAP](/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-tools-comparison) (le partenaire peut être requis).
- Je dois mettre en service les mêmes objets pour plusieurs locataires. Cela n’est pas techniquement pris en charge, mais dépend de la définition de « same ».

Dois-je personnaliser les règles de synchronisation par défaut[(](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering)objets de filtre, modifier les [attributs,](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized) [ID](/azure/active-directory/hybrid/plan-connect-userprincipalname)de connexion alternatif, et ainsi de suite) ? Évitez!. Une plateforme d’identité est aussi utile que les services qui l’utilisent. Bien que vous pouvez faire toutes sortes de configurations complexes, pour répondre à cette question, vous devez examiner l’impact sur les applications. Si vous filtrez des objets à messagerie, la liste d’adresses réseau des services en ligne sera incomplète . si l’application s’appuie sur des attributs spécifiques, leur filtrage aura un impact imprévisible ; et ainsi de suite. Il ne s’agit pas d’une décision d’équipe d’identité.

XYZ SaaS prend en charge l’approvisionnement juste-à-temps (JIT), pourquoi avez-vous besoin de ma synchronisation ? Voir ci-dessus. De nombreuses applications ont besoin d’informations de « profil » pour les fonctionnalités. Vous ne pouvez pas avoir de liste d’adresses gal si tous les objets à messagerie ne sont pas disponibles. Il en va de même pour la mise en service [des utilisateurs](/azure/active-directory/app-provisioning/user-provisioning) dans les applications intégrées à Azure AD.

### <a name="authentication"></a>Authentification

[Synchronisation de hachage de mot](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization) de passe (PHS) et [authentification](/azure/active-directory/hybrid/how-to-connect-pta-how-it-works) directe (PTA) par rapport à la [fédération](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).

En règle générale, la fédération [fait l’objet d’une](/azure/active-directory/hybrid/choose-ad-authn) grande question. Plus simple est généralement préférable et par conséquent utiliser PHS, sauf si vous avez une bonne raison de ne pas le faire. Il est également possible de configurer différentes méthodes d’authentification pour différents domaines DNS dans le même client.

Certains clients activent la fédération + PHS principalement pour :

- Option de [secours](/azure/active-directory/hybrid/plan-migrate-adfs-password-hash-sync) (pour la récupération d’urgence) si le service de fédération n’est pas disponible.
- Fonctionnalités supplémentaires (par exemple : [Azure AD DS)](/azure/active-directory-domain-services/tutorial-configure-password-hash-sync)et services de sécurité (ex.: informations d’identification [divulguées)](/azure/active-directory/reports-monitoring/concept-risk-events#leaked-credentials)
- Prise en charge des services dans Azure qui ne comprennent pas l’authentification fédérée (par exemple, [Fichiers Azure](/azure/storage/files/storage-files-active-directory-overview)).

Je pars souvent à travers le flux d’authentification des clients pour clarifier certains détails. Le résultat ressemble à l’image ci-dessous, ce qui n’est pas aussi bon que le processus interactif d’y arriver.

![Exemple de conversation de tableau blanc](../media/solutions-architecture-center/identity-beyond-whiteboard-example.png)

Ce type de dessin de tableau blanc illustre l’endroit où les stratégies de sécurité sont appliquées dans le flux d’une demande d’authentification. Dans cet exemple, les stratégies appliquées via le service AD FS (Active Directory Federation Service) sont appliquées à la première demande de service, mais pas aux demandes de service suivantes. C’est au moins une raison pour déplacer les contrôles de sécurité dans le cloud autant que possible.

Nous avons toujours été en mesure de nous souvenir de l' sign-on unique (SSO, [Single Sign-On).](/azure/active-directory/manage-apps/what-is-single-sign-on) Certains clients pensent pouvoir y parvenir en choisissant le fournisseur de fédération (STS) « de droite ». Azure AD peut vous aider considérablement à activer les [fonctionnalités d'](/azure/active-directory/manage-apps/plan-sso-deployment) cesso, mais aucun STS n’est magique. Il existe trop de méthodes d’authentification « héritées » qui sont toujours utilisées pour les applications critiques. L’extension d’Azure AD avec [des solutions](/azure/active-directory/saas-apps/tutorial-list) partenaires peut résoudre un grand nombre de ces scénarios. L' sso est une stratégie et un parcours. Vous ne pouvez pas y arriver sans passer aux [normes pour les applications.](/azure/active-directory/develop/v2-app-types) Cette rubrique est liée à un parcours vers l’authentification [sans](/azure/active-directory/authentication/concept-authentication-passwordless) mot de passe, qui n’a pas non plus de réponse magique.

[L’authentification multifacteur](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) est essentielle aujourd’hui[(ici pour](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) plus d’informations). Ajoutez-y [l’analyse](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) du comportement des utilisateurs et vous avez une solution qui empêche les cyberattaques les plus courantes. Même les services grand public sont en train de passer à l' mba. Toutefois, je rencontre toujours de nombreux clients qui ne souhaitent pas passer aux approches [d’authentification](../enterprise/hybrid-modern-auth-overview.md) moderne. Le principal argument que j’ai entendu est qu’il aura un impact sur les utilisateurs et les applications héritées. Parfois, un bon coup de pied peut aider les clients à se déplacer , Exchange Online [les modifications annoncées.](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282) De nombreux rapports Azure AD [sont](/azure/active-directory/fundamentals/concept-fundamentals-block-legacy-authentication) désormais disponibles pour aider les clients avec cette transition.

### <a name="authorization"></a>Autorisation

Selon [Wikipedia,](https://en.wikipedia.org/wiki/Authorization)« autoriser » consiste à définir une stratégie d’accès. De nombreuses personnes y pensent comme la possibilité de définir des contrôles d’accès à un objet (fichier, service, et ainsi de suite). Dans le monde actuel des cybermenaces, ce concept évolue rapidement en une stratégie dynamique qui peut réagir à divers vecteurs de menace et ajuster rapidement les contrôles d’accès en réponse à ces menaces. Par exemple, si j’accède à mon compte bancaire à partir d’un emplacement inhabituel, je reçois des étapes de confirmation supplémentaires. Pour aborder ce sujet, nous devons non seulement prendre en compte la stratégie proprement dite, mais également l’écosystème des méthodologies de détection des menaces et de corrélation de signal.

Le moteur de stratégie d’Azure AD est implémenté à l’aide de [stratégies d’accès conditionnel.](/azure/active-directory/conditional-access/overview) Ce système dépend des informations de divers autres systèmes de détection des menaces pour prendre des décisions dynamiques. Un affichage simple ressemble à l’illustration suivante :

![Moteur de stratégie dans Azure AD](../media/solutions-architecture-center/identity-and-beyond-illustration-3.png)

La combinaison de tous ces signaux permet d’obtenir des stratégies dynamiques telles que celles-ci :

- Si une menace est détectée sur votre appareil, votre accès aux données sera réduit au web uniquement sans possibilité de téléchargement.
- Si vous téléchargez un volume anormalement élevé de données, tout ce que vous téléchargez sera chiffré et restreint.
- Si vous accédez à un service à partir d’un appareil nonmanaté, vous serez bloqué contre les données hautement sensibles, mais vous serez autorisé à accéder aux données non restreintes sans pouvoir les copier vers un autre emplacement.

Si vous êtes d’accord avec cette définition étendue de l’autorisation, vous devez implémenter des solutions supplémentaires. Les solutions que vous implémentez dépendent de la dynamique que vous souhaitez que la stratégie soit et des menaces que vous souhaitez hiérarchiser. Voici quelques exemples de ces systèmes :

- [Azure AD Identity Protection](/azure/active-directory/identity-protection/)
- [Microsoft Defender pour l’identité](/azure-advanced-threat-protection/)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Microsoft Defender pour Office 365](../security/office-365-security/defender-for-office-365.md)
- [Microsoft Cloud App Security](/cloud-app-security/) (MCAS)
- [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md)
- [Microsoft Intune](/mem/intune/)
- [Protection des données Microsoft](../compliance/information-protection.md) (MIP)
- [Azure Sentinel](/azure/sentinel/)

Bien entendu, en plus d’Azure AD, différents services et applications ont leurs propres modèles d’autorisation spécifiques. Certains d’entre eux sont abordés plus loin dans la section délégation.

### <a name="audit"></a>Audit

Azure AD offre des fonctionnalités [d’audit et de rapports](/azure/active-directory/reports-monitoring/) détaillées. Toutefois, il ne s’agit généralement pas de la seule source d’informations nécessaire pour prendre des décisions de sécurité. Pour plus d’informations à ce sujet, voir la section délégation.

## <a name="theres-no-exchange"></a>Il n’y a aucune Exchange

N’oubliez pas ! Cela ne signifie pas Exchange est en cours d’SharePoint, et ainsi de suite). Il s’agit toujours d’un service principal. Ce que je veux dire, c’est que, depuis un certain temps, les fournisseurs de technologies sont en transition entre les expériences utilisateur (UX) et englobent les composants de plusieurs services. Dans Microsoft 365, un exemple simple est « pièces[jointes](https://support.office.com/article/Attach-files-or-insert-pictures-in-Outlook-email-messages-BDFAFEF5-792A-42B1-9A7B-84512D7DE7FC)modernes », où les pièces jointes aux messages électroniques sont stockées dans SharePoint Online ou OneDrive Entreprise.

![Attachement d’un fichier à un e-mail](../media/solutions-architecture-center/modern-attachments.png)

Si vous regardez Outlook client, vous pouvez voir de nombreux services qui sont « connectés » dans le cadre de cette expérience, pas seulement Exchange. Cela inclut Azure AD, Recherche Microsoft, applications, profil, conformité et Office 365 groupes.

![Outlook interface avec des callouts](../media/solutions-architecture-center/identity-and-beyond-conceptual-screenshot.png)

En savoir plus [Infrastructure Microsoft Fluid](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-ignite-blog-microsoft-fluid-framework-preview/ba-p/978268) la prévisualisation des fonctionnalités à venir. En prévisualisation maintenant, je peux lire et répondre Teams conversations directement dans Outlook. En fait, le [client Teams est](https://products.office.com/microsoft-teams/download-app) l’un des exemples les plus importants de cette stratégie.

Dans l’ensemble, il est plus difficile de tracer une ligne claire entre Office 365 et d’autres services dans les clouds Microsoft. Je considère qu’il s’agit d’un avantage important pour les clients, car ils peuvent bénéficier d’une innovation totale dans tout ce que nous faisons, même s’ils utilisent un seul composant. Assez cool et a des implications très importantes pour de nombreux clients.

Aujourd’hui, je trouve que de nombreux groupes de clients sont structurés autour des « produits ». Il est logique pour un monde local, car vous avez besoin d’un expert pour chaque produit spécifique. Toutefois, je suis entièrement satisfait de ne pas avoir à déboguer une base de données Active Directory ou Exchange une nouvelle fois, car ces services ont été déplacés vers le cloud. L’automatisation (de type cloud) supprime certains travaux manuels répétitifs (voir ce qui est arrivé aux fabriques). Toutefois, elles sont remplacées par des exigences plus complexes pour comprendre l’interaction entre les services, l’impact, les besoins de l’entreprise, etc. Si vous êtes prêt à [apprendre,](/learn/)il existe d’excellentes opportunités activées par la transformation cloud. Avant d’entrer dans la technologie, je parle souvent aux clients de la gestion des changements dans les compétences informatiques et les structures d’équipe.

Pour tous SharePoint les fans et les développeurs, n’hésitez pas à demander « Comment puis-je faire du XYZ SharePoint en ligne ? » Utilisez [Power Automate](/power-automate/) (ou Flow) pour le flux de travail, il s’agit d’une plateforme beaucoup plus puissante. Utilisez [Azure Bot Framework pour](/azure/bot-service/) créer une meilleure UX pour votre liste d’éléments 500 K. Commencez à [utiliser Microsoft Graph](https://developer.microsoft.com/graph/) au lieu de CSOM. [Microsoft Teams](/MicrosoftTeams/Teams-overview) inclut SharePoint mais également un monde plus. Il existe de nombreux autres exemples que je peux énumérer. Il y a là un vaste et formidable éventail. Ouvrez la porte et [commencez à explorer.]()

L’autre impact courant est dans le domaine de la conformité. Cette approche entre services semble complètement dérouter de nombreuses stratégies de conformité. Je continue de voir les organisations qui indiquent : « Je dois journalner toutes les communications par courrier électronique dans un système eDiscovery ». Qu’est-ce que cela signifie vraiment lorsque le courrier électronique n’est plus seulement un courrier électronique, mais une fenêtre d’accès à d’autres services ? Office 365 a une approche complète de la [conformité,](../compliance/index.yml)mais la modification des personnes et des processus est souvent beaucoup plus difficile que la technologie.

Il existe de nombreuses autres implications en matière de personnes et de processus. À mon avis, il s’agit d’un domaine critique et sous-abordé. Peut-être plus dans un autre article.

## <a name="tenant-structure-options"></a>Options de structure du client

### <a name="single-tenant-vs-multi-tenant"></a>Client unique et multi-locataire

En règle générale, la plupart des clients ne doivent avoir qu’un seul client de production. Il existe de nombreuses raisons pour lesquelles plusieurs clients sont difficiles (lui donner [une Bing](https://www.bing.com/search?q=office%20365%20multiple%20tenants)recherche) ou lire ce [livre blanc](https://aka.ms/multi-tenant-user). En même temps, de nombreux clients d’entreprise avec qui je travaille ont un autre (petit) client pour l’apprentissage informatique, les tests et l’expérimentation. L’accès Azure entre locataires est facilité avec [Azure Azure](https://azure.microsoft.com/services/azure-lighthouse/). Office 365 et de nombreux autres services SaaS ont des limites pour les scénarios entre locataires. Il y a beaucoup à prendre en compte dans les scénarios [Azure AD B2B.](/azure/active-directory/b2b/what-is-b2b)

De nombreux clients se retrouvent avec plusieurs clients de production après une fusion et une acquisition (M&A) et souhaitent se consolider. Aujourd’hui, ce n’est pas simple et nécessiterait Microsoft Consulting Services (MCS) ou un partenaire plus des logiciels tiers. Des travaux d’ingénierie sont en cours pour répondre à différents scénarios avec des clients multi-clients à l’avenir.

Certains clients choisissent d’opter pour plusieurs clients. Il doit s’agit d’une décision très attentive et presque toujours pilotée par une raison professionnelle ! Voici quelques exemples :

- Structure d’entreprise de type de holding où la collaboration facile entre les différentes entités n’est pas requise et où il existe de forts besoins d’administration et d’isolation.
- Après une acquisition, une décision commerciale est prise de conserver deux entités distinctes.
- Simulation de l’environnement d’un client qui ne modifie pas l’environnement de production du client.
- Développement de logiciels pour les clients.

Dans ces scénarios multi-clients, les clients souhaitent souvent conserver une configuration identique entre les clients ou signaler les modifications et les dérives de configuration. Cela implique souvent de passer des modifications manuelles à la configuration en tant que code. Le support microsoft microsoft propose un atelier pour ces types de conditions requises en fonction de cette adresse IP publique : <https://Microsoft365dsc.com> .

### <a name="multi-geo"></a>Multi-Géo

À [Multi-Géo](../enterprise/microsoft-365-multi-geo.md) ou non à Multi-Géo, c’est la question. Avec Office 365 multigéogé, vous pouvez mettre en service et stocker des données au repos dans les emplacements géographiques que vous avez choisis pour répondre aux exigences de résidence des [données.](../enterprise/o365-data-locations.md) Il existe de nombreux détails concernant cette fonctionnalité. Gardez les éléments suivants à l’esprit :

- Il ne fournit pas d’avantages en terme de performances. Les performances peuvent être pire si la [conception du réseau](https://aka.ms/office365networking) n’est pas correcte. Obtenez des appareils « proches » du réseau Microsoft, pas nécessairement à vos données.
- Il ne s’agit pas d’une solution [pour la conformité au R GDPR.](https://www.microsoft.com/trust-center/privacy/gdpr-overview) Le R GDPR ne se concentre pas sur la indépendance des données ou les emplacements de stockage. Il existe d’autres cadres de conformité pour cela.
- Elle ne résout pas la délégation de l’administration (voir ci-dessous) ni les [obstacles aux informations.](../compliance/information-barriers.md)
- Il n’est pas identique à multi-locataire et nécessite des flux de travail [de mise](https://github.com/MicrosoftDocs/azure-docs-pr/blob/master/articles/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation.md) en service utilisateur supplémentaires.
- Il ne déplace [pas votre client](../enterprise/moving-data-to-new-datacenter-geos.md) (votre Azure AD) vers une autre zone géographique.

## <a name="delegation-of-administration"></a>Délégation de l’administration

Dans la plupart des grandes organisations, la séparation des tâches et du contrôle d’accès basé sur les rôles (RBAC) est une réalité nécessaire. Je vais m’excuser à l’avance. Ce n’est pas aussi simple que certains clients le souhaitent. Les exigences client, juridique, de conformité et autres sont différentes et parfois en conflit dans le monde entier. La simplicité et la flexibilité sont souvent sur les côtés opposés les uns des autres. Ne vous y faites pas mal, nous pouvons faire un meilleur travail à ce niveau. Des améliorations significatives ont été (et seront) apportées au fil du temps. Visitez votre Centre de [technologie Microsoft](https://www.microsoft.com/mtc) local pour trouver le modèle adapté aux besoins de votre entreprise sans lire de documents 379230 ! Ici, je vais me concentrer sur ce à quoi vous devez penser et non sur la raison pour laquelle il s’agit de cette façon. Vous trouverez ci-dessous cinq domaines différents à planifier et certaines des questions courantes que j’ai rencontrées.

### <a name="azure-ad-and-microsoft-365-admin-centers"></a>Centres d’administration Azure AD et Microsoft 365 de gestion

La liste des rôles intégrés est longue [et croissante.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) Chaque rôle se compose d’une liste d’autorisations de rôle regroupées pour permettre l’utilisation d’actions spécifiques. Vous pouvez voir ces autorisations dans l’onglet « Description » à l’intérieur de chaque rôle. Vous pouvez également en voir une version plus lisible dans le centre Administration Microsoft 365. Les définitions des rôles intégrés ne peuvent pas être modifiées. En règle générale, il s’agit de trois catégories :

- **Administrateur général**: ce rôle « [](../enterprise/protect-your-global-administrator-accounts.md) tout puissant » doit être hautement protégé, comme vous le feriez dans d’autres systèmes. Recommandations classiques : aucune affectation permanente et utilisation d’Azure AD Privileged Identity Management (PIM) ; Authentification forte ; et ainsi de suite. Il est intéressant de noter que ce rôle ne vous donne pas accès à tous les accès par défaut. En règle générale, je vois une confusion concernant l’accès à la conformité et l’accès Azure, abordée plus loin. Toutefois, ce rôle peut toujours attribuer l’accès à d’autres services dans le client.
- **Administrateurs de service spécifiques**: certains services (Exchange, SharePoint, Power BI, etc.) utilisent des rôles d’administration de haut niveau d’Azure AD. Cela n’est pas cohérent dans tous les services et d’autres rôles spécifiques au service sont abordés ultérieurement.
- **Fonctionnel**: il existe une longue liste (et croissante) de rôles axés sur des opérations spécifiques (inviter des invités, et ainsi de suite). Régulièrement, d’autres d’entre elles sont ajoutées en fonction des besoins des clients.

Il n’est pas possible de déléguer tout (bien que l’écart diminue), ce qui signifie que le rôle d’administrateur général doit parfois être utilisé. La configuration en tant que code et l’automatisation doivent être envisagées au lieu de l’appartenance aux personnes de ce rôle.

**Remarque**: le Centre d’administration Microsoft 365 dispose d’une interface plus conviviale, mais offre un sous-ensemble de fonctionnalités par rapport à l’expérience d’administration Azure AD. Les deux portails utilisent les mêmes rôles Azure AD, de sorte que les modifications se produisent au même endroit. Conseil : si vous souhaitez une interface utilisateur d’administration axée sur la gestion des identités sans tout l’encombrement Azure, utilisez <https://aad.portal.azure.com> .

Qu’y a-t-il dans le nom ? Ne faites pas d’hypothèses à partir du nom du rôle. La langue n’est pas un outil très précis. L’objectif doit être de définir les opérations qui doivent être déléguées avant de déterminer les rôles nécessaires. L’ajout d’une personne au rôle « Lecteur de sécurité » ne lui permet pas de voir tous les paramètres de sécurité.

La possibilité de créer des [rôles personnalisés](/azure/active-directory/users-groups-roles/roles-custom-overview) est une question courante. Cette fonctionnalité est limitée dans Azure AD aujourd’hui (voir ci-dessous), mais augmente au fil du temps. Elles s’appliquent aux fonctions dans Azure AD et peuvent ne pas s’étendre « vers le bas » du modèle hiérarchique (abordé ci-dessus). Chaque fois que j’ai affaire à « personnalisé », j’ai tendance à revenir à mon principal « simple est préférable ».

Une autre question courante est la possibilité d’étendue des rôles à un sous-ensemble d’un répertoire. Un exemple ressemble à « Administrateur du helpdesk pour les utilisateurs de l’UE uniquement ». [Les unités administratives](/azure/active-directory/users-groups-roles/directory-administrative-units) sont conçues pour résoudre ce problème. Comme ci-dessus, je les trouve applicables aux fonctions dans Azure AD et peuvent ne pas s’étendre sur « bas ». Bien entendu, certains rôles n’ont pas de sens pour l’étendue (administrateurs globaux, administrateurs de service, et ainsi de suite).

Aujourd’hui, tous ces rôles nécessitent une appartenance directe (ou une affectation dynamique si vous utilisez [Azure AD PIM](/azure/active-directory/privileged-identity-management/)). Cela signifie que les clients doivent les gérer directement dans Azure AD et qu’ils ne peuvent pas être basés sur l’appartenance à un groupe de sécurité. Je ne suis pas un fan de la création de scripts pour gérer ces derniers, car il aurait besoin de s’exécuter avec des droits élevés. Je recommande généralement l’intégration d’API à des systèmes de processus tels que ServiceNow ou à l’aide d’outils de gouvernance partenaires tels que Saviynt. Des travaux d’ingénierie sont en cours pour résoudre ce problème au fil du temps.

[J’ai mentionné Azure AD PIM](/azure/active-directory/privileged-identity-management/) plusieurs fois. Il existe une solution Microsoft Identity Manager (MIM) [Privileged Access Management](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) (PAM) correspondante pour les contrôles locaux. Vous pouvez également examiner les stations de travail [à](/windows-server/identity/securing-privileged-access/privileged-access-workstations) accès privilégié (PAW) et la gouvernance d’identité [Azure AD.](/azure/active-directory/governance/identity-governance-overview) Il existe également différents outils tiers, qui peuvent activer l’élévation de rôle dynamique, juste-à-temps et juste-à-temps. Cela fait généralement partie d’une discussion plus large sur la sécurisation d’un environnement.

Parfois, les scénarios appellent l’ajout d’un utilisateur externe à un rôle (voir la section multi-locataires ci-dessus). Cela fonctionne très bien. [Azure AD B2B](/azure/active-directory/b2b/) est une autre rubrique importante et agréable à parcourir par les clients, peut-être dans un autre article.

### <a name="security-and-compliance-center-scc"></a>Centre de sécurité et conformité (SCC)

[Les autorisations](../security/office-365-security/permissions-in-the-security-and-compliance-center.md) dans le Centre Office 365 sécurité et conformité & sont une collection de « groupes de rôles », qui sont distincts et distincts des rôles Azure AD. Cela peut prêter à confusion, car certains de ces groupes de rôles ont le même nom que les rôles Azure AD (par exemple, lecteur de sécurité), mais ils peuvent avoir des appartenances différentes. Je préfère utiliser les rôles Azure AD. Chaque groupe de rôles se compose d’un ou plusieurs « rôles » (voir ce que je veux dire sur la réutilisation du même mot ?) et ont des membres d’Azure AD, qui sont des objets à messagerie. En outre, vous pouvez créer un groupe de rôles avec le même nom qu’un rôle, qui peut contenir ou non ce rôle (évitez cette confusion).

En un sens, il s’agit d’une évolution du modèle Exchange groupes de rôles. Toutefois, Exchange Online possède sa propre interface [de gestion des groupes de rôles.](/exchange/permissions-exo) Certains groupes de rôles dans Exchange Online sont verrouillés et gérés à partir d’Azure AD ou du Centre de sécurité & conformité, mais d’autres peuvent avoir des noms identiques ou similaires et sont gérés dans Exchange Online (ce qui ajoute à la confusion). Nous vous recommandons d’éviter d’utiliser Exchange Online interface utilisateur, sauf si vous avez besoin d’étendues pour Exchange gestion.

Vous ne pouvez pas créer de rôles personnalisés. Les rôles sont définis par les services créés par Microsoft et augmenteront à mesure que de nouveaux services seront introduits. Ce concept est similaire aux [rôles définis par les applications](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) dans Azure AD. Lorsque de nouveaux services sont activés, de nouveaux groupes de rôles doivent souvent être créés pour accorder ou déléguer l’accès à ces derniers (par [exemple,](../compliance/insider-risk-management-configure.md)la gestion des risques internes).

Ces groupes de rôles nécessitent également une appartenance directe et ne peuvent pas contenir de groupes Azure AD. Malheureusement, aujourd’hui, ces groupes de rôles ne sont pas pris en charge par Azure AD PIM. Comme les rôles Azure AD, j’ai tendance à recommander leur gestion par le biais d’API ou d’un produit de gouvernance partenaire tel que Saviynt, ou d’autres.

Les rôles du Centre de sécurité & conformité s’étendent sur Microsoft 365 et vous ne pouvez pas étendre ces groupes de rôles à un sous-ensemble de l’environnement (comme vous pouvez le faire avec des unités administratives dans Azure AD). De nombreux clients se demandent comment ils peuvent subdelegate. Par exemple, « créer une stratégie DLP uniquement pour les utilisateurs de l’UE ». Aujourd’hui, si vous avez des droits sur une fonction spécifique dans le Centre de sécurité & conformité, vous avez des droits sur tout ce qui est couvert par cette fonction dans le client. Toutefois, de nombreuses stratégies ont des fonctionnalités pour cibler [](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) un sous-ensemble de l’environnement (par exemple, « rendre ces étiquettes disponibles uniquement pour ces utilisateurs »). Une gouvernance et une communication adéquates sont un composant essentiel pour éviter les conflits. Certains clients choisissent d’implémenter une approche « configuration en tant que code » pour traiter la sous-délégation dans le Centre de sécurité & conformité. Certains services spécifiques sont en charge de la sous-délégation (voir ci-dessous).

Il est important de noter que les contrôles actuellement gérés via le Centre de sécurité & conformité (protection.office.com) sont en cours de migration vers deux portails d’administration distincts : security.microsoft.com et compliance.microsoft.com. La modification est la seule constante !

### <a name="service-specific"></a>Spécifique au service

Comme indiqué précédemment, de nombreux clients cherchent à obtenir un modèle de délégation plus granulaire. Exemple courant : « Gérer le service XYZ uniquement pour les utilisateurs et les emplacements de division X » (ou une autre dimension). La possibilité de le faire dépend de chaque service et n’est pas cohérente entre les services et fonctionnalités. En outre, chaque service peut avoir un modèle RBAC distinct et unique. Au lieu de discuter de tous ces éléments (cela prendra toujours du temps), j’ajoute des liens pertinents pour chaque service. Il ne s’agit pas d’une liste complète, mais elle vous aidera à démarrer.

- **Exchange Online** - (/exchange/permissions-exo/permissions-exo)
- **SharePoint Online** - (/sharepoint/manage-site-collection-administrators)
- **Microsoft Teams** - (/microsoftteams/itadmin-readiness)
- **eDiscovery** - (.. /compliance/index.yml)
  - **Filtrage des autorisations** - (.. /compliance/index.yml)
  - **Limites de conformité** - (.. /compliance/set-up-compliance-boundaries.md)
  - **Advanced eDiscovery** - (.. /compliance/overview-ediscovery-20.md)
- **Yammer** - (/yammer/manage-yammer-users/manage-yammer-admins)
- **Multi-géo** - (.. /enterprise/add-a-sharepoint-geo-admin.md)
- **Dynamics 365** – (/dynamics365/)

  Remarque : ce lien est à la racine de la documentation. Il existe plusieurs types de services avec des variantes dans le modèle d’administration/délégation.

- **Plateforme Power -** (/power-platform/admin/admin-documentation)
  - **Power Apps** - (/power-platform/admin/wp-security)

    Remarque : il existe plusieurs types avec des variantes dans les modèles d’administration/délégation.

  - **Power Automate** - (/power-automate/environments-overview-admin)
  - **Power BI** - (/power-bi/service-admin-governance)

    Remarque : la sécurité et la délégation de plateforme de données (qui Power BI est un composant) sont un domaine complexe.

- **MEM/Intune** - (/mem/intune/fundamentals/role-based-access-control)
- **Microsoft Defender pour le point de terminaison** - (/windows/security/threat-protection/microsoft-defender-atp/user-roles)
- **Microsoft 365 Defender** - (.. /security/defender/m365d-permissions.md)
- **Microsoft Cloud App Security** - (/cloud-app-security/manage-admins)
- **Stream** - (/stream/assign-administrator-user-role)
- **Obstacles à l’information** - (.. /compliance/information-barriers.md)

### <a name="activity-logs"></a>Journaux d’activité

Office 365 un journal [d’audit unifié.](../compliance/search-the-audit-log-in-security-and-compliance.md) Il s’agit [d’un journal très détaillé,](/office/office-365-management-api/office-365-management-activity-api-schema)mais ne lisez pas trop le nom. Il peut ne pas contenir tout ce que vous souhaitez ou avez besoin pour vos besoins de sécurité et de conformité. En outre, certains clients sont vraiment intéressés par [l’audit avancé.](../compliance/advanced-audit.md)

Voici quelques exemples Microsoft 365 journaux accessibles via d’autres API :

- [Azure AD](/azure/azure-monitor/platform/diagnostic-settings) (activités non liées aux Office 365)
- [Exchange Suivi des messages](/powershell/module/exchange/get-messagetrace)
- Systèmes UEBA/menaces abordés ci-dessus (par exemple, Azure AD Identity Protection, Microsoft Cloud App Security, Microsoft Defender pour endpoint, et ainsi de suite)
- [Protection des données Microsoft](../compliance/data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/api-power-bi)
- [Microsoft Graph](https://graph.microsoft.com)

Il est important d’identifier d’abord toutes les sources de journaux nécessaires pour un programme de sécurité et de conformité. Notez également que les différents journaux ont des limites de rétention en ligne différentes.

Du point de vue de la délégation d’administrateur, la plupart Microsoft 365 journaux d’activité n’ont pas de modèle RBAC intégré. Si vous êtes autorisé à voir un journal, vous pouvez voir tout ce qui y est. Un exemple courant d’exigence client est : « Je souhaite être en mesure d’interroger l’activité uniquement pour les utilisateurs de l’UE » (ou une autre dimension). Pour atteindre cette exigence, nous devons transférer les journaux vers un autre service. Dans le cloud Microsoft, nous vous recommandons de le transférer vers [Azure Sentinel](/azure/sentinel/overview) ou [Log Analytics.](/azure/azure-monitor/learn/quick-create-workspace)

Diagramme de haut niveau :

![diagramme des sources de journaux pour un programme de sécurité et de conformité](../media/solutions-architecture-center/identity-beyond-illustration-4.png)

Le diagramme ci-dessus représente les fonctionnalités intégrées pour envoyer des journaux au Hub d’événements et/ou stockage Azure et/ou Azure Log Analytics. Tous les systèmes n’incluent pas encore cette pré-utilisation. Toutefois, il existe d’autres approches pour envoyer ces journaux au même référentiel. Par exemple, voir [Protection de votre Teams avec Azure Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/protecting-your-teams-with-azure-sentinel/ba-p/1265761).

La combinaison de tous les journaux dans un emplacement de stockage inclut des avantages ajoutés, tels que les corrélations croisées, les temps de rétention personnalisés, l’augmentation des données nécessaires pour prendre en charge le modèle RBAC, etc. Une fois les données dans ce système de stockage, vous pouvez créer un tableau de bord Power BI (ou un autre type de visualisation) avec un modèle RBAC approprié.

Les journaux n’ont pas besoin d’être dirigés vers un seul endroit. Il peut également être utile [d’intégrer Office 365 journaux de](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) connexion Microsoft Cloud App Security un modèle RBAC personnalisé dans [Power BI](../admin/usage-analytics/usage-analytics.md). Les différents référentiels ont des avantages et des audiences différents.

Il est important de mentionner qu’il existe un système d’analyse intégré très riche pour la sécurité, les menaces, les vulnérabilités, etc. dans un service appelé [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md).

De nombreux clients de grande taille souhaitent transférer ces données de journal vers un système tiers (par exemple, SIEM). Il existe différentes approches à ce sujet, mais en général, [Azure Event Hub](/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) et [Graph](/graph/security-integration) sont de bons points de départ.

### <a name="azure"></a>Azure

Je suis souvent invité à savoir s’il existe un moyen de séparer les rôles à privilèges élevés entre Azure AD, Azure et SaaS (ex.: Administrateur général pour Office 365 mais pas Azure).  Pas vraiment.  L’architecture multi-client est nécessaire si une séparation administrative complète est requise, mais cela ajoute une [complexité significative](https://aka.ms/multi-tenant-user) (voir ci-dessus). Tous ces services font partie de la même limite de sécurité/identité (voir le modèle de hiérarchie ci-dessus).

Il est important de comprendre les relations entre les différents services dans le même client. Je travaille avec de nombreux clients qui sont en train de créer des solutions d’entreprise qui couvrent Azure, Office 365 et Power Platform (et souvent également des services cloud locaux et tiers). Un exemple courant :

1. Je souhaite collaborer sur un ensemble de documents/images/etc(Office 365)
2. Envoyer chacun d’eux via un processus d’approbation (plateforme Power Platform)
3. Une fois tous les composants approuvés, assemblez-les dans un ou plusieurs livrables unifiés (Azure) [Graph API Microsoft est](/azure/active-directory/develop/microsoft-graph-intro) votre meilleur ami pour ces composants.  Pas impossible, mais beaucoup plus complexe pour concevoir une solution couvrant [plusieurs locataires](/azure/active-directory/develop/single-and-multi-tenant-apps).

Azure Role-Based Access Control (RBAC) permet une gestion fine des accès pour Azure. À l’aide de RBAC, vous pouvez gérer l’accès aux ressources en accordant aux utilisateurs le moins d’autorisations nécessaires pour effectuer leurs tâches. Les détails ne sont pas pris en compte pour ce document, mais pour plus d’informations sur le contrôle d’accès basé sur un rôle (RBAC), voir Qu’est-ce que le contrôle d’accès basé sur un rôle [(RBAC) dans Azure ?](/azure/role-based-access-control/overview) Le RBAC est important, mais ne fait qu’une partie des considérations de gouvernance pour Azure. [L’infrastructure d’adoption](/azure/cloud-adoption-framework/govern/) cloud constitue un excellent point de départ pour en savoir plus. J’aime la façon dont [mon ami, Andres Ravinet,](https://www.linkedin.com/in/andres-ravinet/)parcourt les clients étape par étape à travers différents composants pour décider de l’approche. Une vue de haut niveau pour différents éléments (pas aussi bonne que le processus d’accès au modèle client réel) ressemble à ceci :

![Vue d’avant-plan des composants Azure pour l’administration déléguée](../media/solutions-architecture-center/identity-beyond-illustration-5.png)

Comme vous pouvez le voir dans l’image ci-dessus, de nombreux autres services doivent être pris en compte dans le cadre de la conception (par exemple, les stratégies [Azure,](/azure/governance/policy/overview)les plans [Azure,](/azure/governance/blueprints/overview)les groupes de [gestion,](/azure/governance/management-groups/)etc.).

## <a name="conclusion"></a>Conclusion

Démarré en tant que résumé court, s’est terminé plus longtemps que prévu.  J’espère que vous êtes maintenant prêt à vous préparer à la création d’un modèle de délégation pour votre organisation.  Cette conversation est très courante chez les clients. Il n’existe aucun modèle qui fonctionne pour tout le monde. En attente de quelques améliorations planifiées de l’ingénierie Microsoft avant de documenter les modèles courants que nous voyons parmi les clients. En attendant, vous pouvez travailler avec votre équipe de compte Microsoft pour organiser une visite au Centre de technologie Microsoft le plus [proche.](https://www.microsoft.com/mtc)  Vous y voyez !
