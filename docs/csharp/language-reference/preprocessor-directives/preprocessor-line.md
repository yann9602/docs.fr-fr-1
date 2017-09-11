---
title: "#<a name=\"line-c-reference\"></a>line (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#line'
dev_langs:
- CSharp
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 13
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
ms.openlocfilehash: 89eac93497deb2312e9da358a22e37db1e4a2f80
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="line-c-reference"></a><span data-ttu-id="084a4-102">#line (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="084a4-102">#line (C# Reference)</span></span>
<span data-ttu-id="084a4-103">`#line` vous permet de modifier le numéro de ligne du compilateur et (éventuellement) la sortie du nom de fichier pour les erreurs et les avertissements.</span><span class="sxs-lookup"><span data-stu-id="084a4-103">`#line` lets you modify the compiler's line number and (optionally) the file name output for errors and warnings.</span></span> <span data-ttu-id="084a4-104">Cet exemple montre comment signaler deux avertissements associés à des numéros de ligne.</span><span class="sxs-lookup"><span data-stu-id="084a4-104">This example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="084a4-105">La directive `#line 200` affecte de force la valeur 200 au numéro de ligne (bien que la valeur par défaut soit #7) et jusqu’à la prochaine directive #line, le nom de fichier indiqué est « Special ».</span><span class="sxs-lookup"><span data-stu-id="084a4-105">The `#line 200` directive forces the line number to be 200 (although the default is #7) and until the next #line directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="084a4-106">La directive par défaut #line rétablit la numérotation de lignes par défaut, qui compte le nombre de lignes qui ont été renumérotés par la directive précédente.</span><span class="sxs-lookup"><span data-stu-id="084a4-106">The #line default directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="084a4-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="084a4-107">Remarks</span></span>  
 <span data-ttu-id="084a4-108">La directive `#line` peut être utilisée dans une étape intermédiaire automatisée du processus de génération.</span><span class="sxs-lookup"><span data-stu-id="084a4-108">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="084a4-109">Par exemple, si des lignes ont été supprimées du fichier de code source d’origine, mais que vous voulez que le compilateur continue de générer une sortie sur la base de la numérotation de lignes d’origine du fichier, vous pouvez supprimer les lignes et simuler ensuite la numérotation de lignes d’origine avec `#line`.</span><span class="sxs-lookup"><span data-stu-id="084a4-109">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>  
  
 <span data-ttu-id="084a4-110">La directive `#line hidden` masque les lignes successives du débogueur, de sorte que quand le développeur parcourt le code, les lignes situées entre une directive `#line hidden` et la directive `#line` suivante (en supposant qu’il ne s’agit pas d’une autre directive `#line hidden`) sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="084a4-110">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="084a4-111">Cette option peut aussi être utilisée pour permettre à ASP.NET de différencier le code défini par l’utilisateur du code généré par l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="084a4-111">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="084a4-112">Même si ASP.NET est le principal utilisateur de cette fonctionnalité, il est probable que d’autres générateurs de code source pourront l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="084a4-112">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>  
  
 <span data-ttu-id="084a4-113">Une directive `#line hidden` n’affecte ni les noms de fichiers ni les numéros de lignes dans les rapports d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="084a4-113">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="084a4-114">Autrement dit, si une erreur se produit dans un bloc masqué, le compilateur indique le nom du fichier et le numéro de ligne actuels de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="084a4-114">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>  
  
 <span data-ttu-id="084a4-115">La directive `#line filename` spécifie le nom de fichier que vous souhaitez voir apparaître dans la sortie du compilateur.</span><span class="sxs-lookup"><span data-stu-id="084a4-115">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="084a4-116">Par défaut, le nom réel du fichier de code source est utilisé.</span><span class="sxs-lookup"><span data-stu-id="084a4-116">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="084a4-117">Le nom de fichier doit être entre guillemets doubles (" ") et doit être précédé d’un numéro de ligne.</span><span class="sxs-lookup"><span data-stu-id="084a4-117">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>  
  
 <span data-ttu-id="084a4-118">Un fichier de code source peut contenir un nombre illimité de directives `#line`.</span><span class="sxs-lookup"><span data-stu-id="084a4-118">A source code file can have any number of `#line` directives.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="084a4-119">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="084a4-119">Example 1</span></span>  
 <span data-ttu-id="084a4-120">L’exemple suivant montre comment le débogueur ignore les lignes masquées dans le code.</span><span class="sxs-lookup"><span data-stu-id="084a4-120">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="084a4-121">Quand vous exécutez l’exemple, celui-ci affiche trois lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="084a4-121">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="084a4-122">Or, quand vous définissez un point d’arrêt, comme dans l’exemple, et que vous appuyez sur F10 pour parcourir le code, vous pouvez remarquer que le débogueur ignore la ligne masquée.</span><span class="sxs-lookup"><span data-stu-id="084a4-122">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="084a4-123">Vous remarquerez aussi que même si vous définissez un point d’arrêt au niveau de la ligne masquée, le débogueur continuera de l’ignorer.</span><span class="sxs-lookup"><span data-stu-id="084a4-123">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="084a4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="084a4-124">See Also</span></span>  
 <span data-ttu-id="084a4-125">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="084a4-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="084a4-126">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="084a4-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="084a4-127">Directives de préprocesseur C#</span><span class="sxs-lookup"><span data-stu-id="084a4-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

