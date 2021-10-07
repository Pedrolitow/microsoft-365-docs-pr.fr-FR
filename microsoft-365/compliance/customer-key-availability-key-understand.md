---
title: Découvrir la clé de disponibilité pour la clé client
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
description: Découvrez la clé de disponibilité utilisée pour récupérer les clés client perdues.
ms.openlocfilehash: 72e66e9deb74400944c6ea65ea3ac167a703da26
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60170786"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Découvrir la clé de disponibilité pour la clé client

La clé de disponibilité est une clé racine générée et mise en service automatiquement lorsque vous créez une stratégie de chiffrement de données. Microsoft 365 stocke et protège la clé de disponibilité. La clé de disponibilité est fonctionnellement comme les deux clés racine que vous fournissez pour le chiffrement de service avec la clé client. La clé de disponibilité encapsule les clés d’un niveau inférieur dans la hiérarchie de clés. Contrairement aux clés que vous fournissez et gérez dans Azure Key Vault, vous ne pouvez pas accéder directement à la clé de disponibilité. Microsoft 365 automatisés gèrent la clé de disponibilité par programme. Ces services lancent des opérations automatisées qui n’impliquent jamais un accès direct à la clé de disponibilité.

L’objectif principal de la clé de disponibilité est de fournir une fonctionnalité de récupération en cas de perte imprévue de clés racines que vous gérez. La perte peut être le résultat d’une mauvaise gestion ou d’une action malveillante. Si vous perdez le contrôle de vos clés racine, contactez le Support Microsoft et Microsoft vous aidera tout au long du processus de récupération à l’aide de la clé de disponibilité. Vous utiliserez la clé de disponibilité pour migrer vers une nouvelle stratégie de chiffrement de données avec les nouvelles clés racines que vous provisionnez.

Stockage et le contrôle de la clé de disponibilité sont délibérément différents des clés Azure Key Vault pour trois raisons :

- La clé de disponibilité fournit une fonctionnalité de récupération , « break-glass » si le contrôle sur les deux clés Azure Key Vault est perdu.
- La séparation des contrôles logiques et des emplacements de stockage sécurisés fournit une défense en profondeur et protège contre la perte de toutes les clés et de vos données contre une attaque ou un point de défaillance unique.
- La clé de disponibilité offre une fonctionnalité de haute disponibilité si les services Microsoft 365 ne parviennent pas à accéder aux clés hébergées dans Azure Key Vault en raison d’erreurs temporaires. Cette règle s’applique uniquement au chiffrement Exchange Online et Skype Entreprise service. SharePoint Les fichiers en ligne, OneDrive Entreprise et Teams n’utilisent jamais la clé de disponibilité, sauf si vous demandez explicitement à Microsoft de lancer le processus de récupération.

Le partage de la responsabilité de protéger vos données, à l’aide de différents processus et protections pour la gestion des clés, permet de réduire le risque que toutes les clés (et par conséquent vos données) soient définitivement perdues ou détruites. Microsoft vous fournit l’autorité unique sur la désactivation ou la destruction de la clé de disponibilité lorsque vous quittez le service. Par défaut, personne chez Microsoft n’a accès à la clé de disponibilité : elle est uniquement accessible par le code de service Microsoft 365.

Pour plus [d’informations](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) sur la sécurisation des clés, voir le Centre de sécurité Microsoft.
  
## <a name="availability-key-uses"></a>Utilisations des clés de disponibilité

La clé de disponibilité offre une fonctionnalité de récupération pour les scénarios dans lesquels un malfaiteur externe ou un interne malveillant vole le contrôle de votre coffre de clés, ou lorsque la mauvaise gestion par inadvertance entraîne la perte de clés racine. Cette fonctionnalité de récupération s’applique à tous les services Microsoft 365 compatibles avec la clé client. Les services individuels utilisent la clé de disponibilité différemment. Microsoft 365 utilise uniquement la clé de disponibilité comme décrit ci-dessous.

### <a name="exchange-online-and-skype-for-business-uses"></a>Exchange Online et Skype Entreprise’utilisation

