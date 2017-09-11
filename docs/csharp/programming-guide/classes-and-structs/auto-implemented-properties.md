---
title: "Propriétés implémentées automatiquement (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: 23
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
ms.openlocfilehash: 92e0037b73f1054673ea8060b71af5bd4db13ca3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="587c2-102">Propriétés implémentées automatiquement (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="587c2-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="587c2-103">En C# 3.0 et versions ultérieures, les propriétés implémentées automatiquement rendent la déclaration de propriété plus concise quand aucune logique supplémentaire n’est requise dans les accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="587c2-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="587c2-104">Elles permettent également au code client de créer des objets.</span><span class="sxs-lookup"><span data-stu-id="587c2-104">They also enable client code to create objects.</span></span> <span data-ttu-id="587c2-105">Quand vous déclarez une propriété comme indiqué dans l'exemple suivant, le compilateur crée un champ de stockage privé et anonyme uniquement accessible via les accesseurs `get` et `set` de la propriété.</span><span class="sxs-lookup"><span data-stu-id="587c2-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="587c2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="587c2-106">Example</span></span>  
 <span data-ttu-id="587c2-107">L'exemple suivant montre une classe simple qui a des propriétés implémentées automatiquement :</span><span class="sxs-lookup"><span data-stu-id="587c2-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 <span data-ttu-id="587c2-108">[!code-cs[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="587c2-108">[!code-cs[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]</span></span>  
  
 <span data-ttu-id="587c2-109">En C# 6 et versions ultérieures, vous pouvez initialiser des propriétés implémentées automatiquement de la même façon que des champs :</span><span class="sxs-lookup"><span data-stu-id="587c2-109">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="587c2-110">La classe qui est illustrée dans l'exemple précédent est mutable.</span><span class="sxs-lookup"><span data-stu-id="587c2-110">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="587c2-111">Le code client peut modifier les valeurs dans les objets après leur création.</span><span class="sxs-lookup"><span data-stu-id="587c2-111">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="587c2-112">Dans les classes complexes qui contiennent un comportement significatif (méthodes) ainsi que des données, il est souvent nécessaire d'avoir des propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="587c2-112">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="587c2-113">Toutefois, pour les petites classes ou les petits structs qui encapsulent simplement un ensemble de valeurs (données) et qui ont peu de comportements ou aucun, vous devez rendre les objets immuables en déclarant l’accesseur set comme étant [privé](../../../csharp/language-reference/keywords/private.md) (immuables pour les consommateurs) ou en déclarant uniquement un accesseur get (immuables partout sauf dans le constructeur).</span><span class="sxs-lookup"><span data-stu-id="587c2-113">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="587c2-114">Pour plus d’informations, consultez [Guide pratique pour implémenter une classe Lightweight avec des propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="587c2-114">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="587c2-115">Les attributs sont autorisés sur les propriétés implémentées automatiquement, mais évidemment pas sur les champs de stockage puisque ces derniers ne sont pas accessibles à partir de votre code source.</span><span class="sxs-lookup"><span data-stu-id="587c2-115">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="587c2-116">Si vous devez utiliser un attribut sur le champ de stockage d'une propriété, créez simplement une propriété normale.</span><span class="sxs-lookup"><span data-stu-id="587c2-116">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587c2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="587c2-117">See Also</span></span>  
 <span data-ttu-id="587c2-118">[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="587c2-118">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 [<span data-ttu-id="587c2-119">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="587c2-119">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

