---
title: -utf8output (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /utf8output
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 95630afcfcd2ae9ab64660eb0f022dd0733b4c4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="utf8output-c-compiler-options"></a><span data-ttu-id="44a62-102">/utf8output (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="44a62-102">/utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="44a62-103">L’option **/utf8output** affiche la sortie du compilateur en utilisant un encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="44a62-103">The **/utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44a62-104">Syntax</span></span>  
  
```console  
/utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="44a62-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="44a62-105">Remarks</span></span>  
 <span data-ttu-id="44a62-106">Dans certaines configurations internationales, la sortie du compilateur ne peut pas s’afficher correctement dans la console.</span><span class="sxs-lookup"><span data-stu-id="44a62-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="44a62-107">Dans ce cas, utilisez **/utf8output** et redirigez la sortie du compilateur vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="44a62-107">In these configurations, use **/utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="44a62-108">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="44a62-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a62-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44a62-109">See Also</span></span>  
 [<span data-ttu-id="44a62-110">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="44a62-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
