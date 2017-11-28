---
title: 'Comment : initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="fb696-102">Comment : initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fb696-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="fb696-103">Une méthode <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> prend deux paramètres, un pour la clé et l’autre pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="fb696-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="fb696-104">Pour initialiser un <xref:System.Collections.Generic.Dictionary`2>, or any collection whose ` ou toute collection dont la méthode Add prend plusieurs paramètres, mettez chaque jeu de paramètres entre accolades, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fb696-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb696-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="fb696-105">Example</span></span>  
 <span data-ttu-id="fb696-106">Dans l’exemple de code suivant, un <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type ` est initialisé avec des instances de type StudentName\`.</span><span class="sxs-lookup"><span data-stu-id="fb696-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="fb696-107">Notez les deux paires d’accolades dans chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="fb696-107">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="fb696-108">Les accolades les plus intérieures encadrent l’initialiseur d’objet pour le `StudentName`, et les accolades les plus extérieures encadrent l’initialiseur pour la paire clé/valeur qui sera ajoutée à `students`<xref:System.Collections.Generic.Dictionary\`2>.</span><span class="sxs-lookup"><span data-stu-id="fb696-108">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary\`2>.</span></span> <span data-ttu-id="fb696-109">Pour finir, l’initialiseur de collection entier pour le dictionnaire est placé entre accolades.</span><span class="sxs-lookup"><span data-stu-id="fb696-109">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb696-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fb696-110">Compiling the Code</span></span>  
 <span data-ttu-id="fb696-111">Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb696-111">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="fb696-112">Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], et il a une référence à System.Core.dll et une directive using pour System.Linq.</span><span class="sxs-lookup"><span data-stu-id="fb696-112">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="fb696-113">Si un ou plusieurs de ces éléments requis sont manquants dans le projet, vous pouvez les ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="fb696-113">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb696-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb696-114">See Also</span></span>  
 [<span data-ttu-id="fb696-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fb696-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fb696-116">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="fb696-116">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
