---
title: "-preferreduilang (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /preferreduilang
dev_langs:
- CSharp
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
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
ms.openlocfilehash: b94c2794642ad93a78eaafdeb655310e4ecb2d25
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="preferreduilang-c-compiler-options"></a><span data-ttu-id="b96c0-102">/preferreduilang (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="b96c0-102">/preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="b96c0-103">L’option de compilateur `/preferreduilang` vous permet de spécifier la langue dans laquelle le compilateur C# affiche la sortie, comme les messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b96c0-103">By using the `/preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b96c0-104">Syntax</span></span>  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="b96c0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b96c0-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="b96c0-106">Le [nom de la langue](http://go.microsoft.com/fwlink/p/?LinkId=236992) à utiliser pour la sortie du compilateur.</span><span class="sxs-lookup"><span data-stu-id="b96c0-106">The [language name](http://go.microsoft.com/fwlink/p/?LinkId=236992) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b96c0-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="b96c0-107">Remarks</span></span>  
 <span data-ttu-id="b96c0-108">Vous pouvez utiliser l’option de compilateur `/preferreduilang` pour spécifier la langue que le compilateur C# doit utiliser pour les messages d’erreur et d’autres types de sortie de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b96c0-108">You can use the `/preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="b96c0-109">Si le module linguistique de la langue n’est pas installé, le paramètre de langue du système d’exploitation est utilisé et aucune erreur n’est signalée.</span><span class="sxs-lookup"><span data-stu-id="b96c0-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="b96c0-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b96c0-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96c0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b96c0-111">See Also</span></span>  
 [<span data-ttu-id="b96c0-112">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="b96c0-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

