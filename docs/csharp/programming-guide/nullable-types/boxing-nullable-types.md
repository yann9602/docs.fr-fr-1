---
title: Boxing des types Nullable (Guide de programmation C#)
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ce063a70ced98fd8b99b4b46d704e08ddc96e10
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="20e91-102">Boxing des types Nullable (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="20e91-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="20e91-103">Les objets basés sur des types Nullable sont boxed uniquement si l’objet n’est pas Null.</span><span class="sxs-lookup"><span data-stu-id="20e91-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="20e91-104">Si <xref:System.Nullable%601.HasValue%2A> a la valeur `false`, la référence d’objet est affectée à `null` au lieu du boxing.</span><span class="sxs-lookup"><span data-stu-id="20e91-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="20e91-105">Exemple :</span><span class="sxs-lookup"><span data-stu-id="20e91-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="20e91-106">Si l’objet n’est pas null (si <xref:System.Nullable%601.HasValue%2A> a la valeur `true`), le boxing s’applique uniquement au type sous-jacent sur lequel repose l’objet Nullable.</span><span class="sxs-lookup"><span data-stu-id="20e91-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="20e91-107">Le boxing d’un type de valeur Nullable non null convertit le type de valeur lui-même, et non pas le <xref:System.Nullable%601?displayProperty=fullName> qui encapsule le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="20e91-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=fullName> that wraps the value type.</span></span> <span data-ttu-id="20e91-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="20e91-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="20e91-109">Les deux objets boxed sont identiques à ceux créés par le boxing des types non Nullable.</span><span class="sxs-lookup"><span data-stu-id="20e91-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="20e91-110">Comme les types boxed non Nullable, ils peuvent être unboxed en types Nullable, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="20e91-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="20e91-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="20e91-111">Remarks</span></span>  
 <span data-ttu-id="20e91-112">Le comportement de types Nullable quand ils sont boxed présente deux avantages :</span><span class="sxs-lookup"><span data-stu-id="20e91-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="20e91-113">Les objets Nullable et leur équivalent boxed peuvent être testés pour chercher des valeurs Null :</span><span class="sxs-lookup"><span data-stu-id="20e91-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
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
  
2.  <span data-ttu-id="20e91-114">Les types Nullable boxed prennent en charge pleinement les fonctionnalités du type sous-jacent :</span><span class="sxs-lookup"><span data-stu-id="20e91-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="20e91-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20e91-115">See Also</span></span>  
 <span data-ttu-id="20e91-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="20e91-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="20e91-117">[Types Nullable](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="20e91-117">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="20e91-118">Guide pratique pour identifier un type Nullable</span><span class="sxs-lookup"><span data-stu-id="20e91-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)

