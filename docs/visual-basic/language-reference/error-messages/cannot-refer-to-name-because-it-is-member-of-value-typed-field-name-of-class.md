---
title: "Ne peut pas faire référence à &#39; &lt;nom&gt;&#39; car il est membre du champ de valeur typée &#39;&lt; nom&gt;&#39; de classe &#39;&lt; ClassName&gt;&#39; qui a &#39; System.MarshalByRefObject &#39; comme classe de base"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords: BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="e1c41-102">Ne peut pas faire référence à &#39; &lt;nom&gt;&#39; car il est membre du champ de valeur typée &#39;&lt; nom&gt;&#39; de classe &#39;&lt; ClassName&gt;&#39; qui a &#39; System.MarshalByRefObject &#39; comme classe de base</span><span class="sxs-lookup"><span data-stu-id="e1c41-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="e1c41-103">La `System.MarshalByRefObject` classe permet aux applications qui prennent en charge l’accès à distance à des objets entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e1c41-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="e1c41-104">Types doivent hériter la `MarshalByRejectObject` classe lorsque le type est utilisé dans les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e1c41-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="e1c41-105">L’état de l’objet ne doit pas être copié, car les membres de l’objet ne sont pas utilisables en dehors du domaine d’application dans lequel ils ont été créés.</span><span class="sxs-lookup"><span data-stu-id="e1c41-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="e1c41-106">**ID d’erreur :** BC30310</span><span class="sxs-lookup"><span data-stu-id="e1c41-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1c41-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e1c41-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="e1c41-108">Vérification de la référence de s’assurer que le membre fait référence est valide.</span><span class="sxs-lookup"><span data-stu-id="e1c41-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="e1c41-109">Qualifier explicitement le membre avec le `Me` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="e1c41-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c41-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1c41-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="e1c41-111">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="e1c41-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
