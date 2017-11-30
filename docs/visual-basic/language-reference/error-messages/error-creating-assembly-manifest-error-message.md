---
title: "Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="f26ef-102">Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt;</span><span class="sxs-lookup"><span data-stu-id="f26ef-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="f26ef-103">Le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] appelle Assembly Linker (Al.exe, également appelé Alink) pour générer un assembly avec un manifeste.</span><span class="sxs-lookup"><span data-stu-id="f26ef-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="f26ef-104">L'éditeur de liens a signalé une erreur dans la phase de préémission de création de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="f26ef-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="f26ef-105">Cela peut être dû à des problèmes avec le fichier de clé ou le conteneur de clé indiqué.</span><span class="sxs-lookup"><span data-stu-id="f26ef-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="f26ef-106">Pour signer un assembly, vous devez fournir un fichier de clé valide contenant des informations relatives aux clés publiques et privées.</span><span class="sxs-lookup"><span data-stu-id="f26ef-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="f26ef-107">Pour différer la signature d’un assembly, vous devez cocher la case **Différer la signature uniquement** et fournir un fichier de clé valide contenant des informations de clés publiques.</span><span class="sxs-lookup"><span data-stu-id="f26ef-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="f26ef-108">La clé privée n'est pas nécessaire quand la signature d'un assembly est différée.</span><span class="sxs-lookup"><span data-stu-id="f26ef-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="f26ef-109">Pour plus d’informations, consultez [Comment : signer un Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span><span class="sxs-lookup"><span data-stu-id="f26ef-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="f26ef-110">**ID d’erreur :** BC30140</span><span class="sxs-lookup"><span data-stu-id="f26ef-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f26ef-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f26ef-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="f26ef-112">Examinez le message d’erreur entre guillemets et consultez la rubrique [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) erreur AL1019 davantage d’explications et conseils</span><span class="sxs-lookup"><span data-stu-id="f26ef-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="f26ef-113">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f26ef-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26ef-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f26ef-114">See Also</span></span>  
 [<span data-ttu-id="f26ef-115">Guide pratique pour signer un assembly (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="f26ef-115">How to: Sign an Assembly (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [<span data-ttu-id="f26ef-116">Page Signature, Concepteur de projet</span><span class="sxs-lookup"><span data-stu-id="f26ef-116">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 [<span data-ttu-id="f26ef-117">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="f26ef-117">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="f26ef-118">Avertissements et erreurs de l’outil Al.exe</span><span class="sxs-lookup"><span data-stu-id="f26ef-118">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="f26ef-119">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="f26ef-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
