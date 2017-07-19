---
title: "M&#233;thodes g&#233;n&#233;riques Field et SetField (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# M&#233;thodes g&#233;n&#233;riques Field et SetField (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fournit des méthodes d'extension à la classe <xref:System.Data.DataRow> pour accéder aux valeurs de colonne : la méthode <xref:System.Data.DataRowExtensions.Field%2A> et la méthode <xref:System.Data.DataRowExtensions.SetField%2A>. Ces méthodes facilitent l'accès des développeurs aux valeurs de colonne, particulièrement pour les valeurs Null. Le <xref:System.Data.DataSet> utilise <xref:System.DBNull.Value> pour représenter les valeurs Null, alors que [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] utilise la prise en charge de type Nullable introduite dans [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  Pour pouvoir utiliser l'accesseur de colonne existant dans <xref:System.Data.DataRow>, vous devez effectuer un cast de l'objet de retour vers le type approprié.  Si un champ particulier d'un <xref:System.Data.DataRow> peut avoir la valeur Null, vous devez vérifier explicitement une valeur Null parce que le fait de retourner une <xref:System.DBNull.Value> et d'effectuer implicitement un cast vers un autre type lève une <xref:System.InvalidCastException>.  Dans l'exemple suivant, si la méthode <xref:System.Data.DataRow.IsNull%2A> n'était pas été utilisée pour vérifier une valeur Null, une exception serait levée si l'indexeur retournait une <xref:System.DBNull.Value> et tentait d'effectuer un cast vers une <xref:System.String>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 La méthode <xref:System.Data.DataRowExtensions.Field%2A> donne accès aux valeurs de colonne d'un <xref:System.Data.DataRow> et le <xref:System.Data.DataRowExtensions.SetField%2A> définit les valeurs de colonne dans un <xref:System.Data.DataRow>.  Les deux méthodes <xref:System.Data.DataRowExtensions.Field%2A> et <xref:System.Data.DataRowExtensions.SetField%2A> gèrent des types Nullable, ce qui fait que vous n'avez pas à vérifier explicitement les valeurs Null comme dans l'exemple précédent.  Les deux méthodes sont également des méthodes génériques, ce qui fait que vous n'avez pas à effectuer un cast du type de retour.  
  
 L'exemple suivant utilise la méthode <xref:System.Data.DataRowExtensions.Field%2A>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 Notez que le type de données spécifié dans le paramètre générique `T` de la méthode <xref:System.Data.DataRowExtensions.Field%2A> et de la méthode <xref:System.Data.DataRowExtensions.SetField%2A> doit correspondre au type de la valeur sous\-jacente,  sinon une exception <xref:System.InvalidCastException> est levée.  Le nom de la colonne spécifiée doit également correspondre à celui de la colonne dans le <xref:System.Data.DataSet>, sinon une <xref:System.ArgumentException> est levée.  Dans les deux cas, l'exception est levée au moment de l'exécution pendant l'énumération des données lorsque la requête est exécutée.  
  
 La méthode <xref:System.Data.DataRowExtensions.SetField%2A> n'effectue aucune conversion de type.  Toutefois, cela ne signifie pas qu'une conversion de type ne se produira pas.  La méthode <xref:System.Data.DataRowExtensions.SetField%2A> expose le comportement [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] de la classe <xref:System.Data.DataRow>.  Une conversion de type pourrait être exécutée par l'objet <xref:System.Data.DataRow> et la valeur convertie serait enregistrée ensuite sur l'objet <xref:System.Data.DataRow>.  
  
## Voir aussi  
 <xref:System.Data.DataRowExtensions>