---
title: "Consid&#233;rations sur la s&#233;curit&#233; (Entity Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Consid&#233;rations sur la s&#233;curit&#233; (Entity Framework)
Cette rubrique décrit les considérations sur la sécurité qui sont spécifiques au développement, au déploiement et à l'exécution d'applications [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Vous devez également suivre ces recommandations pour créer des applications [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sécurisées.  Pour plus d'informations, consultez [Vue d'ensemble de la sécurité](../../../../../docs/framework/data/adonet/security-overview.md).  
  
## Considérations générales sur la sécurité  
 Les considérations sur la sécurité suivantes s'appliquent à toutes les applications qui utilisent [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### Utilisez uniquement des fournisseurs de sources de données approuvés.  
 Pour communiquer avec la source de données, un fournisseur doit effectuer les opérations suivantes :  
  
-   recevoir la chaîne de connexion d'[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ;  
  
-   traduire l'arborescence de commandes en langage de requête natif de la source de données ;  
  
-   assembler et retourner des jeux de résultats.  
  
 Pendant l'opération d'ouverture de session, les informations qui sont basées sur le mot de passe de l'utilisateur sont passées au serveur via bibliothèques réseau de la source de données sous\-jacente.  Un fournisseur malveillant peut voler les informations d'identification de l'utilisateur, générer des requêtes malveillantes ou falsifier le jeu de résultats.  
  
#### Chiffrez votre connexion pour protéger les données sensibles.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne gère pas directement le chiffrement des données.  Si les utilisateurs accèdent aux données via un réseau public, votre application doit établir une connexion chiffrée à la source de données pour augmenter la sécurité.  Pour plus d'informations, voir la documentation relative à la sécurité pour votre source de données.  Pour une source de données SQL Server, consultez [Chiffrement des connexions à SQL Server](http://go.microsoft.com/fwlink/?LinkId=119544).  
  
#### Sécurisez la chaîne de connexion.  
 La protection de l'accès à votre source de données représente l'un de vos principaux objectifs lorsque vous sécurisez une application.  Une chaîne de connexion présente une vulnérabilité potentielle si elle n'est pas sécurisée ou si elle n'est pas correctement construite.  Lorsque vous stockez les informations de connexion au format texte brut ou que vous les conservez dans la mémoire, vous risquez de compromettre l'ensemble de votre système.  Les méthodes recommandées pour sécuriser des chaînes de connexion sont les suivantes :  
  
-   Utilisez l'authentification Windows avec une source de données SQL Server.  
  
     Lorsque vous utilisez l'authentification Windows pour vous connecter à une source de données SQL Server, la chaîne de connexion ne contient pas d'informations d'ouverture de session et de mot de passe.  
  
-   Chiffrez les sections du fichier de configuration à l'aide d'une configuration protégée.  
  
     ASP.NET fournit une nouvelle fonctionnalité, appelée « configuration protégée », qui vous permet de chiffrer les informations sensibles dans un fichier de configuration.  Bien qu'elle ait été conçue à l'origine pour ASP.NET, vous pouvez utiliser la configuration protégée pour chiffrer les sections des fichiers de configuration dans des applications Windows.  Pour obtenir une description détaillée des nouvelles fonctionnalités de configuration protégée, voir [Encrypting Configuration Information Using Protected Configuration](../Topic/Encrypting%20Configuration%20Information%20Using%20Protected%20Configuration.md).  
  
-   Stockez les chaînes de connexion dans des fichiers de configuration sécurisés.  
  
     Vous ne devez jamais incorporer des chaînes de connexion dans votre code source.  Vous pouvez stocker des chaînes de connexion dans des fichiers de configuration, ce qui évite d'avoir à les incorporer dans le code de votre application.  Par défaut, l'Assistant EDM stocke les chaînes de connexion dans le fichier de configuration de l'application.  Vous devez sécuriser ce fichier pour empêcher l'accès non autorisé.  
  
-   Utilisez des générateurs de chaînes de connexion lors de la création dynamique de connexions.  
  
     Si vous devez construire des chaînes de connexion au moment de l'exécution, utilisez la classe <xref:System.Data.EntityClient.EntityConnectionStringBuilder>.  Cette classe du générateur de chaînes permet d'empêcher les attaques par injection de chaîne de connexion en validant et en plaçant dans une séquence d'échappement les informations d'entrée non valides.  Pour plus d'informations, consultez [Procédure : générer une chaîne de connexion pour EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  Utilisez également la classe du générateur de chaînes appropriée pour élaborer la chaîne de connexion à la source de données qui fait partie de la chaîne de connexion [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations sur les générateurs de chaînes de connexion pour les fournisseurs ADO.NET, consultez [Générateurs de chaînes de connexion](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Pour plus d'informations, consultez [Protection des informations de connexion](../../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
#### N'exposez pas un EntityConnection à des utilisateurs non approuvés.  
 Un objet <xref:System.Data.EntityClient.EntityConnection> expose la chaîne de connexion de la connexion sous\-jacente.  Un utilisateur ayant accès à un objet <xref:System.Data.EntityClient.EntityConnection> peut également modifier l'objet <xref:System.Data.ConnectionState> de la connexion sous\-jacente.  La classe <xref:System.Data.EntityClient.EntityConnection> n'est pas thread\-safe.  
  
#### Ne passez pas de connexions à l'extérieur du contexte de sécurité.  
 Après avoir établi une connexion, vous ne devez pas la passer à l'extérieur du contexte de sécurité.  Par exemple, un thread bénéficiant de l'autorisation nécessaire pour ouvrir une connexion ne doit pas stocker la connexion dans un emplacement global.  Si la connexion est disponible dans un emplacement global, un autre thread malveillant peut utiliser la connexion ouverte sans que cette autorisation lui soit explicitement accordée.  
  
#### Gardez à l'esprit que les informations de connexion et les mots de passe peuvent être visibles dans un vidage de la mémoire.  
 Lorsque les informations d'ouverture de session et de mot de passe de la source de données sont fournies dans la chaîne de connexion, ces informations sont conservées en mémoire jusqu'à ce que le garbage collection récupère les ressources.  Il est par conséquent impossible de déterminer quand une chaîne de mot de passe n'est plus en mémoire.  Si une application se bloque, un fichier de vidage de la mémoire peut contenir des informations sensibles sur la sécurité, et l'utilisateur qui exécute l'application ainsi que tout utilisateur disposant d'un accès en tant qu'administrateur à l'ordinateur peuvent consulter le fichier de vidage de la mémoire.  Utilisez l'authentification Windows pour les connexions à Microsoft SQL Server.  
  
#### Accordez aux utilisateurs uniquement les autorisations nécessaires dans la source de données.  
 Un administrateur de source de données doit accorder uniquement les autorisations nécessaires aux utilisateurs.  Même si [!INCLUDE[esql](../../../../../includes/esql-md.md)] ne prend pas en charge les instructions DML qui modifient les données, telles qu'INSERT, UPDATE ou DELETE, les utilisateurs peuvent néanmoins accéder à la connexion à la source de données.  Un utilisateur malveillant pourrait utiliser cette connexion pour exécuter des instructions DML dans le langage natif de la source de données.  
  
#### Exécutez les applications avec les autorisations minimales.  
 Lorsque vous permettez à une application managée de s'exécuter avec une autorisation de confiance totale, le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] ne limite pas l'accès de l'application à votre ordinateur.  De ce fait, une faille de sécurité dans votre application risque de compromettre l'ensemble de votre système.  Pour utiliser la sécurité d'accès du code et d'autres mécanismes de sécurité dans le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], vous devez exécuter les applications en utilisant des autorisations de confiance partielle et avec l'ensemble minimal des autorisations qui sont requises pour permettre à l'application de fonctionner.  Les autorisations d'accès au code suivantes sont les autorisations minimales requises par votre application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] :  
  
-   <xref:System.Security.Permissions.FileIOPermission> : <xref:System.Security.Permissions.FileIOPermissionAccess> pour ouvrir les fichiers de métadonnées spécifiés ou <xref:System.Security.Permissions.FileIOPermissionAccess> pour rechercher des fichiers de métadonnées dans un répertoire.  
  
-   <xref:System.Security.Permissions.ReflectionPermission> : <xref:System.Security.Permissions.ReflectionPermissionFlag> pour prendre en charge des requêtes LINQ to Entities.  
  
-   <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState> pour s'inscrire dans un objet <xref:System.Transactions> <xref:System.Transactions.Transaction>.  
  
-   <xref:System.Security.Permissions.SecurityPermission> : <xref:System.Security.Permissions.SecurityPermissionFlag> pour sérialiser des exceptions à l'aide de l'interface <xref:System.Runtime.Serialization.ISerializable>.  
  
-   Autorisation d'ouvrir une connexion de base de données et d'exécuter des commandes sur la base de données, telle que <xref:System.Data.SqlClient.SqlClientPermission> pour une base de données [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 Pour plus d'informations, consultez [Sécurité d'accès du code et ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
#### N'installez pas d'applications non approuvées.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] n'applique aucune autorisation de sécurité et appelle tout le code d'objet de données fourni par l'utilisateur en cours de traitement, qu'il soit approuvé ou non.  Assurez\-vous que l'authentification et l'autorisation du client sont effectuées par la banque de données et par votre application.  
  
#### Limitez l'accès à tous les fichiers de configuration.  
 Un administrateur doit limiter l'accès en écriture à tous les fichiers qui spécifient la configuration d'une application, y compris à enterprisesec.config, à security.config, à machine.conf et au fichier de configuration de l'application \<*application*\>.exe.config.  
  
 Le nom invariant du fournisseur est modifiable dans le fichier app.config.  L'application cliente doit prendre la responsabilité de l'accès au fournisseur sous\-jacent via le modèle Factory du fournisseur standard en utilisant un nom fort.  
  
#### Limitez les autorisations aux fichiers de modèle et de mappage.  
 Un administrateur doit limiter l'accès en écriture aux fichiers de modèle et de mappage \(.edmx, .csdl, .ssdl et .msl\) uniquement aux utilisateurs qui modifient le modèle ou les mappages.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requiert uniquement l'accès en lecture à ces fichiers au moment de l'exécution.  Un administrateur doit également limiter l'accès aux fichiers de couche objet et aux fichiers de code source de vue précompilés qui sont générés par les outils [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)].  
  
## Considérations sur la sécurité pour les requêtes  
 Vous devez tenir compte des considérations sur la sécurité suivantes lors de l'interrogation d'un modèle conceptuel.  Ces considérations s'appliquent aux requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] utilisant EntityClient et aux requêtes d'objet utilisant LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)] et les méthodes du Générateur de requêtes.  
  
