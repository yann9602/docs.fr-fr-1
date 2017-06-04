---
title: "Proc&#233;dure&#160;: g&#233;n&#233;rer le mod&#232;le objet en Visual Basic ou&#160;C# | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: g&#233;n&#233;rer le mod&#232;le objet en Visual Basic ou&#160;C# #
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle.  Deux outils sont disponibles pour générer automatiquement un modèle [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C\# à partir des métadonnées d'une base de données existante.  
  
-   Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez générer un modèle objet à l'aide d'[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].  Le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fournit une interface utilisateur élaborée pour vous aider à générer un modèle objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Outil en ligne de commande SQLMetal  Pour plus d'informations, consultez [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.  Pour plus d'informations, consultez [Procédure : créer dynamiquement une base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 La documentation du [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fournit des exemples montrant comment générer un modèle objet [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C\# à l'aide du [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].  Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal.  Pour plus d'informations, consultez [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## Exemple  
 La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] comme modèle objet basé sur les attributs de l'exemple de base de données Northwind.  Des procédures stockées et des fonctions sont également restituées.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## Exemple  
 La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C\# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind.  Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## Voir aussi  
 [Guide de programmation](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)   
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)   
 [Procédure : personnaliser des classes d'entité à l'aide de l'éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)   
 [Mappage basé sur les attributs](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)   
 [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)   
 [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)   
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)