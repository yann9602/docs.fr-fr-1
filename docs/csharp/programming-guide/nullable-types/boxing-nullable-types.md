---
title: "Boxing des types Nullable (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "boxing (C#), types Nullable"
  - "types Nullable (C#), boxing et unboxing"
  - "unboxing (C#), types Nullable"
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Boxing des types Nullable (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les objets basés sur des types Nullable sont boxed uniquement si l'objet n'est pas Null.  Si <xref:System.Nullable%601.HasValue%2A> a la valeur `false`, la référence d'objet est assignée à `null` au lieu de boxing.  Par exemple :  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Si l'objet n'est pas Null \(si <xref:System.Nullable%601.HasValue%2A> a la valeur `true`\), le boxing s'applique au type sous\-jacent sur lequel repose l'objet Nullable.  Le boxing d'un type valeur Nullable non Null convertit le type valeur lui\-même, pas le <xref:System.Nullable%601?displayProperty=fullName> qui encapsule le type valeur.  Par exemple :  
  
```  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 Les deux objets boxed sont identiques à ceux créés par le boxing des types non Nullable.  Comme les types boxed non Nullable, ils peuvent être unboxed en types Nullable, comme dans l'exemple suivant :  
  
```  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## Notes  
 Le comportement de types Nullable lorsqu'ils sont boxed a deux avantages :  
  
1.  Les objets Nullable et leur équivalent boxed peuvent être testés pour chercher des valeurs Null :  
  
    ```  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  Les types Nullable boxed prennent en charge pleinement les fonctionnalités du type sous\-jacent :  
  
    ```  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [Comment : identifier un type Nullable](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)