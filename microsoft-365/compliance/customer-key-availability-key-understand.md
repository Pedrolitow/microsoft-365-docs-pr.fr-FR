---
title: En savoir plus sur la clé de disponibilité pour la clé client Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 02/05/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
description: En savoir plus sur la clé de disponibilité utilisée pour récupérer les clés de client Office 365.
ms.openlocfilehash: cb5284f46245db1d00506ab0e178244aac53a21f
ms.sourcegitcommit: 21338a9287017a66298e0ff557e80051946ebf13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2020
ms.locfileid: "42604171"
---
# <a name="learn-about-the-availability-key-for-office-365-customer-key"></a>En savoir plus sur la clé de disponibilité pour la clé client Office 365

La clé de disponibilité est une clé racine générée et configurée automatiquement lors de la création d’une stratégie de chiffrement de données. Office 365 stocke et protège la clé de disponibilité. La clé de disponibilité est équivalente aux deux clés racines que vous fournissez pour le chiffrement de service avec la clé client. La clé de disponibilité renvoie les clés d’une couche vers le bas dans la hiérarchie de clés. Contrairement aux touches que vous fournissez et gérez dans le coffre de clés Azure, vous ne pouvez pas accéder directement à la clé de disponibilité. Les services automatisés Office 365 gèrent la clé de disponibilité par programmation. Ces services lancent des opérations automatisées qui n’impliquent jamais un accès direct à la clé de disponibilité.

L’objectif principal de la clé de disponibilité est de fournir des fonctionnalités de récupération à partir de la perte imprévisible de clés racines que vous gérez. La perte peut être due à une erreur de gestion ou à une action malveillante. Si vous perdez le contrôle de vos clés racines, contactez le support Microsoft et Microsoft vous aidera à effectuer le processus de récupération à l’aide de la clé de disponibilité. Vous utiliserez la clé de disponibilité pour migrer vers une nouvelle stratégie de chiffrement de données avec de nouvelles clés racine que vous mettez en service.

Le stockage et le contrôle de la clé de disponibilité sont délibérément différents des clés Azure Key Vault pour trois raisons :

- La clé de disponibilité offre une fonctionnalité de récupération, de « disjoncteur », si le contrôle des deux clés Azure Key Vault est perdu.
- La séparation des contrôles logiques et des emplacements de stockage sécurisés fournit une défense approfondie et protège contre la perte de toutes les clés, ainsi que vos données, d’une attaque ou d’un point de défaillance unique.
- La clé de disponibilité offre une fonctionnalité haute disponibilité si les services Office 365 ne peuvent pas atteindre les clés hébergées dans le coffre-fort des clés Azure en raison d’erreurs passagères. Cette règle s’applique uniquement aux services de chiffrement Exchange Online et Skype entreprise. Les fichiers SharePoint Online, OneDrive entreprise et Teams n’utilisent jamais la clé de disponibilité, sauf si vous demandez explicitement à Microsoft de lancer le processus de récupération.

Le partage de la responsabilité de protéger vos données à l’aide d’un grand nombre de protections et de processus de gestion des clés permet de réduire le risque que toutes les clés (et par conséquent, vos données) soient définitivement perdues ou détruites. Microsoft vous fournit une autorité exclusive sur la désactivation ou la destruction de la clé de disponibilité lorsque vous quittez le service. Par défaut, personne de Microsoft n’a accès à la clé de disponibilité : elle est uniquement accessible par le code de service Office 365.

Consultez le centre de gestion de la [confidentialité Microsoft](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) pour plus d’informations sur la sécurisation des clés.
  
## <a name="availability-key-uses"></a>Utilisation de la clé de disponibilité

La clé de disponibilité fournit des fonctionnalités de récupération pour les scénarios dans lesquels un malefactor externe ou un Insider malveillant vole le contrôle de votre coffre-fort ou lorsque la gestion involontaire entraîne la perte de clés racines. Cette fonctionnalité de récupération s’applique à tous les services Office 365 compatibles avec la clé client. Les services individuels utilisent différemment la clé de disponibilité. Office 365 utilise uniquement la clé de disponibilité dans les méthodes décrites ci-dessous.

### <a name="exchange-online-and-skype-for-business-uses"></a>Utilisation d’Exchange Online et de Skype entreprise

