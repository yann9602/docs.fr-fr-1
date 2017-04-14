---
title: "Proc&#233;dure&#160;: g&#233;n&#233;rer du code personnalis&#233; en modifiant un fichier DBML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: g&#233;n&#233;rer du code personnalis&#233; en modifiant un fichier DBML
Vous pouvez générer du code source [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C\# à partir d'un fichier de métadonnées .dbml \(database markup language\).  Cette approche permet de personnaliser le fichier .dbml par défaut avant de générer le code de mappage de l'application.  Il s'agit d'une fonctionnalité avancée.  
  
 Les étapes de ce processus sont les suivantes :  
  
1.  Générez un fichier .dbml.  
  
2.  Utilisez un éditeur pour modifier le fichier .dbml.  Notez que le fichier .dbml doit être validé par rapport au fichier .xsd \(XML Schema Definition\) pour les fichiers .dbml [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  Pour plus d'informations, consultez [Génération de code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Générez le code source [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C\#.  
  
 Les exemples suivants utilisent l'outil en ligne de commande SQLMetal.  Pour plus d'informations, consultez [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## Exemple  
 Le code suivant génère un fichier .dbml à partir de l'exemple de base de données Northwind.  Vous pouvez utiliser le nom de la base de données ou le nom du fichier .mdf comme source pour les métadonnées de base de données.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## Exemple  
 Le code suivant génère le fichier de code source [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C\# à partir d'un fichier .dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## Voir aussi  
 [Génération de code dans LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)   
 [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)   
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)