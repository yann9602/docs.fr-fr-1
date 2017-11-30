---
title: '&#39; &lt;membername&gt;&#39; ne peuvent pas exposer de type &#39;&lt; TypeName&gt;&#39; en dehors du projet via &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords: BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="ef938-102">&#39; &lt;membername&gt;&#39; ne peuvent pas exposer de type &#39;&lt; TypeName&gt;&#39; en dehors du projet via &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="ef938-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="ef938-103">Une variable, un paramètre de procédure ou un retour de fonction est exposé à l’extérieur de son conteneur, mais il est déclaré comme un type qui ne doit pas être exposé en dehors du conteneur.</span><span class="sxs-lookup"><span data-stu-id="ef938-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="ef938-104">Le squelette du code suivant illustre une situation qui génère cette erreur.</span><span class="sxs-lookup"><span data-stu-id="ef938-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="ef938-105">Un type qui est déclaré `Protected`, `Friend`, `Protected Friend`, ou `Private` est destiné à l’accès à l’extérieur de son contexte de déclaration est limité.</span><span class="sxs-lookup"><span data-stu-id="ef938-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="ef938-106">L’utiliser comme données de type d’une variable avec un accès moins limité nuit à cet objectif.</span><span class="sxs-lookup"><span data-stu-id="ef938-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="ef938-107">Dans le code squelette précédent, `exposedVar` est `Public` et expose `privateClass` au code que vous ne devez pas y accéder.</span><span class="sxs-lookup"><span data-stu-id="ef938-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="ef938-108">**ID d’erreur :** BC30909</span><span class="sxs-lookup"><span data-stu-id="ef938-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef938-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ef938-109">To correct this error</span></span>  
  
-   <span data-ttu-id="ef938-110">Modifier le niveau d’accès de la variable, un paramètre de procédure ou une fonction de retour pour être au moins aussi restrictif que le niveau d’accès de son type de données.</span><span class="sxs-lookup"><span data-stu-id="ef938-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef938-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef938-111">See Also</span></span>  
 [<span data-ttu-id="ef938-112">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef938-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
