---
title: "Propriétés implémentées automatiquement (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1aa923c6d8208c2d5451957c4112493d0acd561d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="f6581-102">Propriétés implémentées automatiquement (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f6581-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="f6581-103">En C# 3.0 et versions ultérieures, les propriétés implémentées automatiquement rendent la déclaration de propriété plus concise quand aucune logique supplémentaire n’est requise dans les accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="f6581-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="f6581-104">Elles permettent également au code client de créer des objets.</span><span class="sxs-lookup"><span data-stu-id="f6581-104">They also enable client code to create objects.</span></span> <span data-ttu-id="f6581-105">Quand vous déclarez une propriété comme indiqué dans l'exemple suivant, le compilateur crée un champ de stockage privé et anonyme uniquement accessible via les accesseurs `get` et `set` de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f6581-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6581-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6581-106">Example</span></span>  
 <span data-ttu-id="f6581-107">L'exemple suivant montre une classe simple qui a des propriétés implémentées automatiquement :</span><span class="sxs-lookup"><span data-stu-id="f6581-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="f6581-108">En C# 6 et versions ultérieures, vous pouvez initialiser des propriétés implémentées automatiquement de la même façon que des champs :</span><span class="sxs-lookup"><span data-stu-id="f6581-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="f6581-109">La classe qui est illustrée dans l'exemple précédent est mutable.</span><span class="sxs-lookup"><span data-stu-id="f6581-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="f6581-110">Le code client peut modifier les valeurs dans les objets après leur création.</span><span class="sxs-lookup"><span data-stu-id="f6581-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="f6581-111">Dans les classes complexes qui contiennent un comportement significatif (méthodes) ainsi que des données, il est souvent nécessaire d'avoir des propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="f6581-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="f6581-112">Toutefois, pour les petites classes ou les petits structs qui encapsulent simplement un ensemble de valeurs (données) et qui ont peu de comportements ou aucun, vous devez rendre les objets immuables en déclarant l’accesseur set comme étant [privé](../../../csharp/language-reference/keywords/private.md) (immuables pour les consommateurs) ou en déclarant uniquement un accesseur get (immuables partout sauf dans le constructeur).</span><span class="sxs-lookup"><span data-stu-id="f6581-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="f6581-113">Pour plus d’informations, consultez [Guide pratique pour implémenter une classe Lightweight avec des propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f6581-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="f6581-114">Les attributs sont autorisés sur les propriétés implémentées automatiquement, mais évidemment pas sur les champs de stockage puisque ces derniers ne sont pas accessibles à partir de votre code source.</span><span class="sxs-lookup"><span data-stu-id="f6581-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="f6581-115">Si vous devez utiliser un attribut sur le champ de stockage d'une propriété, créez simplement une propriété normale.</span><span class="sxs-lookup"><span data-stu-id="f6581-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6581-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6581-116">See Also</span></span>  
 [<span data-ttu-id="f6581-117">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f6581-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="f6581-118">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="f6581-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