#### Empêchez les attaques par injection de code SQL.  
 Les applications reçoivent fréquemment des entrées externes \(provenant d'un utilisateur ou d'un autre agent externe\) et exécutent des actions en fonction de ces entrées.  Toute entrée qui provient directement ou indirectement d'un utilisateur ou d'un agent externe doit avoir un contenu qui utilise la syntaxe du langage cible afin d'exécuter des actions non autorisées.  Lorsque le langage cible est un langage SQL, tel que [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], cette manipulation est appelée « attaque par injection de code SQL ».  Un utilisateur malveillant peut injecter des commandes directement dans la requête et effacer une table de base de données, provoquer un déni de service ou modifier d'une manière ou d'une autre la nature de l'opération en cours.  
  
-   Attaques par injection [!INCLUDE[esql](../../../../../includes/esql-md.md)] :  
  
     Les attaques par injection de code SQL peuvent être effectuées dans [!INCLUDE[esql](../../../../../includes/esql-md.md)] en fournissant une entrée malveillante à des valeurs qui sont utilisées dans un prédicat de requête et dans les noms de paramètres.  Pour éviter le risque d'injection de code SQL, vous ne devez jamais associer une entrée d'utilisateur à un texte de commande [!INCLUDE[esql](../../../../../includes/esql-md.md)].  
  
     Les requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] acceptent des paramètres partout où des littéraux sont admis.  Vous devez utiliser des requêtes paramétrables au lieu d'injecter des littéraux directement dans la requête à partir d'un agent externe. Vous devez également envisager d'utiliser les méthodes du Générateur de requêtes pour construire sans risque [Entity SQL](http://msdn.microsoft.com/fr-fr/05685434-05e6-41c2-8d5e-8933b88a40b0).  
  
