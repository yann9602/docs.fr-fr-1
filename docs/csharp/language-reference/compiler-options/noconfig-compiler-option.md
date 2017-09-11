---
title: -noconfig (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /noconfig
dev_langs:
- CSharp
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 11
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
ms.openlocfilehash: 594e972dc834ab74412e30a48428f850ae02b5ac
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="noconfig-c-compiler-options"></a><span data-ttu-id="f4e28-102">/noconfig (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="f4e28-102">/noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="f4e28-103">L’option **/noconfig** indique au compilateur de ne pas compiler avec le fichier csc.rsp, qui se trouve dans le même répertoire que le fichier csc.exe d’où il est chargé.</span><span class="sxs-lookup"><span data-stu-id="f4e28-103">The **/noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4e28-104">Syntax</span></span>  
  
```console  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="f4e28-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="f4e28-105">Remarks</span></span>  
 <span data-ttu-id="f4e28-106">Le fichier csc.rsp fait référence à tous les assemblys fournis avec le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4e28-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="f4e28-107">Les références réelles qui sont incluses dans l’environnement de développement Visual Studio .NET varient en fonction du type de projet.</span><span class="sxs-lookup"><span data-stu-id="f4e28-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="f4e28-108">Vous pouvez modifier le fichier csc.rsp et spécifier les options de compilateur supplémentaires qui doivent être incluses dans chaque compilation avec csc.exe via la ligne de commande (à l’exception de l’option **/noconfig**).</span><span class="sxs-lookup"><span data-stu-id="f4e28-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **/noconfig** option).</span></span>  
  
 <span data-ttu-id="f4e28-109">Le compilateur traite les options passées à la commande **csc** en dernier.</span><span class="sxs-lookup"><span data-stu-id="f4e28-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="f4e28-110">De ce fait, toute option sur la ligne de commande se substitue au paramètre de la même option dans le fichier csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="f4e28-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="f4e28-111">Si vous ne voulez pas que le compilateur recherche et utilise les paramètres du fichier csc.rsp, spécifiez **/noconfig**.</span><span class="sxs-lookup"><span data-stu-id="f4e28-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **/noconfig**.</span></span>  
  
 <span data-ttu-id="f4e28-112">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="f4e28-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e28-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4e28-113">See Also</span></span>  
 <span data-ttu-id="f4e28-114">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4e28-114">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="f4e28-115">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="f4e28-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

