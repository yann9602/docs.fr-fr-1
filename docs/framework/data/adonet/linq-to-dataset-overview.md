---
title: Vue d'ensemble de LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0295ff475367b0867ff0a5b0dd85f7a686e343bc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-dataset-overview"></a>Vue d'ensemble de LINQ to DataSet
Le <xref:System.Data.DataSet> est l'un des composants de [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] les plus largement utilisés. C'est un élément clé du modèle de programmation déconnecté sur lequel [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] est basé. Il vous permet de mettre en cache explicitement les données de sources différentes.  Pour la couche Présentation, le <xref:System.Data.DataSet> est étroitement intégré aux contrôles d'interface utilisateur graphique pour la liaison de données. Pour la couche intermédiaire, il fournit un cache qui préserve la forme relationnelle de données et inclut des services simples et rapides de requête et de navigation dans la hiérarchie. Une technique courante pour réduire le nombre de demandes sur une base de données consiste à utiliser le <xref:System.Data.DataSet> pour la mise en cache dans la couche intermédiaire. Par exemple, considérez un pilotage par des données [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application Web. En général, une partie significative des données d'application ne change pas fréquemment et est commune à plusieurs sessions ou utilisateurs. Ces données peuvent être conservées en mémoire sur le serveur web, ce qui réduit le nombre de demandes adressées à la base de données et accélère les interactions de l’utilisateur. Un autre aspect utile de le <xref:System.Data.DataSet> est qu’il permet à une application afficher des sous-ensembles de données à partir d’une ou plusieurs sources de données dans l’application. L'application peut alors manipuler les données en mémoire, tout en conservant sa forme relationnelle.  
  
 Cependant, en dépit de son importance, le <xref:System.Data.DataSet> a des capacités de requête limitées. La méthode <xref:System.Data.DataTable.Select%2A> peut être utilisée pour le filtrage et le tri, et les méthodes <xref:System.Data.DataRow.GetChildRows%2A> et <xref:System.Data.DataRow.GetParentRow%2A> pour la navigation dans la hiérarchie. Pour toute opération plus complexe, cependant, le développeur doit écrire une requête personnalisée. Cela peut entraîner un dysfonctionnement des applications et les rendre difficiles à gérer.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] facilite et accélère l'interrogation de données mises en cache dans un objet <xref:System.Data.DataSet>. Ces requêtes sont exprimées dans le langage de programmation même, plutôt qu'en tant que littéraux de chaîne incorporés dans le code de l'application. Ainsi, les développeurs n'ont pas à apprendre de langage de requête spécifique. En outre, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] active [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] aux développeurs de travailler de manière plus productive, parce que le [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE fournit la vérification de la syntaxe de la compilation, les types statiques et prise en charge IntelliSense pour [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] peut également être utilisé pour interroger des données qui ont été consolidées à partir d'une ou plusieurs sources de données. Cela permet de réaliser plusieurs scénarios qui requièrent de la flexibilité dans la façon dont les données sont représentées et gérées. En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Interrogation de DataSets à l'aide de LINQ to DataSet  
 Avant de procéder à l'interrogation d'un objet <xref:System.Data.DataSet> à l'aide de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], vous devez remplir le <xref:System.Data.DataSet>. Il existe plusieurs façons de charger des données dans un <xref:System.Data.DataSet>, par exemple à l’aide de la <xref:System.Data.Common.DataAdapter> classe ou [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md). Une fois que les données ont été chargées dans un <xref:System.Data.DataSet> de l’objet, vous pouvez commencer à interroger. Formulation de requêtes à l’aide de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] est similaire à celle de [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] par rapport aux autres [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-sources de données. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]requêtes peuvent être effectuées sur des tables uniques dans un <xref:System.Data.DataSet> ou par rapport à plusieurs tables à l’aide de la <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A> opérateurs de requête standard.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]les requêtes sont pris en charge sur les deux typé et <xref:System.Data.DataSet> objets. Si le schéma du <xref:System.Data.DataSet> est connu au moment du design de l'application, nous vous recommandons d'utiliser un <xref:System.Data.DataSet> typé. Dans un <xref:System.Data.DataSet>, les tables et lignes ont des membres typés pour chaque colonne, ce qui rend les requêtes plus simples et plus lisibles.  
  
 Outre les opérateurs de requête standard implémentés dans System.Core.dll, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ajoute plusieurs <xref:System.Data.DataSet>-extensions spécifiques qui le rendent plus facile de requête sur un jeu de <xref:System.Data.DataRow> objets. Ces extensions spécifiques à <xref:System.Data.DataSet> incluent des opérateurs pour comparer des séquences de lignes, ainsi que des méthodes qui fournissent l'accès aux valeurs de colonne d'un <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Applications multicouches et LINQ to DataSet  
 Les applications de données multicouches sont des applications centrées sur les données qui sont étagées en plusieurs couches logiques. Une application multicouche classique inclut une couche Présentation, une couche intermédiaire et une couche Données. La séparation des composants d'application en couches distinctes renforce la facilité de maintenance et l'évolutivité de l'application. Pour plus d’informations sur les applications de données multicouches, consultez [travailler avec les jeux de données dans les applications multicouches](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
 Dans les applications multicouches, le <xref:System.Data.DataSet> est souvent utilisé dans la couche intermédiaire pour mettre en cache les informations pour une application Web. Le [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] les fonctionnalités d’interrogation est implémentée via les méthodes d’extension et étend la ADO.NET 2.0 existant <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
