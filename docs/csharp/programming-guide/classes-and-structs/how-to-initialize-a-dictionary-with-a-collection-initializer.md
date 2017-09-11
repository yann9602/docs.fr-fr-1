---
title: 'Comment : initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41d6a9934daaa1274901e20de58cfd480c904bfa
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="782b4-102">Comment : initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="782b4-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="782b4-103">Une méthode <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> prend deux paramètres, un pour la clé et l’autre pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="782b4-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="782b4-104">Pour initialiser un <xref:System.Collections.Generic.Dictionary`2>, or any collection whose ` ou toute collection dont la méthode Add prend plusieurs paramètres, mettez chaque jeu de paramètres entre accolades, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="782b4-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="782b4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="782b4-105">Example</span></span>  
 <span data-ttu-id="782b4-106">Dans l’exemple de code suivant, un <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type ` est initialisé avec des instances de type StudentName\`.</span><span class="sxs-lookup"><span data-stu-id="782b4-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`.</span></span>  
  
 <span data-ttu-id="782b4-107">[!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="782b4-107">[!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]</span></span>  
  
 <span data-ttu-id="782b4-108">Notez les deux paires d’accolades dans chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="782b4-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="782b4-109">Les accolades les plus intérieures encadrent l’initialiseur d’objet pour le `StudentName`, et les accolades les plus extérieures encadrent l’initialiseur pour la paire clé/valeur qui sera ajoutée à `students`<xref:System.Collections.Generic.Dictionary\`2>.</span><span class="sxs-lookup"><span data-stu-id="782b4-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary\`2>.</span></span> <span data-ttu-id="782b4-110">Pour finir, l’initialiseur de collection entier pour le dictionnaire est placé entre accolades.</span><span class="sxs-lookup"><span data-stu-id="782b4-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="782b4-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="782b4-111">Compiling the Code</span></span>  
 <span data-ttu-id="782b4-112">Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="782b4-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="782b4-113">Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], et il a une référence à System.Core.dll et une directive using pour System.Linq.</span><span class="sxs-lookup"><span data-stu-id="782b4-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="782b4-114">Si un ou plusieurs de ces éléments requis sont manquants dans le projet, vous pouvez les ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="782b4-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="782b4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="782b4-115">See Also</span></span>  
 <span data-ttu-id="782b4-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="782b4-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="782b4-117">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="782b4-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

