---
title: "-preferreduilang (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4fcf075dd951d733d294a62de98365c77b16a51d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="e2676-102">-preferreduilang (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="e2676-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="e2676-103">L’option de compilateur `-preferreduilang` vous permet de spécifier la langue dans laquelle le compilateur C# affiche la sortie, comme les messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e2676-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2676-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2676-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2676-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2676-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="e2676-106">Le [nom de la langue](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) à utiliser pour la sortie du compilateur.</span><span class="sxs-lookup"><span data-stu-id="e2676-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2676-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e2676-107">Remarks</span></span>  
 <span data-ttu-id="e2676-108">Vous pouvez utiliser l’option de compilateur `-preferreduilang` pour spécifier la langue que le compilateur C# doit utiliser pour les messages d’erreur et d’autres types de sortie de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e2676-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="e2676-109">Si le module linguistique de la langue n’est pas installé, le paramètre de langue du système d’exploitation est utilisé et aucune erreur n’est signalée.</span><span class="sxs-lookup"><span data-stu-id="e2676-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="e2676-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e2676-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2676-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2676-111">See Also</span></span>  
 [<span data-ttu-id="e2676-112">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="e2676-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
