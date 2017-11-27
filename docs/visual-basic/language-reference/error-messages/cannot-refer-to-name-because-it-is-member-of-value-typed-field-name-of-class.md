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
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Ne peut pas faire référence à &#39; &lt;nom&gt;&#39; car il est membre du champ de valeur typée &#39;&lt; nom&gt;&#39; de classe &#39;&lt; ClassName&gt;&#39; qui a &#39; System.MarshalByRefObject &#39; comme classe de base
La `System.MarshalByRefObject` classe permet aux applications qui prennent en charge l’accès à distance à des objets entre les limites du domaine d’application. Types doivent hériter la `MarshalByRejectObject` classe lorsque le type est utilisé dans les limites du domaine d’application. L’état de l’objet ne doit pas être copié, car les membres de l’objet ne sont pas utilisables en dehors du domaine d’application dans lequel ils ont été créés.  
  
 **ID d’erreur :** BC30310  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérification de la référence de s’assurer que le membre fait référence est valide.  
  
2.  Qualifier explicitement le membre avec le `Me` (mot clé).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.MarshalByRefObject>  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)
