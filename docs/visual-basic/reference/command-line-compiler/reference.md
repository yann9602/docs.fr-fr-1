---
title: Reference (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
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
ms.openlocfilehash: 6870c0b6008124bad18f8eba9207d06e085f2307
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="reference-visual-basic"></a><span data-ttu-id="b77dd-102">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b77dd-102">/reference (Visual Basic)</span></span>
<span data-ttu-id="b77dd-103">Entraîne le compilateur à rendre les informations de type dans les assemblys spécifiés disponibles pour le projet en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="b77dd-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b77dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b77dd-104">Syntax</span></span>  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="b77dd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b77dd-105">Arguments</span></span>  
  
|<span data-ttu-id="b77dd-106">Terme</span><span class="sxs-lookup"><span data-stu-id="b77dd-106">Term</span></span>|<span data-ttu-id="b77dd-107">Définition</span><span class="sxs-lookup"><span data-stu-id="b77dd-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="b77dd-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b77dd-108">Required.</span></span> <span data-ttu-id="b77dd-109">Liste délimitée par des virgules des noms de fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b77dd-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="b77dd-110">Si le nom de fichier contient un espace, placez le nom entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="b77dd-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b77dd-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="b77dd-111">Remarks</span></span>  
 <span data-ttu-id="b77dd-112">Les fichiers que vous importez doivent contenir des métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b77dd-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="b77dd-113">Seuls les types publics sont visibles en dehors de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b77dd-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="b77dd-114">Le [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option importe des métadonnées à partir d’un module.</span><span class="sxs-lookup"><span data-stu-id="b77dd-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="b77dd-115">Si vous référencez un assembly (Assembly A) qui lui-même référence un autre assembly (Assembly B), vous devez référencer l’Assembly B si :</span><span class="sxs-lookup"><span data-stu-id="b77dd-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="b77dd-116">Un type à partir de l’Assembly A hérite d’un type ou implémente une interface à partir de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="b77dd-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="b77dd-117">Un champ, une propriété, un événement ou une méthode qui a un type de paramètre ou type de retour de l’Assembly B est appelé.</span><span class="sxs-lookup"><span data-stu-id="b77dd-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="b77dd-118">Utilisez [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel sont trouve une ou plusieurs références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b77dd-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="b77dd-119">Le compilateur reconnaisse un type dans un assembly (pas un module), il doit être forcé à résoudre le type.</span><span class="sxs-lookup"><span data-stu-id="b77dd-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="b77dd-120">Un exemple de comment vous pouvez faire cela consiste à définir une instance du type.</span><span class="sxs-lookup"><span data-stu-id="b77dd-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="b77dd-121">Autres méthodes sont disponibles pour résoudre les noms de types dans un assembly pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="b77dd-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="b77dd-122">Par exemple, si vous héritez d’un type dans un assembly, le nom de type puis devienne connu du compilateur.</span><span class="sxs-lookup"><span data-stu-id="b77dd-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="b77dd-123">Le fichier réponse Vbc.rsp, qui référence couramment utilisés [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblys, est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="b77dd-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="b77dd-124">Utilisez `/noconfig` si vous ne souhaitez pas que le compilateur utilise Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="b77dd-124">Use `/noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="b77dd-125">La forme abrégée de `/reference` est `/r`.</span><span class="sxs-lookup"><span data-stu-id="b77dd-125">The short form of `/reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b77dd-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="b77dd-126">Example</span></span>  
 <span data-ttu-id="b77dd-127">La suivant code compile le fichier source je`nput.vb` et référence des assemblys de M`etad1.dll` et M`etad2.dll` pour produire O`ut.exe`.</span><span class="sxs-lookup"><span data-stu-id="b77dd-127">The following code compiles source file I`nput.vb` and reference assemblies from M`etad1.dll` and M`etad2.dll` to produce O`ut.exe`.</span></span>  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b77dd-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b77dd-128">See Also</span></span>  
 <span data-ttu-id="b77dd-129">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b77dd-129">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b77dd-130"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="b77dd-130"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="b77dd-131"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="b77dd-131"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="b77dd-132"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="b77dd-132"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="b77dd-133"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="b77dd-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
