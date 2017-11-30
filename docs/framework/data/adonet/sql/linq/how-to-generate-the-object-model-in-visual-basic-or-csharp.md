---
title: "Comment : générer le modèle objet en Visual Basic ou C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ff5a314fb4264f57f1db3e8475a2e3105897f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Comment : générer le modèle objet en Visual Basic ou C# #
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], un modèle objet dans votre propre langage de programmation est mappé à une base de données relationnelle. Deux outils sont disponibles pour générer automatiquement un [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou le modèle c# à partir des métadonnées de base de données existante.  
  
-   Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez générer un modèle objet à l'aide d'[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fournit une interface utilisateur élaborée pour vous aider à générer un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modèle objet. Pour plus d’informations, consultez [Linq to SQL Tools dans Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
-   Outil en ligne de commande SQLMetal Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Si vous ne possédez pas de base de données existante et que vous souhaitez en créer une à partir d'un modèle objet, vous pouvez utiliser votre éditeur de code et <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Pour plus d’informations, consultez [Comment : créer dynamiquement une base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Documentation pour le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] fournit des exemples montrant comment générer un [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou le modèle objet c# à l’aide de la [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Les informations suivantes fournissent des exemples d'utilisation de l'outil en ligne de commande SQLMetal. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemple  
 La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] comme modèle objet basé sur les attributs de l'exemple de base de données Northwind. Des procédures stockées et des fonctions sont également restituées.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Exemple  
 La ligne de commande SQLMetal présentée dans l'exemple suivant produit du code C# comme modèle objet basé sur les attributs de l'exemple de base de données Northwind. Des procédures stockées et des fonctions sont également restituées, et les noms de table sont automatiquement pluralisés.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [Le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Mappage basé sur un attribut](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
