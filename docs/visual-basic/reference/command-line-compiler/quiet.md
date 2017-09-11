---
title: /quiet | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
dev_langs:
- VB
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bc21be8982fea52bf25d0bedeec2b78eee1e705f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="quiet"></a><span data-ttu-id="bd8df-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="bd8df-102">/quiet</span></span>
<span data-ttu-id="bd8df-103">Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="bd8df-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd8df-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd8df-105">Notes</span><span class="sxs-lookup"><span data-stu-id="bd8df-105">Remarks</span></span>  
 <span data-ttu-id="bd8df-106">Par défaut, l'option `/quiet` n'est pas activée.</span><span class="sxs-lookup"><span data-stu-id="bd8df-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="bd8df-107">Lorsque le compilateur signale une erreur de syntaxe ou un avertissement, il renvoie également la ligne de code source.</span><span class="sxs-lookup"><span data-stu-id="bd8df-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="bd8df-108">Pour les applications qui analysent les résultats de la compilation, il peut être plus pratique pour la sortie du compilateur est uniquement le texte de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="bd8df-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="bd8df-109">Dans l’exemple suivant, `Module1` génère une erreur qui inclut le code source compilé sans `/quiet`.</span><span class="sxs-lookup"><span data-stu-id="bd8df-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="bd8df-110">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bd8df-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="bd8df-111">Compilé avec `/quiet`, le compilateur extrait uniquement ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bd8df-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="bd8df-112">La `/quiet` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bd8df-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd8df-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd8df-113">Example</span></span>  
 <span data-ttu-id="bd8df-114">Le code suivant compile `T2.vb` et n’affiche pas de code pour les diagnostics du compilateur liés à la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="bd8df-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd8df-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd8df-115">See Also</span></span>  
 <span data-ttu-id="bd8df-116">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="bd8df-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="bd8df-117"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="bd8df-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