En plus de la fonctionnalité de récupération, Exchange Online et Skype entreprise utilisent la clé de disponibilité pour garantir la disponibilité des données lors de problèmes temporaires ou intermittents liés au service qui accède aux clés racines. Lorsque le service ne peut pas atteindre l’une ou l’autre de vos clés de client dans le coffre-fort des clés Azure en raison d’erreurs temporaires, le service utilise automatiquement la clé de disponibilité. Le service n’accède jamais directement à la clé de disponibilité.

Les systèmes automatisés dans Exchange Online et Skype entreprise peuvent utiliser la clé de disponibilité pendant les erreurs temporaires afin de prendre en charge les services principaux automatisés, tels que les antivirus, la découverte électronique, la protection contre la perte de données, les déplacements de boîtes aux lettres et l’indexation des données.

### <a name="sharepointonlineonedriveforbusinessandteamsfiles-uses"></a>SharePoint Online, OneDrive entreprise et les fichiers teams utilisent

Pour les fichiers SharePoint Online, OneDrive entreprise et Teams, la clé de disponibilité n’est jamais utilisée en dehors de la capacité de récupération et les clients doivent explicitement demander à Microsoft d’utiliser la clé de disponibilité pendant un scénario de récupération. Les opérations de service automatisées s’appuient uniquement sur vos clés de client dans le coffre-fort de clés Azure. Pour obtenir des informations détaillées sur le fonctionnement de la hiérarchie des clés pour ces services, voir [How SharePoint Online, OneDrive entreprise et Team Files utilisent la clé Availability](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key).

## <a name="availability-key-security"></a>Sécurité de la clé de disponibilité

