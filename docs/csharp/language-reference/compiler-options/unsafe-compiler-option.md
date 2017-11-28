---
title: "-unsafe (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 146977522b400418a26f6a83e1a0ccdca8675bf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-compiler-options"></a><span data-ttu-id="287d6-102">/unsafe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="287d6-102">/unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="287d6-103">L’option de compilateur **/unsafe** permet la compilation de code utilisant le mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="287d6-103">The **/unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="287d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="287d6-104">Syntax</span></span>  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="287d6-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="287d6-105">Remarks</span></span>  
 <span data-ttu-id="287d6-106">Pour plus d’informations sur le code unsafe, consultez [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="287d6-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="287d6-107">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="287d6-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="287d6-108">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="287d6-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="287d6-109">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="287d6-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="287d6-110">Cochez la case **Autoriser le code unsafe**.</span><span class="sxs-lookup"><span data-stu-id="287d6-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="287d6-111">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="287d6-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="287d6-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="287d6-112">Example</span></span>  
 <span data-ttu-id="287d6-113">Compilez `in.cs` selon le mode non sécurisé :</span><span class="sxs-lookup"><span data-stu-id="287d6-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="287d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="287d6-114">See Also</span></span>  
 [<span data-ttu-id="287d6-115">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="287d6-115">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="287d6-116">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="287d6-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
