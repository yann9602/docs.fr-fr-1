---
title: "Comment : déclarer et utiliser des propriétés en lecture-écriture (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17bdd05196f834b491c69f648bec0b7cb6e3cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="e0cb8-102">Comment : déclarer et utiliser des propriétés en lecture-écriture (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e0cb8-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="e0cb8-103">Les propriétés offrent la commodité des membres de données publics sans les risques liés à un accès non protégé, non contrôlé et non vérifié aux données d’un objet.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="e0cb8-104">Cela se fait au moyen d’*accesseurs*, lesquels sont des méthodes spéciales qui affectent et récupèrent des valeurs du membre de données sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="e0cb8-105">L’accesseur [set](../../../csharp/language-reference/keywords/set.md) permet aux membres de données d’être affectés, et l’accesseur [get](../../../csharp/language-reference/keywords/get.md) récupère des valeurs de membres de données.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="e0cb8-106">L’exemple suivant montre une classe `Person` qui possède deux propriétés : `Name` (string) et `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="e0cb8-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="e0cb8-107">Étant donné que les deux propriétés fournissent des accesseurs `get` et `set`, elles sont considérées comme des propriétés en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0cb8-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0cb8-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e0cb8-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e0cb8-109">Robust Programming</span></span>  
 <span data-ttu-id="e0cb8-110">Dans l’exemple précédent, les propriétés `Name` et `Age` sont [publiques](../../../csharp/language-reference/keywords/public.md), et incluent un accesseur `get` et un accesseur `set`.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="e0cb8-111">Cela permet à n’importe quel objet de lire et d’écrire ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="e0cb8-112">Toutefois, il est parfois souhaitable d’exclure l’un des accesseurs.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="e0cb8-113">L’omission de l’accesseur `set`, par exemple, met la propriété en lecture seule :</span><span class="sxs-lookup"><span data-stu-id="e0cb8-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 <span data-ttu-id="e0cb8-114">Vous pouvez également exposer publiquement un accesseur mais rendre l’autre private ou protected.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="e0cb8-115">Pour plus d’informations, consultez [Accessibilité de l’accesseur asymétrique](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="e0cb8-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="e0cb8-116">Une fois les propriétés déclarées, vous pouvez les utiliser comme s’il s’agissait de champs de la classe.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="e0cb8-117">Cela permet une syntaxe très naturelle pour obtenir ou définir la valeur d’une propriété, comme dans les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0cb8-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 <span data-ttu-id="e0cb8-118">Notez qu’une variable `value` spéciale est disponible dans la méthode `set` d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="e0cb8-119">Cette variable contient la valeur que l’utilisateur a spécifiée, par exemple :</span><span class="sxs-lookup"><span data-stu-id="e0cb8-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 <span data-ttu-id="e0cb8-120">Notez la syntaxe correcte pour incrémenter la propriété `Age` sur un objet `Person` :</span><span class="sxs-lookup"><span data-stu-id="e0cb8-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 <span data-ttu-id="e0cb8-121">Si des méthodes `set` et `get` distinctes ont été utilisées pour modeler des propriétés, le code équivalent peut avoir la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="e0cb8-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="e0cb8-122">La méthode `ToString` est substituée dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="e0cb8-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 <span data-ttu-id="e0cb8-123">Vous pouvez remarquer que `ToString` n’est pas utilisée de façon explicite dans le programme.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="e0cb8-124">Elle est appelée par défaut par les appels `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="e0cb8-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0cb8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0cb8-125">See Also</span></span>  
 [<span data-ttu-id="e0cb8-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e0cb8-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e0cb8-127">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e0cb8-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="e0cb8-128">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="e0cb8-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
