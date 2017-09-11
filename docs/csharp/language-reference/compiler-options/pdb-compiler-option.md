---
title: -pdb (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /pdb
dev_langs:
- CSharp
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 8
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
ms.openlocfilehash: 7c72c12347a9096aeed063b84310356cb07b49c3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pdb-c-compiler-options"></a><span data-ttu-id="38b5e-102">/pdb (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="38b5e-102">/pdb (C# Compiler Options)</span></span>
<span data-ttu-id="38b5e-103">L’option de compilateur **/pdb** spécifie le nom et l’emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="38b5e-103">The **/pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38b5e-104">Syntax</span></span>  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="38b5e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="38b5e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="38b5e-106">Nom et emplacement du fichier de symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="38b5e-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38b5e-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="38b5e-107">Remarks</span></span>  
 <span data-ttu-id="38b5e-108">Quand vous spécifiez [/debug (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), le compilateur crée un fichier .pdb dans le même répertoire que celui dans lequel le compilateur va créer le fichier de sortie (.exe ou .dll) avec un nom de fichier identique à celui du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="38b5e-108">When you specify [/debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="38b5e-109">**/pdb** vous permet de spécifier un nom de fichier autre que celui par défaut et un emplacement pour le fichier .pdb.</span><span class="sxs-lookup"><span data-stu-id="38b5e-109">**/pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="38b5e-110">Cette option du compilateur ne peut pas être définie dans l’environnement de développement Visual Studio, ni être modifiée par programmation.</span><span class="sxs-lookup"><span data-stu-id="38b5e-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38b5e-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="38b5e-111">Example</span></span>  
 <span data-ttu-id="38b5e-112">Compilez `t.cs` et créez un fichier .pdb sous le nom tt.pdb :</span><span class="sxs-lookup"><span data-stu-id="38b5e-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="38b5e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38b5e-113">See Also</span></span>  
 <span data-ttu-id="38b5e-114">[Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="38b5e-114">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="38b5e-115">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="38b5e-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

