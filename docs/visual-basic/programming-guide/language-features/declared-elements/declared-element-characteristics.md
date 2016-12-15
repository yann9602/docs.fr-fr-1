---
title: "Declared Element Characteristics (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declared elements, lifetime"
  - "access levels, declared elements"
  - "declared elements, scope"
  - "visibility, declared elements"
  - "elements, programming"
  - "scope, declared elements"
  - "lifetime, declared elements"
  - "declared elements, access level"
  - "data types [Visual Basic], declared elements"
  - "declared elements, visibility"
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declared Element Characteristics (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une *caractéristique* d'un élément déclaré est un aspect de cet élément qui détermine l'interaction du code avec ce dernier.  Chaque élément déclaré possède une ou plusieurs des caractéristiques suivantes qui lui sont associées :  
  
-   *Type de données* — les valeurs possibles de l'élément et le mode de stockage de ces valeurs.  Pour plus d'informations, consultez [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
-   *Durée de vie* — la période d'exécution pendant laquelle il est possible d'utiliser l'élément.  Pour plus d'informations, consultez [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   *Portée* — l'ensemble du code qui peut faire référence à l'élément sans qualifier son nom.  Pour plus d'informations, consultez [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).  
  
-   *Niveau d'accès* — l'autorisation pour le code d'utiliser l'élément.  Pour plus d'informations, consultez [How to: Control the Availability of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).  
  
## Caractéristiques des éléments  
 Le tableau suivant répertorie les éléments déclarés et les caractéristiques qui s'appliquent à chacun d'eux.  
  
|Élément|Type de données|Durée de vie|Portée <sup>1</sup>|Niveau d'accès|  
|-------------|---------------------|------------------|-------------------------|--------------------|  
|Variable|Oui|Oui|Oui|Oui|  
|Constante|Oui|Non|Oui|Oui|  
|Énumération|Oui|Non|Oui|Oui|  
|Structure|Non|Non|Oui|Oui|  
|Propriété|Oui|Oui|Oui|Oui|  
|Méthode|Non|Oui|Oui|Oui|  
|Procédure \(`Sub` ou `Function`\)|Non|Oui|Oui|Oui|  
|Paramètre de procédure|Oui|Oui|Oui|Non|  
|Retour de fonction|Oui|Oui|Oui|Non|  
|Opérateur|Oui|Non|Oui|Oui|  
|Interface|Non|Non|Oui|Oui|  
|Classe|Non|Non|Oui|Oui|  
|Événement|Non|Non|Oui|Oui|  
|Délégué|Non|Non|Oui|Oui|  
  
 La portée <sup>1</sup> est parfois connue sous le nom de *visibilité*.  
  
## Voir aussi  
 [Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)