-   Attaques par injection [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] :  
  
     Bien qu'il soit possible de composer des requêtes dans [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)], cette opération est effectuée via l'API de modèle objet. Contrairement aux requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)], les requêtes [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] ne sont pas composées par manipulation de chaîne ou concaténation et ne sont pas sujettes à des attaques par injection de code SQL au sens classique du terme.  
  
#### Évitez les jeux de résultats très volumineux.  
 Un jeu de résultats très volumineux pourrait entraîner l'arrêt du système client si le client effectue des opérations qui consomment des ressources proportionnelles à la taille du jeu de résultats.  Les jeux de résultats volumineux inattendus peuvent se produire dans les conditions suivantes :  
  
-   dans les requêtes qui n'incluent pas de conditions de filtre appropriées sur une base de données volumineuse ;  
  
-   dans les requêtes qui créent des jointures cartésiennes sur le serveur ;  
  
-   dans les requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] imbriquées.  
  
 Lorsque vous acceptez une entrée d'utilisateur, vous devez vous assurer que l'entrée ne peut pas générer des jeux de résultats plus volumineux que ce que le système peut gérer.  Vous pouvez également utiliser la méthode <xref:System.Linq.Queryable.Take%2A> dans [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)] ou l'opérateur [LIMIT](../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dans [!INCLUDE[esql](../../../../../includes/esql-md.md)] pour limiter la taille du jeu de résultats.  
  
