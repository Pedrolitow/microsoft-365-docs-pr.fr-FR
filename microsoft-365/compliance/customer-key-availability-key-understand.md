---
title: Découvrir la clé de disponibilité pour la clé client
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- purview-compliance
- tier1
search.appverid:
- MET150
description: Découvrez la clé de disponibilité utilisée pour récupérer les clés client perdues.
ms.openlocfilehash: 3a6fcebcd9ccc3a6e81728803e19b3b21a62432a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68641950"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Découvrir la clé de disponibilité pour la clé client

La clé de disponibilité est une clé racine générée et approvisionnée automatiquement lorsque vous créez une stratégie de chiffrement des données. Microsoft 365 stocke et protège la clé de disponibilité. La clé de disponibilité est fonctionnellement semblable aux deux clés racine que vous fournissez pour le chiffrement de service avec la clé client. La clé de disponibilité encapsule les clés d’un niveau inférieur dans la hiérarchie de clés. Contrairement aux clés que vous fournissez et gérez dans Azure Key Vault, vous ne pouvez pas accéder directement à la clé de disponibilité. Les services automatisés Microsoft 365 gèrent la clé de disponibilité par programmation. Ces services lancent des opérations automatisées qui n’impliquent jamais un accès direct à la clé de disponibilité.

L’objectif principal de la clé de disponibilité est de fournir une capacité de récupération à partir de la perte inattendue de clés racine que vous gérez. La perte peut être le résultat d’une mauvaise gestion ou d’une action malveillante. Si vous perdez le contrôle de vos clés racine, contactez Support Microsoft et Microsoft vous aidera tout au long du processus de récupération à l’aide de la clé de disponibilité. Vous allez utiliser la clé de disponibilité pour migrer vers une nouvelle stratégie de chiffrement des données avec de nouvelles clés racine que vous provisionnez.

Le stockage et le contrôle de la clé de disponibilité sont délibérément différents d’Azure Key Vault clés pour trois raisons :

- La clé de disponibilité fournit une fonctionnalité de récupération « break-glass » si le contrôle sur les deux clés Azure Key Vault est perdu.
- La séparation des contrôles logiques et des emplacements de stockage sécurisés fournit une défense en profondeur et protège contre la perte de toutes les clés et de vos données d’une attaque ou d’un point de défaillance unique.
- La clé de disponibilité fournit une fonctionnalité de haute disponibilité si les services Microsoft 365 ne parviennent pas à atteindre les clés hébergées dans Azure Key Vault en raison d’erreurs temporaires. Cette règle s’applique uniquement au chiffrement de service Exchange Online et Skype Entreprise. Les fichiers SharePoint Online, OneDrive Entreprise et Teams n’utilisent jamais la clé de disponibilité, sauf si vous demandez explicitement à Microsoft de lancer le processus de récupération.

Le partage de la responsabilité de protéger vos données, à l’aide de diverses protections et processus pour la gestion des clés, réduit le risque que toutes les clés (et donc vos données) soient définitivement perdues ou détruites. Microsoft vous donne l’autorité unique sur la désactivation ou la destruction de la clé de disponibilité lorsque vous quittez le service. Par défaut, personne chez Microsoft n’a accès à la clé de disponibilité : elle est uniquement accessible par le code de service Microsoft 365.

Pour plus d’informations sur la façon dont nous sécurisons les clés, consultez le Centre de gestion de la [confidentialité Microsoft](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) .
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="availability-key-uses"></a>Utilisations de la clé de disponibilité

La clé de disponibilité fournit la fonctionnalité de récupération pour les scénarios dans lesquels un insider malveillant externe ou malveillant vole le contrôle de votre coffre de clés, ou lorsque la mauvaise gestion accidentelle entraîne la perte de clés racine. Cette fonctionnalité de récupération s’applique à tous les services Microsoft 365 compatibles avec la clé client. Les services individuels utilisent la clé de disponibilité différemment. Microsoft 365 utilise uniquement la clé de disponibilité comme décrit ci-dessous.

### <a name="exchange-online-and-skype-for-business-uses"></a>utilisations Exchange Online et Skype Entreprise

