---
title: '#<a name="externalsource-directive"></a>ExternalSource (Directive)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="externalsource-directive"></a><span data-ttu-id="23066-102">#ExternalSource, directive</span><span class="sxs-lookup"><span data-stu-id="23066-102">#ExternalSource Directive</span></span>
<span data-ttu-id="23066-103">Indique un mappage entre des lignes spécifiques de code source et du texte externe à la source.</span><span class="sxs-lookup"><span data-stu-id="23066-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23066-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23066-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="23066-105">Composants</span><span class="sxs-lookup"><span data-stu-id="23066-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="23066-106">Le chemin d’accès à la source externe.</span><span class="sxs-lookup"><span data-stu-id="23066-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="23066-107">Le numéro de ligne de la première ligne de la source externe.</span><span class="sxs-lookup"><span data-stu-id="23066-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="23066-108">La ligne où l’erreur se produit dans la source externe.</span><span class="sxs-lookup"><span data-stu-id="23066-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="23066-109">Met fin au bloc `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="23066-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23066-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="23066-110">Remarks</span></span>  
 <span data-ttu-id="23066-111">Cette directive est utilisée uniquement par le compilateur et le débogueur.</span><span class="sxs-lookup"><span data-stu-id="23066-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="23066-112">Un fichier source peut inclure des directives de source externe, qui indiquent un mappage entre des lignes spécifiques de code dans le fichier source et du texte externe à la source, tel qu’un fichier .aspx.</span><span class="sxs-lookup"><span data-stu-id="23066-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="23066-113">Si des erreurs sont rencontrées dans le code source désigné lors de la compilation, ils sont identifiés comme provenant de la source externe.</span><span class="sxs-lookup"><span data-stu-id="23066-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="23066-114">Directives de source externe n’ont aucun effet sur la compilation et ne peut pas être imbriquées.</span><span class="sxs-lookup"><span data-stu-id="23066-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="23066-115">Ils sont destinés à un usage interne par l’application uniquement.</span><span class="sxs-lookup"><span data-stu-id="23066-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23066-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23066-116">See Also</span></span>  
 [<span data-ttu-id="23066-117">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="23066-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
