---
title: Guide pratique pour afficher les arguments de ligne de commande (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
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
ms.openlocfilehash: cf8a57cce252b3596f0a19c9df643427615467c6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="9b3f7-102">Guide pratique pour afficher les arguments de ligne de commande (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9b3f7-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="9b3f7-103">Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles à `Main` par l’intermédiaire d’un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="9b3f7-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="9b3f7-104">Les arguments sont fournis sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="9b3f7-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="9b3f7-105">Chaque élément du tableau contient un argument.</span><span class="sxs-lookup"><span data-stu-id="9b3f7-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="9b3f7-106">Les espaces blancs entre arguments sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="9b3f7-106">White-space between arguments is removed.</span></span> <span data-ttu-id="9b3f7-107">Par exemple, considérez ces appels de ligne de commande d’un fichier exécutable fictif :</span><span class="sxs-lookup"><span data-stu-id="9b3f7-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="9b3f7-108">Entrée sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="9b3f7-108">Input on Command-line</span></span>|<span data-ttu-id="9b3f7-109">Tableau de chaînes passé à Main</span><span class="sxs-lookup"><span data-stu-id="9b3f7-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="9b3f7-110">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="9b3f7-110">**executable.exe a b c**</span></span>|<span data-ttu-id="9b3f7-111">"a"</span><span class="sxs-lookup"><span data-stu-id="9b3f7-111">"a"</span></span><br /><br /> <span data-ttu-id="9b3f7-112">"b"</span><span class="sxs-lookup"><span data-stu-id="9b3f7-112">"b"</span></span><br /><br /> <span data-ttu-id="9b3f7-113">"c"</span><span class="sxs-lookup"><span data-stu-id="9b3f7-113">"c"</span></span>|  
|<span data-ttu-id="9b3f7-114">**executable.exe un deux**</span><span class="sxs-lookup"><span data-stu-id="9b3f7-114">**executable.exe one two**</span></span>|<span data-ttu-id="9b3f7-115">"un"</span><span class="sxs-lookup"><span data-stu-id="9b3f7-115">"one"</span></span><br /><br /> <span data-ttu-id="9b3f7-116">"deux"</span><span class="sxs-lookup"><span data-stu-id="9b3f7-116">"two"</span></span>|  
|<span data-ttu-id="9b3f7-117">**executable.exe "un deux" trois**</span><span class="sxs-lookup"><span data-stu-id="9b3f7-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="9b3f7-118">"un deux"</span><span class="sxs-lookup"><span data-stu-id="9b3f7-118">"one two"</span></span><br /><br /> <span data-ttu-id="9b3f7-119">"trois"</span><span class="sxs-lookup"><span data-stu-id="9b3f7-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9b3f7-120">Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projets](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="9b3f7-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b3f7-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b3f7-121">Example</span></span>  
 <span data-ttu-id="9b3f7-122">Cet exemple affiche les arguments de ligne de commande passés à une application de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9b3f7-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="9b3f7-123">La sortie présentée concerne la première entrée du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9b3f7-123">The output shown is for the first entry in the table above.</span></span>  
  
 <span data-ttu-id="9b3f7-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9b3f7-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3f7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b3f7-125">See Also</span></span>  
 <span data-ttu-id="9b3f7-126">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9b3f7-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9b3f7-127">[Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span><span class="sxs-lookup"><span data-stu-id="9b3f7-127">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span></span>  
 <span data-ttu-id="9b3f7-128">[Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="9b3f7-128">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 <span data-ttu-id="9b3f7-129">[Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span><span class="sxs-lookup"><span data-stu-id="9b3f7-129">[How to: Access Command-Line Arguments Using foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span></span>  
 [<span data-ttu-id="9b3f7-130">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="9b3f7-130">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