Outre la fonctionnalité de récupération, Exchange Online et Skype Entreprise utilisent la clé de disponibilité pour garantir la disponibilité des données pendant les problèmes opérationnels temporaires ou intermittents liés au service qui accède aux clés racine. Lorsque le service ne peut pas accéder à l’une de vos clés client dans Azure Key Vault en raison d’erreurs temporaires, le service utilise automatiquement la clé de disponibilité. Le service ne passe JAMAIS directement à la clé de disponibilité.

Les systèmes automatisés dans Exchange Online et Skype Entreprise peuvent utiliser la clé de disponibilité lors d’erreurs temporaires pour prendre en charge des services principaux automatisés tels que l’antivirus, la découverte électronique, la protection contre la perte de données, les déplacements de boîtes aux lettres et l’indexation des données.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>SharePoint Les fichiers en ligne, OneDrive Entreprise et Teams en ligne

Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, la clé de disponibilité n’est JAMAIS utilisée en dehors de la fonctionnalité de récupération et les clients doivent explicitement demander à Microsoft de lancer l’utilisation de la clé de disponibilité pendant un scénario de récupération. Les opérations de service automatisées reposent uniquement sur vos clés client dans le coffre de clés Azure. Pour obtenir des informations détaillées sur le fonctionnement de la hiérarchie de clés pour ces services, voir comment les fichiers [SharePoint Online, OneDrive Entreprise](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key)et Teams utilisent la clé de disponibilité.

## <a name="availability-key-security"></a>Sécurité de clé de disponibilité

