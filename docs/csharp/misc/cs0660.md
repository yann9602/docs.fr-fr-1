---
title: "Avertissement du compilateur (niveau&#160;3) CS0660 | Microsoft Docs"
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
  - "CS0660"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0660"
ms.assetid: 2f77b45b-c5c6-46af-abe9-002e67887896
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS0660
'class' définit l’opérateur \=\= ou l’opérateur \!\= mais ne se substitue pas à Object.Equals\(object o\)  
  
 Le compilateur a détecté l’opérateur d’égalité ou d’inégalité défini par l’utilisateur, mais n’a détecté aucune substitution pour la fonction **Equals**. Un opérateur d’égalité ou d’inégalité défini par l’utilisateur sous\-entend que vous souhaitez également substituer la fonction **Equals**. Pour plus d’informations, consultez [NIB \- Indications concernant la substitution de Equals\(\) et de l'opérateur \=\= \(Guide de programmation C\#\)](http://msdn.microsoft.com/fr-fr/7e4c24c5-7693-4c45-88fb-ba5204fbcb20).  
  
 L’exemple suivant génère l’avertissement CS0660 :  
  
```  
// CS0660.cs // compile with: /W:3 /warnaserror class Test   // CS0660 { public static bool operator == (object o, Test t) { return true; } // uncomment the Equals function to resolve // public override bool Equals(object o) // { //    return true; // } public override int GetHashCode() { return 0; } public static void Main() { } }  
```