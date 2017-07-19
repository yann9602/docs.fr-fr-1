---
title: "Boxing des types Nullable (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: e4ff2e8a31ca5a59494f80597460e90107e78c8a
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="boxing-nullable-types-c-programming-guide"></a>Boxing des types Nullable (Guide de programmation C#)
Les objets basés sur des types Nullable sont boxed uniquement si l’objet n’est pas Null. Si <xref:System.Nullable%601.HasValue%2A> a la valeur `false`, la référence d’objet est assignée à `null` au lieu de boxing. Exemple :  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 Si l’objet n’est pas Null (si <xref:System.Nullable%601.HasValue%2A> a la valeur `true`), le boxing s’applique au type sous-jacent sur lequel repose l’objet Nullable. Le boxing d’un type de valeur Nullable non Null convertit le type de valeur lui-même, pas le <xref:System.Nullable%601?displayProperty=fullName> qui encapsule le type de valeur. Exemple :  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 Les deux objets boxed sont identiques à ceux créés par le boxing des types non Nullable. Comme les types boxed non Nullable, ils peuvent être unboxed en types Nullable, comme dans l’exemple suivant :  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a>Remarques  
 Le comportement de types Nullable quand ils sont boxed présente deux avantages :  
  
1.  Les objets Nullable et leur équivalent boxed peuvent être testés pour chercher des valeurs Null :  
  
    ```csharp  
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
  
2.  Les types Nullable boxed prennent en charge pleinement les fonctionnalités du type sous-jacent :  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [Comment : identifier un type Nullable](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
