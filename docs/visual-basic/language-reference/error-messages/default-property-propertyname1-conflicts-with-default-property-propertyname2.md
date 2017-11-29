---
title: "Propriété par défaut &#39; &lt;nom_propriété1&gt;&#39; est en conflit avec la propriété par défaut &#39;&lt; propertyName2&gt;&#39; dans &#39;&lt; ClassName&gt;&#39; et devrait donc être déclaré &#39; Shadows &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords: BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Propriété par défaut &#39; &lt;nom_propriété1&gt;&#39; est en conflit avec la propriété par défaut &#39;&lt; propertyName2&gt;&#39; dans &#39;&lt; ClassName&gt;&#39; et devrait donc être déclaré &#39; Shadows &#39;
Une propriété est déclarée avec le même nom qu’une propriété définie dans la classe de base. Dans ce cas, la propriété de cette classe doit occulter la propriété de classe de base.  
  
 Ce message est un avertissement. `Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40007  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajouter le `Shadows` mot clé à la déclaration ou modifiez le nom de la propriété déclarée.  
  
## <a name="see-also"></a>Voir aussi  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
