---
title: "Comment&#160;: obtenir les propri&#233;t&#233;s de l&#39;objet de syst&#232;me d&#39;impression sans r&#233;flexion | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PrintSystemObject, obtenir les propriétés"
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: obtenir les propri&#233;t&#233;s de l&#39;objet de syst&#232;me d&#39;impression sans r&#233;flexion
L'utilisation de la réflexion pour détailler les propriétés \(et les types de ces propriétés\) sur un objet peut ralentir les performances de l'application.  L'espace de noms <xref:System.Printing.IndexedProperties> permet d'obtenir ces informations à l'aide de la réflexion.  
  
## Exemple  
 Les étapes de cette procédure sont les suivantes :  
  
1.  Créer une instance du type.  Dans l'exemple ci\-dessous, le type est le type <xref:System.Printing.PrintQueue> fourni avec [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], mais un code presque identique doit fonctionner pour les types que vous dérivez de <xref:System.Printing.PrintSystemObject>.  
  
2.  Créez un <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> à partir de la <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> du type.  La propriété <xref:System.Collections.DictionaryEntry.Value%2A> de chaque entrée dans ce dictionnaire est un objet de l'un des types dérivés de <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
3.  Énumérer les membres du dictionnaire.  Pour chacun d'eux, procédez comme suit.  
  
4.  Effectuez un cast de la valeur de chaque entrée sur <xref:System.Printing.IndexedProperties.PrintProperty> et utilisez\-le pour créer un objet <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
5.  Récupérez le type de <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> de chaque objet <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## Voir aussi  
 <xref:System.Printing.IndexedProperties.PrintProperty>   
 <xref:System.Printing.PrintSystemObject>   
 <xref:System.Printing.IndexedProperties>   
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Collections.DictionaryEntry>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)