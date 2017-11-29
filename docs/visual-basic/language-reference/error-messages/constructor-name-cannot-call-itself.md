---
title: "Constructeur &#39; &lt;nom&gt;&#39; ne peut pas s’appeler lui-même"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords: BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="73499-102">Constructeur &#39; &lt;nom&gt;&#39; ne peut pas s’appeler lui-même</span><span class="sxs-lookup"><span data-stu-id="73499-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="73499-103">A `Sub New` procédure dans une classe ou une structure s’appelle elle-même.</span><span class="sxs-lookup"><span data-stu-id="73499-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="73499-104">Est de l’objectif d’un constructeur pour initialiser une instance d’une classe ou structure lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="73499-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="73499-105">Une classe ou structure peut avoir plusieurs constructeurs fournies ont tous des listes de paramètres différentes.</span><span class="sxs-lookup"><span data-stu-id="73499-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="73499-106">Un constructeur est autorisé à appeler un autre constructeur pour effectuer ses fonctionnalités en plus de son propre.</span><span class="sxs-lookup"><span data-stu-id="73499-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="73499-107">Ne peut pas s’appeler lui-même un constructeur, mais en fait il entraînerait une récurrence infinie si autorisé.</span><span class="sxs-lookup"><span data-stu-id="73499-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="73499-108">**ID d’erreur :** BC30298</span><span class="sxs-lookup"><span data-stu-id="73499-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73499-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="73499-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="73499-110">Vérifiez la liste des paramètres du constructeur appelé.</span><span class="sxs-lookup"><span data-stu-id="73499-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="73499-111">Il doit être différent de celui du constructeur qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="73499-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="73499-112">Si vous ne souhaitez pas appeler un autre constructeur, supprimez le `Sub New` intégralité de l’appel.</span><span class="sxs-lookup"><span data-stu-id="73499-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73499-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73499-113">See Also</span></span>  
 [<span data-ttu-id="73499-114">Durée de vie d’un objet : création et destruction des objets</span><span class="sxs-lookup"><span data-stu-id="73499-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
