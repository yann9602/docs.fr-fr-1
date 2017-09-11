---
title: "-unsafe (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /unsafe
dev_langs:
- CSharp
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
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
ms.openlocfilehash: 8f285af57d6a06d38d20b2c28e4a637fbc3ecf2c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-c-compiler-options"></a><span data-ttu-id="7d04f-102">/unsafe (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="7d04f-102">/unsafe (C# Compiler Options)</span></span>
<span data-ttu-id="7d04f-103">L’option de compilateur **/unsafe** permet la compilation de code utilisant le mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="7d04f-103">The **/unsafe** compiler option allows code that uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d04f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d04f-104">Syntax</span></span>  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a><span data-ttu-id="7d04f-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="7d04f-105">Remarks</span></span>  
 <span data-ttu-id="7d04f-106">Pour plus d’informations sur le code unsafe, consultez [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="7d04f-106">For more information about unsafe code, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7d04f-107">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d04f-107">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7d04f-108">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="7d04f-108">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="7d04f-109">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="7d04f-109">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="7d04f-110">Cochez la case **Autoriser le code unsafe**.</span><span class="sxs-lookup"><span data-stu-id="7d04f-110">Select the **Allow Unsafe Code** check box.</span></span>  
  
 <span data-ttu-id="7d04f-111">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d04f-111">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d04f-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d04f-112">Example</span></span>  
 <span data-ttu-id="7d04f-113">Compilez `in.cs` selon le mode non sécurisé :</span><span class="sxs-lookup"><span data-stu-id="7d04f-113">Compile `in.cs` for unsafe mode:</span></span>  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d04f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d04f-114">See Also</span></span>  
 <span data-ttu-id="7d04f-115">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="7d04f-115">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="7d04f-116">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="7d04f-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

