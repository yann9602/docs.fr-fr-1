---
title: "#<a name=\"pragma-warning-c-reference\"></a>pragma warning (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma warning'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 75c11acfd096d36c96ceb9e9c5c0d16e47e58fa1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="c0864-102">#pragma warning (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c0864-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="c0864-103">`#pragma warning` peut activer ou désactiver certains avertissements.</span><span class="sxs-lookup"><span data-stu-id="c0864-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0864-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0864-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0864-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0864-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="c0864-106">Liste de numéros d’avertissement séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c0864-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="c0864-107">Le préfixe « CS » est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c0864-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="c0864-108">Quand aucun numéro d’avertissement n’est spécifié, `disable` désactive tous les avertissements et `restore` active tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="c0864-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0864-109">Pour trouver les numéros d’avertissement dans Visual Studio, générez votre projet, puis recherchez les numéros d’avertissement dans la fenêtre **Sortie**.</span><span class="sxs-lookup"><span data-stu-id="c0864-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0864-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0864-110">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0864-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0864-111">See Also</span></span>  
 <span data-ttu-id="c0864-112">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0864-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c0864-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0864-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c0864-114">[Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0864-114">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 [<span data-ttu-id="c0864-115">Erreurs du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="c0864-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)

