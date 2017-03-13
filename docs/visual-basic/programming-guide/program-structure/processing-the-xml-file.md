---
title: "Processing the XML File (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML comments, parsing [Visual Basic]"
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Processing the XML File (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le compilateur génère une chaîne d'identification pour chaque construction de votre code qui est placée entre balises de manière à générer de la documentation.  \(Pour plus d'informations sur la façon d'ajouter des balises à votre code, consultez [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).\) La chaîne d'identification identifie de manière unique la construction.  Les programmes qui traitent le fichier XML peuvent utiliser la chaîne d'identification pour identifier l'élément de métadonnées\/réflexion [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] correspondant.  
  
 Le fichier XML n'est pas une représentation hiérarchique de votre code, mais une simple liste comportant un identificateur généré pour chaque élément.  
  
 Lorsqu'il génère les chaînes d'identification, le compilateur respecte les règles suivantes :  
  
-   La chaîne ne doit contenir aucun espace blanc.  
  
-   La première partie de la chaîne d'identification identifie le type de membre identifié, à l'aide d'un caractère unique suivi de deux points.  Les types de membres utilisés sont présentés ci\-dessous.  
  
|||  
|-|-|  
|Caractère|Description|  
|N|Espace de noms<br /><br /> Vous ne pouvez pas ajouter de commentaires de documentation à un espace de noms, mais vous pouvez ajouter des références CREF à ces commentaires, lorsqu'elles sont prises en charge.|  
|T|type : `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|champ : `Dim`|  
|P|propriété : `Property` \(y compris les propriétés par défaut\)|  
|M|méthode : `Sub`, `Function`, `Declare`, `Operator`|  
|E|événement : `Event`|  
|\!|chaîne d'erreur<br /><br /> Le reste de la chaîne fournit des informations sur l'erreur.  Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] génère des informations d'erreur pour les liens qui ne peuvent pas être résolus.|  
  
-   La deuxième partie de `String` est composée du nom complet de l'élément, à partir de la racine de l'espace de noms.  Le nom de l'élément, ses types englobants et l'espace de noms sont séparés par des points.  Si le nom de l'élément lui\-même comporte des points, ils sont remplacés par un signe dièse \(\#\).  Par principe, aucun nom d'élément ne doit contenir de signe dièse à l'origine.  Par exemple, le nom complet du constructeur `String` est `System.String.#ctor`.  
  
-   Pour les propriétés et méthodes, s'il existe des arguments pour la méthode, la liste des arguments figure à la suite entre parenthèses.  En l'absence d'arguments, aucune parenthèse n'est mentionnée.  Les arguments sont séparés par des virgules.  L'encodage de chaque argument correspond directement à son encodage dans une signature [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)].  
  
## Exemple  
 Le code ci\-dessous illustre la manière dont les chaînes d'identification sont générées pour une classe et ses membres.  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## Voir aussi  
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)