---
title: "Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords: BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 932c36778720718d777412f958c16b4a650e3b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a><span data-ttu-id="f1045-102">Les littéraux XML et les propriétés XML ne sont pas pris en charge dans du code incorporé au sein d'ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f1045-102">XML literals and XML properties are not supported in embedded code within ASP.NET</span></span>
<span data-ttu-id="f1045-103">Littéraux XML et les propriétés XML ne sont pas prises en charge du code incorporé au sein d’ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f1045-103">XML literals and XML properties are not supported in embedded code within ASP.NET.</span></span> <span data-ttu-id="f1045-104">Pour utiliser les fonctionnalités XML, déplacez le code pour le code-behind.</span><span class="sxs-lookup"><span data-stu-id="f1045-104">To use XML features, move the code to code-behind.</span></span>  
  
 <span data-ttu-id="f1045-105">Un littéral XML ou une propriété d’axe XML est définie dans le code incorporé (`<%= =>`) dans un fichier ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f1045-105">An XML literal or XML axis property is defined within embedded code (`<%= =>`) in an ASP.NET file.</span></span>  
  
 <span data-ttu-id="f1045-106">**ID d’erreur :** BC31200</span><span class="sxs-lookup"><span data-stu-id="f1045-106">**Error ID:** BC31200</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1045-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f1045-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f1045-108">Déplacez le code qui inclut le littéral XML ou une propriété d’axe XML dans un fichier de code-behind ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f1045-108">Move the code that includes the XML literal or XML axis property to an ASP.NET code-behind file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1045-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1045-109">See Also</span></span>  
 [<span data-ttu-id="f1045-110">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="f1045-110">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="f1045-111">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="f1045-111">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="f1045-112">XML</span><span class="sxs-lookup"><span data-stu-id="f1045-112">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