En plus de la fonctionnalité de récupération, Exchange Online et Skype Entreprise utiliser la clé de disponibilité pour garantir la disponibilité des données lors de problèmes opérationnels temporaires ou intermittents liés au service qui accède aux clés racine. Lorsque le service ne peut pas atteindre l’une de vos clés client dans Azure Key Vault en raison d’erreurs temporaires, le service utilise automatiquement la clé de disponibilité. Le service ne passe JAMAIS directement à la clé de disponibilité.

Les systèmes automatisés dans Exchange Online et Skype Entreprise peuvent utiliser la clé de disponibilité pendant les erreurs temporaires pour prendre en charge les services back-end automatisés tels que l’antivirus, la découverte électronique, les Protection contre la perte de données Microsoft Purview, les déplacements de boîtes aux lettres et les données Indexation.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>Les fichiers SharePoint Online, OneDrive Entreprise et Teams utilisent

Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, la clé de disponibilité n’est JAMAIS utilisée en dehors de la fonctionnalité de récupération et les clients doivent indiquer explicitement à Microsoft de lancer l’utilisation de la clé de disponibilité pendant un scénario de récupération. Les opérations de service automatisé reposent uniquement sur vos clés client dans Azure Key Vault. Pour plus d’informations sur le fonctionnement de la hiérarchie de clés pour ces services, consultez [comment les fichiers SharePoint Online, OneDrive Entreprise et Teams utilisent la clé de disponibilité](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key).

## <a name="availability-key-security"></a>Sécurité de la clé de disponibilité

