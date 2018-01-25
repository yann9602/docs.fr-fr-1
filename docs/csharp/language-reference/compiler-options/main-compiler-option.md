---
title: -main (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5f1d06bf408f13a78df503ab10fe3c57b4ff68a3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="1d343-102">-main (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="1d343-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="1d343-103">Cette option spécifie la classe qui contient le point d’entrée du programme dans le cas où plusieurs classes contiennent une méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="1d343-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d343-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d343-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d343-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1d343-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="1d343-106">Type contenant la méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="1d343-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d343-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1d343-107">Remarks</span></span>  
 <span data-ttu-id="1d343-108">Si votre compilation comprend plusieurs types avec une méthode [Main](../../../csharp/programming-guide/main-and-command-args/index.md), vous pouvez spécifier le type qui contient la méthode **Main** à utiliser comme point d’entrée dans le programme.</span><span class="sxs-lookup"><span data-stu-id="1d343-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="1d343-109">Cette option est à utiliser lors de la compilation d’un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="1d343-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1d343-110">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1d343-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1d343-111">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="1d343-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="1d343-112">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="1d343-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="1d343-113">Modifiez la propriété **Objet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="1d343-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="1d343-114">Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d343-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d343-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d343-115">Example</span></span>  
 <span data-ttu-id="1d343-116">Compilez `t2.cs` et `t3.cs`, en spécifiant que la **Main** se trouve dans `Test2` :</span><span class="sxs-lookup"><span data-stu-id="1d343-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d343-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d343-117">See Also</span></span>  
 [<span data-ttu-id="1d343-118">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="1d343-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1d343-119">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="1d343-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
