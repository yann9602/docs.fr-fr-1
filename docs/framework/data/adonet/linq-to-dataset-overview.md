---
title: "Vue d&#39;ensemble de LINQ to DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Vue d&#39;ensemble de LINQ to DataSet
Le <xref:System.Data.DataSet> est l'un des composants de [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] les plus largement utilisés. C'est un élément clé du modèle de programmation déconnecté sur lequel [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] est basé. Il vous permet de mettre en cache explicitement les données de sources différentes.  Pour la couche Présentation, le <xref:System.Data.DataSet> est étroitement intégré aux contrôles d'interface utilisateur graphique pour la liaison de données. Pour la couche intermédiaire, il fournit un cache qui préserve la forme relationnelle de données et inclut des services simples et rapides de requête et de navigation dans la hiérarchie.  Une technique courante pour réduire le nombre de demandes sur une base de données consiste à utiliser le <xref:System.Data.DataSet> pour la mise en cache dans la couche intermédiaire.  Prenons l'exemple d'une application Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pilotée par les données.  En général, une partie significative des données d'application ne change pas fréquemment et est commune à plusieurs sessions ou utilisateurs.  Ces données peuvent être conservées en mémoire sur le serveur Web, ce qui réduit le nombre de demandes adressées à la base de données et accélère les interactions de l'utilisateur.  Un autre aspect utile du <xref:System.Data.DataSet> est qu'il permet aux applications de placer des sous\-ensembles de données d'une ou plusieurs sources de données dans l'espace d'application.  L'application peut alors manipuler les données en mémoire, tout en conservant sa forme relationnelle.  
  
 Cependant, en dépit de son importance, le <xref:System.Data.DataSet> a des capacités de requête limitées.  La méthode <xref:System.Data.DataTable.Select%2A> peut être utilisée pour le filtrage et le tri, et les méthodes <xref:System.Data.DataRow.GetChildRows%2A> et <xref:System.Data.DataRow.GetParentRow%2A> pour la navigation dans la hiérarchie.  Pour toute opération plus complexe, cependant, le développeur doit écrire une requête personnalisée.  Cela peut entraîner un dysfonctionnement des applications et les rendre difficiles à gérer.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] facilite et accélère l'interrogation de données mises en cache dans un objet <xref:System.Data.DataSet>.  Ces requêtes sont exprimées dans le langage de programmation même, plutôt qu'en tant que littéraux de chaîne incorporés dans le code de l'application.  Ainsi, les développeurs n'ont pas à apprendre de langage de requête spécifique.  De plus, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] permet aux développeurs [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] de travailler de manière plus productive, parce que l'IDE [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] fournit la vérification de la syntaxe au moment de la compilation, les types statiques et la prise en charge IntelliSense pour [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] peut également être utilisé pour interroger des données qui ont été consolidées à partir d'une ou plusieurs sources de données.  Cela permet de réaliser plusieurs scénarios qui requièrent de la flexibilité dans la façon dont les données sont représentées et gérées.  En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.  
  
## Interrogation de DataSets à l'aide de LINQ to DataSet  
 Avant de procéder à l'interrogation d'un objet <xref:System.Data.DataSet> à l'aide de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], vous devez remplir le <xref:System.Data.DataSet>. Il existe plusieurs manières de charger des données dans un <xref:System.Data.DataSet>, comme l'utilisation de la classe <xref:System.Data.Common.DataAdapter> ou de [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  Une fois les données chargées dans un objet <xref:System.Data.DataSet>, vous pouvez y exécuter des requêtes.  La formulation de requêtes à l'aide de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] est similaire à l'utilisation de [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] sur d'autres sources de données compatibles[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].  Il est possible d'exécuter des requêtes [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sur des tables uniques d'un <xref:System.Data.DataSet> ou sur plusieurs tables à l'aide des opérateurs de requête standard <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>.  
  
 Les requêtes [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sont prises en charge sur des objets <xref:System.Data.DataSet> typés et non typés.  Si le schéma du <xref:System.Data.DataSet> est connu au moment du design de l'application, nous vous recommandons d'utiliser un <xref:System.Data.DataSet> typé. Dans un <xref:System.Data.DataSet> typé, les tables et les lignes ont des membres typés pour chaque colonne, ce qui rend les requêtes plus simples et plus lisibles.  
  
 Outre les opérateurs de requête standard implémentés dans System.Core.dll, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ajoute plusieurs extensions spécifiques au <xref:System.Data.DataSet> pour faciliter l'exécution des requêtes sur un ensemble d'objets <xref:System.Data.DataRow>.  Ces extensions spécifiques à <xref:System.Data.DataSet> incluent des opérateurs pour comparer des séquences de lignes, ainsi que des méthodes qui fournissent l'accès aux valeurs de colonne d'un <xref:System.Data.DataRow>.  
  
## Applications multicouches et LINQ to DataSet  
 Les applications de données multicouches sont des applications centrées sur les données qui sont étagées en plusieurs couches logiques.  Une application multicouche classique inclut une couche Présentation, une couche intermédiaire et une couche Données.  La séparation des composants d'application en couches distinctes renforce la facilité de maintenance et l'évolutivité de l'application.  Pour plus d'informations sur les applications de données multicouches, consultez [Utilisation de groupes de données dans des applications multicouches](../Topic/Work%20with%20datasets%20in%20n-tier%20applications.md).  
  
 Dans les applications multicouches, le <xref:System.Data.DataSet> est souvent utilisé dans la couche intermédiaire pour mettre en cache les informations pour une application Web.  Les fonctionnalités d'interrogation de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sont implémentées par des méthodes d'extension et étendent le <xref:System.Data.DataSet> ADO.NET 2.0 existant.  
  
## Voir aussi  
 [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [LINQ à SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)