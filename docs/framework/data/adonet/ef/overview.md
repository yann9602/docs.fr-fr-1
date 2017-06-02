---
title: "Vue d&#39;ensemble d&#39;Entity Framework | Microsoft Docs"
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
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Vue d&#39;ensemble d&#39;Entity Framework
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] est un ensemble de technologies dans ADO.NET qui prennent en charge le développement d'applications logicielles orientées données.  Les architectes et les développeurs d'applications orientées données sont confrontés à la nécessité d'atteindre deux objectifs très différents.  Ils doivent modeler les entités, les relations et la logique des problèmes liés à l'activité de l'entreprise qu'ils résolvent, et ils doivent également travailler avec les moteurs de données utilisés pour stocker et récupérer les données.  Les données peuvent être réparties entre plusieurs systèmes de stockage, chacun ayant ses propres protocoles ; même les applications qui fonctionnent avec un seul système de stockage doivent équilibrer les besoins du système de stockage par rapport aux besoins en matière d'écriture d'un code d'application efficace et facile à gérer.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permet aux développeurs de travailler avec des données sous la forme de propriétés et d'objets spécifiques aux domaines, tels que des clients et des adresses de clients, sans qu'il soit nécessaire de se préoccuper des tables et des colonnes de base de données sous\-jacentes dans lesquelles sont stockées ces données. Avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], les développeurs peuvent travailler à un niveau supérieur d'abstraction lorsqu'ils traitent les données, et peuvent créer et maintenir des applications orientées données avec moins de code que dans les applications traditionnelles.  Étant donné qu'[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] est un composant du [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], les applications [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] peuvent s'exécuter sur tout ordinateur sur lequel [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 SP1 \(ou une version ultérieure\) est installé.  
  
 Les sections suivantes de cette rubrique fournissent plus de détails sur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] :  
  
