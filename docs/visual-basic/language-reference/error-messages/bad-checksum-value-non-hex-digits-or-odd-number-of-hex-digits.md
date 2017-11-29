---
title: "Valeur de checksum erronée, pas de chiffre hexadécimal ou de nombre impair de chiffres hexadécimaux"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords: BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1158742c8eaa51bcbb5607795f16ae6c2b570db4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="b5677-102">Valeur de checksum erronée, pas de chiffre hexadécimal ou de nombre impair de chiffres hexadécimaux</span><span class="sxs-lookup"><span data-stu-id="b5677-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="b5677-103">Une valeur de checksum contient des chiffres hexadécimaux non valides ou comporte un nombre impair de chiffres.</span><span class="sxs-lookup"><span data-stu-id="b5677-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="b5677-104">Quand ASP.NET génère un fichier source Visual Basic (extension .vb), il calcule une checksum et la place dans un fichier source masqué, identifié par `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="b5677-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="b5677-105">L'utilisateur peut également générer un fichier .vb pour effectuer cela, mais il est préférable de réserver ce processus à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="b5677-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="b5677-106">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="b5677-106">By default, this message is a warning.</span></span> <span data-ttu-id="b5677-107">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b5677-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b5677-108">**ID d’erreur :** BC42033</span><span class="sxs-lookup"><span data-stu-id="b5677-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5677-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b5677-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="b5677-110">Si ASP.NET génère le fichier source Visual Basic, redémarrez la génération du projet.</span><span class="sxs-lookup"><span data-stu-id="b5677-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2.  <span data-ttu-id="b5677-111">Si l'avertissement persiste après le redémarrage, réinstallez ASP.NET, puis réessayez la génération.</span><span class="sxs-lookup"><span data-stu-id="b5677-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3.  <span data-ttu-id="b5677-112">Si l'avertissement n'est toujours pas résolu, ou si vous n'utilisez pas ASP.NET, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b5677-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5677-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5677-113">See Also</span></span>  
 <span data-ttu-id="b5677-114">[ASP.NET Overview](https://msdn.microsoft.com/library/4w3ex9c2.aspx) (Vue d’ensemble d’ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="b5677-114">[ASP.NET Overview](https://msdn.microsoft.com/library/4w3ex9c2.aspx)</span></span>  
 [<span data-ttu-id="b5677-115">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="b5677-115">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