Microsoft partage la responsabilité de la protection des données avec vous en instanciant la clé de disponibilité et en prenant des mesures étendues pour la protéger. Microsoft n’expose pas le contrôle direct de la clé de disponibilité aux clients. Par exemple, vous pouvez uniquement faire pivoter les touches dont vous êtes propriétaire dans le coffre de clés Azure. Pour plus d’informations, reportez-vous à [la rubrique répéter ou faire pivoter une clé de client ou de disponibilité](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Magasins clés secrètes de disponibilité

Microsoft protège les clés de disponibilité dans les magasins de secret interne contrôlés à l’accès tels que le coffre-fort de clés Azure. Nous mettons en œuvre des contrôles d’accès pour empêcher les administrateurs Microsoft d’accéder directement aux secrets contenus dans. Les opérations de magasin secret, y compris la rotation et la suppression de clés, ont lieu via des commandes automatiques qui n’impliquent jamais un accès direct à la clé de disponibilité. Les opérations de gestion du magasin secret sont limitées à des ingénieurs spécifiques et nécessitent une escalade de privilèges via un outil interne, bte post. L’escalade des privilèges nécessite l’approbation et la justification du responsable avant d’être accordé. Lockbox garantit que l’accès est limité au temps avec la révocation d’accès automatique lors de l’expiration du temps ou de l’ingénieur déconnexion.

Les clés de disponibilité **Exchange Online et Skype entreprise** sont stockées dans un magasin de secrets Active Directory Exchange Online. Les clés de disponibilité sont stockées de manière sécurisée dans des conteneurs spécifiques du client dans le contrôleur de domaine Active Directory. Cet emplacement de stockage sécurisé est distinct et isolé du magasin de secrets des fichiers SharePoint Online, OneDrive entreprise et Teams.

Les clés de disponibilité des **fichiers SharePoint Online, OneDrive entreprise et** teams sont stockées dans un magasin de secret interne géré par l’équipe de service. Ce service de stockage sécurisé de secrets comporte des serveurs frontaux avec des points de terminaison d’application et une base de données SQL comme serveur principal. Les clés de disponibilité sont stockées dans la base de données SQL et sont encapsulées (chiffrées) par des clés de chiffrement de magasin secret qui utilisent une combinaison de AES-256 et HMAC pour chiffrer la clé de disponibilité au repos. Les clés de chiffrement de la Banque secrète sont stockées dans un composant isolé de façon logique de la même base de données SQL et sont également chiffrées avec les clés RSA-2048 contenues dans les certificats gérés par l’autorité de certification Microsoft. Ces certificats sont stockés dans les serveurs frontaux du magasin secret qui effectuent des opérations sur la base de données.

### <a name="defense-in-depth"></a>Défense en profondeur

Microsoft a recours à une stratégie de protection approfondie pour empêcher les acteurs malveillants d’influer sur la confidentialité, l’intégrité ou la disponibilité des données client stockées dans le Cloud Microsoft. Des contrôles spécifiques de prévention et de détective sont mis en œuvre pour protéger le magasin secret et la clé de disponibilité dans le cadre de la stratégie de sécurité globale.

Office 365 est conçu pour empêcher toute utilisation abusive de la clé de disponibilité. La couche application est la seule méthode qui permet de déchiffrer et de déchiffrer les données, y compris la clé de disponibilité. Seul le code de service Office 365 a la capacité d’interpréter et de parcourir la hiérarchie de clés pour les activités de chiffrement et de déchiffrement. L’isolement logique existe entre les emplacements de stockage des clés client, des clés de disponibilité, d’autres clés hiérarchiques et des données client. Cette isolation réduit le risque d’exposition des données en cas de compromission d’un ou de plusieurs emplacements. Chaque couche de la hiérarchie offre des fonctionnalités de détection d’intrusion 24x7 pour protéger les données et les secrets stockés.

Les contrôles d’accès sont implémentés pour empêcher les accès non autorisés aux systèmes internes, y compris les magasins clés secrètes de disponibilité. Les ingénieurs Microsoft ne disposent pas d’un accès direct aux magasins clés secrètes de disponibilité. Pour plus d’informations sur les contrôles d’accès, consultez la section [contrôles d’accès administratif dans Office 365](https://docs.microsoft.com/Office365/securitycompliance/office-365-administrative-access-controls-overview).

Les contrôles techniques empêchent le personnel de Microsoft de se connecter à des comptes de service à privilèges élevés, qui pourraient sinon être utilisés par des agresseurs pour emprunter l’identité des services Office 365. Par exemple, ces contrôles empêchent l’ouverture de session interactive.

Les contrôles de journalisation et de surveillance de la sécurité sont une autre mise en œuvre de défense approfondie qui limite les risques pour les services Microsoft et vos données. Les équipes de service Microsoft ont déployé des solutions de surveillance actives qui génèrent des alertes et des journaux d’audit. Toutes les équipes de service chargent leurs journaux dans un référentiel central où les journaux sont regroupés et traités. Les outils internes examinent automatiquement les enregistrements pour vérifier que les services fonctionnent dans un état optimal, résilient et sécurisé. L’activité inhabituelle est marquée pour examen supplémentaire.

Tout événement de journal indiquant une violation potentielle de la stratégie de sécurité Microsoft est immédiatement porté à la connaissance des équipes de sécurité Microsoft. La sécurité Office 365 a configuré les alertes pour détecter les tentatives d’accès aux magasins clés secrètes de disponibilité. Des alertes sont également générées si le personnel de Microsoft tente de se connecter de façon interactive à des comptes de service, ce qui est interdit et protégé par les contrôles d’accès. La sécurité d’Office 365 détecte et signale également les écarts du service Office 365 des opérations de base normales. Malefactors toute tentative d’utilisation abusive des services Office 365 déclenche des alertes entraînant l’éviction du contrevenant de l’environnement Cloud Microsoft.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Utiliser la clé de disponibilité pour récupérer suite à une perte de clé

Si vous perdez le contrôle de vos clés de client, la clé de disponibilité vous permet de récupérer et de rechiffrer vos données.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Procédure de récupération pour Exchange Online et Skype entreprise

Si vous perdez le contrôle de vos clés client, la clé de disponibilité vous donne la possibilité de récupérer vos données et de remettre en ligne vos ressources Office 365. La clé de disponibilité continue de protéger vos données pendant la récupération. À un niveau élevé, pour effectuer une récupération complète après une perte de clé, vous devez créer une nouvelle DEP et déplacer les ressources affectées vers la nouvelle stratégie.

Pour chiffrer vos données avec de nouvelles clés de client, créez de nouvelles clés dans le coffre-fort des clés Azure, créez une nouvelle DEP en utilisant les nouvelles clés de client, puis affectez la nouvelle DEP aux boîtes aux lettres actuellement chiffrées avec la DEP précédente pour laquelle les clés ont été perdues ou compromises.

Ce processus de rechiffrement peut prendre jusqu’à 72 heures. Il s’agit de la durée standard lorsque vous modifiez une DEP.
  
### <a name="recovery-procedure-for-sharepointonlineonedriveforbusinessandteamsfiles"></a>Procédure de récupération pour les fichiers SharePoint Online, OneDrive entreprise et Teams

Pour les fichiers SharePoint Online, OneDrive entreprise et Teams, la clé de disponibilité n’est jamais utilisée en dehors de la capacité de récupération. Vous devez indiquer explicitement à Microsoft d’utiliser la clé de disponibilité pendant un scénario de récupération. Pour lancer le processus de récupération, contactez Microsoft pour activer la clé de disponibilité. Une fois activée, la clé de disponibilité est automatiquement utilisée pour déchiffrer vos données, ce qui vous permet de chiffrer les données avec une nouvelle DEP associée à de nouvelles clés de client.  

Cette opération est proportionnelle au nombre de sites dans votre organisation. Une fois que vous appelez Microsoft pour utiliser la clé de disponibilité, vous devez être entièrement en ligne au cours des quatre heures.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Utilisation de la clé de disponibilité par Exchange Online et Skype entreprise

Lorsque vous créez une DEP avec une clé client, Office 365 génère une clé de stratégie de chiffrement de données (clé DEP) associée à cette DEP. Le service chiffre la clé DEP trois fois : une fois avec chacune des clés de client et une fois avec la clé de disponibilité. Seules les versions chiffrées de la clé DEP sont stockées et une clé DEP ne peut être déchiffrée qu’à l’aide des clés client ou de la clé Availability. La clé DEP est ensuite utilisée pour chiffrer les clés de boîte aux lettres, qui chiffrent les boîtes aux lettres individuelles.
  
Office 365 suit ce processus pour déchiffrer et fournir des données lorsque les clients utilisent le service :
  
1. Déchiffrez la clé DEP à l’aide de la clé client.

2. Utilisez la clé DEP déchiffrée pour déchiffrer une clé de boîte aux lettres.

3. Utilisez la clé de boîte aux lettres déchiffrée pour déchiffrer la boîte aux lettres elle-même, ce qui vous permet d’accéder aux données de la boîte aux lettres.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Comment les fichiers SharePoint Online, OneDrive entreprise et teams utilisent la clé de disponibilité

L’architecture et l’implémentation de SharePoint Online et OneDrive entreprise et de la clé de disponibilité client diffèrent d’Exchange Online et de Skype entreprise.
  
Lorsqu’une organisation passe à des clés gérées par le client, Office 365 crée une clé intermédiaire propre au client (TIK). Office 365 chiffre le TIK deux fois, une fois avec chacune des clés de client, et stocke les deux versions chiffrées du TIK. Seules les versions chiffrées de TIK sont stockées, et un TIK peut uniquement être déchiffré avec les clés client. Le TIK est ensuite utilisé pour chiffrer les clés de site, qui sont ensuite utilisées pour chiffrer les clés BLOB (également appelées clés de bloc de fichiers). En fonction de la taille du fichier, le service peut fractionner un fichier en plusieurs segments de fichiers chacun avec une clé unique. Les objets BLOB (blocs de fichiers) eux-mêmes sont chiffrés avec les clés BLOB et stockés dans le service de stockage BLOB Microsoft Azure.
  
Office 365 suit ce processus pour déchiffrer et fournir des fichiers clients lorsque les clients utilisent le service :

1. Déchiffrer le TIK à l’aide de la clé client.

2. Utilisez la TIK déchiffrée pour déchiffrer une clé de site.

3. Utilisez la clé de site déchiffrée pour déchiffrer une clé BLOB.

4. Utilisez la clé BLOB déchiffrée pour déchiffrer le BLOB.

Office 365 déchiffre une TIK en émettant deux demandes de déchiffrement vers Azure Key Vault avec un décalage léger. Le premier à terminer fournit le résultat, annulant l’autre requête.
  
Si vous perdez l’accès à vos clés client, Office 365 chiffre également le TIK avec une clé de disponibilité et le stocke avec le TIKs chiffré avec chaque clé client. La TIK chiffrée avec la clé de disponibilité est utilisée uniquement lorsque le client appelle Microsoft pour inscrire le chemin de récupération lorsqu’il perd l’accès à ses clés, de manière malveillante ou accidentelle.
  
Pour des raisons de disponibilité et d’envergure, les TIKs déchiffrées sont mises en cache dans un cache de mémoire à limite de temps. Deux heures avant la date d’expiration d’un cache TIK, Office 365 tente de déchiffrer chaque TIK. Le déchiffrement du TIKs prolonge la durée de vie du cache. Si le déchiffrement d’TIK échoue pendant une durée considérable, Office 365 génère une alerte pour notifier l’ingénierie avant l’expiration du cache. Uniquement si le client appelle Microsoft Office 365 lancer l’opération de récupération, ce qui implique le déchiffrement de l’TIK avec la clé de disponibilité stockée dans le magasin secret de Microsoft et l’intégration de nouveau au client à l’aide de l’TIK déchiffrée et d’un nouveau jeu de clés Azure Key Vault fournies par le client.
  
À l’heure actuelle, la clé client est impliquée dans la chaîne de chiffrement et de déchiffrement des données de fichier SharePoint Online stockées dans le magasin d’objets BLOB Azure, mais pas dans les éléments de liste SharePoint Online ou les métadonnées stockées dans la base de données SQL. Office 365 n’utilise pas la clé de disponibilité pour Exchange Online, Skype entreprise, SharePoint Online, OneDrive entreprise et teams autres que le cas décrit ci-dessus, qui est initié par le client. L’accès humain aux données client est protégé par le référentiel sécurisé du client.

## <a name="availability-key-triggers"></a>Déclencheurs de clés de disponibilité

Office 365 déclenche la clé de disponibilité uniquement dans des circonstances spécifiques. Ces circonstances diffèrent par service.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Déclencheurs pour Exchange Online et Skype entreprise
  
1. Office 365 lit la DEP à laquelle la boîte aux lettres est affectée afin de déterminer l’emplacement des deux clés de client dans le coffre-fort de clés Azure.

2. Office 365 choisit de manière aléatoire l’une des deux clés de client de la DEP et envoie une demande au coffre-fort de clés Azure pour désencapsuler la clé DEP à l’aide de la clé client.

3. Si la demande d’empaquetage de la clé DEP à l’aide de la clé client échoue, Office 365 envoie une deuxième demande à la chambre forte des clés Azure, ce qui lui demande d’utiliser la deuxième clé (second) client.

4. Si la deuxième demande d’empaquetage de la clé DEP à l’aide de la clé client échoue, Office 365 examine les résultats des deux requêtes.

    - Si l’examen détermine que les requêtes ont échoué en renvoyant une erreur système :

       - Office 365 déclenche la clé de disponibilité pour déchiffrer la clé DEP.

       - Office 365 utilise ensuite la clé DEP pour déchiffrer la clé de boîte aux lettres et terminer la demande de l’utilisateur. 

       - Dans ce cas, le coffre-fort de clés Azure ne peut pas répondre ou être inaccessible en raison d’une erreur passagère.

    - Si l’examen détermine que les demandes ayant échoué à retourner l’accès a été REFUSée :

       - Cela signifie qu’une action délibérée, involontaire ou malveillante a été effectuée pour rendre les clés du client indisponibles (par exemple, lors du processus de purge des données dans le cadre de la cessation du service).

       - Dans ce cas, la clé de disponibilité est utilisée uniquement pour les actions système et non pour les actions de l’utilisateur, la demande de l’utilisateur échoue et l’utilisateur reçoit un message d’erreur.

>[!IMPORTANT]
>Le code de service Office 365 dispose toujours d’un jeton de connexion valide pour les motifs sur les données client afin de fournir des services Cloud de valeur ajoutée. Par conséquent, tant que la clé de disponibilité n’a pas été supprimée, elle peut être utilisée comme secours pour les actions lancées par Exchange Online et Skype entreprise telles que la création d’index de recherche ou le transfert de boîtes aux lettres. Cela s’applique à la fois aux erreurs passagères et aux demandes d’accès refusé au coffre-fort de clés Azure.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Déclencheurs pour les fichiers SharePoint Online, OneDrive entreprise et Teams

Pour les fichiers SharePoint Online, OneDrive entreprise et Teams, la clé de disponibilité n’est jamais utilisée en dehors de la capacité de récupération et les clients doivent explicitement demander à Microsoft d’utiliser la clé de disponibilité pendant un scénario de récupération.

## <a name="audit-logs-and-the-availability-key"></a>Journaux d’audit et clé de disponibilité

Les systèmes automatisés dans Office 365 traitent toutes les données à mesure qu’elles circulent dans le système pour fournir des services Cloud, par exemple, l’antivirus, la découverte électronique, la protection contre la perte de données et l’indexation des données. Office 365 ne génère pas de journaux visibles par le client pour cette activité. En outre, le personnel de Microsoft n’accède pas à vos données dans le cadre de ces opérations système normales.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>Journalisation de la clé de disponibilité de Skype entreprise et Exchange Online

Lorsque la clé de disponibilité Exchange Online et Skype entreprise Access permet de fournir des services, Office 365 publie des journaux visibles par le client accessibles depuis le centre de sécurité et de conformité. Un enregistrement de journal d’audit pour l’opération de clé de disponibilité est généré chaque fois que le service utilise la clé de disponibilité. Un nouveau type d’enregistrement appelé « chiffrement du service de clés du client » avec le type d’activité « secours de la clé de disponibilité » permet aux administrateurs de filtrer les résultats de recherche du [Journal d’audit unifié](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance) pour afficher les enregistrements de clés de disponibilité.

Les enregistrements de journal incluent des attributs tels que la date, l’heure, l’activité, l’ID de l’organisation et l’ID de stratégie de chiffrement des données. L’enregistrement est disponible dans le cadre des journaux d’audit unifiés Office 365 et est accessible à partir de l’onglet de recherche du journal d’audit du centre de sécurité et de conformité Office 365.

![Recherche des événements clés de disponibilité dans le journal d’audit](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Les enregistrements de clés de disponibilité Exchange Online et Skype entreprise utilisent le [schéma commun](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) de l’activité de gestion Office 365 avec des paramètres personnalisés supplémentaires : ID de stratégie, ID de version de clé d’étendue et ID de demande.

![Paramètres personnalisés de clé de disponibilité](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>Journalisation des clés de disponibilité des fichiers SharePoint Online, OneDrive entreprise et des fichiers teams

La journalisation de la clé de disponibilité n’est pas encore disponible pour ces services. Pour les fichiers SharePoint Online, OneDrive entreprise et Teams, la clé de disponibilité n’est activée que par Microsoft, lorsque vous y êtes invité, à des fins de récupération. Par conséquent, vous connaissez déjà tous les événements dans lesquels la clé de disponibilité est utilisée pour ces services.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Clé de disponibilité dans la hiérarchie des clés de client
  
Office 365 utilise la clé de disponibilité pour encapsuler la couche de clés plus bas dans la hiérarchie de clés établie pour le chiffrement du service de clé client. Il existe différentes hiérarchies de clés entre les services. Les algorithmes de clé diffèrent également entre les clés de disponibilité et d’autres clés dans la hiérarchie de chaque service applicable. Les algorithmes de clé de disponibilité utilisés par les différents services sont les suivants :

- Les clés de disponibilité Exchange Online et Skype entreprise utilisent AES-256.

- Les clés de disponibilité des fichiers SharePoint Online, OneDrive entreprise et teams utilisent la RSA-2048.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour Exchange Online et Skype entreprise

![Chiffrements de chiffrement pour la clé client Exchange Online](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>Chiffrements de chiffrement utilisés pour chiffrer les clés pour SharePoint Online et OneDrive entreprise

![Chiffrements de chiffrement pour la clé client SharePoint Online](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Articles connexes

- [Chiffrement de service avec la clé client pour Office 365](customer-key-overview.md)

- [Configurer la clé client pour Office 365](customer-key-set-up.md)

- [Gérer la clé client pour Office 365](customer-key-manage.md)

- [Faire pivoter ou faire pivoter une clé client ou une clé de disponibilité](customer-key-availability-key-roll.md)