#### Évitez de retourner les résultats IQueryable lors de l'exposition de méthodes à des appelants potentiellement non fiables.  
 Évitez de retourner des types <xref:System.Linq.IQueryable%601> des méthodes exposées aux appelants potentiellement non fiables pour les raisons suivantes :  
  
-   Le consommateur d'une requête qui expose un type <xref:System.Linq.IQueryable%601> pourrait appeler des méthodes qui exposent des données sécurisées ou augmentent la taille du jeu de résultats.  Par exemple, considérez la signature de méthode suivante :  
  
    ```  
    public IQueryable<Customer> GetCustomer(int customerId)  
    ```  
  
     Un consommateur de cette requête pourrait appeler `.Include("Orders")` sur le `IQueryable<Customer>` retourné pour récupérer des données que la requête ne projette pas d'exposer.  Cela peut être évité en modifiant le type de retour de la méthode en <xref:System.Collections.Generic.IEnumerable%601> et en appelant une méthode \(telle que `.ToList()`\) qui matérialise les résultats.  
  
-   Parce que les requêtes <xref:System.Linq.IQueryable%601> sont exécutées lorsque les résultats sont itérés, le consommateur d'une requête qui expose un type <xref:System.Linq.IQueryable%601> pourrait intercepter des exceptions levées.  Les exceptions pourraient contenir des informations non prévues pour le consommateur.  
  
## Considérations sur la sécurité pour les entités  
 Les considérations sur la sécurité suivantes s'appliquent lors de la génération et l'utilisation de types d'entités.  
  
