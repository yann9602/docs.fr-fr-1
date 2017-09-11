---
title: "-checked (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
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
ms.openlocfilehash: 63ba89ec42748ccea065bf0fd258fb559abca099
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="checked-c-compiler-options"></a><span data-ttu-id="98cb7-102">/checked (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="98cb7-102">/checked (C# Compiler Options)</span></span>
<span data-ttu-id="98cb7-103">L’option **/checked** spécifie si une instruction arithmétique entière qui produit une valeur en dehors de la plage du type de données, et qui n’est pas dans la portée d’un mot clé [checked](../../../csharp/language-reference/keywords/checked.md) ou [unchecked](../../../csharp/language-reference/keywords/unchecked.md), doit provoquer une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="98cb7-103">The **/checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98cb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98cb7-104">Syntax</span></span>  
  
```console  
/checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="98cb7-105">Notes</span><span class="sxs-lookup"><span data-stu-id="98cb7-105">Remarks</span></span>  
 <span data-ttu-id="98cb7-106">Une instruction arithmétique entière qui est dans la portée d’un mot clé `checked` ou `unchecked` n’est pas soumise à l’effet de l’option **/checked**.</span><span class="sxs-lookup"><span data-stu-id="98cb7-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **/checked** option.</span></span>  
  
 <span data-ttu-id="98cb7-107">Si une instruction arithmétique entière qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked` produit une valeur en dehors de la plage du type de données, et que **/checked+** (**/checked**) est utilisé dans la compilation, cette instruction provoque une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="98cb7-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **/checked+** (**/checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="98cb7-108">Si **/checked-** est utilisé dans la compilation, cette instruction ne provoque pas d’exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="98cb7-108">If **/checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="98cb7-109">La valeur par défaut pour cette option est **/checked-**.</span><span class="sxs-lookup"><span data-stu-id="98cb7-109">The default value for this option is **/checked-**.</span></span> <span data-ttu-id="98cb7-110">Vous pouvez notamment employer **/checked-** pour générer des applications de grande taille.</span><span class="sxs-lookup"><span data-stu-id="98cb7-110">One scenario for using **/checked-** is in building large applications.</span></span> <span data-ttu-id="98cb7-111">Des outils automatisés sont parfois utilisés pour créer ces applications et peuvent affecter automatiquement + à **/checked**.</span><span class="sxs-lookup"><span data-stu-id="98cb7-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **/checked** to +.</span></span> <span data-ttu-id="98cb7-112">Vous pouvez remplacer l’option globale par défaut de l’outil en spécifiant **/checked-**.</span><span class="sxs-lookup"><span data-stu-id="98cb7-112">You can override the tool's global default by specifying **/checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="98cb7-113">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98cb7-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="98cb7-114">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="98cb7-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="98cb7-115">Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="98cb7-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="98cb7-116">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="98cb7-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="98cb7-117">Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="98cb7-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="98cb7-118">Modifiez la propriété **Vérifier les dépassements de capacité arithmétiques positifs et négatifs**.</span><span class="sxs-lookup"><span data-stu-id="98cb7-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="98cb7-119">Pour accéder à cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="98cb7-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98cb7-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="98cb7-120">Example</span></span>  
 <span data-ttu-id="98cb7-121">La commande suivante compile `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="98cb7-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="98cb7-122">L’utilisation de `/checked` dans la commande spécifie que toute instruction arithmétique entière dans le fichier qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked`, et qui produit une valeur en dehors de la plage du type de données, provoque une exception au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="98cb7-122">The use of `/checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="98cb7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98cb7-123">See Also</span></span>  
 <span data-ttu-id="98cb7-124">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="98cb7-124">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="98cb7-125">[Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties) </span><span class="sxs-lookup"><span data-stu-id="98cb7-125">[Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties) </span></span>  
 [<span data-ttu-id="98cb7-126">Présentation du Concepteur de projets</span><span class="sxs-lookup"><span data-stu-id="98cb7-126">Introduction to the Project Designer</span></span>](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)