-   [Donner vie à des modèles](#LifeToModels)  
  
-   [Mappage d'objets à des données](#MappingObjectsToData)  
  
-   [Accessibilité et modification des données d'entité](#AccessingData)  
  
-   [Fournisseurs de données](#DataProviders)  
  
-   [Entity Data Model Tools](#Tools)  
  
-   [En savoir plus](#LearnMore)  
  
<a name="LifeToModels"></a>   
## Donner vie à des modèles  
 La division de l'application ou du service en trois parties \(modèle de domaine, modèle logique et modèle physique\) constitue une approche de conception commune et utilisé de longue date pour la construction d'une application ou d'un service.  Le modèle de domaine définit les entités et les relations dans le système qui est en cours de modélisation.  Le modèle logique d'une base de données relationnelle normalise les entités et les relations dans des tables avec des contraintes de clé étrangère.  Le modèle physique s'occupe des fonctionnalités d'un moteur de données particulier en spécifiant des détails de stockage tels que le partitionnement et l'indexation.  
  
 Le modèle physique est perfectionné par les administrateurs de bases de données pour améliorer les performances, mais les programmeurs qui écrivent du code d'application limitent principalement leur utilisation du modèle logique à l'écriture de requêtes SQL et à l'appel de procédures stockées.  Les modèles de domaine sont généralement utilisés comme un outil permettant de capturer et de communiquer les besoins d'une application, fréquemment sous la forme de diagrammes inertes qui sont consultés et passés en revue dans les phases préliminaires d'un projet, puis abandonnés.  De nombreuses équipes de développement ne créent pas de modèle conceptuel et commencent en spécifiant des tables, des colonnes et des clés dans une base de données relationnelle.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] donne vie aux modèles conceptuels en permettant aux développeurs d'interroger des entités et des relations dans le modèle de domaine \(appelé modèle *conceptuel* dans [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]\) tout en s'appuyant sur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour traduire ces opérations en commandes spécifiques à la source de données.  Cela libère les applications des dépendances codées en dur sur une source de données particulière.  
  
 Lorsque vous utilisez Code First, le modèle conceptuel est mappé au modèle de stockage dans le code.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] peut déduire le modèle conceptuel basé sur les types d'objets et les configurations supplémentaires que vous définissez.  Les métadonnées de mappage sont générées au moment de l'exécution selon une combinaison de la manière dont vous avez défini vos types de domaine et données de configuration supplémentaires que vous fournissez dans le code.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] génère la base de données nécessaire en fonction des métadonnées.  Pour plus d'informations, consultez [Création et mappage d'un modèle conceptuel](http://go.microsoft.com/fwlink/?LinkID=235382).  
  
 Lorsque vous utilisez Entity Data Model Tools, le modèle conceptuel, le modèle de stockage et les mappages entre les deux sont exprimés dans les schémas basés sur XML et sont définis dans les fichiers qui ont les extensions de nom correspondantes :  
  
-   Le langage CSDL \(Conceptual Schema Definition Language\) définit le modèle conceptuel.  Le langage CSDL correspond à l'implémentation [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] du modèle [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  L'extension de fichier est .csdl.  
  
-   Le langage SSDL \(Store Schema Definition Language\) définit le modèle de stockage, également appelé « modèle logique ».  L'extension de fichier est .ssdl.  
  
-   Le langage MSL \(Mapping Specification Language\) définit les mappages entre le modèle de stockage et le modèle conceptuel.  L'extension de fichier est .msl.  
  
 Le modèle de stockage et les mappages peuvent être modifiés le cas échéant, sans besoin de modifier le modèle conceptuel, les classes de données ou le code d'application.  Étant donné que les modèles de stockage sont spécifiques au fournisseur, vous pouvez travailler avec un modèle conceptuel cohérent entre différentes sources de données.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise ces fichiers de modèle et de mappage pour transformer des opérations de création, de lecture, de mise à jour et de suppression sur des entités et des relations dans le modèle conceptuel en opérations équivalentes dans la source de données.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] prend même en charge le mappage d'entités du modèle conceptuel à des procédures stockées de la source de données.  Pour plus d'informations, consultez [Spécifications CSDL, SSDL et MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).  
  
<a name="MappingObjectsToData"></a>   
## Mappage d'objets à des données  
 La programmation orientée objet présente une difficulté pour l'interaction avec les systèmes de stockage des données.  Bien que l'organisation des classes reflète souvent l'organisation des tables de bases de données relationnelles, l'adéquation n'est pas parfaite.  Plusieurs tables normalisées correspondent fréquemment à une seule classe, et les relations entre les classes sont souvent représentées différemment des relations entre les tables.  Par exemple, pour représenter le client d'une commande, une classe `Order` peut utiliser une propriété qui contient une référence à une instance d'une classe `Customer`, tandis qu'une ligne de la table `Order` d'une base de données contient une colonne \(ou un ensemble de colonnes\) de clé étrangère avec une valeur qui correspond à une valeur de clé primaire dans la table `Customer`.  Une classe `Customer` peut avoir une propriété nommée `Orders` qui contient une collection d'instances de la classe `Order` alors que la table `Customer` d'une base de données n'a aucune colonne comparable.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] donne aux développeurs la flexibilité de représenter les relations de cette façon, ou de modeler de façon plus précise les relations lorsqu'elles sont représentées dans la base de données.  
  
 Les solutions existantes ont essayé de rétablir la continuité de ce qu'on appelle fréquemment « défaut d'adaptation d'impédance », en mappant uniquement des classes et des propriétés orientées objet à des colonnes et à des tables relationnelles.  Au lieu d'adopter cette approche traditionnelle, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mappe des tables relationnelles, des colonnes et des contraintes de clé étrangère dans des modèles logiques à des entités et des relations dans des modèles conceptuels.  Cela permet une plus grande souplesse dans la définition des objets et l'optimisation du modèle logique.  Les outils [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] génèrent des classes de données extensibles en fonction du modèle conceptuel.  Ces classes sont des classes partielles qui peuvent être étendues avec des membres supplémentaires que le développeur ajoute.  Par défaut, les classes générées pour un modèle conceptuel particulier dérivent de classes de base qui fournissent des services de matérialisation d'entités sous forme d'objets, ainsi que de suivi et d'enregistrement des modifications.  Les développeurs peuvent utiliser ces classes pour travailler avec les entités et les relations sous forme d'objets liés par des associations.  Les développeurs peuvent également personnaliser les classes générées pour un modèle conceptuel. Pour plus d'informations, consultez [Utilisation d'objets](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
<a name="AccessingData"></a>   
## Accessibilité et modification des données d'entité  
 Plus qu'une simple solution de mappage relationnel objet supplémentaire, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permet fondamentalement à des applications d'accéder à des données qui sont représentées sous la forme d'entités et de relations dans le modèle conceptuel, et de les modifier. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise les informations contenues dans le modèle et les fichiers de mappage pour traduire des requêtes d'objet sur des types d'entités qui sont représentés en requêtes spécifiques à la source de données dans le modèle conceptuel.  Les résultats des requêtes sont matérialisés en objets gérés par [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] offre les méthodes suivantes pour interroger un modèle conceptuel et retourner des objets :  
  
-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Fournit la prise en charge de LINQ \(Language Integrated Query\) pour interroger des types d'entités définis dans un modèle conceptuel.  Pour plus d'informations, consultez [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialecte SQL indépendant du stockage qui fonctionne directement avec les entités dans le modèle conceptuel et qui prend en charge les concepts [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)].  [!INCLUDE[esql](../../../../../includes/esql-md.md)] est utilisé à la fois avec les requêtes d'objet et les requêtes exécutées à l'aide du fournisseur EntityClient.  Pour plus d'informations, consultez [Vue d'ensemble d'Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut le fournisseur de données EntityClient.  Ce fournisseur gère les connexions, traduit des requêtes d'entité dans les requêtes spécifiques à la source de données et retourne un lecteur de données que [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise pour matérialiser les données d'entité dans des objets.  Lorsque la matérialisation d'objets n'est pas requise, le fournisseur EntityClient peut également être utilisé comme un fournisseur de données [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] standard en permettant aux applications d'exécuter des requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] et d'utiliser le lecteur de données en lecture seule retournées.  Pour plus d'informations, consultez [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Le diagramme suivant illustre l'architecture [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour l'accès aux données :  
  
 ![Diagramme d'architecture Entity Framework](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd\_EFArchDiagram")  
  
 Les outils [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] peuvent générer une classe dérivée de `System.Data.Objects.ObjectContext` ou `System.Data.Entity.DbContext` qui représente le conteneur d'entités défini dans le modèle conceptuel.  Ce contexte de l'objet fournit les fonctionnalités permettant de suivre les modifications, et de gérer les identités, l'accès concurrentiel et les relations.  Cette classe expose également une méthode `SaveChanges` qui écrit les insertions, les mises à jour et des suppressions dans la source de données.  Comme les requêtes, ces modifications sont apportées soit par des commandes générées automatiquement par le système, soit par des procédures stockées qui sont spécifiées par le développeur.  
  
<a name="DataProviders"></a>   
## Fournisseurs de données  
 Le fournisseur `EntityClient` étend le modèle de fournisseur [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] en accédant aux données en termes d'entités conceptuelles et de relations.  Il exécute des requêtes qui utilisent [!INCLUDE[esql](../../../../../includes/esql-md.md)].  [!INCLUDE[esql](../../../../../includes/esql-md.md)] fournit le langage de requête sous\-jacent qui permet à `EntityClient` de communiquer avec la base de données.  Pour plus d'informations, consultez [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut un fournisseur de données SqlClient mis à jour qui prend en charge les arborescences de commandes canoniques.  Pour plus d'informations, consultez [SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).  
  
<a name="Tools"></a>   
## Entity Data Model Tools  
 En association avec le runtime [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] inclut les outils de mappage et de modélisation.  Pour plus d'informations, consultez [Modélisation et mappage](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).  
  
<a name="LearnMore"></a>   
## En savoir plus  
 Les rubriques suivantes vous permettent den savoir plus sur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] :  
  
 [Mise en route](../../../../../docs/framework/data/adonet/ef/getting-started.md)  
 Fournit des informations sur la façon d'être rapidement à même d'utiliser le [Quickstart](http://msdn.microsoft.com/fr-fr/0bc534be-789f-4819-b9f6-76e51d961675), lequel montre comment créer une application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] simple.  
  
 [Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)  
 Définit un grand nombre des termes introduits par Entity Data Model et [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et qui sont utilisés dans la documentation [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
 [Ressources Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md)  
 Fournit des liens vers des rubriques conceptuelles et des liens vers des rubriques et des ressources externes permettant de générer des applications [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
## Voir aussi  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)