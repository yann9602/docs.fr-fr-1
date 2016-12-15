---
title: "Names of Declared XML Elements and Attributes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "declarations [XML in Visual Basic]"
  - "element names [XML in Visual Basic]"
  - "names in XML literals"
  - "attribute names [XML in Visual Basic]"
  - "XML literals [Visual Basic], element names"
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Names of Declared XML Elements and Attributes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette rubrique fournit des indications [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour nommer des éléments XML et des attributs dans les littéraux XML. Dans un littéral XML, vous pouvez spécifier un nom local ou un nom qualifié.  Un nom qualifié se compose d'un préfixe d'espace de noms XML, de deux\-points et d'un nom local.  Pour plus d'informations sur les préfixes d'espace de noms XML, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## Règles  
 Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], le nom local d'un élément ou d'un attribut doit adhérer aux règles suivantes.  
  
-   Il peut commencer par un espace de noms.  Il doit commencer par un caractère alphabétique ou un trait de soulignement \(`_`\).  
  
-   Il doit ne doit contenir que des caractères alphabétiques, des chiffres décimaux, des traits de soulignement, des points \(.\) et des traits d'union \(\-\).  
  
-   Il ne doit pas dépasser 1.024 caractères.  
  
-   Les deux\-points qui figurent dans les noms indiquent la délimitation d'espace de noms.  Par conséquent, vous ne pouvez les utiliser que pour spécifier un espace de noms XML pour un nom particulier.  
  
 De plus, vous devez respecter l'indication suivante.  
  
-   La spécification XML 1.0 préserve tous les noms commençant par une chaîne « xml » de toute variation de mise en majuscules.  N'utilisez donc pas ces noms pour vos noms d'éléments et d'attributs.  
  
### Indications sur la longueur du nom  
 Pour des raisons d'ordre pratique, un nom devrait être aussi court que possible tout en identifiant clairement la nature de l'élément.  La lisibilité de votre code s'en trouve améliorée, et la justification et la taille de fichier source réduites.  
  
 Il ne devrait toutefois pas être court au point de mal décrire l'élément ou son utilisation par votre code.  Cette considération est importante pour la lisibilité de votre code.  Si une autre personne a du mal à le comprendre ou si vous devez l'observer longtemps après l'avoir écrit, ce nom prend du temps ; les noms d'éléments bien choisis permettent en revanche d'économiser du temps.  
  
## Respect de la casse dans les noms  
 Les noms d'éléments XML respectent la casse des lettres.  Cela signifie que lorsque le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compare deux noms qui ne diffèrent que par la casse des lettres, il les interprète comme deux noms différents.  Il interprète, par exemple, `ABC` et `abc` comme deux éléments distincts.  
  
## Espaces de noms XML  
 Lorsque vous créez un littéral d'élément XML, vous pouvez spécifier le préfixe d'espace de noms XML pour le nom d'élément.  Pour plus d'informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## Voir aussi  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)