---
title: "Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
dev_langs:
- VB
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
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
ms.openlocfilehash: 12e08feff09e901839c4e282d32a0a4e54e12576
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="53440-102">Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt;</span><span class="sxs-lookup"><span data-stu-id="53440-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="53440-103">Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle Assembly Linker (Al.exe, également appelé Alink) pour générer un assembly avec un manifeste.</span><span class="sxs-lookup"><span data-stu-id="53440-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="53440-104">L'éditeur de liens a signalé une erreur dans la phase de préémission de création de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="53440-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="53440-105">Cela peut être dû à des problèmes avec le fichier de clé ou le conteneur de clé indiqué.</span><span class="sxs-lookup"><span data-stu-id="53440-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="53440-106">Pour signer un assembly, vous devez fournir un fichier de clé valide contenant des informations relatives aux clés publiques et privées.</span><span class="sxs-lookup"><span data-stu-id="53440-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="53440-107">Pour différer la signature d’un assembly, vous devez sélectionner le **temporiser la signature uniquement** et fournir un fichier de clé valid qui contient des informations sur les informations de clé publique.</span><span class="sxs-lookup"><span data-stu-id="53440-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="53440-108">La clé privée n'est pas nécessaire quand la signature d'un assembly est différée.</span><span class="sxs-lookup"><span data-stu-id="53440-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="53440-109">Pour plus d’informations, consultez [Comment : signer un Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span><span class="sxs-lookup"><span data-stu-id="53440-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="53440-110">**ID d’erreur :** BC30140</span><span class="sxs-lookup"><span data-stu-id="53440-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="53440-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="53440-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="53440-112">Examinez le message d’erreur cité et consultez la rubrique [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) erreur AL1019 davantage d’explications et conseils</span><span class="sxs-lookup"><span data-stu-id="53440-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="53440-113">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="53440-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53440-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53440-114">See Also</span></span>  
 <span data-ttu-id="53440-115">[Guide pratique pour signer un assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564) </span><span class="sxs-lookup"><span data-stu-id="53440-115">[How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564) </span></span>  
<span data-ttu-id="53440-116"> [Page Signature, Concepteur de projet](https://docs.microsoft.com/visualstudio/ide/reference/signing-page-project-designer) </span><span class="sxs-lookup"><span data-stu-id="53440-116"> [Signing Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/signing-page-project-designer) </span></span>  
<span data-ttu-id="53440-117"> [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="53440-117"> [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="53440-118"> [Avertissements et erreurs de l’outil Al.exe](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span><span class="sxs-lookup"><span data-stu-id="53440-118"> [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span></span>  
<span data-ttu-id="53440-119"> [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="53440-119"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
