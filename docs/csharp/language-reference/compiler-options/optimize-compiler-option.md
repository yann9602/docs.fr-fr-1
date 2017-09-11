---
title: -optimize (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /optimize
dev_langs:
- CSharp
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
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
ms.openlocfilehash: 75a2b65c159e9adb0103765468182919ed6b0a23
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="optimize-c-compiler-options"></a><span data-ttu-id="6b78f-102">/optimize (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="6b78f-102">/optimize (C# Compiler Options)</span></span>
<span data-ttu-id="6b78f-103">L’option **/optimize** active ou désactive les optimisations effectuées par le compilateur pour réduire la taille de votre fichier de sortie et le rendre plus rapide et plus efficace.</span><span class="sxs-lookup"><span data-stu-id="6b78f-103">The **/optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b78f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b78f-104">Syntax</span></span>  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b78f-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="6b78f-105">Remarks</span></span>  
 <span data-ttu-id="6b78f-106">**/optimize** indique aussi au common language runtime d’optimiser le code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b78f-106">**/optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="6b78f-107">Par défaut, les optimisations sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="6b78f-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="6b78f-108">Pour activer les optimisations, spécifiez **/optimize+**.</span><span class="sxs-lookup"><span data-stu-id="6b78f-108">Specify **/optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="6b78f-109">Quand vous créez un module destiné à être utilisé par un assembly, utilisez les mêmes paramètres **/optimize** que ceux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6b78f-109">When building a module to be used by an assembly, use the same **/optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="6b78f-110">**/o** est la forme abrégée de **/optimize**.</span><span class="sxs-lookup"><span data-stu-id="6b78f-110">**/o** is the short form of **/optimize**.</span></span>  
  
 <span data-ttu-id="6b78f-111">Il est possible de combiner les options **/optimize** et [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="6b78f-111">It is possible to combine the **/optimize** and [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6b78f-112">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6b78f-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="6b78f-113">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="6b78f-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="6b78f-114">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="6b78f-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="6b78f-115">Modifiez la propriété **Optimiser le code**.</span><span class="sxs-lookup"><span data-stu-id="6b78f-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="6b78f-116">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="6b78f-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b78f-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b78f-117">Example</span></span>  
 <span data-ttu-id="6b78f-118">Compilez `t2.cs` et activez les optimisations du compilateur :</span><span class="sxs-lookup"><span data-stu-id="6b78f-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b78f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b78f-119">See Also</span></span>  
 <span data-ttu-id="6b78f-120">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="6b78f-120">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="6b78f-121">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="6b78f-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