#### Ne partagez pas un ObjectContext entre des domaines d'application.  
 Le partage d'un objet <xref:System.Data.Objects.ObjectContext> avec plusieurs domaines d'application peut exposer des informations dans la chaîne de connexion.  Il est préférable de transférer les objets sérialisés ou les graphiques d'objets à l'autre domaine d'application, puis d'attacher ces objets à un objet <xref:System.Data.Objects.ObjectContext> dans ce domaine d'application.  Pour plus d'informations, consultez [Serializing Objects](http://msdn.microsoft.com/fr-fr/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
#### Évitez les violations de la cohérence des types.  
 Si la cohérence des types est violée, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne peut pas garantir l'intégrité des données dans les objets.  Les violations de la cohérence des types peuvent se produire si vous permettez à des applications non approuvées de s'exécuter avec une sécurité d'accès du code d'un niveau de confiance totale.  
  
#### Gestion des exceptions.  
 Accédez aux méthodes et aux propriétés d'un <xref:System.Data.Objects.ObjectContext> dans un bloc try\-catch.  L'interception d'exceptions empêche des exceptions non gérées d'exposer aux utilisateurs de votre application des entrées dans <xref:System.Data.Objects.ObjectStateManager> ou dans les informations de modèle \(telles que les noms de tables\).  
  
## Considérations sur la sécurité pour les applications ASP.NET  
 Lorsque vous utilisez des chemins d'accès dans des applications [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)], il est recommandé de tenir compte des points suivants.  
  
#### Vérifiez si votre hôte effectue des contrôles de chemin d'accès.  
 Lorsque la chaîne de la substitution `|DataDirectory|` \(placées entre barres verticales\) est utilisée, [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] vérifie que le chemin d'accès résolu est pris en charge.  Par exemple, « .. » n'est pas autorisé derrière `DataDirectory`.  Le même contrôle est effectué par le processus qui héberge [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] pour résoudre l'opérateur de racine de l'application Web \(`~`\).  IIS effectue ce contrôle ; toutefois, les hôtes autres qu'IIS ne peuvent pas vérifier que le chemin d'accès résolu est pris en charge.  Vous devez connaître le comportement de l'hôte sur lequel vous déployez une application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
#### Ne faites pas de suppositions sur les noms de chemins d'accès résolus.  
 Bien que les valeurs auxquelles l'opérateur racine \(`~`\) et la chaîne de la substitution `DataDirectory` correspondent doivent rester constantes pendant l'exécution de l'application, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] n'empêche pas l'hôte de modifier ces valeurs.  
  
#### Vérifiez la longueur du chemin d'accès avant le déploiement.  
 Avant de déployer une application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous devez vous assurer que les valeurs de l'opérateur racine \(~\) et de la chaîne de substitution `DataDirectory` ne dépassent pas les limites de longueur de chemin d'accès du système d'exploitation.  Les fournisseurs de données [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] ne garantissent pas que la longueur du chemin d'accès respecte les limites valides.  
  
## Considérations sur la sécurité pour les métadonnées ADO.NET  
 Les considérations sur la sécurité suivantes s'appliquent lors de la génération et de l'utilisation de fichiers de modèle et de mappage.  
  
#### N'exposez pas d'informations sensibles via la journalisation.  
 Les composants du service de métadonnées [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] n'enregistrent aucune information personnelle.  Si des résultats ne peuvent pas être retournés à cause de restrictions d'accès, les systèmes de gestion de base de données et les systèmes de fichiers doivent retourner zéro résultat au lieu de lever une exception qui pourrait contenir des informations sensibles.  
  
#### N'acceptez pas d'objets MetadataWorkspace provenant de sources non fiables.  
 Les applications ne doivent pas accepter les instances de la classe <xref:System.Data.Metadata.Edm.MetadataWorkspace> provenant de sources non fiables.  Il est préférable de construire et de remplir explicitement un espace de travail à partir d'une telle source.  
  
## Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [Points à prendre en considération pour le déploiement](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)   
 [Considérations sur la migration](../../../../../docs/framework/data/adonet/ef/migration-considerations.md)