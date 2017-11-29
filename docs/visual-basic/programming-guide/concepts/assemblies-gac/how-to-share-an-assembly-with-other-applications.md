---
title: "Comment : partager un Assembly avec d’autres Applications (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 491791ba9b6f0cf6da86a160eddf8e78109b11c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="286d3-102">Comment : partager un Assembly avec d’autres Applications (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="286d3-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="286d3-103">Les assemblys peuvent être privés ou partagés. Par défaut, la plupart des programmes simples se composent d’un assembly privé, car ils ne sont pas destinés à être utilisés par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="286d3-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="286d3-104">Pour partager un assembly avec d’autres applications, celui-ci doit être placé dans le [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="286d3-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="286d3-105">Partage d’un assembly</span><span class="sxs-lookup"><span data-stu-id="286d3-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="286d3-106">Créez votre assembly.</span><span class="sxs-lookup"><span data-stu-id="286d3-106">Create your assembly.</span></span> <span data-ttu-id="286d3-107">Pour plus d’informations, consultez [Création d’assemblys](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="286d3-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="286d3-108">Attribuez un nom fort à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="286d3-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="286d3-109">Pour plus d’informations, consultez [Guide pratique pour signer un assembly avec un nom fort](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="286d3-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="286d3-110">Assignez des informations de version à votre assembly.</span><span class="sxs-lookup"><span data-stu-id="286d3-110">Assign version information to your assembly.</span></span> <span data-ttu-id="286d3-111">Pour plus d’informations, consultez [Versioning des assemblys](https://msdn.microsoft.com/library/51ket42z).</span><span class="sxs-lookup"><span data-stu-id="286d3-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="286d3-112">Ajoutez votre assembly au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="286d3-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="286d3-113">Pour plus d’informations, consultez [Guide pratique pour installer un assembly dans le Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="286d3-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="286d3-114">Accédez aux types contenus dans l’assembly à partir d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="286d3-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="286d3-115">Pour plus d’informations, consultez [Guide pratique pour référencer un assembly avec un nom fort](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="286d3-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286d3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="286d3-116">See Also</span></span>  
 <span data-ttu-id="286d3-117">[Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md) [assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="286d3-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="286d3-118">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="286d3-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
