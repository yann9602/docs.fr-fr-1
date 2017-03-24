---
title: "Noms des éléments XML déclarés et attributs (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ed8ecf69170acf9745a4038975e7e3421722d52d
ms.lasthandoff: 03/13/2017

---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nom des attributs et des éléments XML déclarés (Visual Basic)
Cette rubrique fournit des [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] conseils pour les noms des éléments XML et des attributs dans les littéraux XML.  Dans un littéral XML, vous pouvez spécifier un nom local ou un nom qualifié. Un nom qualifié se compose d’un préfixe d’espace de noms XML, un signe deux-points et un nom local. Pour plus d’informations sur les préfixes d’espace de noms XML, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Règles  
 Un nom local d’un élément ou attribut dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doivent respecter les règles suivantes.  
  
-   Il peut commencer par un espace de noms. Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).  
  
-   Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux, des traits de soulignement, points (.) et des traits d’union (-).  
  
-   Il ne doit pas être supérieure à 1 024 caractères.  
  
-   Les deux-points qui figurent dans les noms indiquent la délimitation d’espace de noms. Par conséquent, vous pouvez utiliser les deux-points uniquement pour spécifier un espace de noms XML pour un nom particulier.  
  
 En outre, vous devez respecter la règle suivante.  
  
-   La spécification XML 1.0 préserve tous les noms commençant par la chaîne « xml » de toute variation de mise en majuscules. Par conséquent, n’utilisez pas ces noms pour l’élément et les noms d’attributs.  
  
### <a name="name-length-guidelines"></a>Instructions de longueur de nom  
 Dans la pratique, un nom doit être aussi court que possible tout en identifiant clairement la nature de l’élément. Cela améliore la lisibilité de votre code et réduit la taille de fichier source et de longueur de ligne.  
  
 Toutefois, votre nom ne doit pas être court qu’il ne pas décrire suffisamment l’élément ou la façon dont votre code utilise. Ceci est important pour la lisibilité de votre code. Si une autre personne essaie de le comprendre ou si vous devez l’observer longtemps après que l’avoir écrit, ce nom peut gagner du temps.  
  
## <a name="case-sensitivity-in-names"></a>Respect de la casse dans les noms  
 Noms d’éléments XML respectent la casse. Cela signifie que lorsque la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur compare deux noms qui ne diffèrent que par la casse, il les interprète comme deux noms différents. Par exemple, il interprète `ABC` et `abc` comme deux éléments distincts.  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Lorsque vous créez un élément XML littérale, vous pouvez spécifier le préfixe d’espace de noms XML pour le nom de l’élément. Pour plus d’informations, consultez [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
