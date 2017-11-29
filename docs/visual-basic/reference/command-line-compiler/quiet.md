---
title: /quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b816cadb9d805d57a14e9b5df553654dd8167af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="quiet"></a><span data-ttu-id="68078-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="68078-102">/quiet</span></span>
<span data-ttu-id="68078-103">Empêche le compilateur d'afficher le code pour les erreurs et les avertissements liés à la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="68078-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68078-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68078-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="68078-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="68078-105">Remarks</span></span>  
 <span data-ttu-id="68078-106">Par défaut, l'option `/quiet` n'est pas activée.</span><span class="sxs-lookup"><span data-stu-id="68078-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="68078-107">Lorsque le compilateur signale une erreur de syntaxe ou un avertissement, il génère également la ligne de code source.</span><span class="sxs-lookup"><span data-stu-id="68078-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="68078-108">Pour les applications qui analysent la sortie du compilateur, il peut être plus pratique pour la sortie du compilateur est uniquement le texte de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="68078-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="68078-109">Dans l’exemple suivant, `Module1` génère une erreur qui inclut le code source compilé sans `/quiet`.</span><span class="sxs-lookup"><span data-stu-id="68078-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="68078-110">Sortie :</span><span class="sxs-lookup"><span data-stu-id="68078-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="68078-111">Compilé avec `/quiet`, le compilateur génère uniquement les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="68078-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="68078-112">Le `/quiet` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="68078-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68078-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="68078-113">Example</span></span>  
 <span data-ttu-id="68078-114">Le code suivant compile `T2.vb` et n’affiche pas de code pour les diagnostics du compilateur liés à la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="68078-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="68078-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68078-115">See Also</span></span>  
 [<span data-ttu-id="68078-116">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68078-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="68078-117">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="68078-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
