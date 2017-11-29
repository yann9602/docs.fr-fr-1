---
title: "&#39; &lt;typename&gt;&#39; ne peut pas hériter &lt;type&gt; &#39;&lt; nom_type_base&gt;&#39; car il étend l’accès de la base de &lt;type&gt; en dehors de l’assembly"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords: BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39; &lt;typename&gt;&#39; ne peut pas hériter &lt;type&gt; &#39;&lt; nom_type_base&gt;&#39; car il étend l’accès de la base de &lt;type&gt; en dehors de l’assembly
Une classe ou interface hérite d’une classe de base ou interface, mais ne comporte un niveau d’accès moins restrictif.  
  
 Par exemple, un `Public` interface hérite d’un `Friend` interface, ou un `Protected` hérite de la classe une `Private` classe. Cela expose la classe de base ou une interface pour accéder aux au-delà du niveau prévu.  
  
 **ID d’erreur :** BC30910  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Modifier le niveau d’accès de la classe dérivée ou une interface soit au moins aussi restrictif que celui de la classe de base ou l’interface.  
  
     ou  
  
-   Si le niveau d’accès moins restrictif, supprimez le `Inherits` instruction. Vous ne peut pas hériter d’une classe de base plus restreinte ou une interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
