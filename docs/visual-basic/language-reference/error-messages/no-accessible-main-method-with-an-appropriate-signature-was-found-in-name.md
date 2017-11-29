---
title: "Non accessible &#39; Principaux &#39; méthode avec une signature appropriée a été trouvé dans &#39; &lt;nom&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords: BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f45dc17304c3c9d62b65760f2c1b5d461812a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="21878-102">Non accessible &#39; Principaux &#39; méthode avec une signature appropriée a été trouvé dans &#39; &lt;nom&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="21878-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="21878-103">Les applications de ligne de commande doivent avoir un `Sub Main` défini.</span><span class="sxs-lookup"><span data-stu-id="21878-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="21878-104">`Main`doit être déclarée comme `Public Shared` si elle est définie dans une classe, ou en tant que `Public` s’il est défini dans un module.</span><span class="sxs-lookup"><span data-stu-id="21878-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="21878-105">Pour plus d’informations sur `Main`, consultez [NIB : Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).</span><span class="sxs-lookup"><span data-stu-id="21878-105">For more information on `Main`, see [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).</span></span>  
  
 <span data-ttu-id="21878-106">**ID d’erreur :** BC30737</span><span class="sxs-lookup"><span data-stu-id="21878-106">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21878-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="21878-107">To correct this error</span></span>  
  
-   <span data-ttu-id="21878-108">Définir un `Public Sub Main` procédure pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="21878-108">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="21878-109">Déclarez-le en tant que `Shared` si et seulement si vous la définissez au sein d’une classe.</span><span class="sxs-lookup"><span data-stu-id="21878-109">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21878-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21878-110">See Also</span></span>  
 [<span data-ttu-id="21878-111">NIB : Version de Visual Basic de Hello, World</span><span class="sxs-lookup"><span data-stu-id="21878-111">NIB: Visual Basic Version of Hello, World</span></span>](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [<span data-ttu-id="21878-112">Structure d’un programme Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21878-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="21878-113">Procédures</span><span class="sxs-lookup"><span data-stu-id="21878-113">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
