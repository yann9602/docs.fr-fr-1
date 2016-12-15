---
title: "Erreur du compilateur CS0668 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0668"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0668"
ms.assetid: 7bdaa795-ce13-4284-b753-a617c1735cfa
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0668
Deux indexeurs ont des noms différents ; l'attribut IndexerName doit être utilisé avec le même nom sur chaque indexeur d'un type  
  
 Les valeurs passées à l’attribut **IndexerName** doivent être les mêmes pour tous les indexeurs d’un type. Pour plus d’informations sur l’attribut **IndexerName**, consultez [IndexerNameAttribute, classe](frlrfSystemRuntimeCompilerServicesIndexerNameAttributeClassTopic).  
  
 L’exemple suivant génère l’erreur CS0668 :  
  
```  
// CS0668.cs using System; using System.Runtime.CompilerServices; class IndexerClass { [IndexerName("IName1")] public int this [int index]   // indexer declaration { get { return index; } set { } } [IndexerName("IName2")] public int this [string s]    // CS0668, change IName2 to IName1 { get { return int.Parse(s); } set { } } void Main() { } }  
```