Microsoft partage la responsabilité de la protection des données avec vous en instanciant la clé de disponibilité et en prenant des mesures complètes pour la protéger. Microsoft n’expose pas le contrôle direct de la clé de disponibilité aux clients. Par exemple, vous pouvez uniquement restaurer (faire pivoter) les clés que vous possédez dans Azure Key Vault. Pour plus d’informations, consultez [Roll or rotate a customer key or an availability key](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Magasins de clés secrètes de disponibilité

Microsoft protège les clés de disponibilité dans les magasins de secrets internes contrôlés par l’accès, comme les Key Vault Azure accessibles par le client. Nous implémentons des contrôles d’accès pour empêcher les administrateurs Microsoft d’accéder directement aux secrets qu’ils contiennent. Les opérations du Magasin des secrets, y compris la rotation et la suppression des clés, se produisent via des commandes automatisées qui n’impliquent jamais un accès direct à la clé de disponibilité. Les opérations de gestion des magasins secrets sont limitées à des ingénieurs spécifiques et nécessitent une élévation des privilèges via un outil interne, Lockbox. L’élévation des privilèges nécessite l’approbation et la justification du gestionnaire avant d’être accordée. Lockbox garantit que l’accès est limité dans le temps avec la révocation automatique de l’accès à l’expiration du délai d’expiration ou la déconnexion de l’ingénieur.

les clés de disponibilité **Exchange Online et Skype Entreprise** sont stockées dans un magasin de secrets Exchange Online Active Directory. Les clés de disponibilité sont stockées en toute sécurité dans des conteneurs spécifiques au locataire dans le contrôleur de domaine Active Directory. Cet emplacement de stockage sécurisé est distinct et isolé du magasin de secrets de fichiers SharePoint Online, OneDrive Entreprise et Teams.

Les clés de disponibilité **des fichiers SharePoint Online, OneDrive Entreprise et Teams** sont stockées dans un magasin de secrets interne géré par l’équipe de service. Ce service de stockage sécurisé des secrets a des serveurs frontaux avec des points de terminaison d’application et un SQL Database comme serveur principal. Les clés de disponibilité sont stockées dans le SQL Database et sont encapsulées (chiffrées) par des clés de chiffrement de magasin secret qui utilisent une combinaison d’AES-256 et HMAC pour chiffrer la clé de disponibilité au repos. Les clés de chiffrement du magasin secret sont stockées dans un composant isolé logiquement du même SQL Database et sont chiffrées avec des clés RSA-2048 contenues dans des certificats gérés par l’autorité de certification Microsoft. Ces certificats sont stockés dans les serveurs frontaux du magasin secret qui effectuent des opérations sur la base de données.

### <a name="defense-in-depth"></a>Défense en profondeur

Microsoft utilise une stratégie de défense approfondie pour empêcher les acteurs malveillants d’affecter la confidentialité, l’intégrité ou la disponibilité des données client stockées dans microsoft cloud. Des contrôles préventifs et de détection spécifiques sont implémentés pour protéger le magasin de secrets et la clé de disponibilité dans le cadre de la stratégie de sécurité globale.

Microsoft 365 est conçu pour empêcher toute mauvaise utilisation de la clé de disponibilité. La couche Application est la seule méthode par laquelle les clés, y compris la clé de disponibilité, peuvent être utilisées pour chiffrer et déchiffrer des données. Seul le code de service Microsoft 365 a la possibilité d’interpréter et de parcourir la hiérarchie des clés pour les activités de chiffrement et de déchiffrement. L’isolation logique existe entre les emplacements de stockage des clés client, des clés de disponibilité, d’autres clés hiérarchiques et des données client. Cette isolation atténue le risque d’exposition des données en cas de compromission d’un ou de plusieurs emplacements. Chaque couche de la hiérarchie a intégré des fonctionnalités de détection d’intrusion 24 h/24 et 7 j/7 pour protéger les données et les secrets stockés.

Des contrôles d’accès sont implémentés pour empêcher l’accès non autorisé aux systèmes internes, y compris les magasins de clés secrètes de disponibilité. Les ingénieurs Microsoft n’ont pas d’accès direct aux magasins de clés secrètes de disponibilité. Pour plus d’informations sur les contrôles d’accès, consultez [Contrôles d’accès administratifs dans Microsoft 365](/compliance/assurance/assurance-administrative-access-controls-overview).

Les contrôles techniques empêchent le personnel De Microsoft de se connecter à des comptes de service à privilèges élevés, qui pourraient autrement être utilisés par les attaquants pour emprunter l’identité des services Microsoft. Par exemple, ces contrôles empêchent l’ouverture de session interactive.

Les contrôles de journalisation et de surveillance de la sécurité sont une autre protection de défense en profondeur implémentée qui atténue les risques pour les services Microsoft et vos données. Les équipes de service Microsoft ont déployé des solutions de supervision actives qui génèrent des alertes et des journaux d’audit. Toutes les équipes de service chargent leurs journaux dans un référentiel central où les journaux sont agrégés et traités. Les outils internes examinent automatiquement les enregistrements pour vérifier que les services fonctionnent dans un état optimal, résilient et sécurisé. L’activité inhabituelle est signalée pour examen plus approfondi.

Tout événement de journal qui indique une violation potentielle de la stratégie de sécurité Microsoft est immédiatement porté à l’attention des équipes de sécurité Microsoft. La sécurité Microsoft 365 a configuré des alertes pour détecter les tentatives d’accès aux magasins de clés secrètes de disponibilité. Des alertes sont également générées si le personnel de Microsoft tente d’ouvrir une session interactive aux comptes de service, ce qui est interdit et protégé par les contrôles d’accès. La sécurité Microsoft 365 détecte également et alerte les écarts du service Microsoft 365 par rapport aux opérations de base de référence normales. Les malfaiteurs qui tentent de mal utiliser les services Microsoft 365 déclenchent des alertes qui entraînent l’éviction du contrevenant de l’environnement cloud Microsoft.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Utiliser la clé de disponibilité pour récupérer de la perte de clé

Si vous perdez le contrôle de vos clés client, la clé de disponibilité vous permet de récupérer et de chiffrer à nouveau vos données.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Procédure de récupération pour Exchange Online et Skype Entreprise

Si vous perdez le contrôle de vos clés client, la clé de disponibilité vous permet de récupérer vos données et de remettre en ligne vos ressources Microsoft 365 impactées. La clé de disponibilité continue de protéger vos données pendant la récupération. À un niveau élevé, pour récupérer complètement de la perte de clé, vous devez créer un dep et déplacer les ressources impactées vers la nouvelle stratégie.

Pour chiffrer vos données avec de nouvelles clés client, créez de nouvelles clés dans Azure Key Vault, créez un dep à l’aide des nouvelles clés client, puis affectez le nouveau dep aux boîtes aux lettres actuellement chiffrées avec le dep précédent pour lequel les clés ont été perdues ou compromises.

Ce processus de nouveau chiffrement peut prendre jusqu’à 72 heures. Il s’agit de la durée standard lorsque vous modifiez un DEP.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Procédure de récupération pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, la clé de disponibilité n’est JAMAIS utilisée en dehors de la fonctionnalité de récupération. Vous devez indiquer explicitement à Microsoft de lancer l’utilisation de la clé de disponibilité pendant un scénario de récupération. Pour lancer le processus de récupération, contactez Microsoft pour activer la clé de disponibilité. Une fois activée, la clé de disponibilité est automatiquement utilisée pour déchiffrer vos données, ce qui vous permet de chiffrer les données avec un dep nouvellement créé associé aux nouvelles clés client.  

Cette opération est proportionnelle au nombre de sites de votre organisation. Une fois que vous avez appelé Microsoft pour utiliser la clé de disponibilité, vous devez être entièrement en ligne dans un délai d’environ quatre heures.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Comment Exchange Online et Skype Entreprise utiliser la clé de disponibilité

Lorsque vous créez un DEP avec une clé client, Microsoft 365 génère une clé de stratégie de chiffrement des données (CLÉ DEP) associée à ce dep. Le service chiffre la clé DEP trois fois : une fois avec chacune des clés client et une fois avec la clé de disponibilité. Seules les versions chiffrées de la clé DEP sont stockées, et une clé DEP ne peut être déchiffrée qu’avec les clés client ou la clé de disponibilité. La clé DEP est ensuite utilisée pour chiffrer les clés de boîte aux lettres, qui chiffrent des boîtes aux lettres individuelles.
  
Microsoft 365 suit ce processus pour déchiffrer et fournir des données lorsque les clients utilisent le service :
  
1. Déchiffrez la clé DEP à l’aide de la clé client.

2. Utilisez la clé DEP déchiffrée pour déchiffrer une clé de boîte aux lettres.

3. Utilisez la clé de boîte aux lettres déchiffrée pour déchiffrer la boîte aux lettres elle-même, ce qui vous permet d’accéder aux données de la boîte aux lettres.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Utilisation de la clé de disponibilité par les fichiers SharePoint Online, OneDrive Entreprise et Teams

L’architecture et l’implémentation de SharePoint Online et de OneDrive Entreprise pour la clé client et la clé de disponibilité sont différentes de Exchange Online et Skype Entreprise.
  
Lorsqu’une organisation passe à des clés gérées par le client, Microsoft 365 crée une clé intermédiaire spécifique à l’organisation (TIK). Microsoft 365 chiffre la TIK deux fois, une fois avec chacune des clés client, et stocke les deux versions chiffrées de la TIK. Seules les versions chiffrées de la TIK sont stockées, et une TIK ne peut être déchiffrée qu’avec les clés client. La TIK est ensuite utilisée pour chiffrer les clés de site, qui sont ensuite utilisées pour chiffrer les clés d’objet blob (également appelées clés de bloc de fichier). Selon la taille du fichier, le service peut fractionner un fichier en plusieurs blocs de fichiers chacun avec une clé unique. Les objets blob (blocs de fichiers) eux-mêmes sont chiffrés avec les clés d’objet blob et stockés dans le service de stockage d’objets blob Microsoft Azure.
  
Microsoft 365 suit ce processus pour déchiffrer et fournir des fichiers client lorsque les clients utilisent le service :

1. Déchiffrez la TIK à l’aide de la clé client.

2. Utilisez la TIK déchiffrée pour déchiffrer une clé de site.

3. Utilisez la clé de site déchiffrée pour déchiffrer une clé d’objet blob.

4. Utilisez la clé d’objet blob déchiffrée pour déchiffrer l’objet blob.

Microsoft 365 déchiffre une TIK en émettant deux demandes de déchiffrement à Azure Key Vault avec un léger décalage. Le premier à terminer fournit le résultat, en annulant l’autre demande.
  
Si vous perdez l’accès à vos clés client, Microsoft 365 chiffre également la TIK à l’aide d’une clé de disponibilité et stocke celle-ci avec les clés de chiffrement chiffrées avec chaque clé client. La TIK chiffrée avec la clé de disponibilité est utilisée uniquement lorsque le client appelle Microsoft pour inscrire le chemin de récupération lorsqu’il a perdu l’accès à ses clés, de manière malveillante ou accidentelle.
  
Pour des raisons de disponibilité et de mise à l’échelle, les tiK déchiffrés sont mis en cache dans un cache de mémoire limité dans le temps. Deux heures avant l’expiration d’un cache TIK, Microsoft 365 tente de déchiffrer chaque TIK. Le déchiffrement des tiks étend la durée de vie du cache. Si le déchiffrement TIK échoue pendant un laps de temps important, Microsoft 365 génère une alerte pour notifier l’ingénierie avant l’expiration du cache. Ce n’est que si le client appelle Microsoft que Microsoft 365 lance l’opération de récupération, ce qui implique le déchiffrement de la TIK avec la clé de disponibilité stockée dans le magasin secret de Microsoft et l’intégration du locataire à nouveau à l’aide de la TIK déchiffrée et d’un nouvel ensemble de clés Azure Key Vault fournies par le client.
  
À ce jour, customer key est impliquée dans la chaîne de chiffrement et de déchiffrement des données de fichiers SharePoint Online stockées dans le magasin d’objets blob Azure, mais pas dans les éléments de liste ou métadonnées SharePoint Online stockés dans le SQL Database. Microsoft 365 n’utilise pas la clé de disponibilité pour les fichiers Exchange Online, Skype Entreprise, SharePoint Online, OneDrive Entreprise et Teams autres que le cas décrit ci-dessus, qui est initié par le client. L’accès humain aux données client est protégé par Customer Lockbox.

## <a name="availability-key-triggers"></a>Déclencheurs de clé de disponibilité

Microsoft 365 déclenche la clé de disponibilité uniquement dans des circonstances spécifiques. Ces circonstances diffèrent selon le service.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Déclencheurs pour Exchange Online et Skype Entreprise
  
1. Microsoft 365 lit le dep auquel la boîte aux lettres est affectée afin de déterminer l’emplacement des deux clés client dans Azure Key Vault.

2. Microsoft 365 choisit de manière aléatoire l’une des deux clés client du dep et envoie une demande à Azure Key Vault pour annuler le dépliage de la clé DEP à l’aide de la clé client.

3. Si la demande de décommutation de la clé DEP à l’aide de la clé client échoue, Microsoft 365 envoie une deuxième demande à Azure Key Vault, en lui demandant cette fois d’utiliser la autre (deuxième) clé client.

4. Si la deuxième demande de décommuter la clé DEP à l’aide de la clé client échoue, Microsoft 365 examine les résultats des deux demandes.

    - Si l’examen détermine que les demandes ont échoué en retournant une erreur système :

       - Microsoft 365 déclenche la clé de disponibilité pour déchiffrer la clé DEP.

       - Microsoft 365 utilise ensuite la clé DEP pour déchiffrer la clé de boîte aux lettres et terminer la demande de l’utilisateur. 

       - Dans ce cas, Azure Key Vault est incapable de répondre ou inaccessible en raison d’une erreur temporaire.

    - Si l’examen détermine que les demandes n’ont pas pu retourner ACCESS DENIED :

       - Cela signifie que des mesures délibérées, accidentelles ou malveillantes ont été prises pour rendre les clés client indisponibles (par exemple, pendant le processus de vidage des données dans le cadre de la sortie du service).

       - Dans ce cas, la clé de disponibilité est utilisée uniquement pour les actions système et non pour les actions de l’utilisateur, la demande de l’utilisateur échoue et l’utilisateur reçoit un message d’erreur.

> [!IMPORTANT]
> Le code de service Microsoft 365 dispose toujours d’un jeton de connexion valide pour le raisonnement sur les données client afin de fournir des services cloud à valeur ajoutée. Par conséquent, tant que la clé de disponibilité n’a pas été supprimée, elle peut être utilisée comme solution de secours pour les actions initiées par des Exchange Online et Skype Entreprise internes, telles que la création d’index de recherche ou le déplacement de boîtes aux lettres. Cela s’applique aux requêtes ERRORS temporaires et ACCESS DENIED adressées à Azure Key Vault.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Déclencheurs pour les fichiers SharePoint Online, OneDrive Entreprise et Teams

Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, la clé de disponibilité n’est JAMAIS utilisée en dehors de la fonctionnalité de récupération et les clients doivent indiquer explicitement à Microsoft de lancer l’utilisation de la clé de disponibilité pendant un scénario de récupération.

## <a name="audit-logs-and-the-availability-key"></a>Journaux d’audit et clé de disponibilité

Les systèmes automatisés de Microsoft 365 traitent toutes les données à mesure qu’elles transitent par le système pour fournir des services cloud, par exemple, l’antivirus, la découverte électronique, la prévention de la perte de données et l’indexation des données. Microsoft 365 ne génère pas de journaux visibles par le client pour cette activité. En outre, le personnel microsoft n’accède pas à vos données dans le cadre de ces opérations système normales.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>journalisation des clés de disponibilité Exchange Online et Skype Entreprise

Lorsque Exchange Online et Skype Entreprise accède à la clé de disponibilité pour fournir un service, Microsoft 365 publie des journaux visibles par le client accessibles à partir du Centre de sécurité et de conformité. Un enregistrement de journal d’audit pour l’opération de clé de disponibilité est généré chaque fois que le service utilise la clé de disponibilité. Un nouveau type d’enregistrement appelé « Chiffrement du service de clé client » avec le type d’activité « Fallback to Availability Key » permet aux administrateurs de filtrer les résultats de recherche du [journal d’audit unifié](./search-the-audit-log-in-security-and-compliance.md) pour afficher les enregistrements de clé de disponibilité.

Les enregistrements de journal incluent des attributs tels que la date, l’heure, l’activité, l’ID d’organisation et l’ID de stratégie de chiffrement des données. L’enregistrement est disponible dans le cadre des journaux d’audit unifiés et est accessible à partir de l’onglet Security & Compliance Center Audit Log Search.

![Rechercher des événements de clé de disponibilité dans le journal d’audit](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Exchange Online et les enregistrements de clé de disponibilité Skype Entreprise utilisent le [schéma commun](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) d’activité de gestion Office 365 avec des paramètres personnalisés ajoutés : ID de stratégie, ID de version de clé d’étendue et ID de demande.

![Paramètres personnalisés de clé de disponibilité](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>Journalisation des clés de disponibilité des fichiers SharePoint Online, OneDrive Entreprise et Teams

La journalisation des clés de disponibilité n’est pas encore disponible pour ces services. Pour les fichiers SharePoint Online, OneDrive Entreprise et Teams, la clé de disponibilité est activée uniquement par Microsoft, lorsque vous y êtes invité, à des fins de récupération. Par conséquent, vous connaissez déjà chaque événement dans lequel la clé de disponibilité est utilisée pour ces services.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Clé de disponibilité dans la hiérarchie customer key
  
Microsoft 365 utilise la clé de disponibilité pour encapsuler le niveau de clés inférieur dans la hiérarchie de clés établie pour le chiffrement du service de clé client. Il existe différentes hiérarchies de clés entre les services. Les algorithmes de clé diffèrent également entre les clés de disponibilité et les autres clés dans la hiérarchie de chaque service applicable. Les algorithmes de clé de disponibilité utilisés par les différents services sont les suivants :

- Les clés de disponibilité Exchange Online et Skype Entreprise utilisent AES-256.

- Les clés de disponibilité des fichiers SharePoint Online, OneDrive Entreprise et Teams utilisent RSA-2048.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Chiffrements utilisés pour chiffrer des clés pour Exchange Online et Skype Entreprise

![Chiffrement des chiffrements pour Exchange Online dans la clé client](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>Chiffrement des chiffrements utilisés pour chiffrer les clés pour SharePoint Online et OneDrive Entreprise

![Chiffrement des chiffrements pour SharePoint Online dans la clé client](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Articles connexes

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Echanger ou alterner entre une clé client ou de disponibilité](customer-key-availability-key-roll.md)