Microsoft partage la responsabilité de la protection des données avec vous en insérant la clé de disponibilité et en prenant des mesures étendues pour la protéger. Microsoft n’expose pas le contrôle direct de la clé de disponibilité aux clients. Par exemple, vous pouvez uniquement faire pivoter (faire pivoter) les clés que vous possédez dans Azure Key Vault. Pour plus d’informations, voir [Roll or rotate a customer key or an availability key](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Magasins de clés secrètes de disponibilité

Microsoft protège les clés de disponibilité dans les magasins de clés secrètes internes contrôlés par l’accès, tels que le coffre de clés Azure accessible aux clients. Nous implémentons des contrôles d’accès pour empêcher les administrateurs Microsoft d’accéder directement aux secrets qu’ils contiennent. Les opérations du magasin secret, y compris la rotation et la suppression de clés, se produisent par le biais de commandes automatisées qui n’impliquent jamais un accès direct à la clé de disponibilité. Les opérations de gestion du magasin secret sont limitées à des ingénieurs spécifiques et nécessitent une escalade des privilèges via un outil interne, Lockbox. L’escalade de privilège nécessite l’approbation et la justification du responsable avant d’être accordée. Lockbox garantit que l’accès est lié au temps avec la révocation automatique d’accès à l’expiration du délai ou à la fermeture de session de l’ingénieur.

**Exchange Online et Skype Entreprise** clés de disponibilité sont stockées dans une Exchange Online de clés secrètes Active Directory. Les clés de disponibilité sont stockées en toute sécurité dans des conteneurs propres au client dans le contrôleur de domaine Active Directory. Cet emplacement de stockage sécurisé est distinct et isolé de la SharePoint des fichiers secrets SharePoint Online, OneDrive Entreprise et Teams fichiers.

**SharePoint en ligne, OneDrive Entreprise** et Teams clés de disponibilité des fichiers sont stockées dans un magasin de clés secrètes interne géré par l’équipe de service. Ce service de stockage sécurisé des secrets dispose de serveurs frontaux avec des points de terminaison d’application et SQL Database comme serveur principal. Les clés de disponibilité sont stockées dans le SQL Database et sont enveloppées (chiffrées) par des clés de chiffrement de banque secrète qui utilisent une combinaison DES-256 et HMAC pour chiffrer la clé de disponibilité au repos. Les clés de chiffrement de magasin secret sont stockées dans un composant isolé logiquement de la même SQL Database et sont chiffrées avec des clés RSA-2048 contenues dans des certificats gérés par l’autorité de certification Microsoft. Ces certificats sont stockés dans les serveurs frontaux du magasin secret qui effectuent des opérations sur la base de données.

### <a name="defense-in-depth"></a>Défense en profondeur

Microsoft utilise une stratégie de défense en profondeur pour empêcher les acteurs malveillants d’avoir un impact sur la confidentialité, l’intégrité ou la disponibilité des données client stockées dans Microsoft Cloud. Des contrôles de prévention et de témoin spécifiques sont implémentés pour protéger la clé secrète et la clé de disponibilité dans le cadre de la stratégie de sécurité globale.

Microsoft 365 est conçu pour éviter toute utilisation abusive de la clé de disponibilité. La couche d’application est la seule méthode par laquelle les clés, y compris la clé de disponibilité, peuvent être utilisées pour chiffrer et déchiffrer des données. Seul Microsoft 365 code de service a la possibilité d’interpréter et de parcourir la hiérarchie de clés pour les activités de chiffrement et de déchiffrement. Il existe une isolation logique entre les emplacements de stockage des clés client, des clés de disponibilité, d’autres clés hiérarchiques et des données client. Cette isolation atténue le risque d’exposition des données dans le cas où un ou plusieurs emplacements sont compromis. Chaque couche de la hiérarchie a intégré des fonctionnalités de détection des intrusions 24 heures sur 24 et 7 jours sur 7 pour protéger les données et les secrets stockés.

Les contrôles d’accès sont implémentés pour empêcher tout accès non autorisé aux systèmes internes, y compris aux magasins de clés secrètes de disponibilité. Les ingénieurs Microsoft n’ont pas un accès direct aux magasins de clés secrètes de disponibilité. Pour plus d’informations sur les contrôles d’accès, examinez [les contrôles d’accès](/compliance/assurance/assurance-administrative-access-controls-overview)administratif Microsoft 365 .

Les contrôles techniques empêchent le personnel Microsoft de se connecter à des comptes de service hautement privilégiés, qui pourraient sinon être utilisés par des personnes malveillantes pour usurper l’identité services Microsoft. Par exemple, ces contrôles empêchent l’accès interactif.

La journalisation de la sécurité et les contrôles de surveillance sont un autre dispositif de protection en profondeur mis en œuvre qui atténue les risques pour services Microsoft et vos données. Les équipes de service Microsoft ont déployé des solutions de surveillance actives qui génèrent des alertes et des journaux d’audit. Toutes les équipes de service téléchargent leurs journaux dans un référentiel central où les journaux sont agrégés et traitées. Les outils internes examinent automatiquement les enregistrements pour vérifier que les services fonctionnent dans un état optimal, résilient et sécurisé. Une activité inhabituelle est signalée pour un examen plus approfondi.

Tout événement de journal qui indique une violation potentielle de la stratégie de sécurité Microsoft est immédiatement mis à l’attention des équipes de sécurité Microsoft. Microsoft 365 sécurité a configuré des alertes pour détecter les tentatives d’accès aux magasins de clés secrètes de disponibilité. Les alertes sont également générées si le personnel de Microsoft tente d’accéder de manière interactive aux comptes de service, ce qui est interdit et protégé par les contrôles d’accès. Microsoft 365 sécurité détecte et avertit également les écarts du service Microsoft 365 par rapport aux opérations de référence normales. Les malfaiteurs qui tentent d’utiliser Microsoft 365 services informatiques déclenchent des alertes qui entraînent la délation de l’agresseur de l’environnement cloud de Microsoft.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Utiliser la clé de disponibilité pour récupérer après une perte de clé

Si vous perdez le contrôle de vos clés client, la clé de disponibilité vous permet de récupérer et de re-chiffrer vos données.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Procédure de récupération pour Exchange Online et Skype Entreprise

Si vous perdez le contrôle de vos clés client, la clé de disponibilité vous permet de récupérer vos données et de remettre en ligne vos ressources Microsoft 365 données impactées. La clé de disponibilité continue de protéger vos données pendant la récupération. À un niveau élevé, pour récupérer entièrement après une perte de clé, vous devez créer une nouvelle stratégie de dép. de données et déplacer les ressources impactées vers la nouvelle stratégie.

Pour chiffrer vos données avec de nouvelles clés client, créez de nouvelles clés dans Azure Key Vault, créez un dep à l’aide des nouvelles clés client, puis affectez la nouvelle dep aux boîtes aux lettres actuellement chiffrées avec le PED précédent pour lesquels les clés ont été perdues ou compromises.

Ce processus de re-chiffrement peut prendre jusqu’à 72 heures. Il s’agit de la durée standard lorsque vous modifiez une PD DEP.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Procédure de récupération pour SharePoint online, OneDrive Entreprise et Teams fichiers

Pour SharePoint en ligne, OneDrive Entreprise et Teams, la clé de disponibilité n’est JAMAIS utilisée en dehors de la fonctionnalité de récupération. Vous devez explicitement demander à Microsoft de lancer l’utilisation de la clé de disponibilité lors d’un scénario de récupération. Pour lancer le processus de récupération, contactez Microsoft pour activer la clé de disponibilité. Une fois activée, la clé de disponibilité est automatiquement utilisée pour déchiffrer vos données, ce qui vous permet de chiffrer les données avec un dep nouvellement créé associé aux nouvelles clés client.  

Cette opération est proportionnelle au nombre de sites dans votre organisation. Une fois que vous avez appelé Microsoft pour utiliser la clé de disponibilité, vous devez être entièrement en ligne dans un délai d’environ quatre heures.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Comment Exchange Online et Skype Entreprise la clé de disponibilité

Lorsque vous créez une dep avec clé client, Microsoft 365 génère une clé de stratégie de chiffrement de données (DEP Key) associée à cette dep. Le service chiffre la clé DEP trois fois : une fois avec chacune des clés client et une fois avec la clé de disponibilité. Seules les versions chiffrées de la clé DEP sont stockées et une clé DEP peut uniquement être déchiffrée avec les clés client ou la clé de disponibilité. La clé DEP est ensuite utilisée pour chiffrer les clés de boîte aux lettres, qui chiffrent des boîtes aux lettres individuelles.
  
Microsoft 365 suit ce processus pour déchiffrer et fournir des données lorsque les clients utilisent le service :
  
1. Déchiffrez la clé DEP à l’aide de la clé client.

2. Utilisez la clé DEP déchiffrée pour déchiffrer une clé de boîte aux lettres.

3. Utilisez la clé de boîte aux lettres déchiffrée pour déchiffrer la boîte aux lettres elle-même, ce qui vous permet d’accéder aux données de la boîte aux lettres.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Comment SharePoint en ligne, OneDrive Entreprise et les fichiers Teams la clé de disponibilité

L’architecture SharePoint online et OneDrive Entreprise et l’implémentation de la clé client et de la clé de disponibilité sont différentes de Exchange Online et Skype Entreprise.
  
Lorsqu’une organisation passe à des clés gérées par le client, Microsoft 365 crée une clé intermédiaire spécifique à l’organisation (TIK). Microsoft 365 chiffre deux fois la TIK, une fois avec chacune des clés client, et stocke les deux versions chiffrées de la TIK. Seules les versions chiffrées de la TIK sont stockées et une TIK ne peut être déchiffrée qu’avec les clés client. La TIK est ensuite utilisée pour chiffrer les clés de site, qui sont ensuite utilisées pour chiffrer les clés blob (également appelées clés de blocs de fichiers). Selon la taille du fichier, le service peut fractionner un fichier en plusieurs blocs de fichiers chacun avec une clé unique. Les blobs (blocs de fichiers) eux-mêmes sont chiffrés avec les clés blob et stockés dans Microsoft Azure service de stockage blob.
  
Microsoft 365 suit ce processus pour déchiffrer et fournir des fichiers clients lorsque les clients utilisent le service :

1. Déchiffrez la TIK à l’aide de la clé client.

2. Utilisez la TIK déchiffrée pour déchiffrer une clé de site.

3. Utilisez la clé de site déchiffrée pour déchiffrer une clé blob.

4. Utilisez la clé blob déchiffrée pour déchiffrer l’objet blob.

Microsoft 365 déchiffre une TIK en émettant deux demandes de déchiffrement à Azure Key Vault avec un léger décalage. Le premier à terminer fournit le résultat, en anxant l’autre demande.
  
Si vous perdez l’accès à vos clés client, Microsoft 365 chiffre également la TIK avec une clé de disponibilité et la stocke avec les clés TIK chiffrées avec chaque clé client. La TIK chiffrée avec la clé de disponibilité est utilisée uniquement lorsque le client appelle Microsoft pour inscrire le chemin de récupération lorsqu’il a perdu l’accès à ses clés, de manière malveillante ou accidentelle.
  
Pour des raisons de disponibilité et d’échelle, les TIK déchiffrés sont mis en cache dans un cache mémoire limité dans le temps. Deux heures avant l’expiration d’un cache TIK, Microsoft 365 tente de déchiffrer chaque TIK. Le déchiffrement des tiks étend la durée de vie du cache. Si le déchiffrement TIK échoue pendant un certain temps, Microsoft 365 génère une alerte pour avertir les ingénieurs avant l’expiration du cache. Ce n’est que si le client appelle Microsoft Microsoft 365 lancer l’opération de récupération, ce qui implique le déchiffrement de la TIK avec la clé de disponibilité stockée dans la banque secrète microsoft et l’intégration du client à nouveau à l’aide de la TIK déchiffrée et d’un nouvel ensemble de clés Azure Key Vault fournies par le client.
  
À ce jour, la clé client est impliquée dans la chaîne de chiffrement et de déchiffrement des données de fichier SharePoint Online stockées dans le magasin d’objets blob Azure, mais pas dans les métadonnées ou les éléments de liste SharePoint Online stockés dans le SQL Database. Microsoft 365 n’utilise pas la clé de disponibilité pour les fichiers Exchange Online, Skype Entreprise, SharePoint Online, OneDrive Entreprise et Teams autres que ceux décrits ci-dessus, qui sont initiés par le client. L’accès humain aux données client est protégé par Customer Lockbox.

## <a name="availability-key-triggers"></a>Déclencheurs de clé de disponibilité

Microsoft 365 la clé de disponibilité uniquement dans des circonstances spécifiques. Ces circonstances diffèrent selon le service.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Déclencheurs pour Exchange Online et Skype Entreprise
  
1. Microsoft 365 lit le dep auquel la boîte aux lettres est affectée afin de déterminer l’emplacement des deux clés client dans Azure Key Vault.

2. Microsoft 365 choisit de manière aléatoire l’une des deux clés client du dep et envoie une demande à Azure Key Vault pour décocrire la clé DEP à l’aide de la clé client.

3. Si la demande de décodage de la clé DEP à l’aide de la clé client échoue, Microsoft 365 envoie une deuxième demande à Azure Key Vault, qui lui demande cette fois d’utiliser l’autre (deuxième) clé client.

4. Si la deuxième demande de décodage de la clé DEP à l’aide de la clé client échoue, Microsoft 365 examine les résultats des deux demandes.

    - Si l’examen détermine que les demandes n’ont pas pu renvoyer une ERREUR système :

       - Microsoft 365 la clé de disponibilité pour déchiffrer la clé DEP.

       - Microsoft 365 la clé DEP pour déchiffrer la clé de boîte aux lettres et terminer la demande de l’utilisateur. 

       - Dans ce cas, Azure Key Vault ne peut pas répondre ou est inaccessible en raison d’une erreur temporaire.

    - Si l’examen détermine que les demandes n’ont pas pu renvoyer ACCESS REFUSÉ :

       - Cela signifie que des actions délibérées, accidentelles ou malveillantes ont été prises pour rendre les clés client indisponibles (par exemple, pendant le processus de purge des données dans le cadre de la sortie du service).

       - Dans ce cas, la clé de disponibilité est utilisée uniquement pour les actions système et non pour les actions de l’utilisateur, la demande de l’utilisateur échoue et l’utilisateur reçoit un message d’erreur.

> [!IMPORTANT]
> Microsoft 365 code de service a toujours un jeton de connexion valide pour le raisonnement sur les données client afin de fournir des services cloud à valeur ajoutée. Par conséquent, tant que la clé de disponibilité n’a pas été supprimée, elle peut servir de référence pour les actions initiées ou internes à des Exchange Online et des Skype Entreprise telles que la création ou le déplacement de boîtes aux lettres d’index de recherche. Cela s’applique aux demandes ERRORS temporaires et ACCÈS REFUSÉ à Azure Key Vault.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Déclencheurs pour SharePoint en ligne, OneDrive Entreprise et Teams fichiers

Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, la clé de disponibilité n’est JAMAIS utilisée en dehors de la fonctionnalité de récupération et les clients doivent explicitement demander à Microsoft de lancer l’utilisation de la clé de disponibilité pendant un scénario de récupération.

## <a name="audit-logs-and-the-availability-key"></a>Journaux d’audit et clé de disponibilité

Les systèmes automatisés dans Microsoft 365 traiter toutes les données à mesure qu’ils circulent dans le système pour fournir des services cloud, par exemple, la détection électronique, la détection électronique, la protection contre la perte de données et l’indexation des données. Microsoft 365 ne génère pas de journaux visibles par le client pour cette activité. En outre, le personnel Microsoft n’accède pas à vos données dans le cadre de ces opérations système normales.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>Exchange Online journalisation Skype Entreprise clé de disponibilité

Lorsque Exchange Online et Skype Entreprise la clé de disponibilité pour fournir le service, Microsoft 365 publie des journaux visibles par les clients accessibles à partir du Centre de sécurité et conformité. Un enregistrement du journal d’audit pour l’opération de clé de disponibilité est généré chaque fois que le service utilise la clé de disponibilité. Un nouveau type d’enregistrement appelé « Chiffrement du service de clé client » avec le type d’activité « De retour à la clé de disponibilité » permet aux administrateurs de filtrer les résultats de recherche du journal [d’audit](./search-the-audit-log-in-security-and-compliance.md) unifié pour afficher les enregistrements de clé de disponibilité.

Les enregistrements de journal incluent des attributs tels que la date, l’heure, l’activité, l’ID d’organisation et l’ID de stratégie de chiffrement des données. L’enregistrement est disponible dans le cadre des journaux d’audit unifiés et est accessible à partir de l’onglet Recherche du journal d’audit du Centre de sécurité & conformité.

![Recherche de clé de disponibilité dans le journal d’audit](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Exchange Online et Skype Entreprise clé de disponibilité utilisent le schéma [](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) commun activité de gestion Office 365 avec des paramètres personnalisés ajoutés : ID de stratégie, ID de version de la clé d’étendue et ID de demande.

![Paramètres personnalisés de clé de disponibilité](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>SharePoint Journalisation de la clé de disponibilité OneDrive Entreprise, OneDrive Entreprise et Teams fichiers en ligne

La journalisation des clés de disponibilité n’est pas encore disponible pour ces services. Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, la clé de disponibilité est activée uniquement par Microsoft, lorsque vous vous y êtes invité, à des fins de récupération. Par conséquent, vous connaissez déjà chaque événement dans lequel la clé de disponibilité est utilisée pour ces services.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Clé de disponibilité dans la hiérarchie de clés client
  
Microsoft 365 utilise la clé de disponibilité pour encapsuler le niveau de clés inférieur dans la hiérarchie de clés établie pour le chiffrement du service de clé client. Différentes hiérarchies clés existent entre les services. Les algorithmes de clé diffèrent également entre les clés de disponibilité et les autres clés dans la hiérarchie de chaque service applicable. Les algorithmes de clé de disponibilité utilisés par les différents services sont les suivants :

- Les clés Exchange Online et Skype Entreprise de disponibilité utilisent AES-256.

- Les SharePoint de disponibilité des fichiers OneDrive Entreprise, Teams en ligne et en ligne utilisent RSA-2048.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour Exchange Online et Skype Entreprise

![Chiffrements de chiffrement pour Exchange Online clé client](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour SharePoint Online et OneDrive Entreprise

![Chiffrements de chiffrement pour SharePoint client en ligne](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Articles connexes

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)